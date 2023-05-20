---
title: 信用卡保險儲存
description: 購物者可以保存（保存）其信用卡詳細資訊以備將來購買。
exl-id: b4060307-ffcd-41cb-9b9d-a2fef02f23bd
source-git-commit: 817a01e98876bddf5f41a253501984539b3351cd
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# 信用卡保險儲存

將一次性客戶轉變為擁有信用卡保險庫的忠誠顧客。 購物者可在結帳期間保存或「保管庫」其信用卡憑據，以便在以後購買相同或其他商戶時，在同一商戶帳戶內儲存。

![保存信用卡供以後使用](assets/save-card-for-later.png)

購物者使用儲存的令牌，用他們保存的信用卡資訊完成將來的結帳。

![將儲存的憑據用於將來的購買](assets/use-stored-card.png)

他們還可以輕鬆地從 [儲存的付款方法](https://docs.magento.com/user-guide/customers/account-dashboard-stored-payment-methods.html) 在他們的賬戶里。

![在我的帳戶中儲存的付款方法](assets/stored-payment-methods.png)

## 啟用保險儲存

您可以為客戶啟用信用卡保險儲存 _和_ 管理員中的商戶 — 用於 [!DNL Payment Services] [設定](settings.md#card-vaulting)。

## 在管理中使用保險儲存

如果客戶擁有以前保險的信用卡，則商戶可以使用其保險支付方法在管理員中為該客戶建立後續訂單。

僅當客戶在系統中儲存了一個現有帳戶和一個有效令牌，並且該令牌是以前完成的付款時，您才能在管理員中使用保險卡。

要在管理員中為使用其拱形信用卡的客戶建立訂單，請執行以下操作：

1. [建立訂單並添加產品](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html)。
1. 在 _[!UICONTROL Payment & Shipping Information]_選中&#x200B;**[!UICONTROL Stored Cards]**付款方式。
1. 選擇所需的保險儲存信用卡付款方法。
1. 完成訂單的其他必要步驟後， [提交](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html?lang=en#step-3%3A-submit-the-order)。

   ![在管理員中為客戶使用保險卡](assets/admin-vaultedcard.png)

## 安全

最少的信用卡資訊與購物者共用；只看到其拱形信用卡的最後四位，過期日期和品牌。 信用卡資訊與支付提供方一起儲存以滿足 [PCI](security.md#PCI-compliance) 合規性標準。
