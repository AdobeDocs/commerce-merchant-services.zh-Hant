---
title: refineProduct查詢
description: '''Adobe Commerce目錄服務的''refineProduct'' GraphQL查詢參考指南'''
source-git-commit: 7edfdd71c0900a6bdc7c064a29a6cce405a361ab
workflow-type: tm+mt
source-wordcount: '1267'
ht-degree: 0%

---


# refineProduct查詢

此 `refineProduct` 查詢會縮小 `products` 針對複雜產品執行的查詢。 執行 `refineProduct` 查詢，您必須執行 `products` 查詢並建構回應，以便傳回 `options` 在 `ComplexProductView` 內嵌片段。 當購物者在店面上選取產品選項（例如大小或顏色）時，請執行 `refineProduct` 查詢，指定SKU和選取的選項值ID作為輸入。 根據複雜產品擁有的產品選項數，您可能需要執行 `refineProduct` 查詢多次，直到購物者選取特定變體為止。

您應建構查詢的回應，使其同時包含 `ComplexProductView` 和 `SimpleProductView` 內嵌片段。 如果購物者尚未選取所有必要選項，則查詢會根據選取的選項和可能的剩餘選項，傳回未選取選項的ID以及產品的最低和最高價格。 如果購物者已選取所有必要選項，查詢會傳回關於簡單產品的詳細資訊，其中包括設定的價格。

## 語法

```graphql
refineProduct(sku: String!, optionIds: [String!]!): ProductView
```

## 必要標題

您必須指定下列HTTP標題才能執行此查詢。

| 標題 | 說明 |
|--- | ---|
| `Magento-Customer-Group` | 若為店面用戶端，此值將可在 `dataservices_customer_group` cookie。 |
| `Magento-Environment-Id` | 此值顯示在 **系統** > **商務服務連接器** > **SaaS標識符** > **資料空間ID** 或可透過執行 `bin/magento config:show services_connector/services_id/environment_id` 命令。 |
| `Magento-Store-Code` | 指派給與活動商店視圖關聯的商店的代碼。 例如， `main_website_store`. |
| `Magento-Store-View-Code` | 指派給作用中商店檢視的程式碼。 例如， `default`. |
| `Magento-Website-Code` | 指派給與作用中商店檢視相關聯的網站的代碼。 例如， `base`. |
| `X-Api-Key` | 在上線過程中產生的唯一金鑰。 |

## 使用範例

### 返回部分選定複雜產品的詳細資訊

以下查詢返回有關產品中型變體可用顏色選項的詳細資訊 `MH12`. 的值 `optionIDs` 輸入參數取自 `products` 查詢 [傳回複雜產品的詳細資訊](products.md#complex-product-example) 範例。

**請求：**

```graphql
query {
    refineProduct(optionIds: ["Y29uZmlndXJhYmxlLzE4Ni8xNzc="], sku: "MH12") {
        __typename
        id
        sku
        name
        url
        ... on SimpleProductView {
            price {
                final {
                    amount {
                        value
                    }
                }
                regular {
                    amount {
                        value
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
                        }
                    }
                    regular {
                        amount {
                            value
                        }
                    }
                }
                minimum {
                    final {
                        amount {
                            value
                        }
                    }
                    regular {
                        amount {
                            value
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
    "refineProduct": {
      "__typename": "ComplexProductView",
      "id": "VFVneE1nAFpHVm1ZWFZzZEEATXpSbE1qYzBNR0V0TnpRM015MDBZemc1TFRnM016QXROVGMwTURObVkyVXlOMkZsAGJXRnBibDkzWldKemFYUmxYM04wYjNKbABZbUZ6WlEAVFVGSFUxUkhNREExTlRjNU1ETTQ",
      "sku": "MH12",
      "name": "Ajax Full-Zip Sweatshirt 2",
      "url": "http://example.com/ajax-full-zip-sweatshirt.html",
      "options": [
        {
          "id": "color",
          "title": "Color",
          "required": false,
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
        }
      ],
      "priceRange": {
        "maximum": {
          "final": {
            "amount": {
              "value": 69
            }
          },
          "regular": {
            "amount": {
              "value": 69
            }
          }
        },
        "minimum": {
          "final": {
            "amount": {
              "value": 69
            }
          },
          "regular": {
            "amount": {
              "value": 69
            }
          }
        }
      }
    }
  }
}
```

### 返回關於完全選擇的複雜產品的詳細資訊

在以下查詢中，購物者已針對大小和顏色選取選項。 回應包含對應簡單產品的詳細資訊。

**請求：**

```graphql
query {
    refineProduct(optionIds: ["Y29uZmlndXJhYmxlLzE4Ni8xNzc=", "Y29uZmlndXJhYmxlLzkzLzU5"], sku: "MH12") {
        __typename
        id
        sku
        name
        url
        ... on SimpleProductView {
            price {
                final {
                    amount {
                        value
                    }
                }
                regular {
                    amount {
                        value
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
                        }
                    }
                    regular {
                        amount {
                            value
                        }
                    }
                }
                minimum {
                    final {
                        amount {
                            value
                        }
                    }
                    regular {
                        amount {
                            value
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
    "refineProduct": {
      "__typename": "SimpleProductView",
      "id": "VFVneE1pMU5MVUpzZFdVAFpHVm1ZWFZzZEEATXpSbE1qYzBNR0V0TnpRM015MDBZemc1TFRnM016QXROVGMwTURObVkyVXlOMkZsAGJXRnBibDkzWldKemFYUmxYM04wYjNKbABZbUZ6WlEAVFVGSFUxUkhNREExTlRjNU1ETTQ",
      "sku": "MH12-M-Blue",
      "name": "Ajax Full-Zip Sweatshirt -M-Blue",
      "url": "http://example.com/catalog/product/view/id/235/s/ajax-full-zip-sweatshirt-m-blue/",
      "price": {
        "final": {
          "amount": {
            "value": 69
          }
        },
        "regular": {
          "amount": {
            "value": 69
          }
        }
      }
    }
  }
}
```

## 輸入欄位

您必須指定SKU值，並至少指定一個選項ID作為輸入。

| 欄位 | 資料類型 | 說明 |
|--- | --- | ---|
| `optionIds` | [字串！]! | 指派給購物者所選取產品選項的ID清單，如特定顏色和大小。 |
| `sku` | 字串！ | 複雜產品的SKU。 |

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
