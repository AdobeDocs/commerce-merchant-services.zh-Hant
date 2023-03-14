---
title: "添加Facet"
description: 「了解如何將可篩選的產品屬性新增為 [!DNL Live Search] 刻面」
exl-id: 0df6c21b-55b3-41ce-94f4-f70b70ffb84e
source-git-commit: 10edbb6127405d45c06d4c8ffc89d92a6ca061c3
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 0%

---

# 新增Facet

任何可篩選的產品屬性都可作為Facet使用。 此 *新增Facet* 面板會列出目前的facet，並可輕鬆將其他產品屬性指派為facet。 在這三個步驟的過程中，會選擇屬性作為面向，並視需要編輯屬性，並將變更發佈到店面。

![Faceting工作區](assets/facets-add.png)

## 步驟1:新增Facet

1. 在管理員中，前往 **行銷** > SEO與搜尋> **[!DNL Live Search]**.
1. 在 *Faceting* 按一下 **新增Facet**.
1. 在 *新增Facet* 清單中，每個可用屬性都有單獨的 ![添加按鈕](assets/btn-add.png). 完成下列任一項：

   * 在 *Facet屬性* ，選擇您要用作小面的產品屬性，然後按一下 **新增**.
   * 若要尋找特定產品屬性，請在 *搜尋* 框。 然後，按一下 **新增**.

      若要設定價格對應間隔和分組，請參閱 [設定](settings.md). 若要進一步了解，請前往 [小平面類型](facets-type.md).
小面會新增至 *動態Facet* 清單和 *發佈變更* 按鈕可用。

1. 如果找不到要新增的面，請前往 **商店** >屬性> **產品** 並確認屬性具有 [必要屬性](facets.md) 可用作小面。 如有必要，請更新屬性的以下店面屬性：

   * 用於搜尋 —  `Yes`
   * 用於搜索結果分層導航 —  `Yes`
   * 用於分層導航 —  `Filterable (with results)`

1. 出現提示時，刷新快取。

   下次同步目錄時，該面向便可在店面中使用 [!DNL Live Search]. 如果刻面在兩小時後無法使用，請參閱 [同步目錄資料](install.md#synchronize-catalog-data).

## 步驟2:編輯Facet屬性（可選）

1. 要編輯小面屬性，請按一下 **更多** (![更多選取器](assets/btn-more.png))選項。
1. 在功能表上，按一下 **編輯**. 接著，視需要調整下列屬性。

   * 標籤 — ([無頭](facets-type.md) 僅)輸入您要使用的Facet標籤。
   * 排序類型 — Facet按字母順序排列 [!DNL Commerce] 店面。 對於無頭式實作，Facet可依字母順序或依計數排序。 選項：字母順序，計數（僅限無頭）
   * 最大值 — 輸入店面中顯示的最大刻面值數。 有效條目：0-30;預設值：8

1. 完成後，按一下 **儲存**.

   ![Faceting工作區](assets/facet-edit.png)

1. 將小面固定到 *篩選器* 清單，按一下灰色圖釘(![管腳選擇器](assets/btn-pin-gray.png))。
1. 要更改固定小面的順序，請按一下 **移動** (![移動選擇器](assets/btn-move.png))圖示，並將列拖曳至 *固定的刻面* 區段。

## 步驟3:發佈變更

1. 當小面完成時，按一下 **發佈變更**.
1. 等待Facet出現在商店中。
如果刻面在兩小時後無法使用，請參閱 [驗證導出](install.md#synchronize-catalog-data) 中。

## 欄位說明

| 欄位 | 說明 |
|--- |--- |
| 標籤 | ([無頭](facets-type.md) 僅限) [刻面標籤](facets-type.md) 可編輯顯示於店面的內容，以符合您的品牌。 |
| 排序類型 | 用於 [排序](facets-type.md) 刻面。 全部 [!DNL Commerce] 店面只按字母順序排列小平面。 無頭式實作也可依 `Count`. 選項：<br />按字母排序 — 按字母排序刻面。<br />計數 — （僅限無頭）根據找到的匹配數對刻面進行排序。 |
| 最大值 | 每個面向可顯示於店面的值數上限。 代表值範圍的刻面會平均分配。 有效條目：0-30;預設值：8 |

### 控制項

| 控制 | 說明 |
|--- |--- |
| ![管腳選擇器](assets/btn-pin-blue.png) | 將小面插入或取消插入 *篩選器* 清單。 |
| ![更多選取器](assets/btn-more.png) | 顯示可套用至選取小面的更多動作功能表。 選項：編輯、刪除 |
| ![移動選擇器](assets/btn-move.png) | 使用 *移動* 表徵圖將固定小平面拖到 *固定的刻面* 區段。 |
