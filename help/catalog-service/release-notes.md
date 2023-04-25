---
title: '[!DNL Catalog Service] 發行說明'
description: 的最新發行資訊 [!DNL Catalog Service] Adobe Commerce。
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
source-git-commit: f310f840e286859070002ab0e23eda3787c89f36
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# [!DNL Catalog Service] 發行說明

以下版本說明 [!DNL Catalog Service] 包括：

![新增](../assets/new.svg) 新功能
![修正](../assets/fix.svg) 修正和改良
![錯誤](../assets/bug.svg) 已知問題

## 最新主要版本

_2023年4月25日_

![新增](../assets/new.svg) 目錄服務客戶現在可以利用 [SaaS價格索引器](../price-index/index.md).

### 第1.7版

_2023年4月12日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 目錄服務現在會清除已刪除的產品變體。
![修正](../assets/fix.svg) 基礎架構可擴充性和效能改善。

#### 已知限制

尚不支援下列功能：

* 以固定價格捆綁產品
* 動態屬性有效負載的最大大小為9 MB。
* 組產品價格。 可使用簡單的產品價格計算。
* 在影像陣列中，只有第一個影像包含角色。

使用API Mesh和核心GraphQL API可解決下列限制：

* 最低廣告價格
* [分層定價](mesh.md)
* 可下載的產品和禮品卡

### 第1.6版

_2023年3月28日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 新增色票至 [`products`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/products/) 查詢。
![新增](../assets/new.svg) 新增取得 `entityId` 使用 [API Mesh](mesh.md).

### 第1.5版

_2023年3月6日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 新增 [`categories`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/categories/) GraphQL功能。
![修正](../assets/fix.svg) 改善效能和API可擴充性。

### 第1.4版

_2023年2月7日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 發佈目錄服務元資料包以簡化安裝步驟。
![修正](../assets/fix.svg) API可擴充性和效能改善。

### 第1.3版

_2023年1月17日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 簡化並改善入門體驗。
![新增](../assets/new.svg) 生產前測試可使用新的客戶沙箱端點。
![新增](../assets/new.svg) 新增對虛擬產品的支援。
![修正](../assets/fix.svg) API可擴充性和效能改善。

### 第1.1版

_2022年11月18日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 目錄服務現在支援Adobe [API Mesh](https://developer.adobe.com/graphql-mesh-gateway/).
![修正](../assets/fix.svg) 改善API可擴充性和整體效能。

### 1.0版

_2022年10月4日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 現在支援捆綁和分組產品。
![新增](../assets/new.svg) 新增B2B可見性覆寫。 產品現在可供搜尋，並可針對特定客戶群組新增至購物車。
![修正](../assets/fix.svg) 服務現在更穩定，效能也有所提高。

## 舊版

+++測試版

### 0.3版 — 測試版+

_2022年9月12日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 變體支援的影像：系統會根據選取的選項傳回產品影像
![新增](../assets/new.svg) 價格支援的角色：僅允許特定客戶群組的成員查看產品價格
![修正](../assets/fix.svg) 提高服務的穩定性和效能
![新增](../assets/new.svg) 從目錄中刪除產品時，會收到更新

### 測試版

_2022年8月9日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 此 `products` 和 `refineProduct` 查詢會傳回下列資料：

* 預先定義（系統）產品屬性。
* 動態產品屬性，並依角色篩選（產品顯示頁面/產品清單頁面）。
* 產品選項。
* 產品影像並依角色(PDP/PLP)篩選。
* 簡單產品的特定價格和可配置產品的價格範圍。
* 客戶群組價格和價格範圍。 在沒有客戶群組的購物者，系統會傳回後援的預設價格。
* 使用B2B客戶專屬定價的產品類型。

+++
