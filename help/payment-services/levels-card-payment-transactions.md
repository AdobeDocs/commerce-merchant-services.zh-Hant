---
title: 第2級和第3級處理
description: 中的卡付款處理層級 [!DNL Payment Services] 交易。
role: Admin
feature: Payments
source-git-commit: d1379bb108f2259051641a7bf77cd8b459fd9cbf
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---


# 第2級和第3級處理

提供三種層級的卡片處理方式： [!DNL Payment Services]：

* 層級1是最常見的，需要較少的資訊，因此通常比使用層級2或層級3資料處理的交易產生較高的交換費用，這些資料通常與公司和購買信用卡有關。

* 有第2層和第3層， [!DNL Payment Services] 接受大量購買卡或公司卡交易的交換加(IC++)定價客戶，可能會因為允許交易而獲得較低的處理率 [!DNL Payment Services] 以傳送有關交易的詳細資訊。 如果交易符合資格，則根據卡片網路需求，商家可能會收到特定交易的較低處理率。

>[!NOTE]
>
>層級2與層級3訂價僅適用於Visa與MasterCard交易。 American Express只提供第2層定價。 Discover不提供第2級或第3級定價。 另請參閱 [付款處理](https://developer.paypal.com/docs/checkout/advanced/processing/){target=_blank} 如需詳細資訊，請參閱PayPal開發人員檔案。

另請參閱 [什麼是IC++?](https://www.paypal.com/us/brc/article/what-is-interchange-plus-plus){target=_blank} 如需詳細資訊，請參閱PayPal開發人員檔案。

第2級與第3級處理資料可讓商家降低其IC++定價，前提是他們提供購買的其他細節，以降低處理器風險，並提供有利的方面：

* 提供這項處理資料，大型客戶的費用將會降低。

* 客戶不太可能遇到詐騙情況，因為訂單具有更多資訊。

不過，卡片網路（如Visa和Mastercard）最終會決定交易是否符合第2級或第3級處理的資格：

* 第2層資料包含其他資訊，例如訂單的稅捐金額、客戶代碼或採購單編號。

* 第3層資料更瞭解有關銷售的詳細資訊，這有助於取得相較於第2層更低的交換率。 第3層資料包含採購料號摘要、採購單位數量、訂購料號的單位及其他特定明細等資訊。

[!DNL Payment Services] 會收集這項資料，並提供付款交易的詳細報表。

## 中的第2層及第3層卡付款交易 [!DNL Payment Services]

要符合第2級或第3級處理的資格，商家必須傳送先前的資訊，不過最終決定交易在處理時符合哪個層級的資訊是卡片網路。

請參閱 [付款處理常見問題集](https://www.paypal.com/us/cshelp/article/ts2278?_ga=1.131773126.875104296.1712843492){target=_blank} 如需詳細資訊，請參閱PayPal開發人員檔案。

根據預設，第2層及第3層處理功能會停用 [!DNL Payment Services] 商店級別的商家。

如果您已使用IC++訂價，便可使用第2級與第3級處理。 若要啟用此功能，您可以透過 [命令列介面(CLI)](configure-cli.md).

>[!IMPORTANT]
>
>如果您有任何問題，請聯絡您的 [!DNL Payment Services] 客戶經理。
