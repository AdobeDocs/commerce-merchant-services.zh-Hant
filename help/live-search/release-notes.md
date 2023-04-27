---
title: '[!DNL Live Search] 發行說明'
description: 「 [!DNL Live Search] 來自Adobe Commerce。」
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
source-git-commit: f955cfc918c19a3c32126d8c9ef8a59b0e0dce0a
workflow-type: tm+mt
source-wordcount: '1241'
ht-degree: 0%

---

# [!DNL Live Search] 發行說明

以下版本說明 [!DNL Live Search].
目前主要發行版本已獲得支援。 較舊版本的發行說明僅供參考。
更新包括：

![新增](../assets/new.svg) 新功能
![修正](../assets/fix.svg) 修正和改良
![錯誤](../assets/bug.svg) 已知問題


_2023年4月25日_

![新增](../assets/new.svg) Live Search客戶現在可以利用 [SaaS價格索引器](../price-index/index.md).

## [!DNL Live Search] 3.0.1 {#301}

_2023年3月14日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

### 新功能

* 規則預覽中的產品項目卡
* [產品清單頁面Widget](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-storefront/plp-styling.html)
* [類別篩選選項](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/#facets)
* 新增拖放功能，以建立Pin事件
* 新的Pin操作：
   * 按一下「固定到點」(Pin to spot) — 按一下「固定」(Pin)按鈕可建立「固定」(Pin)事件
   * 釘到頂端 — 將產品置於第一個位置
   * 釘到底部 — 將產品放在結果底部
   * 只要按一下即可取消固定事件
* [規則的智慧排名](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-admin/rules/rules-add.html#ranking-type)

### 更新

* 配置規則現在會自動對位置進行唯一排序
* 刪除現有事件現在會更新預覽
* 無法儲存沒有事件的規則
* 移除面向「選取類型」選取器
* 新增未儲存規則的「編輯」新狀態

### 修正

* 修正儲存期間發生未完成事件時的伺服器錯誤
* 修正有多個事件時正確刪除特定事件的問題
* 修正新增新事件時，現有規則事件不會更新的問題
* 修正了從詳細資訊中按第二下「編輯」的問題， [!DNL Live Search] 需要重新載入的頁面
* 同義詞：修正使用者點出輸入時，無法將焦點傳回欄位的問題
* 其他微幅錯誤修正和效能更新


* ![錯誤](../assets/bug.svg)  — 僅Live Search Widget支援依「建議您」排名。 預設Luma和PWA搜尋功能不支援此功能。
* ![錯誤](../assets/bug.svg)  — 自訂價格屬性Facet在Luma中無法正確呈現，但API會對這些Facet正確篩選。

商戶必須升級 [!DNL Live Search] 擴充功能版本>= 3.0.1以存取這些功能。

建議您先升級並測試再推送至生產環境。 在驗證其測試環境結果後，考慮在非高峰時段升級生產環境。

## 舊版

+++2.0.5和之前版本

## [!DNL Live Search] 2.0.5 {#205}

[!BADGE 相容性]{type=Informative tooltip="相容性"}

* ![修正](../assets/fix.svg)  — 當SDK資源因網路問題而無法使用時，即時搜尋會擲回錯誤。 此錯誤已修正。

商家必須升級Live Search擴充功能版本>= 2.0.5才能存取這些功能。

建議您先升級並測試再推送至生產環境。 在驗證其測試環境結果後，考慮在非高峰時段升級生產環境。

### [!DNL Live Search] 2.0.4 {#204}

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 「即時搜尋」現在支援以管理員中的「顯示無庫存產品」設定進行篩選。 如果「顯示無現貨產品」設為false, `inStock = true` 會新增至篩選器。
![修正](../assets/fix.svg) 為了改善效能，「建議」區塊已從「即時搜尋」快顯視窗中移除。 資料仍會透過GraphQL傳遞，以備您取代功能時使用。
![修正](../assets/fix.svg) `categories` 和 `categoryPath` 已更換 `categoryIds` 類別篩選。 請參閱 [productSearch](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) 主題。
![修正](../assets/fix.svg) 先前，系結至B2B公司的使用者在執行搜尋時，會收到錯誤的客戶群組代碼。 Live Search現在會傳回正確的值。
![修正](../assets/fix.svg) 以前，當搜尋不存在的詞語時，即時搜尋會傳回錯誤。 此錯誤現已修正。

商戶必須升級 [!DNL Live Search] 擴充功能版本>= 2.0.4以存取這些功能。

建議使用者在推送至生產環境前先升級並測試。 在驗證其測試環境結果後，考慮在非高峰時段升級生產環境。

### [!DNL Live Search] 2.0.3 {#203}

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 現場搜尋現在支援B2B功能，方法是採用類別權限、共用目錄和客戶群專屬定價。

商戶必須升級 [!DNL Live Search] 擴充功能版本>= 2.0.3以存取這些功能。

建議使用者在推送至生產環境前先升級並測試。 在驗證其測試環境結果後，考慮在非高峰時段升級生產環境。

### [!DNL Live Search] 2.0 {#20}

[!BADGE 相容性]{type=Informative tooltip="相容性"}

現有 [!DNL Live Search] 安裝必須升級為 [!DNL Live Search] 2.0.0可善用下列新功能、修正和改良：

![新增](../assets/new.svg) [!DNL Live Search] 運行Adobe Commerce 2.4.4的安裝現在支援PHP 8.1。
![新增](../assets/new.svg) 此 `Magento_ElasticsearchCatalogPermissionsGraphQl` 模組會新增至安裝期間停用的模組清單。
![新增](../assets/new.svg) 中的可用行數 [[!DNL storefront popover]](quick-tour.md) 可從 *管理*.
![新增](../assets/new.svg) Beta [PWA](https://developer.adobe.com/commerce/pwa-studio/) 相容性 [!DNL Live Search].
![新增](../assets/new.svg) 此 [!DNL Live Search] 安裝程式會隨進階程式變更而更新。
![修正](../assets/fix.svg) [進階搜尋](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) 從店面頁尾移除的連結。
![錯誤](../assets/bug.svg) 不支援下列產品屬性 [Commerce GraphQL API](https://developer.adobe.com/commerce/webapi/graphql/) 若與測試版PWA相關： `description`, `name`, `short_description`
![錯誤](../assets/bug.svg) 測試版PWA [!DNL Live Search] 不支援 [事件處理](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).

### [!DNL Live Search] 1.3.1 {#131}

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![修正](../assets/fix.svg) [自訂價格屬性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/attributes-input-types.html) 設為 [face]({% link live-search/facets-add.md %})。
![修正](../assets/fix.svg) 修正當沒有 [貨幣符號](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html#step-5%3A-customize-currency-symbols-(optional)) (`data-currency-symbol`)可用。
![修正](../assets/fix.svg) [[!DNL Storefront popover]](storefront-popover.md) 現在會顯示 [特價](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-special.html) （最低最終價格）。

### [!DNL Live Search] 1.3.0 {#130}

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) [效能](performance.md) 「報表控制面板」可提供購物者所使用搜尋詞的深入分析。
![新增](../assets/new.svg) [!DNL Live Search] [Storefront事件SDK](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) 可透過事件發佈和訂閱服務及量度來存取通用資料層。
![修正](../assets/fix.svg) 此 [[!DNL Storefront popover]](storefront-popover.md) 有新 `active` 類別 `.search-autocomplete` 控制可見性的容器。
![修正](../assets/fix.svg) 在店面， [搜尋詞](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html#popular-search-terms) 頁尾連結已移除，且其快取已停用 [!DNL Live Search] 安裝。
![錯誤](../assets/bug.svg) Search適配器的修補程式可處理重複產品。
![錯誤](../assets/bug.svg) [!DNL Live Search] 支援 [單源](https://experienceleague.adobe.com/docs/commerce-admin/inventory/sources/sources-manage.html) 具有多個（虛擬）的（物理）清點位置 [股票](https://experienceleague.adobe.com/docs/commerce-admin/inventory/stocks/stocks-manage.html). 目前不支援多個庫存來源。

### [!DNL Live Search] 1.2.0 {#120}

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) [[!DNL Storefront popover]](storefront-popover.md) 當購物者在「搜尋」方塊中輸入查詢時，顯示最上層搜尋結果的建議產品和縮圖影像。
![新增](../assets/new.svg) 商務 *管理* 在鍵盤長時間不活動期間，工作階段保持開啟
![新增](../assets/new.svg) [!DNL Live Search] 上線後自動啟用
![修正](../assets/fix.svg) 初始索引時間不到一小時
![修正](../assets/fix.svg) 近乎即時的增量產品更新（安裝和安裝後）
![修正](../assets/fix.svg) 同義詞編輯器中的可排序列
![修正](../assets/fix.svg) [!DNL Live Search] 如果搜尋條件包含空的排序順序值，則不再擲回錯誤
![修正](../assets/fix.svg) 如果屬性代碼包含字串「to」或「from」，範圍篩選不再中斷

### [!DNL Live Search] 1.1.0 {#110}

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![錯誤](../assets/bug.svg) 此 [!DNL Live Search] 服務僅支援 [基本貨幣](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html) Adobe Commerce裝置。
![錯誤](../assets/bug.svg) 新增面向時，產品屬性摘要在設為時無法正確更新 `Update on Save`. 若要避免此問題，請前往 [索引管理](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) 並將產品屬性摘要設為 `Update by Schedule`.
![錯誤](../assets/bug.svg) [!DNL Live Search] 同義字是根據商店檢視而定義，但目前是根據網站儲存，並以 `environmentId` 和 `storeViewCode`. 因此，所有網站和Adobe Commerce安裝內的儲存檢視都會共用同義字。 最近建立的儲存視圖同義詞集優先。
![錯誤](../assets/bug.svg) 如果同義詞詞包含多個單詞，則每個單詞都被視為單獨的同義詞。 例如，如果您將「time piece」定義為「watch」的同義字，則「time」和「piece」都會視為watch的同義字。

+++

## 檔案

若要深入了解：

* [Adobe Commerce開發人員檔案](https://developer.adobe.com/commerce/docs)
* [Adobe Commerce使用手冊](https://experienceleague.adobe.com/docs/commerce.html)
* [[!DNL Live Search] 在Marketplace上](https://marketplace.magento.com/magento-live-search.html)
