---
title: 「入門概述」
description: '"[!DNL Live Search] 入門流程、系統要求、界限和限制」'
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
source-git-commit: 484319fc1df6c29c972b57c13bd0ed711e374e99
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# 入門概述

若要開始使用 [!DNL Live Search] 若為Adobe Commerce，請完成入門程式以安裝擴充功能、設定API金鑰，以及同步您的目錄。

## 上線流程

![[!DNL Live Search] 入門圖](assets/onboarding-flow.svg)

## 需求 {#requirements}

* [Adobe Commerce](https://magento.com/products/magento-commerce) 2.4.4+
* PHP 8.1、8.2
* [!DNL Composer]

### 支援平台

* Adobe Commerce on prem(EE):2.4.4+
* Adobe Commerce on Cloud(ECE):2.4.4+

## 邊界和閾值

此時， [!DNL Live Search] search/category API有下列支援的限制和靜態界限：

### 索引

* 每個商店檢視索引最多300個產品屬性。
* 僅從Adobe Commerce資料庫中索引產品。
* CMS頁面未編列索引。

### 查詢

* [!DNL Live Search] 無法存取類別樹的完整分類，這會導致部分分層導覽搜尋案例超出其範圍。
* [!DNL Live Search] 使用唯一的GraphQL端點進行查詢，以支援智慧型facet和「隨您搜尋」等功能。 雖然類似 [MagentoGraphQL API](https://developer.adobe.com/commerce/webapi/graphql/)，則會有一些差異，而目前某些欄位可能不完全相容。

### 規則

* 每個商店檢視的規則數上限為50。
* 每個規則的條件數上限為10。
* 每個規則的事件數上限為25。

### 同義字

* [!DNL Live Search] 每個商店檢視最多可管理200個同義字。

### PWA測試版

* 與原生Commerce店面的Live Search相比，目前Live Search測試版PWA實作傳回搜尋結果的處理時間更長。
* 測試版PWA [!DNL Live Search] 不支援 [事件處理](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).
* GraphQL不支援下列產品屬性，因為它用於 [PWA](https://developer.adobe.com/commerce/pwa-studio/): `description`, `name`, `short_description`

### 目前不支援

* 此 [進階搜尋](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) 模組在 [!DNL Live Search] 已安裝，且店面頁尾中的「進階搜尋」連結會遭到移除。
* [自訂價格群組](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-group.html)
* 使用的多個庫存位置 [MCOM](https://experienceleague.adobe.com/docs/commerce-admin/systems/integrations/mcom.html) 或其他OMS擴充功能
* 產品價格不包括 [增值稅](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/taxes/vat.html) （增值稅）。
