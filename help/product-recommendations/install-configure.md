---
title: 安裝和配置
description: 瞭解如何安裝、更新和卸載 [!DNL Product Recommendations]。
exl-id: fa599f72-1064-41da-ac54-2b3a3c16a1fe
source-git-commit: 78f226465b9d84707612596a5aa4622aa7869ee1
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# 安裝和配置

部署 [!DNL Product Recommendations] 要求安裝模組並配置 [Commerce Services連接器](../landing/saas.md)。 隨著更新的發佈，您可以輕鬆使用最新版本更新安裝。

- [安裝](#install)
- [配置](#configure)
- [更新](#update)
- [卸載](#uninstall)

## 安裝 [!DNL Product Recommendations] {#install}

因為 [!DNL Product Recommendations] 模組是獨立的元包，更新發佈比Adobe Commerce更頻繁。 要確保您使用最新的錯誤修復和功能是最新的，請參閱 [發行說明](release-notes.md)。

安裝 `magento/product-recommendations` 具有Composer的模組：

```bash
composer require magento/product-recommendations
```

### 添加頁面生成器支援 {#pbsupport}

[!DNL Product Recommendations] for Page Builder是可選模組，單獨安裝。 要使用 [!DNL Product Recommendations] 使用Page Builder，通過運行以下命令來安裝模組：

```bash
composer require magento/module-page-builder-product-recommendations
```

通過啟用 [!DNL Product Recommendations] 在頁面生成器中，可以添加現有的活動 [推薦單元](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) 到在頁面生成器中建立的任何內容，如頁面、塊和動態塊。

請參閱 [使用 [!DNL Product Recommendations] 使用頁面生成器內容](page-builder.md) 以獲取更多說明。

### 添加可視相似性建議類型 {#vissimsupport}

的 _視覺相似性_ 建議類型允許您將建議單元部署到產品詳細資訊頁面，該頁面顯示 [相似](type.md#visualsim) 查看的產品。 這種推薦類型在產品的影像和視覺方面是購物體驗的重要組成部分時最為有用。 安裝 _視覺相似性_ 通過運行以下命令執行建議類型：

```bash
composer require magento/module-visual-product-recommendations
```

## 配置 [!DNL Product Recommendations] {#configure}

安裝後 `magento/product-recommendations` 模組，必須配置 [Commerce Services連接器](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) 指定API密鑰並選擇SaaS資料空間。

要確保目錄導出正確運行，請確認 [克隆](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) 工作和 [索引器](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) 正在運行 `Product Feed` 索引器設定為 `Update by Schedule`。

通過API鍵成功連結到Commerce Services並指定SaaS資料空間時，目錄同步將開始。 你可以 [驗證](verify.md) 行為資料被發到你的店面。

## 更新 [!DNL Product Recommendations] 安裝 {#update}

和Adobe Commerce一樣， [!DNL Product Recommendations] 使用Composer進行安裝和更新。 更新 `magento/product-recommendations` 模組，運行以下命令：

```bash
composer update magento/product-recommendations --with-dependencies
```

要更新到主版本，如從3.0到4.0，必須編輯根 `composer.json` 檔案。 (請參閱 [發行說明](release-notes.md) 有關最新版本的資訊。) 例如，開啟主 `composer.json` 檔案和搜索 `magento/product-recommendations` 模組：

```json
"require": {
    ...
    "magento/product-recommendations": "^3.0",
    ...
}
```

讓我們把主版本從 `3.0` 至 `4.0`:

```json
"require": {
    ...
    "magento/product-recommendations": "^4.0",
    ...
}
```

保存 `composer.json` 檔案和運行：

```bash
composer update magento/product-recommendations --with-dependencies
```

或者，如果您安裝了 `magento/module-visual-product-recommendations` 和 `magento/module-page-builder-product-recommendations` 模組：

```bash
composer update --with-dependencies magento/product-recommendations magento/module-visual-product-recommendations magento/module-page-builder-product-recommendations
```

>[!NOTE]
>
> 在產品Recommendations的3.x.x版中，您只需一個API密鑰。 在4.x.x版和更高版本中，必須提供生產公用和專用API密鑰以及沙盒公用和專用API密鑰。 如果不提供兩對API密鑰，則無法訪問管理中的產品Recommendations功能。 但是，資料收集將繼續在您的商店中，現有建議將繼續顯示給您的購物者。

## 卸載 [!DNL Product Recommendations] {#uninstall}

如有必要，你可以 [卸載](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html) 產品建議模組。
