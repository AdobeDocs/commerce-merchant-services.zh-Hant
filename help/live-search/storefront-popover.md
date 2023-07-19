---
title: "[!DNL Storefront Popover]"
description: '"此 [!DNL Live Search storefront popover] 會以動態方式傳回建議的產品和縮圖。」'
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: 96a5791c5716f612f473540f27bd3f99b1bfe7c8
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# [!DNL Storefront Popover]

時間 [!DNL Live Search] 是 [已安裝](install.md)， a [!DNL popover] 出現在店面，購物者輸入 [搜尋](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) 方塊。 鍵入每個字元後， [!DNL popover] 已更新為熱門搜尋結果的建議產品和縮圖影像。

[!DNL Live Search] 傳回兩個或更多字元的查詢結果。 若為部分相符，每個字的字元數上限為20。 「鍵入時搜尋」查詢中的字元數無法設定。

## 可搜尋的屬性

若要產生高針對性的結果，請檢閱 [可搜尋](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) (`searchable=true`)產品屬性。 為確保相關性，請讓屬性只有在包含具有清晰簡潔含義的內容時才可供搜尋。 避免使用包含較不精確、冗長文字的屬性，例如 `description`雖然預設為啟用搜尋，但可能會降低搜尋結果的精確度。 例如，如果有人搜尋「短褲」，而襯衫的說明包含「短袖口徑」一詞，則襯衫會包含在搜尋結果中。

下列屬性一律可搜尋：

* `sku`
* `name`
* `categories`

[[!DNL Live Search popover]](assets/storefront-search-as-you-type.png)

## [!DNL Popover] 頁面大小

的頁面大小 [!DNL popover] 決定可以傳回多少行自動完成產品。 之前，頁面大小以硬式編碼撰寫為六行。 不過， `page_size` value現在是可從以下位置設定的設定： *管理員*. 在Live Search安裝期間， `page_size` 值會變更為的目前值 [目錄搜尋](https://experienceleague.adobe.com/docs/commerce-admin/config/catalog/catalog.html) - `Autocomplete Limit` 設定。

依預設，「目錄搜尋 — 自動完成限制」值會設定為八行（或數列）。 若要變更的頁面大小 [!DNL popover]，請執行下列動作：

1. 於 *管理員* 側欄，前往 **商店** >設定> **設定**.
1. 在左側面板中，展開 **目錄** 並選擇 **目錄** 從設定清單中。
1. 展開 *目錄搜尋* 區段。
1. 設定 **自動完成限制** 至您要在 [!DNL popover].
1. 完成後，按一下 **儲存設定**.

## 目錄服務

此 [Adobe Commerce的目錄服務](../catalog-service/overview.md) 擴充功能提供豐富的檢視模型目錄資料，以快速完整地呈現與產品相關的店面體驗。 目錄服務可與Live Search搭配使用，以提供目前原生擴充功能不支援的功能：

* 色票
* 延伸屬性
* 其他產品資訊可以匯入

商戶可使用目錄服務自訂和擴充Widget或店面元素，但這不屬於Adobe支援團隊的範圍。

## 限制

* 此 [!DNL Live Search] [!DNL storefront popover] 僅適用於使用 *Luma* 主題，或根據以下主題的自訂主題： *Luma*. 搜尋結果頁面上的階層連結不包含 *流明* 樣式。
* 此 [!DNL popover] 不支援 *空白* 主題。 另請參閱 [樣式 [!DNL Popover] 元素](storefront-popover-styling.md) 以深入瞭解。
* 此 [!DNL popover] 不支援快速訂購表單。
* 不支援願望清單和產品比較。
* 僅支援基本貨幣。
