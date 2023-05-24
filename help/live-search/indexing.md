---
title: '"[!DNL Live Search] 索引」'
description: 「瞭解如何 [!DNL Live Search] 索引產品屬性屬性。」
exl-id: 04441e58-ffac-4335-aa26-893988a89720
source-git-commit: f310f840e286859070002ab0e23eda3787c89f36
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 0%

---

# 索引

產品屬性屬性（中繼資料）會決定：

* 如何在目錄中使用屬性
* 它在商店中的外觀和行為
* 資料傳輸作業中包含的資料

屬性中繼資料的範圍是 `website/store/store view`.

此 [!DNL Live Search] API可讓使用者端依任何具有下列屬性的產品屬性排序： [店面屬性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) `Use in Search` 設定為 `Yes` (在Adobe Commerce管理員中)。 啟用時， `Search Weight` 和 `Visible in Advanced Search` 可以為屬性設定。

[!DNL Live Search] 不會為已刪除的產品或設為的產品建立索引 `Not Visible Individually`.

>[!NOTE]
>
> 商務客戶，具有 [!DNL Live Search] 可透過以下優勢，利用網站更快速的價格更新及同步化時間： [SaaS價格索引器](../price-index/index.md).

## 索引管道

使用者端從店面呼叫搜尋服務以擷取（可篩選、可排序）索引中繼資料。 只有具備以下條件的可搜尋產品屬性： *用於分層導覽* 屬性設定為 `Filterable (with results)` 和 *用於產品清單中的排序* 設定為 `Yes` 可由search service呼叫。
若要建構動態查詢，搜尋服務需要知道哪些屬性可搜尋及其權重。 [!DNL Live Search] 接受Adobe Commerce搜尋權重（1-10，其中10是最高優先順序）。 在結構描述中可以找到與目錄服務同步和共用的資料清單，其定義如下：

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

![[!DNL Live Search] 索引使用者端搜尋圖表](assets/indexing-pipeline.svg)

1. 檢查商家 [!DNL Live Search] 權利。
1. 取得含屬性中繼資料變更的商店檢視。
1. 儲存索引屬性。
1. 重新索引搜尋索引。

### 完整索引

時間 [!DNL Live Search] 已設定並在上線期間進行同步，最多可能需要8小時才能建立初始索引。 此程式開始於 `cron` 提交摘要並完成執行。

以下事件會觸發完全同步和索引建置：

* 入門 [目錄資料同步](install.md#synchronize-catalog-data)
* 屬性中繼資料的變更

例如，變更 `Use in Search` 的屬性 `color` 屬性來源 `No` 至 `Yes` 將屬性中繼資料變更為 `searchable=true`，並觸發完全同步和重新索引。 下列屬性中繼資料在變更時會觸發完全同步和重新索引：

* `filterableInSearch`
* `searchable`
* `sortable`
* `visibleInSearch`

### 串流產品更新

建立初始索引後，於 [入門](install.md#synchronize-catalog-data)，系統會持續同步及重新索引下列增量產品更新：

* 新增至目錄的新產品
* 產品屬性值的變更

例如，將新的色票值新增至 `color` 屬性會以串流產品更新的形式處理。
串流更新工作流程：

1. 更新的產品會從Adobe Commerce執行個體同步至目錄服務。
1. 索引服務不斷從目錄服務尋找產品更新。 更新的產品到達目錄服務時會建立索引。
1. 產品更新可能最多需要15分鐘才能在中提供 [!DNL Live Search].

## 使用者端搜尋

此 [!DNL Live Search] API可讓使用者端透過設定 [店面屬性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html)， *用於產品清單中的排序* 至 `Yes`. 根據主題，此設定會導致屬性包含在 [排序方式](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation.html) 目錄頁面上的分頁控制項。 索引最多可包含300個產品屬性 [!DNL Live Search]，搭配 [店面屬性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) 可搜尋和可篩選的區段。
索引中繼資料儲存在索引管道中，可供搜尋服務存取。

![[!DNL Live Search] 索引中繼資料API圖表](assets/index-metadata-api.svg)

### 可排序的屬性工作流程

1. 使用者端呼叫搜尋服務。
1. 搜尋服務會呼叫搜尋管理服務。
1. Search Service呼叫索引管道。

## 已針對所有產品建立索引

此清單中的欄位順序反映了匯出產品資料中欄的一般順序。

* `environment_id`
* `website_code`
* `store_code`
* `store_view_code`
* `product_id`
* `sku`
* `name`
* `type`
* `displayable`
* `deleted`
* `url`
* `currency`
* `meta_description`
* `meta_keyword`
* `meta_title`
* `description`
* `short_description`
* `weight`
* `image`
* `small_image`
* `thumbnail_image`
* `prices`
* `in_stock`
* `low_stock`

下列欄位會針對所有可設定的產品編制索引：

* `childrenSkus`
