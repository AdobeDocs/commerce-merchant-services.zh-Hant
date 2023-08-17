---
title: 設定 [!DNL Quick Checkout] 適用於Adobe Commerce的擴充功能
description: 瞭解的設定選項 [!DNL Quick Checkout] 以及如何成功上線並設定擴充功能。
exl-id: 892e04dc-17d6-45e9-b2ab-c7a0735a75bc
feature: Checkout, Services
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 1%

---

# [!DNL Quick Checkout] 設定

[!DNL Quick Checkout] 適用於Adobe Commerce和Magento Open Source的設定檢視可提供設定擴充功能所需的所有資訊。

若要存取這些組態設定：

1. 在 _管理員_ 側欄，前往 **商店** > _設定_ > **設定**.
1. 在左側面板中，展開 **銷售** 並選取 **簽出**.

   ![快速簽出](assets/config-new-logo-view.png)

請參閱 [入門](../quick-checkout/onboarding.md) 主題，以取得如何設定 [!DNL Quick Checkout] 適用於Adobe Commerce。

## 啟用擴充功能

![快速簽出](assets/enable-method.png)

| 欄位 | 範圍 | 說明 |
|---|---|---|
| [!UICONTROL Enable] | 網站 | 啟用或停用 [!DNL Quick Checkout] 您的網站。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Method] | 網站 | 為您的設定方法或環境 [!DNL Quick Checkout]. 選項： [!UICONTROL Sandbox] / [!UICONTROL Production] |

{style="table-layout:auto"}

## 帳戶認證

![快速簽出](assets/account-creds.png)

| 欄位 | 範圍 | 說明 |
|---|---|---|
| [!UICONTROL API key] | 網站 | 後端用來與互動的私密金鑰 [!DNL Bolt] API。 |
| [!UICONTROL Publishable key] | 網站 | 您前端用來與互動的金鑰 [!DNL Bolt] API。 |
| [!UICONTROL Signing secret] | 網站 | 用於對從收到的請求進行簽名驗證 [!DNL Bolt]. |

{style="table-layout:auto"}

## 服務設定

![快速簽出](assets/service-settings.png)

| 欄位 | 範圍 | 說明 |
|---|---|---|
| [!UICONTROL Title] | 存放區檢視 | 在結帳期間，在「付款方式」檢視中，新增文字以顯示為此付款選項的標題。 選項： [!UICONTROL text field] |
| [!UICONTROL Payment Action] | 網站 | 此 [付款動作](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} 指定付款方式的。 選項： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Debug Mode] | 網站 | 啟用或停用偵錯模式。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Enable checkout tracking] | 網站 | 定義Adobe Commerce是否允許與Bolt共用的簽出追蹤資訊。 預設為啟用。 如果停用，報告將受到影響。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Next Stage After Login Mode] | 網站 | 在客戶登入後變更導覽流程。 選項： [!UICONTROL Payment] / [!UICONTROL Shipping] |
| [!UICONTROL Automatic Login Enabled] | 網站 | 定義條件 [!DNL Quick Checkout] 允許在結帳期間自動登入。 預設為啟用。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Automatic Login Network] | 網站 | 選取客戶自動登入的網路。 預設為啟用Bolt。 選項： [!UICONTROL Bolt + Merchant] / [!UICONTROL Bolt] |

{style="table-layout:auto"}
