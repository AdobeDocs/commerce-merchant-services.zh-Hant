---
title: 上線 [!DNL Payment Services]
description: 連線您的執行個體 [!DNL Payment Services] 功能，完成一些入門步驟。
role: User
level: Intermediate
exl-id: 1ee8c660-0941-4378-a1d7-ae45de3de211
source-git-commit: d8be88f47f103c5d632540dae743ede398a9b7ad
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# 上線 [!DNL Payment Services]

若要開始使用 [!DNL Payment Services] 的 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source]，您必須完成一些入門步驟，才能將執行個體與支付功能連線。

## 上線流程

![上線流程](assets/onboarding-diagram.svg)

此上線流程圖顯示上線的一般流程 [!DNL Payment Services].

在您完成沙箱或即時付款上線後，可從以下位置存取financial reporting： [!DNL Payment Services] 在Admin中。

如果沙箱和即時支付都已上線並啟用，您可以從以下位置輕鬆地在這些模式之間切換： [!DNL Payment Services] 首頁。

## 必要條件

為了使用 [!DNL Payment Services]，您的執行個體必須具備下列可用專案：

* 服務聯結器模組
* 服務識別碼模組
* API金鑰

服務聯結器與服務ID模組會在以下期間自動安裝： [安裝 [!DNL Payment Services]](install.md). 安裝完成後，您可以在組態設定中看到新區段(**[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**)時，選擇此選項&#x200B;**[!UICONTROL Services]**—**[!UICONTROL Commerce Services Connector]**.

若要瞭解如何建立或存取您的API金鑰，請參閱 [API認證](#obtain-api-credentials).

## 入門步驟

1. [安裝 [!DNL Payment Services] 擴充功能](install.md#get-payment-services).
1. [取得API認證](connect.md#obtain-api-credentials).
1. [連線您的執行個體](connect.md#configure-commerce-services) 至Commerce服務。 每個Commerce執行個體只能完成此連線一次。
1. [設定沙箱服務](sandbox.md#enable-sandbox-testing) (或者，您也可以繼續前往 [啟用即時付款](sandbox.md#enable-live-payments) 如果您已在其他環境中測試功能)，請使用測試PayPal付款處理帳戶。
1. [設定 [!DNL Payment Services] 作為您的付款方式](production.md#set-payment-services-as-payment-method)，以開始處理測試付款。
1. [要求付款權益](production.md#request-payments-entitlement-from-adobe) 以啟用即時上線。
1. [完成商戶上線](production.md#complete-merchant-onboarding) 啟用您的Commerce網站的即時付款。
1. [取得您的 [!DNL Payment Services] 商家ID](production.md#configure-pricing-tier) 然後交給銷售人員設定正確的定價層級。
1. [啟用 [!DNL Payment Services] 在即時模式中](production.md#enable-live-payments) 以開始處理即時付款。
1. 測試付款，兩者皆有 [沙箱](sandbox.md#test-in-sandbox-environment) 和 [生產](production.md#test-in-production) 環境。

>[!NOTE]
>
>如果您未在管理員（步驟3）中設定Commerce Services，則無法設定沙箱或即時付款。

## 疑難排除

* [疑難排解 [!DNL Payment Services] 安裝](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-install.html?lang=en)
* [未驗證PayPal沙箱帳戶](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-paypal-acct.html)
* [已延遲 [!DNL Payment Services] 報告資料](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-report-info-delayed.html)
* [在沙箱環境中處理付款時，測試信用卡無法透過PayPal](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-cc-sandbox-failure.html?lang=en)
