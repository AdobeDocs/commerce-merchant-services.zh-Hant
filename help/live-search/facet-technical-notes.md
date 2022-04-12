---
title: 方面技術說明
description: 有關使用Live Search Facets的技術說明。
exl-id: 37982610-0ff7-48b7-b088-be7d2eff8a57
source-git-commit: e53fb13b98684757b8081b2e19dd33d925e8ce5d
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 0%

---

# 方面技術說明

Faceting是一種高效能的過濾方法，它使用可搜索的靜態和動態屬性值的多個維作為搜索標準。

[!DNL Live Search] 使用 `productSearch` 返回faceting的查詢和特定於 [!DNL Live Search]。 請參閱 [`productSearch` 查詢](https://devdocs.magento.com/live-search/product-search.html) 的上界。

## 方面聚合

如果店面有三個方面（類別、顏色和價格），購物者在這三個方面都進行篩選(顏色=藍色，價格在$10.00-50.00，類別= `promotions`)。

* `categories` 聚合 — 聚合 `categories`的 `color` 和 `price` 過濾器，但不是 `categories` 的子菜單。
* `color` 聚合 — 聚合 `color`的 `price` 和 `categories` 過濾器，但不是 `color` 的子菜單。
* `price` 聚合 — 聚合 `price`的 `color` 和 `categories` 過濾器，但不是 `price` 的子菜單。
