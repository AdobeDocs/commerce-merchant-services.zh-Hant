---
title: '"[!DNL Product Recommendations] 發行說明'''
description: 的最新發佈資訊 [!DNL Product Recommendations] Adobe Commerce。
exl-id: 1758e688-d26f-45e7-818c-d4726338a6c3
source-git-commit: f955cfc918c19a3c32126d8c9ef8a59b0e0dce0a
workflow-type: tm+mt
source-wordcount: '1102'
ht-degree: 0%

---

# [!DNL Product Recommendations] 發行說明

發行說明包含對以下內容的更新 [!DNL Product Recommendations] 模組：

* [!DNL Product Recommendations] 元包： `magento/product-recommendations`
* 頁面生成器支援 [!DNL Product Recommendations] （可選）模組： `magento/module-page-builder-product-recommendations`
* 支援視覺相似性推薦類型 [!DNL Product Recommendations] （可選）模組： `magento/module-visual-product-recommendations`

為當前主發佈的版本提供支援。 提供了舊版本的發行說明供參考。
發行說明包括：

![新建](../assets/new.svg) 新功能
![修復](../assets/fix.svg) 修復和改進
![蟲](../assets/bug.svg) 已知問題

請參閱開發人員文檔以 [瞭解產品相容性](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html)。

## 當前主版本

_2023年4月25日_

![新建](../assets/new.svg) 產品Recommendations客戶現在可以利用 [SaaS價格索引](../price-index/index.md)。

### 5.0.0magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg) 更新產品Recommendations以支援Adobe Commerce2.4.6。
![新建](../assets/new.svg) 這是主版本。 [編輯](install-configure.md#update) 根 `composer.json` 檔案。

#### 已知限制

* 的 `websiteCode` 如果值包含下划線(_)，則返回的值不正確。

### 以前的版本

+++4.0.1和之前版本

### 4.0.1magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![修復](../assets/fix.svg) 以前，產品Recommendations在顯示貨幣切換到非預設貨幣時會顯示錯誤。 現在，轉換貨幣正常工作。

### 4.0.0magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg) 已添加 [就緒性指標](create.md) 以幫助您直觀顯示每種建議類型的培訓進度。
![新建](../assets/new.svg) 這是主版本。 [編輯](install-configure.md#update) 根 `composer.json` 檔案。 此版本還要求您在安裝和配置產品Recommendations時提供兩個API密鑰： [生產密鑰和沙盒密鑰](../landing/saas.md)。

#### 已知限制

* 的 `websiteCode` 如果值包含下划線(_)，則返回的值不正確。

### 3.3.7magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg) 已添加PHP 8.1支援
![新建](../assets/new.svg) 改進了影像大小調整，以便在參考顯示模板中更一致地處理影像大小調整

### 3.3.6magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg) 優化 [!DNL Product Recommendations] 元包，明確列出依賴項

### 3.3.5magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg) 已添加 [B2B支援](onboarding.md#b2bsupport) 在產品Recommendations
![新建](../assets/new.svg) 已將新源添加到 [同步目錄資料](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) 到Commerce Services的命令行

### 3.3.3magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg) 添加新 [推薦類型](type.md):轉換（查看到購物車）、轉換（查看到購買）和最近查看。 這些新建議類型可在 `magento/product-recommendations` 模組3.2.2和更高版本。
![修復](../assets/fix.svg) 修復了Amplish的Web應用程式防火牆(WAF)錯誤阻止cookie的問題
![修復](../assets/fix.svg) 未在中顯示分配給非預設商店視圖的產品的已修復問題 _Recommendations產品預覽_ 為特定儲存視圖建立建議時的面板
![修復](../assets/fix.svg) 已修復問題，其中頁面生成器中的某些建議單元名稱阻止建議單元顯示在店面上

### 3.3.2magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![修復](../assets/fix.svg) B2B支援的已修復缺失依賴項

### 3.3.1magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg) 增加了對B2B客戶組定價的支援。 設定 [價格篩選](filters.md) 在推薦單元上，登錄的B2B客戶查看所顯示產品的客戶組定價集。

### 3.3.0magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg) 增加了對Adobe客戶端資料層的支援，以標準化跨Adobe Commerce功能和服務的行為資料收集。 查看 [自述](https://github.com/adobe/magento-storefront-event-collector/blob/main/README.md) 來瞭解更多資訊。

### 3.2.6magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![修復](../assets/fix.svg) 已修復JavaScript模式錯誤
![修復](../assets/fix.svg) 修復了Amplish的Web應用程式防火牆(WAF)錯誤阻止cookie的問題

### 3.2.5magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg) 已將Magento服務更名為 [商務服務](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) 並改進了管理員的可用性

### 3.2.4magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![修復](../assets/fix.svg) 已修復索引產品屬性時出現的「無法檢索可配置產品選項資料」錯誤

### 3.2.3magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![修復](../assets/fix.svg) 已修復目錄同步期間的「無法檢索可配置產品選項資料」錯誤
![修復](../assets/fix.svg) 修復了啟用「將儲存代碼添加到URL」配置時未正確設定儲存代碼的問題
![修復](../assets/fix.svg) 改進了對管理面板配置更改的檢測，以確保這些更改反映在目錄同步資料中

### 3.2.2magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg) 已添加 [預覽建議結果](create.md) 創作時。 這可能要求您將模組更新為最新版本。
![新建](../assets/new.svg) 已添加 [監控和管理](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) 管理員的目錄同步進程。
![新建](../assets/new.svg) 已添加 [篩選](filters.md) 以控制在建議書中顯示的產品。
![新建](../assets/new.svg) 已添加 [視覺相似性](type.md#visualsim) 建議類型。

### 1.2.1頁面生成器的magento/module-page-builder-product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg) 已添加對3.2.0+版本的支援 `magento/product-recommendations` 模組

### 3.1.0magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg) 已添加 [重新同步](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) 通過命令行將目錄連接到SaaS服務。
![新建](../assets/new.svg) 添加了對資料庫表前置詞的支援
![修復](../assets/fix.svg) 已刪除PHP 7.1支援

### 3.0.8magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![修復](../assets/fix.svg) 修復了在配置模組之前為資料收集發送事件的問題，導致無效通信

### 3.0.6magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg) **(Beta)** 包括對新產品的支援 [視覺相似性](type.md#visualsim) 建議類型。

### 1.0.0magento/module-visual-product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg) **(Beta)** [視覺相似性](type.md#visualsim)。 使用 _視覺相似性_ 建議類型，您可以將建議單元部署到產品詳細資訊頁面，該頁面顯示的產品在視覺上與查看的產品相似。

### 3.0.5magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![修復](../assets/fix.svg) 已修復目錄導出過程中可能出現的「無法檢索產品選項資料」錯誤。
![修復](../assets/fix.svg) 中的貨幣符號 _收入_ 列 _產品Recommendations_ 儀表板現在可以正確反映已配置的基本貨幣。

### 3.0.4magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![修復](../assets/fix.svg) 增加對Adobe Commerce的支2.4.0

### 3.0.3magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![修復](../assets/fix.svg) 在店面模板中改進符號實現

### 1.0.4頁面生成器的magento/module-page-builder-product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg) 編輯頁面生成器內容類型時添加了產品建議案名稱

### 3.0.2magento/product建議

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg) 在頁面生成器中選擇建議單元時，在網格上添加了狀態列
![修復](../assets/fix.svg) 解決了產品和映像URL中的http/https協定不正確的問題

### 3.0.1magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

這是主版本。 [編輯](install-configure.md#update) 項目的root composer.json檔案。

![新建](../assets/new.svg) 獲取 [!DNL Product Recommendations] 從備用SaaS資料空間。 這樣，您就可以在其他非生產環境中使用在產品環境中計算的產品建議。 [交換SaaS資料空間](settings.md) 進一步說明了此功能。

![修復](../assets/fix.svg) 已修復使用uBlock Origin的購物者禁止結帳的問題
![修復](../assets/fix.svg) 修復了發送無關的附加購物車事件的問題

### 1.0.3頁面生成器的magento/module-page-builder-product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg) 頁面生成器支援。 通過頁面生成器整合，您可以準確而大量地將建議單元放置在頁面生成器創作的內容上的任意位置。 您還可以自行設定標題和建議單元的樣式。 轉到 [頁面生成器](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) 的子菜單。

### 2.0.0magento/product-recommendations

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg) 通用發佈！

+++

## 文檔

瞭解有關 [!DNL Product Recommendations] 和 [!DNL Product Recommendations] 開發：

* [使用手冊](overview.md)
* [開發人員文檔](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/development-overview.html)
