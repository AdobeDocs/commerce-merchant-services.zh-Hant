---
title: '"Faceting Workspace"'
description: 「學學如何 [!DNL Live Search] 「」
exl-id: b47b5c19-59bb-41e4-9599-3b90cbc44b70
source-git-commit: bffbede99865e9085f60392e474065a454446370
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---

# Faceting工作區

的 [!DNL Live Search] 工作區列出了當前可用的所有小平面，並提供了對設定和管理小平面所需工具的訪問權限。 固定小平面首先出現在現有小平面清單中，然後是動態小平面。 可以篩選清單以顯示所有小平面，或僅顯示已固定或動態的小平面。

![Faceting工作區](assets/faceting-workspace.png)

## 設定範圍

如果您的Adobe Commerce安裝包含多個商店視圖，請設定 **範圍** 到 [商店視圖](https://docs.magento.com/user-guide/configuration/scope.html) 應用方面設定。

## 篩選清單

1. 按一下 **篩選依據** 控制項。
1. 選擇以下選項之一：

   * 所有篩選器
   * 已固定
   * 動態

   ![Faceting工作區](assets/facets-filter-by.png)

## 添加方面

1. 按一下 **添加小平面**。
1. 請參閱 [添加小平面](facets-add.md) 的上界。

## 列說明

| 列 | 說明 |
|--- |--- |
| （第一列） | 列出被固定的小平面和動態小平面 [標籤](facets-type.md) 對購物者來說是可見的。 |
| 選擇類型 | 的 [選擇方法](facets-type.md) 分配給相應產品屬性的。 的 `single select` 類型用於所有 [!DNL Commerce] 店面。 對於無頭實施， `multi-select` 類型可以用邏輯運算子(`or` 或 `and`)以確定返回的產品集。 |
| 排序類型 | 的 [排序順序](facets-type.md) 方面值。 小平面按字母順序排序 [!DNL Commerce] 店面。 對於 [頭] 實現中，facet可按字母順序或按計數排序。 選項：按字母順序排列，計數（僅限無頭） |
| 最大值 | 在儲存面中作為篩選器可用的多面值數，最多為10。 |

## 控制項

| 控制項 | 說明 |
|--- |--- |
| 添加小平面 | 開啟 [刻面編輯器](facets-add.md)。 |
| 篩選依據 | 確定 [小平面類型](facets-type.md) 清單中的。 選項：全部，固定，動態 |
