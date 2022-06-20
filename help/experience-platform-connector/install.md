---
title: 從Adobe Commerce安裝和配置Adobe Experience Platform連接器
description: 瞭解如何從Adobe Commerce安裝、配置、更新和卸載Adobe Experience Platform連接器。
source-git-commit: 9b5f2da08167e22bbba504009bccc87d0ab02c48
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# 安裝和配置Experience Platform連接器

在安裝擴展之前， [查看先決條件](overview.md#prereqs)。

## 安裝擴展

1. 安裝Experience Platform連接器集合包。

   ```bash
   composer require magento/platform-connector
   ```

   此元包包含以下模組：

   * `module-platform-connector-admin`  — 更新管理員UI
   * `module-platform-connector`  — 設定 `ImsOrgId` 和 `datastreamId` Magento店面事件SDK中

1. 安裝Commerce Data Services擴展以包括配置檔案和簽出事件。

   ```bash
   composer require magento/data-services
   ```

   Commerce Data Services擴展為儲存面事件提供屬性上下文。 例如，當發生簽出事件時，將包括有關購物車中有多少物料的資訊以及這些物料的產品屬性資料。

1. 安裝Commerce Service Connector。

   ```bash
   composer require magento/commerce-services
   ```

   Commerce Service Connector允許您將Adobe Commerce實例連接到 [Adobe CommerceSaaS](../landing/saas.md) 和Adobe Experience Platform。

1. （可選）要包括 [!DNL Live Search] 資料，包括搜索事件，安裝 [[!DNL Live Search]](../live-search/install.md) 擴展。

## 更新Experience Platform連接器 {#update}

要更新Experience Platform連接器，請從命令行運行以下命令：

```bash
composer update magento/platform-connector --with-dependencies
```

要更新到主版本，如從1.0.0到2.0.0，請編輯項目的根 [!DNL Composer] `.json` 檔案，如下所示：

1. 開啟根 `composer.json` 檔案和搜索 `magento/platform-connector`。

1. 在 `require` 部分，按如下方式更新版本號：

   ```json
   "require": {
      ...
      "magento/platform-connector": "^2.0",
      ...
    }
   ```

1. **保存** `composer.json`。 然後，從命令行運行以下命令：

   ```bash
   composer update magento/platform-connector –-with-dependencies
   ```

## 卸載Experience Platform連接器 {#uninstall}

要卸載Experience Platform連接器，請參閱 [卸載模組](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-uninstall-mods.html)。
