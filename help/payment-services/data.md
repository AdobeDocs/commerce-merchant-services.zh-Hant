---
title: 可用資料
description: 使用financial reporting資料來調解與非商務系統的報告。
role: User
level: Intermediate
source-git-commit: 1186b4e52f1d613332a7862c58f482c2591e29a8
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# 可用資料

您可以使用某些訂單和付款資料，以便跨外部系統協調Adobe Commerce財務報告。

## 與ERP系統協調

您可以使用與特定訂單關聯的增量ID，將Adobe Commerce財務報告與非Adobe企業資源計畫(ERP)系統進行調節。

當Payment Services將商務訂單傳送至PayPal時，增加的ID會納入為 `custom_id`. 此 `custom_id` 顯示在商家活動詳細資訊中，以取得付款，並顯示在PayPal網頁鈎點中。

`custom_id` 在商家活動詳細資訊的底部進行支付：

![`custom_id` 在商家活動詳細資訊中](assets/merchant-activity.png)

`custom_id` 在PayPal的Webhook中：

```json
   ...
   },
   "seller_protection": {
   "status": "NOT_ELIGIBLE"
   },
   "create_time": "2022-08-28T21:06:53Z",
   "custom_id": "000000829",
   "supplementary_data": {
   "related_ids":

   { "authorization_id": "6WW957787A749904A", "order_id": "3SV13726F9525791J" }
   },
   ...
```

如需詳細資訊，請參閱PayPal的REST API檔案：

* [`purchase_unit` 其中 `custom_id` 駐留](https://developer.paypal.com/docs/api/orders/v2/#definition-purchase_unit:~:text=Read%20only.-,purchase_unit, — 折疊)
* [顯示訂單詳細資訊](https://developer.paypal.com/docs/api/orders/v2/#orders_get)
