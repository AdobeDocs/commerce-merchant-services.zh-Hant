---
title: "Faceting Workspace"
description: 「學習如何 [!DNL Live Search] faceting workspace。」
exl-id: b47b5c19-59bb-41e4-9599-3b90cbc44b70
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Facet Workspace

此 [!DNL Live Search] 工作區會列出目前可用的所有Facet，並可存取設定和管理Facet所需的工具。 固定的Facet會先出現在現有Facet的清單中，接著是動態Facet。 您可以篩選清單，以顯示所有刻面，或僅顯示已固定或動態的刻面。

![Faceting工作區](assets/faceting-workspace.png)

## 設定範圍

若您的Adobe Commerce安裝包含多個商店檢視，請設定 **範圍** 到 [商店檢視](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) 的Facet設定。

## 篩選清單

1. 按一下 **篩選依據** 控制。
1. 選擇以下選項之一：

   * 所有篩選器
   * 固定
   * 動態

   ![Faceting工作區](assets/facets-filter-by.png)

## 新增Facet

1. 按一下 **新增Facet**.
1. 請參閱 [新增Facet](facets-add.md) 以取得詳細指示。

## 欄說明

| 欄 | 說明 |
|--- |--- |
| （第一欄） | 列出已固定和動態Facet，由 [標籤](facets-type.md) 供購物者檢視。 |
| 選擇類型 | 此 [選擇方法](facets-type.md) 會指派給對應的產品屬性。 此 `single select` 「類型」(type)用於所有 [!DNL Commerce] 店面。 對於無頭式實作， `multi-select` 類型可以用邏輯運算子(`or` 或 `and`)，以判斷傳回的產品集。 |
| 排序類型 | 此 [排序順序](facets-type.md) 小平面值。 Facet按字母順序排列 [!DNL Commerce] 店面。 針對 [無頭] 實作中，Facet可依字母順序或依計數排序。 選項：字母順序，計數（僅限無頭） |
| 最大值 | 在店面中以篩選形式提供的小面值數目，最多10個。 |

## 控制項

| 控制 | 說明 |
|--- |--- |
| 新增Facet | 開啟 [刻面編輯器](facets-add.md). |
| 篩選依據 | 決定 [刻面類型](facets-type.md) 清單中顯示的。 選項：全部，固定，動態 |
