---
title: 「多面向工作區」
description: 「瞭解您如何周遊 [!DNL Live Search] 多面向工作區。」
exl-id: b47b5c19-59bb-41e4-9599-3b90cbc44b70
source-git-commit: 4978bdb5549f5df911863a23fdfbfc9ab9ad05df
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---

# 多面向工作區

此 *多面向* 工作區會列出目前可用的所有Facet，並可讓您存取設定和管理Facet所需的工具。 釘選多面會先出現在現有多面的清單中，然後是動態多面。 您可以篩選清單以顯示所有多面，或僅顯示已釘選或動態的多面。

![多面向工作區](assets/faceting-workspace.png)

## 設定範圍

如果您的Adobe Commerce安裝包含多個商店檢視，請設定 **範圍** 至 [存放區檢視](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) 您的Facet設定套用的位置。

## 篩選清單

1. 按一下 **篩選依據** 控制。
1. 選擇下列其中一個選項：

   * 所有篩選器
   * 已固定
   * 動態

## 新增面向

1. 按一下 **新增多面向**.
1. 另請參閱 [新增Facet](facets-add.md) 以取得詳細指示。

## 欄說明

| 欄 | 說明 |
|--- |--- |
| （第一欄） | 列出釘選和動態Facet，依據 [標籤](facets-type.md) 購物者看得見的其他內容。 |
| 排序型別 | 此 [排序順序](facets-type.md) 的Facet值。 Facet會依字母順序排序所有 [!DNL Commerce] 店面。 的 [headless] 實作，Facet可依字母順序或計數排序。 選項：字母順序、計數（僅限Headless） |
| 最大值 | 店面中作為篩選器可用的多面值數量（最多10個）。 |

## 控制項

| 控制 | 說明 |
|--- |--- |
| 新增多面向 | 開啟 [Facet編輯器](facets-add.md). |
| 篩選依據 | 決定 [Facet型別](facets-type.md) 會出現在清單中。 選項：全部、固定、動態 |
