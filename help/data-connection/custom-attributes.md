---
title: 新增自訂訂單屬性
description: 瞭解如何將自訂訂單屬性新增至您的後台資料，並將這些屬性傳送至Experience Platform。
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 14d190726324e2f42d66c2270f2e27be5a74132f
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 2%

---

# 新增自訂訂單屬性

在本文中，您將瞭解如何新增自訂屬性至後台事件。 透過自訂屬性，您可以擷取豐富的資料深入解析來增強分析，並進一步為購物者建立個人化體驗。

自訂屬性支援兩個層級：

- 訂單層級
- 訂單料號層次

>[!NOTE]
>
>Adobe[!DNL Commerce]支援資料型別為字串、布林值或日期的自訂屬性。

將自訂屬性新增至後端辦公室事件需要您：

1. 在您的[!DNL Commerce]安裝中建立專案。
1. 更新您的結構描述，以便新的自訂屬性可以正確地內嵌到Experience Platform中。
1. 在Admin中，確認正在擷取自訂屬性並傳送給Experience Platform。

>[!IMPORTANT]
>
>以下目錄結構和程式碼範例說明如何實作自訂屬性。 所需的實際目錄結構和程式碼取決於存放區設定和環境。

## 步驟1：建立目錄結構

1. 導覽至[!DNL Commerce]安裝中的`app/code`目錄，並建立模組目錄。 例如： `Magento/AepCustomAttributes`。 此目錄包含自訂屬性所需的檔案。
1. 在模組目錄中，建立名為`etc`的子目錄。 `etc`目錄包含`module.xml`、`query.xml`、`di.xml`和`et_schema.xml`檔案。

## 步驟2：定義相依性和設定版本

建立定義相依性和安裝程式版本的`module.xml`檔案。 例如：

```xml
<?xml version="1.0"?>
<!--
/**
* Copyright (c) [year], [name]. All rights reserved.
*/
-->
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Module/etc/module.xsd">
    <module name="Magento_SalesRuleStaging" setup_version="2.0.0">
        <sequence>
            <module name="Magento_Staging"/>
            <module name="Magento_SalesRule"/>
        </sequence>
    </module>
</config>
```

## 步驟3：擷取銷售訂單資料

建立可擷取銷售訂單資料的`query.xml`檔案。 例如：

```xml
<query>
    <source name="sales_order" type="sales">
        <attribute name="increment_id" operator="eq" alias="order_increment_id"/>
        <link source="inventory_source_item" condition_type="by_sku"/>
    </source>
</query>
```

## 步驟4：設定相依性插入

建立設定相依性插入的`di.xml`檔案。 例如：

```xml
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
          package="com.example.instrumentedtest"
          android:versionCode="1"
          android:versionName="1.0">
    <uses-sdk android:minSdkVersion="8" android:targetSdkVersion="15"/>
    
    <instrumentation
        android:name=".MyInstrumentationTestRunner"
        android:targetPackage="com.example.instrumentedtest"/>
    
    <!-- More instrumentation elements might be here -->
</manifest>
```

## 步驟5：定義用於相依性插入的服務

建立`et_schema.xml`檔案，定義用於相依性插入的服務。 例如：

```xml
<services>
    <service id="App\Controller\MainController" class="App\Controller\MainController">
        <argument type="service" id="doctrine.orm.default_entity_manager"/>
        <argument type="service" id="form.factory"/>
        <argument type="service" id="security.authorization_checker"/>
    </service>

    <!-- ... -->

    <service id="App\Controller\SecurityController" class="App\Controller\SecurityController">
        <argument type="service" id="security.authentication_utils"/>
        <tag name="controller.service_arguments"/>
    </service>

    <!-- ... -->
</services>
```

## 步驟6：建立PHP檔案的目錄

在與`etc`目錄相同的層級，建立名為`Module/Provider`的目錄。 此目錄包含`OrderCustomAttributes`和`OrderItemCustomAttributes` PHP檔案。

## 步驟7：定義OrderCustomAttribute

建立定義順序自訂屬性的`OrderCustomAttributes.php`檔案。 例如：

```php
namespace App\Transformers;

use League\Fractal\TransformerAbstract;
use Illuminate\Support\Collection;

class CustomAttributeTransformer extends TransformerAbstract
{
    protected $availableIncludes = [];
    protected $defaultIncludes = [];

    public function __construct($signsField, $jsonSignsField = null)
    {
        $this->signsField = $signsField;
        $this->jsonSignsField = $jsonSignsField;
    }

    public function transform(Collection $collection)
    {
        // Initialize array for additional information.
        $additionalInformation = [];

        // Source - this comes from values sent to this transformer.
        foreach ($collection->{$this->signsField} ?: [] as $value) {
            if (is_array($value)) {
                // If value is an array, serialize it.
                foreach ($value as &$item) {
                    if (isset($item['custom_attr'])) {
                        // Serialize custom attribute data.
                        ...
                    }
                }
            } else {
                // Add non-array values directly.
                ...
            }
        }

        ...

        return [
            'current' => ...,
            'additional_information' => ...,
            'source' => ...,
        ];
    }

    private function flatten(array $values)
    {
      return Arr::flatten($values);
  }
}
```

## 步驟8：定義OrderItemCustomAttribute

建立定義訂單專案自訂屬性的`OrderItemCustomAttributes.php`檔案。 例如：

```php
namespace Magento\AepCustomAttributes\Model\Provider;

use Magento\Framework\Serialize\Serializer\Json;

class OrderItemCustomAttribute
{
    private Json $jsonSerializer;
    private string $usingField;

    public function __construct(Json $jsonSerializer, string $usingField)
    {
        $this->jsonSerializer = $jsonSerializer;
        $this->usingField = $usingField;
    }

    public function get(array $values): array
    {
        $output = [];
        $values = $this->flatten($values);

        foreach ($values as $row) {
            $info = \is_string($row['additionalInformation']) ? $row['additionalInformation'] : '{}';
            $unserializedData = $this->jsonSerializer->unserialize($info) ?? [];

            $attrLabel = implode(',', ['label1', 'label2']);
            $unserializedData['custom_attr1'] = $attrLabel;

            $additionalInformation = [];
            foreach ($unserializedData as $name => $value) {
                $additionalInformation[] = [
                    'name' => $name,
                    'value' => \is_string($value) ? $value : $this->jsonSerializer->serialize($value),
                ];
            }

            foreach ($additionalInformation as $information) {
                $output[] = [
                    'additionalInformation' => $information,
                    $this->usingField => $row[$this->usingField],
                ];
            }
        }

        return $output;
    }

    private function flatten(array $values): array
    {
        return array_merge([], ...array_values($values));
    }
}
```

## 步驟9：建立productContext檔案的目錄

在與`etc`目錄相同的層級，建立名為`Plugin/Module`的目錄。 此目錄包含`ProductContext.php`檔案。

## 步驟10：定義ProductContext類別

建立名為`ProductContext.php`的檔案來定義`ProductContext`類別。 例如：

```php
namespace Magento\Catalog\Model\Product;

use Magento\Framework\App\ResourceConnection;
use Magento\Quote\Api\Data\CartInterface;

class ProductContext
{
    private $brandCache = [];
    private $resourceConnection;

    public function __construct(
        ResourceConnection $resourceConnection
    ) {
        $this->resourceConnection = $resourceConnection;
    }

    public function afterGetProductData($subject, array $result)
    {
        if (isset($result['brand_id'])) {
            if (!isset($this->brandCache[$result['brand_id']])) {
                // @todo load brand label by brand id.
                $this->brandCache[$result['brand_id']] = 'Brand Label ' . $result['brand_id'];
            }
            $result['brands'] = ['label' => $this->brandCache[$result['brand_id']]];
        }

        return $result;
    }
}
```

## 步驟11：註冊模組

在與`etc`目錄相同的層級，建立登入模組的`registration.php`檔案。 例如：

```php
use \Magento\Framework\Component\ComponentRegistrar;

ComponentRegistrar::register(
    ComponentRegistrar::MODULE,
    'Dfe_Stripe',
    __DIR__
);
```

## 步驟12：擴充您現有的XDM結構

為確保您的[!DNL Commerce]結構描述能夠在Experience Platform中擷取新的自訂訂單屬性，您需要擴充結構描述以包含這些自訂欄位。

若要瞭解如何擴充現有的XDM結構描述以包含這些自訂欄位，請參閱Experience Platform檔案中的[在UI中建立及編輯結構描述](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/resources/schemas#custom-fields-for-standard-groups)一文。 租使用者ID欄位是動態產生的；但是，欄位結構應類似於Experience Platform檔案中提供的範例。

>[!IMPORTANT]
>
>XDM自訂屬性必須符合從[!DNL Commerce]傳送的屬性。

至`commerce.order`，新增訂單層級的欄位：

![訂單層級](assets/order-level.png)

至`productListItems`，新增訂單專案層級的欄位：

![訂單專案層級](assets/order-item-level.png)

## 步驟12：確認正在擷取資料

檢視Admin中的[資料自訂](connect-data.md#data-customization)索引標籤，以確認正在擷取自訂屬性資料並傳送給Experience Platform。

### 疑難排解

如果您在&#x200B;**[!UICONTROL Data Customization]**&#x200B;標籤上看到訊息`No custom order attributes found.`，請確認下列事項：

1. 您已完成啟用[Data Connector擴充功能](overview.md#prerequisites)的必要條件。
1. 您已設定[自訂訂單屬性](#add-custom-order-attributes)。
1. 至少已產生一個訂購事件。
