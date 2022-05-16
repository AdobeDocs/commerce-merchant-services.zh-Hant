---
title: 「造型 [!DNL Popover] 元素"
description: 「關於自定義 [!DNL Live Search storefront popover]"
exl-id: 033049f2-976e-4299-b026-333ac4b481a3
source-git-commit: bffbede99865e9085f60392e474065a454446370
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# 造型 [!DNL Popover] 元素

的 [[!DNL storefront popover]](storefront-popover.md) 始終顯示產品 `name` 和 `price`，且無法配置欄位的選擇。 但是， [!DNL popover] 元素可以使用CSS類設定樣式。 例如，以下聲明更改了 [!DNL popover] 容器和頁腳。

```css
.livesearch.popover-container {
    background-color: lavender;
}

.livesearch.view-all-footer {
    background-color: magenta;
}
```

## 容器可見性

的父元件 `.livesearch.popover-container` 是 `.search-autocomplete`。  的 `.active` class表示容器的可見性。 的 `.active` 在 [!DNL popover] 開啟。

```css
.search-autocomplete.active   /* visible */
.search-autocomplete          /* not visible */
```

有關造型庫面元素的詳細資訊，請參閱 [層疊樣式表(CSS)](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/css-topics/css-overview.html) 的 [前端開發人員指南](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/bk-frontend-dev-guide.html)。

## 類選擇器

以下類選擇器可用於對中的容器、建議和產品元素進行樣式化 [!DNL popover]。

* `.livesearch.popover-container`
* `.livesearch.view-all-footer`
* `.livesearch.suggestions-container`
* `.livesearch.suggestions-header`
* `.livesearch.suggestion`
* `.livesearch.products-container`
* `.livesearch.product-result`
* `.livesearch.product-name`
* `.livesearch.product-price`

### 容器類選擇器

`.livesearch.popover-container`

![[!DNL Popover] 容器](assets/livesearch-popover-container.png)

`.livesearch.view-all-footer`

![查看所有頁腳](assets/livesearch-view-all-footer.png)

### 建議類選擇器

`.livesearch.suggestions-container`
![建議容器](assets/livesearch-suggestions-container.png)

`.livesearch.suggestions-header`
![建議標題](assets/livesearch-suggestions-header.png)

`.livesearch.suggestion`
![建議](assets/livesearch-suggestion.png)

### 產品類選擇器

`.livesearch.products-container`
![產品容器](assets/livesearch-product-container.png)

`.livesearch.product-result`
![產品結果](assets/livesearch-product-result.png)

`.livesearch.product-name`
![產品名稱](assets/livesearch-product-name.png)

`.livesearch.product-price`
![產品價格](assets/livesearch-product-price.png)

## 使用修改的主題 {#working-with-modified-theme}

的 [!DNL storefront popover] 可與自定義 [主題](https://devdocs.magento.com/guides/v2.3/frontend-dev-guide/themes/theme-overview.html) 繼承所需檔案的 *盧馬*。 的 `top.search` 在 `header-wrapper` 的 `Magento_Search` 不能修改模組。

```html
<referenceContainer name="header-wrapper">
   <block class="Magento\Framework\View\Element\Template" name="top.search" as="topSearch" template="Magento_Search::form.mini.phtml">
      <arguments>
         <argument name="configProvider" xsi:type="object">Magento\Search\ViewModel\ConfigProvider</argument>
      </arguments>
   </block>
</referenceContainer>
```

## 禁用 [!DNL popover]

禁用 [!DNL popover] 並恢復標準 [快速搜索](https://docs.magento.com/user-guide/catalog/search-quick.html) 功能，輸入以下命令：

```bash
bin/magento module:disable Magento_LiveSearchStorefrontPopover
```
