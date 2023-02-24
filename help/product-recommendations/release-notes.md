---
title: '[!DNL Product Recommendations] 發行說明'
description: 的最新發行資訊 [!DNL Product Recommendations] 從Adobe Commerce。
exl-id: 1758e688-d26f-45e7-818c-d4726338a6c3
source-git-commit: fd3f71a1b3d958f3aa79f0ba6603d30e16e70507
workflow-type: tm+mt
source-wordcount: '975'
ht-degree: 0%

---

# [!DNL Product Recommendations] 發行說明

發行說明包含下列更新 [!DNL Product Recommendations] 模組：

* [!DNL Product Recommendations] 元包： `magento/product-recommendations`
* 中的頁面產生器支援 [!DNL Product Recommendations] （可選）模組： `magento/module-page-builder-product-recommendations`
* 支援的視覺相似度建議類型 [!DNL Product Recommendations] （可選）模組： `magento/module-visual-product-recommendations`

發行說明包括：

![新增](../assets/new.svg) 新功能
![修正](../assets/fix.svg) 修正和改良

請參閱開發人員檔案，以 [了解產品相容性](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## 最新主要版本

### 4.0.1 magento/product-recommendations

![修正](../assets/fix.svg) 之前，產品Recommendations會在顯示貨幣切換為非預設貨幣時顯示錯誤。 切換貨幣現在可正常運作。

### 4.0.0 magento/product-recommendations

![新增](../assets/new.svg) 新增 [就緒指標](create.md) 可協助您視覺化每種建議類型的訓練進度。
![新增](../assets/new.svg) 這是主要版本。 [編輯](install-configure.md#update) 根 `composer.json` 檔案。 此版本也要求您在安裝和設定產品Recommendations時提供兩個API金鑰： [生產金鑰和沙箱金鑰](../landing/saas.md).

#### 已知限制

* 此 `websiteCode` 如果值包含底線(_)，則會錯誤地傳回值。

### 舊版

+++3.3.7和之前版本

### 3.3.7 magento/product-recommendations

![新增](../assets/new.svg) 新增PHP 8.1支援
![新增](../assets/new.svg) 改善影像大小調整功能，以便在參考顯示範本中更一致地處理影像大小調整

### 3.3.6 magento/product-recommendations

![新增](../assets/new.svg) 最佳化 [!DNL Product Recommendations] 明確列出依賴項

### 3.3.5 magento/product-recommendations

![新增](../assets/new.svg) 新增 [B2B支援](onboarding.md#b2bsupport) 在產品Recommendations
![新增](../assets/new.svg) 新增摘要至 [同步目錄資料](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) 到Commerce Services

### 3.3.3 magento/product-recommendations

![新增](../assets/new.svg) 新增 [建議類型](type.md):轉換（檢視到購物車）、轉換（檢視到購買）和最近查看。 這些新建議類型可在 `magento/product-recommendations` 模組3.2.2和更新版本。
![修正](../assets/fix.svg) 修正Ambeyt的Web應用程式防火牆(WAF)錯誤封鎖Cookie的問題
![修正](../assets/fix.svg) 修正指派給非預設商店檢視的產品未顯示在 _Recommendations產品預覽_ 面板
![修正](../assets/fix.svg) 修正頁面產生器中某些建議單位名稱無法讓建議單位顯示在店面的問題

### 3.3.2 magento/product-recommendations

![修正](../assets/fix.svg) 修正B2B支援缺少相依性的問題

### 3.3.1 magento/product-recommendations

![新增](../assets/new.svg) 新增對B2B客戶群組定價的支援。 當您設定 [價格篩選](filters.md) 在建議單位上，已登入的B2B客戶會看見所顯示產品的客戶群組定價集。

### magento/product-recommendations的3.3.0

![新增](../assets/new.svg) 新增對Adobe用戶端資料層的支援，以標準化跨Adobe Commerce功能和服務的行為資料收集。 請參閱 [讀我檔案](https://github.com/adobe/magento-storefront-event-collector/blob/main/README.md) 了解更多。

### 3.2.6 magento/product-recommendations

![修正](../assets/fix.svg) 修正JavaScript強制回應錯誤
![修正](../assets/fix.svg) 修正Ambeyt的Web應用程式防火牆(WAF)錯誤封鎖Cookie的問題

### 3.2.5 magento/product-recommendations

![新增](../assets/new.svg) 將Magento服務重新命名為 [商務服務](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) 並改善「管理員」中的可用性

### 3.2.4 magento/product-recommendations

![修正](../assets/fix.svg) 修正了在索引產品屬性時，「無法擷取可設定產品選項資料」錯誤

### 3.2.3 magento/product-recommendations

![修正](../assets/fix.svg) 修正目錄同步期間「無法擷取可設定產品選項資料」錯誤
![修正](../assets/fix.svg) 修正當您啟用「新增商店代碼至URL」設定時，商店代碼未正確設定的問題
![修正](../assets/fix.svg) 改善「管理面板」組態變更的偵測，確保這些變更反映在「目錄同步」資料中

### 3.2.2 magento/product-recommendations

![新增](../assets/new.svg) 將 [預覽建議結果](create.md) 在建立時。 您可能需要將模組更新至最新版本。
![新增](../assets/new.svg) 將 [監視和管理](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) 管理員的目錄同步程式。
![新增](../assets/new.svg) 新增 [篩選器](filters.md) 控制建議中顯示的產品。
![新增](../assets/new.svg) 新增 [視覺相似度](type.md#visualsim) 建議類型。

### 1.2.1針對頁面產生器的magento/module-page-builder-product-recommendations

![新增](../assets/new.svg) 新增對3.2.0+版的支援， `magento/product-recommendations` 模組

### 3.1.0 magento/product-recommendations

![新增](../assets/new.svg) 將 [重新同步](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) 通過命令行將目錄發送到SaaS服務。
![新增](../assets/new.svg) 新增對資料庫表前置詞的支援
![修正](../assets/fix.svg) 移除PHP 7.1支援

### 3.0.8 magento/product-recommendations

![修正](../assets/fix.svg) 修正在設定模組之前，為資料收集傳送事件，導致無效流量的問題

### 3.0.6 magento/product-recommendations

![新增](../assets/new.svg) **（測試版）** 包括對新 [視覺相似度](type.md#visualsim) 建議類型。

### 1.0.0 magento/module-visual-product-recommendations

![新增](../assets/new.svg) **（測試版）** [視覺相似度](type.md#visualsim). 使用 _視覺相似度_ 建議類型，您可以將建議單位部署至產品詳細資料頁面，該頁面會顯示視覺上類似於正在檢視之產品的產品。

### 3.0.5 magento/product-recommendations

![修正](../assets/fix.svg) 修正了目錄匯出期間可能發生的「無法擷取產品選項資料」錯誤。
![修正](../assets/fix.svg) 貨幣符號，位於 _收入_ 欄 _產品Recommendations_ 控制面板現在會正確反映設定的基本貨幣。

### 3.0.4 magento/product-recommendations

![修正](../assets/fix.svg) 新增對Adobe Commerce 2.4.0的支援

### 3.0.3 magento/product-recommendations

![修正](../assets/fix.svg) 改善店面範本中的符號實作

### 1.0.4針對頁面產生器的magento/module-page-builder-product-recommendations

![新增](../assets/new.svg) 新增編輯頁面產生器內容類型時的產品建議名稱

### 3.0.2 magento/product-recommendations

![新增](../assets/new.svg) 在頁面產生器中選取建議單位時，在格線上新增狀態欄
![修正](../assets/fix.svg) 修正產品和影像URL中http/https通訊協定錯誤的問題

### 3.0.1 magento/product-recommendations

這是主要版本。 [編輯](install-configure.md#update) 您專案的根composer.json檔案。

![新增](../assets/new.svg) 擷取 [!DNL Product Recommendations] 從備用SaaS資料空間。 這可讓您將在產品環境中計算的產品建議用於其他非生產環境。 [切換SaaS資料空間](settings.md) 進一步說明此功能。

![修正](../assets/fix.svg) 修正使用「區塊來源」的購物者無法結帳的問題
![修正](../assets/fix.svg) 修正傳送無關附加至購物車事件的問題

### 1.0.3針對頁面產生器的magento/module-page-builder-product-recommendations

![新增](../assets/new.svg) 頁面產生器支援。 透過頁面產生器整合，您可以在頁面產生器撰寫的內容上，將建議單位精確精細地放置在任何任意位置。 您也可以設定標題和建議單位本身的樣式。 前往 [頁面產生器](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) 以取得更多資訊。

### 2.0.0 magento/product-recommendations

![新增](../assets/new.svg) 正式發行！

+++

## 檔案

若要深入了解 [!DNL Product Recommendations] 和 [!DNL Product Recommendations] 開發：

* [使用手冊](overview.md)
* [開發人員檔案](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/development-overview.html)
