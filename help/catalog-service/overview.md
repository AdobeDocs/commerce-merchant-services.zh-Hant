---
title: '[!DNL Catalog Service]'
description: '''[!DNL Catalog Service] 針對Adobe Commerce，提供比原生Adobe Commerce GraphQL查詢更快速擷取「產品顯示頁面」和「產品清單頁面」內容的方法。'
exl-id: 266faca4-6a65-4590-99a9-65b1705cac87
source-git-commit: 489de0f56cba06620c334e2b17040b32a72968ef
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 0%

---

# [!DNL Catalog Service] 針對Adobe Commerce

此 [!DNL Catalog Service] 針對Adobe Commerce擴充功能，提供豐富檢視模型（唯讀）目錄資料，以快速且完整地呈現與產品相關的店面體驗，包括：

* 產品詳細資料頁面
* 產品清單和類別頁面
* 搜尋結果頁面
* 產品輪盤
* 產品比較頁面
* 轉譯產品資料的任何其他頁面，例如購物車、訂購和願望清單頁面

此 [!DNL Catalog Service] uses [GraphQL](https://graphql.org/) 請求和接收產品資料。 GraphQL是前端用戶端用來與後端(例如Adobe Commerce)上定義的應用程式程式設計介面(API)通訊的查詢語言。 GraphQL是常見的通訊方法，因為其重量輕，可讓系統整合商指定每個回應的內容和順序。

Adobe Commerce有兩個GraphQL系統。 核心GraphQL系統提供廣泛的查詢（讀取操作）和突變（寫入操作），允許購物者與許多類型的頁面互動，包括產品、客戶帳戶、購物車、結帳等。 但是，傳回產品資訊的查詢沒有針對速度進行最佳化。 服務GraphQL系統只能對產品和相關資訊執行查詢。 這些查詢比類似的核心查詢更具效能。

您可以將這些查詢發送到網關(網址為https://catalog-service.adobe.io/graphql)，以運行這些查詢。

## 架構

下圖顯示兩個GraphQL系統：

![目錄架構圖](assets/catalog-service-architecture.png)

在核心GraphQL系統中，PWA會向商務應用程式傳送要求，商務應用程式會接收每個要求，處理，可能會透過多個子系統傳送要求，然後傳回回應給店面。 此往返可能導致頁面載入時間緩慢，並可能導致較低的轉換率。

[!DNL Catalog Service] 是店面服務網關。 該服務訪問一個單獨的資料庫，該資料庫包含產品詳細資訊和相關資訊，如產品屬性、變型、價格和類別。 此服務會透過索引，讓資料庫與Adobe Commerce保持同步。
由於服務繞過與應用程式的直接通信，因此能夠減少請求的延遲和響應週期。

>[!NOTE]
>
>此閘道可供日後與產品Recommendations整合。 在此版本中，您可以存取 [!DNL Catalog Service GraphQL] 和 [!DNL Live Search] 如果您對這兩種產品都有有效的許可證密鑰，則從同一端點查詢。

核心和服務GraphQL系統不會直接彼此通訊。 您可從不同的URL存取每個系統，而呼叫需要不同的標題資訊。 這兩個GraphQL系統設計為可搭配使用。 此 [!DNL Catalog Service] GraphQL系統可擴大核心繫統，讓產品店面體驗更快。

您可以選擇實作 [Adobe Developer App Builder的API Mesh](https://developer.adobe.com/graphql-mesh-gateway/) 將兩個Adobe Commerce GraphQL系統與使用Adobe Developer的私人和協力廠商API及其他軟體介面整合。 網格可配置為確保路由到每個端點的調用在標題中包含正確的授權資訊。

## 架構詳細資訊

以下各節說明兩個GraphQL系統之間的一些差異。

### 結構管理

由於目錄服務以服務的形式運作，整合商無需擔心基礎版本的商務。 所有版本查詢的語法都相同。 此外，所有商戶的結構都一致。 這種一致性使得建立最佳做法更加容易，並顯著增加對店面小工具的重複使用。

### 簡化產品類型

此結構將產品類型的多樣性降低為兩種使用案例：

* 簡單產品是指以單一價格和數量定義的產品。 目錄服務將簡單、虛擬、可下載和禮品卡產品類型映射到 `simpleProductViews`.

* 複雜產品由多個簡單產品組成。 構成簡單的產品可以有不同的價格。 也可以定義複雜產品，以便購物者可以指定元件簡單產品的數量。 目錄服務將可配置、捆綁和分組的產品類型映射到 `complexProductViews`.

複雜的產品選項是統一的，並且可以根據其行為（而非類型）進行區分。 每個選項值代表簡單產品。 此選項值可存取簡單的產品屬性，包括價格。 當購物者為複雜產品選取所有選項時，選取的選項組合會指向特定的簡單產品。 在購物者為所有可用選項選取值之前，簡單產品仍不明確。

### 價格

簡單產品代表有價格的基本銷售單位。 目錄服務會計算折扣前的一般價格以及折扣後的最終價格。 定價計算可以包括固定產品稅。 它們會排除個人化促銷活動。

複雜產品沒有固定的價格。 相反，目錄服務會傳回連結範例的價格。 例如，商家可以初始將相同的價格分配給可配置產品的所有變體。 如果某些尺寸或顏色不受歡迎，商家就可以降低這些變種的價格。 因此，複雜（可配置）產品的價格首先顯示一個價格區間，反映標準和不受歡迎變體的價格。 購物者為所有可用選項選取值後，店面會顯示單一價格。

## 實作

安裝程式需要配置 [商務服務連接器](../landing/saas.md). 完成後，下一步是讓系統整合商更新店面代碼以合併 [!DNL Catalog Service] 查詢。 全部 [!DNL Catalog Service] 查詢會路由至GraphQL閘道。 URL會在上線程式期間提供。
