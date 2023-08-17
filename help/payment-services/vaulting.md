---
title: 信用卡存放
description: 購物者可以儲存信用卡詳細資料，以便日後購買。
exl-id: b4060307-ffcd-41cb-9b9d-a2fef02f23bd
feature: Payments, Checkout
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# 信用卡存放

透過信用卡保險庫將一次性客戶轉換為忠實購物者。 購物者可以在結帳時儲存（或「儲存庫」）他們的信用卡憑證，以便用於稍後購買相同或另一個商店的相同商家帳戶。

![儲存他們的信用卡以供日後使用](assets/save-card-for-later.png)

購物者會使用儲存的代號，以其儲存的信用卡資訊完成未來的結帳。

![使用已儲存的憑證以供日後購買](assets/use-stored-card.png)

他們也可以輕鬆地從刪除其存放的信用卡 [儲存的付款方法](https://docs.magento.com/user-guide/customers/account-dashboard-stored-payment-methods.html) 在我帳戶中。

![我的帳戶中儲存的付款方法](assets/stored-payment-methods.png)

## 啟用存放區

您可以為客戶啟用信用卡存放區 _和_ Admin中的商家 — 適用於您位於以下位置的商店： [!DNL Payment Services] [設定](settings.md#card-vaulting).

## 在管理員中使用存放區

如果客戶先前擁有儲存的信用卡，則商家可以使用其儲存的付款方式，在「管理員」中建立該客戶的後續訂單。

如果客戶同時擁有現有帳戶，且系統中儲存了先前完成付款的有效權杖，則您只能在「管理員」中使用存放卡。

若要在「管理員」中，使用客戶的保管式信用卡來建立訂單：

1. [建立訂單並新增產品](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html).
1. 在 _[!UICONTROL Payment & Shipping Information]_，選取&#x200B;**[!UICONTROL Stored Cards]**作為付款方式。
1. 選取所需的存放信用卡付款方式。
1. 完成訂單的任何其他必要步驟後， [提交它](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html?lang=en#step-3%3A-submit-the-order).

   ![在管理中使用客戶的保管式信用卡](assets/admin-vaultedcard.png)

## 安全性

最低限度的信用卡資訊會與購物者共用；他們只會看到其存放的信用卡的最後四位數字、到期日及品牌。 信用卡資訊會與付款提供者一併儲存以滿足 [PCI](security.md#PCI-compliance) 法規遵循標準。
