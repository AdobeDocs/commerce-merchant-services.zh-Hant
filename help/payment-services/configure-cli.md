---
title: 命令列組態
description: 安裝後，您可以設定 [!DNL Payment Services] 使用命令列介面(CLI)。
role: Admin, Developer
level: Intermediate
exl-id: 265ab1be-fe52-41f3-85cb-addbc2ddfb17
feature: Payments, Checkout, Configuration, Integration
source-git-commit: d1379bb108f2259051641a7bf77cd8b459fd9cbf
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 0%

---

# 命令列組態

安裝之後 [!DNL Payment Services]，您可從以下位置輕鬆進行設定： [在首頁內](payments-home.md) 或透過命令列介面(CLI)執行。

## 設定資料匯出

[!DNL Payment Services] 結合訂單資料（從匯出） [!DNL Magento Open Source] 和 [!DNL Adobe Commerce] 付款提供者的彙總付款資料，以建立有用的報表。 此 [!DNL Payment Services] 擴充功能會使用索引器有效率地收集報表的所有必要資料。

若要瞭解中使用的資料 [!DNL Payment Services] 報表，請參閱 [訂單付款狀態報表](order-payment-status.md#data-used-in-the-report).

### 設定cron [!DNL Magento Open Source]

如果您想使用 `BY SCHEDULE` 索引模式開啟 [!DNL Magento Open Source]，您必須設定cron。 另請參閱 [設定並執行cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html).

### 設定索引子

訂單資料會匯出並保留在付款服務中，使用兩種索引模式之一：`ON SAVE` （預設）或 `BY SCHEDULE` （建議使用）。

下列索引用於 [!DNL Payment Services]：

| 程式碼 | 名稱 | 說明 |
|    ---    |  ---  |  ---  |
| `sales_order_data_exporter` | 銷售訂單摘要 | 建立訂單資料的索引 |
| `sales_order_status_data_exporter` | 銷售訂單狀態摘要 | 建立銷售訂單狀態資料的索引 |
| `store_data_exporter` | 商店資訊源 | 建立存放區資料的索引 |

若要變更所有三個索引器的索引模式，請執行：

```bash
bin/magento indexer:set-mode schedule sales_order_data_exporter sales_order_status_data_exporter store_data_exporter
```

>[!TIP]
>
>如果您未在指令中指定任何索引子，則所有索引子都會更新為相同的值。 如果要變更特定的索引子，必須在指令中列出它。

若要進一步瞭解手動變更索引器的模式，請參閱 [設定索引子](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html#configure-indexers){target="_blank"} 在開發人員檔案中。 若要瞭解如何在管理員中加以變更，請參閱 [索引管理](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode){target="_blank"} （在核心使用手冊中）。

### 手動重新索引資料

您可以手動重新索引資料，而不是等待資料自動發生。 另請參閱 [重新索引](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html#reindex){target="_blank"} 在 [管理索引子](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html){target="_blank"} 以取得詳細資訊。

時間 `BY SCHEDULE` 模式已設定，系統會追蹤已變更的實體，而cron作業會根據設定的排程更新這些實體的索引。 另請參閱 [從命令列執行cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html#config-cli-cron-group-run) 在 [設定並執行cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html))，瞭解如何使用cron工作手動觸發索引。

### 將重新索引的資料傳送至付款服務

資料編制索引後，會自動傳送至 [!DNL Payment Services]. 您也可以使用此命令手動觸發傳送索引資料的程式：

```bash
bin/magento saas:resync --feed [feedName]
```

使用下列命令選項：

| 命令 | 說明 |
|  ---  |  ---  |
| `bin/magento saas:resync --feed [feedName]` | 執行指定摘要的重新索引，並將其傳送至對應的服務 |
| `bin/magento saas:resync --no-reindex` | 略過索引化並從索引傳送未同步的資料 |

此 `--feed` 引數可讓您指定要傳送的摘要：

| 摘要 | 說明 |
|  ---  |  ---  |
| `paymentServicesOrdersProduction` | 生產模式中的訂單摘要 |
| `paymentServicesOrdersSandbox` | 沙箱模式下的訂單摘要 |
| `paymentServicesOrderStatusesProduction` | 生產模式中的訂單狀態 |
| `paymentServicesOrderStatusesSandbox` | 在沙箱模式中的訂單狀態 |
| `paymentServicesStoresProduction` | 以生產模式儲存 |
| `paymentServicesStoresSandbox` | 以沙箱模式儲存 |

報告所需的所有資料都會傳送到 [!DNL Payment Services] 如果已設定並安裝cron，則會自動進行。 您也可以手動觸發傳送cron資料至的程式 [!DNL Payment Services].

```bash
bin/magento cron:run --group payment_services_data_export
```

若要進一步瞭解重新索引和索引子，請參閱 [管理索引子](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html) 開發人員檔案中的主題。

## 設定L2/L3處理

[!DNL Payment Services] 可以處理卡片付款交易的層級2與層級3資料，以提供商戶的其他資訊。

>[!WARNING]
>
> 透過PayPal與第2層及第3層處理功能整合，僅適用於美國商家。 另請參閱 [付款處理](https://developer.paypal.com/docs/checkout/advanced/processing/){target=_blank} 如需詳細資訊，請參閱PayPal開發人員檔案。

如果您想要使用L2/L3處理資料 [!DNL Payment Services]，或如果您有任何問題，請聯絡您的 [!DNL Payment Services] 客戶經理。

瞭解中使用的L2和L3處理 [!DNL Payment Services]，請參閱 [第2級和第3級處理](levels-card-payment-transactions.md).
