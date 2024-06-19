---
title: '"[!DNL SaaS Data Export Extension] 發行說明」'
description: 的最新版本資訊 [!DNL Data Export Extension] 適用於Adobe Commerce。
feature: Services, Release Notes
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# [!DNL SaaS Data Export] 擴充功能發行說明

以下發行說明說明說明最新版本的 [!DNL SaaS data export] 副檔名。 支援目前的主要發行版本。 舊版的發行說明僅供參考。

更新包括：

![新增](../assets/new.svg) 新功能
![修正](../assets/fix.svg) 修正和改良
![錯誤](../assets/bug.svg) 已知問題


>[!NOTE]
>
>SaaS資料匯出擴充功能是隨「即時搜尋」、「產品Recommendations」和「目錄服務」自動安裝的模組集合。 您可以使用撰寫器檢查系統上安裝的版本。 在某些情況下，您可能會想要升級系統上的資料匯出擴充功能，以取得修正或新功能，而不更新Commerce服務版本。

## 目前的主要版本

## 103.3.5版

![修正](../assets/fix.svg) 設定SaaS一般模組最新相容資料匯出版本的相依性。

![修正](../assets/fix.svg) 已取代 `ScopeConfig` 執行個體，具有 `ServiceConfigInterface` 以支援不同的服務組態。

## 103.3.4版

![修正](../assets/fix.svg) 新增更多有關重新索引程式的詳細資訊，以改善Commerce SaaS資料匯出記錄。

## 103.3.3版本

![新增](../assets/new.svg) SaaS資料匯出現在會快取屬性中繼資料查詢的Entity-Attribute-Value (EAV)屬性。

![修正](../assets/fix.svg) 修正的問題： `InventoryStockStatus` 如果產品已刪除，摘要未在重試時儲存。

## 103.3.2版

![修正](../assets/fix.svg) 修正的問題： `modifiedAt` 移除的實體摘要中缺少欄位。

## 103.3.1版

![修正](../assets/fix.svg) 已修正導致 `Invalid Template File` 安裝Page Builder時，產品摘要重新索引期間顯示的訊息。

## 103.3.0版

![新增](../assets/new.svg) 已將立即匯出摘要表格移轉至統一結構：
`id`， `source_entity_id`， `feed_id`， `modified_at`， `is_deleted`， `status`， `feed_data`， `feed_hash`， `errors`

![新增](../assets/new.svg) 已將目錄和詳細目錄摘要移轉至立即匯出解決方案。

![新增](../assets/new.svg) 將立即匯出摘要cron-job重新命名為 `*_feed_resend_failed_items`.

![新增](../assets/new.svg) 已重新命名立即匯出摘要和變更記錄表。

![修正](../assets/fix.svg) 設定 `modified_at` 欄位僅會顯示在需要摘要的摘要資料中。

![修正](../assets/fix.svg) 修改 `productAttributes` 查詢以僅擷取產品屬性。

## 103.2.6版

![修正](../assets/fix.svg) 修正當表格有首碼時，無法重新索引摘要的問題。

## 103.2.5版

![修正](../assets/fix.svg) 最佳化價格查詢。

## 103.2.4版

![修正](../assets/fix.svg) 修正啟用Commerce Inventory management時，產品顯示的不正確庫存狀態。

## 103.2.3版本

![修正](../assets/fix.svg) 修正網站層級特殊定價。
![修正](../assets/fix.svg) 已針對處理的所有摘要新增Mutex。


## 103.2.2版

![修正](../assets/fix.svg) 改善大型目錄的摘要批次處理策略。 批次表格現在會填入有限數量的ID，以減少記憶體使用量。

![修正](../assets/fix.svg) 消除CommerceInventoryDataExporter對MSI模組的硬性相依性。

![修正](../assets/fix.svg) 已改善 `commerce-data-exporter` 記錄檔以收集更多資訊，並按不同的匯出階段進行組織。

## 103.2.1版

- 已發行更新版本。

## 103.2.0版

- 新增產品和價格的多執行緒資料同步。

