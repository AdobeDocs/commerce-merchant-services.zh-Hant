---
title: 配置 [!DNL Quick Checkout] Adobe Commerce分機
description: 瞭解 [!DNL Quick Checkout] 以及如何成功安裝並設定擴展。
exl-id: 892e04dc-17d6-45e9-b2ab-c7a0735a75bc
source-git-commit: f790732804e110aad298689c0ddf74547ff17618
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# [!DNL Quick Checkout] 設定

[!DNL Quick Checkout] 對於Adobe Commerce和Magento Open Source，提供配置視圖，其中包含設定擴展所需的所有資訊。

要訪問這些配置設定：

1. 在 _管理_ 邊欄，轉到 **商店** > _設定_ > **配置**。
1. 在左面板中，展開 **銷售** 選擇 **簽出**。

   ![快速簽出](assets/config-new-logo-view.png)

請參閱 [登機](../quick-checkout/onboarding.md) 有關如何配置的詳細資訊，請參閱主題 [!DNL Quick Checkout] Adobe Commerce。

## 啟用擴展

![快速簽出](assets/enable-method.png)

| 欄位 | 範圍 | 說明 |
|---|---|---|
| [!UICONTROL Enable] | 網站 | 啟用或禁用 [!DNL Quick Checkout] 的子菜單。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Method] | 網站 | 設定方法或環境 [!DNL Quick Checkout]。 選項： [!UICONTROL Sandbox] / [!UICONTROL Production] |

{style="table-layout:auto"}

## 帳戶憑據

![快速簽出](assets/account-creds.png)

| 欄位 | 範圍 | 說明 |
|---|---|---|
| [!UICONTROL API key] | 網站 | 後端用於與交互的私鑰 [!DNL Bolt] API。 |
| [!UICONTROL Publishable key] | 網站 | 前端用於與交互的密鑰 [!DNL Bolt] API。 |
| [!UICONTROL Signing secret] | 網站 | 用於對從接收的請求進行簽名驗證 [!DNL Bolt]。 |

{style="table-layout:auto"}

## 服務設定

![快速簽出](assets/service-settings.png)

| 欄位 | 範圍 | 說明 |
|---|---|---|
| [!UICONTROL Title] | 商店視圖 | 在結帳期間，在「付款方法」視圖中將要顯示的文本添加為此付款選項的標題。 選項： [!UICONTROL text field] |
| [!UICONTROL Payment Action] | 網站 | 的 [付款操作](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} 指定的付款方式。 選項： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Debug Mode] | 網站 | 啟用或禁用調試模式。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Enable checkout tracking] | 網站 | 定義Adobe Commerce是否允許與Bolt共用簽出跟蹤資訊。 預設啟用。 如果禁用，則報告將受到影響。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Next Stage After Login Mode] | 網站 | 在客戶登錄後更改導航流。 選項： [!UICONTROL Payment] / [!UICONTROL Shipping] |
| [!UICONTROL Automatic Login Enabled] | 網站 | 定義 [!DNL Quick Checkout] 允許在簽出期間自動登錄。 預設啟用。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Automatic Login Network] | 網站 | 選擇客戶自動登錄的網路。 預設情況下啟用Bolt。 選項： [!UICONTROL Bolt + Merchant] / [!UICONTROL Bolt] |

{style="table-layout:auto"}
