---
title: '"[!DNL Quick Checkout] Adobe Commerce開發人員資訊」'
description: '"[!DNL Quick Checkout] 開發商資訊。」'
exl-id: 8926eda4-b4de-4938-a86c-b095616f61f6
source-git-commit: 9841db7616c8aa6d5bc5af3e6e92c0abe9a4a1e2
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 0%

---

# [!DNL Quick Checkout] 開發者資訊

本主題包含與Adobe Commerce和Magento Open Source代碼密切合作並希望瞭解有關 [!DNL Quick Checkout] 擴展。

## 擴展點

使用擴展點定制 [!DNL Quick Checkout]。

通過使用擴展點，您可以進行自定義，而無需實際更改應用程式碼中的核心元件。

## 發運詳細資訊步驟

擴展點可用於在登錄後自定義自動步驟導航 [!DNL Bolt]。

一旦購物者登錄 [!DNL Bolt]，所有有效資訊都會預先填寫並重定向到付款詳細資訊步驟以下達訂單。 查看 [簽出流](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/manage-checkout/checkout-flow.html) 的子菜單。

此擴展點允許阻止導航到付款步驟，並且在存在需要購物者在發運步驟上執行附加操作的擴展時非常有用。 有關如何將擴展點與混合使用的示例，請參閱下面的示例：

1. 在中註冊新混音 `require-config.js` 檔案位於 `app/code/Vendor/ModuleName/view/frontend/`。

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

1. 在 `can-navigate-to-payment.js` 檔案位於 `app/code/Vendor/ModuleName/view/frontend/web/js/model/`。

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
> 這是德國(DE)中希望保持「發運詳細資訊」步驟的購物者的示例。

檢查 [[!DNL Bolt] 開發者幫助](https://help.bolt.com/developers/) 的 [!DNL Bolt] 為開發人員準備。
