---
title: productSearch查詢
description: '''Adobe Commerce目錄服務的''productSearch'' GraphQL查詢參考指南'''
source-git-commit: 49692cf4375ebb975b2cf132d21ac8debe609a90
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# productSearch查詢

Adobe Commerce的目錄服務 `productSearch` 查詢可使用即時搜尋來傳回指定為輸入之SKU的詳細資訊。 雖然此查詢與 [`productSearch` 查詢](https://devdocs.magento.com//live-search/product-search.html)，即時搜尋會傳回 `productView` 物件。 請參閱 [`productSearch` 查詢](https://devdocs.magento.com//live-search/product-search.html) 參考資訊主題。

## 語法

```graphql
productSearch(
    phrase: String!
    page_size: Int = 20
    current_page: Int = 1
    filter: [SearchClauseInput!]
    sort: [ProductSearchSortInput!]
): ProductSearchResponse!
```

## 必要標題

您必須指定下列HTTP標題才能執行此查詢。

| 標題 | 說明 |
|--- | ---|
| `Magento-Customer-Group` | 若為店面用戶端，此值將可在 `dataservices_customer_group` cookie。 |
| `Magento-Environment-Id` | 此值可透過執行 `bin/magento config:show services_connector/services_id/environment_id` 命令。 請參閱 [商務服務](https://docs.magento.com/user-guide/configuration/services/saas.html) |
| `Magento-Store-Code` | 指派給與活動商店視圖關聯的商店的代碼。 例如， `main_website_store`. |
| `Magento-Store-View-Code` | 指派給作用中商店檢視的程式碼。 例如， `default`. |
| `Magento-Website-Code` | 指派給與作用中商店檢視相關聯的網站的代碼。 例如， `base`. |
| `X-Api-Key` | 在上線過程中產生的唯一金鑰。 |

## 使用範例

在以下範例中，查詢會傳回與上一個範例相同產品的資訊。 但是，它的建構是為了在目錄服務中傳回項目資訊 `productView` 物件而非核心 `product` 物件。 請注意，定價資訊會因產品類型而異。 為了簡潔起見，不會顯示Facet資訊。

**請求：**

```graphql
{
  productSearch(
    phrase: "bag"
    sort: [
      {
        attribute: "price"
        direction: DESC }]
    page_size: 9
  ) {
    page_info {
      current_page
      page_size
      total_pages
    }
    items {
      productView {
        name
        sku
        ... on SimpleProductView {
          price {
            final {
              amount {
                value
                currency
              }
            }
            regular {
              amount {
                value
                currency
              }
            }
          }
        }
        ... on ComplexProductView {
          options {
            id
            title
            required
            values {
              id
              title
            }
          }
          priceRange {
            maximum {
              final {
                amount {
                  value
                  currency
                }
              }
              regular {
                amount {
                  value
                  currency
                }
              }
            }
            minimum {
              final {
                amount {
                  value
                  currency
                }
              }
              regular {
                amount {
                  value
                  currency
                }
              }
            }
          }
        }
      }
    }
  }
}
```

**回應：**

```json
{
  "data": {
    "productSearch": {
      "page_info": {
        "current_page": 1,
        "page_size": 9,
        "total_pages": 3
      },
      "items": [
        {
          "productView": {
            "name": "Impulse Duffle",
            "sku": "24-UB02",
            "price": {
              "final": {
                "amount": {
                  "value": 74,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 74,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Fusion Backpack 567890",
            "sku": "24-MB02",
            "price": {
              "final": {
                "amount": {
                  "value": 59,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 59,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Rival Field Messenger",
            "sku": "24-MB06",
            "price": {
              "final": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Push It Messenger Bag",
            "sku": "24-WB04",
            "price": {
              "final": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Overnight Duffle",
            "sku": "24-WB07",
            "price": {
              "final": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Wayfarer Messenger Bag 987",
            "sku": "24-MB05",
            "price": {
              "final": {
                "amount": {
                  "value": 44,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 44,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Driven Backpack",
            "sku": "24-WB03",
            "price": {
              "final": {
                "amount": {
                  "value": 36,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 36,
                  "currency": "USD"
                }
              }
            }
          }
        }
      ]
    }
  }
}
```
