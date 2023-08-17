---
title: 使用者工作階段存留期
description: 管理員可為設定Adobe Commerce使用者的Cookie存留期 [!DNL Quick Checkout] 副檔名。
exl-id: 32cf5d70-9a50-49ca-8b40-5f04bc1e24b7
feature: Checkout, Services
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---

# 使用者工作階段存留期

購物者工作階段的期限取決於數個因素，可在您的Adobe Commerce管理員中加以設定。 另請參閱 [設定Cookie期限](https://experienceleague.adobe.com/docs/commerce-admin/customers/customer-accounts/configure/customer-online-options.html){target=_blank} 以取得詳細資訊。

設定的Cookie存留期可能會影響您的 [!DNL Quick Checkout] 如果：

1. 由於非使用中，購物者會登出Adobe Commerce。
1. 此 [!DNL Bolt] 工作階段過期。

如果購物者在其購物時下訂單 [!DNL Bolt] 工作階段過期，已成功下訂單，但使用者已從兩個網路登出。

如果使用者在成功結帳後仍為作用中，他們將不會同時從Adobe Commerce和登出 [!DNL Bolt].
