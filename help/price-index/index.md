---
title: SaaS價格索引
description: 使用SaaS價格索引提高效能
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
exl-id: 747c0f3e-dfde-4365-812a-5ab7768342ab
source-git-commit: 209bdf9c69ff81481d6df7cb8e8832deef13c9f4
workflow-type: tm+mt
source-wordcount: '744'
ht-degree: 0%

---

# SaaS價格索引

SaaS價格索引加快了在SaaS客戶網站提交價格更改後反映價格更改所需的時間。 此可選模組允許具有大型、複雜目錄或具有多個網站或客戶組的商家更快、更連續地處理價格變化。

管道的最大瓶頸是：計算繁重的過程（如索引和價格計算）已從PHP核心轉移到Adobe的雲基礎架構。 這使商家能夠迅速擴大資源，以提高價格指數化時間，並以更快的速度將這些變化反映到網站上。

向SaaS服務提供核心索引資料流的情況如下：

![預設資料流](assets/old_way.png)

使用SaaS價格索引，流程是：

![SaaS價格索引資料流](assets/new_way.png)

所有符合要求的商家都可以從這些改進中獲益，但那些將獲得最大收益的商家是客戶：

* 價格不變：需要反複更改價格以達到戰略目標的商家，如頻繁促銷、季節性折扣或庫存減價。
* 多個網站和/或客戶組：具有跨多個網站（域/品牌）和/或客戶組的共用產品目錄的商家。
* 跨網站或客戶組的大量獨特價格：具有廣泛共用產品目錄的商戶，其中包含網站或客戶群之間的獨特價格，例如具有預先協商價格的B2B商戶，具有不同定價策略的品牌。

如果您有依賴PHP核心價格索引器的第三方應用程式，請閱讀文檔並咨詢擴展提供商，然後進行任何更改。

SaaS價格索引可免費為使用Adobe Commerce服務的客戶提供。

本迷你指南介紹SaaS價格索引的工作原理以及如何啟用它。

## 系統要求

要使用SaaS價格索引，您需要：

* Adobe Commerce2.4.4+
* 至少安裝了下列SaaS服務之一：

   * [目錄服務](../catalog-service/overview.md)
   * [即時搜索](../live-search/guide-overview.md)
   * [產品Recommendations](../product-recommendations/guide-overview.md)

## 模組

SaaS價格索引使用一組模組來提供功能。 所需模組的清單可能略有不同，具體取決於儲存設定。

這些模組將新源添加到管理員。 這些將向SaaS索引器傳送價格計算所需的資料，並忽略PHP核心價格索引器。

```
magento/module-saas-price
magento/module-saas-scopes
magento/module-product-override-price-remover
magento/module-bundle-product-override-data-exporter
```

使用Luma和Adobe Commerce酷睿GraphQL的客戶可以安裝一個模組，該模組提供Luma和酷睿GraphQL相容性，並禁用PHP核心價格索引器：

```
adobe-commerce/catalog-adapter
```

的 `catalog-adapter` 只與2.4.5相容。對2.4.4和2.4.6的支援將在不久的將來釋放。
如果第三方擴展或任何其他原因需要，可以重新啟用PHP核心價格索引器。

## 警告

根據產品類型、價格複雜性和目錄大小等因素，SaaS價格索引可能是您的商店的合適解決方案。 閱讀以下限制並確定這是否適合您的站點。

目前，SaaS價格索引支援簡單、分組、虛擬、可配置和捆綁動態產品類型。
對可下載、禮品卡和捆綁固定產品類型的支援即將推出。

新源應手動與 `resync` [CLI命令](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html#resynccmdline)。 否則，在標準同步過程中刷新資料。 獲取有關 [目錄同步](../landing/catalog-sync.md) 處理。

## 使用方案

### 沒有擴展依賴項的Luma

* 安裝了所需服務(即時搜索、產品Recommendations、目錄服務)的Luma或Abode Commerce核心GraphQL商戶
* 沒有依賴PHP核心價格索引器的第三方擴展
* 銷售簡單、可配置、分組、虛擬和捆綁動態產品

1. 啟用新源。
1. 安裝目錄適配器。

### 具有PHP核心價格索引器依賴的Luma和Abode Commerce Core GraphQl

* 安裝了受支援服務(即時搜索、產品Recommendations、目錄服務)的Luma或Abode Commerce核心GraphQL商戶
* 依靠PHP核心價格索引器進行第三方擴展
* 銷售簡單、可配置、分組、虛擬和捆綁動態產品

1. 啟用新源
1. 安裝目錄適配器。
1. 重新啟用PHP核心價格索引器。
1. 在中使用新源和Luma相容代碼 `catalog-adapter` 中。

### 無頭商人

* 安裝了受支援服務(即時搜索、產品Recommendations、目錄服務)的無頭商家
* 不依賴PHP核心價格索引器
* 銷售簡單、可配置、分組、虛擬和捆綁動態產品

1. 啟用新源
1. 安裝目錄適配器，該適配器將禁用PHP核心價格索引器。

### Luma/CoreGraphQL/無頭產品，不支援產品類型

* 盧瑪/無頭商家
* 銷售禮品卡、可下載或捆綁固定產品

對於當前不受支援的產品類型，請等待完全的產品類型支援。
