---
title: 自訂
description: 了解如何自訂您的產品建議。
exl-id: b1b8e770-45ec-4403-b79b-4f0a9f7bd959
source-git-commit: a34c3c8a5caca1bbf611b2df650c562aeeab297b
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 自訂

安裝產品Recommendations模組時，Adobe Commerce會建立 `ProductRecommendationsLayout` 目錄。 此目錄包含可自訂的範本檔案，以變更建議在店面上的顯示方式。 具體來說，您可以修改或覆寫下列範本：

`<your theme>/Magento_ProductRecommendationsLayout/web/template/recommendations.html`

有關修改模板檔案的詳細資訊，請參閱 [範本自訂](https://developer.adobe.com/commerce/frontend-core/guide/templates/walkthrough/) （位於前端開發人員指南中）。

若您修改 `recommendations.html` 檔案中，您必須保留檔案中的下列標籤，以確保Adobe Commerce可從您的店面收集建議量度：

| 標籤 | 使用 |
|---|---|
| `<div data-bind="attr : {'data-unit-id' : unitId }"...</div>` | 收集檢視事件。 |
| `<a data-bind="attr : {'data-sku' : sku, 'data-unit-id'}"...</a>` | 收集點擊事件。 <br/>**注意：** 如果您新增任何錨點標籤，則必須包含這些屬性。 |

除了 `recommendations.html` 檔案， `ProductRecommendationsLayout` 目錄包含下列子目錄：

| 目錄 | 用途 |
|---|---|
| `layout` | 包含 `*.xml` 每個頁面類型的檔案 |
| `templates` | 包含呼叫擷取和呈現指令碼的檔案 |
| `web/js` | 包含為您的存放區擷取及呈現建議的JavaScript檔案 |
| `web/template` | 包含 `magento/product-recommendations` 模組 |

## 推薦單元定位

當您 [建立](create.md) 建議，您可指定 [位置](placement.md) 顯示在頁面上。 建議單元可放置在主要內容容器的頂端或底部。 不過，您可以自訂此位置。 如果您建立頁面產生器建議內容類型，請使用頁面產生器工具將建議單位置於頁面上。 對於所有其他頁面類型，請編輯 `*.xml` 建立建議時產生的檔案。

1. 變更為 `layout` 目錄：

   ```bash
   cd `<your theme>/Magento_ProductRecommendationsLayout/layout`
   ```

   下表列出了此目錄中存在的XML檔案：

   | 檔案名 | 頁面 |
   |---|---|
   | `catalog_category_view.xml` | 類別 |
   | `catalog_product_view.xml` | 產品詳細資料 |
   | `checkout_cart_index.xml` | 購物車 |
   | `checkout_onepage_success.xml` | 結帳 |
   | `cms_index_index.xml` | 首頁 |

   >[!NOTE]
   >
   >檔案名稱 `layout` 如果您的存放區使用協力廠商擴充功能，則目錄可能會不同。

1. 現在來修改 `catalog_product_view.xml` 檔案，讓建議單位出現在產品詳細資料頁面上的產品影像之後。 在自定義此XML檔案之前，我們先查看該檔案，並了解需要修改的部分：

   ```xml
   <?xml version="1.0"?>
   <page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
       <referenceBlock name="page.wrapper">
           <block class="Magento\Framework\View\Element\Template" before="-" name="product_recommendations_fetcher" template="Magento_ProductRecommendationsStorefront::fetcher.phtml" />
       </referenceBlock>
       <body>
           <referenceBlock name="main.content">
               <block class="Magento\ProductRecommendationsStorefront\Block\Renderer" after="-" name="product_recommendations_product_below_content" template="Magento_ProductRecommendationsStorefront::renderer.phtml">
                   <arguments>
                       <argument name="pagePlacement" xsi:type="string">below-main-content</argument>
                   </arguments>
               </block>
           </referenceBlock>
       </body>
   </page>
   ```

   在上述程式碼片段中， `main.content` 參考區塊表示建議單位將放置在該元素的某處。 其 `block` 元素包含 `after="-"` 屬性，指定在主要內容區塊之後，建議單位將顯示在頁面上。

1. 現在來指定不同的內容區塊以修改此檔案。

   您將更改引用塊 `name` 從 `main.content` to `product.info.media`.

   ```xml
   <?xml version="1.0"?>
   <page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
       <referenceBlock name="page.wrapper">
           <block class="Magento\Framework\View\Element\Template" before="-" name="product_recommendations_fetcher" template="Magento_ProductRecommendationsStorefront::fetcher.phtml" />
       </referenceBlock>
       <body>
           <referenceBlock name="product.info.media">
               <block class="Magento\ProductRecommendationsStorefront\Block\Renderer" after="-" name="product_recommendations_product_below_content" template="Magento_ProductRecommendationsStorefront::renderer.phtml">
                   <arguments>
                       <argument name="pagePlacement" xsi:type="string">below-main-content</argument>
                   </arguments>
               </block>
           </referenceBlock>
       </body>
   </page>
   ```

   此變更會導致建議單位出現在產品詳細資料頁面上的產品影像後面。 如果您希望建議單位顯示在 `product.info.media`，變更 `after="-"` 屬性至 `before="-"`. 此 `pagePlacement` 引數是不應修改的內部引數。

請參閱 [配置概觀](https://developer.adobe.com/commerce/frontend-core/guide/layouts/) 以取得頁面上區塊類型的詳細資訊。

## 自訂產品屬性

開發人員通常需要存取店面建議單位中的自訂產品屬性值，以便根據這些屬性為產品新增視覺處理。

例如，如果您的商店銷售某些有機產品，則這些產品上可能會有自訂屬性，指定為 `Organic = Yes`. 您可能需要存取店面上的此屬性值，以便在這些產品出現在Recommendations時，給予特別的視覺處理。 同樣地，存取這些自訂產品屬性值可讓您標示產品，或在網站的展示層驅動自訂邏輯。

![新增徽章](assets/unit-custom.png)

若要在頁面上呈現建議單位時確定自訂產品屬性可用，請設定 `Used in Product Listing` 屬性 `Yes` 在 [產品屬性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html) 頁面。

設定此屬性時，JSON裝載會包含 `attributes` 包含屬性代碼和值陣列的對象。 然後，您可以根據這些屬性值套用自訂店面樣式，例如新增特殊的視覺處理或徽章，如前所述。

>[!NOTE]
>
>產品屬性變更最多可能需要一小時才會出現在JSON裝載中。
