---
title: SaaS價格索引
description: 使用SaaS價格索引來改善效能
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
exl-id: 5b92d6ea-cfd6-4976-a430-1a3aeaed51fd
source-git-commit: 3809d27fc3689519e4a162aa52f481d254aec656
workflow-type: tm+mt
source-wordcount: '713'
ht-degree: 0%

---

# SaaS價格索引

SaaS價格指數會縮短反映價格變動所需的時間 [Commerce服務](../landing/saas.md) 在它們提交之後。 如此一來，擁有大型複雜目錄、或擁有多個網站或客戶群組的商家，就能持續處理價格變更。
如果您有Headless店面或使用 [catalog-adapter](./catalog-adapter.md) 擴充功能上，客戶可以停用Adobe Commerce核心價格索引器。

運算密集程式（例如指數化和價格計算）已從Commerce核心移至Adobe的雲端基礎結構。 這可讓商家快速擴充資源，以縮短價格指數化時間，並更快速地反映這些變更。

核心索引資料流動到SaaS服務的形式如下：

![預設資料流程](assets/old_way.png)

使用SaaS價格指數時，流程為：

![SaaS價格指數資料流程](assets/new_way.png)

所有商戶都能受益於這些改善，但收益最大的是客戶：

* 不變價格變更：需要重複變更價格以符合策略性目標（例如頻繁促銷、季節性折扣或存貨減價）的商家。
* 多個網站和/或客戶群組：在多個網站（網域/品牌）和/或客戶群組中，擁有共用產品目錄的商家。
* 跨網站或客戶群組的大量不重複價格：具有廣泛共用產品目錄的商家，其中包含跨網站或客戶群組的不重複價格，例如，具有預先議定價格的B2B商家，以及具有不同定價策略的品牌。

使用Adobe Commerce服務的客戶可免費使用SaaS價格索引，且支援所有內建Adobe Commerce產品型別的價格計算。

本迷你指南說明SaaS價格索引的運作原理以及如何啟用。

## 需求

* Adobe Commerce 2.4.4+
* 具有最新版Adobe Commerce擴充功能的下列其中至少一個Commerce服務：

   * [目錄服務](../catalog-service/overview.md)
   * [即時搜尋](../live-search/guide-overview.md)
   * [產品Recommendations](../product-recommendations/guide-overview.md)

Luma和Adobe Commerce Core GraphQL使用者可安裝 [`catalog-adapter`](catalog-adapter.md) 此擴充功能提供Luma和核心GraphQl相容性，並停用Adobe Commerce產品價格索引器。

## 使用狀況

升級具有SaaS價格索引支援的Adobe Commerce執行個體後，請同步新摘要：

```
bin/magento saas:resync --feed=scopesCustomerGroup
bin/magento saas:resync --feed=scopesWebsite
bin/magento saas:resync --feed=prices
```

## 自訂產品型別的價格

自訂產品型別支援價格計算，例如基本價格、特殊價格、群組價格、目錄規則價格等。

如果您的自訂產品型別使用特定公式來計算最終價格，您可以擴充產品價格摘要的行為。

## 使用狀況

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Magento\ProductPriceDataExporter\Model\Provider\ProductPrice">
        <plugin name="custom_type_price_feed" type="YourModule\CustomProductType\Plugin\UpdatePriceFromFeed" />
    </type>
</config>
```

新的摘要應手動與同步 `resync` [CLI命令](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html#resynccmdline). 否則，資料會在標準同步程式中重新整理。 取得更多關於 [目錄同步](../landing/catalog-sync.md) 程式。

## 使用案例

### Luma沒有擴充功能相依性

* 已安裝必要服務(即時搜尋、產品Recommendations、目錄服務)的Luma或Adobe Commerce Core GraphQL商家
* 沒有依賴PHP核心價格索引器的第三方擴充功能
* 銷售簡單、可設定、群組、虛擬和套裝的動態產品

1. 啟用新摘要。
1. 安裝目錄介面卡。

### Luma和Adobe Commerce核心GraphQl搭配PHP核心價格索引器相依性

* 已安裝支援服務(即時搜尋、產品Recommendations、目錄服務)的Luma或Adobe Commerce Core GraphQL商家
* 透過依賴PHP核心價格索引器的協力廠商擴充功能
* 銷售簡單、可設定、群組、虛擬和套裝的動態產品

1. 啟用新的摘要
1. 安裝目錄介面卡。
1. 重新啟用PHP核心價格索引器。
1. 在中使用新的摘要和Luma相容性代碼 `catalog-adapter` 模組。

### Headless商家

* 已安裝支援服務(即時搜尋、產品Recommendations、目錄服務)的Headless商人
* 不依賴PHP核心價格索引器
* 銷售簡單、可設定、群組、虛擬和套裝的動態產品

1. 啟用新摘要
1. 安裝目錄轉接器，這會停用PHP核心價格索引器。

## 自訂價格

SaaS價格索引器支援Adobe Commerce中提供的自訂產品型別價格功能，例如特殊價格、群組價格和目錄規則價格。

例如：有自訂產品型別  `custom_type` 以及具有SKU「自訂型別產品」的產品。

依預設，Commerce Data Export擴充功能會將下列價格摘要傳送至價格索引器：

```json
{
    "sku": "Custom Type Product",
    "type": "SIMPLE", // must be "SIMPLE" regardless of the real product type
    "customerGroupCode": "0",
    "websiteCode": "base",
    "regular": 123, // the regular base price found in catalog_product_entity_decimal table
    "discounts":    // list of discounts: special_price, group, catalog_rule
    [
        {
            "code": "catalog_rule",
            "price": 102.09
        }
    ],
    "deleted": false,
    "updatedAt": "2023-07-31T13:07:54+00:00"
}
```

如果「自訂產品型別」使用唯一公式來計算產品價格，則系統整合經銷商可擴充Commerce Data Export擴充功能，以覆寫價格和折扣欄位。

1. 在上建立外掛程式 `Magento\ProductPriceDataExporter\Model\Provider\ProductPrice` 類別。

`di.xml` 檔案：

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Magento\ProductPriceDataExporter\Model\Provider\ProductPrice">
        <plugin name="custom_type_price_feed" type="YourModule\CustomProductType\Plugin\UpdatePriceFromFeed" disabled="false" />
    </type>
</config>
```

1. 使用自訂公式建立方法：

```php
class UpdatePriceFromFeed
{
    /**
    * @param ProductPrice $subject
    * @param array $result
    * @param array $values
    *
    * @return array
    */
    public function afterGet(ProductPrice $subject, array $result, array $values) : array
    {
        // Get all custom products, prices and discounts per website and customer groups
        // Override the output $result with your data for the corresponding products
        return $result;
    }
}
```
