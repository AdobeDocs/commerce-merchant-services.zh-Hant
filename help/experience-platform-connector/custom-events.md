---
title: 建立自定義事件
description: 瞭解如何建立自定義事件將您的Adobe Commerce資料連接到其他AdobeDX產品。
exl-id: 5a754106-c66a-4280-9896-6d065df8a841
source-git-commit: 2b735c292920bb0e9052d86bf152748e7ce96079
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# 建立自定義事件

可以擴展 [業務平台](events.md) 通過建立自己的儲存事件來收集行業特有的資料。 建立和配置自定義事件時，它將發送到 [Adobe Commerce事件收集者](https://github.com/adobe/commerce-events/tree/main/packages/commerce-events-collectors)。

## 處理自定義事件

僅支援Adobe Experience Platform的自定義事件。 自定義資料不會轉發到Adobe Commerce儀表板和度量跟蹤器。

對於任何 `custom` 事件，收集器添加 `personId` (`ecid`) `customContext` 捲起 `xdm` 對象，然後轉發到邊緣。

示例：

通過Adobe Commerce事件SDK發佈的自定義事件：

```javascript
mse.publish.custom({
    customContext: { customStrAttr: "cheetah", customNumAttr: 128 },
});
```

在Experience Platform邊：

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
> 使用自定義事件可能會影響預設的Adobe Analytics報告。

## 處理事件覆蓋（自定義屬性）

僅支援標準事件的屬性Experience Platform。 自定義資料不會轉發到Commerce儀表板和度量跟蹤器。

對於具有集的任何事件 `customContext`，收集器將覆蓋 `personId` 和Adobe Analytics計數器，並轉發中設定的所有其他屬性 `customContext`。

示例：

具有通過Adobe Commerce事件SDK發佈的替代的產品視圖：

```javascript
mse.publish.productPageView({
    customContext: { customCode: "okapi" },
});
```

在Experience Platform邊：

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

通過Adobe Commerce事件SDK發佈的具有Adobe Commerce替代的產品視圖：

```javascript
mse.publish.productPageView({
    customContext: { commerce: { customCode: "mongoose" } },
});
```

在Experience Platform邊：

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
> 使用自定義屬性覆蓋事件可能會影響預設的Adobe Analytics報告。
