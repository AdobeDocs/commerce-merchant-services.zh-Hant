---
title: "[!DNL Storefront Popover]"
description: 「 [!DNL Live Search storefront popover] 動態傳回建議的產品和縮圖。」
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: 92889130fd7482e0b99fb08746e6fd2830b0345e
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# [!DNL Storefront Popover]

當 [!DNL Live Search] is [已安裝](install.md), [!DNL popover] 當購物者在 [搜尋](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) 框。 在輸入每個字元後， [!DNL popover] 會以最上層搜尋結果的建議產品和縮圖影像更新。

[!DNL Live Search] 傳回兩個或兩個以上字元的查詢結果。 若是部分比對，每個字詞的字元數上限為20。 「按鍵入搜索」查詢中的字元數不可配置。

## 可搜尋屬性

若要產生目標明確的結果，請檢閱 [可搜尋](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) (`searchable=true`)產品屬性。 為確保關聯性，只有在屬性中包含含義清晰且簡明的內容時，才可搜索屬性。 請避免使用包含較少精確、冗長文字的屬性，例如 `description`，雖然預設會啟用搜尋功能，但可能會降低搜尋結果的精確度。 例如，如果某人搜尋「短褲」，而有描述包含「短袖」一詞的襯衫，則搜尋結果會包含這些襯衫。

下列屬性一律可供搜尋：

* `sku`
* `name`
* `categories`

[[!DNL Live Search popover]](assets/storefront-search-as-you-type.png)

## [!DNL Popover] 頁面大小

頁面大小 [!DNL popover] 決定可傳回多少行自動完成的產品。 之前，頁面大小會硬式編碼為六行。 不過， `page_size` 值現在是可從 *管理*. 在Live Search安裝期間， `page_size` 值會變更為 [目錄搜尋](https://experienceleague.adobe.com/docs/commerce-admin/config/catalog/catalog.html) - `Autocomplete Limit` 設定。

依預設，「目錄搜尋 — 自動完成限制」值會設為八行（或列）。 若要變更 [!DNL popover]，請執行下列動作：

1. 在 *管理* 邊欄，轉到 **商店** >設定> **設定**.
1. 在左側面板中，展開 **目錄** 選擇 **目錄** 從設定清單。
1. 展開 *目錄搜尋* 區段。
1. 設定 **自動完成限制** 至您要在 [!DNL popover].
1. 完成後，按一下 **儲存設定**.

## 限制

* 此 [!DNL Live Search] [!DNL storefront popover] 僅適用於使用 *盧馬* 主題，或根據 *盧馬*.
* 此 [!DNL popover] 不支援 *空白* 主題。 請參閱 [樣式 [!DNL Popover] 元素](storefront-popover-styling.md) 了解更多。
* 此 [!DNL popover] 「快速訂購」表單不支援。
