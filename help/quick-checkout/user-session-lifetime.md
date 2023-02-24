---
title: 使用者工作階段存留期
description: 管理員可為 [!DNL Quick Checkout] 擴充功能。
exl-id: 32cf5d70-9a50-49ca-8b40-5f04bc1e24b7
source-git-commit: b89427124cf76e7f36076454949191ee1d88f52c
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---

# 使用者工作階段期限

購物者工作階段的存留期由數個因素決定，可在您的Adobe Commerce管理員中設定。 請參閱 [設定Cookie期限](https://experienceleague.adobe.com/docs/commerce-admin/customers/customer-accounts/configure/customer-online-options.html){target=_blank} 以取得更多資訊。

已設定的Cookie存留期可能會影響您的 [!DNL Quick Checkout] 如果：

1. 由於無活動，購物者會登出Adobe Commerce。
1. 此 [!DNL Bolt] 工作階段過期。

如果購物者在 [!DNL Bolt] 工作階段過期時，順利下訂單，但使用者已從兩個網路登出。

如果使用者在成功結帳後仍處於作用中狀態，則不會從Adobe Commerce和 [!DNL Bolt].
