---
title: 將商務資料連結至Adobe Experience Platform
description: 了解如何將您的Commerce資料連結至Adobe Experience Platform。
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: 710a18a63c84f0ae0a5aa3b3ad50fdfce0358db6
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 0%

---

# 將商務資料連結至Adobe Experience Platform {#connectaep}

若要將您的Adobe Commerce執行個體連結至Adobe Experience Platform，您必須提供組織ID和資料流ID。

![Experience Platform連接器配置](assets/epc-config-sf.png)

## 一般

1. 登入您的Adobe帳戶，位於 [商務服務連接器](../landing/saas.md#organizationid) 並選取您的組織ID。

1. 在管理員中，前往 **系統** >服務> **Experience Platform連接器**.

1. 在 **範圍** 下拉式清單，將內容設為 **網站**.

1. 在 **組織ID** 欄位中，您會看到與Adobe Experience Platform帳戶相關聯的ID，如 [商務服務連接器](../landing/saas.md#organizationid). 組織ID為全域。 每個Adobe Commerce例項只能關聯一個組織ID。

1. （選用）如果您已有 [AEP Web SDK(alloy)](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html) 已部署至您的網站，請啟用核取方塊並新增AEP Web SDK的名稱。 否則，請將這些欄位留空，Experience Platform連接器就會為您部署一個欄位。

   >[!NOTE]
   >
   >如果您指定自己的AEP Web SDK,Experience Platform連接器會使用與該SDK相關聯的資料流ID，而非本頁所指定的資料流ID（如果有的話）。

## 資料收集

>[!NOTE]
>
>對於已註冊我們後台測試版計畫的商家，您將看到一個複選框以啟用後台活動。 如果您想參加後台測試計畫，請聯繫 [drios@adobe.com](mailto:drios@adobe.com).

![BetaExperience Platform連接器配置](assets/epc-config-beta.png)

在 **資料收集** 區段中，您可以指定要收集和傳送至Experience Platform邊緣的資料類型。 只要AEP Web SDK和組織ID有效，預設會自動傳送店面事件。 請參閱事件主題以深入了解 [店面](events.md#storefront-events) 和 [後台](events.md#beta-order-status-events) 事件。

>[!NOTE]
>
>中的所有欄位 **資料收集** 區段 **網站** 範圍或更高。

1. 選擇 **後台事件** 如果您想要發送訂單狀態資訊，例如，已下單、取消、退貨或已發運訂單。

   >[!NOTE]
   >
   >依預設，所有後台資料都會傳送至Experience Platform邊緣。 如果購物者選擇退出資料收集，您必須在Experience Platform中明確設定購物者的隱私權偏好設定。 這與店面事件不同，在店面事件中，收集者已根據購物者偏好處理同意。 [深入了解](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/consent/adobe/dataset.html) 關於在Experience Platform中設定購物者的隱私偏好設定。

1. （如果您是使用自己的AEP Web SDK，請略過此步驟。） [建立](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/configure.html#create) Adobe Experience Platform中的資料流，或選取您要用於收集的現有資料流。

1. （如果您是使用自己的AEP Web SDK，請略過此步驟。） 在 **資料流ID** 欄位，貼上新資料流或現有資料流的ID。

## 欄位說明

| 欄位 | 說明 |
|--- |--- |
| 範圍 | 您要套用組態設定的特定網站。 |
| 組織ID（全域） | 屬於購買AdobeDX產品的組織的ID。 此ID會將您的Adobe Commerce執行個體連結至Adobe Experience Platform。 |
| AEP Web SDK是否已部署至您的網站 | 如果您已將自己的AEP Web SDK部署至網站，請選取此核取方塊 |
| AEP Web SDK名稱（全域） | 如果您的網站已部署Experience PlatformWeb SDK，請在此欄位中指定該SDK的名稱。 這可讓「店面事件收集器」和「店面事件SDK」使用您的Experience PlatformWeb SDK，而非Experience Platform連接器部署的版本。 如果您的網站未部署Experience PlatformWeb SDK，請將此欄位留空，Experience Platform連接器就會為您部署一個。 |
| 店面事件 | 只要組織ID和資料流ID有效，就預設會勾選此選項。 店面事件會在購物者瀏覽您的網站時，從他們收集匿名的行為資料。 |
| 後台事件（測試版） | 如果勾選此選項，事件裝載會包含匿名的訂單狀態資訊，例如訂單已下、已取消、已退還或已發運。 |
| 資料流ID（網站） | 允許資料從Adobe Experience Platform流向其他AdobeDX產品的ID。 此ID必須與您特定Adobe Commerce例項內的特定網站相關聯。 如果您指定自己的Experience PlatformWeb SDK，請勿在此欄位中指定資料流ID。 Experience Platform連接器會使用與該SDK相關聯的資料流ID，並忽略此欄位中指定的任何資料流ID（如果有的話）。 |

安裝Experience Platform連接器擴充功能後，已建立Adobe Commerce和Adobe Experience Platform之間的連結，並指定Datastream ID，商務資料便開始流向Adobe Experience Platform邊緣和其他AdobeDX產品。

>[!NOTE]
>
> 資料從邊緣流到其他AdobeDX產品所花費的時間可能有所不同。

## 邊緣的商務資料

當商務資料傳送至Adobe Experience Platform Edge時，您可以建立如下的報表：

![Adobe Experience Manager中的商務資料](assets/aem-data-1.png)
_Adobe Experience Manager中的商務資料_
