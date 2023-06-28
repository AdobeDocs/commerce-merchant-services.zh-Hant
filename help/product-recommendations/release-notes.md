---
title: '''[!DNL Product Recommendations] 發行說明'
description: 的最新版本資訊 [!DNL Product Recommendations] 來自Adobe Commerce。
exl-id: 1758e688-d26f-45e7-818c-d4726338a6c3
source-git-commit: 326b852b67d4f4160badc652b24853df3a8de644
workflow-type: tm+mt
source-wordcount: '1102'
ht-degree: 0%

---

# [!DNL Product Recommendations] 發行說明

發行說明包含下列專案的更新 [!DNL Product Recommendations] 模組：

* [!DNL Product Recommendations] 中繼套件： `magento/product-recommendations`
* 中的頁面產生器支援 [!DNL Product Recommendations] （選用）模組： `magento/module-page-builder-product-recommendations`
* 的視覺相似度推薦型別支援 [!DNL Product Recommendations] （選用）模組： `magento/module-visual-product-recommendations`

提供目前主要發行版本的支援。 舊版的發行說明僅供參考。
發行說明包括：

![新增](../assets/new.svg) 新功能
![修正](../assets/fix.svg) 修正和改良
![錯誤](../assets/bug.svg) 已知問題

請參閱開發人員檔案，以 [瞭解產品相容性](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## 目前的主要版本

_2023年4月25日_

![新增](../assets/new.svg) Recommendations客戶現在可以利用的產品 [SaaS價格索引](../price-index/index.md).

### 5.0.0的magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 更新產品Recommendations以支援Adobe Commerce 2.4.6。
![新增](../assets/new.svg) 此為主要版本發行版本。 [編輯](install-configure.md#update) 根 `composer.json` 專案的檔案。

#### 已知限制

* 此 `websiteCode` 如果值包含底線(_)，則傳回的值不正確。

### 舊版

+++4.0.1和舊版

### 4.0.1版magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![修正](../assets/fix.svg) 以前，當顯示貨幣切換為非預設貨幣時，產品Recommendations會顯示錯誤。 現在切換貨幣可正常運作。

### 4.0.0的magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 已新增 [整備程度指標](create.md) 協助您視覺化每個建議型別的培訓進度。
![新增](../assets/new.svg) 此為主要版本發行版本。 [編輯](install-configure.md#update) 根 `composer.json` 專案的檔案。 此版本也要求您在安裝和設定Product Recommendations時提供兩個API金鑰： [生產金鑰和沙箱金鑰](../landing/saas.md).

#### 已知限制

* 此 `websiteCode` 如果值包含底線(_)，則傳回的值不正確。

### 3.3.7的magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 新增PHP 8.1支援
![新增](../assets/new.svg) 改善影像調整大小，使參考顯示範本中的影像大小調整更一致

### 3.3.6的magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 已最佳化 [!DNL Product Recommendations] 透過明確列出相依性進行中繼包

### 3.3.5的magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 已新增 [B2B支援](onboarding.md#b2bsupport) 在產品Recommendations中
![新增](../assets/new.svg) 已將新摘要新增至 [同步目錄資料](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) 至商務服務（透過命令列）

### 3.3.3的magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 已新增 [建議型別](type.md)：轉換（檢視到購物車）、轉換（檢視到購買）和最近檢視。 這些新建議型別可在 `magento/product-recommendations` 模組3.2.2和更新版本。
![修正](../assets/fix.svg) 修正Fastly的Web應用程式防火牆(WAF)無法正確封鎖Cookie的問題
![修正](../assets/fix.svg) 修正指派給非預設存放區檢視的產品未顯示於 _Recommendations產品預覽_ 建立該特定存放區檢視的建議時的面板
![修正](../assets/fix.svg) 修正Page Builder中某些建議單位名稱無法顯示於店面的問題

### 3.3.2版magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![修正](../assets/fix.svg) 修正B2B支援的遺失相依性

### 3.3.1的magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 新增B2B客戶群組定價支援。 當您設定 [價格篩選](filters.md) 在建議單位上，登入的B2B客戶會看到所顯示產品的客戶群組訂價集。

### 3.3.0的magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 新增對Adobe Client Data Layer的支援，以標準化跨Adobe Commerce功能與服務的行為資料收集。 請參閱 [讀我檔案](https://github.com/adobe/magento-storefront-event-collector/blob/main/README.md) 以深入瞭解。

### 3.2.6的magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![修正](../assets/fix.svg) 修正JavaScript強制回應錯誤
![修正](../assets/fix.svg) 修正Fastly的Web應用程式防火牆(WAF)無法正確封鎖Cookie的問題

### 3.2.5的magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 將Magento服務重新命名為 [Commerce服務](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) 並改善管理員的可用性

### 3.2.4的magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![修正](../assets/fix.svg) 修正索引產品屬性時「無法擷取可設定的產品選項資料」錯誤

### 3.2.3的magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![修正](../assets/fix.svg) 修正目錄同步期間的「無法擷取可設定的產品選項資料」錯誤
![修正](../assets/fix.svg) 修正啟用「將存放區代碼新增至URL」設定時，存放區代碼未正確設定的問題
![修正](../assets/fix.svg) 改善對Admin Panel設定變更的偵測功能，以確保這些變更會反映在目錄同步處理資料中

### 3.2.2的magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 新增以下功能： [預覽推薦結果](create.md) 建立時。 這可能需要您將模組更新至最新版本。
![新增](../assets/new.svg) 新增以下功能： [監視和管理](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) 管理員的目錄同步程式。
![新增](../assets/new.svg) 已新增 [篩選器](filters.md) 控制要在建議中顯示的產品。
![新增](../assets/new.svg) 已新增 [視覺相似度](type.md#visualsim) 建議型別。

### 1.2.1 magento/module-page-builder-product-recommendations for Page Builder

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 新增對3.2.0+版本的 `magento/product-recommendations` 模組

### 3.1.0的magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 新增以下功能： [重新同步](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) 透過命令列將目錄傳送至SaaS服務。
![新增](../assets/new.svg) 新增支援資料庫表格首碼
![修正](../assets/fix.svg) 移除PHP 7.1支援

### 3.0.8個magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![修正](../assets/fix.svg) 修正設定模組前，針對資料收集傳送事件，造成流量無效的問題

### 3.0.6版magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) **(Beta)** 包含對新增功能的支援 [視覺相似度](type.md#visualsim) 建議型別。

### 1.0.0 magento/module-visual-product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) **(Beta)** [視覺相似度](type.md#visualsim). 使用 _視覺相似度_ 建議型別，您可以將建議單位部署至產品詳細資料頁面，該頁面顯示視覺上類似正在檢視之產品的產品。

### 3.0.5個magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![修正](../assets/fix.svg) 修正在目錄匯出期間可能發生的「無法擷取產品選項資料」錯誤。
![修正](../assets/fix.svg) 中的貨幣符號 _收入_ 上的欄 _產品Recommendations_ 儀表板現在可正確反映設定的基本貨幣。

### 3.0.4個magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![修正](../assets/fix.svg) 新增對Adobe Commerce 2.4.0的支援

### 3.0.3個magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![修正](../assets/fix.svg) 改善店面範本中的符號實作

### 1.0.4 magento/module-page-builder-product-recommendations for Page Builder

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 在編輯Page Builder內容型別時新增產品推薦名稱

### 3.0.2 magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 在Page Builder中選取「建議單位」時，在網格上新增狀態列
![修正](../assets/fix.svg) 修正產品和影像URL中http/https通訊協定不正確的問題

### 3.0.1的magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

此為主要版本發行版本。 [編輯](install-configure.md#update) 您專案的根composer.json檔案。

![新增](../assets/new.svg) 擷取 [!DNL Product Recommendations] 來自替代SaaS資料空間。 這可讓您在其他非生產環境中使用產品環境中計算的產品推薦。 [切換SaaS資料空間](settings.md) 進一步說明此功能。

![修正](../assets/fix.svg) 修正使用uBlock Origin禁止購物者結帳的問題
![修正](../assets/fix.svg) 修正傳送無關的購物車加值專案事件的問題

### 1.0.3 magento/module-page-builder-product-recommendations for Page Builder

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) Page Builder支援。 透過Page Builder整合，您可以準確且詳細地將Recommendation單位放置在Page Builder編寫內容上的任何位置。 您也可以設定標題與建議單位本身的樣式。 前往 [頁面產生器](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) 以取得詳細資訊。

### 2.0.0個magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 正式發行！

+++

## 檔案

若要深入瞭解 [!DNL Product Recommendations] 和 [!DNL Product Recommendations] 開發：

* [使用手冊](overview.md)
* [開發人員檔案](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/development-overview.html)
