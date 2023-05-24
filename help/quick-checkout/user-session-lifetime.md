---
title: 使用者工作階段期限
description: 管理員可針對以下專案設定Adobe Commerce使用者的Cookie存留期： [!DNL Quick Checkout] 副檔名。
exl-id: 32cf5d70-9a50-49ca-8b40-5f04bc1e24b7
source-git-commit: b89427124cf76e7f36076454949191ee1d88f52c
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---

# 使用者工作階段存留期

購物者工作階段的期限由數個因素決定，這些因素可在您的Adobe Commerce管理員中設定。 另請參閱 [設定Cookie期限](https://experienceleague.adobe.com/docs/commerce-admin/customers/customer-accounts/configure/customer-online-options.html){target=_blank} 以取得詳細資訊。

設定的Cookie期限可能會影響 [!DNL Quick Checkout] 如果：

1. 由於非使用中，購物者會登出Adobe Commerce。
1. 此 [!DNL Bolt] 工作階段過期。

如果購物者下訂單時 [!DNL Bolt] 工作階段過期，訂單已成功下達，但使用者已從兩個網路登出。

如果使用者在成功結帳後仍為作用中，他們將不會同時從Adobe Commerce和登出 [!DNL Bolt].
