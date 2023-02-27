---
title: Inventory management來源轉移
description: 「為 [!DNL Store Fulfillment solution] Adobe Commerce·Inventory management。 設定新庫存並將庫存從預設庫存中轉移出來，這樣您就可以將它分配給配置為啟用「儲存完成」解決方案所需的儲存裝貨功能的來源。
role: User, Admin
level: Intermediate
exl-id: 669d4dce-4cac-4bde-acc5-26c70a51f7f1
source-git-commit: e7493618e00e28e2de5043ae2d7e05a81110d8f1
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---


# Inventory management來源轉移

此 [!DNL Store Fulfillment] 解決方案使用原生Adobe Commerce Inventory management。 依預設， [!DNL Commerce] 配置將所有Web庫存分配給預設庫存，但無法分配其他來源。 由於網站只能分配單個庫存，因此商家必須配置新庫存，並根據需要將其預設來源庫存轉移到分配給適當範圍的來源。 然後，可將源分配給新庫存。

>[!IMPORTANT]
>
>商家必須維護組和捆綁產品類型中包含的所有產品的預設來源。 這些產品需要滿足庫存物料中最小數量閾值的庫存數量，並且包括庫存狀態 [!UICONTROL In Stock].

這些設定變更可協助您完成下列三項工作：

1. [將庫存轉移至來源](https://docs.magento.com/user-guide/catalog/inventory-bulk-transfer-inventory.html) 要將庫存從預設庫存/來源移動到新庫存/來源，請執行以下操作：

1. [批量分配源](https://docs.magento.com/user-guide/catalog/inventory-bulk-assign-sources.html) 為所有產品新增新來源。

1. [產品屬性的完整大量更新](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html) 若要新增 `Allow Store Pickup` 和 `Allow Home Delivery` 屬性至現有產品。 安裝解決方案時，屬性會有最佳 *預設* 值。 不過，在您完成大量更新程式之前，這些屬性不會套用至現有產品。

庫存會從選取的來源（零售商店位置或電子商務倉庫）中扣除。 用作電子商務倉庫的來源必須分配給與商店裝貨位置相同的庫存，並且在零售位置之前優先。 如需詳細資訊，請參閱 [為庫存排定來源的優先順序](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html).

如需管理庫存、庫存和來源的詳細資訊，請參閱Adobe Commerce使用者檔案：

- [管理庫存](https://docs.magento.com/user-guide/catalog/inventory-management.html)

- [管理庫存數量](https://docs.magento.com/user-guide/catalog/inventory-manage-inventory-quantities.html)

- [管理庫存](https://docs.magento.com/user-guide/catalog/inventory-stock.html)

- [管理來源](https://docs.magento.com/user-guide/catalog/inventory-sources.html)

- [為庫存排定來源的優先順序](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html)

- [產品屬性的大量更新](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html)


>[!IMPORTANT]
>
>更改庫存和庫存源的配置也可能對整合系統產生下游影響。 請務必了解詳細目錄配置的變更如何影響這些系統。
