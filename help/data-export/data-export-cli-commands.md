---
title: SaaS資料匯出命令列介面
description: 瞭解如何使用命令列介面命令來管理的摘要和程式 [!DNL data export extension] 用於Adobe Commerce SaaS服務。
recommendations: noCatalog
exl-id: f360d920-7d02-4317-8c56-c7d4c4ed2ff2
source-git-commit: af9de40a717d2cb55a5f42483bd0e4cbcd913f64
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---

# SaaS資料匯出命令列介面參考

開發人員和系統管理員可使用管理SaaS資料匯出的同步作業。 [Adobe Commerce命令列工具](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/config-cli) (CLI)。 此 `saas:resync` 命令包含在 `magento/saas-export` 封裝。

Adobe不建議使用 `saas:resync` 定期執行指令。 使用指令的典型情況如下：

- 初始同步
- 此 [SaaS資料空間ID](https://experienceleague.adobe.com/en/docs/commerce-admin/config/services/saas) 已變更，且您需要將資料同步至新資料空間。
- 疑難排解

## 初始同步

>[!NOTE]
>如果您使用Live Search或Product Recommendations，就不需要執行初始同步。 此程式會在您將服務連線至您的Commerce執行個體後自動啟動。

當您觸發 `saas:resync` 從命令列（視目錄大小而定）更新資料可能需要幾分鐘到幾小時的時間。

對於初始同步，Adobe建議以下列順序執行命令：

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

## 命令範例

使用前 `saas:resync` 命令，檢閱 [選項說明](#command-options).

- 執行實體摘要的完整重新同步。

  ```
  bin/magento saas:resync --feed='<FEED_NAME>' 1
  ```

  已成功匯出的摘要不會重新同步。

- 完全重新同步指定的摘要和清理資料

  ```
  bin/magento saas:resync --feed='FEED_NAME' --cleanup-feed
  ```

  僅在執行 [!DNL Data Space ID Cleanup] 作業。

- 如需立即匯出摘要，請重新傳送所有資料至連線的Commerce服務，而不會截斷摘要表格中的索引資料

  ```
   bin/magento saas:resync --feed='FEED_NAME' --no-reindex
  ```

- 列出可用的命令和選項以及說明。

  ```
  bin/magento saas:resync --help
  ```

## 命令選項

下列選項可用於管理 `saas:resync` 操作。

>[!NOTE]
>
>此 `saas:resync` command也支援進階選項，藉由增加批次大小和新增多執行緒處理來改善資料匯出命令。 另請參閱 [自訂匯出處理](customize-export-processing.md).

### `feed`

此必要選項指定要重新同步哪個進給圖元，例如 `products`.

此 `feed` 選項值可包含任何可用的實體摘要：

- `products`：產品資料摘要
- `productAttributes`：產品屬性資料摘要
- `categories`：類別資料摘要
- `variants`：可設定的產品變數資料摘要
- `prices`：產品價格資料摘要
- `categoryPermissions`：類別許可權資料摘要
- `productOverrides`：產品許可權資料摘要
- `inventoryStockStatus`：庫存狀態資料摘要
- `scopesWebsite`：有商店和商店檢視的網站資料摘要
- `scopesCustomerGroup`：客戶群組資料摘要
- `orders`：銷售訂單資料摘要

視何者而定 [Commerce服務](../landing/saas.md) 已安裝，則可能有不同的摘要集可用於 `saas:resync` 命令。

### `no-reindex`

此選項會將現有的目錄資料重新提交至 [!DNL Commerce Services] 而不重新索引。 如果未指定此選項，則命令會在同步資料之前執行完整重新索引。

此選項的行為取決於摘要是否匯出 [舊版或立即匯出模式](data-synchronization.md#synchronization-modes)

- 對於舊版匯出摘要，同步程式不會截斷摘要表格中的索引資料。 而是將所有資料重新傳送至Adobe Commerce服務。
- 對於立即匯出摘要，如果指定，則會忽略此選項。 對於這些摘要，重新同步程式不會截斷索引，而只會重新同步更新或先前失敗的專案。

### `cleanup`

此選項會在同步之前清除摘要索引器表格。 指定後，SaaS資料匯出會針對指定的摘要執行完全重新同步，並清除摘要表格中的所有現有資料。

Adobe建議只有在執行 [!DNL Data Space ID Cleanup] 作業。

>[!WARNING]
>
>**請勿定期使用此選項**. 這可能會導致Adobe Commerce Services出現資料同步問題。 例如， `delete product event` 可能不會傳播至Adobe Commerce服務，如果 `cleanup` 選項時才會使用。

## 疑難排解

如果您在連線的Commerce服務中未看到預期的資料，請透過檢查資料匯出錯誤記錄檔並使用 `saas:resync` 命令與環境變數一起使用以檢閱裝載和效能分析工具資料。 另請參閱 [檢閱記錄檔並進行疑難排解](troubleshooting-logging.md).
