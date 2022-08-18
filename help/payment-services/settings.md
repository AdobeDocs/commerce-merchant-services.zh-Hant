---
title: 付款服務設定
description: 安裝後，您可以配置 [!DNL Payment Services] 的下一頁。
role: Admin, User
level: Intermediate
exl-id: 108f2b24-39c1-4c87-8deb-d82ee1c24d55
source-git-commit: ecfe1448a0272fe5401090b322f4b69dffd1a8fa
workflow-type: tm+mt
source-wordcount: '1087'
ht-degree: 0%

---

# 設定

您可以自定義 [!DNL Payment Services] 以及 [!DNL Payment Services] 回家。

配置 [!DNL Payment Services] 為 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 按一下 **[!UICONTROL Settings]**。 這些配置選項僅適用於在 _[!UICONTROL Payment mode]_欄位_[!UICONTROL Settings]_ > _[!UICONTROL General]_。

>[!IMPORTANT]
>
> 有關多儲存或舊式配置，請參閱 [在管理員中配置](configure-admin.md) 主題。

## 啟用付款服務

您可以啟用 [!DNL Payment Services] 為您的網站啟用沙盒測試或即時付款 [!UICONTROL General] 的子菜單。

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**。

   ![首頁視圖](assets/payment-services-menu-small.png)

1. 按一下 **[!UICONTROL Settings]**. 請參閱 [簡介 [!DNL Payment Services] 首頁](payments-home.md) 的子菜單。

   的 _[!UICONTROL General]_部分包括用於啟用的設定 [!DNL Payment Services] 付款方式。

1. 啟用 [!DNL Payment Services] 作為您商店的付款方式，在 _[!UICONTROL General]_節，切換(**[!UICONTROL Enable Payment Services as payment method]**) `Yes`。

1. 如果你還在測試 [!DNL Payment Services] 為你的商店，設定 **付款模式** 至 `Sandbox`。 如果準備啟用即時付款，請將其設定為 `Production`。

   >[!NOTE]
   >
   >您 _[!UICONTROL Sandbox Merchant ID]_和_[!UICONTROL Production Merchant ID]_ 在您完成沙箱和/或生產後，自動生成並呈現在他們受人尊敬的領域中。

1. 按一下 **[!UICONTROL Save]**.

   如果嘗試在不保存更改的情況下從此視圖中導航，則會出現一個模式，提示您放棄更改、繼續編輯或保存更改。

1. 導航到 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 按一下 **[!UICONTROL Flush Cache]** 刷新所有無效的快取。

現在，您可以繼續更改 [付款選項](#configure-payment-options) 功能和店面顯示。

### 常規配置選項

| 欄位 | 範圍 | 說明 |
|---|---|---|
| [!UICONTROL Enable] | 網站 | 啟用或禁用 [!DNL Payment Services] 的子菜單。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Payment mode] | 商店視圖 | 設定儲存的方法或環境。 選項： [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | 商店視圖 | 您的沙盒商戶ID，在沙盒登機過程中自動生成。 |
| [!UICONTROL Production Merchant ID] | 商店視圖 | 您的生產商ID，它在裝箱過程中自動生成。 |

## 配置付款選項

現在，您已為網站啟用了Payment Services，您可以更改付款功能和店面顯示的預設設定。

### 信用卡欄位

的 _[!UICONTROL Credit Card Fields]_設定為信用卡或借記卡付款方法提供簡單且安全的結帳選項。

請參閱 [付款選項](payments-options.md#credit-card-fields) 的子菜單。

1. 在 **[!UICONTROL Scope]** 下拉菜單，您要為其啟用付款方法。
1. 要更改在結帳期間顯示的付款方法的名稱，請在 **[!UICONTROL Checkout title]** 的子菜單。
1. 至 [設定付款活動](production.md#set-payment-services-as-payment-method)切換 **[!UICONTROL Payment action]** 至 `Authorize` 或 `Authorize and Capture`。
1. 要啟用調試模式，請切換 **[!UICONTROL Debug Mode]** 選擇器。
1. 按一下 **[!UICONTROL Save]**.

   如果嘗試在不保存更改的情況下從此視圖中導航，則會出現一個模式，提示您放棄更改、繼續編輯或保存更改。

1. 導航到 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 按一下 **[!UICONTROL Flush Cache]** 刷新所有無效的快取。

#### 配置選項

| 欄位 | 範圍 | 說明 |
|---|---|---|
| [!UICONTROL Title] | 商店視圖 | 在結帳期間，在「付款方法」視圖中將要顯示的文本添加為此付款選項的標題。 選項： [!UICONTROL text field] |
| [!UICONTROL Payment Action] | 網站 | 的 [付款操作](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;}，用於指定的付款方法。 選項： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Debug Mode] | 網站 | 啟用或禁用調試模式。 選項： [!UICONTROL Yes] / [!UICONTROL No] |

### 付款按鈕

的 [!DNL PayPal Smart Buttons] 付款選項可為客戶提供簡單、快速和安全的結帳流程。 請參閱 [付款選項](payments-options.md#paypal-smart-buttons) 的子菜單。

您可以啟用和配置PayPal智慧按鈕付款選項：

1. 在 **[!UICONTROL Scope]** 下拉菜單，您要為其啟用付款方法。
1. 要更改在結帳期間顯示的付款方法的名稱，請在 **[!UICONTROL Checkout Title]** 的子菜單。
1. 至 [設定付款活動](production.md#set-payment-services-as-payment-method)切換 **[!UICONTROL Payment action]** 至 `Authorize` 或 `Authorize and Capture`。
1. 使用切換選擇器啟用或禁用 [!DNL PayPal smart button] 顯示功能：
   - **[!UICONTROL Show PayPal buttons on product detail page]**
   - **[!UICONTROL Show PayPal buttons in mini cart preview]**
   - **[!UICONTROL Show PayPal buttons on cart page]**
   - **[!UICONTROL Show PayPal Pay Later button]**
   - **[!UICONTROL Show PayPal Pay Later message]**
   - **[!UICONTROL Show Venmo button]**
   - **[!UICONTROL Show Apple Pay button]**

      >[!NOTE]
      >
      > 用Apple付你錢 [必須有Apple開發員帳戶](test-validate.md#test-in-sandbox-environment) （包括假信用卡和帳單資訊）以test它。 準備好在沙盒中使用Apple支付時 *或* 生產模式，完成任何 [測試和驗證](test-validate.md)，請聯繫您的銷售代表，以便為您的即時商店啟用它。

      當您開啟/關閉付款按鈕或PayPal Pay Later消息的可見性時，該配置的可視預覽將顯示在「設定」頁的底部。

1. 要啟用調試模式，請切換 **[!UICONTROL Debug Mode]** 選擇器。
1. 按一下 **[!UICONTROL Save]**.

   如果嘗試在不保存更改的情況下從此視圖中導航，則會出現一個模式，提示您放棄更改、繼續編輯或保存更改。

1. 導航到 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 按一下 **[!UICONTROL Flush Cache]** 刷新所有無效的快取。

#### 配置選項

| 欄位 | 範圍 | 說明 |
|---|---|---|
| [!UICONTROL Title] | 商店視圖 | 在結帳期間，在「付款方法」視圖中將要顯示為此付款選項標題的文本添加。 選項：文本欄位 |
| [!UICONTROL Payment Action] | 網站 | 的 [付款操作](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;}，用於指定的付款方法。 選項： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show PayPal buttons on product detail page] | 商店視圖 | 啟用或禁用 [!DNL PayPal Smart Buttons] 產品詳細資訊頁面。 選項： [!UICONTROL  Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons in mini cart preview] | 商店視圖 | 啟用或禁用 [!DNL PayPal Smart Buttons] 的子菜單。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons on cart page] | 商店視圖 | 啟用或禁用 [!DNL PayPal Smart Buttons] 的子菜單。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal Pay Later button] | 商店視圖 | 啟用或禁用顯示付款按鈕的支付後付款選項外觀。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal Pay Later Message] | 網站 | 在購物車、產品頁面、迷你購物車和結帳流程中啟用或禁用「稍後付款」消息。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show Venmo button] | 商店視圖 | 啟用或禁用顯示付款按鈕的「供應商」付款選項。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show Apple Pay button] | 商店視圖 | 啟用或禁用顯示付款按鈕的Apple支付付款選項。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Debug Mode] | 網站 | 啟用或禁用調試模式。 選項： [!UICONTROL Yes] / [!UICONTROL No] |

### 按鈕樣式

您還可以配置 _[!UICONTROL Button style]_PayPal智慧按鈕的選項：

1. 更改 **[!UICONTROL Layout]**&#x200B;選中 `Vertical` 或 `Horizontal`。

   >[!NOTE]
   >
   > 如果按鈕樣式配置為 `Horizontal` 您的商店配置為顯示多個PayPal智慧按鈕，您只能看到產品頁、結帳頁和迷你購物車上顯示的兩個按鈕，以及購物車中顯示的一個按鈕。

1. 要在水準佈局中啟用標籤線，請切換 **[!UICONTROL Show tagline]** 選擇器。
1. 修改 **[!UICONTROL Color]**，則選擇所需的顏色選項。
1. 修改 **[!UICONTROL Shape]**&#x200B;選中 `Pill` 或 `Rect`。
1. 要啟用按鈕高度選擇器，請切換 **[!UICONTROL Responsive button height]** 選擇器。
1. 修改 **[!UICONTROL Label]**，選擇所需的標籤選項。

   當您更改佈局、顏色、形狀、高度和標籤的配置選項時，該配置的可視預覽會顯示在「設定」頁的底部。

1. 按一下 **[!UICONTROL Save]**.

   如果嘗試在不保存更改的情況下從此視圖中導航，則會出現一個模式，提示您放棄更改、繼續編輯或保存更改。

1. 導航到 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 按一下 **[!UICONTROL Flush Cache]** 刷新所有無效的快取。

您可以配置 [!DNL PayPal Smart Buttons] 造型 [管理中的舊式配置](configure-admin.md#configure-paypal-smart-buttons) 或者這裡 [!DNL Payment Services Home]。 請參閱 [PayPal的按鈕樣式指南](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) 的雙曲餘切值。

#### 配置選項

| 欄位 | 範圍 | 說明 |
|--- |--- |--- |
| [!UICONTROL Layout] | 儲存視圖 | 定義付款按鈕的佈局樣式。 選項： [!UICONTROL Vertical] / [!UICONTROL Horizontal] |
| [!UICONTROL Tagline] | 儲存視圖 | 啟用/禁用標語。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Color] | 儲存視圖 | 定義付款按鈕的顏色。 選項： [!UICONTROL Blue] / [!UICONTROL Gold] / [!UICONTROL Silver] / [!UICONTROL White] / [!UICONTROL Black] |
| [!UICONTROL Shape] | 儲存視圖 | 定義付款按鈕的形狀。 選項： [!UICONTROL Rectangular] / [!UICONTROL Pill] |
| [!UICONTROL Responsive Button Height] | 儲存視圖 | 定義付款按鈕是否使用預設高度。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Height] | 儲存視圖 | 定義付款按鈕的高度。 預設值：無 |
| [!UICONTROL Label] | 儲存視圖 | 定義顯示在付款按鈕中的標籤。 選項： [!UICONTROL PayPal] / [!UICONTROL Checkout] / [!UICONTROL Buynow] / [!UICONTROL Pay] / [!UICONTROL Installment] |
