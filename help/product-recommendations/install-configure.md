---
title: 安裝與設定
description: 瞭解如何安裝、更新及解除安裝 [!DNL Product Recommendations]。
exl-id: fa599f72-1064-41da-ac54-2b3a3c16a1fe
role: Admin, Developer
source-git-commit: 96a5791c5716f612f473540f27bd3f99b1bfe7c8
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# 安裝與設定

將[!DNL Product Recommendations]部署至您的店面和管理員，需要您安裝模組並設定[Commerce Services Connector](../landing/saas.md)。 在發行更新時，您可以使用最新版本輕鬆更新安裝。

- [安裝](#install)
- [設定](#configure)
- [更新](#update)
- [解除安裝](#uninstall)

## 安裝[!DNL Product Recommendations] {#install}

由於[!DNL Product Recommendations]模組是獨立的中繼套件，因此比Adobe Commerce更頻繁地發行更新。 若要確定您使用最新的錯誤修正和功能，請參閱[發行說明](release-notes.md)。

使用撰寫器安裝`magento/product-recommendations`模組：

```bash
composer require magento/product-recommendations
```

### 新增頁面產生器支援 {#pbsupport}

Page Builder的[!DNL Product Recommendations]為選用模組，需另行安裝。 若要搭配Page Builder使用[!DNL Product Recommendations]，請執行以下命令來安裝模組：

```bash
composer require magento/module-page-builder-product-recommendations
```

透過在頁面產生器中啟用[!DNL Product Recommendations]，您可以將現有的作用中[建議單位](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html)新增到頁面產生器中建立的任何內容，例如頁面、區塊和動態區塊。

如需進一步說明，請參閱[搭配頁面產生器內容](page-builder.md)使用 [!DNL Product Recommendations] 。

### 新增視覺相似度推薦型別 {#vissimsupport}

_視覺相似度_&#x200B;建議型別可讓您將建議單位部署至產品詳細資料頁面，該頁面會顯示與正在檢視的產品[視覺上類似](type.md#visualsim)的產品。 當產品的影像和視覺方面是購物體驗的重要部分時，此建議型別最有用。 執行下列命令，安裝&#x200B;_視覺相似度_&#x200B;建議型別：

```bash
composer require magento/module-visual-product-recommendations
```

## 設定[!DNL Product Recommendations] {#configure}

安裝`magento/product-recommendations`模組後，您必須指定API金鑰並選取SaaS資料空間，以設定[Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html)。

若要確保目錄匯出正在正確執行，請確認[cron](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html)工作和[索引子](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)正在執行，且`Product Feed`索引子設定為`Update by Schedule`。

當您透過API金鑰成功連結至Commerce服務並指定SaaS資料空間時，目錄同步就會開始。 然後，您可以[驗證](verify.md)行為資料正在傳送至您的店面。

## 更新您的[!DNL Product Recommendations]安裝 {#update}

如同所有的Adobe Commerce，[!DNL Product Recommendations]使用Composer進行安裝和更新。 若要更新`magento/product-recommendations`模組，請執行下列動作：

```bash
composer update magento/product-recommendations --with-dependencies
```

若要更新為主要版本，例如從3.0到4.0，您必須編輯專案的根`composer.json`檔案。 （如需最新版本的相關資訊，請參閱[發行說明](release-notes.md)。） 例如，讓我們開啟主要`composer.json`檔案並搜尋`magento/product-recommendations`模組：

```json
"require": {
    ...
    "magento/product-recommendations": "^3.0",
    ...
}
```

讓我們將主要版本從`3.0`增加到`4.0`：

```json
"require": {
    ...
    "magento/product-recommendations": "^4.0",
    ...
}
```

儲存`composer.json`檔案並執行：

```bash
composer update magento/product-recommendations --with-dependencies
```

或者，如果您已安裝`magento/module-visual-product-recommendations`與`magento/module-page-builder-product-recommendations`模組：

```bash
composer update --with-dependencies magento/product-recommendations magento/module-visual-product-recommendations magento/module-page-builder-product-recommendations
```

>[!NOTE]
>
> 在產品Recommendations 3.x.x版中，您只需要單一API金鑰。 在4.x.x版及更新版本中，您必須提供生產用公開和私人API金鑰，以及沙箱公開和私人API金鑰。 如果您未提供這兩組API金鑰，將無法在「管理員」中存取「產品Recommendations」功能。 不過，資料收集仍會繼續存在於您的店面，而現有的建議仍會繼續向您的購物者顯示。

## 防火牆

若要讓產品Recommendations通過防火牆，請新增`commerce.adobe.io`至允許清單。

## 解除安裝[!DNL Product Recommendations] {#uninstall}

如有必要，您可以[解除安裝](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html)產品建議模組。
