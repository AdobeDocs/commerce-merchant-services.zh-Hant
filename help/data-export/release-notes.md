---
title: '[!DNL SaaS Data Export Extension]發行說明'
description: 適用於Adobe Commerce的 [!DNL Data Export Extension] 的最新發行資訊。
feature: Services, Release Notes
recommendations: noCatalog
exl-id: 0c7aeeda-e8a6-4740-b466-0661a6d2df07
source-git-commit: 93be63ca7a4edc2890a37a6460a123e28226301a
workflow-type: tm+mt
source-wordcount: '711'
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

## 103.3.11版

![修正](../assets/fix.svg)資料匯出服務現在會以百分比傳送套件組合產品的特殊價格資料，以更正先前傳送為最終價格的問題。 <!--MDEE-854-->
![Fix](../assets/fix.svg)已更新與Monolog 3相容的Monolog實作。<!--MDEE-858-->

## 103.3.10版

![修正](../assets/fix.svg)修正產品自訂選項摘要的多重商店檢閱過濾。 <!--MDEE-842-->
![修正](../assets/fix.svg)在摘要的雜湊值變更之前，不會重新提交無效的摘要。<!--MDEE-848-->

## 103.3.9版

![修正](../assets/fix.svg)刪除實體時，會針對網站(`scopesWebsite`)和客戶群組(`scopesCustomerGroup`)的範圍設定服務摘要傳播`deleted`旗標。<!--MDEE-839-->

## 103.3.8版本

![修正](../assets/fix.svg)已停用的組態選項已不再匯出為作用中選項。<!--MDEE-812-->
![Fix](../assets/fix.svg)變更子產品時，現在會在可設定的產品上更新選項和值。 <!--MDEE-835-->
![新](../assets/new.svg)已新增在產品屬性摘要中包含其他系統屬性資料的功能。

## 103.3.7版

![修正](../assets/fix.svg)從InventoryDataExporter模組移除不必要的相依性。
![修正](../assets/fix.svg)已變更CatalogInventoryDataExporter模組中所含存貨模組的必要版本，以支援Adobe Commerce 2.4.4版。

## 103.3.6版

![修正](../assets/fix.svg)修正多執行緒模式中摘要重新索引期間發生的死結。 查詢現在分成插入和更新操作。
![修正](../assets/fix.svg)已針對有許多網站的大型目錄最佳化價格查詢。
![New](../assets/new.svg)已新增重試邏輯，以便在發生死結時重新執行失敗的交易。

## 103.3.5版

![修正](../assets/fix.svg)設定SaaS一般模組最新相容資料匯出版本的相依性。

![修正](../assets/fix.svg)已將`ScopeConfig`執行個體取代為`ServiceConfigInterface`以支援不同的服務設定。

## 103.3.4版

![修正](../assets/fix.svg)新增支援資料傳輸稽核記錄，方法是在每次從Commerce執行個體傳輸資料至Commerce服務<!--MDEE-785-->時，新增傳送`data_sent_outside`事件的機制

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

![新](../assets/new.svg)已重新命名立即匯出摘要、索引器檢視ID和變更記錄表。
- 摘要表格（和索引子檢視ID）：
   - `catalog_data_exporter_products` -> `cde_products_feed`
   - `catalog_data_exporter_product_attributes` -> `cde_product_attributes_feed`
   - `catalog_data_exporter_categories` -> `cde_categories_feed`
   - `catalog_data_exporter_product_prices` -> `cde_product_prices_feed`
   - `catalog_data_exporter_product_variants` -> `cde_product_variants_feed`
   - `inventory_data_exporter_stock_status` -> `inventory_data_exporter_stock_status_feed`
- 變更記錄表名稱 — 遵循與摘要表相同的命名模式，但變更記錄表名稱會新增`_cl`尾碼。  例如`catalog_data_exporter_products_cl`-> `cde-products_feed_cl`
如果您的自訂程式碼會參考任何這些實體，請以新名稱更新參考，以確保您的程式碼繼續正常運作。

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
