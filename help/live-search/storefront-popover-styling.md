---
title: 「樣式 [!DNL Popover] 元素」
description: 「關於自訂的技術說明 [!DNL Live Search storefront popover]"
exl-id: 033049f2-976e-4299-b026-333ac4b481a3
source-git-commit: 67da9016d4bca9750fa9e440cce08ad1ae7100e2
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# 樣式 [!DNL Popover] 元素

此 [[!DNL storefront popover]](storefront-popover.md) 一律顯示產品 `name` 和 `price`，且無法設定欄位選項。 不過， [!DNL popover] 可以使用CSS類別來設定元素的樣式。 例如，下列宣告會變更 [!DNL popover] 容器和頁尾。

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

下列類別選取器可用來設定容器和產品元素在 [!DNL popover].

* `.livesearch.popover-container`
* `.livesearch.view-all-footer`
* `.livesearch.products-container`
* `.livesearch.product-result`
* `.livesearch.product-name`
* `.livesearch.product-price`

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

此 [!DNL storefront popover] 可與自訂的 [主題](https://developer.adobe.com/commerce/frontend-core/guide/themes/) 會繼承下列專案的必要檔案： *Luma*. 此 `top.search` 中的區塊 `header-wrapper` 的 `Magento_Search` 模組不可修改。

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
