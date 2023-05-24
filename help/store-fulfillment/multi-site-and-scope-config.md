---
title: 多個網站和範圍設定
description: 設定多個網站的庫存和傳送方法，並儲存範圍。
role: User, Admin
level: Intermediate
exl-id: 8939046e-1c26-4380-83be-ff8e074e591d
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# 多個網站和範圍設定

您可以設定 [範圍](https://docs.magento.com/user-guide/configuration/scope.html) 對於幾個元素，以容納多個網站、商店和商店檢視：

- [管理庫存](https://docs.magento.com/user-guide/catalog/inventory-stock.html) 每個範圍

- 管理 [!DNL Delivery Methods] 每個範圍

您可以將庫存指派給網站或商店範圍。 然後，更新商店來源以設定可用的傳送方法（首頁傳送、商店取貨）。

成功更新設定後，Adobe Commerce店面中產品詳細資料頁面(PDP)上的商店取貨選項只能針對允許商店取貨的庫存來源提供的產品選擇。

## 管理店內取貨設定

啟用或停用 [!UICONTROL In-Store Pickup] 每個網站或商店範圍的選項 [傳遞方法設定](enable-general.md#delivery-methods) 在Admin中。

1. 導覽至 **[!UICONTROL Stores > Configuration]**.

1. 選取要設定的範圍（網站至商店）。

1. 選取範圍後，導覽至 **[!UICONTROL Sales > Delivery Methods]**.

1. 停用或啟用 **[!UICONTROL In-Store Pickup]** 傳遞方法。

您也可以管理此區段中是否有全域可用的路邊或店內取貨。

管理 [!UICONTROL In-Store Pickup] 和 [!UICONTROL Delivery Method] 每個庫存來源的設定。 您有許多其他設定，在實施上擁有完整的彈性。
