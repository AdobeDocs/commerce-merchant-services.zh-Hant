---
title: "Facets類型"
description: '"[!DNL Live Search] facets是動態的，並在相關時出現在「過濾器」(Filters)清單中。'
exl-id: 49fb7609-64b3-4ae8-928d-54c99032d919
source-git-commit: 995f528abc0011c6ae7c4c524982c301072ec2eb
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# 小平面類型

[!DNL Live Search] 使用各種小平面類型，它們出現在 *篩選器* 清單。 可用小平面清單會根據返回的產品進行更改。 以下特性會影響其呈現和行為：

* 固定小平面 — 最常用小平面可固定到清單頂部。 其餘小平面列於 *排序類型* 在被釘住的小平面後排序。
* 動態Facets — 可 [Adobe Sensei](https://www.adobe.com/sensei.html) 查找與產品集和查詢最相關的內容。 該計算考慮了整個目錄的屬性元資料，並在查詢時確定了查詢的最相關方面。
* 常用方面 — 搜索結果中最常出現的產品屬性。
* 價格方面 — 按價格範圍返回產品。 您可以在 [*設定*](settings.md) 頁籤。

查詢時， [!DNL Live Search] 以動態和常用小平面組生成搜索結果。

![Facets — 價格](assets/storefront-search-results-run-price.png)

## 店面和無頭選項

為 [!DNL Commerce] storefront由搜索適配器處理，該適配器路由請求並在storefront中呈現結果。 全部 [!DNL Commerce] storefront facets按字母順序與單選選項一起排序，而與分配給相應屬性的輸入類型無關。 在店面中可用的小平面根據當前主題進行呈現，並反映對分層導航的呈現所做的任何定制。

相反， [頭](https://developer.adobe.com/commerce/php/architecture/technical-vision/web-api/) 實現由API處理並支援其它選項。 無頭小平面可以按字母順序或按計數排序，並且可以具有單選選項或多選選項。

### 小平面標籤

對於 [!DNL Commerce] 商店，小面標籤由 [*屬性屬性*](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html)。 對於具有多個視圖的儲存，可以在 *管理標籤*。 對於無頭實現，從 [面向工作區](faceting-workspace.md)。

### 排序類型

為店面呈現的所有小平面按字母順序排序。 對於無頭實現，小平面可按字母順序或按計數排序。

| 排序類型 | 說明 |
|--- |--- |
| 字母 | 在店面 *篩選器* 按字母順序排列小平面。 |
| 計數 | （僅限無頭）對於無頭實現，小平面也可以按照在當前返回的產品集中每個小平面找到的值數進行排序。 |
