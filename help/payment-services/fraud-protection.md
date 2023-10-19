---
title: 顯著的防欺詐功能
description: 啟用自動的詐騙保護 [!DNL Payment Services] 含已簽署。
role: Admin, User
level: Intermediate
feature: Payments, Checkout, Configuration, Security
exl-id: 440296bb-a6ff-408b-8195-3027916e4f84
source-git-commit: 480b35fbc57b8528dbc305aa7db52483ba49d98c
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# 有效保護詐騙

您可以為以下專案啟用自動防欺詐功能： [!DNL Payment Services] 使用 [代表擴充功能](https://commercemarketplace.adobe.com/signifyd-module-connect.html).

Adobe Commerce支援Signifyd 5.4.0和更新版本。 [!DNL Payment Services] 支援預先驗證和後期驗證標籤流程。

表示/[!DNL Payment Services] 整合提供信用卡、借記卡、保管卡、透過管理員結帳，以及PayPal和Apple Pay付款方式的涵蓋範圍。 雖然部分交易的細節並未在支付服務和Signifyd之間分享，但Signifyd為所有支付方式提供全面的風險保障，確保最大限度的保護。

另請參閱 [重要檔案](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#downloadandinstallingmagento2extension) 以瞭解如何安裝和設定擴充功能。

## 入門

您必須直接與簽署通訊，才能將擴充功能上線並搭配使用 [!DNL Payment Services] — 沒有 [!DNL Payment Services] 需要設定。 安裝後，您就可以在Admin中設定Signifyd擴充功能。 與此擴充功能相關的任何支援將由Signfyd管理。

使用Signid上線時，您必須：

1. 連絡代理人以設定新帳戶。
1. 依預設，表示為 [加入允許清單](https://github.com/signifyd/magento2/blob/main/docs/RESTRICT-PAYMENTS.md) 為確保Signifyd不會觸發其目前不支援的其他付款選項。 若要禁止特定付款方式，您必須進行變更。
1. 向Signifyd確認PayPal不會拒絕可能由Signifyd核准的訂單，方法是透過Paypal中的商家詐騙保護設定。
1. 啟用要與相容的Signifyd擴充功能 [!DNL Payment Services]：
   * 使用時 [!DNL Payment Services] 在 _即時_ 模式，表示必須處於生產模式。
   * 使用時 [!DNL Payment Services] 在 _Sandbox_ 模式，表示必須處於測試模式。

## 設定

由於「表示」會對您的訂單採取某些作業，因此必須設定擴充功能，以根據您設定的付款作業適當地執行作業 [!DNL Payment Services].

這些設定選項與支付服務和Signifyd整合不相容：

* 時間 [!DNL Payment Services] 已設定為 `Authorize` 付款動作 _和_ 表示位於 `PostAuth` 模式，具有 _[!UICONTROL Decline Guarantees]_選項已設為&#x200B;**建立銷退折讓單**.

  原因： [!DNL Payment Services] 建立授權交易，表示然後嘗試退款。


* [!DNL Payment Services] 已設定為 `Authorize and Capture` 付款動作 _和_ 表示位於 `PostAuth` 模式，具有 _[!UICONTROL Decline Guarantees]_選項已設為&#x200B;**取消訂單**.

  原因： [!DNL Payment Services] 建立擷取交易，表示然後嘗試作廢。


如需的相關資訊，請參閱重要檔案 [設定擴充功能](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#configuringmagento2extension).

請參閱簽署檔案，將其 [進一步瞭解訂單工作流程](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#howmagento2works).
