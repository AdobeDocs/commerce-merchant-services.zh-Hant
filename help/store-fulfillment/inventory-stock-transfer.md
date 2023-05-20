---
title: Inventory management源傳輸
description: "配置 [!DNL Store Fulfillment solution] Adobe Commerce·Inventory management。 設定新庫存並從預設庫存中轉移庫存，以便您可以將其分配給配置為啟用「商店完成」解決方案所需的「商店提貨」功能的來源。"
role: User, Admin
level: Intermediate
exl-id: 669d4dce-4cac-4bde-acc5-26c70a51f7f1
source-git-commit: e7493618e00e28e2de5043ae2d7e05a81110d8f1
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---


# Inventory management源傳輸

的 [!DNL Store Fulfillment] 解決方案使用Adobe CommerceInventory management。 預設情況下， [!DNL Commerce] 配置將所有Web庫存分配給預設庫存，而預設庫存不能分配附加來源。 由於網站只能分配單個庫存，因此商家必須配置新庫存，並根據需要將其預設來源庫存轉移到分配給相應範圍的來源。 然後，可將源分配給新庫存。

>[!IMPORTANT]
>
>商家必須維護組和捆綁產品類型中包括的所有產品的預設來源。 這些產品需要滿足庫存物料的最小數量閾值的庫存數量，並且庫存狀態為 [!UICONTROL In Stock]。

這些配置更改可幫助您完成以下三項任務：

1. [將庫存轉移到來源](https://docs.magento.com/user-guide/catalog/inventory-bulk-transfer-inventory.html) 將庫存從預設庫存/來源移至新庫存/來源。

1. [批量分配源](https://docs.magento.com/user-guide/catalog/inventory-bulk-assign-sources.html) 添加所有產品的新源。

1. [完成產品屬性的批量更新](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html) 的 `Allow Store Pickup` 和 `Allow Home Delivery` 屬性。 安裝解決方案時，屬性具有 *預設* 值。 但是，在您完成批量更新過程之前，這些屬性不會應用於現有產品。

庫存從選定來源（零售商店地點或電子商務倉庫）中扣除。 用作電子商務倉庫的來源必須與商店裝貨地點分配到相同的庫存，並在零售地點之前排定優先順序。 有關其他資訊，請參見 [對庫存的來源進行優先排序](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html)。

有關管理庫存、庫存和來源的詳細資訊，請參閱Adobe Commerce用戶文檔：

- [管理庫存](https://docs.magento.com/user-guide/catalog/inventory-management.html)

- [管理庫存數量](https://docs.magento.com/user-guide/catalog/inventory-manage-inventory-quantities.html)

- [管理庫存](https://docs.magento.com/user-guide/catalog/inventory-stock.html)

- [管理源](https://docs.magento.com/user-guide/catalog/inventory-sources.html)

- [對庫存的來源進行優先排序](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html)

- [產品屬性的批量更新](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html)


>[!IMPORTANT]
>
>更改庫存和庫存來源的配置也會對整合系統產生下游影響。 確保您瞭解對清單配置的更改如何影響這些系統。
