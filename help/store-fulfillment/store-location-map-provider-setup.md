---
title: 儲存位置和映射系統配置
description: 配置距離提供程式以在店面UI中支援商店位置映射。 「商店完成」解決方案要求距離提供商為端到端完成工作流啟用零售商店搜索和其他映射和調度功能。
role: User, Admin
level: Intermediate
exl-id: d09c4652-e2eb-49dc-8c42-2aa9b6be5d6b
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# 儲存位置和映射設定

通過配置 [距離提供者](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html) 以搜尋零售商店位置。

**需求**

在設定程式期間，您會為Google地圖平台提供Google API金鑰。 如果你沒有， [從Google地圖平台產生一個](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html#configure-google-maps).

配置距離提供程式：

1. 從 **[!UICONTROL Stores > General]** 在「管理員」中設定，為「地圖」內容類型新增「Google地圖」整合。

   - 前往 **[!UICONTROL Stores > Configuration  > General > Content Management]**.

   - 將Google API金鑰新增至 **[!UICONTROL Google Maps API Key]** 欄位。

1. 從 **[!UICONTROL Stores > Inventory]** 在「管理員」中，選擇「儲存完成」的距離提供程式。

   - 前往 **[!UICONTROL Stores > Configuration > Catalog > Inventory]**.

   - 展開 **[!UICONTROL Distance Provider for Distance Based SSA]** 區段。

   - 設定 **提供者** to **Google地圖**.

1. 配置 **[!UICONTROL Google Distance Provider]**.

   - 新增 **Google API金鑰**.

   - 設定 **[!UICONTROL Computation Mode]** to `Driving` 和 **[!UICONTROL Value]** to `Distance`
