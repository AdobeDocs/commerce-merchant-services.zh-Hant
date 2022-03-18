---
title: 退款
description: 建立退款 [!DNL Payment Services] 作為貸項通知單流程的一部分。
exl-id: 2b3721a1-9c9d-4e3f-ab7d-5bd61573dcb4
source-git-commit: fd818dadbaa2a58efd7313ce888c7dda27d25f14
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# 退款

退款 [!DNL Payment Services] 訂單是作為貸項通知單流程的一部分在管理員中建立的。 貸項通知單是一份單據，它顯示應付客戶的全額或部分退款金額，這些退款可以應用於採購或直接退還給客戶。 只能為以下訂單簽發貸項通知單 [發票](https://docs.magento.com/user-guide/sales/invoice-create.html){target=&quot;_blank&quot;}。

請參閱 [貸項通知單](https://docs.magento.com/user-guide/sales/credit-memos.html)有關詳細資訊，並瞭解如何發放和打印貸項通知單的核心使用手冊中的{target=&quot;_blank&quot;}。

對於使用PayPal或信用卡處理的訂單，您可以：

* 退款訂單的全部金額
* 退回訂單的部分金額（或多個部分金額）
* 退款金額小於特定訂單項的值

請參閱 [簽發貸項通知單](https://docs.magento.com/user-guide/sales/credit-memo-create.html)有關詳細資訊，請參閱我們的核心使用手冊中的{target=&quot;_blank&quot;}。

>[!NOTE]
>
>如果您試圖將訂單部分退款至超過剩餘訂單金額（原始金額減去現有退款總額），或者您為大於全部訂單金額的金額發放退款，則PayPal或信用卡處理的訂單將出錯。

的 [!UICONTROL Payment Action] 設定 [!UICONTROL Payment Settings] 配置 — 或 `Authorize` 或 `Authorize and Capture` — 確定 [基本退款工作流](https://docs.magento.com/user-guide/sales/credit-memos.html#refund-workflow)訂單的{target=&quot;_blank&quot;}。

查看 [付款活動設定部分](https://docs.magento.com/user-guide/sales/credit-memo-create.html#payment-action-setting){target=&quot;_blank&quot;，共 _簽發貸項通知單_ 的子菜單。
