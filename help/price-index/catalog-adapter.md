---
title: 目錄配接器擴充功能
description: 使用目錄配接器從Commerce Services轉譯價格
seo-title: Catalog Adapter Extension
seo-description: Using Catalog Adapter to render prices from Commerce Services
source-git-commit: 6b578e7113c278a05a64f2db5e032bccc4a9580a
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---


# 目錄配接器

此 `Catalog Adapter` 擴充功能會停用預設的Adobe Commerce產品價格索引器，改用以下專案所提供的價格： [目錄服務](../catalog-service/overview.md).
Adobe Commerce產品價格索引器已停用，且在安裝這些擴充功能模組時無法開啟。 只有移除或停用此擴充功能，才能重新啟用預設的產品價格索引子。

## 需求

* Adobe Commerce 2.4.4+
* 已安裝下列其中一個Commerce Services：

   * [目錄服務](../catalog-service/overview.md)
   * [即時搜尋](../live-search/guide-overview.md)

## 安裝

若要使用 `catalog-adapter` 模組， [!DNL Live Search] 和 [!DNL Catalog Service] 必須先安裝及設定。 請遵循 [安裝 [!DNL Live Search]](../live-search/install.md) 和 [目錄服務安裝](../catalog-service/installation.md) 指示後再繼續。

安裝這些服務後，請執行以下命令：

```bash
composer require adobe-commerce/catalog-adapter
```

## 可重新啟用Adobe Commerce產品價格索引器

如果您有協力廠商應用程式依賴預設的Adobe Commerce產品價格索引器，則可使用下列命令將其重新啟用：

```bash
# re-enable Product Price indexer
bin/magento module:disable Magento_PriceIndexerDisabler
# reindex Product Price indexer 
bin/magento index:reindex catalog_product_price
```

## 停用Headless店面案例的產品價格索引器

如果您有Headless Commerce執行個體，您可能需要停用Adobe Commerce產品價格索引子，以減少Adobe Commerce執行個體的負載。
這是透過安裝 `magento/module-price-indexer-disabler` 模組：

```bash
composer require magento/module-price-indexer-disabler
```

## 使用案例

以下是一些常見的 `Catalog Adapter` 情境。

### Adobe Commerce產品價格索引器沒有相依性

* 您是已安裝必要服務(即時搜尋、產品Recommendations、目錄服務)的Luma或Adobe Commerce Core GraphQL商家
* 沒有依賴Adobe Commerce產品價格索引器的第三方擴充功能

1. 安裝目錄介面卡。

### 依賴於Adobe Commerce產品價格索引器

* 您是已安裝支援服務(即時搜尋、產品Recommendations、目錄服務)的Luma或Adobe Commerce Core GraphQL商家
* 您使用依賴Adobe Commerce產品價格索引器的第三方擴充功能

1. 安裝目錄介面卡。
1. 重新啟用預設的Adobe Commerce產品價格索引器。

### Headless Commerce例項

* 具有已安裝所需服務(即時搜尋、產品Recommendations、目錄服務)的Headless Commerce執行個體的商家
* 不依賴預設的Adobe Commerce產品價格索引器

1. 從目錄介面卡套件安裝「價格停用程式」
