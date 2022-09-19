---
title: 空洞
description: 撤消允許您釋放信用卡或借記卡帳戶中的資金，這些資金被授權阻止或保留以獲取購買金額。
exl-id: 029a7038-2812-46ce-b188-929a7a758d89
source-git-commit: 7b31fe7a71c3c238e6448627b2edfe06bbfbc80e
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# 空洞

使用 [!DNL Payment Services]，您可以使用現有的商務功能來撤消交易。 撤消允許您釋放信用卡或借記卡帳戶中的資金，這些資金被授權阻止或保留以獲取購買金額。

>[!NOTE]
>
>只有在尚未捕獲付款時，您才可以撤消交易記錄。

如果您的商店是 [已配置](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;}僅授權（非擷取）銷售點的資金，從您的商店購買會導致訂單與 `Processing` 狀態（在商務管理員中）。

您也可以 [取消訂單](https://docs.magento.com/user-guide/sales/order-update.html#cancel-a-pending-order)未開具發票的{target=&quot;_blank&quot;}。 任何未捕獲的授權也作為取消過程的一部分被撤消。

>[!NOTE]
>
>取消訂單也會產生無效，但取消訂單並不會觸發取消。

若要進一步了解訂單所經過的基本步驟，請參閱 [訂單工作流程](https://docs.magento.com/user-guide/sales/order-workflow.html)核心使用手冊中的{target=&quot;_blank&quot;}主題。

要了解撤消功能以及如何撤消訂單交易，請參閱 [處理訂單](https://docs.magento.com/user-guide/sales/order-processing.html)核心使用手冊中的{target=&quot;_blank&quot;}。
