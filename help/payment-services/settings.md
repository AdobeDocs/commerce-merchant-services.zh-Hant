---
title: 付款服務設定
description: 安裝後，您可以配置 [!DNL Payment Services] 的下一頁。
role: Admin, User
level: Intermediate
exl-id: 108f2b24-39c1-4c87-8deb-d82ee1c24d55
source-git-commit: f14b4a1abe9c0f85dc9f070467f94819c1fe89e6
workflow-type: tm+mt
source-wordcount: '1909'
ht-degree: 0%

---

# 設定

您可以自定義 [!DNL Payment Services] 以及 [!DNL Payment Services] 回家。

配置 [!DNL Payment Services] 為 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 按一下 **[!UICONTROL Settings]**。 這些配置選項僅適用於在 _[!UICONTROL Payment mode]_的[_&#x200B;常規&#x200B;_配置選項](#configure-general-settings)。

有關多儲存或舊式配置，請參見 [在管理員中配置](configure-admin.md)。

## 配置常規設定

的 [!UICONTROL General] 設定提供了啟用或禁用付款服務作為付款方法的功能，以及向客戶交易記錄添加資訊以用自定義資訊標籤或為網站或商店視圖添加前置詞。

### 啟用付款服務

您可以啟用 [!DNL Payment Services] 為您的網站啟用沙盒測試或即時支付。

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**。

   ![首頁視圖](assets/payment-services-menu-small.png)

1. 按一下 **[!UICONTROL Settings]**。 請參閱 [簡介 [!DNL Payment Services] 首頁](payments-home.md) 的子菜單。

   的 _[!UICONTROL General]_部分包括用於啟用的設定 [!DNL Payment Services] 付款方式。

1. 啟用 [!DNL Payment Services] 作為您商店的付款方式，在 _[!UICONTROL General]_節，切換&#x200B;**[!UICONTROL Enable Payment Services as payment method]**至 `Yes`。

1. 如果你還在測試 [!DNL Payment Services] 為你的商店，設定 **付款模式** 至 `Sandbox`。 如果準備啟用即時付款，請將其設定為 `Production`。

   >[!NOTE]
   >
   >您 _[!UICONTROL Sandbox Merchant ID]_和_[!UICONTROL Production Merchant ID]_ 在您完成沙箱和/或生產後，自動生成並呈現在他們受人尊敬的領域中。

1. 按一下 **[!UICONTROL Save]**。

   如果嘗試在不保存更改的情況下從此視圖中導航，則會出現一個模式，提示您放棄更改、繼續編輯或保存更改。

1. 導航到 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 按一下 **[!UICONTROL Flush Cache]** 刷新所有無效的快取。

現在，您可以繼續更改 [付款選項](#configure-payment-options) 功能和店面顯示。

### 添加軟描述符

可以添加 [!UICONTROL Soft Descriptor] 到您的網站或單個儲存視圖配置。 軟描述符顯示在客戶交易記錄銀行對帳單上。 例如，如果您有多個商店/品牌/目錄，則可以通過向 [!UICONTROL Soft Descriptor] 的子菜單。

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**。

   ![首頁視圖](assets/payment-services-menu-small.png)

1. 按一下 **[!UICONTROL Settings]**。 請參閱 [簡介 [!DNL Payment Services] 首頁](payments-home.md) 的子菜單。
1. 選擇網站或商店視圖，位於 **[!UICONTROL Scope]** 下拉菜單，您要為其建立軟描述符。 對於初始設定，將此設定保留為 **[!UICONTROL Default]** 的子菜單。
1. 在文本欄位中添加自定義文本（最多22個字元），替換 `Custom descriptor`。
1. 按一下 **[!UICONTROL Save]**。
1. 要為網站或儲存視圖建立除已配置預設值之外的軟描述符，請執行以下操作：
   1. 選擇網站或商店視圖，位於 **[!UICONTROL Scope]** 下拉菜單，您要為其建立軟描述符。
   1. 切換 _關_ **[!UICONTROL Use website]** 或 **[!UICONTROL Use default]**，取決於您選擇的範圍)。
   1. 在文本欄位中添加自定義文本。
   1. 按一下 **[!UICONTROL Save]**。
1. 啟用網站或儲存視圖的預設可變描述符 _或_ 用於父網站的軟描述符：
   1. 選擇網站或商店視圖，位於 **[!UICONTROL Scope]** 下拉菜單，要為其啟用現有軟描述符。
   1. 切換 _上_ **[!UICONTROL Use website]** 或 **[!UICONTROL Use default]**，具體取決於您選擇的範圍)。
   1. 按一下 **[!UICONTROL Save]**。

   如果嘗試在不保存更改的情況下從此視圖中導航，則會出現一個模式，提示您放棄更改、繼續編輯或保存更改。

### 配置選項

| 欄位 | 範圍 | 說明 |
|---|---|---|
| [!UICONTROL Enable] | 網站 | 啟用或禁用 [!DNL Payment Services] 的子菜單。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Payment mode] | 商店視圖 | 設定儲存的方法或環境。 選項： [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | 商店視圖 | 您的沙盒商戶ID，在沙盒登機過程中自動生成。 |
| [!UICONTROL Production Merchant ID] | 商店視圖 | 您的生產商ID，它在裝箱過程中自動生成。 |
| [!UICONTROL Soft Descriptor] | 網站或商店視圖 | 將軟描述符添加到您的網站和商店視圖，以將資訊添加到客戶交易記錄中，這些交易記錄描述品牌、商店或產品線。 的 [!UICONTROL Use website] 切換應用在網站級別添加的任何軟描述符。 的 [!UICONTROL Use default] 切換應用作為預設添加的任何可變描述符。 |

## 配置付款選項

現在您已啟用 [!UICONTROL Payment Services] 對於您的網站，您可以更改付款功能和店面顯示的預設設定。

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**。

   ![首頁視圖](assets/payment-services-menu-small.png)

1. 按一下 **[!UICONTROL Settings]**。 請參閱 [簡介 [!DNL Payment Services] 首頁](payments-home.md) 的子菜單。
1. 為配置 [信用卡](#credit-card-fields)。 [付款按鈕](#payment-buttons), [按鈕樣式](#button-style)，按以下部分。

### 信用卡欄位

的 _[!UICONTROL Credit Card Fields]_設定為信用卡或借記卡付款方法提供簡單且安全的結帳選項。

請參閱 [付款選項](payments-options.md#credit-card-fields) 的子菜單。

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**。

   ![首頁視圖](assets/payment-services-menu-small.png)

1. 在 **[!UICONTROL Scope]** 下拉菜單，您要為其啟用付款方法。
1. 要更改在結帳期間顯示的付款方法的名稱，請在 **[!UICONTROL Checkout title]** 的子菜單。
1. 至 [設定付款活動](production.md#set-payment-services-as-payment-method)切換 **[!UICONTROL Payment action]** 至 `Authorize` 或 `Authorize and Capture`。
1. 啟用 [3DS安全身份驗證](security.md#3ds) (`Off` 預設)切換 **[!UICONTROL 3DS Secure authentication]** 選擇器 `Always` 或 `When required`。
1. 要啟用或禁用簽出頁上的信用卡欄位，請切換 **[!UICONTROL Show on checkout page]** 選擇器。
1. 啟用或禁用 [卡保險](#card-vaulting)，切換 **[!UICONTROL Vault enabled]** 選擇器。
1. 啟用或禁用 [管理員中的保險儲存付款方法](#card-vaulting) （對於商戶，使用其拱形付款方法為管理員中的客戶完成訂單）, **[!UICONTROL Show vaulted methods in Admin]** 選擇器。
1. 要啟用或禁用調試模式，請切換 **[!UICONTROL Debug Mode]** 選擇器。
1. 按一下 **[!UICONTROL Save]**。

   如果嘗試在不保存更改的情況下從此視圖中導航，則會出現一個模式，提示您放棄更改、繼續編輯或保存更改。

1. [刷新快取](#flush-the-cache)。

#### 配置選項

| 欄位 | 範圍 | 說明 |
|---|---|---|
| [!UICONTROL Title] | 商店視圖 | 在結帳期間，在「付款方法」視圖中將要顯示的文本添加為此付款選項的標題。 選項： [!UICONTROL text field] |
| [!UICONTROL Payment Action] | 網站 | 的 [付款操作](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} 指定的付款方式。 選項： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL 3DS Secure authentication] | 網站 | 啟用或禁用 [3DS安全身份驗證](security.md#3ds)。 選項： [!UICONTROL Always] / [!UICONTROL When Required] / [!UICONTROL Off] |
| [!UICONTROL Show on checkout page] | 網站 | 啟用或禁用要在簽出頁上顯示的信用卡欄位。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled] | 商店視圖 | 啟用或禁用 [信用卡保險](vaulting.md)。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show vaulted payment methods in Admin] | 商店視圖 | 啟用或禁用商家在管理員中為客戶完成訂單的能力 [使用拱形付款方法](vaulting.md)。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Debug Mode] | 網站 | 啟用或禁用調試模式。 選項： [!UICONTROL Yes] / [!UICONTROL No] |

### 付款按鈕

的 [!DNL PayPal Smart Buttons] 付款選項可為客戶提供簡單、快速和安全的結帳流程。 請參閱 [付款選項](payments-options.md#paypal-smart-buttons) 的子菜單。

您可以啟用和配置PayPal智慧按鈕付款選項：

1. 在 **[!UICONTROL Scope]** 下拉菜單，您要為其啟用付款方法。
1. 要更改在結帳期間顯示的付款方法的名稱，請在 **[!UICONTROL Checkout Title]** 的子菜單。
1. 至 [設定付款活動](production.md#set-payment-services-as-payment-method)切換 **[!UICONTROL Payment action]** 至 `Authorize` 或 `Authorize and Capture`。
1. 使用切換選擇器啟用或禁用 [!DNL PayPal smart button] 顯示功能：
   - **[!UICONTROL Show PayPal buttons on product checkout page]**
   - **[!UICONTROL Show PayPal buttons on product detail page]**
   - **[!UICONTROL Show PayPal buttons in mini-cart preview]**
   - **[!UICONTROL Show PayPal buttons on cart page]**
   - **[!UICONTROL Show PayPal Pay Later button]**
   - **[!UICONTROL Show PayPal Pay Later message]**
   - **[!UICONTROL Show Venmo button]**
   - **[!UICONTROL Show Apple Pay button]**

      >[!NOTE]
      >
      > 用Apple付你錢 [必須有Apple沙盒測試員帳戶](https://developer.apple.com/apple-pay/sandbox-testing/#create-a-sandbox-tester-account) （包括假信用卡和帳單資訊）以test它。 準備好在沙盒中使用Apple支付時 _或_ 生產模式，完成任何 [測試和驗證](test-validate.md#test-in-sandbox-environment)完成 [自註冊 [!DNL Apple Pay]](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) (_註冊您的活動域_ 僅限部分和 [將其配置為 [!DNL Payment Services]](settings.md#payment-buttons)。

      當您開啟/關閉付款按鈕或PayPal Pay Later消息的可見性時，該配置的可視預覽將顯示在「設定」頁的底部。

1. 要啟用調試模式，請切換 **[!UICONTROL Debug Mode]** 選擇器。
1. 按一下 **[!UICONTROL Save]**。

   如果嘗試在不保存更改的情況下從此視圖中導航，則會出現一個模式，提示您放棄更改、繼續編輯或保存更改。

1. [刷新快取](#flush-the-cache)。

#### 配置選項

| 欄位 | 範圍 | 說明 |
|---|---|---|
| [!UICONTROL Title] | 商店視圖 | 在結帳期間，在「付款方法」視圖中將要顯示為此付款選項標題的文本添加。 選項：文本欄位 |
| [!UICONTROL Payment Action] | 網站 | 的 [付款操作](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} 指定的付款方式。 選項： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show PayPal buttons on checkout page] | 商店視圖 | 啟用或禁用 [!DNL PayPal Smart Buttons] 的子菜單。 選項： [!UICONTROL  Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons on product detail page] | 商店視圖 | 啟用或禁用 [!DNL PayPal Smart Buttons] 產品詳細資訊頁面。 選項： [!UICONTROL  Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons in mini-cart preview] | 商店視圖 | 啟用或禁用 [!DNL PayPal Smart Buttons] 的子菜單。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
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
   > 如果按鈕樣式配置為 `Horizontal` 您的商店配置為顯示多個PayPal智慧按鈕，您只能看到產品頁、結帳頁和mini-cart上顯示的兩個按鈕，以及購物車中顯示的一個按鈕。

1. 要在水準佈局中啟用標籤線，請切換 **[!UICONTROL Show tagline]** 選擇器。
1. 修改 **[!UICONTROL Color]**，則選擇所需的顏色選項。
1. 修改 **[!UICONTROL Shape]**&#x200B;選中 `Pill` 或 `Rectangle`。
1. 要啟用按鈕高度選擇器，請切換 **[!UICONTROL Responsive button height]** 選擇器。
1. 修改 **[!UICONTROL Label]**，選擇所需的標籤選項。

   當您更改佈局、顏色、形狀、高度和標籤的配置選項時，該配置的可視預覽會顯示在「設定」頁的底部。

1. 按一下 **[!UICONTROL Save]**。

   如果嘗試在不保存更改的情況下從此視圖中導航，則會出現一個模式，提示您放棄更改、繼續編輯或保存更改。

1. [刷新快取](#flush-the-cache)。

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

## 刷新快取

如果更改中的配置 _設定_&#x200B;例如，切換「Apple支付」、「Venmo」或「PayPal PayLater」按鈕，手動刷新快取，以便您的儲存顯示最新配置。

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**。
1. 按一下 **[!UICONTROL Flush Cache]** 刷新所有無效的快取。

如果「快取管理」(Cache Management)表中的任何快取類型 `INVALIDATED` 狀態，您的商店可能無法顯示該項目的最新配置。 刷新快取以更新儲存以顯示最新配置。

為確保您的商店定期顯示正確的配置 [刷新快取](https://docs.magento.com/user-guide/system/cache-management.html)。

## 卡保險儲存

您可以啟用允許您的客戶保存其「我的帳戶」中的信用卡資訊以供將來購買的功能。

您還可以在管理員中使用卡保險儲存來為現有客戶完成後續訂單。

在中啟用或禁用卡保險儲存 [信用卡欄位設定](#credit-card-fields)。

請參閱 [信用卡保險儲存](vaulting.md) 的子菜單。

## 3DS

3DS可保護客戶和商戶不在其商店中進行欺詐活動，並使他們能夠遵守歐盟(EU)標準。

在 [信用卡欄位設定](#credit-card-fields)。

請參閱 [3DS安全](security.md#3ds) 的子菜單。

## 使用多個PayPal帳戶

在 [!UICONTROL Payment Services]，您可以在 **一個** 網站級上的商戶帳戶。 例如，如果您在多個國家/地區(使用不同的 [貨幣](https://docs.magento.com/user-guide/stores/currency.html))或者想用Adobe Commerce做你的生意，但不 _全部_，您可以設定您的商戶帳戶以使用多個PayPal帳戶。

請參閱 [站點、儲存和視圖範圍](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html) 的子菜單。

您的銷售代表可以建立新 [範圍](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) 用於您的商戶帳戶，並在附加站點上使用PayPal，以便您配置為顯示的任何PayPal按鈕都會顯示在您的站點上。 請聯繫您的銷售代表，以獲取有關為網站使用多個PayPal帳戶的幫助。
