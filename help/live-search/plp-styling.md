---
title: 產品清單頁面Widget
description: 「啟用和設計 [!DNL Live Search Product Listing Page Widget]"
source-git-commit: c4bca0c7238be653dd13b051634c662e5891767d
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# 產品清單頁面Widget

此 [!DNL Live Search Product Listing Page Widget] (PLP)使用商務服務平台，提供效能、可搜尋和可刻面的產品清單頁面。 本主題說明如何啟用和設定PLP介面工具集的樣式。

## 啟用PLP介面工具集

當 [!DNL Live Search] 服務時，預設搜尋功能會轉換為 [!DNL Live Search] 自動。
必須在「管理員」中啟用PLP介面工具集。

1. 前往 **商店** >設定> **設定** > **[!DNL Live Search]** > **店面功能** 設定 **啟用產品清單小工具** 「是」。
1. 選擇 **儲存設定** 以儲存設定。

## 樣式範例

您可以自訂PLP介面工具集的外觀和風格，以符合您的網站，使用 [CSS](https://developer.adobe.com/commerce/frontend-core/guide/css/).

>[!NOTE]
>
>不會繼承Adobe Commerce主題中具有自訂類別的元素。 這些元素必須由其特定類定位，才能與自訂類匹配；主要動作類別無法用於介面工具集按鈕。
>將繼承CSS內的一般目標元素； `button` 會套用至介面工具集按鈕。

突出顯示的div包含目標類 `ds-sdk-product-item__product-name`.

![分頁](assets/plp-css-example.png)

新增規則以使產品成為大寫，借此自訂產品名稱。

```css
.ds-sdk-product-item__product-name {
 text-transform: uppercase;
}
```

![分頁](assets/plp-css-example-after.png)

## CSS類

### 產品清單

* `.ds-sdk-product-list`:外div
* `.ds-sdk-product-list__grid`:內div

![分頁](assets/plp-css-product-list.png)

#### 產品清單分頁

* `.ds-plp-pagination`

![分頁](assets/plp-css-pagination.png)

* `.ds-plp-pagination_item`

![分頁項目](assets/plp-css-pagination-item.png)

* `.ds-plp-pagination_item--current`

![分頁目前項目](assets/plp-css-pagination-item-current.png)

### 介面工具集

* `.ds-widgets`:外div
* `.ds-widgets__actions`:左側內div
* `.ds-widgets__results`:右側內div

![介面工具集結果](assets/plp-css-widgets.png)

### 排序下拉式清單

* `.ds-sdk-sort-dropdown`

![排序下拉式清單](assets/plp-css-dropdown.png)

* `.ds-sdk-sort-dropdown__button`

![下拉式按鈕](assets/plp-css-dropdown-button.png)

* `.ds-sdk-sort-dropdown__items`

![下拉式項目](assets/plp-css-dropdown-items.png)

* `.ds-sdk-sort-dropdown__items--item`

![下拉式項目](assets/plp-css-dropdown-item.png)

* `.ds-sdk-sort-dropdown__items--item-selected`

![下拉式清單選取的項目](assets/plp-css-dropdown-selected.png)

* `.ds-sdk-sort-dropdown__items--item-active`

![下拉式活動選取](assets/plp-css-dropdown-active.png)

### Facet

* `.ds-plp-facets`
* `.ds-plp-facets__header`
* `.ds-plp-facets__header_title`
* `.ds-plp-facets__header__clear-all`

![Facet標題](assets/plp-css-facets-title-clear.png){width="350"}

* `.ds-plp-facets__pills`
* `.ds-sdk-pill`

![小面丸](assets/plp-css-facets-pill.png){width="350"}

* `.ds-sdk-pill__label`
* `.ds-sdk-pill__cta`

![Facet標籤](assets/plp-css-pill-label-cta.png){width="350"}

* `.ds-plp-facets__list`

![Facet清單](assets/plp-css-facets-list.png){width="350"}

* `.ds-sdk-input`
* `.ds-sdk-input__label`
* `.ds-sdk-input__options`
* `.ds-sdk-input_fieldset_show-more`

![輸入](assets/plp-css-sdk-input.png)

* `.ds-sdk-labelled-input`

![標籤輸入](assets/plp-css-labelled-input.png)

* `.ds-sdk-labelled-input__input`
* `.ds-sdk-labelled-input__label`

![輸入標籤](assets/plp-css-labelled-input-label.png)

### 產品項目

* `.ds-sdk-product-item`
* `.ds-sdk-product-item__image`
* `.ds-sdk-product-item__product-name`
* `.ds-sdk-product-item__product-options`
* `.ds-sdk-product-price`
   * `.ds-sdk-product-price--no-discount`
   * `.ds-sdk-product-price--grouped`
   * `.ds-sdk-product-price--bundle`
   * `.ds-sdk-product-price--discount`

![產品](assets/plp-css-product.png)

### 載入

* `.ds-sdk-loading`
* `.ds-sdk-loading__spinner`
* `.ds-sdk-loading__spinner-label`

![載入指示器](assets/plp-css-loading.png)
