---
title: 「安裝 [!DNL Live Search]"
description: 「瞭解如何安裝、更新和解除安裝 [!DNL Live Search] 來自Adobe Commerce。」
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
source-git-commit: 8b57f2269ae13033f26c0e5e468bc35ce9deaf9f
workflow-type: tm+mt
source-wordcount: '1287'
ht-degree: 0%

---

# 安裝 [!DNL Live Search]

[!DNL Live Search] 會安裝為Adobe Marketplace的擴充功能。 晚於 [!DNL Live Search] 模組（以目錄模組為相依性）已安裝並設定， [!DNL Commerce] 開始與SaaS服務共用搜尋和目錄資料。 此時， *管理員* 使用者可以設定、自訂及管理搜尋Facet、同義字和銷售規則。

本主題提供執行下列操作的指示：

* 安裝 [!DNL Live Search] （方法1和2）
* [更新 [!DNL Live Search]](#update)
* [解除安裝 [!DNL Live Search]](#uninstall)

## 開始之前 {#before-you-begin}

執行下列動作：

1. 確認 [cron工作](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) 和 [索引子](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) 執行中。

1. 選擇符合您需求的入門方法，然後依照指示操作。

   * [方法1](#method-1)：不透過以下方式安裝 [!DNL Elasticsearch]
   * [方法2](#method-2)：安裝方式 [!DNL Elasticsearch] （無停機時間）

## 方法1：不使用Elasticsearch安裝 {#method-1}

安裝時建議使用此上線方法 [!DNL Live Search] 至：

* 新增 [!DNL Commerce] 安裝
* 中繼環境

在此案例中，店面作業在下列情況下中斷： [!DNL Live Search] 服務會為目錄中的所有產品編制索引。 在安裝期間， [!DNL Live Search] 模組已啟用且 [!DNL Elasticsearch] 模組已停用。

>[!NOTE]
>
>自2023年3月起，「即時搜尋」僅支援2.4.4版及更高版本。

1. 安裝Adobe Commerce 2.4.4+ （不含） [!DNL Live Search].

1. 若要下載 `live-search` 封裝，從命令列執行以下命令：

   ```bash
   composer require magento/live-search
   ```

   如需詳細資訊，請參閱 [!DNL Live Search] [相依性](#dependencies) 擷取者： [!DNL Composer].

1. 執行以下命令以停用 [!DNL Elasticsearch] 和相關模組，以及安裝 [!DNL Live Search]：

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch7 Magento_OpenSearch Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   >[!WARNING]
   >
   > 當資料已編制索引並同步化時，店面中無法使用搜尋和類別瀏覽操作。 視目錄大小而定，此程式可能至少需要一小時的時間 `cron` 執行以將您的資料同步到 [!DNL Live Search] 服務。

1. 確認下列各項 [索引子](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) 設為 `Update by Schedule`：

   * 產品摘要
   * 產品變體資訊源
   * 目錄屬性摘要

1. 設定您的 [API金鑰](#configure-api-keys) 並確認您的目錄資料為 [已同步](#synchronize-catalog-data) 替換為 [!DNL Live Search] 服務。

1. 若要讓Facet在店面中成為可用篩選器，請新增 [Facet](facets-add.md) 您需要，根據 [多面向需求](facets.md).

   之後您應該能夠新增Facet `cron` 執行屬性摘要和匯出屬性中繼資料。

1. 之後至少等待一小時 `cron` 執行以同步資料。 然後， [驗證](#verify-export) 已匯出資料。

1. [測試](#test-the-connection) 店面的連線。

## 方法2：使用Elasticsearch安裝 {#method-2}

>[!IMPORTANT]
>
>鑑於2023年8月Elasticsearch7的支援終止公告，建議所有Adobe Commerce客戶移轉至OpenSearch 2.x搜尋引擎。 如需在產品升級期間移轉搜尋引擎的相關資訊，請參閱 [移轉至OpenSearch](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/prepare/opensearch-migration.html) 在 _升級指南_.

安裝時建議使用此上線方法 [!DNL Live Search] 至：

* 現有的生產環境 [!DNL Commerce] 安裝

在此案例中， [!DNL Elasticsearch] 暫時管理來自店面的搜尋請求，而 [!DNL Live Search] 服務會在背景索引所有產品，而不會中斷一般店面作業。 [!DNL Elasticsearch] 已停用，並且 [!DNL Live Search] 在所有目錄資料都編制索引並同步化後啟用。

1. 若要下載 `live-search` 封裝，從命令列執行以下命令：

   ```bash
   composer require magento/live-search
   ```

   如需詳細資訊，請參閱 [!DNL Live Search] [相依性](#live-search-dependencies) 擷取者： [!DNL Composer].

1. 執行以下命令以暫時停用 [!DNL Live Search] 提供店面搜尋結果的模組。

   ```bash
   bin/magento module:disable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   [!DNL Elasticsearch] 持續管理來自店面的搜尋請求，同時 [!DNL Live Search] 服務會在背景同步目錄資料和索引產品。

1. 確認下列各項 [索引子](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) 設為 `Update by Schedule`：

   * 產品摘要
   * 產品變體資訊源
   * 目錄屬性摘要

1. 設定您的 [API金鑰](#configure-api-keys) 並確認您的目錄資料為 [已同步](#synchronize-catalog-data) 替換為 [!DNL Live Search] 服務。

1. 若要讓Facet在店面中成為可用篩選器，請新增 [Facet](facets-add.md) 您需要，根據 [多面向需求](facets.md).

   之後您應該能夠新增Facet `cron` 執行產品和屬性摘要，並將屬性中繼資料匯出至 [!DNL Live Search] 服務。

1. 至少等候一小時，讓資料建立索引並同步。 然後，使用 [GraphQL遊樂場](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/) 預設查詢，以驗證以下內容：

   * 傳回的產品計數接近您對商店檢視的預期。
   * 傳回Facet。

1. 執行以下命令以啟用 [!DNL Live Search] 模組，停用 [!DNL Elasticsearch]，並執行 `setup`.

   ```bash
   bin/magento module:enable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover
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

需要Adobe Commerce API金鑰及其關聯的私密金鑰才能連線 [!DNL Live Search] Adobe Commerce的安裝。 API金鑰會在的帳戶中產生和維護 [!DNL Commerce] 授權持有者，可與開發人員或SI共用。 然後開發人員可以代表授權持有人建立和管理SaaS資料空間。  如果您已經有一組API金鑰，則不需要重新產生。

### Adobe Commerce授權持有者

若要產生API金鑰和私密金鑰，請參閱 [商務服務聯結器](../landing/saas.md).

### Adobe Commerce開發人員或SI

開發人員或SI會設定SaaS資料空間，如 *Commerce服務* 區段。 在 *管理員*，Commerce Services將可在 *設定* 側邊欄（安裝SaaS模組時）。

## 同步目錄資料 {#synchronize-catalog-data}

[!DNL Live Search] 搜尋操作需要同步的產品資料，而且需要同步屬性資料才能設定Facet。 產品目錄與目錄服務之間的初始同步始於 [!DNL Live Search] 是第一個連線。 視目錄的安裝方法和大小而定，匯出資料並編制索引最多可能需要30分鐘。 [!DNL Live Search]. 在結構描述中可以找到與目錄服務同步和共用的資料清單，其定義如下：

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

### 驗證匯出 {#verify-export}

驗證目錄資料是否已從Adobe Commerce執行個體匯出且已同步處理 [!DNL Live Search]，請在下清單格中尋找專案：

* `catalog_data_exporter_products`
* `catalog_data_exporter_product_attributes`

如需其他說明，請參閱 [[!DNL Live Search] 目錄未同步](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-catalog-data-sync.html) 位於支援知識庫中。

### 未來的產品更新

初始同步後，最多可能需要15分鐘才能將增量產品更新提供給店面搜尋。 若要深入瞭解，請前往 [索引 — 串流產品更新](indexing.md).

## 測試連線 {#test-connection}

在店面，驗證下列內容：

* 此 [!UICONTROL Search] 方塊會正確傳回結果
* 類別瀏覽正確傳回結果
* Facet在搜尋結果頁面上可作為篩選使用

如果一切正常運作，恭喜您！ [!DNL Live Search] 已安裝、連線且隨時可使用。

如果您在店面遇到問題，請檢查 `var/log/system.log` API通訊失敗或服務端錯誤的檔案。

## 檢查安裝的版本

在更新Live Search之前，請從命令列執行下列命令，以檢查目前安裝的Live Search版本：

```bash
composer show magento/module-live-search | grep version
```

## 正在更新 [!DNL Live Search] {#update}

待更新 [!DNL Live Search]，從命令列執行以下命令：

```bash
composer update magento/live-search --with-dependencies
```

若要更新至主要版本（例如從2.0.0到3.0.1），請編輯專案的根目錄 [!DNL Composer] `.json` 檔案如下所示：

1. 如果您目前已安裝的 `magento/live-search` 版本為 `2.0.3` 或更低版本，而您正升級至版本 `3.0.0` 或更高版本時，請在升級前執行下列命令：

   ```bash
   bin/magento module:enable Magento_AdvancedSearch
   ```

   有關目前安裝的資訊 `magento/live-search` 版本，請執行以下命令：

   ```bash
   composer show magento/live-search
   ```

1. 開啟根目錄 `composer.json` 檔案和搜尋 `magento/live-search`.

1. 在 `require` 區段，更新版本號碼，如下所示：

   ```json
   "require": {
      ...
      "magento/live-search": "^3.0",
      ...
    }
   ```

1. **儲存** `composer.json`. 然後，從命令列執行下列動作：

   ```bash
   composer update magento/live-search --with-dependencies
   ```

## 解除安裝 [!DNL Live Search] {#uninstall}

若要解除安裝 [!DNL Live Search]，請參閱 [解除安裝模組](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).

## [!DNL Live Search] 套件 {#packages}

| 封裝 | 說明 |
|--- |--- |
| `module-live-search` | 可讓商家針對多面向、同義字、查詢規則等設定其搜尋設定，並提供對唯讀GraphQL遊樂場的存取權，以測試來自 *管理員*. |
| `module-live-search-adapter` | 將搜尋要求從店面路由至 [!DNL Live Search] 服務並呈現店面中的結果。 <br /> — 類別瀏覽 — 路由店面的請求 [頂端導覽](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) 至搜尋服務。<br /> — 全域搜尋 — 路由來自下列專案的請求： [快速搜尋](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) 方塊（位於店面的右上角） [!DNL Live Search] 服務。 |
| `module-live-search-storefront-popover` | 「依輸入方式搜尋」彈出視窗會取代標準快速搜尋，並傳回熱門搜尋結果的資料和縮圖。 |

## [!DNL Live Search] 相依性 {#dependencies}

下列專案 [!DNL Live Search] 相依性擷取自 [!DNL Composer]：

| 相依性 | 說明 |
|--- |--- |
| 匯出模組 | 下列模組會收集並同步目錄資料：<br />`module-sass-catalog`<br />`module-sass-product-override`<br />`module-bundle-product-data-exporter`<br />`module-catalog-data-exporter`<br />`module-catalog-inventory-data-exporter`<br />`module-catalog-url-rewrite-data-exporter`<br />`module-configurable-product-data-exporter`<br />`module-data-exporter`<br />`module-parent-product-data-exporter`<br />`module-product-override-data-exporter` |
| `data-services` | 需要設定您與Commerce Services的連線。 |
| `services-id` | 需要設定您與Commerce Services的連線。 |
