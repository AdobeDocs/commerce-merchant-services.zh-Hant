---
title: "入門概述"
description: '"[!DNL Live Search] 登機流、系統要求、邊界和限制」'
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
source-git-commit: 86e6fdb653278f3e70640155d697897a2ea1b674
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# 入門概述

開始使用 [!DNL Live Search] 對於Adobe Commerce，完成登錄過程以安裝擴展、配置API密鑰和同步目錄。

## 登機流

![[!DNL Live Search] 附圖](assets/onboarding-flow.svg)

## 要求 {#requirements}

* [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+
* 8.1菲律賓比索/8.2
* [!DNL Composer]

### 支援的平台

* Adobe CommerceOnPrem(EE):2.4.4+
* Adobe Commerce雲(ECE):2.4.4+

## 邊界和閾值

當前， [!DNL Live Search] search/category API具有以下受支援的限制和靜態邊界：

### 索引

* 每個儲存視圖索引最多300個產品屬性。
* 僅對來自Adobe Commerce資料庫的產品進行索引。
* 產品必須位於預設共用目錄中。
* 未對CMS頁編製索引。

### 查詢

* [!DNL Live Search] 無權訪問類別樹的完整分類，這使得某些分層導航搜索方案超出其範圍。
* [!DNL Live Search] 使用唯一的GraphQL端點進行查詢，以支援動態分頁和按類型搜索等功能。 雖然與 [GraphQLAPI](https://developer.adobe.com/commerce/webapi/graphql/)，存在一些差異，有些欄位可能不完全相容。

要使用目錄權限限制客戶組，請執行以下操作：

* 產品必須分配給根類別。
* 必須為「未登錄」客戶組授予「允許」瀏覽權限。
* 要將產品限制為「未登錄」客戶組，請轉到每個類別並為每個客戶組設定權限。

### 規則

* 每個儲存視圖的最大規則數為50。
* 每個規則的最大條件數為10。
* 每個規則的最大事件數為25。

### 同義詞

* [!DNL Live Search] 每個儲存視圖最多可管理200個同義詞。

## 價格索引器

Live Search客戶可以使用 [SaaS價格索引器](../price-index/index.md)提供更快的價格更新和同步時間。

### PWA支援

Live Search支援被視為是測試版，因為並非所有PWA都已通過測試 [!DNL Live Search]。 基本功能（如搜索和產品清單頁面）在Venia中工作，但Graphql的某些排列可能無法正確工作。

* 當前的BetaPWA實現 [!DNL Live Search] 返回搜索結果所需的處理時間比 [!DNL Live Search] 和本地商業店。
* [!DNL Live Search] 在PWA不支援 [事件處理](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/)。
* 直接篩選 `description`。 `name`。 `short_description` 使用時不受GraphQL支援 [PWA](https://developer.adobe.com/commerce/pwa-studio/)，但返回時帶有更一般的篩選器。

### 當前不支援

* 的 [高級搜索](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) 模組在 [!DNL Live Search] 已安裝，並且會刪除店面頁腳中的「高級搜索」連結。
* 使用的多個庫存庫位 [MCOM](https://experienceleague.adobe.com/docs/commerce-admin/systems/integrations/mcom.html) 或其他OMS擴展
* 產品價格不包括 [增值稅](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/taxes/vat.html) （增值稅）。
* [層價](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-tier.html) 在「即時搜索跨距」和「產品清單」頁面小部件中不支援。

## Cookie

[!DNL Live Search] 收集用戶交互資料作為其基本功能的一部分，並使用cookie儲存此資料。 收集任何用戶資訊時，用戶必須同意儲存cookie。 [!DNL Live Search] 和 [!DNL Product Recommendations] 共用資料流，因此共用相同的cookie機制。 在中閱讀有關它的詳細資訊 [處理Cookie限制](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie.html)。
