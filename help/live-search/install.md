---
title: 安裝Live Search
description: 瞭解如何從Adobe Commerce安裝、更新和卸載Live Search。
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
source-git-commit: 61d50ec07e7c8ced1696f4169a90302cca4d4f96
workflow-type: tm+mt
source-wordcount: '1211'
ht-degree: 0%

---

# 安裝 [!DNL Live Search]

Live Search作為Adobe市場的擴展安裝。 在 [!DNL Live Search] 安裝和配置了模組（將目錄模組作為依賴項）, [!DNL Commerce] 開始與SaaS服務共用搜索和編錄資料。 現在， *管理* 用戶可以設定、自定義和管理搜索小面、同義詞和促銷規則。

本主題提供了執行以下操作的說明：

* 安裝 [!DNL Live Search] （方法1和2）
* [更新 [!DNL Live Search]](#update)
* [卸載 [!DNL Live Search]](#uninstall)

## 開始之前 {#before-you-begin}

執行以下操作：

1. 確認 [瘋狂的工作](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html) 和 [索引器](https://docs.magento.com/user-guide/system/index-management.html) 正在運行。

1. 選擇符合您要求的登機方法，並按照說明進行操作。

   * [方法1](#method-1):安裝時不 [!DNL Elasticsearch]
   * [方法2](#method-2):安裝時 [!DNL Elasticsearch] （無停機時間）

## 方法1:安裝而不Elasticsearch {#method-1}

安裝時建議使用此登錄方法 [!DNL Live Search] 至：

* 新建 [!DNL Commerce] 安裝
* 暫存環境

在此方案中，在 [!DNL Live Search] 服務為目錄中的所有產品編製索引。 在安裝過程中， [!DNL Live Search] 模組已啟用， [!DNL Elasticsearch] 模組被禁用。

>[!TIP]
>
>要避免鍵入錯誤，請將滑鼠懸停在代碼框的最右側，按一下 [!UICONTROL **複製**] 連結，然後貼上到命令行中。

1. 安裝Adobe Commerce2.4.x，不 [!DNL Live Search]。

1. 下載 `live-search` 軟體包，從命令行運行以下命令：

   ```bash
   composer require magento/DNL live-search
   ```

   有關詳細資訊，請參閱 [!DNL Live Search] [依賴](#dependencies) 被 [!DNL Composer]。

1. 運行以下命令以禁用 [!DNL Elasticsearch] 及相關模組，並安裝 [!DNL Live Search]:

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch6 Magento_Elasticsearch7 Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   >[!WARNING]
   >
   > 當資料被索引和同步時，搜索和類別瀏覽操作在儲存面中不可用。 根據目錄的大小，此過程可能至少需要一小時 `cron` 運行以將資料同步到 [!DNL Live Search] 服務。

1. 驗證以下 [索引器](https://docs.magento.com/user-guide/system/index-management.html) 設定為 `Update by Schedule`:

   * 產品源
   * 產品變型源
   * 目錄屬性源

1. 配置 [API密鑰](#configure-api-keys) 並驗證目錄資料 [同步](#synchronize-catalog-data) 與 [!DNL Live Search] 服務。

1. 要使小平面在儲存面中作為濾鏡可用，請添加 [面](facets-add.md) 你需要，根據 [面向要求](facets.md)。

   您應能在 `cron` 運行屬性源和導出屬性元資料。

1. 等待至少一小時後 `cron` 運行以同步資料。 然後， [驗證](#verify-export) 資料已導出。

1. [Test](#test-the-connection) 店面的連接。

## 方法2:使用Elasticsearch安裝 {#method-2}

安裝時建議使用此登錄方法 [!DNL Live Search] 至：

* 現有生產 [!DNL Commerce] 安裝

在這種情況下， [!DNL Elasticsearch] 臨時管理來自商店的搜索請求，而 [!DNL Live Search] 服務為後台所有產品編製索引，不會中斷正常的店面操作。 [!DNL Elasticsearch] 已禁用， [!DNL Live Search] 在索引和同步所有目錄資料後啟用。

>[!TIP]
>
>要避免鍵入錯誤，請將滑鼠懸停在代碼框的最右側，按一下 [!UICONTROL **複製**] 連結，然後貼上到命令行中。

1. 下載 `live-search` 軟體包，從命令行運行以下命令：

   ```bash
   composer require magento/live-search
   ```

   有關詳細資訊，請參閱 [!DNL Live Search] [依賴](#live-search-dependencies) 被 [!DNL Composer]。

1. 運行以下命令以臨時禁用 [!DNL Live Search] 提供儲存搜索結果的模組。

   ```bash
   bin/magento module:disable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   [!DNL Elasticsearch] 繼續管理來自商店的搜索請求，而 [!DNL Live Search] 服務在後台同步目錄資料和索引產品。

1. 驗證以下 [索引器](https://docs.magento.com/user-guide/system/index-management.html) 設定為 `Update by Schedule`:

   * 產品源
   * 產品變型源
   * 目錄屬性源

1. 配置 [API密鑰](#configure-api-keys) 並驗證目錄資料 [同步](#synchronize-catalog-data) 與 [!DNL Live Search] 服務。

1. 要使小平面在儲存面中作為濾鏡可用，請添加 [面](facets-add.md) 你需要，根據 [面向要求](facets.md)。

   您應能在 `cron` 運行產品和屬性源並將屬性元資料導出到 [!DNL Live Search] 服務。

1. 至少等待一小時，以便對資料進行索引和同步。 然後，使用 [GraphQL操場](https://devdocs.magento.com/live-search/graphql-support.html) 使用預設查詢驗證以下內容：

   * 返回的產品數量接近您對商店視圖的預期。
   * 返回Facet。

1. 運行以下命令以啟用 [!DNL Live Search] 模組，禁用 [!DNL Elasticsearch]，然後運行 `setup`。

   ```bash
   bin/magento module:enable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover
   ```

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch6 Magento_Elasticsearch7 Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch
   ```

   ```bash
   bin/magento setup:upgrade
   ```

1. [Test](#test-the-connection) 店面的連接。

## 配置API密鑰 {#configure-api-keys}

需要Adobe CommerceAPI密鑰及其關聯的私鑰才能連接 [!DNL Live Search] 一個Adobe Commerce。 API密鑰生成並在帳戶中維護 [!DNL Commerce] 許可證持有者，可以與開發商或SI共用。 然後，開發人員可以代表許可證持有者建立和管理SaaS資料空間。  如果已經有一組API密鑰，則無需重新生成它們。

### Adobe Commerce牌照持有人

要生成API密鑰和私鑰，請參閱 [Commerce Services連接器](../landing/saas.md)。

### Adobe Commerce開發商或SI

開發人員或SI按中所述配置SaaS資料空間 *商務服務* 的子菜單。 在 *管理*,Commerce Services將在 *配置* 安裝SaaS模組時的邊欄。

## 同步目錄資料 {#synchronize-catalog-data}

[!DNL Live Search] 需要同步的產品資料以執行搜索操作，並需要同步的屬性資料以配置facet。 產品目錄和目錄服務之間的初始同步始於 [!DNL Live Search] 。 根據目錄的安裝方法和大小，資料可能需要8個小時才能導出和索引。 [!DNL Live Search]。 可以在架構中找到與目錄服務同步和共用的資料清單，該架構定義如下：

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

### 驗證導出 {#verify-export}

驗證目錄資料是否已從您的Adobe Commerce實例導出並已同步， [!DNL Live Search]，在以下表中查找條目：

* `catalog_data_exporter_products`
* `catalog_data_exporter_product_attributes`

有關其他幫助，請參閱 [[!DNL Live Search] 目錄未同步](https://support.magento.com/hc/en-us/articles/4405637804301-Live-search-catalog-not-synchronized) 的子菜單。

### 將來的產品更新

在初始同步後，增量產品更新可能需要15分鐘才能可用於儲存前搜索。 要瞭解詳細資訊，請轉到 [索引 — 流式處理產品更新](indexing.md)。

## Test連接 {#test-connection}

在店面中，驗證以下內容：

* 的 [!UICONTROL Search] 框正確返回結果
* 類別瀏覽正確返回結果
* 多面可用作搜索結果頁上的篩選器

如果一切正常，恭喜！ [!DNL Live Search] 已安裝、已連接並可供使用。

如果在店面遇到問題，請檢查 `var/log/system.log` 檔案，用於服務端的API通信失敗或錯誤。

## 更新 [!DNL Live Search] {#update}

要更新 [!DNL Live Search]，從命令行運行以下命令：

```bash
composer update magento/live-search --with-dependencies
```

要更新到主版本，如從1.0.0到2.0.0，請編輯項目的根 [!DNL Composer] `.json` 檔案，如下所示：

1. 開啟根 `composer.json` 檔案和搜索 `magento/live-search`。

1. 在 `require` 部分，按如下方式更新版本號：

   ```json
   "require": {
      ...
      "magento/live-search": "^2.0",
      ...
    }
   ```

1. **保存** `composer.json`。 然後，從命令行運行以下命令：

   ```bash
   composer update magento/live-search –-with-dependencies
   ```

## 正在卸載 [!DNL Live Search] {#uninstall}

卸載 [!DNL Live Search]，請參閱 [卸載模組](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-uninstall-mods.html)。

## [!DNL Live Search] 軟體包 {#packages}

| 包 | 說明 |
|--- |--- |
| `module-live-search` | 允許商戶配置其面部設定、同義詞、查詢規則等的搜索設定，並提供對只讀GraphQL操作場的訪問權，以test來自查詢的查詢 *管理*。 |
| `module-live-search-adapter` | 將搜索請求從店面路由到 [!DNL Live Search] 並將結果呈現在店面。 <br /> — 類別瀏覽 — 從店面路由請求 [頂部導航](https://docs.magento.com/user-guide/catalog/navigation-top.html) 搜索服務。<br /> — 全局搜索 — 路由來自 [快速搜索](https://docs.magento.com/user-guide/catalog/search-quick.html) 位於店面右上角的 [!DNL Live Search] 服務。 |
| `module-live-search-storefront-popover` | 「鍵入時搜索」跨距將替換標準快速搜索，並返回頂級搜索結果的動態產品建議和縮略圖。 |

## [!DNL Live Search] 依賴 {#dependencies}

以下 [!DNL Live Search] 依賴項由 [!DNL Composer]:

| 依賴項 | 說明 |
|--- |--- |
| 導出模組 | 以下模組收集和同步目錄資料：<br />`saas-export`<br />`module-bundle-product-exporter`<br />`module-catalog-data-exporter`<br />`module-catalog-inventory-data-exporter`<br />`module-catalog-url-rewrite-data-exporter`<br />`module-configurable-product-data-exporter`<br />`module-data-exporter`<br />`module-parent-product-data-exporter` |
| `services-connector` | 配置到Commerce Services的連接時需要。 |
| `module-services-id` | 配置到Commerce Services的連接時需要。 |
