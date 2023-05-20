---
title: "Adobe Commerce用戶的簽出流"
description: 「概述 [!DNL Quick Checkout] 流向Adobe Commerce用戶。」
exl-id: 085e393b-15f6-4d5a-a04d-927b1f95b74e
source-git-commit: f790732804e110aad298689c0ddf74547ff17618
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# 現有Adobe Commerce用戶：它的工作原理

現有Adobe Commerce用戶在將訂單與 [!DNL Quick Checkout] 更快的結帳體驗。

當購物者在結帳時輸入其電子郵件地址時， [!DNL Quick Checkout] 驗證並查找現有 [!DNL Bolt] 帳戶。

## 在Adobe Commerce和 [!DNL Bolt]

當購物者是Adobe Commerce和 [!DNL Bolt] 提供儲存的運輸和付款詳細資訊。

如果 [!DNL Bolt] 結帳時，購物者可繼續其帳戶 [!DNL Quick Checkout] 無縫的結賬體驗：

1. 輸入發送到該密碼的一次性密碼(OTP) [!DNL Bolt] 帳戶的電子郵件地址或移動地址，具體取決於 [中的用戶首選項 [!DNL Bolt] 帳戶](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}。

![OTP彈出窗口](assets/new-logo-otp-email.png)

1. 一旦使用 [!DNL Bolt] 帳戶，詳細資訊會自動添加：

   - 裝運資訊
   - 付款方式

1. 下訂單。

>[!NOTE]
>
> 僅當購物者在結帳頁上時，才會顯示「螺栓OTP」彈出窗口。 購物者可通過關閉彈出窗口選擇不登錄Bolt。

如果購物者在結帳前登錄Adobe Commerce, [!DNL Bolt] OTP彈出窗口在結帳期間不會出現，但會出現一條消息，建議購物者登錄以訪問其螺栓錢包。

如果以現有Adobe Commerce用戶身份下單時遇到問題，請參閱 [排除快速簽出問題](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) 在Adobe Commerce幫助中心。

## 自動登錄

「自動登錄」元件檢測購物者何時具有活動的Bolt會話並自動登錄購物者。 這會跳過帳戶檢測和一次性密碼(OTP)步驟，因為購物者在上一會話中完成了這些步驟。

可以為配置自動登錄 [!DNL Quick Checkout] 。 您可以啟用配置以在簽出期間自動登錄用戶。

1. 在 _管理_ 邊欄，導航 **商店** > **配置** > **簽出** 訪問常規「簽出管理」配置頁。
1. 在 _服務設定_ 節 [!DNL Quick Checkout]，提供設定自動登錄所需的所有詳細資訊。

請參閱 [[!DNL Quick Checkout] 配置服務設定](../quick-checkout/onboarding.md#configure-service-settings) 的子菜單。

>[!NOTE]
>
> 首次登錄時 **自動登錄** 啟用時需要用戶同意通過接受彈出窗口來授權。

## 新建 [!DNL Bolt] 帳戶

否 [!DNL Bolt] 找到帳戶後，購物者繼續執行預設的開箱外Adobe Commerce結賬，購物者從保存的資訊中選擇所有必要的詳細資訊來下訂單：

- 發運和開單資訊
- 裝運方法
- 複核付款方法
- 註冊的選項 [!DNL Bolt] 在下訂單之前，將顯示更快的檢出。 購物者可以同意條款和條件來建立 [!DNL Bolt] 帳戶。

   ![記住 [!DNL Bolt]](assets/checkbox-remember-bolt.png)
