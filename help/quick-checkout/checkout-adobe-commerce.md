---
title: 簽出流
description: 概述 [!DNL Quick Checkout] 為Adobe Commerce用戶流。
exl-id: 085e393b-15f6-4d5a-a04d-927b1f95b74e
source-git-commit: a95d2ed92c69feba03d1b84d44abf08c1d1b4029
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# 現有Adobe Commerce用戶：它的工作原理

現有Adobe Commerce用戶在將訂單與 [!DNL Quick Checkout] 更快的結帳體驗。

當購物者在結帳時輸入其電子郵件地址時， [!DNL Quick Checkout] 驗證並查找現有 [!DNL Bolt] 帳戶。

## 在Adobe Commerce和 [!DNL Bolt]

當購物者是Adobe Commerce和 [!DNL Bolt] 提供儲存的運輸和付款詳細資訊。

如果 [!DNL Bolt] 結帳時，購物者可繼續其帳戶 [!DNL Quick Checkout] 無縫的結賬體驗：

1. 輸入發送到該密碼的一次性密碼(OTP) [!DNL Bolt] 帳戶的電子郵件地址或移動地址，具體取決於 [中的用戶首選項 [!DNL Bolt] 帳戶](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}。

![OTP彈出窗口](assets/pop-up.png)

1. 一旦使用 [!DNL Bolt] 帳戶，詳細資訊會自動添加：

   - 裝運資訊
   - 付款方式

1. 下訂單。

>[!NOTE]
>
> 僅當購物者在結帳頁上時，才會顯示「螺栓OTP」彈出窗口。 購物者可通過關閉彈出窗口選擇不登錄Bolt。

如果購物者在結帳前登錄Adobe Commerce, [!DNL Bolt] 在簽出期間不會顯示OTP彈出窗口。

如果以現有Adobe Commerce用戶身份下單時遇到問題，請參閱 [排除快速簽出問題](https://support.magento.com/hc/en-us/articles/6909450342541) 在Adobe Commerce幫助中心。

## 新建 [!DNL Bolt] 帳戶

否 [!DNL Bolt] 找到帳戶後，購物者繼續執行預設的開箱外Adobe Commerce結賬，購物者從保存的資訊中選擇所有必要的詳細資訊來下訂單：

- 發運和開單資訊
- 裝運方法
- 複核付款方法
- 註冊的選項 [!DNL Bolt] 在下訂單之前，將顯示更快的檢出。 購物者可以同意條款和條件來建立 [!DNL Bolt] 帳戶。

   ![記住 [!DNL Bolt]](assets/checkbox-remember-bolt.png)
