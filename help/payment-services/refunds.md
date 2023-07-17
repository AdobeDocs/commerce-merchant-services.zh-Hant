---
title: 退款
description: 建立退款對象 [!DNL Payment Services] 「管理員」中的訂單，作為銷退折讓單處理的一部分。
exl-id: 2b3721a1-9c9d-4e3f-ab7d-5bd61573dcb4
feature: Payments, Checkout
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---

# 退款

退款 [!DNL Payment Services] 訂單是在「管理員」中建立的，作為銷退折讓單處理的一部分。 銷退折讓單是一種檔案，可顯示全部或部分退款應付給客戶的金額，這些金額可用於購買或直接退款給客戶。 只能針對下列訂單發出銷退折讓單： [已開發票](https://docs.magento.com/user-guide/sales/invoice-create.html){target="_blank"}.

另請參閱 [銷退折讓單](https://docs.magento.com/user-guide/sales/credit-memos.html){target="_blank"} 請參閱我們的核心使用指南，以取得詳細資訊，並瞭解如何核發及列印銷退折讓單。

對於使用PayPal或信用卡處理的訂單，您可以：

* 退還訂單的全部金額
* 退回訂單的部分金額（或多個部分金額）
* 退回小於特定訂單料號值的金額

另請參閱 [核發銷退折讓單](https://docs.magento.com/user-guide/sales/credit-memo-create.html){target="_blank"} 詳細資訊，請參閱我們的核心使用手冊。

>[!NOTE]
>
>如果您嘗試對超過剩餘訂單金額（原始金額減去現有退款總額）的訂單進行部份退款，或是您核發的退款金額大於全部訂單金額，PayPal或信用卡處理的訂單就會發生錯誤。

此 [!UICONTROL Payment Action] 在您的 [!UICONTROL Payment Settings] 組態 — 任一 `Authorize` 或 `Authorize and Capture` — 決定 [基本退款工作流程](https://docs.magento.com/user-guide/sales/credit-memos.html#refund-workflow){target="_blank"} 訂購。

請參閱 [付款動作設定區段](https://docs.magento.com/user-guide/sales/credit-memo-create.html#payment-action-setting){target="_blank"} 之 _核發銷退折讓單_ 以取得詳細資訊。
