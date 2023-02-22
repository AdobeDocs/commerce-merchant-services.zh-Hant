---
title: 設定測試沙箱
description: 使用PayPal沙箱帳戶來使用 [!DNL Payment Services] 在測試模式中。
exl-id: 99c14b4e-e6cf-48f9-9546-5c0d5c71464d
source-git-commit: 817a01e98876bddf5f41a253501984539b3351cd
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 0%

---

# 設定測試沙箱

在開始建立沙箱之前，您必須註冊免費的PayPal開發人員帳戶，並同時建立商家帳戶（以用於上線）和購物者帳戶（以用於測試結帳）。 您可以視需要建立多個開發人員帳戶。

PayPal沙箱帳戶可讓您使用 [!DNL Payment Services] 在測試模式中。 PayPal要求您使用PayPal開發人員入口網站產生的商業沙箱測試帳戶、電子郵件和密碼，以便沙箱上線。 *在沙箱上線程式期間，請勿建立其他帳戶。*

## 沙箱上線

若要完成沙箱上線：

1. 導覽至 [PayPal開發人員帳戶頁面](https://developer.paypal.com/developer/accounts/).
1. 按一下 **[!UICONTROL Log in to Dashboard]** 並使用您現有的PayPal開發人員入口網站產生的商業沙箱測試帳戶登入，或按一下 **註冊** 來建立帳戶。
1. 建立PayPal沙箱帳戶：
   1. 前往 _[!UICONTROL Testing Tools]_>**[!UICONTROL Sandbox Accounts]**.
   1. 按一下 **[!UICONTROL Create account]**.

      如果您在沙箱PayPal上線程式期間建立了PayPal沙箱帳戶，則您必須 [重設您的上線沙箱](#reset-your-sandbox-account) 因為或者你無法驗證你的電子郵件。

   1. 選擇 **[!UICONTROL Business]** 作為「帳戶類型」，然後按一下 **[!UICONTROL Create]**.
   1. 在 _[!UICONTROL Sandbox Accounts]_區段中，按一下_[!UICONTROL Manage accounts]_ 欄。
   1. 按一下 **[!UICONTROL View/edit account]**.

      ![PayPal — 檢視/編輯沙箱帳戶](assets/onboarding-viewedit-sandbox.png)

   1. 複製並儲存電子郵件ID和系統產生的密碼，以供日後使用。

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 按一下 **[!UICONTROL Sandbox onboarding]**.

   如果您尚未完成的沙箱上線，則會顯示此選項 [!DNL Payment Services].

   沙箱商戶ID會自動產生並填入 [設定](settings.md). 請勿變更或更改此ID。

   您將看到一個PayPal窗口，用於連接PayPal帳戶以開始接受付款。

1. 輸入您在步驟3中生成的PayPal沙箱帳戶（而非您的PayPal業務帳戶資訊）以及您的國家/地區的電子郵件和密碼。
1. 按一下 **[!UICONTROL Next]**.

   ![PayPal - Connect PayPal支付帳戶](assets/paypal-connectacct.png)

1. 使用您先前儲存的沙箱帳戶憑證，繼續遵循PayPal流程。
1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   此 **[!UICONTROL Sandbox onboarding]** 按鈕不再顯示，您會看到「沙箱付款待定」文字。

核准PayPal沙箱上線後，您應會看到通知，指出您的付款系統目前處於沙箱模式，且未處理即時付款。

>[!IMPORTANT]
>
>如果您撤銷 [!DNL Payment Services] for [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 對於處理您的付款（在您的PayPal帳戶設定中），您商店中的訂單無法由 [!DNL Payment Services]. 在您的「支付服務」首頁上，會顯示有關已撤銷同意的警報。 若要關閉警報，請按一下 **[!UICONTROL Do not show again]**.

### 重設您的沙箱帳戶

如果您在沙箱PayPal上線程式期間建立了PayPal沙箱帳戶，則您必須重設上線沙箱，因為或無法驗證電子郵件。

重設沙箱帳戶：

1. 按一下 **[!UICONTROL Reset sandbox]**. [建立PayPal商業沙箱帳戶](https://developer.paypal.com/docs/api-basics/sandbox/accounts/#create-a-business-sandbox-account).
1. 按一下 **[!UICONTROL Sandbox onboarding]** 並完成下一組步驟。

## 啟用聯繫電話號碼

聯繫電話號碼允許您獲取PayPal從客戶收集的聯繫電話號碼。 PayPal總是從PayPal賬戶持有者收集聯繫電話，以幫助確認其身份，並聯繫他們以解決其賬戶上的問題，或完成其履行流程。 不過，PayPal不鼓勵直接從商家使用聯繫電話號碼，因為這可能對銷售產生負面影響。 請參閱 [PayPal獲取聯繫電話](https://developer.paypal.com/docs/admin/checkout-settings/#get-contact-telephone-numbers) 檔案以取得詳細資訊。

此功能為 `off` 依預設。 若您啟用此功能，當客戶在結帳頁面外完成「品牌結帳」流程時，商店管理員就會看到電話號碼。

>[!IMPORTANT]
>
>此設定不適用於其他結帳流程。

## 在沙箱環境中測試

請參閱 [測試和驗證](test-validate.md) 以取得更多資訊。
