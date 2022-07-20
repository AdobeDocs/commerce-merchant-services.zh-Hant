---
title: 用戶會話生存期
description: 管理員可以配置您的Adobe Commerce用戶的cookie生存期 [!DNL Quick Checkout] 擴展。
source-git-commit: a95d2ed92c69feba03d1b84d44abf08c1d1b4029
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 0%

---


# 用戶會話生存期

購物者會話的生存期由多個因素決定，這些因素可在您的Adobe Commerce管理員中配置。 請參閱 [配置Cookie生存期](https://docs.magento.com/user-guide/customers/customer-online-options.html){target=_blank}以獲取詳細資訊。

配置的Cookie生存期可能會影響您 [!DNL Quick Checkout] 如果：

1. 由於不活動，購物者從Adobe Commerce註銷。
1. 的 [!DNL Bolt] 會話過期。

如果購物者在他們 [!DNL Bolt] 會話過期，訂單已成功下達，但用戶已從兩個網路註銷。

如果用戶在成功簽出後仍處於活動狀態，則不會從Adobe Commerce和 [!DNL Bolt]。
