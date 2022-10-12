---
title: 將商務資料連結至Adobe Experience Platform
description: 了解如何將您的Commerce資料連結至Adobe Experience Platform。
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: 1af2dee51391c94e19b68481d390cc2629fe1d6e
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# 將商務資料連結至Adobe Experience Platform {#connectaep}

若要將您的Adobe Commerce執行個體連結至Adobe Experience Platform，您必須提供組織ID和資料流ID。

![Experience Platform連接器配置](assets/epc-config.png)

1. 登入您的Adobe帳戶，位於 [商務服務連接器](../landing/saas.md#organizationid) 並選取您的組織ID。

1. 在管理員中，前往 **系統** >服務> **Experience Platform連接器**.

1. 在 **範圍** 下拉式清單，將內容設為 **網站**.

1. 在 **組織ID** 欄位中，您會看到與Adobe Experience Platform帳戶相關聯的ID，如 [商務服務連接器](../landing/saas.md#organizationid). 組織ID為全域。 每個Adobe Commerce例項只能關聯一個組織ID。

1. 在 **資料流ID** 欄位，貼上您資料流的ID [已建立](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html#create) 在Adobe Experience Platform。

   >[!NOTE]
   >
   >資料流ID的範圍必須在網站層級或更高層級設定。 在該層級，階層中的每個網站會使用相同的資料流ID。 您無法在儲存檢視層級設定資料流ID範圍。

1. （選用）如果您的網站未部署AEP Web SDK，請將此欄位留空，Experience Platform連接器就會為您部署一個。 否則，請新增AEP Web SDK的名稱。

## 欄位說明

| 欄位 | 說明 |
|--- |--- |
| 範圍 | 您要套用組態設定的特定網站。 |
| 組織ID（全域） | 屬於購買AdobeDX產品的組織的ID。 此ID會將您的Adobe Commerce執行個體連結至Adobe Experience Platform。 |
| 資料流ID（網站） | 允許資料從Adobe Experience Platform流向其他AdobeDX產品的ID。 此ID必須與您特定Adobe Commerce例項內的特定網站相關聯。 |
| AEP Web SDK名稱（全域） | 如果您的網站未部署AEP Web SDK，請將此欄位留空，Experience Platform連接器就會為您部署一個。 如果您的網站已部署AEP Web SDK，請在此欄位中指定該SDK的名稱。 這可讓「店面事件收集器」和「店面事件SDK」使用您的AEP Web SDK，而非Experience Platform連接器部署的版本。 |

安裝Experience Platform連接器擴充功能後，已建立Adobe Commerce和Adobe Experience Platform之間的連結，並指定Datastream ID，商務資料便開始流向Adobe Experience Platform邊緣和其他AdobeDX產品。

>[!NOTE]
>
> 資料從邊緣流到其他AdobeDX產品所花費的時間可能有所不同。

## 邊緣的商務資料

當商務資料傳送至Adobe Experience Platform Edge時，您可以建立如下的報表：

![Adobe Experience Manager中的商務資料](assets/aem-data-1.png)
_Adobe Experience Manager中的商務資料_
