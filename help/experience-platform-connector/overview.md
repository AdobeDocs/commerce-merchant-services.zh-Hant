---
title: 指南概述
description: 了解如何使用Adobe Commerce連接器將Experience Platform資料與Adobe Experience Platform整合。
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
source-git-commit: 22823b662eefa953fcca6ae78f6c37ee8abff3d1
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# Experience Platform連接器概述

Experience Platform連接器擴充功能可讓Adobe Commerce商戶傳送 [店面](events.md#storefront-events) 和 [後台](events.md#back-office-events) 資料傳送至Adobe Experience Platform邊緣，以便其他Adobe Experience Cloud產品(例如Adobe Analytics和Adobe Target)可以使用該商務資料。 將您的商務資料連結至Adobe Experience Cloud中的其他產品，您可以執行工作，例如分析網站上的使用者行為、執行AB測試，以及建立個人化促銷活動。

[店面事件](events.md#storefront-events) 擷取購物者互動，例如 `View Page`, `View Product`, `Add to Cart`，和 [申請表](events.md#b2b-events) 資訊（適用於B2B商戶）。 [後台](events.md#back-office-events) 事件會擷取訂單狀態的相關資訊，例如訂單已下放、取消、已退還、已發運或完成。 擷取的資料不包含個人識別資訊(PII)。 所有使用者識別碼（例如Cookie ID和IP位址）都會嚴格進行匿名處理。 [深入了解](https://www.adobe.com/privacy/experience-cloud.html).

Experience Platform連接器會顯示在「商務管理員」下方 **系統** >服務> **Experience Platform連接器**.

![Experience Platform連接器擴充功能管理檢視](assets/epc-adminui.png)

## 必要條件 {#prereqs}

若要使用Experience Platform連接器，您必須具備下列條件：

- Adobe Commerce 2.4.3或更新版本
- Adobe ID與組織ID
- [Adobe客戶端資料層(ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html). 收集店面事件資料時需要ACDL。
- 其他AdobeDX產品的使用權限

## 入門步驟

1. [安裝](install.md) Experience Platform連接器延伸模組。
1. [登入](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) Adobe帳戶和 [檢視](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255) 您的組織ID。 組織ID是與您布建之Experience Cloud公司相關聯的ID。 此ID是24個字元的英數字串，後面接著（且必須包含） `@AdobeOrg`.
1. [Connect](connect-data.md) Adobe Commerce例項到Adobe Experience Platform。
1. [建立或更新](update-xdm.md) 具有商務專用欄位群組的XDM結構。
1. [建立資料集](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) 根據您建立或更新的架構。
1. [建立資料流](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) 並選取包含「商務」專用欄位群組的XDM結構。

## 對象

本指南是為想將其Adobe Commerce資料連結至其他AdobeDX產品的Adobe Commerce商家所設計。

### PWA Studio支援

請參閱 [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/) 說明檔案，以取得如何在PWA Studio店面中使用Experience Platform連接器的資訊。

### AEM支援 {#aem-support}

請參閱 [AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/aep.html) 說明檔案，了解如何使用CIF - Connector，將AEM轉譯的產品頁面的storefront事件資料傳送至Experience Platform。

如果您需要資訊或有本指南未涵蓋的問題，請使用下列資源：

- [協助中心](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html){target="_blank"}
- [支援票證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket){target="_blank"} — 提交票證以接收其他幫助。
