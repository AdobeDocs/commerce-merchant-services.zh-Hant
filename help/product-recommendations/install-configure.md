---
title: 安裝和配置
description: 瞭解如何安裝、更新和卸載 [!DNL Product Recommendations]。
exl-id: fa599f72-1064-41da-ac54-2b3a3c16a1fe
source-git-commit: b06d5000263b7ee09608a4a8510d76e9f4bdb809
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# 安裝和配置

部署 [!DNL Product Recommendations] 要求安裝模組並配置 [Commerce Services連接器](../landing/saas.md)。 隨著更新的發佈，您可以輕鬆使用最新版本更新安裝。

- [安裝](#install)
- [配置](#configure)
- [更新](#update)
- [卸載](#uninstall)

## 安裝 [!DNL Product Recommendations] {#install}

因為 [!DNL Product Recommendations] 模組是獨立的元包，更新發佈比Adobe Commerce更頻繁。 要確保最新的錯誤修復程式和功能，請參閱 [發行說明](release-notes.md)。

安裝 `magento/product-recommendations` 具有Composer的模組：

```bash
composer require magento/product-recommendations
```

### 添加頁面生成器支援 {#pbsupport}

[!DNL Product Recommendations] for Page Builder是可選模組，並單獨安裝。 要使用 [!DNL Product Recommendations] 使用Page Builder，通過運行以下命令來安裝模組：

```bash
composer require magento/module-page-builder-product-recommendations
```

通過啟用 [!DNL Product Recommendations] 在頁面生成器中，可以添加現有的活動 [推薦單元](https://docs.magento.com/user-guide/cms/page-builder-add-recommendations.html) 到在頁面生成器中建立的任何內容，如頁面、塊和動態塊。

### 添加可視相似性建議類型 {#vissimsupport}

的 _視覺相似性_ 建議類型允許您將建議單元部署到產品詳細資訊頁面，該頁面顯示 [相似](type.md#visualsim) 查看的產品。 這種推薦類型在產品的影像和視覺方面是購物體驗的重要組成部分時最為有用。 安裝 _視覺相似性_ 通過運行以下命令執行建議類型：

```bash
composer require magento/module-visual-product-recommendations
```

## 配置 [!DNL Product Recommendations] {#configure}

安裝後 `magento/product-recommendations` 模組，必須配置 [Commerce Services連接器](https://docs.magento.com/user-guide/configuration/services/saas.html) 指定API密鑰並選擇SaaS資料空間。

要確保目錄導出正確運行，請確認 [克隆](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html) 工作和 [索引器](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html) 正在運行 `Product Feed` 索引器設定為 `Update by Schedule`。

通過API鍵成功連結到Commerce Services並指定SaaS資料空間時，目錄同步將開始。 你可以 [驗證](verify.md) 行為資料被發到你的店面。

## 更新 [!DNL Product Recommendations] 安裝 {#update}

和Adobe Commerce一樣， [!DNL Product Recommendations] 使用Composer進行安裝和更新。 更新 `magento/product-recommendations` 模組，運行以下命令：

```bash
composer update magento/product-recommendations --with-dependencies
```

要更新為主版本（如從2.0到3.0），必須編輯項目的根 `composer.json` 的子菜單。 (請參閱 [發行說明](release-notes.md) 有關最新版本的資訊。) 例如，開啟主 `composer.json` 檔案和搜索 `magento/product-recommendations` 模組：

```json
"require": {
    ...
    "magento/product-recommendations": "^2.0",
    ...
}
```

讓我們把主版本從 `2.0` 至 `3.0`:

```json
"require": {
    ...
    "magento/product-recommendations": "^3.0",
    ...
}
```

保存 `composer.json` 檔案和運行：

```bash
composer update magento/product-recommendations --with-dependencies
```

## 卸載 [!DNL Product Recommendations] {#uninstall}

如有必要，你可以 [卸載](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-uninstall-mods.html) 產品建議模組。
