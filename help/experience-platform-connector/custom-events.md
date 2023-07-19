---
title: 建立自訂事件
description: 瞭解如何建立自訂事件，將您的Adobe Commerce資料連線到其他AdobeDX產品。
exl-id: 5a754106-c66a-4280-9896-6d065df8a841
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: 1d8609a607e0bcb74fdef47fb8e4e582085836e2
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# 建立自訂事件

您可以擴充 [事件平台](events.md) 建立自己的店面活動，收集業界獨有的資料。 當您建立和設定自訂事件時，它會傳送至 [Adobe Commerce事件收集器](https://github.com/adobe/commerce-events/tree/main/packages/commerce-events-collectors).

## 處理自訂事件

只有Adobe Experience Platform支援自訂事件。 自訂資料不會轉送至Adobe Commerce儀表板和量度追蹤器。

針對任何 `custom` 事件，收集器會新增 `personId` (`ecid`)至 `customContext` 並換行 `xdm` 物件，再轉送至Edge。

範例：

透過Adobe Commerce Events SDK發佈的自訂事件：

```javascript
mse.publish.custom({
    customContext: { customStrAttr: "cheetah", customNumAttr: 128 },
});
```

在Experience Platform邊緣：

```javascript
{
    xdm: {
        personId: 'ecid1234',
        customStrAttr: 'cheetah',
        customNumAttr: 128
    }
}
```

>[!NOTE]
>
> 使用自訂事件可能會影響預設的Adobe Analytics報表。

## 處理事件覆寫（自訂屬性）

只有Experience Platform支援標準事件的屬性覆寫。 自訂資料不會轉送到Commerce儀表板和量度追蹤器。

對於具有集的任何事件 `customContext`，收集器會覆寫 `personId` 和Adobe Analytics計數器，並轉送中設定的所有其他屬性 `customContext`.

範例：

透過Adobe Commerce Events SDK發佈的具有覆寫的產品檢視：

```javascript
mse.publish.productPageView({
    customContext: { customCode: "okapi" },
});
```

在Experience Platform邊緣：

```javascript
{
    xdm: {
        eventType: 'commerce.productViews',
        personId: 'ecid1234',
        customCode: 'okapi',
        commerce: {
            productViews: {
                value : 1
            }
        }
    }
}
```

透過Adobe Commerce Events SDK發佈的具有Adobe Commerce的產品檢視：

```javascript
mse.publish.productPageView({
    customContext: { commerce: { customCode: "mongoose" } },
});
```

在Experience Platform邊緣：

```javascript
{
    xdm: {
        eventType: 'commerce.productViews',
        personId: 'ecid1234',
        commerce: {
            customCode: 'mongoose',
            productViews: {
                value : 1
            }
        }
    }
}
```

>[!NOTE]
>
> 使用自訂屬性覆寫事件可能會影響預設的Adobe Analytics報表。
