---
title: 命令行配置
description: 安裝後，您可以配置 [!DNL Payment Services] 使用命令行介面(CLI)。
role: Admin, Developer
level: Intermediate
exl-id: 265ab1be-fe52-41f3-85cb-addbc2ddfb17
source-git-commit: 9596815e31402f23b399b223f3221074331c1773
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# 命令行配置

安裝後 [!DNL Payment Services]，您可以輕鬆地從 [在家裡](payments-home.md) 或通過命令行介面(CLI)。

## 配置資料導出

[!DNL Payment Services] 合併從中導出的訂單資料 [!DNL Magento Open Source] 和 [!DNL Adobe Commerce] 使用付款提供方的聚合付款資料建立有用報表。 的 [!DNL Payment Services] extension使用索引器來高效地收集報表的所有必要資料。

瞭解中使用的資料 [!DNL Payment Services] 報告，請參閱 [訂單付款狀態報表](order-payment-status.md#data-used-in-the-report)。

### 在上配置cron [!DNL Magento Open Source]

如果您想使用 `BY SCHEDULE` 索引模式 [!DNL Magento Open Source]，必須配置cron。 請參閱 [配置並運行cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html)。

### 設定索引器

訂單資料使用兩種索引模式之一導出並保留在付款服務中。`ON SAVE` （預設）或 `BY SCHEDULE` （推薦）。

以下索引用於 [!DNL Payment Services]:

| 代碼 | 名稱 | 說明 |
|    ---    |  ---  |  ---  |
| `sales_order_data_exporter` | 銷售訂單源 | 建立訂單資料索引 |
| `sales_order_status_data_exporter` | 銷售訂單狀態饋送 | 生成銷售訂單狀態資料的索引 |
| `store_data_exporter` | 儲存源 | 建立儲存資料索引 |

要更改所有三個索引器的索引模式，請運行：

```bash
bin/magento indexer:set-mode schedule sales_order_data_exporter sales_order_status_data_exporter store_data_exporter
```

>[!TIP]
>
>如果在命令中未指定任何索引器，則所有索引器都將更新為相同的值。 如果要更改特定索引器，必須在命令中列出它。

要瞭解有關手動更改索引器模式的詳細資訊，請參見 [配置索引器](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html#configure-indexers)開發人員文檔中的{target=&quot;_blank&quot;}。 要瞭解如何在管理員中更改它，請參見 [索引管理](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode)核心使用手冊中的{target=&quot;_blank&quot;}。

### 手動重新索引資料

您可以手動重新編製資料索引，而不是等待資料自動發生。 請參閱 [重新索引](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html#reindex){target=&quot;_blank&quot; [管理索引器](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html){target=&quot;_blank&quot;}獲取詳細資訊。

當 `BY SCHEDULE` 模式被設定，系統跟蹤已更改的實體，並且cron作業基於設定的計畫更新它們的索引。 請參閱 [從命令行運行cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html#config-cli-cron-group-run) 在 [配置並運行cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html))，瞭解如何使用cron作業手動觸發索引。

### 將重新索引的資料發送到付款服務

在對資料編製索引後，它將自動發送到 [!DNL Payment Services]。 您還可以使用以下命令手動觸發發送索引資料的過程：

```bash
bin/magento saas:resync --feed [feedName]
```

使用以下命令選項：

| 命令 | 說明 |
|  ---  |  ---  |
| `bin/magento saas:resync --feed [feedName]` | 執行指定源的重新索引並將其發送到相應的服務 |
| `bin/magento saas:resync --no-reindex` | 跳過索引並從索引發送未同步的資料 |

的 `--feed` 參數允許您指定要發送的源：

| 進紙 | 說明 |
|  ---  |  ---  |
| `paymentServicesOrdersProduction` | 在生產模式下訂單饋送 |
| `paymentServicesOrdersSandbox` | 在沙盒模式下訂單饋送 |
| `paymentServicesOrderStatusesProduction` | 生產模式下的訂單狀態 |
| `paymentServicesOrderStatusesSandbox` | 在沙盒模式下訂購狀態 |
| `paymentServicesStoresProduction` | 以生產模式儲存 |
| `paymentServicesStoresSandbox` | 在沙盒模式下儲存 |

報告所需的所有資料都發送到 [!DNL Payment Services] 如果配置並安裝了cron，則自動。 您還可以手動觸發向 [!DNL Payment Services]。

```bash
bin/magento cron:run --group payment_services_data_export
```

要瞭解有關重新索引和索引器的詳細資訊，請參閱 [管理索引器](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html) 開發人員文檔中的主題。
