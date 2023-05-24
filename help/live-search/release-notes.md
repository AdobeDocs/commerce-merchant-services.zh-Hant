---
title: '''[!DNL Live Search] 發行說明'
description: 「的最新版本資訊 [!DNL Live Search] 來自Adobe Commerce。」
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
source-git-commit: f955cfc918c19a3c32126d8c9ef8a59b0e0dce0a
workflow-type: tm+mt
source-wordcount: '1241'
ht-degree: 0%

---

# [!DNL Live Search] 發行說明

以下版本說明說明最新版本的 [!DNL Live Search].
提供目前主要發行版本的支援。 舊版的發行說明僅供參考。
更新包括：

![新增](../assets/new.svg) 新功能
![修正](../assets/fix.svg) 修正和改良
![錯誤](../assets/bug.svg) 已知問題


_2023年4月25日_

![新增](../assets/new.svg) Live Search客戶現在可以利用新的 [SaaS價格索引器](../price-index/index.md).

## [!DNL Live Search] 3.0.1 {#301}

_2023年3月14日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

### 新功能

* 規則預覽中的產品專案卡
* [產品清單頁面Widget](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-storefront/plp-styling.html)
* [類別篩選選項](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/#facets)
* 新增拖放以建立Pin事件的功能
* 新釘選動作：
   * 釘選至點 — 按一下即可建立釘選事件的釘選按鈕
   * 釘選到頂端 — 將產品放在第一個位置
   * 釘選至底部 — 將產品置於結果底部
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
* 修正當有多個事件時，正確刪除特定事件的問題
* 修正當新增事件時未更新的現有規則事件
* 已修正詳細資料中的第二個「編輯」點按， [!DNL Live Search] 需要重新載入的頁面
* 同義字：修正使用者點按退出輸入時，無法將焦點傳回欄位的問題
* 其他微幅錯誤修正與效能更新


* ![錯誤](../assets/bug.svg)  — 僅在「即時搜尋」Widget中支援「為您推薦」的排名。 預設的Luma和PWA搜尋功能不支援此功能。
* ![錯誤](../assets/bug.svg)  — 自訂價格屬性Facet無法在Luma中正確轉譯，但API會正確篩選它們。

商家必須升級 [!DNL Live Search] 擴充功能版本>= 3.0.1以存取這些功能。

建議在推送至生產環境前進行升級和測試。 確認測試環境結果後，請考慮在非尖峰時段升級生產環境。

## 舊版

+++2.0.5和舊版

## [!DNL Live Search] 2.0.5 {#205}

[!BADGE 相容性]{type=Informative tooltip="相容性"}

* ![修正](../assets/fix.svg)  — 當SDK資源因網路問題而無法使用時，即時搜尋會擲回錯誤。 此錯誤已修正。

商家必須升級Live Search擴充功能>= 2.0.5版才能存取這些功能。

建議在推送至生產環境前進行升級和測試。 確認測試環境結果後，請考慮在非尖峰時段升級生產環境。

### [!DNL Live Search] 2.0.4 {#204}

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 即時搜尋現在支援以管理員中的「顯示無庫存產品」設定來篩選。 如果「顯示無庫存產品」設為false， `inStock = true` 會新增至篩選器。
![修正](../assets/fix.svg) 為了提高效能，「建議」區塊已從「即時搜尋」快顯視窗中移除。 如果您想要取代功能，資料仍會透過GraphQL傳遞。
![修正](../assets/fix.svg) `categories` 和 `categoryPath` 已取代 `categoryIds` 用於類別篩選。 深入瞭解 [productSearch](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) 主題。
![修正](../assets/fix.svg) 先前，繫結至B2B公司的使用者在執行搜尋時會收到錯誤的客戶群組代碼。 即時搜尋現在會傳回正確的值。
![修正](../assets/fix.svg) 先前，當搜尋不存在的辭彙時，即時搜尋會傳回錯誤。 此錯誤現已修正。

商家必須升級 [!DNL Live Search] 擴充功能版本>= 2.0.4以存取這些功能。

建議使用者在推送至生產環境之前先升級和測試。 確認測試環境結果後，請考慮在非尖峰時段升級生產環境。

### [!DNL Live Search] 2.0.3 {#203}

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) Live Search現在藉由接受類別許可權、共用類別目錄和客戶群組特定定價，來支援B2B功能。

商家必須升級 [!DNL Live Search] 擴充功能版本>= 2.0.3以存取這些功能。

建議使用者在推送至生產環境之前先升級和測試。 確認測試環境結果後，請考慮在非尖峰時段升級生產環境。

### [!DNL Live Search] 2.0 {#20}

[!BADGE 相容性]{type=Informative tooltip="相容性"}

現有 [!DNL Live Search] 安裝必須升級至 [!DNL Live Search] 2.0.0以運用下列新功能、修正和改良：

![新增](../assets/new.svg) [!DNL Live Search] 對於執行Adobe Commerce 2.4.4的安裝，現在支援PHP 8.1。
![新增](../assets/new.svg) 此 `Magento_ElasticsearchCatalogPermissionsGraphQl` 模組會新增至安裝期間停用的模組清單。
![新增](../assets/new.svg) 中可用的行數 [[!DNL storefront popover]](quick-tour.md) 可從以下網址設定： *管理員*.
![新增](../assets/new.svg) Beta [PWA](https://developer.adobe.com/commerce/pwa-studio/) 相容性 [!DNL Live Search].
![新增](../assets/new.svg) 此 [!DNL Live Search] 安裝程式會以進階程式變更更新。
![修正](../assets/fix.svg) [進階搜尋](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) 連結已從店面頁尾移除。
![錯誤](../assets/bug.svg) 下列產品屬性不受支援 [Commerce GraphQL API](https://developer.adobe.com/commerce/webapi/graphql/) 使用與PWA的Beta版相關時： `description`， `name`， `short_description`
![錯誤](../assets/bug.svg) 的PWA測試版 [!DNL Live Search] 不支援 [事件處理](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).

### [!DNL Live Search] 1.3.1 {#131}

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![修正](../assets/fix.svg) [自訂價格屬性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/attributes-input-types.html) 設定為時不再傳回錯誤 [Facet]({%連結live-search/facets-add.md %})。
![修正](../assets/fix.svg) 修正無時導致錯誤發生的問題 [貨幣符號](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html#step-5%3A-customize-currency-symbols-(optional)) (`data-currency-symbol`)可供使用。
![修正](../assets/fix.svg) [[!DNL Storefront popover]](storefront-popover.md) 現在顯示 [特殊價格](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-special.html) （最低最終價格）。

### [!DNL Live Search] 1.3.0 {#130}

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) [效能](performance.md) 報表儀表板可讓您深入瞭解購物者使用的搜尋字詞。
![新增](../assets/new.svg) [!DNL Live Search] [店面事件SDK](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) 可讓您存取具有事件發佈和訂閱服務以及量度的通用資料層。
![修正](../assets/fix.svg) 此 [[!DNL Storefront popover]](storefront-popover.md) 有新的 `active` 的類別 `.search-autocomplete` 控制可見性的容器。
![修正](../assets/fix.svg) 在店面， [搜尋字詞](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html#popular-search-terms) 頁尾連結已移除，而且其快取已停用 [!DNL Live Search] 安裝。
![錯誤](../assets/bug.svg) Search配接器的修補程式可處理重複的產品。
![錯誤](../assets/bug.svg) [!DNL Live Search] 支援 [單一來源](https://experienceleague.adobe.com/docs/commerce-admin/inventory/sources/sources-manage.html) 具有多個（虛擬）的（實體）盤點地點 [庫存](https://experienceleague.adobe.com/docs/commerce-admin/inventory/stocks/stocks-manage.html). 目前不支援多個詳細目錄來源。

### [!DNL Live Search] 1.2.0 {#120}

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) [[!DNL Storefront popover]](storefront-popover.md) 當購物者在「搜尋」方塊中輸入查詢時，顯示建議的產品和排名在前的搜尋結果的縮圖影像。
![新增](../assets/new.svg) 商務 *管理員* 長時間鍵盤不活動期間，工作階段會保持開啟狀態
![新增](../assets/new.svg) [!DNL Live Search] 上線後會自動啟用
![修正](../assets/fix.svg) 初始索引時間不到一小時
![修正](../assets/fix.svg) 近乎即時地增量產品更新（安裝及設定後）
![修正](../assets/fix.svg) 同義字編輯器中的可排序欄
![修正](../assets/fix.svg) [!DNL Live Search] 如果搜尋條件包含空白的排序順序值，不再擲回錯誤
![修正](../assets/fix.svg) 如果屬性程式碼包含字串「to」或「from」，則範圍篩選不再中斷

### [!DNL Live Search] 1.1.0 {#110}

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![錯誤](../assets/bug.svg) 此 [!DNL Live Search] 服務僅支援 [基本貨幣](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html) 安裝Adobe Commerce的ID。
![錯誤](../assets/bug.svg) 新增Facet時，產品屬性摘要在設為時無法正確更新 `Update on Save`. 若要避免此問題，請前往 [索引管理](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) 並將產品屬性摘要設定為 `Update by Schedule`.
![錯誤](../assets/bug.svg) [!DNL Live Search] 同義字是按商店檢視定義，但目前是按網站儲存，並以以下各項的組合識別 `environmentId` 和 `storeViewCode`. 因此，Adobe Commerce安裝中的所有網站和商店檢視會共用同義字。 系統會優先處理最近建立的商店檢視同義字集。
![錯誤](../assets/bug.svg) 如果同義字詞包含多個字詞，則每個字詞都會被視為個別的同義字。 例如，如果您將「time piece」定義為「watch」的同義字，「time」和「piece」都會被視為watch的同義字。

+++

## 檔案

若要深入瞭解：

* [Adobe Commerce開發人員檔案](https://developer.adobe.com/commerce/docs)
* [Adobe Commerce使用手冊](https://experienceleague.adobe.com/docs/commerce.html)
* [[!DNL Live Search] 在市集上](https://marketplace.magento.com/magento-live-search.html)
