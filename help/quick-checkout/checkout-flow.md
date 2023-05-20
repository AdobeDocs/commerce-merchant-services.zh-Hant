---
title: "Adobe Commerce結帳流"
description: 「概述 [!DNL Quick Checkout] Adobe Commerce。」
exl-id: 82761627-a0d4-4cb0-aad1-9865fcb550d4
source-git-commit: f790732804e110aad298689c0ddf74547ff17618
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# [!DNL Quick Checkout] 流

本節概述了使用 [!DNL Quick Checkout] Adobe Commerce分機。

成功 [!DNL Quick Checkout] 流包含以下步驟：

1. 開啟店面，在購物車中添加物品。
1. 繼續簽出。

![簽出](assets/proceed-checkout.png)

>[!NOTE]
>
> 您可以為商家啟用自動登錄。 請參閱 [Bolt的「啟用自動登錄」主題](https://help.bolt.com/products/embedded/direct-api/auto-login/) 的子菜單。

1. 當出現提示時，輸入與 [!DNL Bolt] 帳戶。
1. 輸入發送到該密碼的一次性密碼(OTP) [!DNL Bolt] 帳戶的電子郵件地址或電話號碼。

![OTP彈出窗口](assets/new-logo-otp-email.png)

1. 一旦使用 [!DNL Bolt] 帳戶，結帳詳細資訊自動填寫：

   - 裝運資訊
   - 付款方式

   >[!NOTE]
   >
   > 即使您的結帳詳細資訊自動填寫，您也可以使用現有的錢夾資訊（地址或信用卡資訊）。

1. 下訂單。

的 [!DNL Quick Checkout] 與標準的附加Adobe Commerce結帳選項相容，如 [禮品卡](https://docs.magento.com/user-guide/catalog/product-gift-card.html) 或 [折扣代碼](https://docs.magento.com/user-guide/marketing/price-rules-cart-coupon.html)。

## [!DNL Quick Checkout] 使用案例

的 [!DNL Quick Checkout] 允許在簽出流程中使用多個用例：

- [來賓用戶](../quick-checkout/checkout-bolt.md) 註冊或新 [!DNL Bolt] 帳戶。
- 現有 [Adobe Commerce用戶](../quick-checkout/checkout-adobe-commerce.md) 有或沒有註冊 [!DNL Bolt] 帳戶。

## 獲取幫助

通過以下網站與Adobe Commerce支援部門聯繫： [Adobe Commerce幫助中心](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html) 尋求任何幫助。
