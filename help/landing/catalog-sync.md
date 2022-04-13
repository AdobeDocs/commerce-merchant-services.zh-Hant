---
title: 目錄同步
description: 瞭解如何從中導出產品資料 [!DNL Commerce] 伺服器 [!DNL Commerce Services] 持續更新服務。
exl-id: 19d29731-097c-4f5f-b8c0-12f9c91848ac
source-git-commit: 6d0c7c749fe90c7c204afe47446f3483d8668b53
workflow-type: tm+mt
source-wordcount: '860'
ht-degree: 0%

---

# 目錄同步

Adobe Commerce和Magento Open Source使用索引器將目錄資料編譯成表。 進程由 [事件](https://docs.magento.com/user-guide/system/index-management-events.html) 例如產品價格或庫存水準的更改。

目錄同步進程每小時運行一次，以允許 [!DNL Commerce] 服務以使用目錄資料。 目錄同步從 [!DNL Commerce] 伺服器 [!DNL Commerce] 務，使服務保持最新。 比如說， [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) 需要當前的目錄資訊來準確返回具有正確名稱、定價和可用性的建議。 您可以使用 _目錄同步_ 用於觀察和管理同步過程的儀表板，或 [命令行介面](#resynccmdline) 觸發目錄同步並重新索引產品資料，使用 [!DNL Commerce] 服務。

>[!NOTE]
>
> 使用 _目錄同步_ 儀表板或命令行介面，必須 [API密鑰和SaaS資料空間已配置](saas.md)。

## 訪問目錄同步儀表板

要訪問目錄同步儀表板，請選擇 **系統** > _資料傳輸_ > **目錄同步**。

使用 **目錄同步** 您可以使用的儀表板：

- 查看同步狀態(**正在進行**。 **成功**。 **失敗**)
- 查看同步的產品總數（如果成功）
- 搜索同步的產品以查看其當前狀態
- 按名稱、SKU等搜索儲存目錄
- 查看JSON中同步的產品詳細資訊以幫助診斷同步差異
- 重新啟動同步進程

### 上次同步

報告的同步狀態為：

- **成功**  — 顯示同步成功的日期和時間以及更新的產品數
- **失敗**  — 顯示嘗試同步的日期和時間
- **正在進行**  — 顯示上次成功同步的日期和時間

>[!NOTE]
>
> 目錄同步進程每小時自動運行一次。 但是，如果您沒有在店面看到產品，或者這些產品沒有反映您最近所做的更改，您可以解決 [目錄同步問題](#resolvesync)。

### 已同步的產品

顯示從您的 [!DNL Commerce] 目錄。 初始同步後，您應該只希望同步更改的產品。

## 重新同步 {#resync}

如果必須在每小時計畫同步之前啟動目錄的重新同步，則可以強制執行重新同步。

>[!NOTE]
>
> 強制重新同步會觸發整個產品目錄的重新同步，這會增加硬體資源的負載。

1. 從 _目錄同步_ 儀表板，選擇 **設定**。

   的 _目錄同步設定_ 的子菜單。

1. 在 _重新同步資料_ ，按一下 [!UICONTROL Resync]。

   [!DNL Commerce] 在下一個計畫的同步窗口期間同步目錄。 根據目錄的大小，此操作可能需要很長時間。

## 已同步的目錄產品

的 **已同步的目錄產品** 表格顯示以下資訊。

| 欄位 | 說明 |
|---|---|
| ID | 產品的唯一標識符 |
| 名稱 | 產品的店面名稱 |
| 類型 | 標識產品類型，如簡單、可配置、可下載等 |
| 上次導出時間 | 上次從目錄成功導出產品的日期 |
| 上次修改時間 | 上次在目錄中修改產品的日期 |
| SKU | 顯示產品的庫存單位 |
| 價格 | 產品價格 |
| 可見性 | 產品的可視性設定(如 [!DNL Commerce] 目錄 |

## 解決目錄同步問題 {#resolvesync}

觸發資料重新同步時，資料更新和反映在UI元件（如建議單元）中可能需要一個小時。 但是，如果在等待一小時後，您仍然注意到目錄與商店前面顯示的內容不一致，或者目錄同步失敗，請參閱以下內容：

### 資料差異

1. 在搜索結果中顯示有關產品的詳細視圖。
1. 複製JSON輸出，並驗證內容是否與您在 [!DNL Commerce] 目錄。
1. 如果內容不匹配，請對目錄中的產品進行微小更改，例如添加空格或句點。
1. 等待重新同步或 [觸發手動重新同步](#resync)。

### 同步未運行

如果同步未按計畫運行或未同步任何內容，請參閱 [知識庫](https://support.magento.com/hc/en-us/articles/360042224851)。

### 同步失敗

如果目錄同步的狀態為 **失敗**，提交 [支援票證](https://support.magento.com/hc/en-us/articles/360019088251)。

## 命令行介面 {#resynccmdline}

的 `saas:resync` 命令是 `magento/saas-export` 檔案。 您可以使用 [!DNL Commerce Services] 產品，如 [[!DNL Product Recommendations]](/help/product-recommendations/install-configure.md) 或 [[!DNL Live Search]](/help/live-search/install.md)。

>[!NOTE]
>
> 從命令行觸發資料重新同步時，資料更新可能需要一個小時。

命令選項：

```bash
bin/magento saas:resync --feed <feed name> [no-reindex]
```

下表介紹了 `saas:resync` 參數和說明。

| 參數 | 說明 | 需要？ |
|---| ---| ---|
| `feed` | 指定要重新同步的實體，如 `products` | 是 |
| `no-reindex` | 將現有目錄資料重新提交到 [!DNL Commerce Services] 不重新編製索引。 如果未指定此參數，則命令將在同步資料之前運行完全重新索引。 | 否 |

源名稱可以是下列選項之一：

- `products` — 目錄中的產品
- `categories` — 目錄中的類別
- `variants` — 可配置產品的產品變體，如顏色和大小
- `productattributes` — 產品屬性，如 `activity`。 `gender`。 `tops`。 `bottoms`等等
- `productoverrides` — 特定於客戶的定價和目錄可見性規則，如基於類別權限的規則

### 示例

下面的示例從 [!DNL Commerce] 將其重新同步到Commerce服務：

```bash
bin/magento saas:resync --feed products
```

如果您不想運行產品的完整重新索引，則可以同步已生成的產品資料：

```bash
bin/magento saas:resync --feed products --no-reindex
```
