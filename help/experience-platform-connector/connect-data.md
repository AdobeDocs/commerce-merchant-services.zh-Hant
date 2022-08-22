---
title: 將Commerce資料連接到Adobe Experience Platform
description: 瞭解如何將您的Commerce資料連接到Adobe Experience Platform。
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: 5f8fcc3d6d05cdd854eadd14f53e1ca13625dae3
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# 將Commerce資料連接到Adobe Experience Platform {#connectaep}

在將您的Adobe Commerce資料連接到Adobe Experience Platform之前，必須登錄到您的Adobe帳戶 [Commerce Services連接器](../landing/saas.md#organizationid)。 登錄並選擇組織ID後，可以在 **Experience Platform連接器** 頁。

![Experience Platform連接器配置](assets/epc-config.png)

1. 在管理員中，轉到 **系統** >服務> **Experience Platform連接器**。

1. 在 **範圍** 下拉清單，選擇儲存視圖的上下文或「範圍」。

   IMS組織ID是全局的。 每個Adobe Commerce實例只能關聯一個IMS組織ID。

1. 在 **IMS組織ID** 欄位中，您將看到與Adobe Experience Platform帳戶關聯的ID，如 [Commerce Services連接器](../landing/saas.md#organizationid)。

1. 在 **資料流ID** 欄位，貼上您的資料流的ID [建立](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) 在Adobe Experience Platform。

## Datastream ID與Commerce實例儲存視圖的關係

Datastream ID允許事件從Adobe Experience Platform轉發到其他AdobeDX產品，並可以關聯到您特定Adobe Commerce實例中的特定儲存視圖。 還可以將多個儲存視圖與同一資料流ID關聯。 這取決於什麼對您的業務最有意義。 [瞭解更多資訊](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en#event-forwarding-settings) 關於事件轉發。

## 欄位說明

| 欄位 | 說明 |
|--- |--- |
| 範圍 | 要應用配置設定的特定儲存視圖。 |
| IMS組織（全球） | 屬於購買AdobeDX產品的組織的ID。 此ID將你的Adobe Commerce實例連結到Adobe Experience Platform。 |
| 資料流ID（儲存視圖） | 允許資料從Adobe Experience Platform流到其他AdobeDX產品的ID。 此ID可以與您特定Adobe Commerce實例中的特定storeView關聯。 |

安裝了Experience Platform連接器擴展，建立了Adobe Commerce和Adobe Experience Platform之間的連結，並指定了Datastream ID,Commerce資料開始流向Adobe Experience Platform邊緣和其他AdobeDX產品。

## 邊緣的商業資料

將Commerce資料發送到Adobe Experience Platform邊緣時，可以生成如下報表：

![Adobe Experience Manager商業資料](assets/aem-data-1.png)
_Adobe Experience Manager商業資料_
