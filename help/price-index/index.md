---
title: SaaS價格索引
description: 使用SaaS價格索引來提高效能
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
exl-id: 747c0f3e-dfde-4365-812a-5ab7768342ab
source-git-commit: 7b2d90eb809eada732ed5d3ad4e038bd9733c440
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 0%

---

# SaaS價格索引

SaaS價格索引加快了價格更改在提交後反映在SaaS客戶網站上所花的時間。 此可選模組允許具有大型、複雜目錄或具有多個網站或客戶組的商戶更快、更持續地處理價格變化。

管道的最大瓶頸是：已將大量計算程式（例如索引和價格計算）從PHP核心移至Adobe的雲基礎架構。 這可讓商戶快速擴大資源，以提高價格指數化時間，並以更快的速度反映這些對網站的更改。

所有符合要求的商戶都能從這些改進中受益，但獲得最大收益的商戶是：

* 價格不變：商戶需要反複調整價格以達到策略目標，例如頻繁促銷、季節性折扣或存貨折扣。
* 多個網站和/或客戶群組：在多個網站（網域/品牌）和/或客戶群組之間具有共用產品目錄的商家。
* 網站或客戶群之間的大量不重複價格：具有廣泛共用產品目錄的商家，包含網站或客戶群之間的不重複價格，例如具有預先商定價格的B2B商家、具有不同定價策略的品牌。

如果您有依賴PHP核心價格索引器的第三方應用程式，請閱讀文檔並咨詢擴展提供程式，然後進行任何更改。

使用Adobe Commerce服務的客戶可免費使用SaaS價格索引。

本迷你指南介紹了SaaS價格索引的工作方式，以及如何啟用它。

## 系統需求

要使用SaaS價格索引，您需要：

* Adobe Commerce 2.4.4+
* 至少安裝了以下SaaS服務之一：

   * [目錄服務](../catalog-service/overview.md)
   * [即時搜尋](../live-search/guide-overview.md)
   * [產品Recommendations](../product-recommendations/guide-overview.md)

## 模組

SaaS價格索引使用一組模組來提供功能。 所需模組的清單可能稍有不同，具體取決於儲存設定。

這些模組會將新摘要新增至管理員。 這些饋送將價格計算所需的資料傳輸到SaaS索引器，並忽略PHP核心價格索引器。

```
magento/module-saas-price
magento/module-saas-scopes
magento/module-product-override-price-remover
magento/module-bundle-product-override-data-exporter
```

使用Luma和Adobe Commerce Core GraphQL的客戶可以安裝提供Luma相容性的模組，並停用PHP核心價格索引器：

```
adobe-commerce/catalog-adapter
```

此 `catalog-adapter` 僅與2.4.5相容。近期將發行對2.4.4和2.4.6的支援。
如果第三方擴展或任何其他原因需要，可以重新啟用PHP核心價格索引器。

## 警告

根據產品類型、價格複雜性和目錄大小等因素，SaaS價格索引可能是適合您商店的合適解決方案。 閱讀下列限制並判斷這是否適合您的網站。

目前，SaaS價格索引支援簡單、分組、虛擬、可配置和捆綁動態產品類型。
即將推出可下載、禮品卡和捆綁固定產品類型的支援。

SaaS價格索引支援基價：

* 最低/最高常規價格
* 最低/最高最終價格
* 特價
* 客戶組價格
* 目錄規則價格

選擇使用新的定價摘要後，您可以聯絡 [支援](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html) 來幫你還原。

新摘要應手動同步至 `resync` [CLI命令](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html#resynccmdline). 否則，資料會在標準同步程式中重新整理。 取得 [目錄同步](../landing/catalog-sync.md) 程式。

## 使用情況

### 沒有擴充功能相依性的Luma

* 已安裝必要服務(即時搜尋、產品Recommendations、目錄服務)的Luma或Abode商務核心GraphQL商家
* 沒有依賴PHP核心價格索引器的第三方擴展
* 銷售簡單、可配置、分組、虛擬和捆綁的動態產品

1. 啟用新摘要。
1. 安裝目錄適配器。

### 具有PHP核心價格索引器依賴項的Luma和Abode Commerce Core GraphQl

* 已安裝支援服務(即時搜尋、產品Recommendations、目錄服務)的Luma或Abode商務核心GraphQL商家
* 依賴PHP核心價格索引器的第三方擴展
* 銷售簡單、可配置、分組、虛擬和捆綁的動態產品

1. 啟用新摘要
1. 安裝目錄適配器。
1. 重新啟用PHP核心價格索引器。
1. 在 `catalog-adapter` 模組。

### 無頭商人

* 安裝了受支援服務(即時搜索、產品Recommendations、目錄服務)的無頭商家
* 不依賴PHP核心價格索引器
* 銷售簡單、可配置、分組、虛擬和捆綁的動態產品

1. 啟用新摘要
1. 安裝目錄適配器，該適配器禁用PHP核心價格索引器。

### Luma/Core GraphQL/Headless，不支援的產品類型

* Luma/無頭商人
* 銷售禮品卡、可下載或捆綁固定產品

若目前不支援的產品類型，請等待完整的產品類型支援。
