---
title: '[!DNL Catalog Service]'
description: '''[!DNL Catalog Service] 針對Adobe Commerce，提供比原生Adobe Commerce GraphQL查詢更快速擷取產品顯示頁面和產品清單頁面內容的方法。'
exl-id: 266faca4-6a65-4590-99a9-65b1705cac87
source-git-commit: dfe3d9b8738ea68257831c445f1f0b2c8c8b6859
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 0%

---

# [!DNL Catalog Service] 針對Adobe Commerce

{{catalog-service-beta}}

此 [!DNL Catalog Service] 針對Adobe Commerce擴充功能，提供豐富檢視模型（唯讀）目錄資料，以快速且完整地呈現與產品相關的店面體驗，包括：

* 產品詳細資料頁面
* 產品清單和類別頁面
* 搜尋結果頁面
* 產品輪盤
* 產品比較頁面
* 轉譯產品資料的任何其他頁面，例如購物車、訂購和願望清單頁面

此 [!DNL Catalog Service] uses [GraphQL](https://graphql.org/) 請求和接收產品資料。 GraphQL是一種查詢語言，前端用戶端用來與後端(如Adobe Commerce)上定義的應用程式程式設計介面(API)通訊。 GraphQL是一種常見的通信方法，因為它重量輕，允許系統整合商指定每個響應的內容和順序。

Adobe Commerce有兩個GraphQL系統。 核心GraphQL系統提供廣泛的查詢（讀取操作）和突變（寫入操作），使購物者能夠與許多類型的頁面進行交互，包括產品、客戶帳戶、購物車、結帳等。 但是，傳回產品資訊的查詢沒有針對速度進行最佳化。 服務GraphQL系統只能對產品和相關資訊執行查詢。 這些查詢比類似的核心查詢更具效能。

## 架構

下圖顯示了兩個GraphQL系統：

![目錄架構圖](assets/catalog-service-architecture.png)

在核心GraphQL系統中，PWA會向商務應用程式發送請求，商務應用程式會接收每個請求，處理它，可能通過多個子系統發送請求，然後向店面返迴響應。 此往返可能導致頁面載入時間緩慢，並可能導致較低的轉換率。

[!DNL Catalog Service] 將查詢發送到單獨的GraphQL網關。 該服務訪問一個單獨的資料庫，該資料庫包含產品詳細資訊和相關資訊，如產品屬性、變型、價格和類別。 此服務會透過索引，讓資料庫與Adobe Commerce保持同步。
由於服務繞過與應用程式的直接通信，因此能夠減少請求的延遲和響應週期。

>[!NOTE]
>
>此閘道可供日後與產品Recommendations整合。 在此版本中，您可以存取 [!DNL Catalog Service] 和 [!DNL Live Search] 如果您對這兩種產品都具有有效的許可證密鑰，則會從同一端點進行聯合查詢。

核心和服務GraphQL系統不會直接相互通信。 您可從不同的URL存取每個系統，而呼叫需要不同的標題資訊。 兩個GraphQL系統設計為可一起使用。 此 [!DNL Catalog Service] GraphQL系統可擴大核心繫統，讓產品店面體驗更快。

您可以選擇實作 [Adobe Developer App Builder的API Mesh](https://developer.adobe.com/graphql-mesh-gateway/) 將兩個Adobe Commerce GraphQL系統與使用Adobe Developer的私有和協力廠商API及其他軟體介面整合。 網格可配置為確保路由到每個端點的調用在標題中包含正確的授權資訊。

## 實作

安裝程式需要配置 [商務服務連接器](../landing/saas.md). 完成後，下一步是讓系統整合商更新店面代碼以合併 [!DNL Catalog Service] 查詢。 全部 [!DNL Catalog Service] 查詢會路由至GraphQL閘道。 URL會在上線程式期間提供。
