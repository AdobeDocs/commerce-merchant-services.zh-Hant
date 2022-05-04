---
title: 入門概述
description: Live Search on Boonding流、系統要求、邊界和限制
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
source-git-commit: 66ffbf2576615bb1f6015a13c65af86e8d7ea700
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 入門概述

開始使用 [!DNL Live Search] 對於Adobe Commerce，完成登錄過程以安裝擴展、配置API密鑰和同步目錄。

## 登機流

![[!DNL Live Search] 附圖](assets/onboarding-flow.svg)

## 要求 {#requirements}

* [Adobe Commerce](https://magento.com/products/magento-commerce) 2.4.x
* 7.3菲律賓比索/7.4/8.1
* [!DNL Composer]

### 支援的平台

* Adobe Commerce在prem(EE):2.4.x
* Adobe Commerce雲(ECE):2.4.x

## 邊界和閾值

此時， [!DNL Live Search] search/category API具有以下受支援的限制和靜態邊界：

### 索引

* 每個儲存視圖索引最多300個產品屬性
* 僅索引Adobe Commerce資料庫中的產品
* 不為CMS頁編製索引

### 同義詞

* [!DNL Live Search] 每個同義詞最多可管理200個同義詞 `Data Space ID`。

### 查詢

* [!DNL Live Search] 無權訪問類別樹的完整分類，這使得某些分層導航搜索方案超出其範圍。
* [!DNL Live Search] 使用唯一的GraphQL終結點進行查詢以支援智慧分頁和按類型搜索等功能。 雖然與 [MagentoGraphQL API](https://devdocs.magento.com/guides/v2.4/graphql)，存在一些差異，有些欄位可能目前不完全相容。

### PWABeta版

* 與Live Search與本地Commerce商店相比， Live Search的當前BetaPWA實現需要更多的處理時間來返回搜索結果。
* PWA的β釋放 [!DNL Live Search] 不支援 [事件處理](https://devdocs.magento.com/shared-services/storefront-events-sdk.html)。
* GraphQL在與Beta版本相關時不支援以下產品屬性 [PWA](https://developer.adobe.com/commerce/pwa-studio/): `description`。 `name`。 `short_description`

### 此時不支援

* 的 [高級搜索](https://docs.magento.com/user-guide/catalog/search-advanced.html) 模組在 [!DNL Live Search] 已安裝，並且會刪除店面頁腳中的「高級搜索」連結。
* [客戶組](https://docs.magento.com/user-guide/customers/customer-groups.html)
* [自定義價格組](https://docs.magento.com/user-guide/catalog/product-price-group.html)
* 使用的多個庫存庫位 [MCOM](https://docs.magento.com/user-guide/mcom.html) 或其他OMS擴展
* [整合B2B功能](https://business.adobe.com/products/magento/b2b-ecommerce.html)
* 產品價格不包括 [增值稅](https://docs.magento.com/user-guide/tax/vat.html) （增值稅）。
* 無論在哪些情況下， [股票期權](https://docs.magento.com/user-guide/catalog/inventory-options-global.html) 配置。
