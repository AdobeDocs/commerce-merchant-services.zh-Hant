---
title: 空位
description: 「作廢」可讓您從信用卡或借記卡帳戶中釋放資金，這些帳戶已遭封鎖或因授權而保留以支付購買金額。
exl-id: 029a7038-2812-46ce-b188-929a7a758d89
source-git-commit: 7b31fe7a71c3c238e6448627b2edfe06bbfbc80e
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---

# 空位

替換為 [!DNL Payment Services]，您可以使用現有的Commerce功能來作廢交易。 「作廢」可讓您從信用卡或借記卡帳戶中釋放資金，這些帳戶已遭封鎖或因授權而保留以支付購買金額。

>[!NOTE]
>
>只有在尚未抓取付款時，您才能作廢交易。

如果您的商店為 [已設定](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} 若要在銷售點僅授權（而非擷取）資金，從您的商店購買會導致訂單包含 `Processing` 商務管理員中的狀態。

您也可以 [取消訂單](https://docs.magento.com/user-guide/sales/order-update.html#cancel-a-pending-order){target="_blank"} 未開立商業發票。 在該取消程式中，任何未擷取的授權也會失效。

>[!NOTE]
>
>取消訂單也會產生作廢，但作廢訂單不會觸發取消。

若要進一步瞭解訂單所經過的基本步驟，請參閱 [訂單工作流程](https://docs.magento.com/user-guide/sales/order-workflow.html){target="_blank"} 核心使用手冊中的主題。

若要瞭解作廢功能以及如何作廢訂單異動，請參閱 [處理訂單](https://docs.magento.com/user-guide/sales/order-processing.html){target="_blank"} 在核心使用手冊中。
