---
title: 「Adobe Commerce中Bolt使用者的結帳流程」
description: 概述 [!DNL Quick Checkout] Adobe Commerce中Bolt使用者的流程。
exl-id: 12f58b7e-1f86-4891-b225-9f4be82c2d5d
feature: Checkout, Services, Storefront
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# 訪客使用者

訪客結帳體驗與Adobe使用者體驗不同。 當購物者輸入電子郵件地址進行結帳時， [!DNL Quick Checkout] 驗證並尋找現有的 [!DNL Bolt] 帳戶。

>[!WARNING]
>
> 此 [!DNL In-Store Pickup] (ISPU)功能不支援，當 [!DNL Quick Checkout] 已啟用。

## 已註冊 [!DNL Bolt] 帳戶

若為 [!DNL Bolt] 找到帳戶，購物者會繼續使用 [!DNL Quick Checkout] 順暢的結帳體驗：

1. 輸入傳送至該的一次性密碼(OTP) [!DNL Bolt] 帳戶的電子郵件地址或行動電話，具體取決於 [使用者在「 」中的偏好設定 [!DNL Bolt] 帳戶](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}.

![OTP快顯視窗](assets/new-logo-otp-email.png)

1. 使用登入後 [!DNL Bolt] 帳戶，則會自動新增詳細資料：

   - 送貨資訊
   - 付款方式

1. 下訂單。

>[!TIP]
>
> 訪客使用者下訂單，並可選擇在Adobe Commerce中註冊。

## 新增 [!DNL Bolt] 帳戶

若否 [!DNL Bolt] 找到帳戶後，購物者會繼續使用預設的開箱即用Adobe Commerce結帳，而購物者提供下單所需的所有細節：

- 送貨與帳單資訊
- 送貨方法
- 檢閱付款方式
- 出現一個核取方塊，表示註冊於 [!DNL Bolt] ，以便在下訂單前更快結帳。 購物者可以同意建立其購物網站的相關條款與條件 [!DNL Bolt] 帳戶。
- 訪客使用者下訂單，並可選擇在Adobe Commerce中註冊。
