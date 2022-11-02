---
title: '"測試 [!DNL Quick Checkout] 適用於Adobe Commerce擴充功能」'
description: 「測試和驗證可確保 [!DNL Quick Checkout] 擴充功能可如預期般運作。」
exl-id: 308f39e1-e2f6-40d8-b876-0f9013effed3
source-git-commit: bd02a8083d3f4c9cb0422b27d61bd5462187ffc3
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 測試 [!DNL Quick Checkout] 擴充功能

在您公開 [!DNL Quick Checkout] 若要為您的購物者提供Adobe Commerce擴充功能，建議您在沙箱環境和生產環境中測試。 測試和驗證有助於確保 [!DNL Quick Checkout] 可如預期般運作，為您的商店和客戶提供順暢的結帳體驗。

設定之前 [!DNL Quick Checkout] 在您的Adobe Commerce管理員中，必須建立  [生產](https://merchant.bolt.com/register){target=&quot;_blank&quot;}和 [沙箱](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;}中的商家帳戶 [!DNL Bolt].

## 在沙箱中測試

測試 [!DNL Quick Checkout] 沙箱環境中是非常重要的驗證步驟，即使是僅與連結的模擬環境 [!DNL Bolt] 沙箱帳戶，不是給真正的銀行或商戶。

### 使用沙箱帳戶

測試及驗證沙箱時，您必須使用假信用卡號碼和 [沙箱](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;}中的商家帳戶 [!DNL Bolt]，以便您不會對現有信用卡帳戶建立實際費用。

## 在生產環境中進行測試

>[!NOTE]
>
> 強烈建議您測試 [!DNL Quick Checkout] 在生產環境中，使用真正的信用卡和銀行，然後將擴充功能向購物者公開。 雖然在沙箱中進行測試很重要，但在生產中進行測試是確保其如預期般運作的最蠢方法。

使用以下兩種建議方式之一測試您的生產環境：

- 選擇您知道購物者不會下訂單的時間。
- 使用暫時無法供購物者存取，但可供您測試的網站商店。

使用真實信用卡完成生產測試， [!DNL Bolt] 生產帳戶，測試結帳的整個生命週期。 當您在測試期間完成整個結帳流程時，可清楚了解即時購物者使用此功能時的運作方式。

您還應驗證銀行對帳單上顯示的資訊是否正確且預期（包括業務說明）。

## 如何測試 [!DNL Quick Checkout] 擴充功能

從您的商店完成成功的結帳：

1. 前往您的店面，並將所需項目放入購物車中。
1. 繼續結帳。
1. 輸入與 [!DNL Bolt] 帳戶。
1. 輸入傳送至帳戶電子郵件地址的一次性密碼(OTP)。
1. 選取環境控制面板：

   - 沙箱
   - 生產

1. 下訂單。

下訂單後，您可以在 _訂購網格_ 檢視：

1. 導覽至 _銷售_ > _訂購_.
1. 查看所有已下訂單的清單。

請參閱 [訂購](https://docs.magento.com/user-guide/sales/orders.html) 主題，以取得 _訂購網格_ 檢視。
