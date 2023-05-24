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

設定SaaS價格索引需要安裝新模組並執行CLI命令。 管理員需要命令列存取權才能完成此安裝。

## 必要條件

* Adobe Commerce 2.4.4+
* 至少已安裝下列其中一個SaaS服務：

   * [目錄服務](../catalog-service/overview.md)
   * [即時搜尋](../live-search/guide-overview.md)
   * [產品Recommendations](../product-recommendations/guide-overview.md)

## 安裝必要的模組

視您的設定而定，安裝程式可能會稍有不同。
有些擴充功能會新增摘要和支援程式碼，有些擴充功能會移除預設價格摘要。

1. 將下列模組新增至 `composer.json` 檔案：

   ```json
   "magento/module-saas-price": "102.2.0",
   "magento/module-saas-scopes": "102.2.0",
   "magento/module-product-override-price-remover": "102.2.0",
   "magento/module-bundle-product-override-data-exporter": "102.2.0",
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

視需要手動執行上述索引器。 否則，資料會在標準同步程式中重新整理。 深入瞭解 [目錄同步](../landing/catalog-sync.md) 服務。

Luma和Adobe Commerce Core GraphQL使用者可以安裝 `catalog-adapter` 提供Luma和核心GraphQl相容性並停用PHP核心價格索引器的模組。
若要使用 `catalog-adapter` 模組， [!DNL Live Search] 和 [!DNL Catalog Service] 必須先安裝及設定。 請遵循 [安裝 [!DNL Live Search]](../live-search/install.md) 和 [目錄服務安裝](../catalog-service/installation.md) 指示後再繼續。

若要設定「即時搜尋和目錄轉接器」，請依照 [商務服務聯結器](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html?lang=en) 指示。

```bash
composer require adobe-commerce/catalog-adapter
```

如有需要，可以使用以下指令重新啟用PHP核心價格索引器：

```bash
bin/magento module:disable Magento_PriceIndexerDisabler
```
