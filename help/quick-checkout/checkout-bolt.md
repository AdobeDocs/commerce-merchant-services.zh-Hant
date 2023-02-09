---
title: 「Bolt使用者在Adobe Commerce的結帳流程」
description: 概觀 [!DNL Quick Checkout] 在Adobe Commerce中為Bolt使用者傳送流量。
exl-id: 12f58b7e-1f86-4891-b225-9f4be82c2d5d
source-git-commit: 66082614ffe6456e2c24a1e8d9baaa1113fb7ffb
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# 來賓用戶

訪客結帳體驗與Adobe使用者體驗不同。 當購物者進入結帳的電子郵件地址時， [!DNL Quick Checkout] 驗證它並查找現有 [!DNL Bolt] 帳戶。

>[!WARNING]
>
> 此 [!DNL In-Store Pickup] 當 [!DNL Quick Checkout] 啟用。

## 已註冊 [!DNL Bolt] 帳戶

若 [!DNL Bolt] 帳戶，購物者會繼續使用 [!DNL Quick Checkout] 順暢的結帳體驗：

1. 輸入發送給該密碼的一次性密碼(OTP) [!DNL Bolt] 帳戶的電子郵件地址或行動裝置，視 [使用者的偏好設定(位於 [!DNL Bolt] 帳戶](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}.

![OTP快顯視窗](assets/pop-up.png)

1. 使用 [!DNL Bolt] 帳戶時，系統會自動新增詳細資訊：

   - 裝運資訊
   - 付款方法

1. 下訂單。

>[!TIP]
>
> 訪客使用者下訂單，且可以選擇在Adobe Commerce中註冊。

## 新增 [!DNL Bolt] 帳戶

若否 [!DNL Bolt] 找到帳戶後，購物者會繼續其預設的現成Adobe Commerce結帳，而購物者會提供所有必要的詳細資料以下訂單：

- 運費和帳單資訊
- 裝運方法
- 複核付款方法
- 將出現一個要註冊的複選框 [!DNL Bolt] 以在下訂單前加快結帳。 購物者可同意條款與條件，以建立其 [!DNL Bolt] 帳戶。

   ![記住 [!DNL Bolt]](assets/checkbox-remember-bolt.png)

- 訪客使用者下訂單，且可以選擇在Adobe Commerce中註冊。
