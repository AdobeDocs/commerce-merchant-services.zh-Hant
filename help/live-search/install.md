---
title: "安裝 [!DNL Live Search]"
description: 「了解如何安裝、更新和解除安裝 [!DNL Live Search] 來自Adobe Commerce。」
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '1279'
ht-degree: 0%

---

# 安裝 [!DNL Live Search]

Live Search是以Adobe市集的擴充功能安裝。 在 [!DNL Live Search] 模組（以目錄模組作為依賴項）安裝並配置， [!DNL Commerce] 開始與SaaS服務共用搜索和編錄資料。 此時， *管理* 使用者可以設定、自訂及管理搜尋Facet、同義字和銷售規則。

本主題提供執行下列作業的指示：

* 安裝 [!DNL Live Search] （方法1和2）
* [更新 [!DNL Live Search]](#update)
* [解除安裝 [!DNL Live Search]](#uninstall)

## 開始之前 {#before-you-begin}

執行下列動作：

1. 確認 [cron作業](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) 和 [索引器](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) 執行中。

1. 選擇符合您需求的上線方法，並依照指示操作。

   * [方法1](#method-1):不安裝 [!DNL Elasticsearch]
   * [方法2](#method-2):安裝方式 [!DNL Elasticsearch] （無停機）

## 方法1:不安裝Elasticsearch {#method-1}

安裝時，建議使用此上線方法 [!DNL Live Search] 到a:

* 新增 [!DNL Commerce] 安裝
* 中繼環境

在此情境中，店面操作會在 [!DNL Live Search] 服務對目錄中的所有產品進行索引。 在安裝期間， [!DNL Live Search] 模組已啟用， [!DNL Elasticsearch] 模組已停用。

>[!TIP]
>
>若要避免輸入錯誤，請將滑鼠指標暫留在程式碼方塊的最右側，按一下 [!UICONTROL **複製**] 連結，然後貼到命令列中。

1. 安裝Adobe Commerce 2.4.x(不含 [!DNL Live Search].

1. 若要下載 `live-search` 軟體包，從命令行運行以下內容：

   ```bash
   composer require magento/live-search
   ```

   如需詳細資訊，請參閱 [!DNL Live Search] [相依性](#dependencies) 被 [!DNL Composer].

1. 運行以下命令以禁用 [!DNL Elasticsearch] 和相關模組，並安裝 [!DNL Live Search]:

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch6 Magento_Elasticsearch7 Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch 
   Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   >[!WARNING]
   >
   > 當資料已編列索引並同步時，搜索和類別瀏覽操作在店面中不可用。 視目錄的大小而定，程式可能至少需要一小時的時間 `cron` 執行以同步資料 [!DNL Live Search] 服務。

1. 確認下列項目 [索引器](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) 設為 `Update by Schedule`:

   * 產品摘要
   * 產品變體摘要
   * 目錄屬性摘要

1. 設定您的 [API金鑰](#configure-api-keys) 並確認目錄資料 [已同步](#synchronize-catalog-data) with [!DNL Live Search] 服務。

1. 若要讓Facet在店面中可作為篩選器使用，請新增 [facet](facets-add.md) 根據 [面向需求](facets.md).

   您應可在 `cron` 執行屬性摘要並匯出屬性中繼資料。

1. 至少等候一小時 `cron` 運行以同步資料。 然後， [驗證](#verify-export) 資料已匯出。

1. [測試](#test-the-connection) 店面的連接。

## 方法2:使用Elasticsearch安裝 {#method-2}

安裝時，建議使用此上線方法 [!DNL Live Search] 至：

* 現有生產 [!DNL Commerce] 安裝

在這種情況下， [!DNL Elasticsearch] 暫時管理來自店面的搜尋請求，而 [!DNL Live Search] 服務對後台的所有產品進行索引，不會中斷正常的店面操作。 [!DNL Elasticsearch] 已停用， [!DNL Live Search] 在所有目錄資料已編列索引並同步後啟用。

>[!TIP]
>
>若要避免輸入錯誤，請將滑鼠指標暫留在程式碼方塊的最右側，按一下 [!UICONTROL **複製**] 連結，然後貼到命令列中。

1. 若要下載 `live-search` 軟體包，從命令行運行以下內容：

   ```bash
   composer require magento/live-search
   ```

   如需詳細資訊，請參閱 [!DNL Live Search] [相依性](#live-search-dependencies) 被 [!DNL Composer].

1. 運行以下命令以臨時禁用 [!DNL Live Search] 提供storefront搜索結果的模組。

   ```bash
   bin/magento module:disable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   [!DNL Elasticsearch] 會繼續管理storefront的搜尋請求，而 [!DNL Live Search] 服務在後台同步目錄資料和索引產品。

1. 確認下列項目 [索引器](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) 設為 `Update by Schedule`:

   * 產品摘要
   * 產品變體摘要
   * 目錄屬性摘要

1. 設定您的 [API金鑰](#configure-api-keys) 並確認目錄資料 [已同步](#synchronize-catalog-data) with [!DNL Live Search] 服務。

1. 若要讓Facet在店面中可作為篩選器使用，請新增 [facet](facets-add.md) 根據 [面向需求](facets.md).

   您應可在 `cron` 執行產品和屬性摘要，並將屬性中繼資料匯出至 [!DNL Live Search] 服務。

1. 至少等待一小時，以便對資料進行索引和同步。 然後，使用 [GraphQL遊樂場](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/) 使用預設查詢來驗證下列內容：

   * 傳回的產品計數接近您對商店檢視的預期值。
   * 會傳回Facet。

1. 運行以下命令以啟用 [!DNL Live Search] 模組，禁用 [!DNL Elasticsearch]，然後執行 `setup`.

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

1. [測試](#test-the-connection) 店面的連接。

## 設定API金鑰 {#configure-api-keys}

必須有Adobe Commerce API金鑰及其相關的私密金鑰才能連線 [!DNL Live Search] 安裝Adobe Commerce。 API金鑰會產生並維護於 [!DNL Commerce] 許可證持有者，他們可以與開發商或SI共用。 然後，開發人員可以代表許可證持有者建立和管理SaaS資料空間。  如果您已有一組API金鑰，則不需要重新產生金鑰。

### Adobe Commerce授權人

若要產生API金鑰和私密金鑰，請參閱 [商務服務連接器](../landing/saas.md).

### Adobe Commerce開發人員或SI

開發人員或SI會依照 *商務服務* 區段。 在 *管理*，商務服務將可在 *設定* 安裝SaaS模組時的邊欄。

## 同步目錄資料 {#synchronize-catalog-data}

[!DNL Live Search] 需要同步的產品資料才能執行搜尋操作，並需要同步的屬性資料才能設定facet。 產品目錄與目錄服務之間的初始同步始於 [!DNL Live Search] 時，才會受到追蹤。 根據目錄的安裝方法和大小，資料的匯出和索引最多需要8小時 [!DNL Live Search]. 可在架構中找到與目錄服務同步和共用的資料清單，該架構在中定義：

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

### 驗證導出 {#verify-export}

驗證目錄資料已從您的Adobe Commerce執行個體匯出，且已同步 [!DNL Live Search]，尋找下表中的項目：

* `catalog_data_exporter_products`
* `catalog_data_exporter_product_attributes`

如需其他說明，請參閱 [[!DNL Live Search] 目錄未同步](https://support.magento.com/hc/en-us/articles/4405637804301-Live-search-catalog-not-synchronized) 在支援知識庫中。

### 未來產品更新

初始同步後，增量產品更新最多可能需要15分鐘才可用於店面搜索。 若要進一步了解，請前往 [索引 — 串流產品更新](indexing.md).

## 測試連線 {#test-connection}

在店面中，驗證下列內容：

* 此 [!UICONTROL Search] 框正確返回結果
* 類別瀏覽正確返回結果
* Facet可作為搜尋結果頁面上的篩選器

如果一切正常，恭喜！ [!DNL Live Search] 已安裝、已連接且已可供使用。

如果在店面遇到問題，請檢查 `var/log/system.log` 檔案，以了解服務端的API通訊失敗或錯誤。

## 檢查已安裝的版本

在更新Live Search之前，請從命令列執行下列項目，以檢查目前安裝的Live Search版本：

```bash
composer show magento/module-live-search | grep version
```

## 更新 [!DNL Live Search] {#update}

更新 [!DNL Live Search]，從命令列執行下列內容：

```bash
composer update magento/live-search --with-dependencies
```

若要更新為主要版本，例如從1.0.0更新為2.0.0，請編輯專案的根 [!DNL Composer] `.json` 檔案如下：

1. 如果您目前已安裝 `magento/live-search` 版本 `1.3.1` 或更低版本，且您正在升級至版本 `2.0.0` 或更高版本，在升級前運行以下命令：

   ```bash
   bin/magento module:enable Magento_AdvancedSearch
   ```

   有關當前安裝的資訊 `magento/live-search` 版本，運行以下命令：

   ```bash
   composer show magento/live-search
   ```

1. 開啟根 `composer.json` 檔案和搜索 `magento/live-search`.

1. 在 `require` 部分，請按如下方式更新版本號：

   ```json
   "require": {
      ...
      "magento/live-search": "^2.0",
      ...
    }
   ```

1. **儲存** `composer.json`. 然後，從命令列執行下列動作：

   ```bash
   composer update magento/live-search –-with-dependencies
   ```

## 解除安裝 [!DNL Live Search] {#uninstall}

卸載 [!DNL Live Search]，請參閱 [卸載模組](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).

## [!DNL Live Search] 套件 {#packages}

| 套件 | 說明 |
|--- |--- |
| `module-live-search` | 可讓商戶為Facet、同義字、查詢規則等設定其搜尋設定，並可存取唯讀GraphQL遊樂場，以測試來自 *管理*. |
| `module-live-search-adapter` | 將搜索請求從店面路由到 [!DNL Live Search] 服務，並將結果轉譯到店面。 <br /> — 類別瀏覽 — 從店面路由請求 [頂端導覽](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) 到搜尋服務。<br /> — 全域搜尋 — 路由來自 [快速搜尋](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) 框的右上方 [!DNL Live Search] 服務。 |
| `module-live-search-storefront-popover` | 彈出式視窗會取代標準快速搜尋，並傳回最上層搜尋結果的資料和縮圖。 |

## [!DNL Live Search] 相依性 {#dependencies}

以下 [!DNL Live Search] 依據 [!DNL Composer]:

| 相依性 | 說明 |
|--- |--- |
| 匯出模組 | 以下模組收集和同步目錄資料：<br />`saas-export`<br />`module-bundle-product-exporter`<br />`module-catalog-data-exporter`<br />`module-catalog-inventory-data-exporter`<br />`module-catalog-url-rewrite-data-exporter`<br />`module-configurable-product-data-exporter`<br />`module-data-exporter`<br />`module-parent-product-data-exporter` |
| `services-connector` | 配置與Commerce Services的連接時需要。 |
| `module-services-id` | 配置與Commerce Services的連接時需要。 |
