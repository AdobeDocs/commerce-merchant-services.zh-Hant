---
title: 存放區位置和對應系統設定
description: 設定距離提供者，以在店面UI中支援商店位置對應。 「商店履行」解決方案需要距離提供者，以啟用零售商店搜尋及其他端對端履行工作流程的對應和排程功能。
role: Admin
level: Intermediate
feature: Shipping/Delivery, Integration, Tools and External Services, Configuration
exl-id: d09c4652-e2eb-49dc-8c42-2aa9b6be5d6b
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# 存放區位置和對應設定

透過設定「 」，啟用「商店履行」的商店位置和對應功能 [距離提供者](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html) 以搜尋零售商店位置。

**需求**

在設定程式期間，您會提供Google Maps平台的Google API金鑰。 如果您沒有， [從Google地圖平台產生一個](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html#configure-google-maps).

設定距離提供者：

1. 從 **[!UICONTROL Stores > General]** 在「管理員」中設定，為「對應」內容型別新增「Google對應」整合。

   - 前往 **[!UICONTROL Stores > Configuration  > General > Content Management]**.

   - 將您的Google API金鑰新增至 **[!UICONTROL Google Maps API Key]** 欄位。

1. 從 **[!UICONTROL Stores > Inventory]** 在「管理員」中設定，選取「商店履行」的距離提供者。

   - 前往 **[!UICONTROL Stores > Configuration > Catalog > Inventory]**.

   - 展開 **[!UICONTROL Distance Provider for Distance Based SSA]** 區段。

   - 設定 **提供者** 至 **Google Map**.

1. 配置設定 **[!UICONTROL Google Distance Provider]**.

   - 新增您的 **Google API金鑰**.

   - 設定 **[!UICONTROL Computation Mode]** 至 `Driving` 和 **[!UICONTROL Value]** 至 `Distance`
