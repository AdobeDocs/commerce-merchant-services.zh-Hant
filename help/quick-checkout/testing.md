---
title: 「測試 [!DNL Quick Checkout] 適用於Adobe Commerce擴充功能」
description: 「測試和驗證可確保 [!DNL Quick Checkout] 擴充功能如預期運作。」
exl-id: 308f39e1-e2f6-40d8-b876-0f9013effed3
source-git-commit: bd02a8083d3f4c9cb0422b27d61bd5462187ffc3
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---


# 測試 [!DNL Quick Checkout] 擴充功能

在您公開 [!DNL Quick Checkout] 若是給購物者使用的Adobe Commerce擴充功能，建議您在沙箱環境和生產環境中測試。 測試和驗證可確保 [!DNL Quick Checkout] 如預期運作，為您的商店和客戶提供順暢的結帳體驗。

設定之前 [!DNL Quick Checkout] 在您的Adobe Commerce管理員中，需要建立  [生產](https://merchant.bolt.com/register){target="_blank"} and [sandbox](https://merchant-sandbox.bolt.com/register){target="_blank"} 中的商家帳戶 [!DNL Bolt].

## 在沙箱中測試

測試 [!DNL Quick Checkout] 在沙箱環境中是非常重要的驗證步驟，即使它是僅連線到 [!DNL Bolt] 沙箱帳戶，不適用於真正的銀行或商家。

### 使用沙箱帳戶

當您測試及驗證沙箱時，您必須使用假信用卡號碼和 [沙箱](https://merchant-sandbox.bolt.com/register){target="_blank"} 中的商家帳戶 [!DNL Bolt]，以免建立現有信用卡帳戶的實際費用。

## 在生產環境中測試

>[!NOTE]
>
> 強烈建議您測試 [!DNL Quick Checkout] 在生產環境中，使用真實的信用卡和銀行，然後將擴充功能公開給購物者。 雖然在沙箱中測試很重要，但在生產環境中測試是確保正常運作最萬無一失的方法。

使用以下兩種建議方式之一測試您的生產環境：

- 選擇您知道購物者不會下訂單的時間。
- 使用購物者暫時無法存取但可供您存取以進行測試的網路商店。

使用真正的信用卡完成您的生產測試，並且 [!DNL Bolt] 生產帳戶，測試結帳的整個生命週期。 當您在測試期間完成整個結帳流程時，可讓您清楚瞭解當即時購物者使用此功能時的運作方式。

您也應確認出現在銀行對帳單上，用於生產測試中付款方式的資訊正確與預期（包括業務說明）。

## 如何測試 [!DNL Quick Checkout] 擴充功能

從您的商店成功完成結帳：

1. 前往您的店面，並將所需商品放入購物車中。
1. 繼續結帳。
1. 輸入與關聯的電子郵件地址 [!DNL Bolt] 帳戶時。
1. 輸入傳送至帳戶電子郵件地址的一次性密碼(OTP)。
1. 選取環境控制面板：

   - Sandbox
   - 生產

1. 下訂單。

下訂單後，您便可以在下列位置檢視訂單的詳細資料： _訂單格線_ 檢視：

1. 導覽至 _銷售_ > _訂購_.
1. 檢視所有已下訂單的清單。

請參閱 [訂購](https://docs.magento.com/user-guide/sales/orders.html) 主題以取得更多關於您的資訊 _訂單格線_ 檢視。
