---
title: 舊式付款服務配置
description: 安裝後，您可以配置 [!DNL Payment Services] 在儲存配置的管理中。
role: Admin, User
level: Intermediate
exl-id: e1a3269d-bdf9-4b0f-972f-e8a0ef469503
source-git-commit: 6f13c39f915c382e99c747d9a88e16ed10bebaf3
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 0%

---

# 舊式付款服務配置

您可以自定義 [!DNL Payment Services] 使用管理中的有用配置選項滿足您的需要。

配置時 [!DNL Payment Services] 為 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 在Admin中，這些配置僅適用於在 _[!UICONTROL Method]_欄位_[!UICONTROL General Configuration]_。 在配置欄位中所做的任何更改都與切換 _[!UICONTROL Method]_選擇 — 如果切換方法，則不會重置選擇。

查看 [[!UICONTROL General Configuration] 節](#general-configuration) 的子菜單。

## 常規配置

您可以啟用 [!DNL Payment Services] 為您的商店啟用沙盒測試或即時付款 _[!UICONTROL General Configuration]_的子菜單。

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**。
1. 在左面板中，展開 **[!UICONTROL Sales]** 選擇 **[!UICONTROL Payment Methods]**。

   ![方法視圖](assets/methods-view.png)

1. 展開 _[!UICONTROL Recommended Solutions]_的子菜單。
1. 在 _[!UICONTROL [!DNL Payment Services]]_的_[!UICONTROL General Configuration]_ 的子菜單。
1. 對於 **啟用**，將其設定為 `Yes` 啟用 [!DNL Payment Services] 給你的店。
1. 對於 **方法**，將其設定為 `Sandbox` 如果你還在測試 [!DNL Payment Services] 你的商店 `Production` 如果您已準備好啟用即時付款。

   >[!WARNING]
   >
   >您 _[!UICONTROL Sandbox Merchant ID]_和_[!UICONTROL Production Merchant ID]_ 在您完成沙箱和/或生產後，自動生成並呈現在他們受人尊重的領域。 不要刪除或更改這些ID。

1. 按一下 **[!UICONTROL Save Config]** 的子菜單。

### 配置選項

| 欄位 | 範圍 | 說明 |
|---|---|---|
| [!UICONTROL Enable] | 網站 | 啟用或禁用 [!DNL Payment Services] 的子菜單。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Method] | 商店視圖 | 設定儲存的方法或環境。 選項： [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | 商店視圖 | 您的沙盒商戶ID，在沙盒登機過程中自動生成。 不要更改或更改此ID。 |
| [!UICONTROL Production Merchant ID] | 商店視圖 | 您的生產商ID，它在裝箱過程中自動生成。 不要更改或更改此ID。 |

## [!UICONTROL Credit Card Fields]

的 [!UICONTROL Credit Card Fields] 付款選項為信用卡或借記卡付款方法提供簡單而安全的結帳。

請參閱 [付款選項](payments-options.md#paypal-smart-buttons) 的子菜單。

### 配置信用卡欄位

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**。
1. 在左面板中，展開 **[!UICONTROL Sales]** 選擇 **[!UICONTROL Payment Methods]**。
1. 展開 _[!UICONTROL Recommended Solutions]_的子菜單。
1. 在 _[!UICONTROL Payment Services]_的_[!UICONTROL Credit Card Fields]_ 的子菜單。
1. 對於 **[!UICONTROL Title]**，輸入文本（如果需要）以更改付款方法的名稱，如結帳期間所示。
1. 至 [設定付款活動](production.md#set-payment-services-as-payment-method)選中 **[!UICONTROL Authorize]** 或 **授權和捕獲**。
1. 對於 **調試模式**&#x200B;選項 `Yes` 啟用調試模式(或 `No` 禁用)。
1. 按一下 **[!UICONTROL Save Config]** 的子菜單。

#### 配置選項

| 欄位 | 範圍 | 說明 |
|---|---|---|
| [!UICONTROL Title] | 商店視圖 | 在結帳期間，在「付款方法」視圖中將要顯示的文本添加為此付款選項的標題。 選項： [!UICONTROL text field] |
| [!UICONTROL Payment Action] | 網站 | 的 [付款操作](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;}，用於指定的付款方法。 選項： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Debug Mode] | 網站 | 啟用或禁用調試模式。 選項： [!UICONTROL Yes] / [!UICONTROL No] |

## [!DNL PayPal Smart Buttons]

的 [!DNL PayPal Smart Buttons] 付款選項可為客戶提供簡單、快速和安全的結帳流程。

請參閱 [付款選項](payments-options.md#paypal-smart-buttons) 的子菜單。

### 配置 [!DNL PayPal Smart Buttons]

您可以在管理員中啟用和配置PayPal智慧按鈕付款選項：

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**。
1. 在左面板中，展開 **[!UICONTROL Sales]** 選擇 **[!UICONTROL Payment Methods]**。
1. 展開 _[!UICONTROL Recommended Solutions]_的子菜單。
1. 在 _[!UICONTROL Payment Services]_的_[!UICONTROL PayPal Smart Buttons]_ 的子菜單。
1. 要更改在結帳期間顯示的付款方法的名稱，請編輯 _[!UICONTROL Title]_的子菜單。
1. 至 [設定付款活動](production.md#set-payment-services-as-payment-method)選中 **[!UICONTROL Authorize]** 或 **[!UICONTROL Authorize and Capture]**。
1. 禁用 [稍後付費消息](payments-options.md#pay-later-button) （如果需要），選擇 `No` 為 **[!UICONTROL Display Pay Later Message]**。
1. 要啟用調試模式，請選擇 `Yes` 為 **[!UICONTROL Debug Mode]** (`No` 禁用)。
1. 要保存更改，請按一下 **[!UICONTROL Save Config]** 。

### 配置選項

| 欄位 | 範圍 | 說明 |
|---|---|---|
| [!UICONTROL Title] | 商店視圖 | 在結帳期間，在「付款方法」視圖中將要顯示為此付款選項標題的文本添加。 選項：文本欄位 |
| [!UICONTROL Payment Action] | 網站 | 的 [付款操作](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;}，用於指定的付款方法。 選項： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Display Pay Later Message] | 網站 | 在購物車、產品頁面、迷你購物車和結帳流程中啟用或禁用「稍後付款」消息。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Venmo Enabled] | 商店視圖 | 啟用或禁用顯示付款按鈕的「供應商」付款選項。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Apple Pay Enabled] | 商店視圖 | 啟用或禁用顯示付款按鈕的Apple支付付款選項。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL PayPal Pay Later Enabled] | 商店視圖 | 啟用或禁用顯示付款按鈕的支付後付款選項外觀。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Debug Mode] | 網站 | 啟用或禁用調試模式。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons on product detail page] | 商店視圖 | 啟用或禁用 [!DNL PayPal Smart Buttons] 產品詳細資訊頁面。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons in mini cart preview] | 商店視圖 | 啟用或禁用 [!DNL PayPal Smart Buttons] 打印。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons on cart page] | 商店視圖 | 啟用或禁用 [!DNL PayPal Smart Buttons] 的子菜單。 選項： [!UICONTROL Yes] / [!UICONTROL No] |

### [!DNL PayPal Smart Buttons] 樣式選項

| 欄位 | 範圍 | 說明 |
|--- |--- |--- |
| [!UICONTROL Layout] | 儲存視圖 | 定義Paypal智慧按鈕的佈局樣式。 選項： [!UICONTROL Vertical] / [!UICONTROL Horizontal] |
| [!UICONTROL Color] | 儲存視圖 | 定義Paypal智慧按鈕的顏色。 選項： [!UICONTROL Blue] / [!UICONTROL Gold] / [!UICONTROL Silver] / [!UICONTROL White] / [!UICONTROL Black] |
| [!UICONTROL Shape] | 儲存視圖 | 定義Paypal智慧按鈕的形狀。 選項： [!UICONTROL Rectangular] / [!UICONTROL Pill] |
| [!UICONTROL Use Default Height] | 儲存視圖 | 定義PayPal智慧按鈕是否使用預設高度。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Height] | 儲存視圖 | 定義PayPal智慧按鈕的高度。 預設值：無 |
| [!UICONTROL Label] | 儲存視圖 | 定義顯示在PayPal智慧按鈕中的標籤。 選項： [!UICONTROL PayPal] / [!UICONTROL Checkout] / [!UICONTROL Buynow] / [!UICONTROL Pay] / [!UICONTROL Installment] |
| [!UICONTROL Tagline] | 儲存視圖 | 啟用標籤。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
