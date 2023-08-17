---
title: 「測試 [!DNL Quick Checkout] 適用於Adobe Commerce擴充功能」
description: 「測試和驗證可確保 [!DNL Quick Checkout] 擴充功能如預期運作。」
exl-id: 308f39e1-e2f6-40d8-b876-0f9013effed3
feature: Checkout, Services
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---


# 測試 [!DNL Quick Checkout] 副檔名

在您公開 [!DNL Quick Checkout] 若是給購物者使用的Adobe Commerce擴充功能，建議您在沙箱環境和生產環境中測試。 測試和驗證可確保 [!DNL Quick Checkout] 可如預期運作，並為您的商店和客戶提供順暢的結帳體驗。

設定之前 [!DNL Quick Checkout] 在您的Adobe Commerce管理員中，需要建立  [生產](https://merchant.bolt.com/register){target="_blank"} and [sandbox](https://merchant-sandbox.bolt.com/register){target="_blank"} 中的商家帳戶 [!DNL Bolt].

## 在沙箱中測試

測試 [!DNL Quick Checkout] 在沙箱環境中，是一個非常重要的驗證步驟，即使它是一個僅連線到 [!DNL Bolt] 沙箱帳戶，不適用於真正的銀行或商家。

### 使用沙箱帳戶

當您測試及驗證沙箱時，必須使用假信用卡號碼和 [沙箱](https://merchant-sandbox.bolt.com/register){target="_blank"} 中的商家帳戶 [!DNL Bolt]，以免建立現有信用卡帳戶的實際費用。

## 在生產環境中測試

>[!NOTE]
>
> 強烈建議您測試 [!DNL Quick Checkout] 在生產環境中，使用真實的信用卡和銀行，然後將擴充功能公開給購物者。 雖然在沙箱中測試很重要，但在生產環境中測試是確保如預期般運作的最萬無一失的方法。

使用以下兩種建議方式之一測試您的生產環境：

- 選擇您知道購物者不會下訂單的時間。
- 使用購物者暫時無法存取但可供您存取以進行測試的網站商店。

使用真正的信用卡完成您的生產測試，並 [!DNL Bolt] 生產帳戶，測試結帳的整個生命週期。 當您在測試期間完成整個結帳流程時，可清楚瞭解當直播購物者使用此功能時的運作方式。

您也應確認出現在銀行對帳單上，用於生產測試之付款方式的資訊正確且符合預期（包括業務說明）。

## 如何測試 [!DNL Quick Checkout] 副檔名

完成從商店的成功結帳：

1. 前往您的店面，並將想要的商品放入購物車中。
1. 繼續結帳。
1. 輸入與關聯的電子郵件地址 [!DNL Bolt] 帳戶。
1. 輸入傳送到帳戶電子郵件地址的一次性密碼(OTP)。
1. 選取環境控制面板：

   - Sandbox
   - 生產

1. 下訂單。

下單後，您就可以在 _訂單格線_ 檢視：

1. 瀏覽至 _銷售_ > _訂購_.
1. 檢視所有下單的訂單清單。

請參閱 [訂購](https://docs.magento.com/user-guide/sales/orders.html) 主題，以取得關於您的 _訂單格線_ 檢視。
