---
title: 『[!DNL Product Recommendations] 版本注意事項
description: 的最新版本資訊 [!DNL Product Recommendations] 來自Adobe Commerce。
exl-id: 1758e688-d26f-45e7-818c-d4726338a6c3
feature: Services, Recommendations, Release Notes
source-git-commit: 6f31361e95b17ee3fa19ff3c2f4a7e2d6d9bc091
workflow-type: tm+mt
source-wordcount: '1376'
ht-degree: 0%

---

# [!DNL Product Recommendations] 發行說明

發行說明包含下列專案的更新 [!DNL Product Recommendations] 模組：

* [!DNL Product Recommendations] 中繼封裝： `magento/product-recommendations`
* 中的頁面產生器支援 [!DNL Product Recommendations] （選用）模組： `magento/module-page-builder-product-recommendations`
* 的視覺相似度推薦型別支援 [!DNL Product Recommendations] （選用）模組： `magento/module-visual-product-recommendations`

支援目前的主要發行版本。 舊版的發行說明僅供參考。
發行說明包括：

![新增](../assets/new.svg) 新功能
![修正](../assets/fix.svg) 修正和改良
![錯誤](../assets/bug.svg) 已知問題

請參閱開發人員檔案以 [瞭解產品支援](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability).

## 託管服務更新

這些附註說明在版本化版本發行之外發佈或發現的更新或已知問題，或對託管服務的改進。

_2024年6月28日_

![錯誤](../assets/bug.svg) 從新增至購物車的產品 [!DNL Product Recommendations] 當購物車頁面重新載入時，購物車頁面上的單位並未從建議產品清單中移除。
![錯誤](../assets/bug.svg) 從購物車中移除的產品會繼續留在 `cartSkus` 陣列，直到購物車頁面重新載入為止。

_2023年7月18日_

![新增](../assets/new.svg) [!DNL Product Recommendations] 現在有GraphQL [`recommendations`](https://developer.adobe.com/commerce/services/graphql/recommendations/recommendations/) 查詢。

_2023年4月25日_

![新增](../assets/new.svg) [!DNL Product Recommendations] 客戶現在可以利用 [SaaS價格索引](../price-index/price-indexing.md).

## 目前的主要版本

### 6.0.2的magento/product-recommendations

_2024年5月9日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![修正](../assets/fix.svg) 修正按一下 **[!DNL Add to Cart]** 產品Recommendations單位內簡單產品上的按鈕將購物者重新導向首頁，而非停留在目前頁面。
![錯誤](../assets/bug.svg) 發生驗證錯誤，原因為 `referenceBlock` 中的元素 `ProductRecommendations Layout` XML檔案。

### 舊版

### 6.0.1的magento/product-recommendations

_2024年3月19日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 新增PHP 8.3支援。

### 6.0.0的magento/product-recommendations

_2024年2月22日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 此 [!DNL Catalog Sync Dashboard] 現在是 [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). 此改版後的儀表板提供資料串流的深入分析 [!DNL Product Recommendations]， [!DNL Live Search]、和 [!DNL Catalog Service].
![修正](../assets/fix.svg) 修正導致下列專案的簽出錯誤的問題 [!DNL Product Recommendations].

+++5.0.0和舊版

### 5.0.1的magento/product-recommendations

_2023年9月15日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 已新增模組以支援 [Saas價格索引器](../price-index/price-indexing.md).
![新增](../assets/new.svg) 新增新的資料匯出模組，以支援匯出更多產品型別，包括套件產品和禮品卡。
![修正](../assets/fix.svg) 產品和價格摘要的表格大小已大幅縮減。 表格 `catalog_data_exporter_products` 和 `catalog_data_exporter_product_prices` 應該會大幅縮減規模。

#### 已知限制

* 此 `websiteCode` 如果值包含底線(_)，則傳回的值不正確。

### 5.0.0的magento/product-recommendations

_2023年3月20日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 已更新 [!DNL Product Recommendations] 以支援Adobe Commerce 2.4.6。
![新增](../assets/new.svg) 此為主要版本發行版本。 [編輯](install-configure.md#update) 根 `composer.json` 您的專案的檔案。
![新增](../assets/new.svg) [!DNL Product Recommendations] 現在支援完整 [Inventory management](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) Commerce (先前稱為多Source詳細目錄，或MSI)中的功能。 若要啟用完整支援，您必須 [更新](install-configure.md#update) 相依性模組 `commerce-data-export` 至102.2.0+版。

### 4.0.1的magento/product-recommendations

[!BADGE 支援]{type=Informative tooltip="支援"}

![修正](../assets/fix.svg) 先前， [!DNL Product Recommendations] 將顯示貨幣切換為非預設貨幣時的錯誤。 現在切換貨幣已可正常運作。

### 4.0.0的magento/product-recommendations

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 已新增 [整備程度指標](create.md) 協助您視覺化每個建議型別的培訓進度。
![新增](../assets/new.svg) 此為主要版本發行版本。 [編輯](install-configure.md#update) 根 `composer.json` 您的專案的檔案。 此版本也要求您在安裝和設定時提供兩個API金鑰 [!DNL Product Recommendations]： [生產金鑰和沙箱金鑰](../landing/saas.md).

#### 已知限制

* 此 `websiteCode` 如果值包含底線(_)，則傳回的值不正確。

### 3.3.7的magento/product-recommendations

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 新增PHP 8.1支援
![新增](../assets/new.svg) 改善影像調整大小，讓影像大小調整在參考顯示範本中可以更一致地處理

### 3.3.6的magento/product-recommendations

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 已最佳化 [!DNL Product Recommendations] 透過明確列出相依性進行中繼

### 3.3.5的magento/product-recommendations

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 已新增 [B2B支援](onboarding.md#b2bsupport) 在 [!DNL Product Recommendations]
![新增](../assets/new.svg) 已新增摘要至 [同步目錄資料](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/data-services/catalog-sync) 透過命令列移至Commerce服務

### 3.3.3的magento/product-recommendations

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 已新增 [建議型別](type.md)：轉換（檢視到購物車）、轉換（檢視到購買）和最近檢視。 這些新建議型別可在 `magento/product-recommendations` 模組3.2.2和更新版本。
![修正](../assets/fix.svg) 修正Fastly的Web應用程式防火牆(WAF)無法正確封鎖Cookie的問題
![修正](../assets/fix.svg) 修正指派給非預設存放區檢視的產品未顯示在 _Recommendations產品預覽_ 建立該特定存放區檢視的建議時的面板
![修正](../assets/fix.svg) 修正Page Builder中某些建議單位名稱無法讓建議單位顯示在店面的問題

### 3.3.2的magento/product-recommendations

[!BADGE 支援]{type=Informative tooltip="支援"}

![修正](../assets/fix.svg) 修正B2B支援的相依性遺失

### 3.3.1的magento/product-recommendations

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 新增B2B客戶群組定價支援。 當您設定 [價格篩選](filters.md) 在建議單位上，登入的B2B客戶會看到所顯示產品的客戶群組訂價集。

### 3.3.0的magento/product-recommendations

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 新增Adobe Client Data Layer支援，標準化跨Adobe Commerce功能與服務的行為資料收集。 請參閱 [讀我檔案](https://github.com/adobe/commerce-events/blob/main/packages/storefront-events-collector/README.md) 以進一步瞭解。

### 3.2.6的magento/product-recommendations

[!BADGE 支援]{type=Informative tooltip="支援"}

![修正](../assets/fix.svg) 修正JavaScript強制回應錯誤
![修正](../assets/fix.svg) 修正Fastly的Web應用程式防火牆(WAF)無法正確封鎖Cookie的問題

### 3.2.5的magento/product-recommendations

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 將Magento服務重新命名為 [Commerce服務](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/integration-services/saas) 並改善管理員中的可用性

### 3.2.4的magento/product-recommendations

[!BADGE 支援]{type=Informative tooltip="支援"}

![修正](../assets/fix.svg) 修正編制產品屬性索引時「無法擷取可設定的產品選項資料」錯誤

### 3.2.3的magento/product-recommendations

[!BADGE 支援]{type=Informative tooltip="支援"}

![修正](../assets/fix.svg) 修正目錄同步處理期間的「無法擷取可設定的產品選項資料」錯誤
![修正](../assets/fix.svg) 修正啟用「將存放區代碼新增至URL」設定時，存放區代碼未正確設定的問題
![修正](../assets/fix.svg) 改善偵測管理員面板設定變更的功能，以確保這些變更會反映在目錄同步處理資料中

### 3.2.2的magento/product-recommendations

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 新增以下功能： [預覽推薦結果](create.md) 在建立時。 您可能需要將模組更新至最新版本。
![新增](../assets/new.svg) 新增以下功能： [監視和管理](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/data-services/catalog-sync) 管理員的目錄同步程式。
![新增](../assets/new.svg) 已新增 [篩選器](filters.md) 控制要在建議中顯示的產品。
![新增](../assets/new.svg) 已新增 [視覺相似度](type.md#visualsim) 建議型別。

### 1.2.1適用於Page Builder的magento/module-page-builder-product-recommendations

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 新增對3.2.0+版本的 `magento/product-recommendations` 模組

### 3.1.0的magento/product-recommendations

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 新增以下功能： [重新同步](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/data-services/catalog-sync) 透過命令列將目錄傳送至SaaS服務。
![新增](../assets/new.svg) 新增支援資料庫表格首碼
![修正](../assets/fix.svg) 移除PHP 7.1支援

### 3.0.8個magento/product-recommendations

[!BADGE 支援]{type=Informative tooltip="支援"}

![修正](../assets/fix.svg) 修正在設定模組之前傳送資料收集事件的問題，此問題會導致無效的流量

### 3.0.6的magento/product-recommendations

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) **(Beta)** 包含對新增功能的支援 [視覺相似度](type.md#visualsim) 建議型別。

### 1.0.0 magento/module-visual-product-recommendations

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) **(Beta)** [視覺相似度](type.md#visualsim). 使用 _視覺相似度_ 建議型別，您可以將建議單位部署至產品詳細資料頁面，該頁面會顯示與正在檢視之產品視覺上類似的產品。

### 3.0.5的magento/product-recommendations

[!BADGE 支援]{type=Informative tooltip="支援"}

![修正](../assets/fix.svg) 修正在目錄匯出期間可能發生的「無法擷取產品選項資料」錯誤。
![修正](../assets/fix.svg) 中的貨幣符號 _收入_ 上的欄 _[!DNL Product Recommendations]_儀表板現在會正確反映設定的基本貨幣。

### 3.0.4的magento/product-recommendations

[!BADGE 支援]{type=Informative tooltip="支援"}

![修正](../assets/fix.svg) 新增對Adobe Commerce 2.4.0的支援

### 3.0.3的magento/product-recommendations

[!BADGE 支援]{type=Informative tooltip="支援"}

![修正](../assets/fix.svg) 改善店面範本中的符號實作

### 1.0.4 magento/module-page-builder-product-recommendations for Page Builder

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 新增編輯「頁面產生器」內容型別時的產品推薦名稱

### 3.0.2 magento/product-recommendations

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 在Page Builder中選取「建議單位」時，在網格上新增狀態列
![修正](../assets/fix.svg) 已修正產品和影像URL中不正確的http/https通訊協定問題

### 3.0.1的magento/product-recommendations

[!BADGE 支援]{type=Informative tooltip="支援"}

此為主要版本發行版本。 [編輯](install-configure.md#update) 您專案的根composer.json檔案。

![新增](../assets/new.svg) 擷取 [!DNL Product Recommendations] 來自替代SaaS資料空間。 這可讓您使用 [!DNL Product Recommendations] 在其他非生產環境中運算於您的產品環境中。 [切換SaaS資料空間](settings.md) 進一步說明此功能。

![修正](../assets/fix.svg) 修正使用uBlock Origin禁止購物者結帳的問題
![修正](../assets/fix.svg) 修正傳送無關的加入購物車事件的問題

### 1.0.3適用於Page Builder的magento/module-page-builder-product-recommendations

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 頁面產生器支援。 透過頁面產生器整合，您可以準確且詳細地將Recommendation單位放置在Page Builder編寫內容上的任何位置。 您也可以設定標題與建議單位本身的樣式。 前往 [頁面產生器](https://experienceleague.adobe.com/en/docs/commerce-admin/page-builder/add-content/recommendations) 以取得詳細資訊。

### 2.0.0的magento/product-recommendations

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 正式發行版本！

+++

## 檔案

若要深入瞭解 [!DNL Product Recommendations] 和 [!DNL Product Recommendations] 開發：

* [使用者指南](overview.md)
* [開發人員檔案](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/developer/development-overview)
