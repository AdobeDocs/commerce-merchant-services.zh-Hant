---
title: "新增Facet"
description: 「瞭解如何將可篩選的產品屬性新增為 [!DNL Live Search] 多面向。」
exl-id: 0df6c21b-55b3-41ce-94f4-f70b70ffb84e
source-git-commit: 4978bdb5549f5df911863a23fdfbfc9ab9ad05df
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 0%

---

# 新增Facet

任何可篩選的產品屬性都可以當作Facet使用。 此 *新增多面向* 面板會列出目前的多面，並可讓您輕鬆將其他產品屬性指派為Facet。 在這三個步驟的流程中，選擇屬性作為多面，視需要編輯屬性，並將變更發佈到店面。

![新增Facet](assets/facets-add.png)

## 步驟1：新增多面向

1. 在Admin中，前往 **行銷** > SEO與搜尋> **[!DNL Live Search]**.
1. 在 *多面向* 標籤，按一下 **新增多面向**.
1. 在 *新增多面向* 清單，每個可用屬性都有個別的 ![新增按鈕](assets/btn-add.png). 完成下列任一項作業：

   * 在 *多面向屬性* 清單，選擇要用作Facet的產品屬性，然後按一下 **新增**.
   * 若要尋找特定的產品屬性，請在 *搜尋* 方塊。 然後，按一下 **新增**.

     若要設定價格多面向間隔與群組，請參閱 [設定](settings.md). 若要進一步瞭解，請前往 [Facet型別](facets-type.md).
多面會新增至 *動態Facet* 清單與 *發佈變更* 按鈕變為可用。

1. 如果找不到您要新增的Facet，請移至 **商店** >屬性> **產品** 並確認屬性具有 [必要屬性](facets.md) 用作Facet。 如有必要，請更新屬性的下列店面屬性：

   * 用於搜尋 —  `Yes`
   * 用於搜尋結果階層導覽 —  `Yes`
   * 用於分層導覽 —  `Filterable (with results)`

1. 出現提示時，請重新整理快取。

   下次與目錄同步時，多面即可在店面中使用 [!DNL Live Search]. 如果Facet在兩小時後無法使用，請參閱 [同步目錄資料](install.md#synchronize-catalog-data).

## 步驟2：編輯Facet屬性（選用）

1. 若要編輯多面屬性，請按一下 **更多** (![更多選擇器](assets/btn-more.png))選項。
1. 在功能表上，按一下 **編輯**. 接著，視需要調整下列屬性。

   * 標籤 — ([Headless](facets-type.md) 僅限)輸入您要使用的Facet標籤。
   * 排序型別 — Facet會依字母順序排序 [!DNL Commerce] 店面。 針對Headless實作，Facet可依字母順序或計數排序。 選項：字母順序、計數（僅限Headless）
   * 最大值 — 輸入店面中顯示的多面值數目上限。 有效專案： 0 - 30；預設： 8

1. 完成後，按一下 **儲存**.

   ![編輯Facet](assets/facet-edit.png)

1. 若要將多面釘選至頂端 *篩選器* 清單，按一下灰色圖釘(![圖釘選擇器](assets/btn-pin-gray.png))。
1. 若要變更釘選多面的順序，請按一下 **移動** (![移動選擇器](assets/btn-move.png))圖示並將列拖曳到 *釘選多面向* 區段。

## 步驟3：發佈變更

1. 多面完成後，按一下 **發佈變更**.
1. 等候多面向出現在存放區中。
如果Facet在兩小時後無法使用，請參閱 [驗證匯出](install.md#synchronize-catalog-data) 安裝指示中。

## 欄位說明

| 欄位 | 說明 |
|--- |--- |
| 標籤 | ([Headless](facets-type.md) 僅限) [Facet標籤](facets-type.md) 可編輯店面中顯示的內容，以與您的品牌保持一致。 |
| 排序型別 | 使用於下列專案的方法： [sort](facets-type.md) 多面向。 全部 [!DNL Commerce] 店面僅依字母順序排序Facet。 Headless實作也可以依據 `Count`. 選項：<br />依字母順序 — 依字母順序排序多面向。<br />計數 — （僅限Headless）根據找到的相符專案數來排序Facet。 |
| 最大值 | 可在店面中針對每個多面顯示的最大值數量。 代表值範圍的多面會平均分佈。 有效專案： 0 - 30；預設： 8 |

### 控制項

| 控制 | 說明 |
|--- |--- |
| ![圖釘選擇器](assets/btn-pin-blue.png) | 將多面釘選或取消釘選至頂端 *篩選器* 清單。 |
| ![更多選擇器](assets/btn-more.png) | 顯示可套用至所選Facet的其他動作功能表。 選項：編輯、刪除 |
| ![移動選擇器](assets/btn-move.png) | 使用 *移動* 圖示將釘選多面拖曳至 *釘選Facet* 區段。 |
