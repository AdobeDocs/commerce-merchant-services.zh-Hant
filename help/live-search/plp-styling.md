---
title: 產品清單頁面Widget
description: 啟用並設定樣式 [!DNL Live Search Product Listing Page Widget]
exl-id: f7346a06-a8c7-4a33-8437-ea4f61d9281f
source-git-commit: faf217486d57588d8535c1d605e963c91ec3ee68
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# 產品清單頁面Widget

此 [!DNL Live Search Product Listing Page Widget] (PLP)使用Commerce服務平台，提供高效能、可搜尋且可多面向的產品清單頁面。 本主題說明如何啟用和設定PLP Widget的樣式。

## 啟用PLP Widget

當 [!DNL Live Search] 服務已安裝，預設搜尋功能已轉換為 [!DNL Live Search] 自動。

此 [!DNL Live Search] 新安裝預設啟用PLP Widget。 如果您正在升級 [!DNL Live Search] 而且PLP Widget已關閉，仍會維持關閉。

>[!IMPORTANT]
>
>當 [!DNL Live Search Product Listing Page Widget] 已啟用，則無法變更產品清單頁面上的排序順序方向。

## Widget功能

PLP Widget提供下列現成可用的功能：

- 加入購物車按鈕 — 僅適用於簡單產品。
- 每個產品有多個影像 — 為可設定產品選擇不同顏色時，影像可能會變更。
- 支援色票 — 請注意，色彩屬性必須拼字 `color` 以便程式碼正確驗證。

### 自訂Widget

除了PLP Widget的現成功能以外，您也可以進一步自訂Widget以包含下列功能：

- 依屬性篩選
- 多語言支援
- 價格滑桿

如需有關如何自訂PLP Widget以處理上述功能的資訊，請參閱 `storefront-product-listing-page` 讀我檔案（在下列專案中） [存放庫](https://github.com/adobe/storefront-product-listing-page/).

>[!WARNING]
>
>如果您使用存放庫中的可用程式碼自訂PLP Widget，則需自行負責維護及任何必要的更新。 任何新增PLP Widget功能，若是Adobe發行版本，則可能與您的自訂實施不相容。

## 樣式範例

您可以自訂PLP Widget的外觀與風格，以符合您的網站 [CSS](https://developer.adobe.com/commerce/frontend-core/guide/css/).

>[!NOTE]
>
>Adobe Commerce主題中自訂類別的元素不會繼承。 這些元素必須以其特定類別為目標，以符合自訂類別；主要動作類別在Widget按鈕上無法運作。 會繼承CSS內的一般目標元素； `button` 套用至Widget按鈕。

反白顯示的div包含目標類別 `ds-sdk-product-item__product-name`.

![分頁](assets/plp-css-example.png)

新增規則以大寫方式自訂產品名稱。

```css
.ds-sdk-product-item__product-name {
 text-transform: uppercase;
}
```

![分頁](assets/plp-css-example-after.png)

## CSS類別

### 產品清單

- `.ds-sdk-product-list`：外部div
- `.ds-sdk-product-list__grid`：內部div

![分頁](assets/plp-css-product-list.png)

#### 產品清單分頁

- `.ds-plp-pagination`

![分頁](assets/plp-css-pagination.png)

- `.ds-plp-pagination_item`

![分頁專案](assets/plp-css-pagination-item.png)

- `.ds-plp-pagination_item--current`

![分頁目前專案](assets/plp-css-pagination-item-current.png)

### Widget

- `.ds-widgets`：外部div
- `.ds-widgets__actions`：左側內div
- `.ds-widgets__results`：右側內div

![Widget結果](assets/plp-css-widgets.png)

### 排序下拉式清單

- `.ds-sdk-sort-dropdown`

![排序下拉式清單](assets/plp-css-dropdown.png)

- `.ds-sdk-sort-dropdown__button`

![下拉式清單按鈕](assets/plp-css-dropdown-button.png)

- `.ds-sdk-sort-dropdown__items`

![下拉式清單專案](assets/plp-css-dropdown-items.png)

- `.ds-sdk-sort-dropdown__items--item`

![下拉式清單專案](assets/plp-css-dropdown-item.png)

- `.ds-sdk-sort-dropdown__items--item-selected`

![下拉式清單選取專案](assets/plp-css-dropdown-selected.png)

- `.ds-sdk-sort-dropdown__items--item-active`

![下拉式清單作用中選取專案](assets/plp-css-dropdown-active.png)

### Facet

- `.ds-plp-facets`
- `.ds-plp-facets__header`
- `.ds-plp-facets__header_title`
- `.ds-plp-facets__header__clear-all`

![Facet標題標題](assets/plp-css-facets-title-clear.png){width="350"}

- `.ds-plp-facets__pills`
- `.ds-sdk-pill`

![Facet丸](assets/plp-css-facets-pill.png){width="350"}

- `.ds-sdk-pill__label`
- `.ds-sdk-pill__cta`

![多面向標籤](assets/plp-css-pill-label-cta.png){width="350"}

- `.ds-plp-facets__list`

![Facet清單](assets/plp-css-facets-list.png){width="350"}

- `.ds-sdk-input`
- `.ds-sdk-input__label`
- `.ds-sdk-product-item__product-swatch-group`
- `ds-sdk-product-item__product-swatch-item`
- `.ds-sdk-input_fieldset_show-more`

![輸入](assets/plp-css-sdk-input.png)

- `.ds-sdk-labelled-input`

![標籤的輸入](assets/plp-css-labelled-input.png)

- `.ds-sdk-labelled-input__input`
- `.ds-sdk-labelled-input__label`

![輸入標籤](assets/plp-css-labelled-input-label.png)

### 產品專案

- `.ds-sdk-product-item`
- `.ds-sdk-product-item__image`
- `.ds-sdk-product-item__product-name`
- `.ds-sdk-product-item__product-options`
- `.ds-sdk-product-price`
   - `.ds-sdk-product-price--no-discount`
   - `.ds-sdk-product-price--grouped`
   - `.ds-sdk-product-price--bundle`
   - `.ds-sdk-product-price--discount`

![產品](assets/plp-css-product.png)

### 正在載入

- `.ds-sdk-loading`
- `.ds-sdk-loading__spinner`
- `.ds-sdk-loading__spinner-label`

![正在載入指標](assets/plp-css-loading.png)

## 停用PLP Widget

若要停用PLP Widget：

1. 前往 **商店** >設定> **設定** > **[!DNL Live Search]** > **店面特色** 並設定 **啟用產品清單Widget** 設為「否」。
1. 選取 **儲存設定** 以儲存設定。
