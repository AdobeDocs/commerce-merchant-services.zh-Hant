---
title: Inventory management來源轉移
description: 「設定庫存 [!DNL Store Fulfillment solution] Adobe Commerce Inventory management。 設定新的存貨，並將存貨移出預設存貨，以便您可以將其指定給設定為啟用「商店履行」解決方案所需的「商店提貨」功能的來源。」
role: Admin
level: Intermediate
feature: Shipping/Delivery, Inventory, Configuration
exl-id: 669d4dce-4cac-4bde-acc5-26c70a51f7f1
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---


# Inventory management來源轉移

此 [!DNL Store Fulfillment] 解決方案使用原生Adobe Commerce Inventory management。 根據預設， [!DNL Commerce] 「設定」會將所有網頁庫存指派給預設存貨，此預設庫存不能有其他指派的來源。 由於網站只能指定單一存貨，商家必須設定新存貨，並選擇性地將其預設來源存貨移轉至指定至適當範圍的來源。 然後，可將來源指派給新庫存。

>[!IMPORTANT]
>
>商家必須維護群組及套件產品型別中包含之所有產品的預設來源。 這些產品需要存貨數量符合庫存料號的最低數量臨界值，並包含存貨狀態 [!UICONTROL In Stock].

這些設定變更可協助您完成下列三件事：

1. [將存貨移轉至來源](https://docs.magento.com/user-guide/catalog/inventory-bulk-transfer-inventory.html) 將存貨從預設存貨/來源移至新存貨/來源。

1. [大量指派來源](https://docs.magento.com/user-guide/catalog/inventory-bulk-assign-sources.html) 以新增所有產品的新來源。

1. [完成產品屬性的大量更新](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html) 新增 `Allow Store Pickup` 和 `Allow Home Delivery` 屬性至現有產品。 安裝解決方案時，屬性具有最佳化 *預設* 值。 不過，在您完成大量更新內容程式之前，這些屬性不會套用至現有產品。

庫存會從選取的來源（零售商店地點或電子商務倉儲）中扣除。 用作電子商務倉儲的來源必須指派給與商店取貨地點相同的存貨，並在零售地點之前排定優先順序。 如需詳細資訊，請參閱 [排定庫存來源的優先順序](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html).

如需管理存貨、庫存和來源的詳細資訊，請參閱Adobe Commerce使用者檔案：

- [管理詳細目錄](https://docs.magento.com/user-guide/catalog/inventory-management.html)

- [管理存貨數量](https://docs.magento.com/user-guide/catalog/inventory-manage-inventory-quantities.html)

- [管理庫存](https://docs.magento.com/user-guide/catalog/inventory-stock.html)

- [管理來源](https://docs.magento.com/user-guide/catalog/inventory-sources.html)

- [排定庫存來源的優先順序](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html)

- [產品屬性的大量更新](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html)


>[!IMPORTANT]
>
>變更庫存和庫存來源的設定也會對整合系統產生下游影響。 確保您瞭解庫存設定的變更如何影響這些系統。
