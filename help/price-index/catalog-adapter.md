---
title: 目錄配接器擴充功能
description: 使用目錄配接器從Commerce Services呈現價格
seo-title: Catalog Adapter Extension
seo-description: Using Catalog Adapter to render prices from Commerce Services
exl-id: 2c9120eb-aa51-48e9-b6a4-fffe25fc31f2
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 0%

---

# 目錄配接器

此 `[!DNL Catalog Adapter]` 擴充功能會停用Commerce應用程式中包含的預設產品價格索引器，並使用 [目錄服務](../catalog-service/overview.md) 而非。

此介面卡是專為搭配 [SaaS資料匯出](../data-export/overview.md) 和Adobe Commerce服務。 SaaS資料匯出負責提交價格，以及 [!DNL Catalog Adapter] 會擷取Adobe Commerce服務的所有價格。

當您啟用 [!DNL Catalog Adapter]，價格索引和作業會以下列方式影響：

- Adobe Commerce應用程式中包含的價格索引器已停用。
- 價格是使用SaaS資料匯出和 [SaaS價格索引子](price-indexing.md).
- 當客戶開啟產品、類別或其他顯示產品價格的頁面時，價格會從Adobe Commerce服務擷取。
- 價格會透過以下位置的同步資料傳送至Adobe Commerce服務： [SaaS資料匯出](../data-export/overview.md).
- 結帳會動態重新計算價格。

您可以移除或停用目錄轉接器擴充功能，以在Commerce應用程式中重新啟用價格索引。

## 需求

- Adobe Commerce 2.4.4+
- 已安裝下列Commerce服務之一：

   - [即時搜尋](../live-search/install.md)
   - [產品Recommendations](../product-recommendations/install-configure.md)
   - [目錄服務](../catalog-service/installation.md)

## 安裝

Catalog Adapter擴充功能是Composer中繼套件，可安裝下列模組：

- **價格索引器停用程式** — 此模組停用Commerce應用程式中的價格指數，因此價格會透過SaaS價格指數傳遞。 安裝SaaS價格索引擴充功能時，無法開啟Commerce應用程式中的產品價格索引器。
- **價格提供者** — 此單元提供Adobe Commerce服務產品的價格。 它會形成搜尋查詢並取得前端產品的價格。
- **目錄服務搜尋配接器** — 本模組會回應產品搜尋要求，將價格從Adobe Commerce應用程式傳輸至Adobe Commerce服務。

## 安裝步驟

>[!BEGINTABS]

>[!TAB 雲端基礎結構]

使用此方法來安裝 [!DNL Catalog Adapter] 適用於Commerce Cloud執行個體。

1. 在本機工作站上，變更至雲端基礎結構專案上Adobe Commerce的專案目錄。

   >[!NOTE]
   >
   >如需有關在本機管理Commerce專案環境的資訊，請參閱 [使用CLI管理分支](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches) 在 _雲端基礎結構上的Adobe Commerce使用手冊_.

1. 檢視環境分支，以使用Adobe Commerce Cloud CLI進行更新。

   ```shell
   magento-cloud environment:checkout <environment-id>
   ```

1. 新增目錄配接器模組。

   ```bash
   composer require magento/catalog-adapter --no-update
   ```

1. 更新套件相依性。

   ```bash
   composer update "magento/catalog-adapter"
   ```

1. 提交和推送程式碼變更 `composer.json` 和 `composer.lock` 檔案。

1. 新增、提交和推送程式碼變更 `composer.json` 和 `composer.lock` 檔案至雲端環境。

   ```shell
   git add -A
   git commit -m "Add catalog adapter module"
   git push origin <branch-name>
   ```

   將更新推播到雲端環境會啟動 [Commerce雲端部署程式](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process) 以套用變更。 從檢視部署狀態 [部署記錄](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log).

>[!TAB 內部部署]

使用此方法來安裝 [!DNL Catalog Adapter] 用於內部部署執行個體。

1. 使用Composer將目錄轉接器新增到您的專案：

   ```bash
   composer require magento/catalog-adapter --no-update
   ```

1. 更新相依性並安裝擴充功能：

   ```bash
   composer update  "magento/catalog-adapter"
   ```

1. 升級Adobe Commerce：

   ```bash
   bin/magento setup:upgrade
   ```

1. 清除快取：

   ```bash
   bin/magento cache:clean
   ```

   >[!TIP]
   >
   >在某些情況下，特別是部署到生產時，您可能希望避免清除編譯的程式碼，因為可能需要一些時間。 在進行任何變更之前，請務必先備份系統。

>[!ENDTABS]


## 重新啟用Adobe Commerce產品價格索引器

如果您有協力廠商應用程式依賴預設的Adobe Commerce產品價格索引器，則可以使用下列命令將其重新啟用：

```bash
# re-enable Product Price indexer
bin/magento module:disable Magento_PriceIndexerDisabler
# re-index Product Price indexer
bin/magento index:reindex catalog_product_price
```

## 停用Headless店面案例的產品價格索引器

如果您有Headless Commerce執行個體，您可能需要停用Adobe Commerce產品價格索引器，以減少Adobe Commerce執行個體的負載。 您可以安裝 `magento/module-price-indexer-disabler` 模組：

```bash
composer require magento/module-price-indexer-disabler
```

## 使用案例

以下是一些常見的 `[!DNL Catalog Adapter]` 情境。

### Adobe Commerce產品價格索引器沒有相依性

- 您是已安裝必要服務(即時搜尋、產品Recommendations、目錄服務)的Luma或Adobe Commerce Core GraphQL商家
- 沒有與依賴Adobe Commerce產品價格索引器的第三方擴充功能整合

1. 安裝 [!DNL Catalog Adapter].

### 依賴於Adobe Commerce產品價格索引器

- 您是已安裝支援服務(即時搜尋、產品Recommendations、目錄服務)的Luma或Adobe Commerce Core GraphQL商家
- 您使用依賴Adobe Commerce產品價格索引器的第三方擴充功能

1. 安裝 [!DNL Catalog Adapter].
1. 重新啟用預設的Adobe Commerce產品價格索引器。

### Headless Commerce執行個體

- 具有Headless Commerce執行個體並安裝所需服務(即時搜尋、產品Recommendations、目錄服務)的商家
- 不依賴預設的Adobe Commerce產品價格索引器

1. 安裝 `magento/module-price-indexer-disabler` 來自的模組 [!DNL Catalog Adapter] 封裝。

