---
title: 簽出
description: 根據客戶需求自訂結帳。
feature: Payments, Checkout
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---


# 簽出

您可以設定Adobe Commerce的簽出功能 [!DNL Payment Services] 最適合您的購物者。 功能，例如 [訂單自動作廢](#order-auto-voided-if-error) 和 [信用卡保險庫](#credit-card-vaulting) 確保您的購物者擁有順暢的使用者體驗。

## 訂單在錯誤時自動失效

如果結帳時發生錯誤， [!DNL Payment Services] 自動使訂單失效/取消。

購物者的結帳頁面上會顯示錯誤訊息。 訊息可能會有所不同。

![檢查時發生錯誤](assets/user-checkout-error.png "取出時發生錯誤")

有關已取消訂單的註解也會顯示在特定的「管理員」中 [訂購](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/orders.html?lang=en).

![已取消訂單管理員中的訂單評論](assets/admin-checkout-error.png "已取消訂單管理員中的訂單評論")

如果購物者取得訂單授權，但並未建立訂單並轉換為 `Capture`，訂單會自動失效。 此程式可確保購物者的信用卡上不會預留任何信用額度，並避免在標準29天期間結束時授權失效時產生的付款提供者費用。

>[!NOTE]
>
>只有當客戶使用的付款方式設定為時，才會發生訂單自動作廢 `Authorize` 模式，非 `Authorize and Capture` 模式。

## 從產品頁面結帳

客戶使用PayPal或 [!DNL Pay Later] 按鈕，則只會購買目前產品頁面上所代表的專案。 已位於客戶購物車的專案不會新增至結帳流程，也不會購買。

此功能可讓客戶快速購買目前檢視的專案，同時保留先前新增至購物車的專案。
如果客戶取消訂單，目前產品頁面中的專案會新增到客戶的購物車。

當客戶從產品頁面進入結帳流程時，結帳頁面就會簡化，此檢視畫面只會顯示與訂單相關的資料和選項。

## 信用卡保險存放

購物者可以儲存或「儲存」他們的信用卡資訊，以供日後在網站層級（相同商家帳戶內的任何商店）購買。

另請參閱 [信用卡保險存放](vaulting.md) 以取得詳細資訊
