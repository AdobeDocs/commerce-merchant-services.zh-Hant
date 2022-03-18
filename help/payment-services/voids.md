---
title: 空隙
description: 撤消允許您釋放信用卡或借記卡帳戶中的資金，這些資金被授權為購買金額而阻止或保留。
exl-id: 029a7038-2812-46ce-b188-929a7a758d89
source-git-commit: bcb817775fe9cd9ac7096931dd40d5ec0c4a5cfc
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# 空隙

與 [!DNL Payment Services]，您可以使用現有Commerce功能來撤消事務。 撤消允許您釋放信用卡或借記卡帳戶中的資金，這些資金被授權為購買金額而阻止或保留。

>[!NOTE]
>
>只有在尚未捕獲付款時，您才能撤消事務處理。

如果你的商店 [配置](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;}僅授權（未捕獲）銷售點的資金，從您的商店購買將導致與 `Processing` Magento管理中的狀態。

您也可以 [取消訂單](https://docs.magento.com/user-guide/sales/order-update.html#cancel-a-pending-order)未開票的{target=&quot;_blank&quot;}。 任何未捕獲的授權也作為取消過程的一部分被撤消。

>[!NOTE]
>
>取消訂單也會產生無效，但取消訂單不會觸發取消。

要瞭解有關訂單執行的基本步驟的詳細資訊，請參閱 [訂單工作流](https://docs.magento.com/user-guide/sales/order-workflow.html)核心使用手冊中的{target=&quot;_blank&quot;}主題。

要瞭解撤消功能以及如何撤消訂單事務處理，請參閱： [處理訂單](https://docs.magento.com/user-guide/sales/order-processing.html)核心使用手冊中的{target=&quot;_blank&quot;}。
