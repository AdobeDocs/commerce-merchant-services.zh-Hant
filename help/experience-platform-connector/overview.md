---
title: 指南概述
description: 了解如何使用Adobe Commerce連接器將Experience Platform資料與Adobe Experience Platform整合。
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
source-git-commit: a316b92f75cb227d0c58af07482f9d37568af7ca
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# Experience Platform連接器概述

Experience Platform連接器擴充功能可讓Adobe Commerce商家將資料傳送至Adobe Experience Platform邊緣，讓Adobe Analytics和Adobe Target等其他Adobe Experience Cloud產品都能使用該商務資料。 將您的商務資料連結至Adobe Experience Cloud中的其他產品，您可以執行工作，例如分析網站上的使用者行為、執行AB測試，以及建立個人化促銷活動。

[店面事件](events.md) 擷取購物者互動，例如 `View Page`, `View Product`, `Add to Cart`等。 擷取的資料不包含個人識別資訊(PII)。 所有使用者識別碼（例如Cookie ID和IP位址）都會嚴格進行匿名處理。 [深入了解](https://www.adobe.com/privacy/experience-cloud.html).

Experience Platform連接器會顯示在「商務管理員」下方 **系統** >服務> **Experience Platform連接器**.

![Experience Platform連接器擴充功能管理檢視](assets/epc-adminui.png)

## 必要條件 {#prereqs}

若要使用Experience Platform連接器，您必須具備下列條件：

- Adobe Commerce 2.4.3或更新版本
- Adobe ID與組織ID
- 其他AdobeDX產品的使用權限

## 入門步驟

1. [安裝](install.md) Experience Platform連接器延伸模組。
1. [登入](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) Adobe帳戶和 [檢視](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=en#concept_EA8AEE5B02CF46ACBDAD6A8508646255) 您的組織ID。 組織ID是與您布建之Experience Cloud公司相關聯的ID。 此ID是24個字元的英數字串，後面接著（且必須包含） `@AdobeOrg`.
1. [Connect](connect-data.md) Adobe Commerce例項到Adobe Experience Platform。
1. [建立或更新](update-xdm.md) 具有商務專用欄位群組的XDM結構。
1. [建立資料流](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en) 並選取包含「商務」專用欄位群組的XDM結構。
1. （可選） [上傳購物者設定檔](profile.md) 至Adobe Experience Platform，以便將店面資料歸因於特定的購物者，以增強其購物體驗。

## 對象

本指南專為想將其Adobe Commerce店面資料連結至其他AdobeDX產品的Adobe Commerce商家而設計。

### PWA Studio支援

請參閱 [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/) 說明檔案，以取得如何在PWA Studio店面中使用Experience Platform連接器的資訊。

### AEM支援 {#aem-support}

請參閱 [AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/aep.html) 說明檔案，了解如何使用CIF - Connector，將AEM轉譯的產品頁面的storefront事件資料傳送至Experience Platform。

如果您需要資訊或有本指南未涵蓋的問題，請使用下列資源：

- [協助中心](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html){target=&quot;_blank&quot;}
- [支援票證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket){target=&quot;_blank&quot;} — 提交票證以接收其他幫助。
