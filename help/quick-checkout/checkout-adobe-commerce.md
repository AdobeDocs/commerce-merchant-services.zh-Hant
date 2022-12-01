---
title: "Adobe Commerce使用者的結帳流程"
description: 「 [!DNL Quick Checkout] Adobe Commerce使用者的流量。」
exl-id: 085e393b-15f6-4d5a-a04d-927b1f95b74e
source-git-commit: 1f2305df7566cd77a6be161cc9d1265c0291171c
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 現有Adobe Commerce使用者：運作方式

現有的Adobe Commerce使用者可在使用 [!DNL Quick Checkout] 更快速的結帳體驗。

當購物者在結帳時輸入其電子郵件地址時， [!DNL Quick Checkout] 驗證它並查找現有 [!DNL Bolt] 帳戶。

## Adobe Commerce和 [!DNL Bolt]

當購物者是Adobe Commerce和 [!DNL Bolt] 網路中，兩個網路都被儲存運費和支付詳情。

若 [!DNL Bolt] 帳戶在結帳期間，購物者可繼續使用 [!DNL Quick Checkout] 順暢的結帳體驗：

1. 輸入發送給該密碼的一次性密碼(OTP) [!DNL Bolt] 帳戶的電子郵件地址或行動裝置，視 [使用者的偏好設定(位於 [!DNL Bolt] 帳戶](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}。

![OTP快顯視窗](assets/pop-up.png)

1. 使用 [!DNL Bolt] 帳戶時，系統會自動新增詳細資訊：

   - 裝運資訊
   - 付款方法

1. 下訂單。

>[!NOTE]
>
> 只有當購物者位於結帳頁面時，才會顯示「螺栓OTP」快顯視窗。 購物者可以關閉該快顯視窗，選擇退出登入Bolt。

如果購物者在結帳前已登入Adobe Commerce，則 [!DNL Bolt] OTP快顯視窗在結帳期間不會顯示，但會顯示訊息，建議購物者登入以存取其Bolt Wallet。

如果您在以現有Adobe Commerce使用者的身分下訂單時遇到問題，請參閱 [疑難排解快速結帳問題](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) 文章(在Adobe Commerce說明中心)。

## 新增 [!DNL Bolt] 帳戶

若否 [!DNL Bolt] 找到帳戶後，購物者會繼續其預設的現成Adobe Commerce結帳，而購物者會從其儲存的資訊中選取所有必要的詳細資訊以下訂單：

- 運費和帳單資訊
- 裝運方法
- 複核付款方法
- 登入的選擇 [!DNL Bolt] 以在下訂單前加快結帳。 購物者可同意條款與條件，以建立其 [!DNL Bolt] 帳戶。

   ![記住 [!DNL Bolt]](assets/checkbox-remember-bolt.png)
