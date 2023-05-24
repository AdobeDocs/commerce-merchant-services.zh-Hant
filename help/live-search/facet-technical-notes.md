---
title: 「Facet技術說明」
description: 「關於使用的技術說明 [!DNL Live Search] 多面向。」
exl-id: 37982610-0ff7-48b7-b088-be7d2eff8a57
source-git-commit: 995f528abc0011c6ae7c4c524982c301072ec2eb
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---

# Facet技術備註

多面向是一種高效能篩選方法，使用可搜尋靜態和動態屬性值的多個維度作為搜尋條件。

[!DNL Live Search] 使用 `productSearch` 查詢會傳回刻面及其他特定資料 [!DNL Live Search]. 請參閱 [`productSearch` 查詢](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) 以取得程式碼範例。

## Facet彙總

多面向彙總的執行方式如下：如果店面有三方面（類別、顏色和價格），且購物者對所有三方面(顏色=藍色，價格為$10.00-50.00，類別= `promotions`)。

* `categories` 彙總 — 彙總 `categories`，然後套用 `color` 和 `price` 篩選條件，但不適用於 `categories` 篩選。
* `color` 彙總 — 彙總 `color`，然後套用`price` 和 `categories` 篩選條件，但不適用於 `color` 篩選。
* `price` 彙總 — 彙總 `price`，然後套用 `color` 和 `categories` 篩選條件，但不適用於 `price` 篩選。
