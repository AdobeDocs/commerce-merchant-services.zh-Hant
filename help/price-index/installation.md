---
title: SaaS Price Indexing手動安裝
description: 安裝舊版的SaaS價格索引
seo-title: SaaS Price Indexing installation
seo-description: Installing SaaS Price indexing
exl-id: a607e852-aa04-4be3-9576-a6bf45f8751f
role: Admin, Developer
source-git-commit: be0b8f4c26f11c31da3e5422bb4f4c4af10f2a00
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# SaaS Price Indexing手動安裝

SaaS價格索引現成可供支援 [最新版本](index.md#Requirements) Commerce Services的。
如果您沒有最新版本，並且想要為您的Adobe Commerce執行個體啟用SaaS價格索引，請使用這個迷你指南。

## 必要條件

* Adobe Commerce 2.4.4+
* 至少已安裝下列其中一個SaaS服務：

   * [目錄服務](../catalog-service/overview.md)
   * [即時搜尋](../live-search/guide-overview.md)
   * [產品Recommendations](../product-recommendations/guide-overview.md)

## 安裝必要模組

根據您的設定，安裝程式可能會稍微不同。
有些擴充功能會新增摘要和支援程式碼，有些擴充功能會移除預設價格摘要。

1. 將下列模組新增至 `composer.json` 檔案：

   ```json
   "magento/module-saas-price": "^102.2.0",
   "magento/module-saas-scopes": ^"102.2.0",
   "magento/module-product-override-price-remover": "^102.2.0",
   "magento/module-bundle-product-override-data-exporter": "^102.2.0",
   ```

1. 執行升級命令：

   ```bash
   bin/magento setup:upgrade
   ```

升級之後，提供三個新摘要：

* `prices`  — 負責將價格資料遞送至服務
* `scopesCustomerGroup`  — 負責將客戶群組交付至服務
* `scopesWebsite`  — 負責將網站、商店群組和商店檢視傳送至服務


1. 將新摘要設定為「依排程更新」模式：

   ```bash
   bin/magento indexer:set-mode schedule catalog_data_exporter_product_prices scopes_customergroup_data_exporter scopes_website_data_exporter
   ```

1. 重新索引新的摘要：

   ```bash
   bin/magento saas:resync --feed=scopesCustomerGroup
   bin/magento saas:resync --feed=scopesWebsite
   bin/magento saas:resync --feed=prices
   ```

視需要手動執行上述索引子。 否則，資料會在標準同步程式中重新整理。 深入瞭解 [目錄同步](../landing/catalog-sync.md) 服務。


Luma和Adobe Commerce Core GraphQL使用者可安裝 [`Catalog Adapter`](catalog-adapter.md) 此擴充功能提供Luma和核心GraphQl相容性，並停用Adobe Commerce產品價格索引器。

## 警告

早於 `103.0.0` 版本、SaaS價格索引支援簡單、分組、虛擬、可設定和套裝動態產品型別。
可下載專案、禮品卡和套裝固定產品型別的支援開始於 `magento/module-saas-price:103.0.0` 版本並可立即用於支援的Commerce服務。

新的摘要應手動與同步 `resync` [CLI命令](../landing/catalog-sync.md#resynccmdline). 否則，資料會在標準同步程式中重新整理。 取得更多關於 [目錄同步](../landing/catalog-sync.md) 程式。