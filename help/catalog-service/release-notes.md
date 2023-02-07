---
title: '[!DNL Catalog Service] 發行說明'
description: 的最新發行資訊 [!DNL Catalog Service] Adobe Commerce。
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
source-git-commit: 67f9e5ce69930f3298427a103f9160f925d2ae0d
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 0%

---

# [!DNL Catalog Service] 發行說明

以下版本說明 [!DNL Catalog Service] 包括：

* ![新增](../assets/new.svg) 新功能
* ![修正](../assets/fix.svg) 修正和改良
* ![錯誤](../assets/bug.svg) 已知問題

## 第1.4版

發行日期：2023-2-7與Adobe Commerce(EE)相容：2.4.x與Adobe Commerce for Cloud(ECE)相容：2.4.x穩定性：正式發行

![新增](../assets/new.svg) 發佈目錄服務元資料包以簡化安裝步驟。
![修正](../assets/fix.svg) API可擴充性和效能改善。


### 已知限制

尚不支援下列功能：

* 以固定價格捆綁產品
* 從目錄中刪除變體時，不會收到任何更新。
* 動態屬性有效負載的最大大小為9MB。
* 組產品價格。 可使用簡單的產品價格計算。
* 在影像陣列中，只有第一個影像包含角色。
* 色票
* 透過產品URL載入產品詳細資料頁面。

使用核心GraphQL API可解決下列限制：

* 最低廣告價格
* 分層定價
* 可下載的產品和禮品卡
* 類別(`categories` 和 `categoryList`)

## 第1.3版

發行日期：2023-1-17與Adobe Commerce(EE)相容：2.4.x與Adobe Commerce for Cloud(ECE)相容：2.4.x穩定性：正式發行

![新增](../assets/new.svg) 簡化並改善入門體驗。
![新增](../assets/new.svg) 生產前測試可使用新的客戶沙箱端點。
![新增](../assets/new.svg) 新增對虛擬產品的支援。
![修正](../assets/fix.svg) API可擴充性和效能改善。

### 已知限制

尚不支援下列功能：

* 以固定價格捆綁產品
* 從目錄中刪除變體時，不會收到任何更新。
* 動態屬性有效負載的最大大小為9MB。
* 組產品價格。 可使用簡單的產品價格計算。
* 在影像陣列中，只有第一個影像包含角色。
* 色票
* 透過產品URL載入產品詳細資料頁面。

使用核心GraphQL API可解決下列限制：

* 最低廣告價格
* 分層定價
* 可下載的產品和禮品卡
* 類別(`categories` 和 `categoryList`)

## 第1.1版

發行日期：2022-11-18與Adobe Commerce(EE)相容：2.4.x與Adobe Commerce for Cloud(ECE)相容：2.4.x穩定性：正式發行

![新增](../assets/new.svg) 目錄服務現在支援Adobe [API Mesh](https://developer.adobe.com/graphql-mesh-gateway/).
![修正](../assets/fix.svg) 我們已改善API的可擴充性和整體效能。

### 已知限制

尚不支援下列功能：

* 以固定價格捆綁產品
* 從目錄中刪除變體時，不會收到任何更新。
* 動態屬性有效負載的最大大小為9MB。
* 組產品價格。 可使用簡單的產品價格計算。
* 在影像陣列中，只有第一個影像包含角色。
* 色票
* 透過產品URL載入產品詳細資料頁面。

使用GraphQL API可解決下列限制：

* 最低廣告價格
* 分層定價
* 可下載的產品和禮品卡
* 類別(`categories` 和 `categoryList`)

## 1.0版

發行日期：2022-10-04與Adobe Commerce(EE)相容：2.4.x與Adobe Commerce for Cloud(ECE)相容：2.4.x穩定性：正式發行

![新增](../assets/new.svg) 現在支援捆綁和分組產品。
![新增](../assets/new.svg) 新增B2B可見性覆寫。 產品現在可供搜尋，並可針對特定客戶群組新增至購物車。
![修正](../assets/fix.svg) 服務現在更穩定，效能也有所提高。

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

![新增](../assets/new.svg) 變體支援的影像：系統會根據選取的選項傳回產品影像
![新增](../assets/new.svg) 價格支援的角色：僅允許特定客戶群組的成員查看產品價格
![修正](../assets/fix.svg) 提高服務的穩定性和效能
![新增](../assets/new.svg) 從目錄中刪除產品時，會收到更新

### 已知限制

尚不支援下列功能：

* 分層定價
* 捆綁包和分組產品
* 從目錄中刪除變體時，不會收到任何更新
* B2B可見性覆蓋：產品可供搜尋，或新增至購物車供特定客戶群組使用

## 測試版

發行日期：2022-08-09與Adobe Commerce(EE)相容：2.4.x與Adobe Commerce for Cloud(ECE)相容：2.4.x穩定性：Beta

![新增](../assets/new.svg) 此 `products` 和 `refineProduct` 查詢會傳回下列資料：

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
