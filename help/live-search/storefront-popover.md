---
title: "[!DNL Storefront Popover]"
description: 「 [!DNL Live Search storefront popover] 動態返回建議的產品和縮略圖。」
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: 3820736a25942b147d6e2c7b8820c360d6a0a535
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# [!DNL Storefront Popover]

當 [!DNL Live Search] 是 [已安裝](install.md)的 [!DNL popover] 當購物者鍵入 [搜索](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) 框。 鍵入每個字元後， [!DNL popover] 將使用建議的產品和頂級搜索結果的縮略圖進行更新。

[!DNL Live Search] 返回兩個或更多字元的查詢的結果。 對於部分匹配，每個字的最大字元數為20。 「鍵入時搜索」查詢中的字元數不可配置。

## 可搜索屬性

要生成目標明確的結果，請查看 [可搜索](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) (`searchable=true`)產品屬性。 為確保關聯性，只有在屬性包含含有明確和簡明含義的內容時，才使屬性可搜索。 避免使用包含較不精確、較長文本的屬性，如 `description`，雖然預設情況下啟用搜索功能，但會降低搜索結果的精度。 例如，如果某人搜索「短褲」，而且有帶有「短袖」一詞描述的襯衫，則搜索結果中將包含這些襯衫。

以下屬性始終可搜索：

* `sku`
* `name`
* `categories`

[[!DNL Live Search popover]](assets/storefront-search-as-you-type.png)

## [!DNL Popover] 頁大小

的頁面大小 [!DNL popover] 確定可返回的自動完成產品行數。 以前，頁面大小硬編碼為六行。 然而， `page_size` 值現在是可通過 *管理*。 在Live Search安裝過程中， `page_size` 值更改為 [目錄搜索](https://experienceleague.adobe.com/docs/commerce-admin/config/catalog/catalog.html) - `Autocomplete Limit` 的子菜單。

預設情況下，「目錄搜索 — 自動完成限制」(Catalog Search - Autocomplete Limit)值設定為八行（或八行）。 更改 [!DNL popover]，執行以下操作：

1. 在 *管理* 邊欄，轉到 **商店** >設定> **配置**。
1. 在左面板中，展開 **目錄** 選擇 **目錄** 的子菜單。
1. 展開 *目錄搜索* 的子菜單。
1. 設定 **自動完成限制** 到要允許的行數 [!DNL popover]。
1. 完成後，按一下 **保存配置**。

## 限制

* 的 [!DNL Live Search] [!DNL storefront popover] 僅適用於使用 *盧馬* 主題，或基於 *盧馬*。
* 的 [!DNL popover] 不支援 *空白* 的子菜單。 請參閱 [造型 [!DNL Popover] 元素](storefront-popover-styling.md) 來瞭解更多資訊。
* 的 [!DNL popover] 在快速訂單窗體上不受支援。
* 商家可以自定義和擴展小部件或店面元素(例如：使用 [目錄服務](../catalog-service/overview.md) Storefront API，但這超出了Adobe支援團隊的範圍。
