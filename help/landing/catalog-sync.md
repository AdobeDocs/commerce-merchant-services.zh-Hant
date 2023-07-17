---
title: 目錄同步
description: 瞭解如何從匯出產品資料 [!DNL Commerce] 伺服器至 [!DNL Commerce Services] 持續提供服務，以保持最新狀態。
exl-id: 19d29731-097c-4f5f-b8c0-12f9c91848ac
feature: Catalogs, Data Import/Export, Catalog Service
source-git-commit: d803cd9c78ac8c5529eadf39f361d7e46045359e
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 0%

---

# 目錄同步

Adobe Commerce和Magento Open Source使用索引器將目錄資料編譯為表格。 程式由自動觸發 [事件](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html#events-that-trigger-full-reindexing) 例如產品價格或存貨層次變更。

目錄同步程式每小時執行一次，以允許 [!DNL Commerce] 服務使用目錄資料。 目錄同步會從匯出產品資料 [!DNL Commerce] 伺服器至 [!DNL Commerce] 持續提供服務，以保持服務的最新狀態。 例如， [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) 需要最新的目錄資訊，才能以正確的名稱、定價和可用性準確傳回建議。 您可以使用 _目錄同步_ 儀表板來觀察和管理同步程式或 [命令列介面](#resynccmdline) 若要觸發目錄同步和重新索引產品資料以供以下人員使用： [!DNL Commerce] 服務。

>[!NOTE]
>
> 若要使用 _目錄同步_ 圖示板或命令列介面中，必須有 [API金鑰和已設定的SaaS資料空間](saas.md).

## 存取「目錄同步」控制面板

>[!NOTE]
>
> 此 _目錄同步_ 儀表板僅適用於 _產品Recommendations_ 模組已安裝，且僅會反映與該功能相關的資料投影。 支援其他商務服務，例如 _即時搜尋_ 和 _目錄服務_ 已規劃在未來推出。

若要存取「目錄同步」儀表板，請選取 **系統** > _資料傳輸_ > **目錄同步**.

使用 **目錄同步** 控制面板您可以：

- 檢視同步處理狀態(**進行中**， **成功**， **已失敗**)
- 檢視同步的產品總數（如果成功）
- 搜尋同步的產品以檢視其目前狀態
- 依名稱、SKU等搜尋存放區目錄
- 以JSON檢視同步的產品詳細資訊，以協助診斷同步差異
- 重新起始同步處理作業

### 上次同步

報告以下專案的同步狀態：

- **成功**  — 顯示同步成功的日期和時間，以及更新的產品數量
- **已失敗**  — 顯示嘗試同步的日期和時間
- **進行中**  — 顯示上次成功同步的日期和時間

>[!NOTE]
>
> 目錄同步程式每小時會自動執行一次。 不過，如果您沒有在店面看到產品，或產品未反映您最近所做的變更，您可以解決 [目錄同步問題](#resolvesync).

### 產品已同步

顯示從以下專案同步的產品總數： [!DNL Commerce] 目錄。 初次同步後，您應該只會同步已變更的產品。

## 重新同步 {#resync}

如果必須在每小時排程同步前啟動目錄的重新同步，則可以強制進行重新同步。

>[!NOTE]
>
> 強制重新同步會觸發整個產品目錄的重新同步，而這會增加硬體資源的負載。

1. 從 _目錄同步_ 儀表板，選取 **設定**.

   此 _目錄同步設定_ 頁面便會顯示。

1. 在 _重新同步資料_ 區段，按一下 [!UICONTROL Resync].

   [!DNL Commerce] 會在下一個排定的同步處理期間同步您的目錄。 根據目錄的大小，此操作可能需要很長的時間。


## 已同步的目錄產品

此 **已同步的目錄產品** 表格會顯示下列資訊。

| 欄位 | 說明 |
|---|---|
| ID | 產品的唯一識別碼 |
| 名稱 | 產品的店面名稱 |
| 型別 | 識別產品型別，例如，簡單、可設定、可下載等 |
| 上次匯出時間 | 上次成功從目錄中匯出產品的日期 |
| 上次修改時間 | 上次在目錄中修改產品的日期 |
| SKU | 顯示產品的庫存單位 |
| 價格 | 產品的價格 |
| 可見度 | 產品的可見度設定，如 [!DNL Commerce] 目錄 |

## 解決目錄同步問題 {#resolvesync}

當您觸發資料重新同步時，最多可能需要一小時的時間才會更新資料，並反映在UI元件中，例如建議單位。 但是，如果在等待一小時後，您仍然注意到目錄與店面顯示的內容之間有差異，或是目錄同步失敗，請參考以下內容：

### 資料差異

1. 在搜尋結果中顯示相關產品的詳細檢視。
1. 複製JSON輸出，並確認內容符合您在 [!DNL Commerce] 目錄。
1. 如果內容不符，請對目錄中的產品進行微幅變更，例如新增空格或句點。
1. 等待重新同步或 [觸發手動重新同步](#resync).

### 同步處理未執行

如果同步未依排程執行或未同步任何專案，請參閱 [知識庫](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-product-recommendations-module-in-magento-commerce.html).

### 同步失敗

如果目錄同步的狀態為 **已失敗**，提交 [支援票證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## 命令列介面 {#resynccmdline}

此 `saas:resync` 命令是 `magento/saas-export` 封裝。 您可以使用以下其中一種方式來安裝此套件： [!DNL Commerce Services] 產品，例如 [[!DNL Product Recommendations]](/help/product-recommendations/install-configure.md) 或 [[!DNL Live Search]](/help/live-search/install.md).

>[!NOTE]
>
> 第一次執行資料同步時，請務必執行 `productattributes` 會先輸入內容，然後輸入 `productoverrides`，然後再執行 `products` 摘要。

命令選項：

```bash
bin/magento saas:resync --feed <feed name> [no-reindex]
```

下表說明 `saas:resync` 引數和說明。

| 引數 | 說明 | 必填？ |
|---| ---| ---|
| `feed` | 指定要重新同步的圖元，例如 `products` | 是 |
| `no-reindex` | 將現有目錄資料重新提交至 [!DNL Commerce Services] 而不重新索引。 如果未指定此引數，命令會在同步資料之前執行完整重新索引。 | 否 |

摘要名稱可以是下列其中一項：

- `products` — 目錄中的產品
- `categories` — 目錄中的類別
- `variants` — 可設定產品的產品變化，例如顏色和大小
- `productattributes` — 產品屬性，例如 `activity`， `gender`， `tops`， `bottoms`、等等
- `productoverrides` — 客戶特定的定價和目錄可見性規則，例如以類別許可權為基礎的規則

當您從命令列觸發資料重新同步時，最多可能需要一小時的時間才會更新資料。

如果您使用 [SaaS價格索引](../price-index/index.md) 並需要重新同步，請執行以下命令：

```bash
bin/magento saas:resync --feed=scopesCustomerGroup
bin/magento saas:resync --feed=scopesWebsite
bin/magento saas:resync --feed=prices
```

### 範例

以下範例會重新索引產品資料，從 [!DNL Commerce] 編目並重新同步至Commerce服務：

```bash
bin/magento saas:resync --feed products
```

如果您不想執行產品的完整重新索引，您可以改為同步已產生的產品資料：

```bash
bin/magento saas:resync --feed products --no-reindex
```
