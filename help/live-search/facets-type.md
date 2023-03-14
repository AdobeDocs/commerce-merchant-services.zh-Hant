---
title: "Facet類型"
description: '"[!DNL Live Search] Facet是動態的，並在相關時顯示在「篩選器」清單中。'
exl-id: 49fb7609-64b3-4ae8-928d-54c99032d919
source-git-commit: 995f528abc0011c6ae7c4c524982c301072ec2eb
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# 刻面類型

[!DNL Live Search] 會使用各種facet類型，且會顯示在 *篩選器* 僅在相關時列出。 可用Facet的清單會根據傳回的產品而變更。 下列特性會影響其呈現方式和行為：

* 固定的刻面 — 最常使用的刻面可固定到清單的頂部。 其餘多面體列於 *排序類型* 在固定刻面之後排序。
* 動態Facet — 可 [Adobe Sensei](https://www.adobe.com/sensei.html) 查找與產品集和查詢最相關的資訊。 計算會考慮整個目錄的屬性元資料，並在查詢時確定查詢的最相關面。
* 熱門面向 — 搜尋結果中最常出現的產品屬性。
* 價格面 — 按價格範圍返回產品。 您可以在 [*設定*](settings.md) 標籤。

查詢時， [!DNL Live Search] 會以動態和常用刻面群組產生搜尋結果。

![Facet — 價格](assets/storefront-search-results-run-price.png)

## 店面和無頭選項

為 [!DNL Commerce] storefront由搜索適配器處理，該適配器將路由請求並在storefront中呈現結果。 全部 [!DNL Commerce] 無論指派給對應屬性的輸入類型為何，店面刻面都會以單選選項的字母順序排序。 店面中可用的刻面會根據目前主題呈現，並反映針對分層導覽的呈現方式所做的任何自訂。

相反， [無頭](https://developer.adobe.com/commerce/php/architecture/technical-vision/web-api/) 實作由API處理，並支援其他選項。 無頭刻面可以按字母順序或按計數排序，並可以有單選或多選選項。

### Facet標籤

針對 [!DNL Commerce] 商店，小面標籤由 [*屬性屬性*](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html). 若是具有多個檢視的商店，可在 *管理標籤*. 對於無頭實作，標籤會從 [Facet Workspace](faceting-workspace.md).

### 排序類型

為店面呈現的所有面向按字母順序排序。 對於無頭式實作，Facet可依字母順序或依計數排序。

| 排序類型 | 說明 |
|--- |--- |
| 字母 | 在店面 *篩選器* 清單，Facet按字母順序排序。 |
| 計數 | （僅限無頭）對於無頭實作，Facet也可依目前傳回產品集中每個Facet找到的值數目排序。 |
