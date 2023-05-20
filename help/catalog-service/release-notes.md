---
title: '"[!DNL Catalog Service] 發行說明'''
description: 的最新發佈資訊 [!DNL Catalog Service] Adobe Commerce。
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
source-git-commit: f955cfc918c19a3c32126d8c9ef8a59b0e0dce0a
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# [!DNL Catalog Service] 發行說明

本發行說明描述 [!DNL Catalog Service]。
為當前主發佈的版本提供支援。 提供了舊版本的發行說明供參考。
更新包括：

![新建](../assets/new.svg) 新功能
![修復](../assets/fix.svg) 修復和改進
![蟲](../assets/bug.svg) 已知問題

## 當前主版本

_2023年4月25日_

![新建](../assets/new.svg) 目錄服務客戶現在可以利用新的 [SaaS價格索引器](../price-index/index.md)。

### V1.7版本

_2023年4月12日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg) 目錄服務現在可清除已刪除的產品變型。
![修復](../assets/fix.svg) 基礎架構可擴充性和效能改進。

#### 已知限制

尚不支援以下功能：

* 捆綁具有固定價格的產品
* 動態屬性負載的最大大小為9 MB。
* 將產品價格分組。 可以使用簡單的產品價格計算。
* 在影像陣列中，只有第一個影像包含角色。

使用API Mesh和核心GraphQLAPI可解決以下限制：

* 最低廣告價格
* [分層定價](mesh.md)
* 可下載的產品和禮品卡

### V1.6版本

_2023年3月28日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg) 已將色板添加到 [`products`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/products/) 的子菜單。
![新建](../assets/new.svg) 添加了獲取 `entityId` 使用 [API網格](mesh.md)。

### V1.5版本

_2023年3月6日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg) 已添加 [`categories`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/categories/) GraphQL功能。
![修復](../assets/fix.svg) 提高了效能和API可擴充性。

### V1.4版本

_2023年2月7日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg) 發佈目錄服務元包以簡化安裝步驟。
![修復](../assets/fix.svg) API可擴充性和效能改進。

### V1.3版本

_2023年1月17日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg) 簡化並改進登機體驗。
![新建](../assets/new.svg) 新的客戶沙盒終結點可用於預生產測試。
![新建](../assets/new.svg) 為虛擬產品添加了支援。
![修復](../assets/fix.svg) API可擴充性和效能改進。

### V1.1版本

_2022年11月18日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg) 目錄服務現在支援Adobe [API網格](https://developer.adobe.com/graphql-mesh-gateway/)。
![修復](../assets/fix.svg) 提高了API可擴充性和整體效能。

### V1.0版本

_2022年10月4日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg) 現在支援捆綁和分組產品。
![新建](../assets/new.svg) 已添加B2B可見性覆蓋。 產品現在可搜索，並可以添加到購物車中，供特定客戶組使用。
![修復](../assets/fix.svg) 服務現在更加穩定，效能也得到改善。

## 以前的版本

+++Beta版本

### 0.3版本 — Beta+

_2022年9月12日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg) 支援變型的影像：根據所選選項返回產品影像
![新建](../assets/new.svg) 價格支援的角色：僅允許特定客戶組的成員查看產品的價格
![修復](../assets/fix.svg) 提高了服務的穩定性和效能
![新建](../assets/new.svg) 從目錄中刪除產品時，將接收更新

### Beta版

_2022年8月9日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg) 的 `products` 和 `refineProduct` 查詢返回以下資料：

* 預定義（系統）產品屬性。
* 動態產品屬性並按角色篩選它們（產品顯示頁/產品清單頁）。
* 產品選項。
* 產品影像並按角色(PDP/PLP)過濾。
* 簡單產品的特定價格和可配置產品的價格範圍。
* 客戶組價格和價格範圍。 它們會向沒有客戶群的購物者退回備用違約價格。
* 使用B2B客戶特定定價的產品類型。

+++
