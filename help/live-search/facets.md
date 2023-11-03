---
title: "Facet"
description: '"[!DNL Live Search] 多面向使用屬性值的多個維度作為搜尋條件。」'
exl-id: 63c0b255-6be9-41ad-b4bf-13bb7ff098fd
source-git-commit: 8bac6f053cddd3d47c3aa279abf7c96c79ffcd81
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# Facet

多面向是一種高效能篩選方法，使用多個屬性值的維度作為搜尋條件。 多面向搜尋類似，但比標準要「聰明」得多 [分層導覽](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-layered.html). 可用篩選器的清單由 [可篩選屬性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-layered.html#filterable-attributes) 搜尋結果中傳回的產品數量。

[!DNL Live Search] 使用 `productSearch` 查詢，會傳回多面向及其他特定資料 [!DNL Live Search]. 請參閱 [`productSearch` 查詢](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/) 在開發人員檔案中取得程式碼範例。

![篩選的搜尋結果](assets/storefront-search-results-run.png)

任何已定義的Facet都可以用作URL引數，而且會根據引數值篩選結果： `http://yourstore.com?brand=acme&color=red`.

## 多面向需求

多面的類別和產品屬性需求類似於用於分層導覽的可篩選屬性。 每個屬性的店面屬性都必須設為 `filterable (with results)`.

[!DNL Live Search] 最多支援：

* 100個已設定為Facet的屬性
* 50個可排序屬性
* 200個可篩選屬性
* 200個可搜尋屬性

| 設定 | 說明 |
|--- |--- |
| [類別顯示設定](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/create/categories-display-settings.html) | 錨點 —  `Yes` |
| [屬性屬性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html) | [目錄輸入型別](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/attributes-input-types.html) - `Yes/No`， `Dropdown`， `Multiple Select`， `Price`， `Visual swatch` （僅限Widget）， `Text swatch` （僅限Widget） |
| 屬性店面屬性 | 用於搜尋結果階層導覽 —  `Yes` |

## Facet彙總

多面向聚總的執行方式如下：如果店面有三個Facet （類別、顏色和價格），且購物者會篩選所有三個(顏色=藍色，價格為$10.00-50.00，類別= `promotions`)。

* `categories` 彙總 — 彙總 `categories`，然後套用 `color` 和 `price` 篩選器，但不適用於 `categories` 篩選。
* `color` 彙總 — 彙總 `color`，然後套用`price` 和 `categories` 篩選器，但不適用於 `color` 篩選。
* `price` 彙總 — 彙總 `price`，然後套用 `color` 和 `categories` 篩選器，但不適用於 `price` 篩選。

## 預設屬性值

下列產品屬性具有 [店面屬性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) 使用者 [!DNL Live Search] 預設為啟用。

| 屬性 | 店面屬性 | 屬性 |
|---|---|---|
| 可排序 | 用於產品清單中的排序 | `price` |
| 可搜尋 | 用於搜尋 | `price` <br />`sku`<br />`name` |
| FilterableInSearch | 用於分層導覽 — 可篩選（含結果） | `price`<br />`visibility`<br />`category_name` |

## 預設非系統屬性屬性

下表顯示非系統屬性的預設搜尋和可篩選屬性，包括特定於Luma範例資料的屬性。 設定 *用於搜尋* 屬性屬性至 `Yes` 讓屬性可於兩者中搜尋 [!DNL Live Search] 和原生Adobe Commerce。

| 屬性代碼 | 可搜尋 | 用於分層導覽 |
|--- |--- |--- |
| 活動 | 是 | 可篩選（包含結果） |
| attributes_brand | 是 | 否 |
| 品牌 | 是 | 否 |
| 氣候 | 是 | 可篩選（包含結果） |
| 項圈 | 是 | 可篩選（包含結果） |
| 顏色 | 是 | 可篩選（包含結果） |
| 成本 | 是 | 否 |
| eco_collection | 是 | 可篩選（包含結果） |
| 性別 | 是 | 可篩選（包含結果） |
| 製造商 | 是 | 可篩選（包含結果） |
| 材質 | 是 | 可篩選（包含結果） |
| 用途 | 是 | 可篩選（包含結果） |
| strap_bag | 是 | 可篩選（包含結果） |
| style_general | 是 | 可篩選（包含結果） |

## 預設系統屬性屬性

下表顯示系統屬性的預設搜尋和可篩選特性。

| 屬性代碼 | 可搜尋 | 用於分層導覽 |
|--- |--- |--- |
| allow_open_amou | 是 | 可篩選（包含結果） |
| 說明 | 是 | 否 |
| 名稱 | 是 | 否 |
| 價格 | 是 | 可篩選（包含結果） |
| short_description | 是 | 否 |
| sku | 是 | 否 |
| 狀態 | 是 | 否 |
| tax_class_id | 是 | 否 |
| url_key | 是 | 否 |
| 權重 | 是 | 否 |
