---
title: '[!DNL SaaS Data Export Extension]發行說明'
description: 適用於Adobe Commerce的 [!DNL Data Export Extension] 的最新發行資訊。
feature: Services, Release Notes
recommendations: noCatalog
exl-id: 0c7aeeda-e8a6-4740-b466-0661a6d2df07
source-git-commit: 42a9ea0f62f35db451cd3e780adf530d0699a638
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# [!DNL SaaS Data Export]擴充功能發行說明

下列發行說明說明[!DNL SaaS data export]擴充功能的最新版本。 支援目前的主要發行版本。 舊版的發行說明僅供參考。

更新包括：

![新](../assets/new.svg)新功能
![修正](../assets/fix.svg)修正和改良
![錯誤](../assets/bug.svg)已知問題


>[!NOTE]
>
>SaaS資料匯出擴充功能是隨「即時搜尋」、「產品Recommendations」和「目錄服務」自動安裝的模組集合。 您可以使用撰寫器檢查系統上安裝的版本。 在某些情況下，您可能會想要升級系統上的資料匯出擴充功能，以取得修正或新功能，而不更新Commerce服務版本。

## 目前的主要版本

## 103.3.5版

![修正](../assets/fix.svg)設定SaaS一般模組最新相容資料匯出版本的相依性。

![修正](../assets/fix.svg)已將`ScopeConfig`執行個體取代為`ServiceConfigInterface`以支援不同的服務設定。

## 103.3.4版

![修正](../assets/fix.svg)新增更多有關重新索引程式的詳細資訊，以改善Commerce SaaS資料匯出記錄。

## 103.3.3版本

![新](../assets/new.svg) SaaS資料匯出現在會快取屬性中繼資料查詢的Entity-Attribute-Value (EAV)屬性。

![修正](../assets/fix.svg)修正產品被刪除時，`InventoryStockStatus`摘要未在重試時儲存的問題。

## 103.3.2版

![修正](../assets/fix.svg)修正移除的實體摘要中缺少`modifiedAt`欄位的問題。

## 103.3.1版

![修正](../assets/fix.svg)修正安裝Page Builder時，產品摘要重新索引期間出現`Invalid Template File`訊息的問題。

## 103.3.0版

![新](../assets/new.svg)已移轉立即匯出摘要資料表至統一結構：
`id`、`source_entity_id`、`feed_id`、`modified_at`、`is_deleted`、`status`、`feed_data`、`feed_hash`、`errors`

![新](../assets/new.svg)已將目錄和詳細目錄摘要移轉至立即匯出解決方案。

![新](../assets/new.svg)已將立即匯出摘要cron-job重新命名為`*_feed_resend_failed_items`。

![新](../assets/new.svg)已重新命名立即匯出摘要並變更記錄表。

![修正](../assets/fix.svg)在摘要資料中設定`modified_at`欄位，但僅限於需要它的摘要。

![修正](../assets/fix.svg)修改`productAttributes`查詢以僅擷取產品屬性。

## 103.2.6版

![修正](../assets/fix.svg)修正當資料表有首碼時，無法重新索引摘要的問題。

## 103.2.5版

![修正](../assets/fix.svg)已最佳化價格查詢。

## 103.2.4版

![修正](../assets/fix.svg)修正啟用Commerce Inventory management時，產品顯示的不正確庫存狀態。

## 103.2.3版本

![修正](../assets/fix.svg)修正網站層級特殊定價。
![修正](../assets/fix.svg)已針對所有處理的摘要新增Mutex。


## 103.2.2版

![修正](../assets/fix.svg)已改善大型目錄的摘要批次處理策略。 批次表格現在會填入有限數量的ID，以減少記憶體使用量。

![修正](../assets/fix.svg)消除了CommerceInventoryDataExporter對MSI模組的硬性相依性。

![修正](../assets/fix.svg)已改善`commerce-data-exporter`記錄檔，以收集更多資訊，並依不同的匯出階段加以組織。

## 103.2.1版

- 已發行更新版本。

## 103.2.0版

- 新增產品和價格的多執行緒資料同步。
