---
title: "[!DNL SaaS Data Export Guide]"
description: 「瞭解如何使用 [!DNL data export] Adobe Commerce SaaS服務的擴充功能，可在Adobe Commerce與連線的Commerce服務之間同步資料。」
role: Admin, Developer
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# [!DNL SaaS Data Export] 指南

[!DNL SaaS data export] 透過最佳化Adobe Commerce執行個體和連線的Commerce服務之間的資料同步，來改善前端效能。 將Live Search、產品Recommendations或目錄服務新增至Adobe Commerce安裝時， [!DNL Data export] 擴充功能會自動安裝。

SaaS資料匯出會收集和匯出各種型別的資料，稱為 _摘要_，會彙總特定型別的資訊。 視安裝的Commerce服務而定，SaaS資料匯出摘要包含：

- **目錄實體摘要** 彙總產品資料。 資料包括產品、產品屬性、產品價格、產品變化、類別、類別許可權和產品許可權。
- 此 **範圍摘要** 彙總客戶群組、網站、商店和商店檢視的資料。
- 此 **銷售訂單摘要** 彙總訂單資料，包括其相關實體，如商業發票、出貨、銷退折讓單等。
- 此 **多來源庫存摘要** 彙總存貨狀態料號的相關資料。

資料匯出擴充功能支援數種方法，用以啟動及管理資料同步程式。

- **從Admin或命令列手動同步**

   - 此 [資料管理儀表板](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard) 在Commerce中，「管理員」會提供同步狀態的圖形檢視。 您可以使用控制面板來執行完整的重新同步(_完全同步_)。 不過，Adobe建議僅在第一次將Adobe Commerce連線至Commerce服務時，才執行完整同步。 另請參閱 [同步化程式](data-synchronization.md).

   - 此 [Adobe Commerce命令列工具](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/config-cli) (CLI)提供同步特定摘要的命令，並包含自訂摘要處理的其他選項。

- **與cron工作自動同步**

   - [部分資料同步](data-synchronization.md#partial-synchronization-with-cron-jobs) — 當Commerce管理員使用者更新實體時，Cron作業會觸發部分資料同步。 資料匯出程式只會將這些更新傳送至連線的Commerce服務。 部分同步程式以MView機製為基礎，不需要管理員使用者或系統整合者執行任何動作。

   - [自動重試同步處理錯誤](data-synchronization.md#failed-items-sync-for-error-recovery) — 在資料同步處理期間發生錯誤時，Cron作業會觸發同步處理程式的自動重試。

- **匯出排程和效能**

   - 開發人員和系統整合經銷商能估計SaaS資料匯出所需的時間，以便在Adobe Commerce和連線的服務之間同步資料。 此預估可協助排程資料匯出處理，以防止網站中斷。 另請參閱 [預估資料量和傳輸時間](estimate-data-volume-sync-time.md).

   - 在需要更快速進行同步的情況下，SaaS資料匯出可提供自訂選項來改善匯出處理效能。 另請參閱 [改善資料匯出效能](customize-export-processing.md).

- **追蹤資料匯出活動並進行疑難排解** — 在同步和索引化程式期間，使用資料匯出和saas-export記錄檔來檢閱同步狀態和摘要裝載。 另請參閱 [記錄與疑難排解](troubleshooting-logging.md).



