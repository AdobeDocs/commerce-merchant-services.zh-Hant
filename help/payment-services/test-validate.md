---
title: 測試和驗證
description: 測試和驗證可協助確保 [!DNL Payment Services] 功能可如預期運作，為客戶提供最佳付款選項
exl-id: 95b4615e-73b0-41e8-83e2-e65a0b22f10f
source-git-commit: 0324c2d8e34fee0872d5f52ed3a246094b482aa2
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---

# 測試和驗證

曝光前 [!DNL Payment Services] for [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 對於購物者而言，最好在沙箱環境中測試 _和_ 生產。 測試和驗證可協助確保 [!DNL Payment Services] 功能可如預期運作，為您的商店和客戶提供最佳付款選項。

## 在沙箱環境中測試

測試 [!DNL Payment Services] 在沙箱環境中，即使是僅與PayPal沙箱連結的模擬環境，而非與真正的銀行和商戶連結的模擬環境，仍是重要的驗證步驟。

1. 從您的商店完成成功的結帳，使用 [信用卡欄位](payments-options.md#credit-card-fields) 或 [PayPal智慧按鈕](payments-options.md#paypal-smart-buttons). 請參閱 [測試憑證](#testing-credentials) 以取得有關使用假信用卡進行測試的詳細資訊。
1. 捕獲(當您的付款活動為 [設為 `Authorize and Capture`](onboard.md#set-payment-services-as-payment-method)), [退款](refunds.md)，或 [void](voids.md) 剛完成的訂單。 您也可以簡單 [建立發票](https://docs.magento.com/user-guide/sales/invoice-create.html){target="_blank"} 訂單，若您的付款動作設為 `Authorize` 而非 `Authorize and Capture`.
1. 在24到48小時內，查看 [支付報告](payouts.md).
1. 請參閱 [訂單付款狀態報表](order-payment-status.md).

### 測試憑證

在測試和驗證沙箱時，您必須使用假信用卡號，這樣您就不會對現有信用卡帳戶建立實際費用。

使用PayPal的信用卡生成器 [生成隨機信用卡資訊](https://www.paypal.com/us/smarthelp/article/where-can-i-find-test-credit-card-numbers-ts2157) 用於測試。

若要以沙箱模式測試Apple Pay:

* 建立 [Apple沙箱測試者帳戶](https://developer.apple.com/apple-pay/sandbox-testing/#create-a-sandbox-tester-account)，填入假信用卡和帳單資訊。
* [註冊您的沙箱網域](https://developer.paypal.com/docs/checkout/apm/apple-pay/#link-registeryoursandboxdomains).

>[!NOTE]
>
>PayPal的沙箱支付處理有時會很慢，服務偶爾會中斷。 此情況並不說明即時產品付款處理的速度與效率。

## 在生產環境中測試

強烈建議您測試 [!DNL Payment Services] 在生產中，使用真實信用卡和銀行，然後將此功能向購物者公開。 即使測試 [!DNL Payment Services] 沙箱中的測試非常重要，在生產中進行測試是確保 [!DNL Payment Services] 如預期般運作。

您可以測試 [!DNL Payment Services] 在生產中，有兩種方式：

* 選擇您知道購物者不會下訂單的時間。
* 使用暫時無法供購物者存取，但可供您測試的網站商店。

使用真實信用卡和PayPal帳戶完成生產測試，測試付款的整個生命週期，包括捕獲和退款。 在測試期間完成整個結帳和付款流程，為您提供最清楚的結帳和付款流程 [!DNL Payment Services] 當即時購物者使用此功能時，功能就會運作。

您還應驗證銀行對帳單上顯示的資訊是否正確且預期（包括業務說明）。

若要以生產模式測試Apple Pay，您必須 [註冊生產網域](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain).
