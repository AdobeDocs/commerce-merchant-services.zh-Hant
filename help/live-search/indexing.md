---
title: '"[!DNL Live Search] 索引"'
description: 「瞭解如何 [!DNL Live Search] 索引product屬性屬性。"
exl-id: 04441e58-ffac-4335-aa26-893988a89720
source-git-commit: 2835209ad881db388894c5b1da213312436d3550
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---

# 索引

產品屬性屬性（元資料）決定了屬性在目錄中的使用方式、其在儲存中的外觀和行為，以及資料傳輸操作中包括的資料。 屬性元資料的範圍是 `website/store/store view`。

的 [!DNL Live Search] API允許客戶端按具有 [storefront屬性](https://docs.magento.com/user-guide/stores/attributes-product.html) `Use in Search` 設定為 `Yes` 在Adobe Commerce行政區。 啟用後， `Search Weight` 和 `Visible in Advanced Search` 可以為屬性設定。

>[!NOTE]
>
>[!DNL Live Search] 未對刪除的產品或設定為的產品編製索引 `Not Visible Individually`。

## 索引管線

客戶端從儲存前端調用搜索服務以檢索（可過濾、可排序）索引元資料。 僅具有 *在分層導航中使用* 屬性設定為 `Filterable (with results)` 和 *用於在產品清單中排序* 設定為 `Yes` 可由搜索服務調用。
為了構造動態查詢，搜索服務需要知道哪些屬性是可搜索的及其權重。 [!DNL Live Search] Adobe Commerce的搜索權（1-10，其中10是最優先的）。 可以在架構中找到與目錄服務同步和共用的資料清單，該架構定義如下：

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

![[!DNL Live Search] 索引客戶端搜索圖](assets/indexing-pipeline.svg)

1. 檢查商戶 [!DNL Live Search] 權利。
1. 獲取包含對屬性元資料所做的更改的儲存視圖。
1. 儲存索引屬性。
1. 重新索引搜索索引。

### 完整索引

當 [!DNL Live Search] 在登機期間進行配置和同步，構建初始索引可能需要8小時。 該過程在 `cron` 提交源並完成運行。

以下事件觸發完全同步和索引生成：

* 登機 [目錄資料同步](install.md#synchronize-catalog-data)
* 對屬性元資料的更改

例如，更改 `Use in Search` 屬性 `color` 屬性 `No` 至 `Yes` 將屬性元資料更改為 `searchable=true`，並觸發完全同步和重新索引。 以下屬性元資料在更改時觸發完全同步並重新索引：

* `filterableInSearch`
* `searchable`
* `sortable`
* `visibleInSearch`

### 流式處理產品更新

在 [登機](install.md#synchronize-catalog-data)，以下增量產品更新會持續同步並重新索引：

* 添加到目錄的新產品
* 對產品屬性值的更改

例如，向 `color` 屬性被處理為流產品更新。
流式更新工作流：

1. 更新的產品將從Adobe Commerce實例同步到目錄服務。
1. 索引服務持續從目錄服務查找產品更新。 更新的產品在到達目錄服務時將對其進行索引。
1. 產品更新可能需要15分鐘才能在 [!DNL Live Search]。

## 客戶端搜索

的 [!DNL Live Search] API允許客戶端通過設定 [storefront屬性](https://docs.magento.com/user-guide/catalog/product-attributes.html)。 *用於在產品清單中排序* 至 `Yes`。 根據主題，此設定將使屬性作為選項包括在 [排序依據](https://docs.magento.com/user-guide/catalog/navigation.html) 目錄頁上的分頁控制項。 最多可以通過 [!DNL Live Search], [儲存屬性](https://docs.magento.com/user-guide/stores/attributes-product.html) 可搜索和過濾。
索引元資料被儲存在索引管線中，並且可由搜索服務訪問。

![[!DNL Live Search] 索引元資料API圖](assets/index-metadata-api.svg)

### 可排序屬性工作流

1. 客戶端調用Search Service。
1. Search Service調用Search Admin Service。
1. Search Service調用索引管道。

## 為所有產品編製索引

此清單中欄位的順序反映了導出產品資料中列的典型順序。

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

為所有可配置產品編製了以下欄位的索引：

* `childrenSkus`
