---
title: '"[!DNL Live Search] 索引」'
description: 「了解如何 [!DNL Live Search] 索引產品屬性。」
exl-id: 04441e58-ffac-4335-aa26-893988a89720
source-git-commit: 995f528abc0011c6ae7c4c524982c301072ec2eb
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 0%

---

# 索引

產品屬性（中繼資料）決定：

* 如何在目錄中使用屬性
* 在商店裡的外觀和行為
* 資料傳輸操作中包含的資料

屬性元資料的範圍是 `website/store/store view`.

此 [!DNL Live Search] API可讓用戶端依任何具有 [storefront屬性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) `Use in Search` 設為 `Yes` (在Adobe Commerce管理員中)。 啟用後， `Search Weight` 和 `Visible in Advanced Search` 可為屬性設定。

>[!NOTE]
>
>[!DNL Live Search] 不會將已刪除的產品或設為 `Not Visible Individually`.

## 索引管線

客戶端從店面調用搜索服務以檢索（可過濾、可排序）索引元資料。 只有可搜尋的產品屬性 *用於分層導航* 屬性設定為 `Filterable (with results)` 和 *用於產品清單中的排序* 設為 `Yes` 可由搜尋服務呼叫。
要構建動態查詢，搜索服務需要知道哪些屬性是可搜索的及其權重。 [!DNL Live Search] 會考量Adobe Commerce的搜尋權數（1至10，其中10是最優先順序）。 可在架構中找到與目錄服務同步和共用的資料清單，此架構在中定義：

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

![[!DNL Live Search] 索引客戶搜索圖](assets/indexing-pipeline.svg)

1. 檢查商戶 [!DNL Live Search] 權利。
1. 使用屬性中繼資料的變更取得商店檢視。
1. 儲存索引屬性。
1. 重新索引搜索索引。

### 完整索引

當 [!DNL Live Search] 在上線期間會進行設定並同步，最多需要8小時才能建立初始索引。 此程式在 `cron` 提交摘要並完成執行。

以下事件會觸發完全同步和索引建置：

* 入門 [目錄資料同步](install.md#synchronize-catalog-data)
* 屬性中繼資料的變更

例如，變更 `Use in Search` 屬性 `color` 屬性自 `No` to `Yes` 將屬性中繼資料變更為 `searchable=true`，並觸發完整同步和重新索引。 下列屬性中繼資料會在變更時觸發完全同步和重新索引：

* `filterableInSearch`
* `searchable`
* `sortable`
* `visibleInSearch`

### 串流產品更新

建立初始索引後， [入門](install.md#synchronize-catalog-data)，會持續同步下列增量產品更新並重新編列索引：

* 新產品添加到目錄中
* 產品屬性值的變更

例如，將新色票值新增至 `color` 屬性會以串流產品更新的形式處理。
串流更新工作流程：

1. 更新的產品會從Adobe Commerce執行個體同步至目錄服務。
1. 索引服務會持續從目錄服務尋找產品更新。 更新的產品在到達目錄服務時會建立索引。
1. 產品更新最多可能需要15分鐘，才能在 [!DNL Live Search].

## 用戶端搜尋

此 [!DNL Live Search] API可讓用戶端透過設定 [storefront屬性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html), *用於排序產品清單* to `Yes`. 此設定會根據主題，將屬性納入 [排序依據](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation.html) 目錄頁面上的分頁控制項。 最多可以通過以下方式編製產品屬性索引： [!DNL Live Search]，使用 [店面屬性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) 可供搜尋及篩選。
索引元資料儲存在索引管道中，並可由搜尋服務存取。

![[!DNL Live Search] 索引元資料API圖](assets/index-metadata-api.svg)

### 可排序的屬性工作流

1. 客戶端調用搜索服務。
1. 搜尋服務呼叫搜尋管理服務。
1. 搜索服務調用索引管道。

## 針對所有產品編製索引

此清單中欄位的順序反映了匯出產品資料中欄的典型順序。

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

針對所有可配置產品編製以下欄位的索引：

* `childrenSkus`
