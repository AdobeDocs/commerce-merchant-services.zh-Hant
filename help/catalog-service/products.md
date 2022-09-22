---
title: 產品查詢
description: '''Adobe Commerce目錄服務的''products'' GraphQL查詢參考指南'''
source-git-commit: d9b8c89f6d04aa9d569b450af2893b92938119ad
workflow-type: tm+mt
source-wordcount: '1226'
ht-degree: 0%

---


# 產品查詢

Adobe Commerce的目錄服務 `products` 查詢會傳回指定為輸入之SKU的詳細資訊。 雖然此查詢與 [`products` 查詢](https://devdocs.magento.com/guides/v2.4/graphql/queries/products.html) 核心Adobe Commerce和Magento Open Source皆提供，但有一些差異。

目錄服務查詢需要一或多個SKU值作為輸入。 查詢主要用於檢索資訊以呈現以下類型的內容：

* 產品詳細資料頁面 — 您可以提供指定SKU所識別之產品的完整詳細資料。

* 產品比較頁面 — 您可以擷取關於多項產品的選取資訊，例如名稱、價格和影像。

此 `ProductView` 輸出物件與核心明顯不同 `products` 查詢 `Products` 輸出物件。 主要差異包括：

* 產品要麼簡單，要麼複雜。 簡單、虛擬、可下載和禮品卡產品對應至 `SimpleProductView`. 所有其他產品類型都對應至 `ComplexProductView`. 簡單的產品定價。 複雜的產品有價格範圍。 由於複雜產品由多種簡單產品組成，因此它們可以獲得簡單的產品價格。

* 商家定義的屬性在頂層容器中公開，並指明其店面角色。 角色包括「在PDP上顯示」、「在PLP上顯示」和「在搜索結果上顯示」。

* 影像也可作為頂層容器存取，並可依其角色加以篩選。 影像可以有基本、小或縮圖角色。

## 語法

```graphql
products (skus [String]) [ProductView]
```

## 必要標題

您必須指定下列HTTP標題才能執行此查詢。

| 標題 | 說明 |
| --- | --- |
| `Magento-Customer-Group` | 若為店面用戶端，此值將可在 `dataservices_customer_group` cookie。 |
| `Magento-Environment-Id` | 此值顯示在 **系統** > **商務服務連接器** > **SaaS標識符** > **資料空間ID** 或可透過執行 `bin/magento config:show services_connector/services_id/environment_id` 命令。 |
| `Magento-Store-Code` | 指派給與活動商店視圖關聯的商店的代碼。 例如， `main_website_store`. |
| `Magento-Store-View-Code` | 指派給作用中商店檢視的程式碼。 例如， `default`. |
| `Magento-Website-Code` | 指派給與作用中商店檢視相關聯的網站的代碼。 例如， `base`. |
| `X-Api-Key` | 在上線過程中產生的唯一金鑰。 |

## 使用範例

### 傳回簡單產品的詳細資訊

以下查詢返回有關簡單產品的詳細資訊。

**請求：**

```graphql
query {
  products(skus: ["24-MB02"]) {
    id
    sku
    name
    url
    description
    shortDescription
    attributes(roles: ["visible in Search"]) {
      name
      label
      value
      roles
    }
    ... on SimpleProductView {
      price {
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
```

**回應：**

```json
{
  "data": {
    "products": [
      {
        "id": "TWpRdFRVSXdNZwBaR1ZtWVhWc2RBAE16UmxNamMwTUdFdE56UTNNeTAwWXpnNUxUZzNNekF0TlRjME1ETm1ZMlV5TjJGbABiV0ZwYmw5M1pXSnphWFJsWDNOMGIzSmwAWW1GelpRAFRVRkhVMVJITURBMU5UYzVNRE00",
        "sku": "24-MB02",
        "name": "Fusion Backpack 567890",
        "url": "http://example.com/fusion-backpack.html",
        "description": "<p>With the Fusion Backpack strapped on, every trek is an adventure - even a bus ride to work. That's partly because two large zippered compartments store everything you need, while a front zippered pocket and side mesh pouches are perfect for stashing those little extras, in case you change your mind and take the day off.</p>\r\n<ul>\r\n<li>Durable nylon construction.</li>\r\n<li>2 main zippered compartments.</li>\r\n<li>1 exterior zippered pocket.</li>\r\n<li>Mesh side pouches.</li>\r\n<li>Padded, adjustable straps.</li>\r\n<li>Top carry handle.</li>\r\n<li>Dimensions: 18\" x 10\" x 6\".</li>\r\n</ul>",
        "shortDescription": "",
        "attributes": [
          {
            "name": "activity",
            "label": "Activity",
            "value": [
              "Hiking",
              "School",
              "Yoga"
            ],
            "roles": [
              "visible in PDP",
              "visible in compare list",
              "visible in Search"
            ]
          },
          {
            "name": "features_bags",
            "label": "Features",
            "value": [
              "Hydration Pocket",
              "Audio Pocket",
              "Waterproof",
              "Lightweight"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "material",
            "label": "Material",
            "value": [
              "Burlap",
              "Nylon",
              "Polyester"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "strap_bags",
            "label": "Strap/Handle",
            "value": [
              "Adjustable",
              "Double",
              "Padded"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "style_bags",
            "label": "Style Bags",
            "value": [
              "Backpack",
              "Laptop"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          }
        ],
        "price": {
          "regular": {
            "amount": {
              "value": 59,
              "currency": "USD"
            }
          }
        }
      }
    ]
  }
}
```

### 傳回複雜產品的詳細資訊 {#complex-product-example}

以下查詢返回有關可配置產品的詳細資訊。

**請求：**

```graphql
query {
  products(skus: ["MH12"]) {
    __typename
    id
    sku
    name
    url
    description
    shortDescription
    attributes(roles: ["visible in Search"]) {
      name
      label
      value
      roles
    }
    ... on ComplexProductView {
      priceRange {
        maximum {
          regular {
            amount {
              value
              currency
            }
          }
        }
        minimum {
          regular {
            amount {
              value
              currency
            }
          }
        }
      }
      options {
        id
        required
        title
        values {
          id
          title
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
    "products": [
      {
        "__typename": "ComplexProductView",
        "id": "VFVneE1nAFpHVm1ZWFZzZEEATXpSbE1qYzBNR0V0TnpRM015MDBZemc1TFRnM016QXROVGMwTURObVkyVXlOMkZsAGJXRnBibDkzWldKemFYUmxYM04wYjNKbABZbUZ6WlEAVFVGSFUxUkhNREExTlRjNU1ETTQ",
        "sku": "MH12",
        "name": "Ajax Full-Zip Sweatshirt 2",
        "url": "http://example.com/ajax-full-zip-sweatshirt.html",
        "description": "<p>The Ajax Full-Zip Sweatshirt makes the optimal layering or outer piece for archers, golfers, hikers and virtually any other sportsmen. Not only does it have top-notch moisture-wicking abilities, but the tight-weave fabric also prevents pilling from repeated wash-and-wear cycles.</p>\r\n<p>&bull; Mint striped full zip hoodie.<br />&bull; 100% bonded polyester fleece.<br />&bull; Pouch pocket.<br />&bull; Rib cuffs and hem. <br />&bull; Machine washable.</p>",
        "shortDescription": "",
        "attributes": [
          {
            "name": "climate",
            "label": "Climate",
            "value": [
              "All-Weather",
              "Cool",
              "Indoor",
              "Spring",
              "Windy"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "customattribute",
            "label": "customAttribute",
            "value": "asd",
            "roles": [
              "visible in PDP",
              "visible in PLP",
              "visible in Search"
            ]
          },
          {
            "name": "material",
            "label": "Material",
            "value": [
              "Fleece",
              "Polyester"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "pattern",
            "label": "Pattern",
            "value": "Striped",
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "testtttattribute",
            "label": "testtttAttribute",
            "value": "asd",
            "roles": [
              "visible in PDP",
              "visible in PLP",
              "visible in Search"
            ]
          }
        ],
        "priceRange": {
          "maximum": {
            "regular": {
              "amount": {
                "value": 69,
                "currency": "USD"
              }
            }
          },
          "minimum": {
            "regular": {
              "amount": {
                "value": 69,
                "currency": "USD"
              }
            }
          }
        },
        "options": [
          {
            "id": "color",
            "required": false,
            "title": "Color",
            "values": [
              {
                "id": "Y29uZmlndXJhYmxlLzkzLzU5",
                "title": "Blue"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzkzLzY3",
                "title": "Red"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzkzLzYy",
                "title": "Green"
              }
            ]
          },
          {
            "id": "size",
            "required": false,
            "title": "Size",
            "values": [
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzU=",
                "title": "XS"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzY=",
                "title": "S"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzc=",
                "title": "M"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzg=",
                "title": "L"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzk=",
                "title": "XL"
              }
            ]
          }
        ]
      }
    ]
  }
}
```

## 輸出欄位

此 `ProductView` return物件是可包含下列欄位的介面。 這是由 [`SimpleProductView`](#SimpleProductView-type) 和 [`ComplexProductView`](#ComplexProductView-type) 類型。

| 欄位 | 資料類型 | 說明 |
|--- | --- | ---|
| `attributes(roles: [String])` | [ProductViewAttribute] | 為店面指定的商家定義屬性清單。 |
| `description` | 字串 | 產品的詳細說明。 |
| `id` | ID! | 產品ID，以複合金鑰產生，每個地區皆不重複。 |
| `images(roles: [String])` | [ProductViewImage] | 為產品定義的影像清單。 |
| `metaDescription` | 字串 | 搜尋結果清單產品的簡要概述。 |
| `metaKeyword` | 字串 | 只對搜尋引擎可見的逗號分隔關鍵字清單。 |
| `metaTitle` | 字串 | 在瀏覽器的標題欄和索引標籤以及搜尋結果清單中顯示的字串。 |
| `name` | 字串 | 產品名稱。 |
| `shortDescription` | 字串 | 產品摘要。 |
| `sku` | 字串 | 產品SKU。 |
| `url` | 字串 | 產品的標準URL。 |

### ComplexProductView類型 {#ComplexProductView-type}

此 `ComplexProductView` type表示捆綁、可配置和組產品。 複雜產品價格作為價格範圍返回，因為價格值可能根據所選選項而有所不同。 類型實作 `ProductView`.

| 欄位 | 資料類型 | 說明 |
|--- | --- | ---|
| `attributes(roles: [String])` | [ProductViewAttribute] | 為店面指定的商家定義屬性清單。 |
| `description` | 字串 | 產品的詳細說明。 |
| `id` | ID! | 產品ID，以複合金鑰產生，每個地區皆不重複。 |
| `images(roles: [String])` | [ProductViewImage] | 為產品定義的影像清單。 |
| `metaDescription` | 字串 | 搜尋結果清單產品的簡要概述。 |
| `metaKeyword` | 字串 | 只對搜尋引擎可見的逗號分隔關鍵字清單。 |
| `metaTitle` | 字串 | 在瀏覽器的標題欄和索引標籤以及搜尋結果清單中顯示的字串。 |
| `name` | 字串 | 產品名稱。 |
| `options` | [ProductViewOption] | 可選選項的清單。 |
| `priceRange` | ProductViewPriceRange | 複雜產品的可能價格範圍。 |
| `shortDescription` | 字串 | 產品摘要。 |

### 價格類型

此 `Price type` 定義簡單產品的價格或複雜產品價格範圍的一部分。 其中可包含價格調整清單。

| 欄位 | 資料類型 | 說明 |
|--- | --- | ---|
| `amount` | ProductViewMoney | 包含產品的貨幣值和貨幣代碼。 |

### 價格調整類型

此 `PriceAdjustment` 類型指定價格調整的金額和類型。 范常式式碼值為 `weee`.

| 欄位 | 資料類型 | 說明 |
|--- | --- | ---|
| `amount` | 浮點數 | 價格調整的金額。 |
| `code` | 字串 | 標識價格調整的類型。 |

### ProductViewAttribute類型

此 `ProductViewAttribute` 類型是顯示在店面的客戶定義屬性的容器。

| 欄位 | 資料類型 | 說明 |
|--- | --- | ---|
| `label` | 字串 | 屬性的標籤。 |
| `name` | 字串！ | 屬性代碼的名稱。 |
| `roles` | [字串] | 為店面上的屬性指定的角色，例如「在PLP上顯示」、「在PDP中顯示」或「在搜索中顯示」。 |
| `value` | JSON | 屬性值，任意類型。 |

### ProductViewImage類型

此 `ProductViewImage` 類型包含產品影像的詳細資訊。

| 欄位 | 資料類型 | 說明 |
|--- | --- | ---|
| `label` | 字串 | 產品影像的顯示標籤。 |
| `roles` | [字串] | 說明如何使用影像的清單。 可以是 `image`, `small_image`，或 `thumbnail`. |
| `url` | 字串！ | 產品影像的URL。 |

### ProductViewMoney類型

此 `ProductViewMoney` type會定義貨幣值，包括數值和貨幣代碼。

| 欄位 | 資料類型 | 說明 |
|--- | --- | ---|
| `currency` | ProductViewCurrency | 三字母的貨幣代碼，如USD或EUR。 |
| `value` | 浮點數 | 表示貨幣值的數字。 |

### ProductViewOption類型

產品選項提供了配置產品的方法，方法是選擇特定選項值。 選取一或多個選項，即可指向特定的簡單產品。

| 欄位 | 資料類型 | 說明 |
|--- | --- | ---|
| `id` | ID | 選項的ID。 |
| `multi` | 布林值 | 指出選項是否允許多個選項。 |
| `required` | 布林值 | 指示是否必須選取選項。 |
| `title` | 字串 | 選項的顯示名稱。 |
| `values` | [ProductViewOptionValue!] | 可用選項值的清單。 |

### ProductViewOptionValue介面

此 `ProductViewOptionValue` 介面會定義 `ProductViewOptionValueProduct` 和 `ProductViewOptionValueConfiguration` 類型。

| 欄位 | 資料類型 | 說明 |
|--- | --- | ---|
| `id` | ID | 選項值的ID。 |
| `title` | 字串 | 選項值的顯示名稱。 |

### ProductViewOptionValueConfiguration類型

此 `ProductViewOptionValueConfiguration` 類型是 `ProductViewOptionValue` ，以了解設定值。

| 欄位 | 資料類型 | 說明 |
|--- | --- | ---|
| `id` | ID | 選項值的ID。 |
| `title` | 字串 | 選項值的顯示名稱。 |

### ProductViewOptionValueProduct類型

此 `ProductViewOptionValueProduct` 類型是 `ProductViewOptionValue` 這會新增簡單產品的詳細資訊。

| 欄位 | 資料類型 | 說明 |
|--- | --- | ---|
| `id` | ID | 選項值的ID。 |
| `title` | 字串 | 選項值的顯示名稱。 |
| `product` | SimpleProductView | 簡單產品的詳細資訊。 |

### ProductViewPrice類型

此 `ProductViewPrice` type提供基本產品價格視圖，是簡單產品固有的。

| 欄位 | 資料類型 | 說明 |
|--- | --- | ---|
| `final` | 價格 | 折扣後的價格值，不包括個人化促銷活動。 |
| `regular` | 價格 | 由商家指定的基本產品價格。 |
| `roles` | [字串] | 確定價格應該是可見還是隱藏。 |

### ProductViewPriceRange類型

此 `ProductViewPriceRange` 類型列出複雜產品的最低和最高價格。

| 欄位 | 資料類型 | 說明 |
|--- | --- | ---|
| `maximum` | ProductViewPrice | 最高價格。 |
| `minimum` | ProductViewPrice | 最低價格。 |

### SimpleProductView類型 {#SimpleProductView-type}

此 `SimpleProductView` type代表所有產品類型，但捆綁包、可配置和組除外。 簡單產品價格不包含價格範圍。 `SimpleProductView` 實作 `ProductView`.

| 欄位 | 資料類型 | 說明 |
|--- | --- | ---|
| `attributes(roles: [String])` | [ProductViewAttribute] | 為店面指定的商家定義屬性清單。 |
| `description` | 字串 | 產品的詳細說明。 |
| `id` | ID! | 產品ID，以複合金鑰產生，每個地區皆不重複。 |
| `images(roles: [String])` | [ProductViewImage] | 為產品定義的影像清單。 |
| `metaDescription` | 字串 | 搜尋結果清單產品的簡要概述。 |
| `metaKeyword` | 字串 | 只對搜尋引擎可見的逗號分隔關鍵字清單。 |
| `metaTitle` | 字串 | 在瀏覽器的標題欄和索引標籤以及搜尋結果清單中顯示的字串。 |
| `name` | 字串 | 產品名稱。 |
| `price` | ProductViewPrice | 基本產品價格視圖。 |
| `shortDescription` | 字串 | 產品摘要。 |
| `sku` | 字串 | 產品SKU。 |
| `url` | 字串 | 產品的標準URL。 |
