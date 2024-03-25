---
title: 目錄同步
description: 瞭解如何從匯出產品資料 [!DNL Commerce] 伺服器至 [!DNL Commerce Services].
exl-id: 19d29731-097c-4f5f-b8c0-12f9c91848ac
feature: Catalog Management, Data Import/Export, Catalog Service
source-git-commit: d95c11a35c78d72da8126affb0753d86aa695827
workflow-type: tm+mt
source-wordcount: '1133'
ht-degree: 0%

---


# 目錄同步

>[!NOTE]
>
> 「目錄同步」控制面板現在是「資料管理」控制面板。 這個改版後的儀表板現在支援 [[!DNL Product Recommendations]](../product-recommendations/guide-overview.md)， [[!DNL Live Search]](../live-search/guide-overview.md)、和 [[!DNL Catalog Service]](../catalog-service/overview.md). 客戶可以更新至其中一項服務的最新版本，以取得資料管理控制面板。 如需詳細資訊，請參閱 [資料管理控制面板](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) 檔案。 目前這個主題仍適用於尚未升級且仍擁有目錄同步控制面板的使用者。

Adobe Commerce使用索引器將目錄資料編譯到表格中。 程式自動觸發自 [事件](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html#events-that-trigger-full-reindexing) 例如產品價格或存貨層次變更。

目錄同步服務會將產品資料從 [!DNL Adobe Commerce] 執行個體至 [!DNL Commerce Services] 平台，持續保持資料在最新狀態。 例如， [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) 需要目前的目錄資訊，才能以正確的名稱、價格和可用性準確傳回建議。 使用 _目錄同步_ 儀表板來觀察和管理同步程式或 [命令列介面](#resynccmdline) 觸發目錄同步並重新索引產品資料以供以下人員使用： [!DNL Commerce Services].

## 存取目錄同步控制面板

若要存取「目錄同步」儀表板，請選取 **系統** > _資料傳輸_ > **目錄同步**.

使用 **目錄同步** 控制面板您可以：

- 檢視同步處理狀態(**進行中**， **成功**， **已失敗**)
- 檢視同步的產品總數
- 搜尋同步的產品以檢視其目前狀態
- 依名稱、SKU等搜尋商店目錄。
- 檢視JSON中的同步產品詳細資料，以協助診斷同步差異
- 重新起始同步處理作業

### 上次同步

報告下列專案的同步狀態：

- **成功**  — 顯示同步成功的日期和時間，以及更新的產品數量
- **已失敗**  — 顯示嘗試同步的日期和時間
- **進行中**  — 顯示上次成功同步的日期和時間

目錄同步程式每小時會自動執行一次。 如果您在店面沒有看到預期的產品，或者產品沒有反映您最近所做的變更，您可以解決 [目錄同步問題](#resolvesync).

### 產品已同步

顯示與您同步的產品總數 [!DNL Commerce] 目錄。 初次同步後，只應同步已變更的產品。

## 重新同步 {#resync}

如果必須在每小時排程同步發生之前啟動目錄重新同步，則可以強制進行重新同步。

>[!NOTE]
>
> 強制重新同步會觸發整個產品目錄的重新同步，而這會增加硬體資源的負載。

1. 從 _目錄同步_ 儀表板，選取 **設定**.

   此 _目錄同步設定_ 頁面便會顯示。

1. 在 _重新同步資料_ 區段，按一下 [!UICONTROL Resync].

   [!DNL Commerce] 在下一個排定的同步期間同步您的目錄。 視目錄大小而定，這項作業可能需要很長的時間。

## 同步的目錄產品

此 **同步的目錄產品** 表格會顯示下列資訊。

| 欄位 | 說明 |
|---|---|
| ID | 產品的唯一識別碼 |
| 名稱 | 產品的店面名稱 |
| 型別 | 識別產品型別，例如，簡單、可設定或可下載 |
| 上次匯出 | 上次成功從目錄中匯出產品的日期 |
| 上次修改時間 | 上次在目錄中修改產品的日期 |
| SKU | 顯示產品的庫存單位 |
| 價格 | 產品的價格 |
| 可見度 | 產品的可見度設定，如 [!DNL Commerce] 目錄 |

## 解決目錄同步問題 {#resolvesync}

當您觸發資料重新同步時，可能需要長達一小時的時間才會更新資料，並反映在UI元件（例如建議單位）中。 如果您在店面中仍看到目錄與資料之間的差異，或是目錄同步失敗，請參閱下列內容：

### 資料差異

1. 在搜尋結果中顯示相關產品的詳細檢視。
1. 複製JSON輸出，並確認內容符合您在 [!DNL Commerce] 目錄。
1. 如果內容不符，請對目錄中的產品進行微幅變更，例如新增空格或句點。
1. 等待重新同步或 [觸發手動重新同步](#resync).

### 同步處理未執行

如果同步未依排程執行或未同步任何專案，請參閱此 [知識庫](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-product-recommendations-module-in-magento-commerce.html) 文章。

### 同步失敗

如果目錄同步處理的狀態為 **已失敗**，提交 [支援票證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## 命令列介面 {#resynccmdline}

此 `saas:resync` 指令是 `magento/saas-export` 套件和隨附其中一項隨附的現成可用套件 [!DNL Commerce Services] 產品，例如 [[!DNL Product Recommendations]](/help/product-recommendations/install-configure.md) 或 [[!DNL Live Search]](/help/live-search/install.md).

>[!NOTE]
>
> 第一次執行資料同步時，請執行 `productattributes` 會先傳送摘要，接著再傳送 `productoverrides`，再執行 `products` 摘要。

命令選項：

```bash
bin/magento saas:resync --feed <feed name> [no-reindex|cleanup-feed]
```

下表說明 `saas:resync` 引數和說明。

| 引數 | 說明 | 必填？ |
|---| ---| ---|
| `feed` | 指定要重新同步的實體，例如 `products` | 是 |
| `no-reindex` | 將現有的目錄資料重新提交至 [!DNL Commerce Services] 而不重新索引。 如果未指定此引數，命令會在同步資料之前執行完整重新索引。 | 否 |
| `cleanup-feed` | 在同步之前清除摘要索引器表格。 | 否 |

摘要名稱可以是下列其中一項：

- `products` — 目錄中的產品
- `productattributes` — 產品屬性，例如 `activity`， `gender`， `tops`， `bottoms`、等等
- `variants` — 可設定產品的產品變體，例如顏色和大小
- `prices`  — 產品價格
- `scopesCustomerGroup`  — 客戶群組
- `scopesWebsite`  — 有商店檢視的網站
- `categories` — 目錄中的類別
- `categoryPermissions`  — 每個類別的許可權
- `productoverrides` — 客戶特定的定價和目錄可見性規則，例如以類別許可權為基礎的規則

視何者而定 [Commerce服務](../landing/saas.md) 已安裝，您可能有不同的摘要集可用於 `saas:resync` 命令。

不建議執行 `saas:resync` 指令。 在兩種情況下，您可能需要手動執行命令：

- 初始同步
- 此 [SaaS資料空間ID](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) 已變更

### 初始同步

當您觸發 `saas:resync` 從命令列，視您的目錄大小而定，可能需要幾分鐘到幾小時的時間才會更新資料。

對於初始同步，建議按以下順序執行命令：

```bash
bin/magento saas:resync --feed productattributes
bin/magento saas:resync --feed products
bin/magento saas:resync --feed scopesCustomerGroup
bin/magento saas:resync --feed scopesWebsite
bin/magento saas:resync --feed prices
bin/magento saas:resync --feed productoverrides
bin/magento saas:resync --feed variants
bin/magento saas:resync --feed categories
bin/magento saas:resync --feed categoryPermissions 
```

### 疑難排解

如果您在中看不到預期的資料 [!DNL Commerce Service]，檢查同步處理期間是否發生問題 [!DNL Adobe Commerce] 執行個體至 [!DNL Commerce Service] 平台。

中有兩個記錄檔 `var/log/` 目錄：

- `commerce-data-export-errors.log`  — 若期間發生錯誤 _收集_ 階段
- `saas-export-errors.log`  — 若期間發生錯誤 _傳輸_ 階段

#### 檢查摘要裝載

檢視已傳送給的摘要裝載可能會有幫助 [!DNL Commerce Service]. 這可透過傳遞環境變數來完成 `EXPORTER_EXTENDED_LOG=1`. 此 `no-reindex` 標幟表示只會傳送目前收集的資料。

```bash
EXPORTER_EXTENDED_LOG=1 bin/magento saas:resync --feed=products --no-reindex
```

承載可在以下位置使用： `var/log/saas-export.log`.

#### 保留摘要索引表格中的裝載

起始日期 `magento/module-data-exporter:103.0.0` 部分摘要：產品摘要、價格摘要，在索引表格中僅保留最低必要資料。

不建議在生產環境中保留索引表格中的裝載資料，不過在開發人員執行個體中這可能很有用。 若要這麼做，請傳遞 `PERSIST_EXPORTED_FEED=1` 環境變數：

```bash
PERSIST_EXPORTED_FEED=1 bin/magento saas:resync --feed=products
```

#### 設定檔分析

如果特定摘要的重新索引程式耗時過長，請執行效能評測器以收集可能對支援團隊有用的其他資料。 若要這麼做，請傳遞 `EXPORTER_PROFILER=1`環境變數：

```bash
EXPORTER_PROFILER=1 bin/magento indexer:reindex catalog_data_exporter_products
```

效能分析工具資料儲存在 `var/log/commerce-data-export.log` 格式為：

`<Provider class name>, <# of processed entities>, <execution time im ms>, <memory consumption in Mb>`

#### 提交支援要求

如果您看到與設定或協力廠商擴充功能無關的錯誤，請提交 [支援票證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) 儘可能多的資訊。
