---
title: 儲存完成配置概述
description: 了解可用於自訂商店完成解決方案提供的擴展完成功能的管理員配置設定類型，以及完成配置說明的連結。
role: User, Admin
level: Intermediate
exl-id: c432791a-94a0-457d-9ed9-8937846ce4f4
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# 商店完成配置概述

在Adobe Commerce管理員中，由Walmart Commerce Technologies提供的商店完成服務組態設定會依類型分類。

**按類型儲存完成配置設定**

| **類型** | **說明** | **API可設定** |
|--------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------|
| [一般配置](enable-general.md) | 為Store Fullment解決方案、其活動功能以及連接到Fullment Services的憑據設定的常規整合。 | 否 |
| [銷售電子郵件配置](sales-emails.md) | 為簽入過程中發送的客戶通知設定其他電子郵件模板。 | 否 |
| [商家商店配置](merchant-store-configuration.md) | 將增強的Inventory management來源設為商店。 | 是 |
| [產品庫存管理](product-stock.md) | 配置商家庫存報文傳送和客戶可用的功能。 | 是 |
| [Inventory management來源轉移](inventory-stock-transfer.md) | 設定新庫存，將庫存轉移出預設庫存。 | 是 |
| [多個網站/範圍配置](multi-site-and-scope-config.md) | 為多個網站/商店範圍配置庫存和傳送方法。 | 否 |
| [後台進程系統配置](background-processes.md) | 配置用於與履行服務同步資料的後台進程的計畫。 | 否 |
| [儲存位置和映射設定](store-location-map-provider-setup.md) | 配置使用距離提供程式搜索零售商店和在SLS映射中顯示此資訊的能力 | 是 |
| [簽入體驗設定](check-in-experience-setup.md) | 配置車的顏色，並使選項在簽入過程中可用 | 是 |
| [使用者設定](user-setup.md) | 管理使用Store Assist應用程式的Store關聯的使用者帳戶、角色和權限。 範圍。 | 是 |
| [應用程式設定](app-setup.md) | 檢閱完成上線程式所需的商店協助應用程式可用設定。 無法從Adobe Commerce管理員設定這些設定。 | 是 |

## 使用配置參考

通過在 _按類型儲存完成配置設定_ 表格。

在每種類型的配置參考中，配置詳細資訊顯示在具有以下列標題的表中：

- **欄位** 指要設定的欄位名稱

- **說明** 提供有關欄位用途和行為的重要詳細資訊

- **範圍** 指出設定的Adobe Commerce設定範圍（全域、網站、商店）

- **必填** 值指示是否必須在欄位上設定值

如需技術參考，您也可以找到每個欄位的內部設定路徑。
