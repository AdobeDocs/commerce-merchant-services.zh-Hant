---
title: "Facet技術說明"
description: 「關於使用的技術說明 [!DNL Live Search] 刻面」
exl-id: 37982610-0ff7-48b7-b088-be7d2eff8a57
source-git-commit: 1a55f2fb3d56183e5e73d172ebdc40f340e4d520
workflow-type: tm+mt
source-wordcount: '117'
ht-degree: 0%

---

# Facet技術說明

Faceting是一種高效能篩選方法，使用可搜尋的靜態和動態屬性值的多個維度作為搜尋准則。

[!DNL Live Search] 使用 `productSearch` 傳回faceting的查詢，以及 [!DNL Live Search]. 請參閱 [`productSearch` 查詢](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) 以取得程式碼範例。

## 面向聚合

如果店面有三個Facet（類別、顏色和價格），且購物者對這三個Facet進行篩選(顏色=藍色，價格為$10.00-50.00，類別= `promotions`)。

* `categories` 匯總 — 匯總 `categories`，套用 `color` 和 `price` 篩選，但不是 `categories` 篩選。
* `color` 匯總 — 匯總 `color`，套用 `price` 和 `categories` 篩選，但不是 `color` 篩選。
* `price` 匯總 — 匯總 `price`，套用 `color` 和 `categories` 篩選，但不是 `price` 篩選。
