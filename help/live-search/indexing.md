---
title: '"[!DNL Live Search] 索引」'
description: 「瞭解如何 [!DNL Live Search] 索引產品屬性屬性。」
exl-id: 04441e58-ffac-4335-aa26-893988a89720
source-git-commit: 7eece9b341a27637d7ac00216f18b7fad7c50740
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# 索引

產品屬性屬性（中繼資料）會決定：

* 如何在目錄中使用屬性
* 其在存放區中的外觀和行為
* 資料傳輸作業中包含的資料

屬性中繼資料的範圍是 `website/store/store view`.

此 [!DNL Live Search] API允許使用者端依據任何具有 [店面屬性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) `Use in Search` 設為 `Yes` (在Adobe Commerce管理員中)。 啟用時， `Search Weight` 和 `Visible in Advanced Search` 可設定為屬性。

[!DNL Live Search] 不會索引已刪除的產品或設為 `Not Visible Individually`.

>[!NOTE]
>
> 商務客戶具有 [!DNL Live Search] 可透過以下優勢，利用網站更快速的價格變更更新和同步化時間： [SaaS價格索引子](../price-index/index.md).

## 索引管道

使用者端從店面呼叫搜尋服務以擷取（可篩選、可排序）索引中繼資料。 只有具備以下條件的可搜尋產品屬性： *用於分層導覽* 屬性設定為 `Filterable (with results)` 和 *用於產品清單中的排序* 設為 `Yes` 可由search service呼叫。
若要建構動態查詢，搜尋服務需要知道哪些屬性可搜尋及其權重。 [!DNL Live Search] 遵守Adobe Commerce搜尋權重（1-10，其中10是最高優先順序）。 您可以在結構描述中找到已同步並與目錄服務共用的資料清單，其定義如下：

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

![[!DNL Live Search] 索引使用者端搜尋圖表](assets/indexing-pipeline.svg)

1. 檢查商家 [!DNL Live Search] 權利。
1. 取得含屬性中繼資料變更的存放區檢視。
1. 儲存索引屬性。
1. 重新索引搜尋索引。

### 完整索引

時間 [!DNL Live Search] 已設定並在上線期間同步，最多可能需要30分鐘才能建立初始索引。 大型目錄可能需要更長的時間來編列索引。 此程式在下列時間後開始 `cron` 提交摘要並完成執行。

以下事件會觸發完整同步和索引建置：

* 入門 [目錄資料同步](install.md#synchronize-catalog-data)
* 屬性中繼資料的變更

例如，變更 `Use in Search` 的屬性 `color` 屬性來源 `No` 至 `Yes` 將屬性中繼資料變更為 `searchable=true`，並觸發完整同步和重新索引。 下列屬性中繼資料在變更時觸發完整同步和重新索引：

* `filterableInSearch`
* `searchable`
* `sortable`
* `visibleInSearch`

### 串流產品更新

在建立初始索引期間 [入門](install.md#synchronize-catalog-data)，下列增量產品更新會持續同步並重新索引：

* 新增至目錄的新產品
* 產品屬性值的變更

例如，將新的色票值新增至 `color` 屬性會以串流產品更新的形式處理。
串流更新工作流程：

1. 更新的產品會從Adobe Commerce執行個體同步至目錄服務。
1. 索引服務會持續從目錄服務尋找產品更新。 更新的產品在到達目錄服務時會編制索引。
1. 產品更新可能需要15分鐘的時間才能在中提供 [!DNL Live Search].

## 使用者端搜尋

此 [!DNL Live Search] API可讓使用者端透過設定 [店面屬性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html)， *用於產品清單中的排序* 至 `Yes`. 此設定會根據主題將屬性納入為中的選項 [排序依據：](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation.html) 目錄頁面上的分頁控制項。 索引產品屬性最多可達200個 [!DNL Live Search]，使用 [店面屬性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) 可搜尋及可篩選的專案。
索引中繼資料儲存在索引管道中，並可由搜尋服務存取。

![[!DNL Live Search] 索引中繼資料API圖表](assets/index-metadata-api.svg)

### 可排序的屬性工作流程

1. 使用者端呼叫搜尋服務。
1. 搜尋服務會呼叫搜尋管理服務。
1. Search Service呼叫索引管道。

## 已針對所有產品編制索引

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
