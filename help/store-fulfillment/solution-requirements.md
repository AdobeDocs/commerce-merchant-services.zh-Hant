---
title: 儲存完成要求
description: 布建和上線的需求 [!DNL Store Fulfillment solution].
role: User, Admin
level: Intermediate
exl-id: f9e05049-5904-4f6c-b45d-9f81fbc76b69
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 2%

---

# Adobe Commerce的儲存完成需求

以下各節詳細說明安裝和啟用適用於Adobe Commerce的商店完成解決方案的技術和業務需求。

## 平台和軟體版本需求

此 [!DNL Store Fulfillment] 解決方案適用於下列平台的Adobe Commerce客戶。

- Adobe Commerce雲端基礎架構(ECE)
- Adobe Commerce駐地(EE)

商店完成解決方案與 *軟體相容性* 表格。

**軟體相容性**

| **軟體** | **最低版本** | **最大版本** |
|----------------|---------------------|---------------------|
| Adobe Commerce | 2.4.0 | 2.4.5 |
| 撰寫器 | 1.x | 2.x |
| MariaDB | 10.2 | 10.4 |
| MySQL | 5.7 | 8.0 |
| PHP | 7.4 | 8.1 |

如需詳細需求，請檢閱Adobe Commerce [系統需求](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html) 在 *Adobe Commerce安裝指南*.

## 商店協助應用程式需求

管理商店提貨訂單的端對端程式通過安裝在移動設備上的商店輔助應用來管理。 這些裝置（由零售商提供或由使用其個人智慧手機的商店員工提供）必須符合下列要求：

**最低作業系統需求**

- Android 6
- iOS 12

**最低硬體需求**

- 1 GB RAM
- 600 MB可用磁碟空間

## 業務需求

您的企業必須符合以下最低標準才能實施商店完成解決方案：

- 僅限美國企業

- 企業對消費者(B2C)零售商、消費者包裝商品(CPG)製造商直接銷售給消費者(D2C)，或直接銷售給消費者或小型企業的經銷商

- 至少一個實體商店或倉庫

- 使用Inventory management for Adobe Commerce（亦稱為MSI）管理您的產品詳細目錄

- 將商戶庫存合併的能力

- 在支援「商店完成」解決方案的所有位置儲存Wi-Fi可用性：最低網際網路速度為3 Mbps

- 商店和倉儲協會在輪班期間，可存取iOS或Android行動裝置，無論是個人或商家提供

- 使用商店完成解決方案管理的產品必須具有包含SKU或UPC產品代碼的產品屬性
