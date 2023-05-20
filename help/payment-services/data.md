---
title: 可用資料
description: 使用財務報告資料協調報告與非Commerce系統。
role: User
level: Intermediate
exl-id: dbf41ce9-01f9-45d0-b651-e4c499e83822
source-git-commit: 817a01e98876bddf5f41a253501984539b3351cd
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---

# 可用資料

您可以獲得一些訂單和支付資料，以便跨外部系統協調Adobe Commerce財務報告。

## 與ERP系統協調

您可以使用與特定訂單關聯的增量ID調節Adobe Commerce財務報告與非Adobe企業資源計畫(ERP)系統。

當Oracle Payment Services將Commerce訂單發送到PayPal時，增量ID將作為 `custom_id` _和_ 的 `invoice_id` (它還包含隨機字串 `increment_id`)。

ID在商家活動細節中很容易被訪問，用於支付和在PayPal網鈎中。

的 `invoice_id` 和 `custom_id` 顯示在商家活動詳細資訊底部附近，用於支付：

![`custom_id` 商戶活動詳細資訊](assets/merchant-activity-ids.png)

`custom_id` 和 `invoice_id` 在PayPal網上搜索的細節中：

```json
   ...
   {
    "id": "4E855005GK253170H",
    "intent": "AUTHORIZE",
    "status": "COMPLETED",
    "payment_source": {
        ...
    },
    "purchase_units": [
        {
            ...
            "custom_id": "000001322",
            "invoice_id": "000001322-c01bd7c3-920f-4542-a900-738082177e92",
            ...
            "payments": {
                "authorizations": [
                    {
                       ...
                        "invoice_id": "000001322-c01bd7c3-920f-4542-a900-738082177e92",
                        "custom_id": "000001322",
                        ...
                    }
                ],
                "captures": [
                    {
                        ...
                        "invoice_id": "000001322-c01bd7c3-920f-4542-a900-738082177e92",
                        "custom_id": "000001322",
                        ...
                    }
                ]
            }
        }
    ],
    "payer": {
        ...
    },
    "create_time": "2022-09-12T14:59:01Z",
    "update_time": "2022-09-12T14:59:45Z",
    "links": [
        ...
    ]
}
   ...
```

有關詳細資訊，請參閱PayPal的REST API文檔：

* [`purchase_unit`, `custom_id` 和 `invoice_id` 駐](https://developer.paypal.com/docs/api/orders/v2/#definition-purchase_unit:~:text=Read%20only.-,purchase_unit, — 折疊)
* [顯示訂單詳細資訊](https://developer.paypal.com/docs/api/orders/v2/#orders_get)
