---
title: "[!DNL Storefront Popover]"
description: 「此 [!DNL Live Search storefront popover] 會以動態方式傳回建議的產品和縮圖。」
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: e375404a50dd4972ab584f69d7953aba2c8f4566
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# [!DNL Storefront Popover]

時間 [!DNL Live Search] 是 [已安裝](install.md)， a [!DNL popover] 出現在店面，當購物者輸入 [搜尋](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) 方塊。 輸入每個字元後， [!DNL popover] 已更新為熱門搜尋結果的建議產品和縮圖影像。

[!DNL Live Search] 傳回兩個或更多字元的查詢結果。 若為部分相符，則每個字的字元數上限為20。 「鍵入時搜尋」查詢中的字元數無法設定。

根據預設， [!DNL Live Search] 支援 [搜尋字詞重新導向](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html).

![[!DNL Live Search popover]](assets/storefront-search-as-you-type.png)

>[!TIP]
>
>瞭解如何將產品屬性設定為可在中搜尋 [設定即時搜尋](workspace.md) 文章。

## [!DNL Popover] 頁面大小

的頁面大小 [!DNL popover] 決定可以傳回多少行自動完成產品。 在Live Search安裝期間， `page_size` 值會變更為的目前值 [目錄搜尋](https://experienceleague.adobe.com/docs/commerce-admin/config/catalog/catalog.html) - `Autocomplete Limit` 設定。

依預設，「目錄搜尋 — 自動完成限制」值會設定為八行（或數列）。 若要變更的頁面大小 [!DNL popover]，請執行下列動作：

1. 在 *管理員* 側欄，前往 **商店** >設定> **設定**.
1. 在左側面板中，展開 **目錄** 並選擇 **目錄** 從設定清單中。
1. 展開 *目錄搜尋* 區段。
1. 設定 **自動完成限制** 至您要允許在 [!DNL popover].
1. 完成後，按一下 **儲存設定**.

## 樣式 [!DNL Popover] 範例

您可以自訂外觀與風格 [!DNL Popover] 符合貴公司風格與品牌指導方針的Widget。

此 [!DNL storefront popover] 一律顯示產品 `name` 和 `price`，且無法設定欄位選項。 不過， [!DNL popover] 可以使用為元素設定樣式 [CSS](https://developer.adobe.com/commerce/frontend-core/guide/css/) 類別。 例如，下列宣告會變更 [!DNL popover] 容器和頁尾。

```css
.livesearch.popover-container {
    background-color: lavender;
}

.livesearch.view-all-footer {
    background-color: magenta;
}
```

## 容器可見性

的父元件 `.livesearch.popover-container` 是 `.search-autocomplete`.  此 `.active` 類別指示容器的可見性。 此 `.active` 類別是有條件地新增當 [!DNL popover] 是開啟的。

```css
.search-autocomplete.active   /* visible */
.search-autocomplete          /* not visible */
```

如需有關樣式化店面元素的詳細資訊，請參閱 [階層式樣式表(CSS)](https://developer.adobe.com/commerce/frontend-core/guide/css/) 在 [前端開發人員指南](https://developer.adobe.com/commerce/frontend-core/guide/).

## 類別選取器

您可以使用下列類別選取器，來設定容器和產品元素在 [!DNL popover].

- `.livesearch.popover-container`
- `.livesearch.view-all-footer`
- `.livesearch.products-container`
- `.livesearch.product-result`
- `.livesearch.product-name`
- `.livesearch.product-price`

### 容器類別選取器

#### .livesearch.pover-container

![[!DNL Popover] 容器](assets/livesearch-popover-container.png)

#### .livesearch.view-all-footer

![檢視所有頁尾](assets/livesearch-view-all-footer.png)

### 產品類別選擇器

#### .livesearch.products-container

![產品容器](assets/livesearch-product-container.png)

#### .livesearch.product-result

![產品結果](assets/livesearch-product-result.png)

#### .livesearch.product-name

![產品名稱](assets/livesearch-product-name.png)

#### .livesearch.product-price

![產品價格](assets/livesearch-product-price.png)

#### .livesearch product-link

![產品結果](assets/livesearch-product-link.png)

## 使用修改的主題 {#working-with-modified-theme}

您可以使用 [!DNL storefront popover] 透過自訂 [主題](https://developer.adobe.com/commerce/frontend-core/guide/themes/) 會繼承下列專案的必要檔案： *Luma*. 此 `top.search` 中的區塊 `header-wrapper` 的 `Magento_Search` 模組不可修改。

```html
<referenceContainer name="header-wrapper">
   <block class="Magento\Framework\View\Element\Template" name="top.search" as="topSearch" template="Magento_Search::form.mini.phtml">
      <arguments>
         <argument name="configProvider" xsi:type="object">Magento\Search\ViewModel\ConfigProvider</argument>
      </arguments>
   </block>
</referenceContainer>
```

## 停用 [!DNL popover]

若要停用 [!DNL popover] 並還原標準 [快速搜尋](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) 功能，輸入下列命令：

```bash
bin/magento module:disable Magento_LiveSearchStorefrontPopover
```

## Headless實施

對於採用Headless實作的客戶，您可以安裝 [!DNL Live Search popover] 使用 [npm套件](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).
