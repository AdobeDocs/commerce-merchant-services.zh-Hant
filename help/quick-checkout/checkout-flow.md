---
title: 「Adobe Commerce中的結帳流程」
description: 「概述 [!DNL Quick Checkout] Adobe Commerce中的流量。」
exl-id: 82761627-a0d4-4cb0-aad1-9865fcb550d4
feature: Checkout, Services, Storefront
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# [!DNL Quick Checkout] 流量

本節提供一般簽出體驗的概觀，使用 [!DNL Quick Checkout] 適用於Adobe Commerce擴充功能。

成功 [!DNL Quick Checkout] 流程包含下列步驟：

1. 開啟您的店面，並在購物車中新增商品。
1. 繼續結帳。

![簽出](assets/proceed-checkout.png)

>[!NOTE]
>
> 您可以為商家啟用自動登入。 另請參閱 [Bolt的啟用自動登入主題](https://help.bolt.com/products/embedded/direct-api/auto-login/) 以取得詳細資訊。

1. 出現提示時，輸入與關聯的電子郵件地址 [!DNL Bolt] 帳戶。
1. 輸入傳送至該的一次性密碼(OTP) [!DNL Bolt] 帳戶的電子郵件地址或電話號碼。

![OTP快顯視窗](assets/new-logo-otp-email.png)

1. 使用登入後 [!DNL Bolt] 帳戶，簽出詳細資料會自動填寫：

   - 送貨資訊
   - 付款方式

   >[!NOTE]
   >
   > 您可以使用現有的公事包資訊（地址或信用卡資訊），即使您的結帳詳細資訊已自動填入。

1. 下單。

此 [!DNL Quick Checkout] 與標準的其他Adobe Commerce簽出選項相容，例如 [禮品卡](https://docs.magento.com/user-guide/catalog/product-gift-card.html) 或 [折扣代碼](https://docs.magento.com/user-guide/marketing/price-rules-cart-coupon.html).

## [!DNL Quick Checkout] 使用案例

此 [!DNL Quick Checkout] 允許在結帳流程期間進行多個使用案例：

- [訪客使用者](../quick-checkout/checkout-bolt.md) 具有已註冊或新的 [!DNL Bolt] 帳戶。
- 現有 [Adobe Commerce使用者](../quick-checkout/checkout-adobe-commerce.md) 無論是否具有已註冊的 [!DNL Bolt] 帳戶。

## 取得協助

聯絡Adobe Commerce支援，透過 [Adobe Commerce說明中心](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html) 以取得任何協助。
