---
title: '"[!DNL Live Search] 發行說明'''
description: '"最新發佈資訊 [!DNL Live Search] 來自Adobe Commerce。」'
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
source-git-commit: f955cfc918c19a3c32126d8c9ef8a59b0e0dce0a
workflow-type: tm+mt
source-wordcount: '1241'
ht-degree: 0%

---

# [!DNL Live Search] 發行說明

本發行說明描述 [!DNL Live Search]。
為當前主發佈的版本提供支援。 提供了舊版本的發行說明供參考。
更新包括：

![新建](../assets/new.svg) 新功能
![修復](../assets/fix.svg) 修復和改進
![蟲](../assets/bug.svg) 已知問題


_2023年4月25日_

![新建](../assets/new.svg) 現在， Live Search客戶可以利用新的 [SaaS價格索引器](../price-index/index.md)。

## [!DNL Live Search] 3.0.1 {#301}

_2023年3月14日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

### 新功能

* 規則預覽中的產品物料卡
* [產品清單頁面構件](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-storefront/plp-styling.html)
* [類別篩選選項](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/#facets)
* 已添加拖放功能以建立Pin事件
* 新建Pin操作：
   * 針到針 — 用「針」按鈕建立「針」事件，只需按一下一次
   * 固定至頂部 — 將產品置於第一個位置
   * 固定至底部 — 將產品置於結果底部
   * 按一下一下即可取消固定事件
* [規則智慧排名](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-admin/rules/rules-add.html#ranking-type)

### 更新

* 配置規則現在自動對位置進行唯一排序
* 刪除現有事件將立即更新預覽
* 無法保存沒有事件的規則
* 刪除分頁「選擇類型」選擇器
* 已為未保存的規則添加新的「編輯」狀態

### 修復

* 在保存期間發生未完成事件時修復伺服器錯誤
* 已修復在存在多個事件時正確刪除特定事件
* 添加新事件時未更新的已修復現有規則事件
* 在從詳細資訊中按一下第二個「編輯」時修復， [!DNL Live Search] 頁面需要重新載入
* 同義詞：當用戶按一下輸入時，他們無法將焦點返回到欄位時，已修復問題
* 其他次要錯誤修復和效能更新


* ![蟲](../assets/bug.svg)  — 僅在Live Search小部件中支援按「推薦給您」排名。 預設的Luma和PWA搜索功能不支援它。
* ![蟲](../assets/bug.svg)  — 自定義價格屬性facet在Luma中無法正確呈現，但API會對其進行適當篩選。

商家必須升級 [!DNL Live Search] 擴展版本>= 3.0.1以訪問這些功能。

建議先升級和test，然後再推向生產。 在驗證其測試環境結果後，請考慮在非高峰時段升級生產環境。

## 以前的版本

+++2.0.5和之前版本

## [!DNL Live Search] 2.0.5 {#205}

[!BADGE 相容性]{type=Informative tooltip="相容性"}

* ![修復](../assets/fix.svg)  — 當SDK資源由於網路問題而不可用時，Live Search將引發錯誤。 此Bug已修復。

商家必須升級Live Search擴展版>= 2.0.5才能訪問這些功能。

建議先升級和test，然後再推向生產。 在驗證其測試環境結果後，請考慮在非高峰時段升級生產環境。

### [!DNL Live Search] 2.0.4 {#204}

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg) 現在，Live Search支援通過管理員中的「Display Out of Stock Products」（顯示出庫存產品）設定進行篩選。 如果「Display Out of Stock Products」設定為false, `inStock = true` 的子菜單。
![修復](../assets/fix.svg) 為了提高效能，已從Live Search彈出菜單中刪除「建議」塊。 資料仍通過GraphQL，以防您替換該功能。
![修復](../assets/fix.svg) `categories` 和 `categoryPath` 已更換 `categoryIds` 的子菜單。 閱讀 [產品搜索](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) 主題。
![修復](../assets/fix.svg) 以前，與B2B公司關聯的用戶在進行搜索時會收到不正確的客戶組代碼。 Live Search現在返回正確的值。
![修復](../assets/fix.svg) 以前，在搜索不存在的術語時，Live Search將返回錯誤。 那個蟲子現在已經修復了。

商家必須升級 [!DNL Live Search] 擴展版本>= 2.0.4以訪問這些功能。

建議用戶在推向生產前升級和test。 在驗證其測試環境結果後，請考慮在非高峰時段升級生產環境。

### [!DNL Live Search] 2.0.3 {#203}

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg) Live Search現在支援B2B功能，方法是遵守類別權限、共用目錄和特定於客戶組的定價。

商家必須升級 [!DNL Live Search] 擴展版本>= 2.0.3以訪問這些功能。

建議用戶在推向生產前升級和test。 在驗證其測試環境結果後，請考慮在非高峰時段升級生產環境。

### [!DNL Live Search] 2.0 {#20}

[!BADGE 相容性]{type=Informative tooltip="相容性"}

現有 [!DNL Live Search] 安裝必須升級到 [!DNL Live Search] 2.0.0利用以下新功能、修復和改進：

![新建](../assets/new.svg) [!DNL Live Search] 現在支援PHP 8.1，用於運行Adobe Commerce2.4.4的安裝。
![新建](../assets/new.svg) 的 `Magento_ElasticsearchCatalogPermissionsGraphQl` 模組將添加到在安裝過程中禁用的模組清單中。
![新建](../assets/new.svg) 中的可用行數 [[!DNL storefront popover]](quick-tour.md) 可從 *管理*。
![新建](../assets/new.svg) β [PWA](https://developer.adobe.com/commerce/pwa-studio/) 相容性 [!DNL Live Search]。
![新建](../assets/new.svg) 的 [!DNL Live Search] 安裝過程會隨高級進程更改而更新。
![修復](../assets/fix.svg) [高級搜索](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) 連結從店面頁腳中刪除。
![蟲](../assets/bug.svg) 不支援以下產品屬性 [商業GraphQLAPI](https://developer.adobe.com/commerce/webapi/graphql/) 當用於PWA的beta版時： `description`。 `name`。 `short_description`
![蟲](../assets/bug.svg) PWA的β釋放 [!DNL Live Search] 不支援 [事件處理](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/)。

### [!DNL Live Search] 1.3.1 {#131}

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![修復](../assets/fix.svg) [自定義價格屬性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/attributes-input-types.html) 配置為 [面]({% link live-search/facets-add.md %})。
![修復](../assets/fix.svg) 已修復導致錯誤在否時發生的問題 [貨幣符號](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html#step-5%3A-customize-currency-symbols-(optional)) (`data-currency-symbol`)。
![修復](../assets/fix.svg) [[!DNL Storefront popover]](storefront-popover.md) 現在顯示 [特殊價格](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-special.html) （最終價格）。

### [!DNL Live Search] 1.3.0 {#130}

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg) [效能](performance.md) reporting dashboard提供了消費者使用的搜索術語的洞察。
![新建](../assets/new.svg) [!DNL Live Search] [店面事件SDK](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) 通過事件發佈和訂閱服務以及度量提供對公共資料層的訪問。
![修復](../assets/fix.svg) 的 [[!DNL Storefront popover]](storefront-popover.md) 有新的 `active` 類 `.search-autocomplete` 控制可見性的容器。
![修復](../assets/fix.svg) 在店面， [搜索詞](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html#popular-search-terms) 頁腳連結已刪除，其快取已禁用 [!DNL Live Search] 安裝。
![蟲](../assets/bug.svg) Search適配器的修補程式可處理重複的產品。
![蟲](../assets/bug.svg) [!DNL Live Search] 支援 [單源](https://experienceleague.adobe.com/docs/commerce-admin/inventory/sources/sources-manage.html) 具有多個（虛擬）庫存位置的（物理）庫存 [股票](https://experienceleague.adobe.com/docs/commerce-admin/inventory/stocks/stocks-manage.html)。 現在不支援多個庫存來源。

### [!DNL Live Search] 1.2.0 {#120}

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg) [[!DNL Storefront popover]](storefront-popover.md) 當購物者在「搜索」框中鍵入查詢時，顯示頂級搜索結果的建議產品和縮略圖。
![新建](../assets/new.svg) 商業 *管理* 會話在鍵盤不活動的長時間內保持開啟狀態
![新建](../assets/new.svg) [!DNL Live Search] 登機後自動啟用
![修復](../assets/fix.svg) 初始索引時間不到1小時
![修復](../assets/fix.svg) 增量產品更新接近即時（安裝和安裝後）
![修復](../assets/fix.svg) 同義詞編輯器中的可排序列
![修復](../assets/fix.svg) [!DNL Live Search] 如果搜索條件包含空排序順序值，則不再引發錯誤
![修復](../assets/fix.svg) 如果屬性代碼包含字串&quot;to&quot;或&quot;from&quot;，則範圍篩選不再斷開

### [!DNL Live Search] 1.1.0 {#110}

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![蟲](../assets/bug.svg) 的 [!DNL Live Search] 服務僅支援 [基本幣種](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html) Adobe Commerce裝置。
![蟲](../assets/bug.svg) 添加方面時，當設定為時，「產品屬性饋送」不能正確更新 `Update on Save`。 要避免此問題，請轉到 [索引管理](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) 並將產品屬性訂閱源設定為 `Update by Schedule`。
![蟲](../assets/bug.svg) [!DNL Live Search] 同義詞是按儲存視圖定義的，但是當前按網站儲存，並用同義詞的組合標識 `environmentId` 和 `storeViewCode`。 因此，Adobe Commerce安裝內的所有網站和儲存視圖共用同義詞。 最近為儲存視圖建立的同義詞集優先。
![蟲](../assets/bug.svg) 如果同義詞詞包含多個詞，則每個詞都被視為單獨的同義詞。 例如，如果將&quot;time piece&quot;定義為&quot;watch&quot;的同義詞，則&quot;time&quot;和&quot;piece&quot;都被視為watch的同義詞。

+++

## 文檔

要瞭解更多資訊：

* [Adobe Commerce開發人員文檔](https://developer.adobe.com/commerce/docs)
* [Adobe Commerce使用手冊](https://experienceleague.adobe.com/docs/commerce.html)
* [[!DNL Live Search] 在市場上](https://marketplace.magento.com/magento-live-search.html)
