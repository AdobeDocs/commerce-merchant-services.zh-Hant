---
title: 商店履行需求
description: 布建和上線需求 [!DNL Store Fulfillment solution].
role: Leader, Admin, Developer
level: Intermediate
feature: Shipping/Delivery, Install
exl-id: f9e05049-5904-4f6c-b45d-9f81fbc76b69
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 2%

---

# Adobe Commerce的商店履行需求

以下小節詳細說明安裝和啟用Adobe Commerce適用的Store Fulfillment解決方案的技術和業務需求。

## 平台與軟體版本需求

此 [!DNL Store Fulfillment] 解決方案適用於下列平台上的Adobe Commerce客戶。

- 雲端基礎結構上的Adobe Commerce (ECE)
- Adobe Commerce內部部署(EE)

Store Fulfillment解決方案與 *軟體相容性* 表格。

**軟體相容性**

| **軟體** | **最低版本** | **最大版本** |
|----------------|---------------------|---------------------|
| Adobe Commerce | 2.4.0 | 2.4.5 |
| Composer | 1.x | 2.x |
| MariaDB | 10.2 | 10.4 |
| MySQL | 5.7 | 8.0 |
| PHP | 7.4 | 8.1 |

如需詳細需求，請參閱Adobe Commerce [系統需求](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html) 在 *Adobe Commerce安裝指南*.

## 商店協助應用程式需求

管理商店取貨訂單的端對端程式，可透過安裝在行動裝置上的「商店協助」應用程式來管理。 這些裝置（由零售商或商店員工使用其個人智慧型手機所提供）必須符合下列要求：

**最低作業系統需求**

- Android 6
- iOS 12

**最低硬體需求**

- 1 GB RAM
- 600 MB可用磁碟空間

## 業務需求

您的企業必須符合下列最低條件，才能實作「商店履行」解決方案：

- 僅限美國企業

- 企業對消費者(B2C)零售商、消費性包裝商品(CPG)製造商直接銷售給消費者(D2C)，或直接銷售給消費者或小型企業的經銷商

- 至少一個實體商店或倉庫

- 使用Inventory management for Adobe Commerce （亦稱為MSI）管理您的產品詳細目錄

- 整合商家庫存的能力

- 在所有支援「商店履行」解決方案的地點，都可使用Wi-Fi：網際網路速度下限3 Mbps

- 商店和倉儲關係人在輪班期間可以存取iOS或Android行動裝置，無論為個人使用者或由商家提供

- 使用「商店履行」解決方案管理的產品必須具有包含SKU或UPC產品代碼的產品屬性
