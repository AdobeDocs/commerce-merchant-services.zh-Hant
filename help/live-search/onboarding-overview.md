---
title: 「入門概觀」
description: '"[!DNL Live Search] 上線流程、系統需求、界限和限制」'
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
recommendations: noCatalog
source-git-commit: ee8c37dc5dab9fcbc47d3d66e3ae0f99c9cb82d8
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# 入門概觀

若要開始使用 [!DNL Live Search] 針對Adobe Commerce，請完成入門流程以安裝擴充功能、設定API金鑰，並同步化您的目錄。

## 上線流程

![[!DNL Live Search] 入門圖表](assets/onboarding-flow.svg)

## 需求 {#requirements}

* [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+
* PHP 8.1 / 8.2
* [!DNL Composer]

### 支援平台

* Adobe Commerce內部部署(EE) ： 2.4.4+
* 雲端上的Adobe Commerce (ECE) ： 2.4.4+

## 端點

[!DNL Live Search] 透過位於的端點通訊 `https://catalog-service.adobe.io/graphql`.

## 邊界和臨界值

目前， [!DNL Live Search] 搜尋/類別API有下列支援的限制和靜態邊界：

### 索引

* 每個存放區檢視最多300個產品屬性的索引。
* 僅索引Adobe Commerce資料庫中的產品。
* 產品必須位於預設共用目錄中。
* CMS頁面未編制索引。

### 查詢

* [!DNL Live Search] 無法存取類別樹狀結構的完整分類法，導致某些階層導覽搜尋案例無法存取。
* [!DNL Live Search] 使用唯一的GraphQL端點進行查詢，以支援動態多面向和「依您的型別搜尋」等功能。 雖然與 [GRAPHQL API](https://developer.adobe.com/commerce/webapi/graphql/)存在一些差異，並且某些欄位可能不完全相容。

若要使用「型錄」許可權限制客戶群組，請執行下列動作：

* 必須將產品指派給根類別。
* 必須向「未登入」客戶群組提供「允許」瀏覽許可權。
* 若要將產品限制在「未登入」客戶群組，請移至每個類別，並設定每個客戶群組的許可權。

### 規則

* 每個存放區檢視的規則數上限為50。
* 每個規則的條件數上限為10。
* 每個規則的事件數上限為25。

### 同義字

* [!DNL Live Search] 每個商店檢視最多可管理200個同義字。

## 價格索引器

Live Search客戶可使用新的 [SaaS價格索引子](../price-index/index.md)，提供更快的價格變更更新和同步處理時間。

### PWA支援

[!DNL Live Search] 可與PWA Studio搭配使用，但使用者可能會看到與其他Commerce實施相較的細微差異。 在Venia中，基本功能（例如搜尋和產品清單頁面）可正常運作，但Graphql的某些排列可能無法正常運作。 此外，也可能會出現效能差異。

* 目前的PWA實作 [!DNL Live Search] 傳回搜尋結果所需的處理時間比 [!DNL Live Search] 搭配原生Commerce店面。
* [!DNL Live Search] PWA不支援 [事件處理](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/). 因此智慧型銷售將無法運作。
* 直接篩選 `description`， `name`， `short_description` 不支援GraphQL搭配使用 [PWA](https://developer.adobe.com/commerce/pwa-studio/)，但會以較一般的篩選器傳回。

使用 [!DNL Live Search] 透過PWA Studio，整合經銷商也必須：

1. 安裝 [livesearch-storefront-utils](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).
1. 設定 `environmentId` 在 `storeDetails` 物件。

   ```javascript
   const storeDetails: StoreDetailsProps = {
       environmentId: <Storefront_ID>,
       websiteCode: "base",
       storeCode: "main_website_store",
       storeViewCode: "default",
       searchUnitId: searchUnitId,
       config: {
           minQueryLength: 5,
           pageSize: 8,
           currencySymbol: "$",
           },
       };
   ```

### 目前不支援

* 此 [進階搜尋](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) 模組停用時機 [!DNL Live Search] 已安裝，且店面頁尾中的進階搜尋連結已移除。
* 使用的多個存貨地點 [MCOM](https://experienceleague.adobe.com/docs/commerce-admin/systems/integrations/mcom.html) 或其他OMS擴充功能
* 產品價格不包括 [增值稅](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/taxes/vat.html) (VAT)。
* [層級價格](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-tier.html) 「即時搜尋」彈出視窗和產品清單頁面Widget中不支援。

## Cookie

[!DNL Live Search] 會收集使用者互動資料，作為其基本功能的一部分，而Cookie可用來儲存此資料。 收集任何使用者資訊時，使用者必須同意儲存Cookie。 [!DNL Live Search] 和 [!DNL Product Recommendations] 共用資料串流，因此使用相同的Cookie機制。 如需詳細資訊，請參閱 [處理Cookie限制](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie.html).
