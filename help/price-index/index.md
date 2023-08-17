---
title: SaaS價格索引
description: 使用SaaS價格索引來改善效能
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
exl-id: 747c0f3e-dfde-4365-812a-5ab7768342ab
source-git-commit: 19c4d3263c22914672b38c5dc5ec9908889bb9b6
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 0%

---

# SaaS價格索引

SaaS價格索引可加快價格變更提交後，反映在SaaS客戶網站上的時間。 此選用模組可讓擁有大型複雜目錄或擁有多個網站或客戶群組的商家，更快速且持續地處理價格變更。

此管道的最大瓶頸：例如指數化和價格計算等運算密集程式，已從PHP核心移至Adobe的雲端基礎結構。 這可讓商家快速擴充資源，以縮短價格指數化時間，並以更快的速度在網站中反映這些變更。

核心索引資料流動到SaaS服務的形式如下：

![預設資料流程](assets/old_way.png)

使用SaaS價格指數時，流程為：

![SaaS價格指數資料流程](assets/new_way.png)

所有符合需求的商戶都能受益於這些改善，但收益最大的是擁有下列專案的客戶：

* 不變價格變更：需要重複變更價格以符合策略性目標（例如頻繁促銷、季節性折扣或存貨減價）的商家。
* 多個網站和/或客戶群組：在多個網站（網域/品牌）和/或客戶群組中，擁有共用產品目錄的商家。
* 跨網站或客戶群組的大量不重複價格：具有廣泛共用產品目錄的商家，其中包含跨網站或客戶群組的獨特價格，例如，具有預先議價價格的B2B商家，以及具有不同定價策略的品牌。

如果您有依賴PHP核心價格索引器的協力廠商應用程式，請先閱讀檔案並洽詢擴充功能提供者，然後再進行任何變更。

使用Adobe Commerce服務的客戶可免費使用SaaS價格索引。

本迷你指南說明SaaS價格索引的運作原理以及如何啟用。

## 系統需求

若要使用SaaS價格索引，您需要：

* Adobe Commerce 2.4.4+
* 至少已安裝下列其中一個SaaS服務：

   * [目錄服務](../catalog-service/overview.md)
   * [即時搜尋](../live-search/guide-overview.md)
   * [產品Recommendations](../product-recommendations/guide-overview.md)

## 模組

SaaS價格索引使用一組模組來提供功能。 必要模組的清單可能會因存放區設定而略有不同。

這些模組會新增摘要給管理員。 這些摘要會將價格計算所需的資料傳輸至SaaS索引器，並忽略PHP核心價格索引器。

```
magento/module-saas-price
magento/module-saas-scopes
magento/module-product-override-price-remover
magento/module-bundle-product-override-data-exporter
```

使用Luma和Adobe Commerce Core GraphQL的客戶可以安裝模組，以提供Luma和Core GraphQL相容性，並停用PHP核心價格索引器：

```
adobe-commerce/catalog-adapter
```

此 `catalog-adapter` 僅與2.4.5相容。2.4.4和2.4.6的支援將在不久的未來發行。
如果有第三方擴充功能或任何其他原因，可以重新啟用PHP核心價格索引器。

## 警告

根據產品型別、價格複雜性和目錄大小等因素，SaaS價格索引可能是您商店的正確解決方案。 請閱讀下列限制，並判斷此解決方案是否適合您的網站。

目前，SaaS價格索引支援簡單、分組、虛擬、可設定和 [組合動態](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-bundle.html) 產品型別。
即將支援可下載、禮品卡和套裝固定產品型別。

新的摘要應手動與同步 `resync` [CLI命令](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html#resynccmdline). 否則，資料會在標準同步程式中重新整理。 取得更多關於 [目錄同步](../landing/catalog-sync.md) 程式。

## 使用案例

### Luma沒有擴充功能相依性

* 已安裝必要服務(即時搜尋、產品Recommendations、目錄服務)的Luma或Adobe Commerce Core GraphQL商家
* 沒有依賴PHP核心價格索引器的第三方擴充功能
* 銷售簡單、可設定、群組、虛擬和套裝的動態產品

1. 啟用新摘要。
1. 安裝目錄介面卡。

### Luma和Adobe Commerce核心GraphQl搭配PHP核心價格索引器相依性

* 已安裝支援服務(即時搜尋、產品Recommendations、目錄服務)的Luma或Adobe Commerce Core GraphQL商家
* 透過依賴PHP核心價格索引器的協力廠商擴充功能
* 銷售簡單、可設定、群組、虛擬和套裝的動態產品

1. 啟用新的摘要
1. 安裝目錄介面卡。
1. 重新啟用PHP核心價格索引器。
1. 在中使用新的摘要和Luma相容性代碼 `catalog-adapter` 模組。

### Headless商家

* 已安裝支援服務(即時搜尋、產品Recommendations、目錄服務)的Headless商人
* 不依賴PHP核心價格索引器
* 銷售簡單、可設定、群組、虛擬和套裝的動態產品

1. 啟用新摘要
1. 安裝目錄轉接器，這會停用PHP核心價格索引器。

### Luma/核心GraphQL/Headless搭配不支援的產品型別

* Luma/Headless商家
* 銷售禮品卡、可下載或捆綁式固定產品

若使用目前不支援的產品型別，請等待完整的產品型別支援。
