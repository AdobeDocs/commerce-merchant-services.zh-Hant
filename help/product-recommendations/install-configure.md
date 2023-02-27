---
title: 安裝和配置
description: 了解如何安裝、更新和解除安裝 [!DNL Product Recommendations].
exl-id: fa599f72-1064-41da-ac54-2b3a3c16a1fe
source-git-commit: d56fd57281a5b675e128cca75d4057756a0bf4bf
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# 安裝和配置

部署 [!DNL Product Recommendations] 前端和管理員要求您安裝模組並設定 [商務服務連接器](../landing/saas.md). 隨著更新的發佈，您可以輕鬆地使用最新版本更新您的安裝。

- [安裝](#install)
- [設定](#configure)
- [更新](#update)
- [解除安裝](#uninstall)

## 安裝 [!DNL Product Recommendations] {#install}

因為 [!DNL Product Recommendations] 模組是獨立的元資料包，更新的發佈頻率比Adobe Commerce更高。 若要確認您擁有最新的錯誤修正和功能，請參閱 [發行說明](release-notes.md).

安裝 `magento/product-recommendations` 具有撰寫器的模組：

```bash
composer require magento/product-recommendations
```

### 新增頁面產生器支援 {#pbsupport}

[!DNL Product Recommendations] for Page Builder是選用模組，需另外安裝。 使用 [!DNL Product Recommendations] 使用Page Builder，執行下列命令以安裝模組：

```bash
composer require magento/module-page-builder-product-recommendations
```

啟用 [!DNL Product Recommendations] 在「頁面產生器」中，您可以新增現有的作用中 [建議單位](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) 至在「頁面產生器」中建立的任何內容，例如頁面、區塊和動態區塊。

請參閱 [使用 [!DNL Product Recommendations] 搭配頁面產生器內容](page-builder.md) 以取得進一步指示。

### 新增視覺相似度建議類型 {#vissimsupport}

此 _視覺相似度_ 建議類型可讓您將建議單元部署至顯示產品的產品詳細資料頁面 [視覺相似](type.md#visualsim) 至被檢視的產品。 如果產品的影像和視覺方面是購物體驗的重要部分，此建議類型就十分實用。 安裝 _視覺相似度_ 建議類型，方法是執行下列命令：

```bash
composer require magento/module-visual-product-recommendations
```

## 設定 [!DNL Product Recommendations] {#configure}

安裝 `magento/product-recommendations` 模組，您必須設定 [商務服務連接器](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) 指定API密鑰並選擇SaaS資料空間。

若要確保目錄匯出正確執行，請確認 [cron](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) 工作和 [索引器](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) 執行中 `Product Feed` 索引器設定為 `Update by Schedule`.

當您通過API密鑰成功連結到Commerce Services並指定SaaS資料空間時，目錄同步將開始。 然後 [驗證](verify.md) 行為資料會傳送到您的店面。

## 更新您的 [!DNL Product Recommendations] 安裝 {#update}

和Adobe Commerce一樣， [!DNL Product Recommendations] 使用撰寫器進行安裝和更新。 若要更新 `magento/product-recommendations` 模組，運行以下內容：

```bash
composer update magento/product-recommendations --with-dependencies
```

若要更新為主要版本，例如從3.0更新為4.0，您必須編輯根 `composer.json` 檔案。 (請參閱 [發行說明](release-notes.md) 以取得最新版本的相關資訊。) 例如，開啟主要 `composer.json` 檔案和搜尋 `magento/product-recommendations` 模組：

```json
"require": {
    ...
    "magento/product-recommendations": "^3.0",
    ...
}
```

讓我們從 `3.0` to `4.0`:

```json
"require": {
    ...
    "magento/product-recommendations": "^4.0",
    ...
}
```

儲存 `composer.json` 檔案和運行：

```bash
composer update magento/product-recommendations --with-dependencies
```

或者，如果您已安裝 `magento/module-visual-product-recommendations` 和 `magento/module-page-builder-product-recommendations` 模組：

```bash
composer update --with-dependencies magento/product-recommendations magento/module-visual-product-recommendations magento/module-page-builder-product-recommendations
```

>[!NOTE]
>
> 在Product Recommendations 3.x.x版中，您只需要單一API金鑰。 在4.x.x版及更新版本中，您必須提供生產公開和私人API金鑰，以及沙箱公開和私人API金鑰。 如果您未提供兩組API金鑰，將無法存取「管理」中的「產品Recommendations」功能。 不過，資料收集會繼續在您的店面進行，而現有的建議會繼續顯示給您的購物者。

## 解除安裝 [!DNL Product Recommendations] {#uninstall}

如有必要，您可以 [解除安裝](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html) product-recommendations模組。
