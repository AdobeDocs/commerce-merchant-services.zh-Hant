---
title: '[!DNL Catalog Service] 發行說明'
description: 的最新發行資訊 [!DNL Catalog Service] Adobe Commerce。
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
source-git-commit: bb557e130a7dbef96c625d65cbe191a4ccbe26d0
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# [!DNL Catalog Service] 發行說明

以下版本說明 [!DNL Catalog Service] 包括：

* ![新增](../assets/new.svg)  — 新功能
* ![修正](../assets/fix.svg)  — 修正和改良
* ![錯誤](../assets/bug.svg)  — 已知問題

## 1.0版

發行日期：2022-10-04與Adobe Commerce(EE)相容：2.4.x與Adobe Commerce for Cloud(ECE)相容：2.4.x穩定性：正式發行

![新增](../assets/new.svg)  — 現在支援捆綁和分組產品。
![新增](../assets/new.svg)  — 新增B2B可見性覆寫。 產品現在可供搜尋，並可針對特定客戶群組新增至購物車。
![修正](../assets/fix.svg)  — 服務現在更穩定，效能也有所提高。

### 已知限制

尚不支援下列功能：

* 分層定價
* 從目錄中刪除變體時，不會收到更新
* 動態屬性有效負載的最大大小為&lt;9MB
* 捆綁產品的固定價格
* 分組產品的總價
* 支援虛擬、可下載和禮品卡產品類型
* 最低廣告價格(MAP)

## 0.3版 — 測試版+

發行日期：2022-09-12與Adobe Commerce(EE)相容：2.4.x與Adobe Commerce for Cloud(ECE)相容：2.4.x穩定性：Beta

![新增](../assets/new.svg)  — 支援變體的影像：系統會根據選取的選項傳回產品影像
![新增](../assets/new.svg)  — 價格支援的角色：僅允許特定客戶群組的成員查看產品價格
![修正](../assets/fix.svg)  — 提高服務的穩定性和效能
![新增](../assets/new.svg)  — 從目錄中刪除產品時收到更新

### 已知限制

尚不支援下列功能：

* 分層定價
* 捆綁包和分組產品
* 從目錄中刪除變體時，不會收到任何更新
* B2B可見性覆蓋：產品可供搜尋，或新增至購物車供特定客戶群組使用

## 測試版

發行日期：2022-08-09與Adobe Commerce(EE)相容：2.4.x與Adobe Commerce for Cloud(ECE)相容：2.4.x穩定性：Beta

* ![新增](../assets/new.svg) - `products` 和 `refineProduct` 查詢會傳回下列資料：
* 預先定義（系統）產品屬性。
* 動態產品屬性，並依角色篩選（產品顯示頁面/產品清單頁面）。
* 產品選項。
* 產品影像並依角色(PDP/PLP)篩選。
* 簡單產品的特定價格和可配置產品的價格範圍。
* 客戶群組價格和價格範圍。 在沒有客戶群組的購物者，系統會傳回後援的預設價格。
* 使用B2B客戶專屬定價的產品類型。

### 已知限制

* 不支援捆綁和分組的產品。
* 不支援分層定價。
* 在影像陣列中，只有第一個影像包含角色。
* 不會擷取變體的影像。
* 從目錄中刪除產品或變體時，不會收到更新。
