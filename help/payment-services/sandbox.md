---
title: 設定測試沙盒
description: 使用PayPal沙盒帳戶使用 [!DNL Payment Services] test。
exl-id: 99c14b4e-e6cf-48f9-9546-5c0d5c71464d
source-git-commit: 9596815e31402f23b399b223f3221074331c1773
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 0%

---

# 設定測試沙盒

在啟動入門沙盒之前，您必須註冊一個免費PayPal開發人員帳戶，並建立商家（用於入門）和購物者帳戶（用於測試結賬）。 如果需要，可以建立多個開發人員帳戶。

PayPal沙盒帳戶允許您使用 [!DNL Payment Services] test。 PayPal要求您使用PayPal開發人員門戶生成的業務沙盒test帳戶、電子郵件和密碼進行沙盒登錄。 在沙盒登錄過程中不要建立其他帳戶。

如果在沙盒PayPal登機過程中建立了帳戶，則必須重置登機沙盒，因為或無法驗證電子郵件。

要重置沙盒帳戶：

1. 按一下 **[!UICONTROL Reset sandbox]**. 查看 [PayPal建立業務沙盒帳戶](https://developer.paypal.com/docs/api-basics/sandbox/accounts/#create-a-business-sandbox-account) 的子菜單。
1. 按一下 **[!UICONTROL Sandbox onboarding]** 並完成後續步驟。

要完成入門沙盒操作：

1. 導航到 [PayPal開發人員帳戶頁](https://developer.paypal.com/developer/accounts/)。
1. 按一下 **[!UICONTROL Log in to Home]** 並使用您的現有憑據登錄PayPal開發人員帳戶，或按一下 **註冊** 建立帳戶。
1. 建立PayPal沙盒帳戶：
   1. 轉到 _[!UICONTROL SANDBOX]_>**[!UICONTROL Accounts]**。
   1. 按一下 **[!UICONTROL Create account]**.
   1. 選擇 **[!UICONTROL Business]** 作為「帳戶類型」，然後按一下 **[!UICONTROL Create]**。
   1. 在 _[!UICONTROL Sandbox Accounts]_中，按一下_[!UICONTROL Manage accounts]_ 建立的沙盒帳戶的列。
   1. 按一下 **[!UICONTROL View/edit account]**.

      ![PayPal — 檢視/編輯沙盒帳戶](assets/onboarding-viewedit-sandbox.png)

   1. 複製並保存電子郵件ID和系統生成的密碼，以供將來使用。

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**。
1. 按一下 **[!UICONTROL Sandbox onboarding]**.

   如果尚未完成的沙盒登錄，則此選項可見 [!DNL Payment Services]。

   自動生成沙盒商戶ID並將其填充到 [設定](settings.md)。 不要更改或更改此ID。

   您將收到一個PayPal窗口，用於連接PayPal帳戶以開始接受付款。

1. 輸入您的業務帳戶和國家或地區的電子郵件，然後按一下 **[!UICONTROL Next]**。

   ![PayPal — 連接PayPal付款帳戶](assets/paypal-connectacct.png)

1. 使用以前保存的沙盒帳戶憑據，繼續遵循PayPal流。
1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**。

   的 **[!UICONTROL Sandbox onboarding]** 按鈕不再可見，您會看到「沙盒付款掛起」文本。

當PayPal沙盒登錄獲得批准時，您應看到一則通知，指出您的付款系統當前處於沙盒模式且未處理即時付款。

>[!IMPORTANT]
>
>如果撤消對 [!DNL Payment Services] 為 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 處理付款時（在PayPal帳戶設定中），您的商店中的訂單無法由 [!DNL Payment Services]。

## 啟用聯繫電話號碼

聯繫電話號碼允許您獲取PayPal從客戶那裡收集的聯繫電話號碼。 PayPal總是從PayPal帳戶持有人處收集聯繫電話，以幫助確認他們的身份，並聯繫他們以解決他們帳戶上的問題或完成他們的履行過程。 不過，PayPal不鼓勵直接從商家使用聯繫電話，因為這可能對銷售產生負面影響。 查看 [PayPal獲取聯繫電話](https://developer.paypal.com/docs/admin/checkout-settings/#get-contact-telephone-numbers) 的子菜單。

此功能是 `off` 預設值。 啟用後，當客戶在結帳頁外完成「品牌結帳」流時，商店管理員可以看到電話號碼。

>[!IMPORTANT]
>
>此設定不適用於其他簽出流。

## Test沙盒環境

請參閱 [Test和驗證](test-validate.md) 的子菜單。
