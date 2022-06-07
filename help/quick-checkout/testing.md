---
title: 「測試 [!DNL Quick Checkout] Adobe Commerce分機」
description: 「測試和驗證確保 [!DNL Quick Checkout] 分機工作正常。」
exl-id: 308f39e1-e2f6-40d8-b876-0f9013effed3
source-git-commit: 9841db7616c8aa6d5bc5af3e6e92c0abe9a4a1e2
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---


# Test [!DNL Quick Checkout] 擴展

在你揭露 [!DNL Quick Checkout] 對於您的購物者的Adobe Commerce分機，建議在沙盒環境和生產環境中test。 測試和驗證有助於確保 [!DNL Quick Checkout] 按預期工作，為您的商店和客戶提供無縫的結賬體驗。

在配置 [!DNL Quick Checkout] 在您的Adobe Commerce管理員中，需要建立  [生產](https://merchant.bolt.com/register){target=&quot;_blank&quot;和 [沙坑](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;中的商家帳戶 [!DNL Bolt]。

## 在沙盒中測試

測試 [!DNL Quick Checkout] 在沙箱環境中是非常重要的驗證步驟，即使它是僅連接到模擬環境的驗證步驟 [!DNL Bolt] 沙箱賬戶，不是給真正的銀行或商戶。

### 使用沙盒帳戶

test和驗證沙盒時，必須使用假信用卡號和 [沙坑](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;中的商戶帳戶 [!DNL Bolt]，以便您不會為現有信用卡帳戶建立實際費用。

## 在生產中測試

>[!NOTE]
>
> 強烈建議您test [!DNL Quick Checkout] 在生產環境中，真正的信用卡和銀行，然後把延期權交給購物者。 儘管沙盒測試很重要，但生產測試是確保其按預期工作的最可靠方法。

Test您的生產環境，採用以下兩種推薦方式之一：

- 選擇您知道購物者不會下訂單的時間。
- 使用Webstore，該Webstore暫時無法訪問，但您可以訪問它進行測試。

使用真實信用卡完成生產測試， [!DNL Bolt] 生產客戶，測試結帳的整個生命週期。 當您在測試期間完成整個結帳流程時，它將清晰地顯示即時購物者使用功能時的功能如何工作。

您還應驗證在銀行對帳單上顯示的有關您在生產測試中使用的付款方法的資訊是否正確且預期（包括業務說明）。

## 如何test [!DNL Quick Checkout] 擴展

從您的商店完成成功結帳：

1. 轉到您的店面，將所需的物品放在您的購物車中。
2. 繼續簽出。
3. 輸入與 [!DNL Bolt] 帳戶。
4. 輸入發送到帳戶電子郵件地址的一次性密碼(OTP)。
5. 選擇環境儀表板：

   - 沙盒
   - 生產

6. 下訂單。

下單後，您可以在 _訂單網格_ 視圖：

1. 導航到 _銷售_ > _訂單_。
1. 請參閱：所有已下訂單的清單

查看 [訂單](https://docs.magento.com/user-guide/sales/orders.html) 主題：有關 _訂單網格_ 的子菜單。
