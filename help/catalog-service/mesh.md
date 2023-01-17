---
title: '[!DNL Catalog Service and API Mesh]'
description: '''[!DNL API Mesh] 針對Adobe Commerce提供透過通用GraphQL端點整合多個資料來源的方式。'
source-git-commit: 7b95be48c21e17cb6ba88d326fd061f7de2f8fb5
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# [!DNL Catalog Service and API Mesh]

此 [Adobe Developer App Builder的API Mesh](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) 使開發人員能夠使用AdobeIO將專用或第三方API和其他介面與Adobe產品整合。

將API Mesh與目錄服務搭配使用的第一步，是將API Mesh連線至您的執行個體。 請參閱 [建立網格](https://developer.adobe.com/graphql-mesh-gateway/gateway/create-mesh/).

若要完成設定，您需要 [AdobeIO CLI包](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/) 已安裝。

在AdobeIO上配置Mesh後，運行以下命令，該命令將添加 `CommerceCatalogServiceGraph` 源到網格。

```bash
aio api-mesh:source:install "CommerceCatalogServiceGraph" -f variables.json
```

where `variables.json` 是儲存AdobeIO常用值的單獨檔案。
例如，API金鑰可儲存在檔案中：

```json
{
    "CATALOG_SERVICE_API_KEY":"your_api_key"
}
```

執行此命令後，目錄服務應通過API網格運行。 您可以執行 `aio api-mesh:get` 命令查看更新網格的配置。

## 使用API Mesh

API Mesh可讓使用者使用外部資料來源，以增強您的Adobe Commerce例項。 它也可用來設定現有的商務資料以啟用新功能。

在此範例中，API Mesh可用來啟用Adobe Commerce中的層級價格。
取代 `name `, `endpoint` 和 `x-api-key` 值。

```json
{
  "meshConfig": {
    "sources": [
      {
        "name": "<Commerce Instance Name>",
        "handler": {
          "graphql": {
            "endpoint": "<Adobe Commerce GraphQL endpoint>"
          }
        },
        "transforms": [
            {
                "prefix": {
                    "includeRootOperations": true,
                    "value": "Core_"
                }
            }
        ]
      },
      {
        "name": "CommerceCatalogServiceGraph",
        "handler": {
          "graphql": {
            "endpoint": "https://commerce.adobe.io/catalog-service/graphql/",
            "operationHeaders": {
              "Magento-Store-View-Code": "{context.headers['magento-store-view-code']}",
              "Magento-Website-Code": "{context.headers['magento-website-code']}",
              "Magento-Store-Code": "{context.headers['magento-store-code']}",
              "Magento-Environment-Id": "{context.headers['magento-environment-id']}",
              "x-api-key": "storefront-catalog-apollo",
              "Magento-Customer-Group": "{context.headers['magento-customer-group']}"
            },
            "schemaHeaders": {
              "x-api-key": "<YOUR API-KEY>"
            }
          }
        }
      }
    ],
    "additionalTypeDefs": "extend interface ProductView {\n  price_tiers: [Core_TierPrice]\n}\n extend type SimpleProductView {\n  price_tiers: [Core_TierPrice]\n}\n extend type ComplexProductView {\n  price_tiers: [Core_TierPrice]\n}\n",
    "additionalResolvers": [
        {  
            "targetTypeName": "ProductView",
            "targetFieldName": "price_tiers",
            "sourceName": "MagentoStageCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{\n    items {\n  sku\n    price_tiers {\n        quantity,\n        final_price {\n          value\n          currency\n        }\n      }\n    }\n  }",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].price_tiers"
        },
        {  
            "targetTypeName": "SimpleProductView",
            "targetFieldName": "price_tiers",
            "sourceName": "MagentoStageCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{\n    items {\n  sku\n    price_tiers {\n        quantity,\n        final_price {\n          value\n          currency\n        }\n      }\n    }\n  }",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].price_tiers"
        },
        {  
            "targetTypeName": "ComplexProductView",
            "targetFieldName": "price_tiers",
            "sourceName": "MagentoStageCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{\n    items {\n  sku\n    price_tiers {\n        quantity,\n        final_price {\n          value\n          currency\n        }\n      }\n    }\n  }",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].price_tiers"
        }
    ]
   }
}
```

配置後，請查詢Mesh以獲取分層定價：

```json
query {
  products(skus: ["24-MB04"]) {
    sku
    description
    price_tiers {
        quantity
        final_price {
          value
          currency
        }
      }
    ... on SimpleProductView {
      id
       
      price {
        final {
          amount {
            value
          }
        }
      }
    }
  }
}
```
