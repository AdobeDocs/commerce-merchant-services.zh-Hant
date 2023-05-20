---
title: "Facet技術說明"
description: 「有關使用的技術說明 [!DNL Live Search] facets」
exl-id: 37982610-0ff7-48b7-b088-be7d2eff8a57
source-git-commit: 995f528abc0011c6ae7c4c524982c301072ec2eb
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---

# 方面技術說明

Faceting是一種高效能的過濾方法，它使用可搜索的靜態和動態屬性值的多個維作為搜索標準。

[!DNL Live Search] 使用 `productSearch` 返回faceting的查詢和特定於 [!DNL Live Search]。 請參閱 [`productSearch` 查詢](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) 的上界。

## 方面聚合

Facet聚合執行如下：如果店面有三個方面（類別、顏色和價格），購物者在這三個方面都進行過濾(顏色=藍色，價格在10.00-50.00美元之間，類別= `promotions`)。

* `categories` 聚合 — 聚合 `categories`，則 `color` 和 `price` 過濾器，但不是 `categories` 的子菜單。
* `color` 聚合 — 聚合 `color`，則`price` 和 `categories` 過濾器，但不是 `color` 的子菜單。
* `price` 聚合 — 聚合 `price`，則 `color` 和 `categories` 過濾器，但不是 `price` 的子菜單。
