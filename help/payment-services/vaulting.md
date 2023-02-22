---
title: 信用卡保險儲存
description: 購物者可儲存（儲存）其信用卡詳細資訊，以供日後購買。
exl-id: b4060307-ffcd-41cb-9b9d-a2fef02f23bd
source-git-commit: 817a01e98876bddf5f41a253501984539b3351cd
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# 信用卡保險儲存

透過信用卡儲存，將一次性客戶轉化為忠誠的購物者。 購物者可在結帳期間儲存（或「保管庫」）其信用卡憑證，以用於稍後購買相同或其他商戶帳戶的商品。

![保管信用卡以備以後使用](assets/save-card-for-later.png)

購物者可使用儲存的代號，以儲存的信用卡資訊完成日後的結帳。

![使用儲存的憑據以備將來購買](assets/use-stored-card.png)

他們還可以輕鬆地從 [儲存的付款方法](https://docs.magento.com/user-guide/customers/account-dashboard-stored-payment-methods.html) 在他們的賬戶里。

![在我的帳戶中儲存的付款方法](assets/stored-payment-methods.png)

## 啟用保險儲存

您可以為客戶啟用信用卡保險儲存 _和_ 管理員中的商戶(針對 [!DNL Payment Services] [設定](settings.md#card-vaulting).

## 在管理中使用保險儲存

如果客戶有先前保險存的信用卡，則商家可以使用其保險存付款方法在管理員中為該客戶建立後續訂單。

如果客戶在系統中同時儲存現有帳戶和先前已完成付款的有效代號，則您只能在管理員中使用拱形卡。

要使用客戶的保險卡在管理員中建立訂單，請執行以下操作：

1. [建立訂單並新增產品](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html).
1. 在 _[!UICONTROL Payment & Shipping Information]_，選取&#x200B;**[!UICONTROL Stored Cards]**作為付款方式。
1. 選擇所需的保險卡付款方法。
1. 完成訂單的任何其他必要步驟後， [提交](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html?lang=en#step-3%3A-submit-the-order).

   ![在Admin中為客戶使用保險卡](assets/admin-vaultedcard.png)

## 安全性

最低的信用卡資訊與購物者共用；他們只看到其拱形信用卡的最後四位數、到期日和品牌。 信用卡資訊與支付提供商一起儲存以滿足 [PCI](security.md#PCI-compliance) 合規標準。
