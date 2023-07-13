---
title: '[!DNL Catalog Service]'
description: '''[!DNL Catalog Service] for Adobe Commerce提供的方式來擷取產品顯示頁面和產品清單頁面的內容，速度比原生Adobe Commerce GraphQL查詢快得多。'
exl-id: 266faca4-6a65-4590-99a9-65b1705cac87
recommendations: noCatalog
source-git-commit: 9ae4aff1851e9ce9920c4fbf11d2616d6f0f6307
workflow-type: tm+mt
source-wordcount: '930'
ht-degree: 0%

---

# [!DNL Catalog Service] 適用於Adobe Commerce

此 [!DNL Catalog Service] for Adobe Commerce擴充功能提供豐富的檢視模型（唯讀）目錄資料，以快速完整地呈現與產品相關的店面體驗，包括：

* 產品詳細資料頁面
* 產品清單和類別頁面
* 搜尋結果頁面
* 產品輪播
* 產品比較頁面
* 轉譯產品資料的任何其他頁面，例如購物車、訂單和願望清單頁面

此 [!DNL Catalog Service] 使用 [GraphQL](https://graphql.org/) 以要求及接收產品資料。 GraphQL是前端使用者端用來與後端(例如Adobe Commerce)上定義的應用程式設計介面(API)進行通訊的查詢語言。 GraphQL是常見的通訊方法，因為其重量輕，可讓系統整合商指定每個回應的內容和順序。

Adobe Commerce有兩個GraphQL系統。 核心GraphQL系統提供各種查詢（讀取操作）和變動（寫入操作），讓購物者可以與多種型別的頁面互動，包括產品、客戶帳戶、購物車、結帳等。 但是，傳回產品資訊的查詢並未針對速度進行最佳化。 GraphQL系統只能對產品和相關資訊執行查詢。 這些查詢比類似的核心查詢效能更高。

目錄服務客戶可以使用新的 [SaaS價格索引器](../price-index/index.md)，提供更快的價格變更更新和同步處理時間。

## 架構

下圖顯示兩個GraphQL系統：

![目錄架構圖](assets/catalog-service-architecture.png)

在核心GraphQL系統中，PWA傳送要求至Commerce應用程式，後者接收每個要求、處理要求（可能透過多個子系統傳送要求），然後傳回回應至店面。 此往返可能會導致頁面載入時間緩慢，進而可能降低轉換率。

[!DNL Catalog Service] 是Storefront服務閘道。 此服務會存取個別的資料庫，其中包含產品詳細資料和相關資訊，例如產品屬性、變體、價格和類別。 此服務會透過索引來保持資料庫與Adobe Commerce同步。
因為服務會略過與應用程式的直接通訊，所以能夠減少要求與回應週期的延遲。

>[!NOTE]
>
>此閘道可用於未來與產品Recommendations的整合。 在此版本中，您可以存取 [!DNL Catalog Service GraphQL] 和 [!DNL Live Search] 從相同端點查詢（如果您擁有兩個產品的有效授權金鑰）。

GraphQL系統的核心和服務不會直接相互通訊。 您可以從不同的URL存取每個系統，而且呼叫需要不同的標頭資訊。 這兩個GraphQL系統旨在搭配使用。 此 [!DNL Catalog Service] GraphQL系統可強化核心系統，讓產品店面體驗更快速。

您可以選擇實作 [Adobe Developer App Builder的API網格](https://developer.adobe.com/graphql-mesh-gateway/) 使用Adobe Developer將兩個Adobe Commerce GraphQL系統與私人和協力廠商API及其他軟體介面整合。 您可以設定網格，以確保路由到每個端點的呼叫在標頭中包含正確的授權資訊。

## 架構詳細資料

以下小節說明這兩個GraphQL系統之間的一些差異。

### 結構描述管理

由於Catalog Service是以服務的形式運作，整合經銷商不需擔心基礎Commerce版本。 所有版本的查詢語法都相同。 此外，所有商戶的結構描述都是一致的。 這種一致性使得建立最佳實務變得更容易，並大幅提高店面Widget的重複使用率。

### 簡化產品型別

結構描述將產品型別的多樣性減少為兩個使用案例：

* 簡單產品是指以單一價格和數量定義的產品。 目錄服務將簡單、虛擬、可下載和禮品卡產品型別對應至 `simpleProductViews`.

* 複雜的產品是由多個簡單產品所組成。 元件簡單產品可以有不同的價格。 也可以定義複雜產品，讓購物者可以指定元件簡單產品的數量。 目錄服務將可配置、套件組合和群組的產品型別對應至 `complexProductViews`.

複雜的產品選項會根據其行為而非型別加以統一和區分。 每個選項值都代表一個簡單的產品。 此選項值可存取簡單產品屬性，包括價格。 當購物者為複雜產品選取所有選項時，所選選項的組合指向特定的簡單產品。 在購物者為所有可用選項選取值之前，簡單產品會保持模稜兩可。

### 價格

簡單產品代表有價格的基本銷售單位。 「目錄服務」會計算折扣前的一般價格，以及折扣後的最終價格。 定價計算可包含固定產品稅捐。 它們會排除個人化促銷活動。

複雜產品沒有設定價格。 相反地，目錄服務會傳回連結的簡單專案的價格。 例如，商家一開始可指定相同價格給可設定產品的所有變體。 如果某些尺寸或顏色不受歡迎，商家可能會降低這些系列的價格。 因此，複雜（可設定）產品的價格一開始會顯示價格範圍，反映標準及不受歡迎的變體的價格。 購物者為所有可用選項選取值後，店面會顯示單一價格。

>[!NOTE]
>
> 商務客戶，具有 [!DNL Catalog Service] 可透過以下優勢，利用網站更快速的價格更新及同步化時間： [SaaS價格索引器](../price-index/index.md).

## 實作

安裝程式需要設定 [商務服務聯結器](../landing/saas.md). 完成此操作後，系統整合商下一步將更新店面程式碼以納入 [!DNL Catalog Service] 查詢。 全部 [!DNL Catalog Service] 查詢會路由至GraphQL閘道。 URL會在上線流程期間提供。
