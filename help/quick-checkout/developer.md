---
title: '"[!DNL Quick Checkout] 適用於Adobe Commerce開發人員資訊」'
description: '"[!DNL Quick Checkout] 開發人員資訊。」'
exl-id: 8926eda4-b4de-4938-a86c-b095616f61f6
source-git-commit: b89427124cf76e7f36076454949191ee1d88f52c
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# [!DNL Quick Checkout] 開發人員資訊

本主題包含與Adobe Commerce緊密合作的開發人員適用的資訊，以及 [!DNL Magento Open Source] 程式碼並想要瞭解有關的詳細資訊 [!DNL Quick Checkout] 副檔名。

## 延伸點

使用擴充功能點來自訂 [!DNL Quick Checkout].

透過使用擴充點，您可以進行自訂，而無需實際變更應用程式程式碼中的核心元件。

## 送貨詳細資料步驟

擴充點可用於在登入後自訂自動步驟導覽 [!DNL Bolt].

一旦購物者登入 [!DNL Bolt]，系統會預先填寫所有有效資訊，並重新導向至付款詳細資料步驟來下訂單。 請參閱 [結帳流程](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/manage-checkout/checkout-flow.html) 主題以取得詳細資訊。

此擴充點可防止導覽至付款步驟，而且當有擴充功能需要購物者對出貨步驟執行其他動作時，此擴充功能會很有用。 請參閱以下範例，瞭解如何搭配mixin使用擴充點：

1. 在中註冊新的mixin `require-config.js` 檔案位於 `app/code/Vendor/ModuleName/view/frontend/`.

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

1. 在中延伸模型 `can-navigate-to-payment.js` 檔案位於 `app/code/Vendor/ModuleName/view/frontend/web/js/model/`.

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
> 這是德國購物者(DE)希望停留在「運送詳細資料」步驟的範例。

Check [[!DNL Bolt] 開發人員說明](https://help.bolt.com/developers/) 有關下列專案的詳細資訊： [!DNL Bolt] 適用於開發人員。
