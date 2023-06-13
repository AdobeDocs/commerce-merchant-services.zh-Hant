---
title: 「管理Facet」
description: 「瞭解如何管理現有 [!DNL Live Search] 多面向。」
exl-id: 1d51a36a-20d6-46b6-b379-11e46c8824a0
source-git-commit: bce69f952e70e2e8dcb892357dea41e18f61e5f6
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# 管理Facet

請依照這些指示更新現有Facet的屬性，或變更其在店面中的呈現方式。

## 設定價格方面群組

請參閱 [設定](settings.md) 若要設定價格多面向間隔與群組，請執行下列步驟：

## 編輯facet

1. 尋找您要編輯的Facet。
1. 如果清單中有許多面向，請設定 *篩選依據* 變更為下列其中一項：

   * 已釘選
   * 動態

   若要深入瞭解，請前往 [Facet型別](facets-type.md).

   ![篩選Facet](assets/facets-filter-by-cropped.png)

1. 若要編輯多面屬性，請按一下 **更多** (...)選項。
1. 按一下 **編輯**

   ![編輯選項](assets/facet-edit-menu.png)

1. 若要編輯Facet標籤，請執行下列任一項動作：

   * 對於 [!DNL Commerce] 店面，編輯 [屬性標籤](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html).
   * 針對Headless實作，請按一下第一欄中的值，然後視需要編輯文字。

   ![編輯標籤](assets/facet-edit-label.png)

1. （僅限Headless）若要變更用於排序Facet值的方法，請按一下 *排序型別* 欄並選擇下列其中一項：

   * 按字母順序
   * 計數

   ![編輯計數](assets/facets-edit-count.png)

1. 在 **最大值** 欄，設定在店面中顯示的多面篩選值數目上限（從0到10）。
1. 完成後，按一下 **儲存**.
您的變更要等到發佈後才顯示在店面上。

## 釘選/取消釘選面向

圖釘在按一下時會改變顏色，並可用來將多面移動到 *釘選Facet* 或 *動態Facet* 區段。

1. 將多面釘選到頂端 *篩選器* 清單中，尋找 *動態Facet* 清單並按一下灰色圖釘(![圖釘選擇器](assets/btn-pin-gray.png))。
圖釘會變成藍色，而多面會移至 *釘選Facet* 區段。
1. 若要取消釘選多面，請在 *釘選Facet* 清單並按一下藍色圖釘(![圖釘選擇器](assets/btn-pin-blue.png))。
圖釘會變成灰色，而多面會移至 *動態Facet* 區段。

   ![釘選和動態Facet](assets/facets-pinned-unpinned.png)

>[!NOTE]
>
>如果有兩個同名的標籤，釘選Facet順序可能會不一致。

## 移動釘選面向

>[!NOTE]
>
>釘選Facet的排序僅在Headless實作中受支援。 如果需要排序的Facet，請使用 [!DNL Live Search] PLP Widget.

將列移動到不同位置可以變更釘選多面的順序。 釘選Facet具有 *移動* 圖示(![移動選擇器](assets/btn-move.png))開頭的「 」。 與釘選Facet不同，動態Facet無法移動。

1. 在中尋找面向 *釘選Facet* 區段。
1. 使用 **移動** (![移動選擇器](assets/btn-move.png))圖示以將列拖曳至中的新位置 *釘選Facet* 區段。
發佈變更後，重新排序的Facet會出現在店面 *篩選器* 清單。

## 刪除面向

1. 在清單中尋找Facet並按一下 **更多** (...)選項。
1. 按一下 **刪除**.
1. 提示確認時，按一下 **刪除面向**.
變更發佈後，Facet會從店面中移除。

## 發佈變更

1. 若要使用您的變更更新店面，請按一下 **發佈變更**.
1. 請等候約15分鐘，讓更新出現在您的商店中。
