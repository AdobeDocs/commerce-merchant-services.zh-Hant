---
title: 目錄同步
description: 了解如何從 [!DNL Commerce] 伺服器 [!DNL Commerce Services] 不斷更新服務。
exl-id: 19d29731-097c-4f5f-b8c0-12f9c91848ac
source-git-commit: 853c55fbae3ccfb7abea8ce074127f2871d55688
workflow-type: tm+mt
source-wordcount: '904'
ht-degree: 0%

---

# 目錄同步

Adobe Commerce和Magento Open Source使用索引器將目錄資料編譯為表。 程式會由 [事件](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html#events-that-trigger-full-reindexing) 例如產品價格或庫存水準的變更。

目錄同步程式每小時執行，以允許 [!DNL Commerce] 使用目錄資料的服務。 目錄同步會從 [!DNL Commerce] 伺服器 [!DNL Commerce] 持續提供服務，使服務保持最新。 例如， [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) 需要目前的目錄資訊，才能以正確的名稱、定價和可用性準確傳回建議。 您可以使用 _目錄同步_ 用於觀察和管理同步過程的儀表板，或 [命令行介面](#resynccmdline) 觸發目錄同步並重新索引產品資料以供消耗 [!DNL Commerce] 服務。

>[!NOTE]
>
> 若要使用 _目錄同步_ 控制面板或命令列介面，您必須 [API密鑰和配置的SaaS資料空間](saas.md).

## 存取目錄同步控制面板

>[!NOTE]
>
> 此 _目錄同步_ 只有在 _產品Recommendations_ 模組被安裝並僅反映與該功能相關的資料預測。 支援其他商務服務，例如 _即時搜尋_ 和 _目錄服務_ 是為未來而規劃的。

若要存取目錄同步控制面板，請選取 **系統** > _資料傳輸_ > **目錄同步**.

使用 **目錄同步** 控制面板：

- 查看同步狀態(**進行中**, **成功**, **失敗**)
- 檢視同步的產品總數（如果成功）
- 搜尋同步產品以檢視其目前狀態
- 依名稱、SKU等搜尋商店目錄
- 在JSON中檢視同步產品的詳細資訊，以協助診斷同步不一致
- 重新啟動同步過程

### 上次同步

報告同步狀態為：

- **成功**  — 顯示同步成功的日期和時間以及更新的產品數量
- **失敗**  — 顯示嘗試同步的日期和時間
- **進行中**  — 顯示上次成功同步的日期和時間

>[!NOTE]
>
> 目錄同步程式每小時會自動執行一次。 不過，如果您的店面上沒有看到產品，或者如果產品未反映您最近所做的變更，您可以解決 [目錄同步問題](#resolvesync).

### 已同步的產品

顯示從 [!DNL Commerce] 目錄。 初始同步後，您應該只希望同步已變更的產品。

## 重新同步 {#resync}

如果您必須在每小時計畫同步發生之前啟動目錄的重新同步，則可以強制重新同步。

>[!NOTE]
>
> 強制重新同步會觸發整個產品目錄的重新同步，而增加硬體資源的負載。

1. 從 _目錄同步_ 控制面板，選取 **設定**.

   此 _目錄同步設定_ 頁。

1. 在 _重新同步資料_ ，按一下 [!UICONTROL Resync].

   [!DNL Commerce] 在下次排程的同步視窗中同步目錄。 根據目錄的大小，此操作可能需要很長時間。

## 同步的目錄產品

此 **同步的目錄產品** 表格顯示下列資訊。

| 欄位 | 說明 |
|---|---|
| ID | 產品的唯一識別碼 |
| 名稱 | 產品的店面名稱 |
| 類型 | 識別產品類型，例如簡單、可設定、可下載等 |
| 上次匯出 | 上次成功從目錄導出產品的日期 |
| 上次修改時間 | 上次在目錄中修改產品的日期 |
| SKU | 顯示產品的庫存單位 |
| 價格 | 產品價格 |
| 可見度 | 產品的可見性設定，如 [!DNL Commerce] 目錄 |

## 解決目錄同步問題 {#resolvesync}

觸發資料重新同步時，最多可能需要一小時的資料才會更新，並反映在UI元件（例如建議單位）中。 不過，如果等了一小時後，您仍注意到目錄與店面上顯示的內容不一致，或目錄同步失敗，請參閱下列內容：

### 資料不一致

1. 在搜尋結果中顯示有關產品的詳細檢視。
1. 複製JSON輸出，並確認內容符合您在 [!DNL Commerce] 目錄。
1. 如果內容不符合，請對目錄中的產品進行微幅變更，例如新增空格或句號。
1. 等待重新同步或 [觸發手動重新同步](#resync).

### 同步未運行

如果同步未在排程上執行，或未同步任何內容，請參閱 [知識庫](https://support.magento.com/hc/en-us/articles/360042224851).

### 同步失敗

如果目錄同步的狀態為 **失敗**，提交 [支援票證](https://support.magento.com/hc/en-us/articles/360000913794#submit-ticket).

## 命令列介面 {#resynccmdline}

此 `saas:resync` 命令是 `magento/saas-export` 包。 您可以使用 [!DNL Commerce Services] 產品，例如 [[!DNL Product Recommendations]](/help/product-recommendations/install-configure.md) 或 [[!DNL Live Search]](/help/live-search/install.md).

>[!NOTE]
>
> 從命令列觸發資料重新同步時，最多可能需要一小時的時間才能更新資料。

命令選項：

```bash
bin/magento saas:resync --feed <feed name> [no-reindex]
```

下表說明 `saas:resync` 參數和說明。

| 參數 | 說明 | 必要？ |
|---| ---| ---|
| `feed` | 指定要重新同步的實體，例如 `products` | 是 |
| `no-reindex` | 將現有目錄資料重新提交至 [!DNL Commerce Services] 不需重新索引。 未指定此參數時，命令會在同步資料之前運行完整的重新索引。 | 否 |

摘要名稱可以是下列其中一項：

- `products` — 目錄中的產品
- `categories` — 目錄中的類別
- `variants` — 可配置產品的產品變化，如顏色和大小
- `productattributes` — 產品屬性，例如 `activity`, `gender`, `tops`, `bottoms`等
- `productoverrides` — 特定於客戶的定價和目錄可見性規則，例如基於類別權限的規則

### 範例

下列範例會從 [!DNL Commerce] 將其編錄並重新同步到商務服務：

```bash
bin/magento saas:resync --feed products
```

如果您不想執行產品的完整重新索引，則可以改為同步已產生的產品資料：

```bash
bin/magento saas:resync --feed products --no-reindex
```
