---
title: 商店履行的組態概述
description: 瞭解可用於自訂Store Fulfillment解決方案所提供的延伸履行功能的Admin設定設定型別，以及完成設定的相關說明連結。
role: Admin
level: Intermediate
feature: Shipping/Delivery, Configuration
exl-id: c432791a-94a0-457d-9ed9-8937846ce4f4
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# Store Fulfillment的設定概述

在「Adobe Commerce管理員」中，Walmart Commerce Technologies的「商店履行服務」組態設定會依型別分類。

**依型別儲存履行組態設定**

| **型別** | **說明** | **API可設定** |
|--------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------|
| [一般設定](enable-general.md) | 為Store Fulfillment解決方案、其有效功能及連線至履行服務的憑證設定的一般整合。 | 否 |
| [銷售電子郵件設定](sales-emails.md) | 為簽到程式中傳送的客戶通知設定其他電子郵件範本。 | 否 |
| [商家商店設定](merchant-store-configuration.md) | 將增強的Inventory management來源設定為商家商店。 | 是 |
| [產品庫存管理](product-stock.md) | 設定可供客戶使用的商家股票訊息和功能。 | 是 |
| [Inventory management來源轉移](inventory-stock-transfer.md) | 設定新存貨，將存貨移出預設存貨。 | 是 |
| [多個網站/範圍設定](multi-site-and-scope-config.md) | 為多個網站/商店範圍設定庫存和傳送方法。 | 否 |
| [背景處理序系統組態](background-processes.md) | 設定與履行服務同步資料所使用的背景處理排程。 | 否 |
| [存放區位置和對應設定](store-location-map-provider-setup.md) | 設定使用距離提供者來搜尋零售商店並在SLS地圖中顯示此資訊的功能 | 是 |
| [簽入體驗設定](check-in-experience-setup.md) | 設定入庫程式期間可用的車輛顏色和車輛製造選項 | 是 |
| [使用者設定](user-setup.md) | 管理使用Store Assist應用程式之商店關聯的使用者帳戶、角色和許可權。 範圍。 | 是 |
| [應用程式設定](app-setup.md) | 檢閱完成上線流程所需的Store Assist應用程式的可用設定。 無法從Adobe Commerce管理員設定這些設定。 | 是 |

## 使用設定參考

選取中的型別名稱，檢視每個設定型別的組態參照 _依型別儲存履行組態設定_ 表格。

在每種型別的組態參考中，組態詳細資訊會顯示在含有下列欄標題的表格中：

- **欄位** 指要設定的欄位名稱

- **說明** 提供有關欄位用途和行為的重要細節

- **範圍** 表示設定的Adobe Commerce設定範圍（全域、網站、商店）

- **必填** 值會指出欄位上是否必須設定值

如需技術參考，您還可以找到每個欄位的內部設定路徑。
