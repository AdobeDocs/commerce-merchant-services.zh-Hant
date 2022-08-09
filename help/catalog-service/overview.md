---
title: '"[!DNL Catalog Service]"'
description: '"[!DNL Catalog Service] 因為Adobe Commerce提供了一種比本機的Adobe CommerceGraphQL查詢更快檢索產品顯示頁面和產品清單頁面內容的方法。」'
source-git-commit: eb2242ac99cfaef4ed75936a1b5cc800cc451c83
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# [!DNL Catalog Service] 為Adobe Commerce

{{catalog-service-beta}}

的 [!DNL Catalog Service] 對於Adobe Commerce擴展，提供豐富的視圖模型（只讀）目錄資料，以快速、全面地呈現與產品相關的店面體驗，包括：

* 產品詳細資訊頁
* 產品清單和類別頁
* 搜索結果頁
* 產品貽貝
* 產品比較頁
* 呈現產品資料的任何其他頁，如購物車、訂單和希望的清單頁

的 [!DNL Catalog Service] 使用 [圖形QL](https://graphql.org/) 請求和接收產品資料。 GraphQL是一種查詢語言，前端客戶端使用它與後端(如Adobe Commerce)上定義的應用程式寫程式介面(API)通信。 GraphQL是一種流行的通信方法，因為它輕量，允許系統整合商指定每個響應的內容和順序。

Adobe Commerce有兩個GraphQL系統。 核心GraphQL系統提供多種查詢（讀取操作）和突變（寫入操作），使購物者能夠與多種類型的頁面進行交互，包括產品、客戶帳戶、購物車、結帳等等。 但是，返回產品資訊的查詢沒有針對速度進行優化。 服務GraphQL系統只能對產品和相關資訊執行查詢。 這些查詢比類似的核心查詢效能更高。

## 建築

下圖顯示了兩個GraphQL系統：

![目錄體系結構圖](assets/catalog-service-architecture.png)

在核心GraphQL系統中，PWA向Commerce應用發送請求，Commerce應用接收每個請求，處理它，可能通過多個子系統發送請求，然後返回對儲存前端的響應。 此往返可能導致頁面載入時間慢，可能導致轉換率降低。

[!DNL Catalog Service] 將查詢發送到單獨的GraphQL網關。 該服務訪問包含產品詳細資訊和相關資訊的單獨資料庫，如產品屬性、變型、價格和類別。 該服務通過索引使資料庫與Adobe Commerce保持同步。
由於服務繞過與應用程式的直接通信，因此能夠減少請求和響應週期的延遲。

>[!NOTE]
>
>網關將用於將來與 [!DNL Live Search] 和 [!DNL Product Recommendations]。 在此版本中，您可以 [!DNL Catalog Service] 和來自同一終結點的Live Search查詢（如果您對這兩種產品都具有有效的許可證密鑰）。 但是，來自這兩種產品的查詢當前不共用任何響應資料。

GraphQL系統的核心和服務不直接通信。 您可以從不同的URL訪問每個系統，呼叫需要不同的標題資訊。 兩個GraphQL系統設計為可以一起使用。 的 [!DNL Catalog Service] GraphQL系統增強了核心繫統，使產品庫前體驗更快。

您可以根據需要實施 [用於Adobe Developer應用生成器的API網格](https://developer.adobe.com/graphql-mesh-gateway/) 將兩個Adobe CommerceGraphQL系統與使用Adobe Developer的私有和第三方API和其它軟體介面整合在一起。 網格可以配置成確保路由到每個端點的呼叫在報頭中包含正確的授權資訊。

## 實施

安裝過程需要配置 [Commerce Services連接器](../landing/saas.md)。 完成後，下一步是由系統整合商更新店面代碼以合併 [!DNL Catalog Service] 的下界。 全部 [!DNL Catalog Service] 查詢被路由到GraphQL網關。 URL在登錄過程中提供。

[Adobe Commerce·德夫多斯](https://devdocs.magento.com/catalog-service/index.html) 描述了內核與 [!DNL Catalog Service] 的下界。 還包括每個查詢的參考資訊。
