---
title: 板載 [!DNL Payment Services]
description: 將實例與 [!DNL Payment Services] 功能。
role: User
level: Intermediate
exl-id: 1ee8c660-0941-4378-a1d7-ae45de3de211
source-git-commit: d8be88f47f103c5d632540dae743ede398a9b7ad
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# 板載 [!DNL Payment Services]

開始使用 [!DNL Payment Services] 為 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source]，您必須完成一些附加步驟，以便將實例與付款功能連接。

## 登機流

![登機流](assets/onboarding-diagram.svg)

此登機流程圖顯示登機的一般過程 [!DNL Payment Services]。

完成沙箱或即時付款的登錄後，可以從 [!DNL Payment Services] 的子菜單。

如果同時啟用了沙盒和即時支付，則您可以輕鬆地從 [!DNL Payment Services] 回家。

## 先決條件

為了使用 [!DNL Payment Services]，您的實例必須具有以下功能：

* 服務連接器模組
* 服務ID模組
* API密鑰

服務連接器和服務ID模組在 [安裝 [!DNL Payment Services]](install.md)。 安裝完成後，您可以在配置設定中看到新節(**[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**)**[!UICONTROL Services]**—**[!UICONTROL Commerce Services Connector]**。

要瞭解如何建立或訪問API密鑰，請參閱 [API憑據](#obtain-api-credentials)。

## 登機步驟

1. [安裝 [!DNL Payment Services] 擴展](install.md#get-payment-services)。
1. [獲取API憑據](connect.md#obtain-api-credentials)。
1. [連接實例](connect.md#configure-commerce-services) 服務。 每個Commerce實例只能完成一次此連接。
1. [設定沙盒服務](sandbox.md#enable-sandbox-testing) (或者， [啟用即時支付](sandbox.md#enable-live-payments) 如果您已在其他環境中測試了功能)，則使用testPayPal付款處理帳戶。
1. [設定 [!DNL Payment Services] 作為付款方式](production.md#set-payment-services-as-payment-method)，在沙盒模式下，開始處理test付款。
1. [請求付款權利](production.md#request-payments-entitlement-from-adobe) 以啟用直播。
1. [完整的商戶登機](production.md#complete-merchant-onboarding) 啟用Commerce網站的即時付款。
1. [獲取 [!DNL Payment Services] 商戶ID](production.md#configure-pricing-tier) 並交給銷售人員以配置正確的定價層。
1. [啟用 [!DNL Payment Services] 在即時模式下](production.md#enable-live-payments) 開始處理即時支付。
1. Test付款，在兩者中 [沙坑](sandbox.md#test-in-sandbox-environment) 和 [生產](production.md#test-in-production) 環境。

>[!NOTE]
>
>如果您未在管理中配置Commerce Services（步驟3），則無法設定沙箱或即時付款。

## 故障排除

* [故障排除 [!DNL Payment Services] 安裝](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-install.html?lang=en)
* [未驗證PayPal沙盒帳戶](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-paypal-acct.html)
* [延遲 [!DNL Payment Services] 報表資料](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-report-info-delayed.html)
* [Test信用卡在沙盒環境中處理付款時與PayPal一起失敗](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-cc-sandbox-failure.html?lang=en)
