---
title: SaaS價格索引安裝
description: 安裝SaaS價格索引
seo-title: SaaS Price Indexing installation
seo-description: Installing SaaS Price indexing
source-git-commit: 077be6d893b800b9571a869237501e58accc01e8
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# SaaS價格索引安裝

要設定SaaS價格索引，必須安裝新模組並運行CLI命令。 管理員需要命令列存取權才能完成此安裝。

## 必要條件

* Adobe Commerce 2.4.4+
* 至少安裝了以下SaaS服務之一：

   * [目錄服務](../catalog-service/overview.md)
   * [即時搜尋](../live-search/guide-overview.md)
   * [產品Recommendations](../product-recommendations/guide-overview.md)

## 安裝所需模組

根據您的設定，安裝程式可能會稍有不同。
有些擴充功能會新增新摘要和支援代碼，有些擴充功能會移除預設價格摘要。

1. 將下列模組新增至您的 `composer.json` 檔案：

   ```json
   "magento/module-saas-price": "102.2.0",
   "magento/module-saas-scopes": "102.2.0",
   "magento/module-product-override-price-remover": "102.2.0",
   "magento/module-bundle-product-override-data-exporter": "102.2.0",
   ```

1. 運行升級命令：

   ```bash
   bin/magento setup:upgrade
   ```

升級後，可使用三個新摘要：

* `prices`  — 負責將價格資料提供給服務
* `scopesCustomerGroup`  — 負責將客戶組交付到服務
* `scopesWebsite`  — 負責將網站、商店群組和商店檢視傳送至服務


1. 將新摘要設為「依排程更新」模式：

   ```bash
   bin/magento indexer:set-mode schedule catalog_data_exporter_product_prices scopes_customergroup_data_exporter scopes_website_data_exporter
   ```

1. 重新索引新摘要：

   ```bash
   bin/magento saas:resync --feed=scopesCustomerGroup
   bin/magento saas:resync --feed=scopesWebsite
   bin/magento saas:resync --feed=prices
   ```

視需要手動執行上述索引器。 否則，資料會在標準同步程式中重新整理。 深入了解 [目錄同步](../landing/catalog-sync.md) 服務。

Luma和Adobe Commerce Core GraphQL使用者可以安裝 `catalog-adapter` 提供Luma和Core GraphQl相容性並禁用PHP核心價格索引器的模組。
若要使用 `catalog-adapter` 模組， [!DNL Live Search] 必須先安裝。 關注 [安裝 [!DNL Live Search]](../live-search/install.md) 說明，再繼續。

```bash
composer require adobe-commerce/catalog-adapter
```

如果需要，可以使用以下命令重新啟用PHP核心價格索引器：

```bash
bin/magento module:disable Magento_PriceIndexerDisabler
```
