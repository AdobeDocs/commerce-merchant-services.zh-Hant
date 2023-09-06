---
title: 「Adobe Commerce使用者的結帳流程」
description: 「概述 [!DNL Quick Checkout] Adobe Commerce使用者的流量。」
exl-id: 085e393b-15f6-4d5a-a04d-927b1f95b74e
feature: Checkout, Services, Storefront
source-git-commit: 6ba5a283d9138b4c1be11b80486826304c63247f
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# 現有Adobe Commerce使用者：運作方式

現有的Adobe Commerce使用者可在下訂單時選取已儲存的送貨和付款詳細資料 [!DNL Quick Checkout] 以獲得更快的結帳體驗。

當購物者在結帳時輸入其電子郵件地址時， [!DNL Quick Checkout] 驗證並找到現有的 [!DNL Bolt] 帳戶。

## 在Adobe Commerce和中的註冊使用者 [!DNL Bolt]

當購物者同時是Adobe Commerce和中的註冊使用者時 [!DNL Bolt] 網路，這兩個網路都提供儲存的送貨和付款詳細資料。

如果 [!DNL Bolt] 結帳時找到帳戶，購物者可以繼續使用他們的 [!DNL Quick Checkout] 順暢的結帳體驗：

1. 輸入傳送至該的一次性密碼(OTP) [!DNL Bolt] 帳戶的電子郵件地址或行動裝置，具體取決於 [使用者在「 」中的偏好設定 [!DNL Bolt] 帳戶](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}.

![OTP快顯視窗](assets/new-logo-otp-email.png){width="300" zoomable="yes"}

1. 使用登入後 [!DNL Bolt] 帳戶，則會自動新增詳細資料：

   - 送貨資訊
   - 付款方式

1. 下訂單。

>[!NOTE]
>
> 只有當購物者位於結帳頁面時，才會出現「螺栓OTP」快顯視窗。 購物者可以關閉該快顯視窗，選擇退出登入Bolt。

如果購物者在結帳前登入Adobe Commerce，則 [!DNL Bolt] 結帳期間不會出現OTP快顯視窗，但會顯示一則訊息，建議購物者登入以存取其Bolt Wallet。

如果您以現有Adobe Commerce使用者身分下達訂單時遇到問題，請參閱 [疑難排解Quick Checkout問題](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) Adobe Commerce說明中心中的文章。

## 自動登入

自動登入元件會偵測購物者何時具有作用中的Bolt工作階段，並自動將購物者登入。 這會略過帳戶偵測和一次性密碼(OTP)步驟，因為購物者已在先前的作業階段中完成這些步驟。

您可以設定自動登入 [!DNL Quick Checkout] 使用者。 您可以啟用配置以在簽出時自動登入使用者。

1. 在 _管理員_ 側欄，瀏覽至 **商店** > **設定** > **簽出** 以存取一般簽出管理設定頁面。
1. 在 _服務設定_ 「 」部分 [!DNL Quick Checkout]，提供設定自動登入所需的所有詳細資訊。

另請參閱 [[!DNL Quick Checkout] 設定服務設定](../quick-checkout/onboarding.md#configure-service-settings) 主題以取得詳細資訊。

>[!NOTE]
>
> 首次登入時間 **自動登入** 是否啟用需要使用者同意，才能透過接受快顯視窗來授權啟用。

## 新增 [!DNL Bolt] 帳戶

若否 [!DNL Bolt] 找到帳戶後，購物者會繼續使用預設的現成Adobe Commerce結帳，購物者會從其儲存的資訊中選取所有必要的詳細資料來下訂單：

- 送貨與帳單資訊
- 送貨方法
- 複查付款方式
- 要註冊的選項 [!DNL Bolt] 在下訂單前快速結帳。 購物者可以同意條款與條件來建立其 [!DNL Bolt] 帳戶。

  ![記住 [!DNL Bolt]](assets/checkbox-remember-bolt.png){width="300" zoomable="yes"}
