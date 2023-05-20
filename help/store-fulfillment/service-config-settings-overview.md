---
title: 儲存履行配置概述
description: 瞭解可用於自定義儲存履行解決方案提供的擴展履行功能的管理配置設定類型，以及指向完成配置說明的連結。
role: User, Admin
level: Intermediate
exl-id: c432791a-94a0-457d-9ed9-8937846ce4f4
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# 儲存履行的配置概述

在「Adobe Commerce管理」中，Walmart Commerce Technologies的Store Fulfillment Services的配置設定按類型分類。

**按類型儲存完成配置設定**

| **類型** | **說明** | **API可配置** |
|--------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------|
| [常規配置](enable-general.md) | 為Store Fulfillment解決方案、其活動功能和連接到履行服務的憑據設定常規整合。 | 否 |
| [銷售電子郵件配置](sales-emails.md) | 為在簽入過程中發送的客戶通知設定其他電子郵件模板。 | 否 |
| [商家商店配置](merchant-store-configuration.md) | 將增強的Inventory management來源設定為商店。 | 是 |
| [產品庫存管理](product-stock.md) | 配置可供客戶使用的商家股票消息和功能。 | 是 |
| [Inventory management源傳輸](inventory-stock-transfer.md) | 設定新庫存，將庫存從預設庫存中轉移出來。 | 是 |
| [多個網站/範圍配置](multi-site-and-scope-config.md) | 為多個網站/商店範圍配置庫存和交付方法。 | 否 |
| [後台進程系統配置](background-processes.md) | 配置用於將資料與履行服務同步的後台進程的計畫。 | 否 |
| [儲存位置和映射設定](store-location-map-provider-setup.md) | 配置使用距離提供程式搜索零售商店並在SLS映射中顯示此資訊的功能 | 是 |
| [簽入體驗設定](check-in-experience-setup.md) | 配置車色和車牌選項，這些選項將在簽入過程中可用 | 是 |
| [用戶設定](user-setup.md) | 管理使用Store Assist應用的儲存關聯的用戶帳戶、角色和權限。 範圍。 | 是 |
| [應用程式設定](app-setup.md) | 查看完成登機過程所需的Store Assist應用的可用配置。 無法從Adobe Commerce管理員配置這些設定。 | 是 |

## 使用配置引用

通過在 _按類型儲存完成配置設定_ 的子菜單。

在每種類型的配置引用中，配置詳細資訊顯示在具有以下列標題的表中：

- **欄位** 引用要配置的欄位的名稱

- **說明** 提供了有關該欄位的用途和行為的重要詳細資訊

- **範圍** 指示設定的Adobe Commerce配置範圍（全局、網站、商店）

- **必需** 值指示是否必須在欄位上設定值

有關技術參考，您還可以找到每個欄位的內部配置路徑。
