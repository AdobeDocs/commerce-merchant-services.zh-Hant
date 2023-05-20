---
title: '[!DNL Catalog Service]'
description: '"[!DNL Catalog Service] 因為Adobe Commerce提供了一種方法，它比Adobe CommerceGraphQL本地查詢的檢索速度快得多。」'
exl-id: 266faca4-6a65-4590-99a9-65b1705cac87
source-git-commit: 86e6fdb653278f3e70640155d697897a2ea1b674
workflow-type: tm+mt
source-wordcount: '930'
ht-degree: 0%

---

# [!DNL Catalog Service] 為Adobe Commerce

的 [!DNL Catalog Service] 對於Adobe Commerce擴展，提供豐富的視圖模型（只讀）目錄資料，以快速、全面地呈現與產品相關的店面體驗，包括：

* 產品詳細資訊頁
* 產品清單和類別頁
* 搜索結果頁
* 產品貽貝
* 產品比較頁
* 呈現產品資料的任何其他頁，如購物車、訂單和希望的清單頁

的 [!DNL Catalog Service] 使用 [GraphQL](https://graphql.org/) 請求和接收產品資料。 GraphQL是一種查詢語言，前端客戶端使用它與在後端(如Adobe Commerce)上定義的應用程式寫程式介面(API)通信。 GraphQL是一種流行的通信方法，因為它重量輕，允許系統整合商指定每個響應的內容和順序。

Adobe Commerce有兩個GraphQL系統。 核心GraphQL系統提供多種查詢（讀取操作）和變異（寫入操作），使購物者能夠與多種類型的頁面進行交互，包括產品、客戶帳戶、購物車、結賬等。 但是，返回產品資訊的查詢沒有針對速度進行優化。 服務GraphQL系統只能對產品和相關資訊執行查詢。 這些查詢比類似的核心查詢效能更高。

目錄服務客戶可以使用新 [SaaS價格索引器](../price-index/index.md)提供更快的價格更新和同步時間。

## 建築

下圖顯示了兩個GraphQL系統：

![目錄體系結構圖](assets/catalog-service-architecture.png)

在核心GraphQL系統中，PWA向Commerce應用發送請求，Commerce應用接收每個請求，處理它，可能通過多個子系統發送請求，然後返回對儲存前端的響應。 此往返可能導致頁面載入時間慢，可能導致轉換率降低。

[!DNL Catalog Service] 是Storefront Services網關。 該服務訪問包含產品詳細資訊和相關資訊的單獨資料庫，如產品屬性、變型、價格和類別。 該服務通過索引使資料庫與Adobe Commerce保持同步。
由於服務繞過與應用程式的直接通信，因此能夠減少請求和響應週期的延遲。

>[!NOTE]
>
>該網關將用於將來與產品Recommendations的整合。 在此版本中，您可以 [!DNL Catalog Service GraphQL] 和 [!DNL Live Search] 的許可證密鑰。

核心和服務GraphQL系統之間不直接通信。 您可以從不同的URL訪問每個系統，呼叫需要不同的標題資訊。 兩個GraphQL系統設計為可以一起使用。 的 [!DNL Catalog Service] GraphQL系統加強了核心繫統，使產品店面體驗更快。

您可以根據需要實施 [用於Adobe Developer應用生成器的API網格](https://developer.adobe.com/graphql-mesh-gateway/) 將兩個Adobe CommerceGraphQL系統與使用Adobe Developer的私有和第三方API和其它軟體介面整合在一起。 網格可以配置成確保路由到每個端點的呼叫在報頭中包含正確的授權資訊。

## 架構細節

以下各節介紹兩個GraphQL系統之間的一些差異。

### 架構管理

由於目錄服務作為一種服務運行，整合商不必擔心底層版本的商務。 所有版本的查詢語法相同。 此外，該模式對於所有商家是一致的。 這種一致性使建立最佳做法變得更容易，並顯著增加了店面小部件的重複利用。

### 簡化產品類型

該模式將產品類型的多樣性減少到兩種使用情形：

* 簡單產品是指使用單一價格和數量定義的產品。 目錄服務將簡單、虛擬、可下載和禮品卡產品類型映射到 `simpleProductViews`。

* 複雜產品由多個簡單產品組成。 該元件簡單產品可具有不同的價格。 還可以定義複雜產品，以便購物者可以指定元件簡單產品的數量。 目錄服務將可配置、捆綁和分組的產品類型映射到 `complexProductViews`。

複雜產品選項通過其行為而非類型進行統一和區分。 每個選項值都表示一個簡單的產品。 此選項值可以訪問簡單的產品屬性，包括價格。 當購物者為複雜產品選擇所有選項時，所選選項的組合指向特定的簡單產品。 直到購物者為所有可用選項選擇值時，簡單產品仍然不明確。

### 價格

簡單產品表示具有價格的基本銷售單位。 目錄服務計算折扣前的常規價格以及折扣後的最終價格。 定價計算可包括固定產品稅。 它們不包括個性化促銷。

複雜產品沒有設定的價格。 相反， Catalog Service會返回連結樣本的價格。 例如，商家可以初始為可配置產品的所有變型指定相同的價格。 如果某些尺寸或顏色不受歡迎，商家就可以降低這些變種的價格。 因此，複雜（可配置）產品的價格首先顯示一個價格區間，反映標準和不受歡迎的變體的價格。 購物者為所有可用選項選擇了一個值後，店面將顯示一個單價。

>[!NOTE]
>
> 具有 [!DNL Catalog Service] 可以利用更快的價格變化更新，以及在其網站上同步時間 [SaaS價格索引器](../price-index/index.md)。

## 實施

安裝過程需要配置 [Commerce Services連接器](../landing/saas.md)。 完成後，下一步是由系統整合商更新店面代碼以合併 [!DNL Catalog Service] 的下界。 全部 [!DNL Catalog Service] 查詢被路由到GraphQL網關。 URL在登錄過程中提供。
