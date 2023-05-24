---
title: 指南概述
description: 瞭解如何使用Experience Platform聯結器將Adobe Commerce資料與Adobe Experience Platform整合。
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
source-git-commit: 0d5bbe7d4e2070173930df66c4f159d65c7383ea
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# Experience Platform聯結器總覽

Experience Platform聯結器擴充功能可讓Adobe Commerce商家傳送 [店面](events.md#storefront-events) 和 [後台](events.md#back-office-events) 資料傳送至Adobe Experience Platform edge，以便其他Adobe Experience Cloud產品(例如Adobe Analytics和Adobe Target)可以使用Commerce資料。 透過將您的Commerce資料連線到Adobe Experience Cloud中的其他產品，您可以執行工作，例如分析網站上的使用者行為、執行AB測試和建立個人化行銷活動。

[店面活動](events.md#storefront-events) 擷取購物者互動，例如 `View Page`， `View Product`， `Add to Cart`、和 [請購單清單](events.md#b2b-events) 資訊（適用於B2B商家）。 [後台](events.md#back-office-events) 事件會擷取訂單狀態的相關資訊，例如，訂單是否已下達、已取消、已退款、已出貨或已完成。 擷取的資料不包括個人識別資訊(PII)。 所有使用者識別碼（例如Cookie ID和IP位址）都需嚴格匿名處理。 [瞭解更多](https://www.adobe.com/privacy/experience-cloud.html).

Experience Platform聯結器會顯示在「商務管理員」中的 **系統** >服務> **Experience Platform聯結器**.

![Experience Platform聯結器擴充功能管理檢視](assets/epc-adminui.png)

## 必要條件 {#prereqs}

若要使用Experience Platform聯結器，您必須具備下列專案：

- Adobe Commerce 2.4.3或更新版本
- Adobe ID和組織ID
- [Adobe使用者端資料層(ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html). 需要ACDL才能收集店面事件資料。
- 其他AdobeDX產品的權益

## 入門步驟

1. [安裝](install.md) Experience Platform聯結器擴充功能。
1. [登入](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) 至您的Adobe帳戶和 [檢視以確認](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255) 您的組織ID。 組織ID是與已布建Experience Cloud公司相關聯的ID。 此ID是24個字元的英數字串，後面接著（而且必須包含） `@AdobeOrg`.
1. [建立或更新](update-xdm.md) 您的XDM結構描述具有商務特定欄位群組。
1. [建立資料集](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) 根據您建立或更新的schema。 此資料集將包含您傳送的Commerce資料。
1. [建立資料串流](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) 並選取包含商務特定欄位群組的XDM結構描述。
1. [連線至Commerce Services](../landing/saas.md).
1. [連線至Adobe Experience Platform](connect-data.md).

## 對象

本指南是專為想要將Adobe Commerce資料與其他AdobeDX產品連結的Adobe Commerce商家所設計。

### PWA Studio支援

請參閱 [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/) 有關如何在Experience Platform店面中使用PWA Studio聯結器的資訊檔案。

### AEM支援 {#aem-support}

請參閱 [AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/aep.html) 說明檔案，瞭解如何使用CIF - Storefront Connector將店面活動資料從AEM轉譯的產品頁面傳送至Experience Platform。Experience Platform

如果您需要本指南未涵蓋的資訊或問題，請使用下列資源：

- [說明中心](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html){target="_blank"}
- [支援票證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket){target="_blank"} — 提交票證以接收其他說明。
