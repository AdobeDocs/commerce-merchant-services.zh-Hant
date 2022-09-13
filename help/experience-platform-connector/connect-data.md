---
title: 將商務資料連結至Adobe Experience Platform
description: 了解如何將您的Commerce資料連結至Adobe Experience Platform。
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: c7344efead97b0562a146f096123dd84f998fd5e
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# 將商務資料連結至Adobe Experience Platform {#connectaep}

若要將您的Adobe Commerce執行個體連結至Adobe Experience Platform，您必須提供組織ID和資料流ID。

![Experience Platform連接器配置](assets/epc-config.png)

1. 登入您的Adobe帳戶，位於 [商務服務連接器](../landing/saas.md#organizationid) 並選取您的組織ID。

1. 在管理員中，前往 **系統** >服務> **Experience Platform連接器**.

1. 在 **範圍** 下拉式清單中，選取存放區檢視的內容或「範圍」。

1. 在 **組織ID** 欄位中，您會看到與Adobe Experience Platform帳戶相關聯的ID，如 [商務服務連接器](../landing/saas.md#organizationid). 組織ID為全域。 每個Adobe Commerce例項只能關聯一個組織ID。

1. 在 **資料流ID** 欄位，貼上您資料流的ID [已建立](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) 在Adobe Experience Platform。

## 資料流ID與您的商務實例儲存視圖的關係

資料流ID可將事件從Adobe Experience Platform轉送至其他AdobeDX產品，且可與您特定Adobe Commerce例項內的特定商店檢視建立關聯。 您也可以將多個商店檢視與相同的資料流ID建立關聯。 這取決於對您的業務最有意義的是什麼。 [深入了解](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en#event-forwarding-settings) 關於事件轉送。

## 欄位說明

| 欄位 | 說明 |
|--- |--- |
| 範圍 | 要應用配置設定的特定儲存視圖。 |
| 組織ID（全域） | 屬於購買AdobeDX產品的組織的ID。 此ID會將您的Adobe Commerce執行個體連結至Adobe Experience Platform。 |
| 資料流ID（儲存檢視） | 允許資料從Adobe Experience Platform流向其他AdobeDX產品的ID。 此ID可與您特定Adobe Commerce例項內的特定商店檢視相關聯。 |

安裝Experience Platform連接器擴充功能後，已建立Adobe Commerce和Adobe Experience Platform之間的連結，並指定Datastream ID，商務資料便開始流向Adobe Experience Platform邊緣和其他AdobeDX產品。

>[!NOTE]
>
> 資料從邊緣流到其他AdobeDX產品所花費的時間可能有所不同。

## 邊緣的商務資料

當商務資料傳送至Adobe Experience Platform Edge時，您可以建立如下的報表：

![Adobe Experience Manager中的商務資料](assets/aem-data-1.png)
_Adobe Experience Manager中的商務資料_
