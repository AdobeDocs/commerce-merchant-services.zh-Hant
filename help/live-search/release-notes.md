---
title: Live Search發行說明
description: 來自Adobe Commerce的Live Search的最新發佈資訊。
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
source-git-commit: 65126f10574801f7ea8d0a863e9bb512dca13f39
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 1%

---

# [!DNL Live Search] 發行說明

本發行說明描述 [!DNL Live Search] 包括：

* ![新建](../assets/new.svg)  — 新功能
* ![修復](../assets/fix.svg)  — 修復和改進
* ![蟲](../assets/bug.svg)  — 已知問題

## [!DNL Live Search] 2.0

* 與Adobe Commerce(EE)相容：2.4.x
* 與Adobe Commerce雲(ECE)相容：2.4.x
* 穩定性：穩定

現有 [!DNL Live Search] 安裝必須升級到 [!DNL Live Search] 2.0.0利用以下新功能、修復和改進：

* ![新建](../assets/new.svg) - [!DNL Live Search] 現在支援PHP 8.1，用於運行Adobe Commerce2.4.4的安裝。
* ![新建](../assets/new.svg) - `Magento_ElasticsearchCatalogPermissionsGraphQl` 模組將添加到在安裝過程中禁用的模組清單中。
* ![新建](../assets/new.svg)  — 中的可用行數 [[!DNL storefront popover]](quick-tour.md) 可從 *管理*。
* ![新建](../assets/new.svg) - Beta [PWA](https://developer.adobe.com/commerce/pwa-studio/) 相容性 [!DNL Live Search]。
* ![新建](../assets/new.svg) - [!DNL Live Search] 安裝過程會隨高級進程更改而更新。
* ![修復](../assets/fix.svg) - [高級搜索](https://docs.magento.com/user-guide/catalog/search-advanced.html) 連結從店面頁腳中刪除。
* ![蟲](../assets/bug.svg)  — 以下產品屬性不受支援 [MagentoGraphQL API](https://devdocs.magento.com/guides/v2.4/graphql) 當用於PWA的beta版時： `description`。 `name`。 `short_description`
* ![蟲](../assets/bug.svg) -PWA的Beta版 [!DNL Live Search] 不支援 [事件處理](https://devdocs.magento.com/shared-services/storefront-events-sdk.html)。

## [!DNL Live Search] 1.3.1

* 與Adobe Commerce(EE)相容：2.4.x
* 與Adobe Commerce雲(ECE)相容：2.4.x
* 穩定性：穩定

* ![修復](../assets/fix.svg) - [自定義價格屬性](https://docs.magento.com/user-guide/stores/attributes-input-types.html) 配置為 [面]({% link live-search/facets-add.md %})。
* ![修復](../assets/fix.svg)  — 已修復問題，導致在沒有 [貨幣符號](https://docs.magento.com/user-guide/stores/currency-symbols.html) (`data-currency-symbol`)。
* ![修復](../assets/fix.svg) - [[!DNL Storefront popover]](storefront-popover.md) 現在顯示 [特殊價格](https://docs.magento.com/user-guide/catalog/product-price-special.html) （最終價格）。

## [!DNL Live Search] 1.3.0

* 與Adobe Commerce(EE)相容：2.4.x
* 與Adobe Commerce雲(ECE)相容：2.4.x
* 穩定性：穩定

* ![新建](../assets/new.svg) - [效能](performance.md) reporting dashboard提供了消費者使用的搜索術語的洞察。
* ![新建](../assets/new.svg) - [!DNL Live Search] [店面事件SDK](https://devdocs.magento.com/shared-services/storefront-events-sdk.html) 通過事件發佈和訂閱服務以及度量提供對公共資料層的訪問。
* ![修復](../assets/fix.svg) - [[!DNL Storefront Popover]](https://devdocs.magento.com/live-search/storefront-popover.html) 有新的 `active` 類 `.search-autocomplete` 控制可見性的容器。
* ![修復](../assets/fix.svg)  — 在店面， [搜索詞](https://docs.magento.com/user-guide/marketing/search-terms-popular.html) 頁腳連結已刪除，其快取已禁用 [!DNL Live Search] 安裝。
* ![蟲](../assets/bug.svg)  — 搜索適配器的修補程式可處理重複的產品。
* ![蟲](../assets/bug.svg) - [!DNL Live Search] 支援 [單源](https://docs.magento.com/user-guide/catalog/inventory-sources.html) 具有多個（虛擬）庫存位置的（物理）庫存 [股票](https://docs.magento.com/user-guide/catalog/inventory-stock.html)。 此時不支援多個庫存來源。

## [!DNL Live Search] 1.2.0

* 與Adobe Commerce(EE)相容：2.4.x
* 與Adobe Commerce雲(ECE)相容：2.4.x
* 穩定性：穩定

* ![新建](../assets/new.svg) - [[!DNL Storefront popover]](storefront-popover.md) 當購物者在「搜索」框中鍵入查詢時，顯示頂級搜索結果的建議產品和縮略圖。
* ![新建](../assets/new.svg)  — 商業 *管理* 會話在鍵盤不活動的長時間內保持開啟狀態
* ![新建](../assets/new.svg) - [!DNL Live Search] 登機後自動啟用
* ![修復](../assets/fix.svg)  — 初始索引時間不到1小時
* ![修復](../assets/fix.svg)  — 接近即時的增量產品更新（安裝和安裝後）
* ![修復](../assets/fix.svg)  — 同義詞編輯器中的可排序列
* ![修復](../assets/fix.svg) - [!DNL Live Search] 如果搜索條件包含空排序順序值，則不再引發錯誤
* ![修復](../assets/fix.svg)  — 如果屬性代碼包含字串「to」或「from」，則範圍篩選不再斷開

## [!DNL Live Search] 1.1.0

* 與Adobe Commerce(EE)相容：2.4.x
* 與Adobe Commerce雲(ECE)相容：2.4.x
* 穩定性：穩定

* ![蟲](../assets/bug.svg) - [!DNL Live Search] 服務僅支援 [基本幣種](https://docs.magento.com/user-guide/stores/currency-configuration.html) Adobe Commerce裝置。
* ![蟲](../assets/bug.svg)  — 添加方面時，當設定為時，「產品屬性饋送」不能正確更新 `Update on Save`。 要避免此問題，請轉到 [索引管理](https://docs.magento.com/user-guide/system/index-management.html) 並將產品屬性訂閱源設定為 `Update by Schedule`。
* ![蟲](../assets/bug.svg) - [!DNL Live Search] 同義詞是按儲存視圖定義的，但是當前按網站儲存，並用同義詞的組合標識 `environmentId` + `storeViewCode`。 因此，Adobe Commerce安裝內的所有網站和儲存視圖共用同一組同義詞。 最近為儲存視圖建立的同義詞集優先。
* ![蟲](../assets/bug.svg)  — 如果同義詞詞包含多個詞，則每個詞都被視為單獨的同義詞。 例如，如果將「time piece」定義為「watch」的同義詞，則「time」和「piece」都被視為watch的同義詞。

## 文檔

要瞭解更多資訊：

* [Adobe Commerce開發人員文檔](https://devdocs.magento.com/)
* [Adobe Commerce使用手冊](https://docs.magento.com/user-guide/)
* [[!DNL Live Search] 在市場上](https://marketplace.magento.com/magento-live-search.html)
