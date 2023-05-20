---
title: 多個網站和範圍配置
description: 為多個網站和儲存作用域配置儲存和交付方法。
role: User, Admin
level: Intermediate
exl-id: 8939046e-1c26-4380-83be-ff8e074e591d
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# 多個網站和範圍配置

可以設定 [範圍](https://docs.magento.com/user-guide/configuration/scope.html) 用於容納多個網站、商店和商店視圖的幾個元素：

- [管理庫存](https://docs.magento.com/user-guide/catalog/inventory-stock.html) 每個作用域

- 管理 [!DNL Delivery Methods] 每個作用域

您可以將庫存分配到網站或商店範圍。 然後，更新儲存源以設定可用的交付方法（家庭交付、儲存提貨）。

在成功更新配置後，Adobe Commerce店面的產品詳細資訊頁(PDP)上的商店拾取選項只能被選擇用於從允許商店拾取的庫存來源中提供的產品。

## 管理儲存中拾取設定

啟用或禁用 [!UICONTROL In-Store Pickup] 選項 [交貨方法配置](enable-general.md#delivery-methods) 的子菜單。

1. 導航到 **[!UICONTROL Stores > Configuration]**。

1. 選擇要配置的範圍（要儲存的網站）。

1. 選擇範圍後，導航到 **[!UICONTROL Sales > Delivery Methods]**。

1. 禁用或啟用 **[!UICONTROL In-Store Pickup]** 傳遞方法。

您還可以管理此部分中是否全局提供庫邊或店內提貨。

管理 [!UICONTROL In-Store Pickup] 和 [!UICONTROL Delivery Method] 設定。 存在許多其他配置，以便在實施過程中具有完全的靈活性。
