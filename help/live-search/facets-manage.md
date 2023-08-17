---
title: 「管理Facet」
description: 「瞭解如何管理現有的 [!DNL Live Search] 多面向。」
exl-id: 1d51a36a-20d6-46b6-b379-11e46c8824a0
source-git-commit: bce69f952e70e2e8dcb892357dea41e18f61e5f6
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# 管理Facet

請依照這些指示更新現有Facet的屬性，或在店面中變更其簡報。

## 設定價格面向群組

請參閱 [設定](settings.md) 設定價格多面區間與群組。

## 編輯Facet

1. 尋找您要編輯的Facet。
1. 如果清單中有許多面向，請設定 *篩選依據* 變更為下列其中一項：

   * 已固定
   * 動態

   若要進一步瞭解，請前往 [Facet型別](facets-type.md).

   ![篩選Facet](assets/facets-filter-by-cropped.png)

1. 若要編輯多面屬性，請按一下 **更多** (...)選項。
1. 按一下 **編輯**

   ![編輯選項](assets/facet-edit-menu.png)

1. 若要編輯多面標籤，請執行下列任一項作業：

   * 針對 [!DNL Commerce] 店面，編輯 [屬性標籤](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html).
   * 對於Headless實作，請按一下第一欄中的值，然後視需要編輯文字。

   ![編輯標籤](assets/facet-edit-label.png)

1. （僅限Headless）若要變更用於排序多面值的方法，請按一下 *排序型別* 欄，並選擇下列其中一項：

   * 字母順序
   * 計數

   ![編輯計數](assets/facets-edit-count.png)

1. 在 **最大值** 欄，設定在店面中顯示的Facet篩選值數目上限（從0到10）。
1. 完成後，按一下 **儲存**.
您的變更要等到發佈後才顯示在店面上。

## 釘選/取消釘選面向

圖釘在按一下時會改變顏色，可用來將多面移動到 *釘選多面向* 或 *動態Facet* 區段。

1. 將多面釘選至頂端 *篩選器* 清單，在 *動態Facet* 清單並按一下灰色圖釘(![圖釘選擇器](assets/btn-pin-gray.png))。
圖釘會變成藍色，而多面會移至 *釘選多面向* 區段。
1. 若要取消釘選多面，請在 *釘選多面向* 清單並按一下藍色圖釘(![圖釘選擇器](assets/btn-pin-blue.png))。
圖釘會變成灰色，而多面會移至 *動態Facet* 區段。

   ![釘選和動態Facet](assets/facets-pinned-unpinned.png)

>[!NOTE]
>
>如果有兩個標籤具有相同名稱，則釘選Facet排序可能會不一致。

## 移動釘選Facet

>[!NOTE]
>
>釘選Facet的排序僅在Headless實施中受支援。 如果需要排序的多面，請使用 [!DNL Live Search] PLP Widget.

將列移至不同位置可變更釘選多面的順序。 釘選多面向具有 *移動* 圖示(![移動選擇器](assets/btn-move.png))中所有規則的URL。 與釘選多面不同，動態Facet無法移動。

1. 尋找Facet於 *釘選多面向* 區段。
1. 使用 **移動** (![移動選擇器](assets/btn-move.png))圖示將列拖曳至中的新位置 *釘選多面向* 區段。
發佈變更後，重新排序的Facet會出現在店面上 *篩選器* 清單。

## 刪除Facet

1. 在清單中尋找多面並按一下 **更多** (...)選項。
1. 按一下 **刪除**.
1. 提示確認時，按一下 **刪除Facet**.
多面在變更發佈後會從店面中移除。

## 發佈變更

1. 若要以您的變更更新店面，請按一下 **發佈變更**.
1. 請等候約15分鐘，讓更新出現在您的商店中。
