---
title: 儲存位置和映射系統配置
description: 配置距離提供程式以支援店面UI中的商店位置映射。 應用商店履行解決方案需要一個距離提供商來啟用零售商店搜索以及端到端履行工作流的其他映射和計畫功能。
role: User, Admin
level: Intermediate
source-git-commit: 42b0118b427b1e04186793b4a57c058bc1cabdd4
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---


# 儲存位置和映射設定

通過配置 [距離提供商](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html) 以搜索零售商店位置。

**要求**

在配置過程中，您為Google地圖平台提供了GoogleAPI密鑰。 如果你沒有， [從Google地圖平台生成一個](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html#configure-google-maps)。

要配置距離提供程式：

1. 從 [!UICONTROL Stores > General] 在管理中，為映射內容類型添加Google映射整合。

   - 轉到 **[!UICONTROL Stores > Configuration  > General > Content Management]**。

   - 將您的GoogleAPI密鑰添加到 **[!UICONTROL Google Maps API Key]** 的子菜單。

1. 從 [!UICONTROL Stores > Inventory] 在Admin中，選擇Store Fulfilment的距離提供程式。

   - 轉到 **[!UICONTROL Stores > Configuration > Catalog > Inventory]**。

   - 展開 **[!UICONTROL Distance Provider for Distance Based SSA]** 的子菜單。

   - 設定 **提供程式** 至 **Google地圖**。

1. 配置 **[!UICONTROL Google Distance Provider]**。

   - 添加 **GoogleAPI密鑰**。

   - 設定 **[!UICONTROL Computation Mode]** 至 `Driving` 和 **[!UICONTROL Value]** 至 `Distance`
