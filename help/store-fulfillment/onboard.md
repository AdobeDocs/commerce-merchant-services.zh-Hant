---
title: 入門概述
description: '"連接 [!DNL Commerce] 實例 [!DNL Store Fulfillment Manager] 完成幾個單車步驟。」'
role: User, Admin
level: Intermediate
exl-id: f8e403ac-9bbd-4ea2-b209-9b1a8d1e32a2
source-git-commit: 26d0ddbcbe648b336d527788668caef1f8e688ed
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 入門概述

通過在您的Commerce實例上安裝擴展並配置API連接實現板載儲存完成。 這些連接可在您的Commerce實例、用於庫存管理的第三方系統和Store Assist應用之間實現通信和資料同步。

完成登錄後，請通過Commerce Admin配置和管理解決方案

![[!DNL Store Fulfillment Service] 管理視圖中的配置](assets/store-fulfillment-admin-home.png)

## 入門概述

1. 為Adobe Commerce安裝Walmart Technologies的Store Fullimfilling。

1. 從管理員處啟用解決方案並完成整合的一般配置、其活動功能，並完成入門表單以連接到履行服務。

1. 配置傳遞方法。

1. 將源設定為物理儲存並配置目錄中的產品。

1. 選擇並配置電子郵件模板，以管理線上購買、在店取貨(BOPIS)交易的客戶通信。

1. 為Store Assist應用建立用戶和角色。

1. 配置後台進程的計畫，以將資料同步到履行服務。

## 要求

安裝、部署和使用解決方案必須滿足以下要求。

* **商業帳戶資訊** — 安裝 [!DNL Channel Manager] 需要 [商業帳戶](https://docs.magento.com/user-guide/magento/magento-account.html){target=&quot;_blank&quot;}。 您需要具有「所有者」或「管理員」訪問權限的帳戶ID和憑據 [!DNL Adobe Commerce] 實例。

* 對於 [!DNL Adobe Commerce] 在雲基礎架構項目上，軟體安裝程式必須具有對雲項目的管理員權限。 請參閱 [管理用戶訪問](https://devdocs.magento.com/cloud/project/user-admin.html)。

* **通過Walmart Technologies軟體存檔（.zip檔案）訪問Store Fulfillment以安裝Store Fulfilment解決方案** — 在啟動和啟用過程中，您的客戶客戶代表將提供對安裝檔案的下載訪問。

* **使用Composer和[!DNL Commerce CLI]** — 請參閱 [常規CLI安裝](https://devdocs.magento.com/extensions/install/){target=&quot;_blank&quot;，瞭解有關使用這些工具在上安裝和配置擴展的資訊 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 平台。

* [!DNL Inventory Management] Adobe Commerce和Magento Open Source

   您必須在Adobe Commerce和Magento Open Source實例上安裝並啟用了Inventory management擴展。 通常，此擴展在Adobe Commerce2.3.x及更高版本上預設安裝並啟用。 有關詳細資訊，請參見 [安裝Inventory management](https://devdocs.magento.com/extensions/inventory-management/) 在Adobe Commerce開發人員文檔中。

## 平台和版本要求

的 [!DNL Store Fulfillment] 解決方案可在以下平台上向Adobe Commerce客戶提供。

* Adobe Commerce雲基礎架構(ECE)
* Adobe Commerce內部(EE)

「儲存履行」解決方案與以下軟體版本相容。

**軟體相容性**

| **軟體** | **最低版本** | **最大版本** |
|----------------|---------------------|---------------------|
| Adobe Commerce | 2.4.0 | 2.4.4 |
| 作曲家 | 1.x | 2.x |
| 瑪麗亞 | 十點二 | 十點四 |
| MySQL | 5.7 | 8.0 |
| 菲律賓比索 | 7.4 | 8.1 |

有關詳細要求，請查閱Adobe Commerce [系統要求](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) 的子菜單。

### 業務需求

您的企業必須滿足以下最低標準才能實施「商店完成」解決方案。

* 僅限美國企業

* B2C零售商、銷售D2C的CPG製造商或銷售D2C或面向小型企業的分銷商

* 至少一個實體商店或倉庫

* 為Adobe Commerce管理您的產品庫存（是MSI）,Inventory management

* 使商戶庫存合併的能力

* 在支援Store Fullimment解決方案的所有位置儲存Wi-Fi可用性

* 商店和倉庫的會員在輪班期間可以訪問iOS或安卓移動設備，不管是個人設備，還是商家提供的

* 使用「商店履行」解決方案管理的產品必須具有包含SKU或UPC產品代碼的產品屬性
