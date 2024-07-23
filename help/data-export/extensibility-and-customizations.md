---
title: 擴充及自訂SaaS資料匯出摘要資料
description: 瞭解如何擴充及自訂 [!DNL SaaS Data Export] 摘要資料。
role: Admin, Developer
recommendations: noCatalog
source-git-commit: 51238f86f36a756b86d07bdf6bb0a5cf0c61cbeb
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# 擴充及自訂SaaS資料匯出摘要資料

[!DNL Commerce Data Export]擴充功能可讓您將資料從[!DNL Commerce]應用程式匯出至Commerce服務，例如即時搜尋、目錄服務和產品Recommendations。 如有需要，您可以擴充及自訂摘要資料，以包含其他資料，或更新`Magento\CatalogDataExporter`模組以修改收集的資料。

>[!NOTE]
>
>將新資料新增至摘要或修改現有資料可能會影響摘要收集效能，並導致Adobe Commerce端的處理邏輯發生問題。 在合併至生產環境之前，請務必測試自訂的程式碼。

## 擴充產品摘要中的屬性資料

產品摘要包含產品處理所需或消費者常用的預設屬性。 您可以將其他系統屬性新增至摘要，以將其納入產品摘要中。

若要完成此工作，請更新`magento/catalog-data-exporter`模組以將其他系統屬性新增到[相依性插入組態檔](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/) (`di.xml`)。 將屬性新增至產品屬性查詢(`Magento\CatalogDataExporter\Model\Query\ProductAttributeQuery`)。

**範例**

```xml
    <type name="Magento\CatalogDataExporter\Model\Query\ProductAttributeQuery">
        <arguments>
            <argument name="systemAttributes" xsi:type="array">
                <item name="news_from_date" xsi:type="string">news_from_date</item>
                ...
                <item name="some_system_attribute_code">some_system_attribute_code</item>
            </argument>
        </arguments>
    </type>
```
