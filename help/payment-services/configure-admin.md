---
title: 舊式支付服務配置
description: 安裝後，您可以設定 [!DNL Payment Services] 在存放區設定的「管理員」中。
role: Admin, User
level: Intermediate
exl-id: e1a3269d-bdf9-4b0f-972f-e8a0ef469503
source-git-commit: 2e9a611cf94bb83733c9cad1e04f4244f62d4272
workflow-type: tm+mt
source-wordcount: '780'
ht-degree: 0%

---

# 舊式支付服務配置

您可以自訂 [!DNL Payment Services] 管理中實用的設定選項，以符合您的需求。

設定時 [!DNL Payment Services] for [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 在「管理員」中，這些設定只會套用至 _[!UICONTROL Method]_欄位_[!UICONTROL General Configuration]_. 您在設定欄位中所做的任何變更，都與切換 _[!UICONTROL Method]_選擇(selection) — 如果切換方法，則選擇不會重置。

## 一般配置

您可以啟用 [!DNL Payment Services] ，並啟用沙箱測試或即時付款 _[!UICONTROL General Configuration]_區段。

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. 在左側面板中，展開 **[!UICONTROL Sales]** 選擇 **[!UICONTROL Payment Methods]**.

   ![方法檢視](assets/methods-view.png)

1. 展開 _[!UICONTROL Recommended Solutions]_區段。
1. 在 _[!UICONTROL [!DNL Payment Services]]_部分，展開_[!UICONTROL General Configuration]_ 區段。
1. 針對 **啟用**，請將設為 `Yes` 啟用 [!DNL Payment Services] 為您的商店。
1. 針對 **方法**，請將設為 `Sandbox` 如果您仍在測試 [!DNL Payment Services] 或 `Production` 如果您已準備好啟用即時付款。

   >[!WARNING]
   >
   >您的 _[!UICONTROL Sandbox Merchant ID]_和_[!UICONTROL Production Merchant ID]_ 會在您完成沙箱和/或生產的上線作業後，自動產生並呈現在其可敬的領域中。 請勿移除或變更這些ID。

1. 按一下 **[!UICONTROL Save Config]** 來儲存變更。
1. 導覽至 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**，然後按一下 **[!UICONTROL Flush Cache]** 刷新所有無效快取。

### 配置選項

| 欄位 | 範圍 | 說明 |
|---|---|---|
| [!UICONTROL Enable] | 網站 | 啟用或禁用 [!DNL Payment Services] 的URL。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Method] | 商店檢視 | 設定商店的方法或環境。 選項： [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | 商店檢視 | 您的沙箱商戶ID，會在沙箱上線期間自動產生。 請勿變更或更改此ID。 |
| [!UICONTROL Production Merchant ID] | 商店檢視 | 您的生產商ID，會在沙箱上線期間自動產生。 請勿變更或更改此ID。 |

## [!UICONTROL Credit Card Fields]

此 [!UICONTROL Credit Card Fields] 付款選項為信用卡或借記卡付款方法提供簡單而安全的結帳。

請參閱 [付款選項](payments-options.md#paypal-smart-buttons) 以取得更多資訊。

### 配置信用卡欄位

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. 在左側面板中，展開 **[!UICONTROL Sales]** 選擇 **[!UICONTROL Payment Methods]**.
1. 展開 _[!UICONTROL Recommended Solutions]_區段。
1. 在 _[!UICONTROL Payment Services]_部分，展開_[!UICONTROL Credit Card Fields]_ 區段。
1. 針對 **[!UICONTROL Title]**，輸入文本（如果需要）以更改付款方法的名稱，如結帳期間所示。
1. 結束日期 [設定付款活動](production.md#set-payment-services-as-payment-method)，選取 **[!UICONTROL Authorize]** 或 **授權和捕獲**.
1. 針對 **除錯模式**，選擇 `Yes` 啟用偵錯模式(或 `No` 停用)。
1. 按一下 **[!UICONTROL Save Config]** 來儲存變更。
1. 導覽至 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**，然後按一下 **[!UICONTROL Flush Cache]** 刷新所有無效快取。

#### 配置選項

| 欄位 | 範圍 | 說明 |
|---|---|---|
| [!UICONTROL Title] | 商店檢視 | 在結帳期間，在「付款方法」視圖中添加要顯示為此付款選項標題的文本。 選項： [!UICONTROL text field] |
| [!UICONTROL Payment Action] | 網站 | 此 [付款動作](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;}，適用於指定的付款方法。 選項： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Debug Mode] | 網站 | 啟用或停用除錯模式。 選項： [!UICONTROL Yes] / [!UICONTROL No] |

## [!DNL PayPal Smart Buttons]

此 [!DNL PayPal Smart Buttons] 付款選項可為您的客戶提供簡單、快速且安全的結帳程式。

請參閱 [付款選項](payments-options.md#paypal-smart-buttons) 以取得更多資訊。

### 設定 [!DNL PayPal Smart Buttons]

您可以在管理員中啟用和配置PayPal智慧按鈕付款選項：

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. 在左側面板中，展開 **[!UICONTROL Sales]** 選擇 **[!UICONTROL Payment Methods]**.
1. 展開 _[!UICONTROL Recommended Solutions]_區段。
1. 在 _[!UICONTROL Payment Services]_部分，展開_[!UICONTROL PayPal Smart Buttons]_ 區段。
1. 要更改付款方法的名稱，如結帳期間所示，請編輯 _[!UICONTROL Title]_欄位。
1. 結束日期 [設定付款活動](production.md#set-payment-services-as-payment-method)，選取 **[!UICONTROL Authorize]** 或 **[!UICONTROL Authorize and Capture]**.
1. 若要停用 [稍後付費訊息](payments-options.md#pay-later-button) （如果需要），請選取 `No` for **[!UICONTROL Display Pay Later Message]**.
1. 若要啟用偵錯模式，請選取 `Yes` 針對 **[!UICONTROL Debug Mode]** (`No` 停用)。
1. 若要儲存變更，請按一下 **[!UICONTROL Save Config]** .
1. 導覽至 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**，然後按一下 **[!UICONTROL Flush Cache]** 刷新所有無效快取。

### 配置選項

| 欄位 | 範圍 | 說明 |
|---|---|---|
| [!UICONTROL Title] | 商店檢視 | 在結帳期間，在「付款方法」視圖中添加要顯示為此付款選項標題的文本。 選項：文字欄位 |
| [!UICONTROL Payment Action] | 網站 | 此 [付款動作](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;}，適用於指定的付款方法。 選項： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Display Pay Later Message] | 網站 | 在購物車、產品頁面、迷你購物車和結帳流程期間，啟用或停用「稍後付費」訊息。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Venmo Enabled] | 商店檢視 | 啟用或禁用顯示付款按鈕的Venmo付款選項。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Apple Pay Enabled] | 商店檢視 | 啟用或禁用顯示付款按鈕的Apple支付付款選項。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL PayPal Pay Later Enabled] | 商店檢視 | 啟用或禁用顯示付款按鈕的稍後付款選項外觀。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Debug Mode] | 網站 | 啟用或停用除錯模式。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons on product detail page] | 商店檢視 | 啟用或禁用 [!DNL PayPal Smart Buttons] 在產品詳細資料頁面上。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons in mini-cart preview] | 商店檢視 | 啟用或禁用 [!DNL PayPal Smart Buttons] 在迷你購物車預覽中。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons on cart page] | 商店檢視 | 啟用或禁用 [!DNL PayPal Smart Buttons] 在購物車頁面上。 選項： [!UICONTROL Yes] / [!UICONTROL No] |

### [!DNL PayPal Smart Buttons] 樣式選項

| 欄位 | 範圍 | 說明 |
|--- |--- |--- |
| [!UICONTROL Layout] | 商店檢視 | 定義Paypal智慧按鈕的佈局樣式。 選項： [!UICONTROL Vertical] / [!UICONTROL Horizontal] |
| [!UICONTROL Color] | 商店檢視 | 定義Paypal智慧按鈕的顏色。 選項： [!UICONTROL Blue] / [!UICONTROL Gold] / [!UICONTROL Silver] / [!UICONTROL White] / [!UICONTROL Black] |
| [!UICONTROL Shape] | 商店檢視 | 定義Paypal智慧按鈕的形狀。 選項： [!UICONTROL Rectangular] / [!UICONTROL Pill] |
| [!UICONTROL Use Default Height] | 商店檢視 | 定義PayPal智慧按鈕是否使用預設高度。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Height] | 商店檢視 | 定義PayPal智慧按鈕的高度。 預設值：無 |
| [!UICONTROL Label] | 商店檢視 | 定義顯示在PayPal智慧按鈕中的標籤。 選項： [!UICONTROL PayPal] / [!UICONTROL Checkout] / [!UICONTROL Buynow] / [!UICONTROL Pay] / [!UICONTROL Installment] |
| [!UICONTROL Tagline] | 商店檢視 | 啟用標籤。 選項： [!UICONTROL Yes] / [!UICONTROL No] |

## 刷新快取

如果您變更設定， [手動刷新快取](/help/payment-services/settings.md#flush-the-cache) 讓您的商店顯示最新的組態設定。
