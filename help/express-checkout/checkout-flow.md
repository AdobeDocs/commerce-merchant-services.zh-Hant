---
title: 簽出流
description: 概述 [!DNL Express Checkout] 在Adobe Commerce。
exl-id: 82761627-a0d4-4cb0-aad1-9865fcb550d4
source-git-commit: bd9541c5e4810085ab85206b2ecca21e66800a2f
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# [!DNL Express Checkout] 流

>[!IMPORTANT]
>
> 此功能僅適用於早期採用者計畫(EAP)用戶，尚不適用於所有客戶。 目前僅限於美國客戶。 請聯繫Adobe Commerce支援部門以獲取幫助和問題。

本節概述了使用 [!DNL Express Checkout] Adobe Commerce分機。

成功 [!DNL Express Checkout] 流包含以下步驟：

1. 開啟店面，在購物車中添加物品。
1. 繼續簽出。

![簽出](assets/proceed-checkout.png)

1. 當出現提示時，輸入與 [!DNL Bolt] 帳戶。
1. 輸入發送到該密碼的一次性密碼(OTP) [!DNL Bolt] 帳戶的電子郵件地址或電話號碼。
1. 一旦使用 [!DNL Bolt] 帳戶，結帳詳細資訊自動填寫：

   - 裝運資訊
   - 付款方式

   >[!NOTE]
   >
   > 即使您的結帳詳細資訊自動填寫，您也可以使用現有的錢夾資訊（地址或信用卡資訊）。

1. 下訂單。

的 [!DNL Express Checkout] 與標準的附加Adobe Commerce結帳選項相容，如 [禮品卡](https://docs.magento.com/user-guide/catalog/product-gift-card.html) 或 [折扣代碼](https://docs.magento.com/user-guide/marketing/price-rules-cart-coupon.html)。

## [!DNL Express Checkout] 使用案例

的 [!DNL Express Checkout] 允許在簽出流程中使用多個用例：

- 已註冊的來賓用戶 [!DNL Bolt] 帳戶。
- 新來賓用戶 [!DNL Bolt] 帳戶。
- 已註冊/未註冊的現有Adobe Commerce用戶 [!DNL Bolt] 帳戶。

## 來賓用戶簽出：它的工作原理

來賓簽出體驗與登錄體驗不同。 當購物者將電子郵件地址輸入結帳時， [!DNL Express Checkout] 驗證它以查找現有 [!DNL Bolt] 帳戶。

### 已註冊 [!DNL Bolt] 帳戶

如果 [!DNL Bolt] 顧客會繼續 [!DNL Express Checkout] 無縫的結賬體驗：

1. 輸入發送到該密碼的一次性密碼(OTP) [!DNL Bolt] 帳戶的電子郵件地址或移動地址，具體取決於 [!DNL Bolt] 帳戶。
1. 一旦使用 [!DNL Bolt] 帳戶，它自動填寫結帳詳細資訊：

   - 裝運資訊
   - 付款方式

1. 下訂單。

>[!TIP]
>
> 來賓用戶下訂單，可在Adobe Commerce註冊。

### 新建 [!DNL Bolt] 帳戶

否 [!DNL Bolt] 找到帳戶後，購物者會繼續執行預設的開箱外結賬，而購物者會提供所有必要的詳細資訊來訂購：

- 發運和開單資訊
- 裝運方法
- 複核付款方法
- 出現一個複選框以註冊 [!DNL Bolt] 以加快簽出速度，然後下訂單。 他們可以同意建立他們的 [!DNL Bolt] 帳戶。

   ![記住 [!DNL Bolt]](assets/checked-bolt.png)

- 來賓用戶下訂單，可在Adobe Commerce註冊。

## 現有Adobe Commerce用戶：它的工作原理

現有用戶可以在用戶將訂單與 [!DNL Express Checkout] 更快的結帳體驗。

當購物者將電子郵件地址輸入結帳時， [!DNL Express Checkout] 驗證它以查找現有 [!DNL Bolt] 帳戶。

### 已註冊 [!DNL Bolt] 與Adobe Commerce用戶的帳戶

如果 [!DNL Bolt] 找到帳戶後，購物者會繼續執行預設的開箱外結賬，購物者會提供所有必要的詳細資訊，然後下單：

- 發運和開單資訊
- 裝運方法
- 複核付款方法

請參閱 [故障排除](../express-checkout/troubleshooting.md) 主題，以獲取現有的Adobe Commerce用戶身份下訂單時遇到的問題。

>[!NOTE]
>
> 如果用戶具有 [!DNL Bolt] 帳戶和電子郵件在Adobe Commerce未註冊，它觸發一次性密碼(OTP)登錄。 查看 [註冊 [!DNL Bolt] 帳戶](#registered-bolt-account) 。

### 新建 [!DNL Bolt] 帳戶

否 [!DNL Bolt] 找到帳戶後，購物者繼續其預設的Adobe Commerce結帳，購物者從保存的資訊中選擇所有必要的詳細資訊來下訂單：

- 發運和開單資訊
- 裝運方法
- 複核付款方法
- 出現一個複選框以註冊 [!DNL Bolt] 以加快簽出速度，然後下訂單。 他們可以同意建立他們的 [!DNL Bolt] 帳戶。

   ![記住 [!DNL Bolt]](assets/checked-bolt.png)

## 獲取幫助

聯繫人 [!DNL Adobe Commerce] 工程團隊通過您指定的Slack [AdobeBeta程式渠道](http://adobe-beta-programs.slack.com/) 尋求任何幫助。
