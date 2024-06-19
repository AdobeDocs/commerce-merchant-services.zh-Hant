---
title: 改善SaaS資料匯出效能
description: 「瞭解如何使用多執行緒資料匯出模式，改善Commerce服務的SaaS資料匯出效能。」
role: Admin, Developer
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 0%

---

# 改善SaaS資料匯出效能

**多執行緒資料匯出模式** 將摘要資料分割為批次並平行處理，加速匯出程式。

開發人員或系統整合經銷商可以使用多執行緒資料匯出模式，而不是預設的單執行緒模式，來改善效能。 在單執行緒模式中，摘要提交程式不會平行化。 此外，由於設定了預設限制，所有使用者端都限製為僅使用一個執行緒。 在大多數情況下，不需要自訂設定。

## 使用多執行緒模式的考量事項

使用資料匯出服務時，您想要在確保精確同步的同時最佳化效能。
Adobe建議使用資料擷取的預設設定，這通常符合Commerce商家的同步需求。 但是，在某些情況下，自訂可能會加快處理時間。

在決定是否自訂資料匯出設定時，請考慮下列關鍵因素：

- **初始同步** — 評估產品和 [預估資料量和傳輸時間](estimate-data-volume-sync-time.md) 根據預設設定。 請自問：您上線Commerce服務後，可以等待此初始資料同步嗎？

- **新增商店檢視或網站** — 如果您打算在開機後新增具有相同產品數的商店檢視或網站，請預估資料量和傳輸時間。 判斷使用預設設定是否可接受同步化時間，或是是否需要多執行緒處理。

- **一般匯入** — 預測定期匯入，例如價格更新或庫存狀態變更。 評估這些更新是否可以在可接受的時間範圍內套用，或是否需要更快速的處理。

- **產品權重** — 考慮您的產品是輕量型還是重型。 如果產品說明或屬性誇大產品大小，請相應地調整批次大小。

請記住，周詳的規劃（包括估計資料量和同步時間）通常可免除自訂需求。 根據這些預估值，排程摘要擷取作業，以獲得最佳結果。

>[!NOTE]
>
>Adobe建議在使用多執行緒處理時務必謹慎。 此功能是尚在改善的早期存取功能。 如果您設定多執行緒以提升效能，可以觸發內含的Adobe Commerce Services護欄，以防止在資料擷取期間誤用系統。 這些護欄也會限制使用者觸發可能使系統過載的同步化變更。 觸發護欄時，請求會遭到封鎖，系統傳回429錯誤。 如果您遇到這些錯誤，請調整您的設定，並提交支援票證以尋求協助。

## 設定多執行緒

所有專案皆支援多執行緒模式 [同步化方法](data-synchronization.md#synchronization-process) — 完全同步、部分同步和失敗專案同步。 若要設定多執行緒，請指定同步處理期間要使用的執行緒數目和批次大小。

- `threadCount` 是啟動以處理實體的執行緒數目。 預設 `threadCount` 是 `1`.
- `batchSize` 是在一個反複專案中處理的實體數目。 預設 `batchSize` 是 `100` 除了價格摘要以外的所有摘要的記錄。 對於價格摘要，預設值為 `500` 記錄。

您可以在執行resync命令時將多執行緒設定為暫存選項，或將多執行緒組態新增到Adobe Commerce應用程式組態中。

>[!NOTE]
>
>請確定SaaS資料匯出的效能符合為消費者端使用者端定義的速率限制。

### 在執行階段設定多執行緒

當您從命令列執行完整同步命令時，請透過新增 `threadCount` 和 `batchSize` CLI指令的選項。

```
bin/magento saas:resync --feed=products --threadCount=2 --batchSize=200
```

命令列上指定的選項會覆寫Adobe Commerce應用程式中指定的資料匯出設定 `config.php` 檔案。

### 將多執行緒新增至Commerce設定

若要使用多執行緒處理所有資料匯出作業，系統整合經銷商或開發人員可以在Commerce應用程式設定中修改每個摘要的執行緒數目和批次大小。

若要套用這些變更，可將自訂值新增至 [系統區段](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/files/config-reference-configphp#system) 設定檔中， `app/etc/config.php`.

**範例：設定產品與價格的多執行緒**

```php
<?php
return [
    'system' => [
        'default' => [
            'commerce_data_export' => [
                'feeds' => [
                    'products' => [
                        'batch_size' => 100,
                        'thread_count' => 2,
                    ],
                    'prices' => [
                        'batch_size' => 400,
                        'thread_count' => 4,
                    ]
                ]
            ],
//   ...
```
