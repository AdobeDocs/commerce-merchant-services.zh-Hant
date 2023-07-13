---
title: '''[!DNL Catalog Service] 發行說明'
description: 的最新版本資訊 [!DNL Catalog Service] 適用於Adobe Commerce。
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
feature: Services, Catalog Service, Release Notes
source-git-commit: 9ae4aff1851e9ce9920c4fbf11d2616d6f0f6307
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# [!DNL Catalog Service] 發行說明

以下版本說明說明最新版本的 [!DNL Catalog Service].
提供目前主要發行版本的支援。 舊版的發行說明僅供參考。
更新包括：

![新增](../assets/new.svg) 新功能
![修正](../assets/fix.svg) 修正和改良
![錯誤](../assets/bug.svg) 已知問題

## 目前的主要版本

### V1.10版本

_2023年6月27日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 目錄服務現在可以在產品詳細資料頁面Widget中顯示相關產品。

#### 已知限制

尚未支援這些功能：

* 以固定價格捆綁產品
* 動態屬性承載的大小上限為9 MB。
* 群組產品價格。 可使用簡單產品價格計算。
* 在影像陣列中，只有第一個影像包含角色。

下列限制可使用API網格和核心GraphQL API來解決：

* 最低廣告價格
* [層級定價](mesh.md)
* 可下載的產品和禮品卡

### V1.7版本

_2023年4月12日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 目錄服務現在會清除已刪除的產品變體。
![修正](../assets/fix.svg) 基礎建設擴充性與效能的改善。

### V1.6版本

_2023年3月28日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 將色票新增至 [`products`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/products/) 查詢。
![新增](../assets/new.svg) 新增取得 `entityId` 使用 [API網格](mesh.md).

### V1.5版本

_2023年3月6日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 已新增 [`categories`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/categories/) GraphQL功能。
![修正](../assets/fix.svg) 改善效能和API擴充性。

### V1.4版本

_2023年2月7日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 已發佈目錄服務中繼資料以簡化安裝步驟。
![修正](../assets/fix.svg) API擴充性和效能的改善。

### V1.3版本

_2023年1月17日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 簡化並改善入門體驗。
![新增](../assets/new.svg) 新的客戶沙箱端點可用於生產前測試。
![新增](../assets/new.svg) 新增對虛擬產品的支援。
![修正](../assets/fix.svg) API擴充性和效能的改善。

### V1.1版本

_2022年11月18日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 目錄服務現在支援Adobe的 [API網格](https://developer.adobe.com/graphql-mesh-gateway/).
![修正](../assets/fix.svg) 改善API擴充性和整體效能。

### V1.0版本

_2022年10月4日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 現在支援套件和分組的產品。
![新增](../assets/new.svg) 新增B2B可見性覆寫。 產品現在可供搜尋，並可新增至特定客戶群組的購物車。
![修正](../assets/fix.svg) 服務現在更穩定，效能也有所提升。

## 舊版

+++Beta版

### 0.3版 — Beta+

_2022年9月12日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 變體支援的影像：根據選取的選項傳回產品影像
![新增](../assets/new.svg) 價格支援的角色：僅允許特定客戶群組的成員檢視產品價格
![修正](../assets/fix.svg) 改善服務的穩定性和效能
![新增](../assets/new.svg) 從目錄中刪除產品時收到更新

### 測試版

_2022年8月9日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) 此 `products` 和 `refineProduct` 查詢會傳回下列資料：

* 預先定義的（系統）產品屬性。
* 動態產品屬性，並依角色（產品顯示頁面/產品清單頁面）篩選。
* 產品選項。
* 產品影像並依角色(PDP/PLP)篩選。
* 簡單產品的特定價格，以及可設定產品的價格範圍。
* 客戶群組價格和價格範圍。 它們會針對沒有客戶群組的購物者傳回遞補預設價格。
* 使用B2B客戶特定定價的產品型別。

+++
