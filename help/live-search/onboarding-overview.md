---
title: 「入門概述」
description: '"[!DNL Live Search] 上線流程、系統需求、界限和限制」'
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
source-git-commit: 86e6fdb653278f3e70640155d697897a2ea1b674
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# 入門概述

若要開始使用 [!DNL Live Search] 針對Adobe Commerce，請完成入門流程以安裝擴充功能、設定API金鑰，並同步化您的目錄。

## 上線流程

![[!DNL Live Search] 入門圖表](assets/onboarding-flow.svg)

## 需求 {#requirements}

* [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+
* PHP 8.1 / 8.2
* [!DNL Composer]

### 支援的平台

* Adobe Commerce內部部署(EE) ：2.4.4+
* 雲端上的Adobe Commerce (ECE) ：2.4.4+

## 邊界和臨界值

目前， [!DNL Live Search] 搜尋/類別API有下列支援的限制和靜態邊界：

### 索引

* 每個商店檢視最多索引300個產品屬性。
* 僅索引Adobe Commerce資料庫中的產品。
* 產品必須位於預設共用目錄中。
* CMS頁面未編制索引。

### 查詢

* [!DNL Live Search] 無法存取類別樹狀結構的完整分類法，這使得一些階層式導覽搜尋情境超出其範圍。
* [!DNL Live Search] 使用唯一的GraphQL端點進行查詢，以支援動態多面向和「依您的型別搜尋」等功能。 雖然與 [GRAPHQL API](https://developer.adobe.com/commerce/webapi/graphql/)，有一些差異，有些欄位可能不完全相容。

若要使用「型錄」許可權來限制客戶群組，請執行下列步驟：

* 必須將產品指派至根類別。
* 必須向「未登入」客戶群組授予「允許」瀏覽許可權。
* 若要將產品限制在「未登入」客戶群組，請移至每個類別，並為每個客戶群組設定許可權。

### 規則

* 每個存放區檢視的規則數量上限為50。
* 每個規則的條件數上限為10。
* 每個規則的最大事件數為25。

### 同義字

* [!DNL Live Search] 每個存放區檢視最多可管理200個同義字。

## 價格索引器

Live Search客戶可使用新的 [SaaS價格索引器](../price-index/index.md)，提供更快的價格變更更新和同步處理時間。

### PWA支援

即時搜尋支援被視為測試版，因為並非所有PWA都經過測試 [!DNL Live Search]. 在Venia中，搜尋和產品清單頁面等基本功能可以運作，但Graphql的某些排列可能無法正常運作。

* 目前的Beta版PWA實施 [!DNL Live Search] 傳回搜尋結果所需的處理時間比 [!DNL Live Search] 搭配原生Commerce店面。
* [!DNL Live Search] PWA中不支援 [事件處理](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).
* 直接篩選 `description`， `name`， `short_description` 不支援GraphQL搭配使用 [PWA](https://developer.adobe.com/commerce/pwa-studio/)，但會以較一般的篩選條件傳回。

### 目前不支援

* 此 [進階搜尋](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) 模組停用時機 [!DNL Live Search] ，並移除店面頁尾中的進階搜尋連結。
* 使用的多個存貨地點 [MCOM](https://experienceleague.adobe.com/docs/commerce-admin/systems/integrations/mcom.html) 或其他OMS擴充功能
* 產品價格不包括 [加值稅](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/taxes/vat.html) (VAT)。
* [層級價格](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-tier.html) 「即時搜尋」彈出視窗和產品清單頁面Widget中不支援。

## Cookie

[!DNL Live Search] 會收集使用者互動資料，作為其基本功能的一部分，而Cookie會用來儲存此資料。 收集任何使用者資訊時，使用者必須同意儲存Cookie。 [!DNL Live Search] 和 [!DNL Product Recommendations] 共用資料串流，因此使用相同的Cookie機制。 如需詳細資訊，請參閱 [處理Cookie限制](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie.html).
