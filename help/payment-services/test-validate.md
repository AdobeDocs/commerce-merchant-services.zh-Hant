---
title: 測試與驗證
description: 測試和驗證可確保 [!DNL Payment Services] 功能如預期運作，並為客戶提供最佳付款選項
exl-id: 95b4615e-73b0-41e8-83e2-e65a0b22f10f
feature: Payments, Checkout
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---

# 測試與驗證

公開之前 [!DNL Payment Services] 的 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 對您的購物者而言，在您的沙箱環境中測試是個好主意 _和_ 生產環境內。 測試和驗證可確保 [!DNL Payment Services] 功能如預期運作，並為您的商店和客戶提供最佳付款選項。

## 在沙箱環境中測試

測試 [!DNL Payment Services] 在沙箱環境中是重要的驗證步驟，即使它是僅連線到PayPal沙箱的模擬環境，而不是連線到真正的銀行和商家。

1. 使用下列任一方式，從您的商店成功完成結帳： [信用卡欄位](payments-options.md#credit-card-fields) 或任何 [PayPal智慧按鈕](payments-options.md#paypal-smart-buttons). 另請參閱 [測試認證](#testing-credentials) 以取得使用假信用卡進行測試的詳細資訊。
1. 擷取(當您的付款動作為 [設定為 `Authorize and Capture`](onboard.md#set-payment-services-as-payment-method))， [退款](refunds.md)，或 [無效](voids.md) 剛完成的訂單。 您也可以 [建立發票](https://docs.magento.com/user-guide/sales/invoice-create.html){target="_blank"} 針對訂單，如果您的付款作業設為 `Authorize` 而非 `Authorize and Capture`.
1. 在24到48小時內，檢視中的交易和其他資訊 [付款報表](payouts.md).
1. 欲瞭解訂單詳情，請參閱 [訂單付款狀態報表](order-payment-status.md).

### 測試認證

在測試和驗證您的沙箱時，您必須使用假的信用卡號碼，這樣您就不會對現有信用卡帳戶建立真正的費用。

使用PayPal的信用卡產生器 [產生隨機信用卡資訊](https://www.paypal.com/us/smarthelp/article/where-can-i-find-test-credit-card-numbers-ts2157) 以進行測試。

若要以沙箱模式測試Apple Pay：

* 建立 [Apple沙箱測試器帳戶](https://developer.apple.com/apple-pay/sandbox-testing/#create-a-sandbox-tester-account)，並填入假信用卡和帳單資訊。
* [註冊您的沙箱網域](https://developer.paypal.com/docs/checkout/apm/apple-pay/#link-registeryoursandboxdomains).

>[!NOTE]
>
>PayPal的沙箱支付處理有時很慢，服務偶爾可能會停止運作。 這種情況並不表示即時產品付款處理的速度和效率。

## 在生產環境中測試

強烈建議您測試 [!DNL Payment Services] 在生產環境中，使用真正的信用卡和銀行，然後向購物者公開此功能。 即使測試 [!DNL Payment Services] 在沙箱中測試很重要，在生產環境中測試是確保 [!DNL Payment Services] 如預期運作。

您可以測試 [!DNL Payment Services] 在生產環境中，使用以下兩種方式之一：

* 選擇您知道購物者不會下訂單的時間。
* 使用購物者暫時無法存取但可供您存取以進行測試的網路商店。

使用真實的信用卡和PayPal帳戶完成您的生產測試，測試付款的整個生命週期，包括擷取和退款。 在測試期間完成整個結帳和付款流程，可讓您清楚瞭解 [!DNL Payment Services] 功能可於即時購物者使用時運作。

您也應確認出現在銀行對帳單上，用於生產測試中付款方式的資訊正確與預期（包括業務說明）。

若要在生產模式下測試Apple Pay，您必須 [註冊您的生產網域](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain).
