---
title: 入門和安裝
description: 了解如何安裝 [!DNL Catalog Service]
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: 4604aacc19d7740c63b39134bd9f4c146479ac8f
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# 入門和安裝

## 必要條件

的上線程式 [!DNL Catalog Service] 需要訪問伺服器的命令行。 如果您不熟悉從命令列進行工作，請要求開發人員或系統整合商提供協助。

### 軟體需求

- Adobe Commerce 2.4.x
- PHP 8.1、7.4、7.3
- 撰寫器：2.x、1.x

### 支援平台

- Adobe Commerce雲基礎架構：2.4.x
- Adobe Commerce駐地：2.4.x

## 安裝擴充功能

您可以安裝 [!DNL Catalog Service] 雲端基礎架構和內部部署執行個體上Adobe Commerce的擴充功能。

此 [!DNL Catalog Service] 隨撰寫器金鑰安裝，這些金鑰連結至商務帳戶 [馬吉德](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-personal/#field-descriptions) 在註冊過程中提供。 撰寫器在初始安裝期間使用這些金鑰 [!DNL Adobe Commerce]，或在撰寫器金鑰先前未儲存至的情況下 `auth.json` 檔案。

請參閱 [取得驗證金鑰](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 以取得關於取得撰寫器金鑰的詳細資訊。

### Adobe Commerce雲基礎架構

使用此方法來安裝 [!DNL Catalog Service] Commerce Cloud例項的擴充功能。

1. 開啟 `<Commerce_root>/composer.json` 檔案，並更新 `require` 區段如下：

   ```json
   "require": {
      "magento/module-saas-catalog": "^101.4.0",
      "magento/module-saas-product-override": "^101.4.0",
      "magento/module-saas-product-variant": "^101.4.0",
      "magento/module-bundle-product-data-exporter": "^101.3.1",
      "magento/module-catalog-data-exporter": "^101.3.1",
      "magento/module-catalog-inventory-data-exporter": "^101.3.1",
      "magento/module-catalog-url-rewrite-data-exporter": "^101.3.1",
      "magento/module-configurable-product-data-exporter": "^101.3.1",
      "magento/module-data-exporter": "^101.3.1",
      "magento/module-parent-product-data-exporter": "^101.3.1",
      "magento/module-product-override-data-exporter": "^101.3.1",
      "magento/data-services": "^7.0.11",
      "magento/services-id": "^3.0.1",
      "magento/services-connector": "1.2.1"
    }
   ```

1. 在本機測試新設定並更新相依性：

   ```bash
   composer update
   ```

   命令會更新所有相依性。

1. 提交並推送您的更改 `composer.json` 和 `composer.lock`.

### 內部部署

使用此方法來安裝 [!DNL Catalog Service] 內部部署執行個體的擴充功能。

1. 開啟 `<Commerce_root>/composer.json` 檔案，並更新 `require` 區段如下：

   ```json
   "require": {
    "magento/module-saas-catalog": "^101.4.0",
    "magento/module-saas-product-override": "^101.4.0",
    "magento/module-saas-product-variant": "^101.4.0",
    "magento/module-bundle-product-data-exporter": "^101.3.1",
    "magento/module-catalog-data-exporter": "^101.3.1",
    "magento/module-catalog-inventory-data-exporter": "^101.3.1",
    "magento/module-catalog-url-rewrite-data-exporter": "^101.3.1",
    "magento/module-configurable-product-data-exporter": "^101.3.1",
    "magento/module-data-exporter": "^101.3.1",
    "magento/module-parent-product-data-exporter": "^101.3.1",
    "magento/module-product-override-data-exporter": "^101.3.1",
    "magento/data-services": "^7.0.11",
    "magento/services-id": "^3.0.1",
    "magento/services-connector": "1.2.1"
   }
   ```

1. 更新相依性並安裝擴充功能：

   ```bash
   composer update
   ```

   命令會更新所有相依性。

1. 升級Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. 清除快取：

   ```bash
   bin/magento cache:clean
   ```

## 目錄服務和API網格

此 [API Mesh](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) 使開發人員能夠使用AdobeIO將專用或第三方API和其他介面與Adobe產品整合。

將API Mesh與目錄服務搭配使用的第一步，是將API Mesh連線至您的執行個體。 請參閱 [建立網格](https://developer.adobe.com/graphql-mesh-gateway/gateway/create-mesh/).

若要完成設定，您需要 [AdobeIO CLI包](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/) 已安裝。

在AdobeIO上配置網格後，運行以下命令以連接新網格。

```bash
aio api-mesh:source:install "CommerceCatalogServiceGraph" -f variables.json
```

where `variables.json` 是儲存AdobeIO常用值的單獨檔案。
例如，API金鑰可儲存在檔案中：

```json
{
    "CATALOG_SERVICE_API_KEY":"your_api_key"
}
```

執行此命令後，目錄服務應通過API網格運行。

## 配置目錄導出

安裝後 [!DNL Catalog Service]，您必須設定 [商務服務連接器](../landing/saas.md) 指定API密鑰並選擇SaaS資料空間。

若要確保目錄匯出正確執行：

- 確認 [cron作業](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) 執行中。
- 驗證 [索引器](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) 執行中。
- 確保 `Catalog Attributes Feed`, `Product Feed`, `Product Overrides Feed`，和 `Product Variant Feed` 索引器設定為 `Update by Schedule`.

## [!DNL Catalog Service] 示範

觀看此影片以了解 [!DNL Catalog Service] 安裝與測試：

>[!VIDEO](https://video.tv.adobe.com/v/3409390?quality=12&learn=on)
