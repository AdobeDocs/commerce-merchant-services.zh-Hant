---
title: 指南概述
description: 瞭解如何使用Experience Platform連接器將Adobe Commerce資料與Adobe Experience Platform整合。
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
source-git-commit: 0d5bbe7d4e2070173930df66c4f159d65c7383ea
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# Experience Platform連接器概述

Experience Platform連接器擴展允許Adobe Commerce商家 [店面](events.md#storefront-events) 和 [後台辦公室](events.md#back-office-events) 資料到Adobe Experience Platform邊緣，因此Adobe Analytics和Adobe Target等其他Adobe Experience Cloud產品可以使用該商務資料。 通過將您的Commerce資料連接到Adobe Experience Cloud的其他產品，您可以執行任務，如分析站點上的用戶行為、執行AB測試和建立個性化市場活動。

[店面事件](events.md#storefront-events) 捕獲購物者交互，例如 `View Page`。 `View Product`。 `Add to Cart`, [申請表](events.md#b2b-events) 資訊（針對B2B商戶）。 [後台辦公室](events.md#back-office-events) 事件捕獲有關訂單狀態的資訊，如訂單已下達、取消、退款、已發運或已完成。 捕獲的資料不包括個人身份資訊(PII)。 所有用戶標識符，如cookie ID和IP地址，都是嚴格匿名的。 [瞭解更多資訊](https://www.adobe.com/privacy/experience-cloud.html)。

Experience Platform連接器出現在Commerce Admin中的 **系統** >服務> **Experience Platform連接器**。

![Experience Platform連接器擴展管理視圖](assets/epc-adminui.png)

## 先決條件 {#prereqs}

要使用Experience Platform連接器，必須具有以下內容：

- Adobe Commerce2.4.3或更新
- Adobe ID和組織ID
- [Adobe客戶端資料層(ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html)。 ACDL是收集儲存前事件資料所必需的。
- 其他AdobeDX產品的權利

## 登機步驟

1. [安裝](install.md) Experience Platform連接器擴展。
1. [登錄](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) Adobe帳戶 [查看以確認](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255) 您的組織ID。 組織ID是與您預配的Experience Cloud公司關聯的ID。 此ID是24個字元的字母數字字串，後跟（必須包括） `@AdobeOrg`。
1. [建立或更新](update-xdm.md) 您的XDM架構，具有特定於Commerce的欄位組。
1. [建立資料集](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) 基於您建立或更新的架構。 此資料集將包含您發送的Commerce資料。
1. [建立資料流](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) 並選擇包含特定於Commerce的欄位組的XDM架構。
1. [連接到Commerce Services](../landing/saas.md)。
1. [連接到Adobe Experience Platform](connect-data.md)。

## 觀眾

本指南針對希望將其Adobe Commerce資料與其他AdobeDX產品連接的Adobe Commerce商家而設計。

### PWA Studio支援

查看 [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/) 文檔，瞭解有關如何在Experience Platform庫面中使用PWA Studio連接器的資訊。

### AEM支援 {#aem-support}

查看 [AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/aep.html) 文檔，瞭解如何使用CIF -Experience Platform連接器將AEM呈現的產品頁面中的storefront事件資料發送到Experience Platform。

如果您需要資訊或有本指南未包括的問題，請使用以下資源：

- [幫助中心](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html){target="_blank"}
- [支援票證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket){target="_blank"} — 提交票證以接收其他幫助。
