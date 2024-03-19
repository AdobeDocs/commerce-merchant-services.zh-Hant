---
title: 「安裝 [!DNL Live Search]"
description: 「瞭解如何安裝、更新及解除安裝 [!DNL Live Search] 來自Adobe Commerce。」
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
role: Admin, Developer
source-git-commit: e8d4215b1f16f1cb34783674cabc046dec135729
workflow-type: tm+mt
source-wordcount: '1217'
ht-degree: 0%

---

# 安裝 [!DNL Live Search]

[!DNL Live Search] 會從Adobe Marketplace安裝為擴充功能。 在 [!DNL Live Search] 模組（以目錄模組為相依性）已安裝並設定， [!DNL Commerce] 開始與SaaS服務共用搜尋和目錄資料。 此時， *管理員* 使用者可以設定、自訂及管理搜尋Facet、同義字和銷售規則。

本主題提供執行下列動作的指示：

* 安裝 [!DNL Live Search] （方法1和2）
* [更新 [!DNL Live Search]](#update)
* [解除安裝 [!DNL Live Search]](#uninstall)

## 開始之前 {#before-you-begin}

執行下列動作：

1. 確認 [cron工作](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) 和 [索引子](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) 執行中。

1. 選擇符合您需求的入門方法，然後依照指示操作。

   * [方法1](#method-1)：不執行安裝 [!DNL OpenSearch]
   * [方法2](#method-2)：安裝方式 [!DNL OpenSearch] （無停機時間）

>[!IMPORTANT]
>
>由於Elasticsearch7於2023年8月宣佈終止支援，建議所有Adobe Commerce客戶移轉至OpenSearch 2.x搜尋引擎。 如需在產品升級期間移轉搜尋引擎的相關資訊，請參閱 [移轉至OpenSearch](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/opensearch-migration) 在 _升級指南_.

## 方法1：不使用OpenSearch安裝 {#method-1}

安裝時，建議使用此上線方法 [!DNL Live Search] 至：

* 新增 [!DNL Commerce] 安裝
* 中繼環境

此情境中，店面作業在下列情況下會中斷： [!DNL Live Search] 服務會為目錄中的所有產品編制索引。 在安裝期間， [!DNL Live Search] 模組已啟用且 [!DNL OpenSearch] 模組已停用。

1. 安裝Adobe Commerce 2.4.4+ （不含） [!DNL Live Search].

1. 若要下載 `live-search` 封裝，從命令列執行下列動作：

   ```bash
   composer require magento/live-search
   ```

1. 執行以下命令以停用 [!DNL OpenSearch] 和相關模組，以及安裝 [!DNL Live Search]：

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch7 Magento_OpenSearch Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   >[!WARNING]
   >
   > 當資料已編制索引並同步時，店面中無法使用搜尋和類別瀏覽操作。 根據目錄的大小，程式可能需要至少一個小時的時間 `cron` 執行以將您的資料同步到 [!DNL Live Search] 服務。

1. 確認下列事項 [索引子](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) 設為「依排程更新」：

   * 產品摘要
   * 產品變體摘要
   * 目錄屬性摘要
   * 產品價格摘要
   * 範圍網站資料摘要
   * 範圍客戶群組資料摘要
   * 類別摘要
   * 類別許可權摘要

1. 設定您的 [API金鑰](#configure-api-keys) 並確認您的目錄資料為 [已同步](#synchronize-catalog-data) 替換為 [!DNL Live Search] 服務。

1. 若要讓多面在店面中成為可用篩選器，請新增 [Facet](facets-add.md) 您需要，根據 [多面向需求](facets.md).

   之後您應該能夠新增Facet `cron` 執行屬性摘要和匯出屬性中繼資料。

1. 請依此順序執行下列命令：

   ```bash
   bin/magento saas:resync --feed productattributes
   bin/magento saas:resync --feed products
   bin/magento saas:resync --feed scopesCustomerGroup
   bin/magento saas:resync --feed scopesWebsite
   bin/magento saas:resync --feed prices
   bin/magento saas:resync --feed productoverrides
   bin/magento saas:resync --feed variants
   bin/magento saas:resync --feed categories
   bin/magento saas:resync --feed categoryPermissions
   ```

1. [驗證](#verify-export) 已匯出資料。

1. [測試](#test-the-connection) 店面的連線。

## 方法2：使用OpenSearch安裝 {#method-2}

安裝時，建議使用此上線方法 [!DNL Live Search] 至：

* 現有的生產環境 [!DNL Commerce] 安裝

在此案例中， [!DNL OpenSearch] 暫時管理店面的搜尋請求，而 [!DNL Live Search] 服務會在背景編制所有產品的索引，不會中斷一般店面的作業。 [!DNL OpenSearch] 已停用，並且 [!DNL Live Search] 在所有目錄資料編制索引並同步之後啟用。

1. 若要下載 `live-search` 封裝，從命令列執行下列動作：

   ```bash
   composer require magento/live-search
   ```

1. 執行以下命令以暫時停用 [!DNL Live Search] 提供店面搜尋結果的模組。

   ```bash
   bin/magento module:disable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover Magento_LiveSearchProductListing 
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   [!DNL Elasticsearch] 持續管理店面的搜尋請求，同時 [!DNL Live Search] 服務會在背景同步目錄資料和索引產品。

1. 確認下列事項 [索引子](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) 設為「依排程更新」：

   * 產品摘要
   * 產品變體摘要
   * 目錄屬性摘要
   * 產品價格摘要
   * 範圍網站資料摘要
   * 範圍客戶群組資料摘要

1. 設定您的 [API金鑰](#configure-api-keys) 並確認您的目錄資料為 [已同步](#synchronize-catalog-data) 替換為 [!DNL Live Search] 服務。

1. 若要讓多面在店面中成為可用篩選器，請新增 [Facet](facets-add.md) 您需要，根據 [多面向需求](facets.md).

   之後您應該能夠新增Facet `cron` 執行產品和屬性摘要，並將屬性中繼資料匯出至 [!DNL Live Search] 服務。

1. 請依此順序執行下列命令：

   ```bash
   bin/magento saas:resync --feed productattributes
   bin/magento saas:resync --feed products
   bin/magento saas:resync --feed scopesCustomerGroup
   bin/magento saas:resync --feed scopesWebsite
   bin/magento saas:resync --feed prices
   bin/magento saas:resync --feed productoverrides
   bin/magento saas:resync --feed variants
   bin/magento saas:resync --feed categories
   bin/magento saas:resync --feed categoryPermissions
   ```

1. 同步完成後，請使用 [GraphQL遊樂場](https://developer.adobe.com/commerce/services/graphql/live-search/) 預設查詢，以驗證以下內容：

   * 傳回的產品計數接近您對商店檢視的預期。
   * 已傳回Facet。

1. 執行以下命令以啟用 [!DNL Live Search] 模組，停用 [!DNL OpenSearch]，並執行 `setup`.

   ```bash
   bin/magento module:enable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover  Magento_LiveSearchProductListing 
   ```

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch6 Magento_Elasticsearch7 Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch 
   Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   ```bash
   bin/magento setup:upgrade
   ```

1. [測試](#test-the-connection) 店面的連線。

## 設定API金鑰 {#configure-api-keys}

需要Adobe Commerce API金鑰及其關聯的私密金鑰才能連線 [!DNL Live Search] Adobe Commerce的安裝。 API金鑰是在的帳戶中產生和維護 [!DNL Commerce] 授權持有者，可與開發人員或SI共用。 開發人員可以代表授權持有人建立和管理SaaS資料空間。  如果您已經有一組API金鑰，則不需要重新產生。

### Adobe Commerce授權持有者

若要產生API金鑰和私密金鑰，請參閱 [Commerce服務聯結器](../landing/saas.md).

### Adobe Commerce開發人員或SI

開發人員或SI會設定SaaS資料空間，如 *Commerce服務* 區段。 在 *管理員*，則Commerce Services可在以下位置使用： *設定* 安裝SaaS模組時顯示的側欄。

## 同步目錄資料 {#synchronize-catalog-data}

[!DNL Live Search] 搜尋作業需要同步化的產品資料，而且需要同步化的屬性資料才能設定Facet。 產品目錄與目錄服務之間的初始同步始於 [!DNL Live Search] 是第一次連線。 視目錄的安裝方法和大小而定，最多可能需要30分鐘的時間來匯出資料並編制索引。 [!DNL Live Search]. 可以在結構描述中找到與目錄服務同步和共用的資料清單，該結構描述定義於：

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

### 驗證匯出 {#verify-export}

驗證目錄資料是否已從您的Adobe Commerce執行個體匯出並同步 [!DNL Live Search]，請在下清單格中尋找專案：

* `catalog_data_exporter_products`
* `catalog_data_exporter_product_attributes`

如需其他說明，請參閱 [[!DNL Live Search] 目錄未同步](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-catalog-data-sync) 位於支援知識庫中。

### 未來的產品更新

初始同步後，增量產品更新最多可能需要15分鐘才能用於店面搜尋。 若要進一步瞭解，請前往 [索引 — 串流產品更新](indexing.md).

## 測試連線 {#test-connection}

在店面，驗證以下內容：

* 此 [!UICONTROL Search] 方塊會正確傳回結果
* 類別瀏覽正確傳回結果
* Facet在搜尋結果頁面上可作為篩選使用

如果一切正常運作，恭喜您！ [!DNL Live Search] 已安裝、連線且隨時可使用。

如果您在店面中遇到問題，請檢查 `var/log/system.log` API通訊失敗或服務端錯誤的檔案。

若要允許即時搜尋通過防火牆，請新增 `commerce.adobe.io` 至允許清單。

## 正在檢查安裝的版本

在更新Live Search之前，請從命令列執行下列操作以檢查已安裝的Live Search版本：

```bash
composer show magento/module-live-search | grep version
```

## 正在更新 [!DNL Live Search] {#update}

更新 [!DNL Live Search]，從命令列執行以下命令：

```bash
composer update magento/live-search --with-dependencies
```

若要更新至主要版本，例如從3.1.1到4.0.0，請編輯專案的根目錄 [!DNL Composer] `.json` 檔案如下所示：

1. 若您目前已安裝 `magento/live-search` 版本為 `3.1.1` 或更低版本，而您正升級至版本 `4.0.0` 或更高版本，請在升級之前執行以下命令：

   ```bash
   bin/magento module:enable Magento_AdvancedSearch
   ```

   有關目前安裝的資訊 `magento/live-search` 版本，執行以下命令：

   ```bash
   composer show magento/live-search
   ```

1. 開啟根 `composer.json` 檔案和搜尋 `magento/live-search`.

1. 在 `require` 區段，更新版本號碼，如下所示：

   ```json
   "require": {
      ...
      "magento/live-search": "^4.0",
      ...
    }
   ```

1. **儲存** `composer.json`. 然後，從命令列執行下列動作：

   ```bash
   composer update magento/live-search --with-dependencies
   ```

## 解除安裝 [!DNL Live Search] {#uninstall}

若要解除安裝 [!DNL Live Search]，請參閱 [解除安裝模組](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall-modules).

## [!DNL Live Search] 套件 {#packages}

| 封裝 | 說明 |
|--- |--- |
| `module-live-search` | 可讓商家針對多面向、同義字、查詢規則等設定其搜尋設定，並提供對唯讀GraphQL遊樂場的存取權，以測試來自 *管理員*. |
| `module-live-search-adapter` | 將搜尋要求從店面路由至 [!DNL Live Search] 服務，並在店面中呈現結果。 <br /> — 類別瀏覽 — 路由店面的請求 [上層導覽](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/navigation/navigation-top) 至搜尋服務。<br /> — 全域搜尋 — 路由來自下列專案的請求： [快速搜尋](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) 方塊位於店面右上角的 [!DNL Live Search] 服務。 |
| `module-live-search-storefront-popover` | 「依輸入方式搜尋」彈出視窗會取代標準快速搜尋，並傳回熱門搜尋結果的資料和縮圖。 |

## [!DNL Live Search] 相依性 {#dependencies}

下列專案 [!DNL Live Search] 相依性擷取自 [!DNL Composer].

* `magento/module-saas-catalog`
* `magento/module-saas-category`
* `magento/module-saas-category-permissions`
* `magento/module-saas-product-override`
* `magento/module-saas-product-variant`
* `magento/module-saas-price`
* `magento/module-saas-scopes`
* `magento/module-bundle-product-data-exporter`
* `magento/module-catalog-inventory-data-exporter`
* `magento/module-catalog-url-rewrite-data-exporter`
* `magento/module-configurable-product-data-exporter`
* `magento/module-parent-product-data-exporter`
* `magento/module-gift-card-product-data-exporter`
* `magento/module-bundle-product-override-data-exporter`
* `data-services`
* `services-id`
