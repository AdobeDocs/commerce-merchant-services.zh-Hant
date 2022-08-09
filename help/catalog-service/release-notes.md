---
title: '"[!DNL Catalog Service] 發行說明"'
description: '"最新發佈資訊 [!DNL Catalog Service] 為Adobe Commerce。」'
source-git-commit: 3959cc5d07f9a0da0ba772a4f3bc56adeb3c6bf3
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# [!DNL Catalog Service] 發行說明

{{catalog-service-beta}}

本發行說明描述 [!DNL Catalog Service] 包括：

* ![新建](../assets/new.svg)  — 新功能
* ![修復](../assets/fix.svg)  — 修復和改進
* ![蟲](../assets/bug.svg)  — 已知問題

## Beta版

* ![新建](../assets/new.svg) - `products` 和 `refineProduct` 查詢返回以下資料：
   * 預定義（系統）產品屬性。
   * 動態產品屬性並按角色篩選它們（產品顯示頁/產品清單頁）。
   * 產品選項。
   * 產品影像並按角色(PDP/PLP)過濾。
   * 簡單產品的特定價格和可配置產品的價格範圍。
   * 客戶組價格和價格範圍。 它們會向沒有客戶群的購物者退回備用違約價格。
   * 使用B2B客戶特定定價的產品類型。

## 已知限制

* 不支援層定價。
* 在映像陣列中，只有第一個映像包含角色。
* 不檢索變型的影像。
* 當從目錄中刪除產品或變型時，不會接收更新。
