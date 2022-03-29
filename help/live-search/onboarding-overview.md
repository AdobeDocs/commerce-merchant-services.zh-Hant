---
title: 入門概述
description: Live Search on Boonding流、系統要求、邊界和限制
source-git-commit: 6220824c6032a33a760fe5c2bb5d2346e00a074b
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# 登機概述

要開始使用Live Search forAdobe Commerce，您必須完成一些入門步驟以安裝擴展、配置API密鑰和同步目錄。

## 登機流

![Live Search onboard圖](assets/onboarding-flow.svg)

## 要求 {#requirements}

* [Adobe Commerce](https://magento.com/products/magento-commerce) 2.4.x
* 7.3菲律賓比索/7.4
* [!DNL Composer]

### 支援的平台

* Adobe Commerce在prem(EE):2.4.x
* Adobe Commerce雲(ECE):2.4.x

## 邊界和閾值

此時， Live Search搜索/類別API具有以下支援的限制和靜態邊界：

### 索引

* 每個儲存視圖索引最多300個產品屬性
* 僅索引Adobe Commerce資料庫中的產品
* 不為CMS頁編製索引

### 查詢限制

* Live Search無權訪問類別樹的完整分類，這使得某些分層導航搜索方案超出其範圍。
* Live Search使用唯一的GraphQL終結點進行查詢以支援智慧分頁和按類型搜索等功能。 雖然與 [MagentoGraphQL API](https://devdocs.magento.com/guides/v2.4/graphql)，存在一些差異，有些欄位可能目前不完全相容。

### PWABeta版

* Live Search的PWA測試版不支援 [事件處理](https://devdocs.magento.com/shared-services/storefront-events-sdk.html)。
* GraphQL在與Beta版本相關時不支援以下產品屬性 [PWA](https://developer.adobe.com/commerce/pwa-studio/): `description`。 `name`。 `short_description`

### 此時不支援

* 的 [高級搜索](https://docs.magento.com/user-guide/catalog/search-advanced.html) 安裝Live Search時，模組被禁用，並且刪除了店面頁腳中的「高級搜索」連結。
* [客戶組](https://docs.magento.com/user-guide/customers/customer-groups.html)
* [自定義價格組](https://docs.magento.com/user-guide/catalog/product-price-group.html)
* 使用的多個庫存庫位 [MCOM](https://docs.magento.com/user-guide/mcom.html) 或其他OMS擴展
* [整合B2B功能](https://business.adobe.com/products/magento/b2b-ecommerce.html)
