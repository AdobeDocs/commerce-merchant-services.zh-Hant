---
title: 命令行配置
description: 安裝後，您可以設定 [!DNL Payment Services] 使用命令行介面(CLI)。
role: Admin, Developer
level: Intermediate
exl-id: 265ab1be-fe52-41f3-85cb-addbc2ddfb17
source-git-commit: 817a01e98876bddf5f41a253501984539b3351cd
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# 命令行配置

安裝後 [!DNL Payment Services]，您可以輕鬆從 [在家裡](payments-home.md) 或通過命令行介面(CLI)。

## 設定資料匯出

[!DNL Payment Services] 合併從導出的訂單資料 [!DNL Magento Open Source] 和 [!DNL Adobe Commerce] 與支付提供商的匯總付款資料建立有用的報表。 此 [!DNL Payment Services] 擴充功能使用索引器來有效收集報表的所有必要資料。

了解中使用的資料 [!DNL Payment Services] 報表，請參閱 [訂單付款狀態報表](order-payment-status.md#data-used-in-the-report).

### 設定cron [!DNL Magento Open Source]

如果您想使用 `BY SCHEDULE` 索引模式開啟 [!DNL Magento Open Source]，您必須設定cron。 請參閱 [設定並執行cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html).

### 設定索引器

訂單資料使用兩種索引模式之一導出並保存在支付服務中 — `ON SAVE` （預設）或 `BY SCHEDULE` （建議）。

下列索引適用於 [!DNL Payment Services]:

| 程式碼 | 名稱 | 說明 |
|    ---    |  ---  |  ---  |
| `sales_order_data_exporter` | 銷售訂單摘要 | 建立訂單資料索引 |
| `sales_order_status_data_exporter` | 銷售訂單狀態摘要 | 建立銷售訂單狀態資料索引 |
| `store_data_exporter` | 儲存摘要 | 建立儲存資料索引 |

要更改所有三個索引器的索引模式，請運行：

```bash
bin/magento indexer:set-mode schedule sales_order_data_exporter sales_order_status_data_exporter store_data_exporter
```

>[!TIP]
>
>如果命令中未指定任何索引器，則所有索引器都將更新為相同的值。 如果要更改特定索引器，必須在命令中列出它。

要了解有關手動更改索引器模式的詳細資訊，請參閱 [配置索引器](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html#configure-indexers){target="_blank"} in the developer documentation. To learn how to change it in the Admin, see [Index management](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode){target="_blank"} 中。

### 手動重新索引資料

您可以手動重新索引資料，而不必等待資料自動發生。 請參閱 [重新索引](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html#reindex){target="_blank"} in [Manage the Indexers](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html){target="_blank"} 以取得更多資訊。

當 `BY SCHEDULE` 模式被設定，系統跟蹤已更改的實體，並且cron作業根據設定的計畫更新它們的索引。 請參閱 [從命令列執行cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html#config-cli-cron-group-run) in [設定並執行cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html))，了解如何使用cron工作手動觸發索引。

### 將重新索引的資料發送到支付服務

資料編列索引後，會自動傳送至 [!DNL Payment Services]. 您也可以使用以下命令手動觸發傳送索引資料的程式：

```bash
bin/magento saas:resync --feed [feedName]
```

使用以下命令選項：

| 命令 | 說明 |
|  ---  |  ---  |
| `bin/magento saas:resync --feed [feedName]` | 執行指定摘要的重新索引，並將其傳送至對應的服務 |
| `bin/magento saas:resync --no-reindex` | 跳過索引並從索引發送未同步的資料 |

此 `--feed` 參數可讓您指定要傳送的摘要：

| 摘要 | 說明 |
|  ---  |  ---  |
| `paymentServicesOrdersProduction` | 在「生產」模式中傳送訂單 |
| `paymentServicesOrdersSandbox` | 在沙箱模式中傳送訂單 |
| `paymentServicesOrderStatusesProduction` | 在「生產」模式下的訂單狀態 |
| `paymentServicesOrderStatusesSandbox` | 在沙箱模式中排序狀態 |
| `paymentServicesStoresProduction` | 以生產模式儲存 |
| `paymentServicesStoresSandbox` | 在沙箱模式中儲存 |

報表所需的所有資料都會傳送至 [!DNL Payment Services] 如果已設定並安裝cron，則會自動執行。 您也可以手動觸發將cron資料傳送至的程式 [!DNL Payment Services].

```bash
bin/magento cron:run --group payment_services_data_export
```

若要進一步了解重新索引和索引器，請參閱 [管理索引器](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html) 開發人員檔案中的主題。
