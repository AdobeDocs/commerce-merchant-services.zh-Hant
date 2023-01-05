---
title: "[!DNL Live Search] 發行說明"
description: 「 [!DNL Live Search] 來自Adobe Commerce。」
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
source-git-commit: 4566727b4e672033997491bcaf075c48e2a55cc8
workflow-type: tm+mt
source-wordcount: '1004'
ht-degree: 1%

---

# [!DNL Live Search] 發行說明

以下版本說明 [!DNL Live Search] 包括：

* ![新增](../assets/new.svg)  — 新功能
* ![修正](../assets/fix.svg)  — 修正和改良
* ![錯誤](../assets/bug.svg)  — 已知問題

## [!DNL Live Search] 2.0.5 {#205}

* 與Adobe Commerce(EE)相容：2.4.x
* 與Adobe Commerce for Cloud(ECE)相容：2.4.x
* 穩定性：穩定

* ![修正](../assets/fix.svg)  — 當SDK資源因網路問題而無法使用時，即時搜尋會擲回錯誤。 此錯誤現已修正。

商家必須升級Live Search擴充功能版本>= 2.0.5才能存取這些功能。

建議您先升級並測試再推送至生產環境。 在驗證其測試環境結果後，考慮在非高峰時段升級生產環境。

## [!DNL Live Search] 2.0.4 {#204}

* 與Adobe Commerce(EE)相容：2.4.x
* 與Adobe Commerce for Cloud(ECE)相容：2.4.x
* 穩定性：穩定

* ![新增](../assets/new.svg)  — 即時搜尋現在支援以管理員中的「顯示無庫存產品」設定進行篩選。 如果「顯示無現貨產品」設為false, `inStock = true` 會新增至篩選器。
* ![修正](../assets/fix.svg)  — 為了改善效能，「建議」區塊已從「即時搜尋」快顯視窗中移除。 資料仍會透過GraphQL傳遞，以備您取代功能時使用。
* ![修正](../assets/fix.svg) - `categories` 和 `categoryPath` 已更換 `categoryIds` 類別篩選。 請參閱 [productSearch](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) 主題。
* ![修正](../assets/fix.svg)  — 先前，系結至B2B公司的使用者在執行搜尋時，會收到錯誤的客戶群組代碼。 Live Search現在會傳回正確的值。
* ![修正](../assets/fix.svg)  — 過去，搜尋不存在的詞語時，Live Search會傳回錯誤。 此錯誤現已修正。

商家必須升級Live Search擴充功能版本>= 2.0.4才能存取這些功能。

我們建議使用者先升級並測試再推送至生產環境。 在驗證其測試環境結果後，考慮在非高峰時段升級生產環境。

## [!DNL Live Search] 2.0.3 {#203}

* 與Adobe Commerce(EE)相容：2.4.x
* 與Adobe Commerce for Cloud(ECE)相容：2.4.x
* 穩定性：穩定

* ![新增](../assets/new.svg) - Live Search現在支援B2B功能，方法是採用類別權限、共用目錄和客戶群特定定價。

商家必須升級Live Search擴充功能版本>= 2.0.3才能存取這些功能。

我們建議使用者先升級並測試再推送至生產環境。 在驗證其測試環境結果後，考慮在非高峰時段升級生產環境。

## [!DNL Live Search] 2.0 {#20}

* 與Adobe Commerce(EE)相容：2.4.x
* 與Adobe Commerce for Cloud(ECE)相容：2.4.x
* 穩定性：穩定

現有 [!DNL Live Search] 安裝必須升級為 [!DNL Live Search] 2.0.0可善用下列新功能、修正和改良：

* ![新增](../assets/new.svg) - [!DNL Live Search] 運行Adobe Commerce 2.4.4的安裝現在支援PHP 8.1。
* ![新增](../assets/new.svg) - `Magento_ElasticsearchCatalogPermissionsGraphQl` 模組會新增至安裝期間停用的模組清單。
* ![新增](../assets/new.svg) - [[!DNL storefront popover]](quick-tour.md) 可從 *管理*.
* ![新增](../assets/new.svg)  — 測試版 [PWA](https://developer.adobe.com/commerce/pwa-studio/) 相容性 [!DNL Live Search].
* ![新增](../assets/new.svg) - [!DNL Live Search] 安裝程式會隨進階程式變更而更新。
* ![修正](../assets/fix.svg) - [進階搜尋](https://docs.magento.com/user-guide/catalog/search-advanced.html) 從店面頁尾移除的連結。
* ![錯誤](../assets/bug.svg)  — 不支援下列產品屬性 [MagentoGraphQL API](https://developer.adobe.com/commerce/webapi/graphql/) 若與測試版PWA相關： `description`, `name`, `short_description`
* ![錯誤](../assets/bug.svg)  — 測試版PWA [!DNL Live Search] 不支援 [事件處理](https://devdocs.magento.com/shared-services/storefront-events-sdk.html).

## [!DNL Live Search] 1.3.1 {#131}

* 與Adobe Commerce(EE)相容：2.4.x
* 與Adobe Commerce for Cloud(ECE)相容：2.4.x
* 穩定性：穩定

* ![修正](../assets/fix.svg) - [自訂價格屬性](https://docs.magento.com/user-guide/stores/attributes-input-types.html) 設為 [face]({% link live-search/facets-add.md %})。
* ![修正](../assets/fix.svg)  — 修正若無 [貨幣符號](https://docs.magento.com/user-guide/stores/currency-symbols.html) (`data-currency-symbol`)可用。
* ![修正](../assets/fix.svg) - [[!DNL Storefront popover]](storefront-popover.md) 現在會顯示 [特價](https://docs.magento.com/user-guide/catalog/product-price-special.html) （最低最終價格）。

## [!DNL Live Search] 1.3.0 {#130}

* 與Adobe Commerce(EE)相容：2.4.x
* 與Adobe Commerce for Cloud(ECE)相容：2.4.x
* 穩定性：穩定

* ![新增](../assets/new.svg) - [效能](performance.md) 「報表控制面板」可提供購物者所使用搜尋詞的深入分析。
* ![新增](../assets/new.svg) - [!DNL Live Search] [Storefront事件SDK](https://devdocs.magento.com/shared-services/storefront-events-sdk.html) 可透過事件發佈和訂閱服務及量度來存取通用資料層。
* ![修正](../assets/fix.svg) - [[!DNL Storefront popover]](storefront-popover.md) 有新 `active` 類別 `.search-autocomplete` 控制可見性的容器。
* ![修正](../assets/fix.svg)  — 在店面， [搜尋詞](https://docs.magento.com/user-guide/marketing/search-terms-popular.html) 頁尾連結已移除，且其快取已停用 [!DNL Live Search] 安裝。
* ![錯誤](../assets/bug.svg)  — 搜索適配器的修補程式可處理重複產品。
* ![錯誤](../assets/bug.svg) - [!DNL Live Search] 支援 [單源](https://docs.magento.com/user-guide/catalog/inventory-sources.html) 具有多個（虛擬）的（物理）清點位置 [股票](https://docs.magento.com/user-guide/catalog/inventory-stock.html). 目前不支援多個庫存來源。

## [!DNL Live Search] 1.2.0 {#120}

* 與Adobe Commerce(EE)相容：2.4.x
* 與Adobe Commerce for Cloud(ECE)相容：2.4.x
* 穩定性：穩定

* ![新增](../assets/new.svg) - [[!DNL Storefront popover]](storefront-popover.md) 當購物者在「搜尋」方塊中輸入查詢時，顯示最上層搜尋結果的建議產品和縮圖影像。
* ![新增](../assets/new.svg)  — 商務 *管理* 在鍵盤長時間不活動期間，工作階段保持開啟
* ![新增](../assets/new.svg) - [!DNL Live Search] 上線後自動啟用
* ![修正](../assets/fix.svg)  — 初始索引時間不到1小時
* ![修正](../assets/fix.svg)  — 幾乎即時增量產品更新（安裝和安裝後）
* ![修正](../assets/fix.svg)  — 同義詞編輯器中的可排序列
* ![修正](../assets/fix.svg) - [!DNL Live Search] 如果搜尋條件包含空的排序順序值，則不再擲回錯誤
* ![修正](../assets/fix.svg)  — 如果屬性代碼包含「to」或「from」字串，則範圍篩選不再中斷

## [!DNL Live Search] 1.1.0 {#110}

* 與Adobe Commerce(EE)相容：2.4.x
* 與Adobe Commerce for Cloud(ECE)相容：2.4.x
* 穩定性：穩定

* ![錯誤](../assets/bug.svg) - [!DNL Live Search] 服務僅支援 [基本貨幣](https://docs.magento.com/user-guide/stores/currency-configuration.html) Adobe Commerce裝置。
* ![錯誤](../assets/bug.svg)  — 新增面向時，產品屬性摘要在設為 `Update on Save`. 若要避免此問題，請前往 [索引管理](https://docs.magento.com/user-guide/system/index-management.html) 並將產品屬性摘要設為 `Update by Schedule`.
* ![錯誤](../assets/bug.svg) - [!DNL Live Search] 同義字是根據商店檢視而定義，但目前是根據網站儲存，並以 `environmentId` + `storeViewCode`. 因此，Adobe Commerce安裝中所有網站和儲存檢視都會共用相同的同義字集。 最近建立的儲存視圖同義詞集優先。
* ![錯誤](../assets/bug.svg)  — 如果同義詞詞包含多個單詞，則每個單詞都被視為單獨的同義詞。 例如，如果您將「time piece」定義為「watch」的同義字，則「time」和「piece」都會視為watch的同義字。

## 檔案

若要深入了解：

* [Adobe Commerce開發人員檔案](https://devdocs.magento.com/)
* [Adobe Commerce使用手冊](https://docs.magento.com/user-guide/)
* [[!DNL Live Search] 在Marketplace上](https://marketplace.magento.com/magento-live-search.html)
