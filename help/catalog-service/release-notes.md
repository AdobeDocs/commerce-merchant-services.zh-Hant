---
title: 『[!DNL Catalog Service] 版本注意事項
description: 的最新版本資訊 [!DNL Catalog Service] 適用於Adobe Commerce。
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
feature: Services, Catalog Service, Release Notes
source-git-commit: 6ca91feefbfc2fbc4d5851040b9f1ca3de6a6560
workflow-type: tm+mt
source-wordcount: '741'
ht-degree: 0%

---

# [!DNL Catalog Service] 發行說明

以下版本說明說明最新版本的 [!DNL Catalog Service].
支援目前的主要發行版本。 舊版的發行說明僅供參考。
更新包括：

![新增](../assets/new.svg) 新功能
![修正](../assets/fix.svg) 修正和改良
![錯誤](../assets/bug.svg) 已知問題

## 目前的主要版本

### V1.19版本

_2024年5月23日_

![修正](../assets/fix.svg) <!--DATA-5033-->此 `InStock` 現在選項值的標幟會考量範圍的設定 `enabled` 產品變體的狀態。

![修正](../assets/fix.svg) <!--DATA-5888-->新增對需要大數字（最多16位數）和更高小數位數（最多4位小數）的產品價格的支援。 若要將價格設定更新套用至您現有的目錄，請從以下位置重新同步目錄資料： [資料管理儀表板](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard)，或使用 [Adobe Commerce命令列介面](../landing/catalog-sync.md#command-line-interface).

#### 已知限制

尚未支援下列功能：

* 動態屬性承載的大小上限為9 MB。
* 本集團產品價格可用簡單產品價格計算。
* 在影像陣列中，只有第一個影像包含角色。

使用API Mesh和核心GraphQL API解決下列限制：

* 最低廣告價格
* 層級定價
* 捆綁固定價格的產品

如需詳細資訊和範例，請參閱 [目錄服務和API網格](mesh.md)

## 舊版

+++ 舊版

### V1.18版本

_2024年4月11日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 新增對PHP 8.3的支援。

![新增](../assets/new.svg) 此 [`products`](https://developer.adobe.com/commerce/services/graphql/catalog-service/products/) 和 [`refineProduct`](https://developer.adobe.com/commerce/services/graphql/catalog-service/refine-product/) 查詢現在會傳回簡單和複雜產品的可自訂選項資料。<!--DATA-5538-->

### V1.17版本

_2024年2月22日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 此 [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) 現已推出。 此改版後的儀表板提供資料串流的深入分析 [!DNL Product Recommendations]， [!DNL Live Search]、和 [!DNL Catalog Service]. 對這項功能的支援已引入的v3.1.0 `catalog-service` 中繼封裝。

### V1.16版本

_2024年2月13日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 目錄服務API現在支援產品影片。
![修正](../assets/fix.svg) 無庫存選項現在顯示在PDP Widget中。

#### 已知限制

尚未支援這些功能：

* 動態屬性承載的大小上限為9 MB。
* 群組產品價格。 此值可使用簡單產品價格計算。
* 在影像陣列中，只有第一個影像包含角色。

下列限制可使用API Mesh和核心GraphQL API來解決：

* 最低廣告價格
* [層級定價](mesh.md)

### V1.13版本

_2023年10月12日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 目錄服務支援 `inStock` 產品變體的標幟。
![新增](../assets/new.svg) 此 `urlKey` 和 `externalId` 欄位已新增至GraphQL結構描述。
![新增](../assets/new.svg) 現已支援可下載的產品和禮品卡。

### V1.12版本

_2023年9月19日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 目錄服務現在使用 [SaaS價格索引](../price-index/price-indexing.md).
![修正](../assets/fix.svg) 此版本包含服務端的錯誤修正和改善。

### V1.11版本

_2023年7月18日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 目錄服務現在支援 [`recommendations`](https://developer.adobe.com/commerce/services/graphql/recommendations/recommendations/) 產品Recommendations的GraphQL查詢。

### V1.10版本

_2023年6月27日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 目錄服務API現在支援 `related products`.

### V1.7版本

_2023年4月12日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 目錄服務現在會清理已刪除的產品變體。
![修正](../assets/fix.svg) 基礎建設擴充能力與效能提升。

### V1.6版本

_2023年3月28日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 將色票新增至 [`products`](https://developer.adobe.com/commerce/services/graphql/catalog-service/products/) 查詢。
![新增](../assets/new.svg) 新增以下功能： `entityId` 使用 [API網格](mesh.md).

### V1.5版本

_2023年3月6日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 已新增 [`categories`](https://developer.adobe.com/commerce/services/graphql/catalog-service/categories/) GraphQL功能。
![修正](../assets/fix.svg) 改善效能和API擴充性。

### V1.4版本

_2023年2月7_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 已發佈目錄服務中繼資料以簡化安裝步驟。
![修正](../assets/fix.svg) API擴充性和效能的改善。

### V1.3版本

_2023年1月17日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 簡化並改善入門體驗。
![新增](../assets/new.svg) 新的客戶沙箱端點可用於生產前測試。
![新增](../assets/new.svg) 新增對虛擬產品的支援。
![修正](../assets/fix.svg) API擴充性和效能的改善。

### V1.1版本

_2022年11月18日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 目錄服務現在支援Adobe的 [API網格](https://developer.adobe.com/graphql-mesh-gateway/).
![修正](../assets/fix.svg) 改善API擴充性和整體效能。

### V1.0版本

_2022年10月4日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 現在支援套件和分組的產品。
![新增](../assets/new.svg) 新增B2B可見性覆寫。 產品現在可供搜尋，並可新增至特定客戶群組的購物車。
![修正](../assets/fix.svg) 服務現在更穩定，效能也有所改善。

### 0.3版 — Beta+

_2022年9月12日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 變體支援的影像：根據選取的選項傳回產品影像
![新增](../assets/new.svg) 價格支援的角色：僅允許特定客戶群組的成員檢視產品價格
![修正](../assets/fix.svg) 改善服務的穩定性與效能
![新增](../assets/new.svg) 從目錄中刪除產品時，會收到更新

### Beta版本

_2022年8月9日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) 此 `products` 和 `refineProduct` 查詢會傳回以下資料：

* 預先定義的（系統）產品屬性。
* 動態產品屬性，並依角色（產品顯示頁面/產品清單頁面）篩選。
* 產品選項。
* 產品影像並依角色(PDP/PLP)篩選。
* 簡單產品的特定價格，以及可設定產品的價格範圍。
* 客戶群組價格和價格範圍。 這類優惠會針對沒有客戶群組的購物者傳回遞補預設價格。
* 使用B2B客戶特定定價的產品型別。
