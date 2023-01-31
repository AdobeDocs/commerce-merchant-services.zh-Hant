---
title: 板載 [!DNL Payment Services]
description: 連結您的執行個體 [!DNL Payment Services] 功能，請完成幾個入門步驟。
role: User
level: Intermediate
exl-id: 1ee8c660-0941-4378-a1d7-ae45de3de211
source-git-commit: d8be88f47f103c5d632540dae743ede398a9b7ad
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# 板載 [!DNL Payment Services]

若要開始使用 [!DNL Payment Services] for [!DNL Adobe Commerce] 和 [!DNL Magento Open Source]，您必須完成幾個入門步驟，將執行個體與付款功能連結。

## 上線流程

![上線流程](assets/onboarding-diagram.svg)

此上線流程圖顯示上線的一般程式 [!DNL Payment Services].

在您完成沙箱或即時付款的上線後，即可從 [!DNL Payment Services] 中。

如果沙箱和即時付款都已上線並啟用，您可以從以下位置輕鬆切換這些模式： [!DNL Payment Services] 家。

## 必要條件

為了使用 [!DNL Payment Services]，您的執行個體必須具備下列功能：

* 服務連接器模組
* 服務ID模組
* API金鑰

服務連接器和服務ID模組會在 [安裝 [!DNL Payment Services]](install.md). 安裝完成後，您可以在組態設定中看到新區段(**[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**)**[!UICONTROL Services]**—**[!UICONTROL Commerce Services Connector]**.

若要了解如何建立或存取您的API金鑰，請參閱 [API憑證](#obtain-api-credentials).

## 入門步驟

1. [安裝 [!DNL Payment Services] 擴充功能](install.md#get-payment-services).
1. [取得API憑證](connect.md#obtain-api-credentials).
1. [連線您的執行個體](connect.md#configure-commerce-services) 至商務服務。 每個Commerce執行個體只需完成一次此連線。
1. [設定沙箱服務](sandbox.md#enable-sandbox-testing) (或者，或者，繼續 [啟用即時支付](sandbox.md#enable-live-payments) 如果您已在其他環境中測試了功能)，且已使用測試的PayPal付款處理帳戶。
1. [設定 [!DNL Payment Services] 作為付款方式](production.md#set-payment-services-as-payment-method)，以開始處理測試付款。
1. [請求付款權利](production.md#request-payments-entitlement-from-adobe) 啟用即時上線功能。
1. [完整的商家入門](production.md#complete-merchant-onboarding) 啟用Commerce網站的即時支付。
1. [取得您的 [!DNL Payment Services] 商家ID](production.md#configure-pricing-tier) 並將其交給銷售人員，以配置正確的定價層。
1. [啟用 [!DNL Payment Services] 在即時模式中](production.md#enable-live-payments) 開始處理即時支付。
1. 測試支付，在 [沙箱](sandbox.md#test-in-sandbox-environment) 和 [生產](production.md#test-in-production) 環境。

>[!NOTE]
>
>如果您未在管理員中設定商務服務（步驟3），則無法設定沙箱或即時付款。

## 疑難排解

* [疑難排解 [!DNL Payment Services] 安裝](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-install.html?lang=en)
* [未驗證PayPal沙箱帳戶](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-paypal-acct.html)
* [延遲 [!DNL Payment Services] 報告資料](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-report-info-delayed.html)
* [在沙箱環境中處理付款時，PayPal無法測試信用卡](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-cc-sandbox-failure.html?lang=en)
