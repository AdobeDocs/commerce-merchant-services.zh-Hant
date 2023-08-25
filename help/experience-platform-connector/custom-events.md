---
title: 建立自訂事件
description: 瞭解如何建立自訂事件，將您的Adobe Commerce資料連線到其他AdobeDX產品。
exl-id: 5a754106-c66a-4280-9896-6d065df8a841
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: 659dd2d1b298ec2a98bb4365a46b09d7468daaad
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---

# 建立自訂事件

您可以擴充 [事件平台](events.md) 建立您自己的店面活動，收集業界獨一無二的資料。 當您建立和設定自訂事件時，會傳送至 [Adobe Commerce事件收集器](https://github.com/adobe/commerce-events/tree/main/packages/commerce-events-collectors).

## 處理自訂事件

僅支援Adobe Experience Platform的自訂事件。 自訂資料不會轉送到Adobe Commerce儀表板和量度追蹤器。

針對任何 `custom` 事件，收集器：

- 新增 `identityMap` 替換為 `ECID` 作為主要身分
- 包含 `email` 在 `identityMap` 作為次要身分 _如果_ `personalEmail.address` 在事件中設定
- 將完整事件包裝在 `xdm` 物件，再轉送至Edge

範例：

透過Adobe Commerce Events SDK發佈的自訂事件：

```javascript
mse.publish.custom({
    commerce: {
        saveForLaters: {
            value: 1,
        },
    },
});
```

在Experience Platform邊緣：

```javascript
{
  xdm: {
    identityMap: {
      ECID: [
        {
          id: 'ecid1234',
          primary: true
        }
      ],
      email: [
        {
          id: "runs@safari.ke",
          primary: false
        }
      ]
    },
    commerce: {
        saveForLaters: {
            value: 1
        }
    }
  }
}
```

>[!NOTE]
>
> 使用自訂事件可能會影響預設的Adobe Analytics報表。

## 處理事件覆寫（自訂屬性）

只有Experience Platform支援標準事件的屬性覆寫。 自訂資料不會轉送到Commerce儀表板和量度追蹤器。

對於任何事件，具有 `customContext`，收集器會以中的欄位覆寫在相關內容中設定的聯結欄位 `customContext`. 覆寫的使用案例是當開發人員想要重複使用和擴充由頁面其他部分在已支援的事件中設定的內容時。

>[!NOTE]
>
>覆寫自訂事件時，應針對該事件型別關閉事件轉送至Experience Platform，以避免重複計算。

範例：

透過Adobe Commerce Events SDK發佈的具覆寫功能的產品檢視：

```javascript
mse.publish.productPageView({
    productListItems: [
        {
            productCategories: [
                {
                    categoryID: "cat_15",
                    categoryName: "summer pants",
                    categoryPath: "pants/mens/summer",
                },
            ],
        },
    ],
});
```

在Experience Platform邊緣：

```javascript
{
  xdm: {
    eventType: 'commerce.productViews',
    identityMap: {
      ECID: [
        {
          id: 'ecid1234',
          primary: true,
        }
      ]
    },
    commerce: {
      productViews: {
        value : 1,
      }
    },
    productListItems: [{
        SKU: "1234",
        name: "leora summer pants",
        productCategories: [{
            categoryID: "cat_15",
            categoryName: "summer pants",
            categoryPath: "pants/mens/summer",
        }],
    }],
  }
}
```

>[!NOTE]
>
> 使用自訂屬性覆寫事件可能會影響預設的Adobe Analytics報表。
