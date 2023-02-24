---
title: '"[!DNL Quick Checkout] Adobe Commerce開發人員資訊」'
description: '"[!DNL Quick Checkout] 開發人員資訊。」'
exl-id: 8926eda4-b4de-4938-a86c-b095616f61f6
source-git-commit: b89427124cf76e7f36076454949191ee1d88f52c
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# [!DNL Quick Checkout] 開發人員資訊

本主題包含與Adobe Commerce密切合作的開發人員的相關資訊，以及 [!DNL Magento Open Source] 程式碼，並想了解 [!DNL Quick Checkout] 擴充功能。

## 延伸點

使用擴充點來自訂 [!DNL Quick Checkout].

使用擴充功能點，您就可以自訂內容，而實際上不需變更應用程式程式碼中的核心元件。

## 發運詳細資訊步驟

擴充點可用來自訂在使用登入後的自動步驟導覽 [!DNL Bolt].

購物者登入後 [!DNL Bolt]，所有有效資訊都會預填並重新導向至付款詳細資料步驟以下單。 請參閱 [結帳流程](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/manage-checkout/checkout-flow.html) 主題以取得詳細資訊。

此擴充點可防止導覽至付款步驟，且在有需要購物者在運送步驟上執行其他動作的擴充功能時，此功能相當實用。 請參閱下列範例，了解如何搭配mixin使用擴充功能點：

1. 在 `require-config.js` 位於 `app/code/Vendor/ModuleName/view/frontend/`.

   ```js
   var config = {
       config: {
           mixins: {
               "Magento_ExpressCheckout/js/model/can-navigate-to-payment": {
                   "Vendor/ModuleName/js/model/can-navigate-to-payment-mixin": true
               }
           }
       }
   };
   ```

1. 在 `can-navigate-to-payment.js` 位於 `app/code/Vendor/ModuleName/view/frontend/web/js/model/`.

   ```js
   define([
       'Magento_Checkout/js/model/quote',
       'mage/utils/wrapper',
   ], function (quote, wrapper) {
       'use strict';
       return function (canNavigateToPayment) {
           return wrapper.wrap(canNavigateToPayment, function (originalAction) {
               /* Include custom checks or conditions to stay on the shipping step,i.e: your shopper is from Germany */
               return originalAction() && quote.shippingAddress().countryId !== 'DE');
           });
       };
   });
   ```

>[!WARNING]
>
> 這是德國(DE)中想停留在「運送詳細資訊」步驟的購物者的範例。

檢查 [[!DNL Bolt] 開發人員說明](https://help.bolt.com/developers/) 如需詳細資訊，請參閱 [!DNL Bolt] 供開發人員使用。
