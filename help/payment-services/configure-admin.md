---
title: 舊版支付服務設定
description: 安裝後，您可以設定 [!DNL Payment Services] （在商店設定的Admin中）。
role: Admin, User
level: Intermediate
exl-id: e1a3269d-bdf9-4b0f-972f-e8a0ef469503
source-git-commit: 817a01e98876bddf5f41a253501984539b3351cd
workflow-type: tm+mt
source-wordcount: '866'
ht-degree: 0%

---

# 舊版 [!DNL Payment Services] 設定

您可以自訂 [!DNL Payment Services] 管理員中有用的設定選項，滿足您的需求。

當您設定 [!DNL Payment Services] 的 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 在Admin中，這些設定僅適用於 _[!UICONTROL Method]_欄位_[!UICONTROL General Configuration]_. 您在設定欄位中所做的任何變更都不會與切換 _[!UICONTROL Method]_選取 — 如果切換方法，您的選取不會重設。

## 一般設定

您可以啟用 [!DNL Payment Services] ，並在以下位置啟用沙箱測試或即時付款： _[!UICONTROL General Configuration]_區段。

1. 於 _管理員_ 側欄，前往 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. 在左側面板中，展開 **[!UICONTROL Sales]** 並選擇 **[!UICONTROL Payment Methods]**.

   ![方法檢視](assets/methods-view.png)

1. 展開 _[!UICONTROL Recommended Solutions]_區段。
1. 在 _[!UICONTROL [!DNL Payment Services]]_區段，展開_[!UICONTROL General Configuration]_ 區段。
1. 對象 **啟用**，將其設為 `Yes` 以啟用 [!DNL Payment Services] ，為您的商店提供。
1. 對象 **方法**，將其設為 `Sandbox` 如果您仍在測試 [!DNL Payment Services] （針對您的商店或） `Production` 如果您已準備好啟用即時付款。

   >[!WARNING]
   >
   >您的 _[!UICONTROL Sandbox Merchant ID]_和_[!UICONTROL Production Merchant ID]_ 當您完成沙箱和/或生產入門時，會自動產生並出現在他們的值得尊敬的欄位中。 請勿移除或變更這些ID。

1. 按一下 **[!UICONTROL Save Config]** 以儲存變更。
1. 導覽至 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**，然後按一下 **[!UICONTROL Flush Cache]** 以重新整理所有無效的快取。

### 設定選項

| 欄位 | 範圍 | 說明 |
|---|---|---|
| [!UICONTROL Enable] | 網站 | 啟用或停用 [!DNL Payment Services] （適用於您的網站）。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Method] | 存放區檢視 | 設定商店的方法或環境。 選項： [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | 存放區檢視 | 您的沙箱商家ID，會在沙箱上線期間自動產生。 請勿變更或變更此ID。 |
| [!UICONTROL Production Merchant ID] | 存放區檢視 | 您的生產廠商ID，會在沙箱上線時自動產生。 請勿變更或變更此ID。 |

## [!UICONTROL Credit Card Fields]

此 [!UICONTROL Credit Card Fields] 付款選項提供簡單且安全的信用卡或扣帳卡付款方式結帳。

另請參閱 [付款選項](payments-options.md#paypal-smart-buttons) 以取得詳細資訊。

### 設定信用卡欄位

1. 於 _管理員_ 側欄，前往 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. 在左側面板中，展開 **[!UICONTROL Sales]** 並選擇 **[!UICONTROL Payment Methods]**.
1. 展開 _[!UICONTROL Recommended Solutions]_區段。
1. 在 _[!UICONTROL Payment Services]_區段，展開_[!UICONTROL Credit Card Fields]_ 區段。
1. 對象 **[!UICONTROL Title]**，輸入文字（如有需要）以變更結帳期間顯示的付款方式名稱。
1. 至 [設定付款作業](production.md#set-payment-services-as-payment-method)，選取 **[!UICONTROL Authorize]** 或 **授權和擷取**.
1. 對象 **[!UICONTROL Show on checkout page]**，選擇 `Yes` 以啟用結帳頁面上的信用卡欄位。
1. 對象 **[!UICONTROL Vault Enabled]**，選擇 `Yes` 以啟用信用卡儲存庫以進行結帳。
1. 對象 **[!UICONTROL Vault Enabled in Admin]**，選擇 `Yes` 讓商家使用其儲存的信用卡建立客戶的訂單。
1. 對象 **[!UICONTROL Debug Mode]**，選擇 `Yes` 啟用偵錯模式(或 `No` 以停用)。
1. 若要啟用 **[!UICONTROL 3DS Secure authentication]** (`Off` 依預設)選擇 `Always` 或 `When required`.
1. 按一下 **[!UICONTROL Save Config]** 以儲存變更。
1. 導覽至 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**，然後按一下 **[!UICONTROL Flush Cache]** 以重新整理所有無效的快取。

#### 設定選項

| 欄位 | 範圍 | 說明 |
|---|---|---|
| [!UICONTROL Title] | 存放區檢視 | 在結帳期間，在「付款方式」檢視中，新增文字以顯示為此付款選項的標題。 選項： [!UICONTROL text field] |
| [!UICONTROL Payment Action] | 網站 | 此 [付款動作](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html) 指定付款方式的。 選項： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show on checkout page] | 網站 | 啟用或停用結帳頁面上的信用卡欄位。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled] | 存放區檢視 | 啟用或停用 [信用卡保險存放](vaulting.md). 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled in Admin] | 存放區檢視 | 啟用或停用 [在Admin中完成客戶訂單的商家](vaulting.md) 使用儲存的付款方式。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL 3DS Secure authentication] | 網站 | 啟用或停用 [3DS安全驗證](security.md#3ds). 選項： [!UICONTROL Always] / [!UICONTROL When Required] / [!UICONTROL Off] |
| [!UICONTROL Debug Mode] | 網站 | 啟用或停用偵錯模式。 選項： [!UICONTROL Yes] / [!UICONTROL No] |

## [!DNL PayPal Smart Buttons]

此 [!DNL PayPal Smart Buttons] 付款選項可為您的客戶提供簡單、快速且安全的結帳程式。

另請參閱 [付款選項](payments-options.md#paypal-smart-buttons) 以取得詳細資訊。

### 設定 [!DNL PayPal Smart Buttons]

您可以在管理員內啟用並設定PayPal智慧按鈕付款選項：

1. 於 _管理員_ 側欄，前往 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. 在左側面板中，展開 **[!UICONTROL Sales]** 並選擇 **[!UICONTROL Payment Methods]**.
1. 展開 _[!UICONTROL Recommended Solutions]_區段。
1. 在 _[!UICONTROL Payment Services]_區段，展開_[!UICONTROL PayPal Smart Buttons]_ 區段。
1. 若要變更結帳時顯示的付款方式名稱，請編輯 _[!UICONTROL Title]_欄位。
1. 至 [設定付款作業](production.md#set-payment-services-as-payment-method)，選取 **[!UICONTROL Authorize]** 或 **[!UICONTROL Authorize and Capture]**.
1. 若要停用 [先付款後傳訊](payments-options.md#pay-later-button) （如有需要），選取 `No` 的 **[!UICONTROL Display Pay Later Message]**.
1. 若要啟用偵錯模式，請選取 `Yes` 的 **[!UICONTROL Debug Mode]** (`No` 停用它)。
1. 若要儲存變更，請按一下 **[!UICONTROL Save Config]** .
1. 導覽至 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**，然後按一下 **[!UICONTROL Flush Cache]** 以重新整理所有無效的快取。

### 設定選項

| 欄位 | 範圍 | 說明 |
|---|---|---|
| [!UICONTROL Title] | 存放區檢視 | 結帳期間，在「付款方式」檢視中，新增要顯示為此付款選項標題的文字。 選項：文字欄位 |
| [!UICONTROL Payment Action] | 網站 | 此 [付款動作](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} 指定付款方式的。 選項： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Display Pay Later Message] | 網站 | 在購物車、產品頁面、迷你購物車和結帳流程中啟用或停用「稍後付款」訊息。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Venmo Enabled] | 存放區檢視 | 啟用或停用顯示付款按鈕的Venmo付款選項。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Apple Pay Enabled] | 存放區檢視 | 啟用或停用顯示付款按鈕的Apple Pay付款選項。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL PayPal Pay Later Enabled] | 存放區檢視 | 啟用或停用顯示付款按鈕的稍後付款選項外觀。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Debug Mode] | 網站 | 啟用或停用偵錯模式。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons on product detail page] | 存放區檢視 | 啟用或停用 [!DNL PayPal Smart Buttons] 在產品詳細資料頁面上。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons in mini-cart preview] | 存放區檢視 | 啟用或停用 [!DNL PayPal Smart Buttons] 在迷你購物車預覽中。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons on cart page] | 存放區檢視 | 啟用或停用 [!DNL PayPal Smart Buttons] 在購物車頁面上。 選項： [!UICONTROL Yes] / [!UICONTROL No] |

### [!DNL PayPal Smart Buttons] 樣式選項

| 欄位 | 範圍 | 說明 |
|--- |--- |--- |
| [!UICONTROL Layout] | 存放區檢視 | 定義Paypal智慧按鈕的版面樣式。 選項： [!UICONTROL Vertical] / [!UICONTROL Horizontal] |
| [!UICONTROL Color] | 存放區檢視 | 定義Paypal智慧型按鈕的色彩。 選項： [!UICONTROL Blue] / [!UICONTROL Gold] / [!UICONTROL Silver] / [!UICONTROL White] / [!UICONTROL Black] |
| [!UICONTROL Shape] | 存放區檢視 | 定義Paypal智慧型按鈕的形狀。 選項： [!UICONTROL Rectangular] / [!UICONTROL Pill] |
| [!UICONTROL Use Default Height] | 存放區檢視 | 定義PayPal智慧型按鈕是否使用預設高度。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Height] | 存放區檢視 | 定義PayPal智慧型按鈕的高度。 預設值：無 |
| [!UICONTROL Label] | 存放區檢視 | 定義出現在PayPal智慧型按鈕中的標籤。 選項： [!UICONTROL PayPal] / [!UICONTROL Checkout] / [!UICONTROL Buynow] / [!UICONTROL Pay] / [!UICONTROL Installment] |
| [!UICONTROL Tagline] | 存放區檢視 | 啟用標語。 選項： [!UICONTROL Yes] / [!UICONTROL No] |

## 清除快取

如果您變更設定， [手動排清快取](/help/payment-services/settings.md#flush-the-cache) 讓您的商店顯示最新的組態設定。

