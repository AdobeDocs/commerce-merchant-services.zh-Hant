---
title: Test和驗證
description: 測試和驗證有助於確保 [!DNL Payment Services] 功能按預期工作，並為客戶提供最佳付款選項
exl-id: 95b4615e-73b0-41e8-83e2-e65a0b22f10f
source-git-commit: 599405b908cc8b770c917a18ad488a1f69be222b
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# Test和驗證

在你曝光之前 [!DNL Payment Services] 為 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 在沙盒環境中test是個好主意 _和_ 生產。 測試和驗證有助於確保 [!DNL Payment Services] 功能可按預期運行，並為您的商店和客戶提供最佳付款選項。

## Test沙盒環境

測試 [!DNL Payment Services] 在沙箱環境中是一個重要的驗證步驟，即使它是僅連接到PayPal沙箱的模擬環境，而不是連接到真正的銀行和商家。

1. 從您的商店完成成功結帳， [信用卡欄位](payments-options.md#credit-card-fields) 或 [PayPal智慧按鈕](payments-options.md#paypal-smart-buttons)。 請參閱 [使用沙盒模式](#use-sandbox-mode) 的子菜單。
1. 捕獲(當付款活動為 [設定為 `Authorize and Capture`](production.md#set-payment-services-as-payment-method)。 [退款](refunds.md)或 [虛](voids.md) 剛剛完成的訂單。 您也可以 [建立發票](https://docs.magento.com/user-guide/sales/invoice-create.html){target=&quot;_blank&quot;}（如果您的付款活動設定為） `Authorize` 而不是 `Authorize and Capture`。
1. 在24-48小時內，查看 [支付報告](payouts.md)。
1. 請參閱 [訂單付款狀態報表](order-payment-status.md)。

### 使用沙盒模式

在測試和驗證沙盒時，您必須使用假信用卡號，這樣您就不會對現有信用卡帳戶建立實際費用。

使用PayPal的信用卡生成器 [生成隨機信用卡資訊](https://www.paypal.com/us/smarthelp/article/where-can-i-find-test-credit-card-numbers-ts2157) 測試。

>[!NOTE]
>
>PayPal的沙盒支付處理有時會很慢，服務偶爾也會停止。 這種情況並不表明即時產品支付處理的速度和效率。

## Test

強烈建議您test [!DNL Payment Services] 在將此功能性向購物者公開之前，先使用真實信用卡和銀行進行生產。 即使測試 [!DNL Payment Services] 沙箱是重要的，生產測試是保證 [!DNL Payment Services] 按預期工作。

你可以test [!DNL Payment Services] 以兩種方式之一：

* 選擇您知道購物者不會下訂單的時間。
* 使用Webstore，該Webstore暫時無法訪問，但您可以訪問它進行測試。

使用真實信用卡和PayPal帳戶完成生產測試，測試付款的整個生命週期，包括捕獲和退款。 在測試期間完成整個結帳和付款流程，為您提供了最清晰的瞭解 [!DNL Payment Services] 當即時購物者使用時，功能將起作用。

您還應驗證在銀行對帳單上顯示的有關您在生產測試中使用的付款方法的資訊是否正確且預期（包括業務說明）。
