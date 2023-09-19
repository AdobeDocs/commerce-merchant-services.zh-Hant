---
title: '[!DNL Live Search] 發行說明'
description: 「的最新版本資訊 [!DNL Live Search] 來自Adobe Commerce。」
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
feature: Services, Search, Release Notes
source-git-commit: add4d61f1e97bdf889ab0de694f8c3921caaab50
workflow-type: tm+mt
source-wordcount: '1459'
ht-degree: 1%

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

+++託管服務更新

_2023年6月13日_

![修正](../assets/fix.svg) 修正引號或撇號等字元造成排名問題的問題。 重新索引將解決這些問題。

_2023年4月25日_

![新增](../assets/new.svg) Live Search客戶現在可以利用新的 [SaaS價格索引子](../price-index/index.md).

+++

## [!DNL Live Search] 3.1.0 {#310}

_2023年9月1日_

[!BADGE 支援]{type="資訊性" tooltip="支援"}

### 更新

* 產品清單Widget已更新，可使用 [目錄服務API](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/product-search/).

## 舊版

+++3.0.2和舊版

## [!DNL Live Search] 3.0.2 {#302}

_2023年8月7日_

[!BADGE 支援]{type="資訊性" tooltip="支援"}

### 新功能

下列值已新增至 `storeDetails` 物件：

* &quot;允許每頁所有產品&quot;
* 匯率
* 「網格上每頁產品允許值」
* 「網格上每頁產品預設值」
* 存放區語言

### 更新

* 已將目錄服務模組新增到中繼資料以支援進階資料擷取。

### 修正

* 此 **我的帳戶** 使用產品清單頁面Widget時，頁面導覽不再消失。

商家必須升級 [!DNL Live Search] 擴充功能版本>= 3.0.2以存取這些功能。

建議先升級並測試，再推送至生產環境。 確認測試環境結果後，請考慮在非尖峰時段升級生產環境。

### 限制

使用即時搜尋產品清單頁面Widget會導致Google Tag Manager失敗。 若需要Google Tag Manager，請使用預設的「搜尋轉接器」。

## 舊版

+++3.0.1和舊版

## [!DNL Live Search] 3.0.1 {#301}

_2023年3月14日_

[!BADGE 支援]{type="資訊性" tooltip="支援"}

### 新功能

* 規則預覽中的產品專案卡
* [產品清單頁面Widget](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-storefront/plp-styling.html)
* [類別篩選選項](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/#facets)
* 新增拖放以建立釘選事件的功能
* 新釘選動作：
   * 釘選到地點 — 按一下即可建立釘選事件的釘選按鈕
   * 釘選到頂端 — 將產品放在第一個位置
   * 釘選到底部 — 將產品放置在結果的底部
   * 按一下即可取消釘選事件
* [規則的智慧型排名](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-admin/rules/rules-add.html#ranking-type)

### 更新

* 設定規則現在會自動以唯一方式排序職位
* 刪除現有事件現在會更新預覽
* 無法儲存沒有事件的規則
* 移除多面向「選取型別」選取器
* 新增未儲存規則的新「編輯」狀態

### 修正

* 修正儲存期間發生未完成事件時的伺服器錯誤
* 修正當有多個事件時正確刪除特定事件的問題
* 修正當新增新事件時現有規則事件未更新的問題
* 已修正來自詳細資料的第二個「編輯」點按， [!DNL Live Search] 需要重新載入的頁面
* 同義字：修正使用者按一下退出輸入時，無法將焦點傳回欄位的問題
* 其他微幅錯誤修正與效能更新


* ![錯誤](../assets/bug.svg)  — 僅在「即時搜尋」Widget中支援「為您推薦」的排名。 預設的Luma和PWA搜尋功能不支援此功能。
* ![錯誤](../assets/bug.svg)  — 自訂價格屬性Facet無法在Luma中正確轉譯，但API會正確篩選它們。

商家必須升級 [!DNL Live Search] 擴充功能版本>= 3.0.1以存取這些功能。

建議先升級並測試，再推送至生產環境。 確認測試環境結果後，請考慮在非尖峰時段升級生產環境。

## [!DNL Live Search] 2.0.5 {#205}

[!BADGE 支援]{type="資訊性" tooltip="支援"}

* ![修正](../assets/fix.svg)  — 當SDK資源因網路問題而無法使用時，即時搜尋會擲回錯誤。 此錯誤已修正。

商家必須升級Live Search擴充功能>= 2.0.5版才能存取這些功能。

建議先升級並測試，再推送至生產環境。 確認測試環境結果後，請考慮在非尖峰時段升級生產環境。

### [!DNL Live Search] 2.0.4 {#204}

[!BADGE 支援]{type="資訊性" tooltip="支援"}

![新增](../assets/new.svg) 即時搜尋現在支援以管理員中的「顯示無庫存產品」設定進行篩選。 如果「顯示無庫存產品」設為false， `inStock = true` 會新增至篩選器。
![修正](../assets/fix.svg) 為了改善效能，「建議」區塊已從「即時搜尋」快顯視窗中移除。 如果您想要取代功能，資料仍會透過GraphQL傳遞。
![修正](../assets/fix.svg) `categories` 和 `categoryPath` 已取代 `categoryIds` 用於類別篩選。 請閱讀以下內容： [productSearch](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) 主題。
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
![新增](../assets/new.svg) 中可用的行數 [[!DNL storefront popover]](quick-tour.md) 您可從以下位置設定： *管理員*.
![新增](../assets/new.svg) 測試版 [PWA](https://developer.adobe.com/commerce/pwa-studio/) 支援 [!DNL Live Search].
![新增](../assets/new.svg) 此 [!DNL Live Search] 安裝程式會更新為進階程式變更。
![修正](../assets/fix.svg) [進階搜尋](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) 從店面頁尾移除的連結。
![錯誤](../assets/bug.svg) 下列產品屬性不受支援 [Commerce GraphQL API](https://developer.adobe.com/commerce/webapi/graphql/) 使用與PWA的Beta版相關時： `description`， `name`， `short_description`
![錯誤](../assets/bug.svg) 適用於的PWA測試版 [!DNL Live Search] 不支援 [事件處理](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).

### [!DNL Live Search] 1.3.1 {#131}

[!BADGE 支援]{type="資訊性" tooltip="支援"}

![修正](../assets/fix.svg) [自訂價格屬性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/attributes-input-types.html) 設定為時不再傳回錯誤 [Facet]({%連結live-search/facets-add.md %})。
![修正](../assets/fix.svg) 修正無時會發生錯誤的問題 [貨幣符號](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html#step-5%3A-customize-currency-symbols-(optional)) (`data-currency-symbol`)可供使用。
![修正](../assets/fix.svg) [[!DNL Storefront popover]](storefront-popover.md) 現在顯示 [特殊價格](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-special.html) （最低最終價格）。

### [!DNL Live Search] 1.3.0 {#130}

[!BADGE 支援]{type="資訊性" tooltip="支援"}

![新增](../assets/new.svg) [效能](performance.md) 報表儀表板可讓您深入分析購物者使用的搜尋辭彙。
![新增](../assets/new.svg) [!DNL Live Search] [店面事件SDK](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) 可讓您存取具有事件發佈和訂閱服務以及量度的通用資料層。
![修正](../assets/fix.svg) 此 [[!DNL Storefront popover]](storefront-popover.md) 有新的 `active` 的類別 `.search-autocomplete` 控制可見性的容器。
![修正](../assets/fix.svg) 在店面， [搜尋字詞](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html#popular-search-terms) 已移除頁尾連結，且已停用其快取 [!DNL Live Search] 安裝。
![錯誤](../assets/bug.svg) Search配接卡的修補程式可處理重複的產品。
![錯誤](../assets/bug.svg) [!DNL Live Search] 支援 [單一來源](https://experienceleague.adobe.com/docs/commerce-admin/inventory/sources/sources-manage.html) （實體）清查地點有多個（虛擬） [庫存](https://experienceleague.adobe.com/docs/commerce-admin/inventory/stocks/stocks-manage.html). 目前不支援多個清查來源。

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

![錯誤](../assets/bug.svg) 此 [!DNL Live Search] 服務僅支援 [基本貨幣](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html) Adobe Commerce安裝的資訊。
![錯誤](../assets/bug.svg) 新增Facet時，產品屬性摘要若設為，將無法正確更新 `Update on Save`. 若要避免此問題，請前往 [索引管理](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) 並將產品屬性摘要設為 `Update by Schedule`.
![錯誤](../assets/bug.svg) [!DNL Live Search] 同義字是按商店檢視定義，但目前是按網站儲存，並以以下組合識別： `environmentId` 和 `storeViewCode`. 因此，Adobe Commerce安裝中的所有網站和商店檢視會共用同義字。 存放區檢視最近建立的同義字集優先。
![錯誤](../assets/bug.svg) 如果同義字詞包含多個字詞，每個字詞都會被視為個別的同義字。 例如，如果您將「time piece」定義為「watch」的同義字，則「time」和「piece」都會被視為監視的同義字。

+++

## 檔案

若要深入瞭解：

* [Adobe Commerce開發人員檔案](https://developer.adobe.com/commerce/docs)
* [Adobe Commerce使用手冊](https://experienceleague.adobe.com/docs/commerce.html)
* [[!DNL Live Search] 在市集上](https://commercemarketplace.adobe.com/magento-live-search.html)
