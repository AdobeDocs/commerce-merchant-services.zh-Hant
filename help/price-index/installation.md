---
title: SaaS價格索引安裝
description: 安裝SaaS價格索引
seo-title: SaaS Price Indexing installation
seo-description: Installing SaaS Price indexing
exl-id: a607e852-aa04-4be3-9576-a6bf45f8751f
source-git-commit: 3820736a25942b147d6e2c7b8820c360d6a0a535
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---

# SaaS價格索引安裝

設定SaaS價格索引需要安裝新模組並運行CLI命令。 管理員需要命令行訪問才能完成此安裝。

## 先決條件

* Adobe Commerce2.4.4+
* 至少安裝了下列SaaS服務之一：

   * [目錄服務](../catalog-service/overview.md)
   * [即時搜索](../live-search/guide-overview.md)
   * [產品Recommendations](../product-recommendations/guide-overview.md)

## 安裝所需模組

根據您的設定，安裝過程可能略有不同。
有些擴展可添加新源和支援代碼，還有一個擴展可刪除預設價格源。

1. 將以下模組添加到 `composer.json` 檔案：

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

升級後，可以使用三個新源：

* `prices`  — 負責向服務提供價格資料
* `scopesCustomerGroup`  — 負責將客戶組交付到服務
* `scopesWebsite`  — 負責將網站、儲存組和儲存視圖交付到服務


1. 將新源配置為「按計畫更新」模式：

   ```bash
   bin/magento indexer:set-mode schedule catalog_data_exporter_product_prices scopes_customergroup_data_exporter scopes_website_data_exporter
   ```

1. 重新索引新源：

   ```bash
   bin/magento saas:resync --feed=scopesCustomerGroup
   bin/magento saas:resync --feed=scopesWebsite
   bin/magento saas:resync --feed=prices
   ```

根據需要手動運行以上索引器。 否則，在標準同步過程中刷新資料。 閱讀有關 [目錄同步](../landing/catalog-sync.md) 服務。

Luma和Adobe Commerce核心GraphQL用戶可以安裝 `catalog-adapter` 提供Luma和Core GraphQl相容性並禁用PHP核心價格索引器的模組。
使用 `catalog-adapter` 模組， [!DNL Live Search] 和 [!DNL Catalog Service] 必須先安裝和配置。 關注 [安裝 [!DNL Live Search]](../live-search/install.md) 和 [目錄服務安裝](../catalog-service/installation.md) 說明，然後繼續。

要配置Live Search和Catalog Adapter，請遵循 [Commerce Services連接器](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html?lang=en) 的下界。

```bash
composer require adobe-commerce/catalog-adapter
```

如果需要，可以使用以下命令重新啟用PHP核心價格索引器：

```bash
bin/magento module:disable Magento_PriceIndexerDisabler
```
