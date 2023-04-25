---
title: 「入門概述」
description: '"[!DNL Live Search] 入門流程、系統需求、界限和限制」'
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
source-git-commit: 86e6fdb653278f3e70640155d697897a2ea1b674
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# 入門概述

若要開始使用 [!DNL Live Search] 若為Adobe Commerce，請完成入門程式以安裝擴充功能、設定API金鑰，以及同步您的目錄。

## 上線流程

![[!DNL Live Search] 入門圖](assets/onboarding-flow.svg)

## 需求 {#requirements}

* [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+
* PHP 8.1 / 8.2
* [!DNL Composer]

### 支援平台

* Adobe Commerce內部部署(EE):2.4.4+
* Adobe Commerce on Cloud(ECE):2.4.4+

## 邊界和閾值

目前， [!DNL Live Search] search/category API有下列支援的限制和靜態界限：

### 索引

* 每個商店檢視索引最多300個產品屬性。
* 僅從Adobe Commerce資料庫中索引產品。
* 產品必須位於預設共用目錄中。
* CMS頁面未編列索引。

### 查詢

* [!DNL Live Search] 無法存取類別樹的完整分類，這會導致部分分層導覽搜尋案例超出其範圍。
* [!DNL Live Search] 使用唯一的GraphQL端點來進行查詢，以支援動態facet和「隨您類型搜尋」等功能。 雖然類似 [GraphQL API](https://developer.adobe.com/commerce/webapi/graphql/)，則會有一些差異，而有些欄位可能不完全相容。

若要使用目錄權限限制客戶群組：

* 必須將產品指派給根類別。
* 必須為「未登入」客戶群組授予「允許」瀏覽權限。
* 若要將產品限制在「未登入」客戶群組，請前往每個類別，並設定每個客戶群組的權限。

### 規則

* 每個商店檢視的規則數上限為50。
* 每個規則的條件數上限為10。
* 每個規則的事件數上限為25。

### 同義字

* [!DNL Live Search] 每個商店檢視最多可管理200個同義字。

## 價格索引器

Live Search客戶可以使用 [SaaS價格索引器](../price-index/index.md)，提供更快的價格更新和同步時間。

### PWA支援

「即時搜尋」支援會視為測試版，因為並非所有PWA都已透過測試 [!DNL Live Search]. 搜尋和產品清單頁面等基本功能可在Venia中運作，但Graphql的某些設定可能無法正常運作。

* 目前的測試版PWA實作 [!DNL Live Search] 傳回搜尋結果的處理時間比 [!DNL Live Search] 與原生商務店面。
* [!DNL Live Search] PWA不支援 [事件處理](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).
* 直接篩選 `description`, `name`, `short_description` GraphQL不支援搭配使用 [PWA](https://developer.adobe.com/commerce/pwa-studio/)，但會以較一般的篩選器傳回。

### 目前不支援

* 此 [進階搜尋](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) 模組在 [!DNL Live Search] 已安裝，且店面頁尾中的「進階搜尋」連結會遭到移除。
* 使用的多個庫存位置 [MCOM](https://experienceleague.adobe.com/docs/commerce-admin/systems/integrations/mcom.html) 或其他OMS擴充功能
* 產品價格不包括 [增值稅](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/taxes/vat.html) （增值稅）。
* [層價](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-tier.html) 即時搜尋彈出視窗和產品清單頁面Widget中不支援。

## Cookie

[!DNL Live Search] 將使用者互動資料收集為其基本功能的一部分，並使用cookie來儲存此資料。 收集任何使用者資訊時，使用者必須同意儲存Cookie。 [!DNL Live Search] 和 [!DNL Product Recommendations] 共用資料流，因此會使用相同的cookie機制。 請參閱 [處理Cookie限制](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie.html).
