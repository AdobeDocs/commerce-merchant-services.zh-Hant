---
title: GraphQL
description: ' [!DNL Live Search] GraphQL工作區可讓您使用您的即時資料建立查詢。'
exl-id: f7b17c5a-a97b-4724-a50e-83e28a4c4c38
source-git-commit: cf94623fd4a87c13d15c81ac62243a508cb1d14d
workflow-type: tm+mt
source-wordcount: '39'
ht-degree: 0%

---

# GraphQL

*GraphQL*&#x200B;工作區可讓管理員使用自己的資料建置和測試GraphQL查詢。

此工作區支援[`productSearch`](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/)和[`attributeMetadata`](https://developer.adobe.com/commerce/services/graphql/live-search/attribute-metadata/)查詢。

![GraphQL工作區](assets/graphql.png)

```graphql
query productSearch {
  productSearch(phrase: "a306") {
    total_count
    items {
      product {
        sku
		name
      }
    }
    facets {
      title
    }
  }
}
```

變數：

```json
{
  "Magento-Environment-Id": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
  "Magento-Website-Code": "base",
  "Magento-Store-Code": "base",
  "Magento-Store-View-Code": "default",
  "X-Api-Key": "search_gql"
}
```

