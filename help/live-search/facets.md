---
title: "Facets"
description: '"[!DNL Live Search] facet使用屬性值的多個維作為搜索標準。」'
exl-id: 63c0b255-6be9-41ad-b4bf-13bb7ff098fd
source-git-commit: 9bacdb5fd232a3603bcb7abe2e93da9ead794d38
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# Facet

Faceting是高效能篩選的方法，使用多個屬性值維度作為搜尋准則。 多面搜索類似，但比標準「更聰明」 [分層導航](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-layered.html). 可用篩選器清單由 [可篩選屬性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-layered.html#filterable-attributes) 搜尋結果中傳回的產品。

![篩選的搜尋結果](assets/storefront-search-results-run.png)

## Facet需求

面向的類別和產品屬性要求類似於用於分層導航的可篩選屬性。 每個屬性的店面屬性必須設定為 `filterable (with results)`.

[!DNL Live Search] 最多支援：

* 100個屬性設定為Facet
* 50個可排序屬性
* 200個可篩選屬性
* 200個可搜索屬性

| 設定 | 說明 |
|--- |--- |
| [類別顯示設定](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/create/categories-display-settings.html) | 錨點 —  `Yes` |
| [屬性屬性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html) | [目錄輸入類型](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/attributes-input-types.html) - `Yes/No`, `Dropdown`, `Multiple Select`, `Price`, `Visual swatch` （僅限介面工具集）, `Text swatch` （僅限widget） |
| 屬性店面屬性 | 用於搜索結果分層導航 —  `Yes` |

## 預設屬性值

下列產品屬性具有 [店面屬性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) 用於 [!DNL Live Search] 和預設啟用。

| 屬性 | Storefront屬性 | 屬性 |
|---|---|---|
| 可排序 | 用於排序產品清單 | `price` |
| 可搜尋 | 在搜尋中使用 | `price` <br />`sku`<br />`name` |
| FilterableInSearch | 在分層導覽中使用 — 可篩選（含結果） | `price`<br />`visibility`<br />`category_name` |

## 預設非系統屬性

下表顯示非系統屬性的預設搜索和可篩選屬性，包括特定於Luma示例資料的屬性。 設定 *在搜尋中使用* 屬性屬性 `Yes` 讓屬性可在兩者中搜尋 [!DNL Live Search] 和原生Adobe Commerce。

| 屬性代碼 | 可搜尋 | 用於分層導航 |
|--- |--- |--- |
| 活動 | 是 | 可篩選（含結果） |
| attributes_brand | 是 | 否 |
| 品牌 | 是 | 否 |
| 氣候 | 是 | 可篩選（含結果） |
| 領口 | 是 | 可篩選（含結果） |
| 色彩 | 是 | 可篩選（含結果） |
| 成本 | 是 | 否 |
| eco_collection | 是 | 可篩選（含結果） |
| 性別 | 是 | 可篩選（含結果） |
| 製造商 | 是 | 可篩選（含結果） |
| 材料 | 是 | 可篩選（含結果） |
| 用途 | 是 | 可篩選（含結果） |
| strap_bags | 是 | 可篩選（含結果） |
| style_general | 是 | 可篩選（含結果） |

## 預設系統屬性

下表顯示系統屬性的預設搜索和可篩選屬性。

| 屬性代碼 | 可搜尋 | 用於分層導航 |
|--- |--- |--- |
| allow_open_amount | 是 | 可篩選（含結果） |
| 說明 | 是 | 否 |
| 名稱 | 是 | 否 |
| 價格 | 是 | 可篩選（含結果） |
| short_description | 是 | 否 |
| sku | 是 | 否 |
| 狀態 | 是 | 否 |
| tax_class_id | 是 | 否 |
| url_key | 是 | 否 |
| 權重 | 是 | 否 |
