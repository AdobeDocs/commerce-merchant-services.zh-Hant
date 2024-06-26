---
title: '"[!DNL Live Search] 發行說明」'
description: 「的最新版本資訊 [!DNL Live Search] 來自Adobe Commerce。」
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
feature: Services, Search, Release Notes
source-git-commit: fe261bfaf5a64c9501bc5523d29f9b6a9fc1a6a2
workflow-type: tm+mt
source-wordcount: '1966'
ht-degree: 0%

---

# [!DNL Live Search] 發行說明

以下版本說明說明最新版本的 [!DNL Live Search].
支援目前的主要發行版本。 舊版的發行說明僅供參考。
更新包括：

![新增](../assets/new.svg) 新功能
![修正](../assets/fix.svg) 修正和改良
![錯誤](../assets/bug.svg) 已知問題

## 託管服務更新

這些附註會說明在版本設定發行之外發佈的更新，或託管服務的改進。

_2024年2月13日_

![新增](../assets/new.svg) [!DNL Live Search] 現在支援設定預設規則 [搜尋銷售](rules.md).

_2023年10月12日_

![新增](../assets/new.svg) Commerce管理員現在可以指定索引的語言 [!DNL Live Search]. 另請參閱 [設定](settings.md).
![修正](../assets/fix.svg) 「搜尋規則」標籤已重新命名為「搜尋銷售」。

_2023年6月13日_

![修正](../assets/fix.svg) 修正引號或撇號等字元造成排名問題的問題。 重新索引可解決這些問題。

_2023年4月25日_

![新增](../assets/new.svg) [!DNL Live Search] 客戶現在可以利用新的 [SaaS價格索引子](../price-index/price-indexing.md).

### PLP Widget

_2024年5月31日_

![新增](../assets/new.svg) 已發行PLP Widget 2.0.0版，其中新增對下列功能的支援：

- 加入購物車按鈕 — 僅適用於簡單產品。
- 每個產品有多個影像 — 為可設定產品選擇不同顏色時，影像可能會變更。

_2023年10月27日_

![新增](../assets/new.svg) 此 [!DNL Live Search] PLP Widget現在支援色票。


## [!DNL Live Search] 4.2.0 {#420}

_2024年5月31日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 更新Live Search擴充功能以使用PLP Widget 2.0.0版。

## [!DNL Live Search] 4.1.2 {#412}

_2024年5月16日_

[!BADGE 支援]{type=Informative tooltip="支援"}

### 更新

![修正](../assets/fix.svg) 已修正 [`productSearch`](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#filtering-by-categories) GraphQL查詢以根據 `categoryPath` 和 `categoryList` 類別。

## [!DNL Live Search] 4.1.1 {#411}

_2024年3月19日_

[!BADGE 支援]{type=Informative tooltip="支援"}

### 新功能

![新增](../assets/new.svg) 新增波蘭文的語言支援。
![新增](../assets/new.svg) [!DNL Live Search] 對於執行Adobe Commerce 2.4.4的安裝現在支援PHP 8.3。

## [!DNL Live Search] 4.1.0 {#410}

_2024年2月22日_

[!BADGE 支援]{type=Informative tooltip="支援"}

### 新功能

![新增](../assets/new.svg) 此 [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard) 現已推出。 此改版後的儀表板提供資料串流的深入分析 [!DNL Product Recommendations]， [!DNL Live Search]、和 [!DNL Catalog Service].

### 更新

![修正](../assets/fix.svg) 已修正當訪客使用者在非預設商店檢視中將產品新增到購物車時導致錯誤的問題。
![修正](../assets/fix.svg) 修正搜尋彈出視窗一律在價格值前面顯示貨幣符號（不論地區設定為何）的問題。
![修正](../assets/fix.svg) 已移除已停用核心外掛程式不必要的型別定義，以修正安裝時的相容性問題。

## [!DNL Live Search] 4.0.0 {#400}

_2023年11月13日_

[!BADGE 支援]{type=Informative tooltip="支援"}

### 新功能

![新增](../assets/new.svg) [!DNL Live Search] 現在支援PLP Widget中的色票。
![新增](../assets/new.svg) [!DNL Live Search] 現在會顯示類別名稱，而非類別ID。
![新增](../assets/new.svg) [!DNL Live Search] 現在支援PLP Widget中的刪除線價格。
![新增](../assets/new.svg) 推出「隱藏篩選器」按鈕以隱藏篩選器面板。


### 更新

![修正](../assets/fix.svg) 此 [!DNL Live Search] 新安裝現在預設啟用PLP Widget。
![修正](../assets/fix.svg) 已重新設定CSS樣式，以便更妥善區隔Widget類別。
![修正](../assets/fix.svg) 微幅錯誤修正

安裝3.1.1版或更新版本後，啟用新的索引子：

- 產品價格摘要
- 範圍網站資料摘要
- 範圍客戶群組資料摘要

升級之後，在將變更推送至生產環境之前，請先在QA或測試環境中測試已更新的設定。

## 舊版

+++3.1.1和舊版

## [!DNL Live Search] 3.1.1 {#311}

_2023年9月15日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 已新增「類別銷售」索引標籤。 使用者現在可以為每個類別新增智慧型排名和手動排名（釘選、提升、隱藏、隱藏）
![新增](../assets/new.svg) 使用者可使用智慧型或手動排名新增單一類別規則
![新增](../assets/new.svg) 使用者現在可以將智慧型排名規則新增到子類別
![新增](../assets/new.svg) 使用智慧型排名刪除子類別時，會提供詳細資訊
![新增](../assets/new.svg) 新增刪除繼承排名策略規則的功能
![新增](../assets/new.svg) 新增刪除單一類別之規則的功能
![新增](../assets/new.svg) 新增規則時，使用者現在可以依類別名稱搜尋
![新增](../assets/new.svg) 使用類別樹狀檢視，使用者現在可以檢視哪個類別已套用規則。
![新增](../assets/new.svg) 類別預覽只會顯示選取的類別。
![新增](../assets/new.svg) AEM CIF [彈出視窗Widget](https://github.com/adobe/aem-cif-guides-venia/pull/319) 和 [PLP Widget](https://github.com/adobe/aem-cif-guides-venia/pull/320) 元件可讓AEM網站充分利用 [!DNL Live Search].

### 更新

![修正](../assets/fix.svg) 產品和價格摘要的表格大小已大幅縮減。 表格 `catalog_data_exporter_products` 和 `catalog_data_exporter_product_prices` 應該會大幅縮減規模。
![修正](../assets/fix.svg) 「規則」標籤重新命名為「搜尋規則」
![修正](../assets/fix.svg) 依「趨勢」排名時，您現在可以選擇以下選項： - 3天（預設） - 14天 — 30天
![修正](../assets/fix.svg) 「活動」（提升/釘選/隱藏/隱藏）已重新命名為「手動排名」
![修正](../assets/fix.svg) 「排名型別」已重新命名為「智慧型排名」
![修正](../assets/fix.svg) 微幅錯誤修正

## [!DNL Live Search] 3.1.0 {#310}

_2023年9月1日_

[!BADGE 支援]{type="資訊性" tooltip="支援"}

### 更新

![修正](../assets/fix.svg) 產品清單Widget已更新，可使用 [目錄服務API](https://developer.adobe.com/commerce/services/graphql/catalog-service/product-search/).

## [!DNL Live Search] 3.0.2 {#302}

_2023年8月7日_

[!BADGE 支援]{type="資訊性" tooltip="支援"}

### 新功能

![新增](../assets/new.svg) 下列值已新增至 `storeDetails` 物件：

- &quot;允許每頁所有產品&quot;
- 匯率
- 「網格上每頁產品允許值」
- 「網格上每頁產品預設值」
- 存放區語言

### 更新

![修正](../assets/fix.svg) 已將目錄服務模組新增到中繼資料以支援進階資料擷取。
![修正](../assets/fix.svg) 此 **我的帳戶** 使用產品清單頁面Widget時，頁面導覽不再消失。

商家必須升級 [!DNL Live Search] 擴充功能版本>= 3.0.2以存取這些功能。

建議先升級並測試，再推送至生產環境。 確認測試環境結果後，請考慮在非尖峰時段升級生產環境。

### 限制

使用即時搜尋產品清單頁面Widget會導致Google Tag Manager失敗。 如果需要Google Tag Manager，請使用預設的「搜尋轉接器」。

## [!DNL Live Search] 3.0.1 {#301}

_2023年3月14日_

[!BADGE 支援]{type="資訊性" tooltip="支援"}

### 新功能

![新增](../assets/new.svg) 規則預覽中的產品專案卡
![新增](../assets/new.svg) [產品清單頁面Widget](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-storefront/plp-styling)
![新增](../assets/new.svg) [類別篩選選項](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#facets)
![新增](../assets/new.svg) 新增拖放以建立釘選事件的功能
![新增](../assets/new.svg) 新釘選動作： — 釘選至點 — 按一下釘選按鈕以建立釘選事件 — 釘選至頂端 — 將產品置於第一個位置 — 釘選至底部 — 將產品置於結果底部 — 按一下即可取消釘選事件
![新增](../assets/new.svg) [規則的智慧型排名](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/rules/rules-add)
![新增](../assets/new.svg) [!DNL Live Search] 現在支援完整 [Inventory management](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) Commerce中的功能(先前稱為多來源詳細目錄(Multi-Source Inventory)，簡稱MSI)。 若要啟用完整支援，您必須 [更新](install.md#update) 相依性模組 `commerce-data-export` 至102.2.0+版。

### 更新

![修正](../assets/fix.svg) 設定規則現在會自動以唯一方式排序職位
![修正](../assets/fix.svg) 刪除現有事件現在會更新預覽
![修正](../assets/fix.svg) 無法儲存沒有事件的規則
![修正](../assets/fix.svg) 移除多面向「選取型別」選取器
![修正](../assets/fix.svg) 新增未儲存規則的新「編輯」狀態

### 修正

![修正](../assets/fix.svg) 修正儲存期間發生未完成事件時的伺服器錯誤
![修正](../assets/fix.svg) 修正當有多個事件時正確刪除特定事件的問題
![修正](../assets/fix.svg) 修正當新增新事件時現有規則事件未更新的問題
![修正](../assets/fix.svg) 已修正來自詳細資料的第二個「編輯」點按， [!DNL Live Search] 需要重新載入的頁面
![修正](../assets/fix.svg) 同義字：修正使用者按一下退出輸入時，無法將焦點傳回欄位的問題
![修正](../assets/fix.svg) 其他微幅錯誤修正與效能更新


![錯誤](../assets/bug.svg)  — 僅在「即時搜尋」Widget中支援「為您推薦」的排名。 預設的Luma和PWA搜尋功能不支援此功能。
![錯誤](../assets/bug.svg)  — 自訂價格屬性Facet無法在Luma中正確轉譯，但API會正確篩選它們。

商家必須升級 [!DNL Live Search] 擴充功能版本>= 3.0.1以存取這些功能。

建議先升級並測試，再推送至生產環境。 確認測試環境結果後，請考慮在非尖峰時段升級生產環境。

## [!DNL Live Search] 2.0.5 {#205}

[!BADGE 支援]{type="資訊性" tooltip="支援"}

![修正](../assets/fix.svg)  — 當SDK資源因網路問題而無法使用時，即時搜尋會擲回錯誤。 此錯誤已修正。

商家必須升級Live Search擴充功能>= 2.0.5版才能存取這些功能。

建議先升級並測試，再推送至生產環境。 確認測試環境結果後，請考慮在非尖峰時段升級生產環境。

### [!DNL Live Search] 2.0.4 {#204}

[!BADGE 支援]{type="資訊性" tooltip="支援"}

![新增](../assets/new.svg) 即時搜尋現在支援以管理員中的「顯示無庫存產品」設定進行篩選。 如果「顯示無庫存產品」設為false， `inStock = true` 會新增至篩選器。
![修正](../assets/fix.svg) 為了改善效能，「建議」區塊已從「即時搜尋」快顯視窗中移除。 如果您想要取代功能，資料仍會透過GraphQL傳遞。
![修正](../assets/fix.svg) `categories` 和 `categoryPath` 已取代 `categoryIds` 用於類別篩選。 請閱讀以下內容： [productSearch](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/) 主題。
![修正](../assets/fix.svg) 先前，繫結至B2B公司的使用者在執行搜尋時會收到錯誤的客戶群組代碼。 即時搜尋現在會傳回正確的值。
![修正](../assets/fix.svg) 先前，當搜尋不存在的辭彙時，即時搜尋會傳回錯誤。 此錯誤現已修正。

商家必須升級 [!DNL Live Search] 擴充功能版本>= 2.0.4以存取這些功能。

建議使用者在推送至生產環境前，先升級並測試。 確認測試環境結果後，請考慮在非尖峰時段升級生產環境。

### [!DNL Live Search] 2.0.3 {#203}

[!BADGE 支援]{type="資訊性" tooltip="支援"}

![新增](../assets/new.svg) Live Search現在藉由接受類別許可權、共用類別目錄和客戶群組特定定價，來支援B2B功能。

商家必須升級 [!DNL Live Search] 擴充功能版本>= 2.0.3以存取這些功能。

建議使用者在推送至生產環境前，先升級並測試。 確認測試環境結果後，請考慮在非尖峰時段升級生產環境。

### [!DNL Live Search] 2.0 {#20}

[!BADGE 支援]{type="資訊性" tooltip="支援"}

現有 [!DNL Live Search] 安裝必須升級至 [!DNL Live Search] 2.0.0以善用下列新功能、修正和改良：

![新增](../assets/new.svg) [!DNL Live Search] 對於執行Adobe Commerce 2.4.4的安裝現在支援PHP 8.1。
![新增](../assets/new.svg) 此 `Magento_ElasticsearchCatalogPermissionsGraphQl` 模組會新增至安裝期間停用的模組清單。
![新增](../assets/new.svg) 中可用的行數 [[!DNL storefront popover]](overview.md) 您可從以下位置設定： *管理員*.
![新增](../assets/new.svg) 測試版 [PWA](https://developer.adobe.com/commerce/pwa-studio/) 支援 [!DNL Live Search].
![新增](../assets/new.svg) 此 [!DNL Live Search] 安裝程式會更新為進階程式變更。
![修正](../assets/fix.svg) [進階搜尋](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) 從店面頁尾移除的連結。
![錯誤](../assets/bug.svg) 下列產品屬性不受支援 [COMMERCE GRAPHQL API](https://developer.adobe.com/commerce/services/graphql/live-search/) 使用與PWA的Beta版相關時： `description`， `name`， `short_description`
![錯誤](../assets/bug.svg) 適用於的PWA測試版 [!DNL Live Search] 不支援 [事件處理](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).

### [!DNL Live Search] 1.3.1 {#131}

[!BADGE 支援]{type="資訊性" tooltip="支援"}

![修正](../assets/fix.svg) [自訂價格屬性](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/attributes-input-types) 設定為時不再傳回錯誤 [Facet]({%連結live-search/facets-add.md %})。
![修正](../assets/fix.svg) 修正無時會發生錯誤的問題 [貨幣符號](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration(optional)) (`data-currency-symbol`)可供使用。
![修正](../assets/fix.svg) [[!DNL Storefront popover]](storefront-popover.md) 現在顯示 [特殊價格](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-special) （最低最終價格）。

### [!DNL Live Search] 1.3.0 {#130}

[!BADGE 支援]{type="資訊性" tooltip="支援"}

![新增](../assets/new.svg) [效能](performance.md) 報表儀表板可讓您深入分析購物者使用的搜尋辭彙。
![新增](../assets/new.svg) [!DNL Live Search] [店面事件SDK](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) 可讓您存取具有事件發佈和訂閱服務以及量度的通用資料層。
![修正](../assets/fix.svg) 此 [[!DNL Storefront popover]](storefront-popover.md) 有新的 `active` 的類別 `.search-autocomplete` 控制可見性的容器。
![修正](../assets/fix.svg) 在店面， [搜尋字詞](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search-terms) 已移除頁尾連結，且已停用其快取 [!DNL Live Search] 安裝。
![錯誤](../assets/bug.svg) Search配接卡的修補程式可處理重複的產品。
![錯誤](../assets/bug.svg) [!DNL Live Search] 支援 [單一來源](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/sources/sources-manage) （實體）清查地點有多個（虛擬） [庫存](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/stocks/stocks-manage). 目前不支援多個清查來源。

### [!DNL Live Search] 1.2.0 {#120}

[!BADGE 支援]{type="資訊性" tooltip="支援"}

![新增](../assets/new.svg) [[!DNL Storefront popover]](storefront-popover.md) 當購物者在「搜尋」方塊中輸入查詢時，顯示排名在前的搜尋結果的建議產品和縮圖影像。
![新增](../assets/new.svg) 商務 *管理員* 在長時間鍵盤不活動期間，工作階段會保持開啟狀態
![新增](../assets/new.svg) [!DNL Live Search] 上線後會自動啟用
![修正](../assets/fix.svg) 初始索引時間不到一小時
![修正](../assets/fix.svg) 近乎即時地增量產品更新（安裝和設定後）
![修正](../assets/fix.svg) 同義字編輯器中的可排序欄
![修正](../assets/fix.svg) [!DNL Live Search] 如果搜尋條件包含空白的排序順序值，不再擲回錯誤
![修正](../assets/fix.svg) 如果屬性程式碼包含字串「to」或「from」，則範圍篩選不再中斷

### [!DNL Live Search] 1.1.0 {#110}

[!BADGE 支援]{type="資訊性" tooltip="支援"}

![錯誤](../assets/bug.svg) 此 [!DNL Live Search] 服務僅支援 [基本貨幣](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration) Adobe Commerce安裝的資訊。
![錯誤](../assets/bug.svg) 新增Facet時，產品屬性摘要若設為，將無法正確更新 `Update on Save`. 若要避免此問題，請前往 [索引管理](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) 並將產品屬性摘要設為 `Update by Schedule`.
![錯誤](../assets/bug.svg) [!DNL Live Search] 同義字是按商店檢視定義，但目前是按網站儲存，並以以下組合識別： `environmentId` 和 `storeViewCode`. 因此，Adobe Commerce安裝中的所有網站和商店檢視會共用同義字。 存放區檢視最近建立的同義字集優先。
![錯誤](../assets/bug.svg) 如果同義字詞包含多個字詞，每個字詞都會被視為個別的同義字。 例如，如果您將「time piece」定義為「watch」的同義字，則「time」和「piece」都會被視為監視的同義字。

+++

## 檔案

若要深入瞭解：

- [Adobe Commerce開發人員檔案](https://developer.adobe.com/commerce/docs)
- [Adobe Commerce使用手冊](https://experienceleague.adobe.com/en/docs/commerce)
- [[!DNL Live Search] 在市集上](https://commercemarketplace.adobe.com/magento-live-search.html)
