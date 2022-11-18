---
title: 支付服務設定
description: 安裝後，您可以設定 [!DNL Payment Services] 在家裡。
role: Admin, User
level: Intermediate
exl-id: 108f2b24-39c1-4c87-8deb-d82ee1c24d55
source-git-commit: c993a2afe5b4da478ab57cbb391bb524d83c3d1a
workflow-type: tm+mt
source-wordcount: '1778'
ht-degree: 0%

---

# 設定

您可以自訂 [!DNL Payment Services] 以實用的設定，滿足您的需求 [!DNL Payment Services] 家。

配置 [!DNL Payment Services] for [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 按一下 **[!UICONTROL Settings]**. 這些設定選項僅適用於 _[!UICONTROL Payment mode]_欄位[_&#x200B;一般&#x200B;_配置選項](#configure-general-settings).

如需多商店或舊版設定，請參閱 [在管理員中進行設定](configure-admin.md).

## 配置常規設定

此 [!UICONTROL General] 設定提供啟用或禁用「支付服務」作為您的支付方法的功能，以及向客戶交易添加資訊，以用自定義資訊標籤或為網站或儲存視圖加上前置詞。

### 啟用支付服務

您可以啟用 [!DNL Payment Services] ，並啟用沙箱測試或即時付款。

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![首頁檢視](assets/payment-services-menu-small.png)

1. 按一下 **[!UICONTROL Settings]**. 請參閱 [簡介 [!DNL Payment Services] 首頁](payments-home.md) 以取得更多資訊。

   此 _[!UICONTROL General]_小節包含用來啟用的設定 [!DNL Payment Services] 作為付款方式。

1. 啟用 [!DNL Payment Services] 作為您商店的付款方式， _[!UICONTROL General]_切換&#x200B;**[!UICONTROL Enable Payment Services as payment method]**to `Yes`.

1. 如果您仍在測試 [!DNL Payment Services] 為您的商店設定 **付款模式** to `Sandbox`. 如果您已準備好啟用即時付款，請將其設定為 `Production`.

   >[!NOTE]
   >
   >您的 _[!UICONTROL Sandbox Merchant ID]_和_[!UICONTROL Production Merchant ID]_ 會在您完成沙箱和/或製作後，自動產生並呈現在其受人尊敬的領域中。

1. 按一下 **[!UICONTROL Save]**.

   如果您嘗試在未儲存變更的情況下離開此檢視，會出現一個強制回應，提示您捨棄變更、繼續編輯或儲存變更。

1. 導覽至 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 按一下 **[!UICONTROL Flush Cache]** 刷新所有無效快取。

您現在可以繼續變更 [付款選項](#configure-payment-options) 功能和店面顯示。

### 添加軟描述符

您可以新增 [!UICONTROL Soft Descriptor] 至您的網站或個別商店檢視設定。 軟描述符顯示在客戶交易銀行對帳單上。 例如，如果您有多個商店/品牌/目錄，則可借由在 [!UICONTROL Soft Descriptor] 欄位。

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![首頁檢視](assets/payment-services-menu-small.png)

1. 按一下 **[!UICONTROL Settings]**. 請參閱 [簡介 [!DNL Payment Services] 首頁](payments-home.md) 以取得更多資訊。
1. 在 **[!UICONTROL Scope]** 要為其建立軟描述符的下拉菜單。 若是初始設定，請將此項目保留為 **[!UICONTROL Default]** 來設定預設值。
1. 在文字欄位中新增自訂文字（最多22個字元），取代 `Custom descriptor`.
1. 按一下 **[!UICONTROL Save]**.
1. 要為網站或儲存視圖建立配置的預設值以外的軟描述符，請執行以下操作：
   1. 在 **[!UICONTROL Scope]** 要為其建立軟描述符的下拉菜單。
   1. 切換 _關閉_ **[!UICONTROL Use website]** (或 **[!UICONTROL Use default]**，視您選取的範圍而定)。
   1. 在文字欄位中新增自訂文字。
   1. 按一下 **[!UICONTROL Save]**.
1. 為網站或儲存區啟用預設軟描述符 _或_ 用於父網站的軟描述符：
   1. 在 **[!UICONTROL Scope]** 要啟用現有軟描述符的下拉菜單。
   1. 切換 _on_ **[!UICONTROL Use website]** (或 **[!UICONTROL Use default]**，取決於您選取的範圍)。
   1. 按一下 **[!UICONTROL Save]**.

   如果您嘗試在未儲存變更的情況下離開此檢視，會出現一個強制回應，提示您捨棄變更、繼續編輯或儲存變更。

### 配置選項

| 欄位 | 範圍 | 說明 |
|---|---|---|
| [!UICONTROL Enable] | 網站 | 啟用或禁用 [!DNL Payment Services] 的URL。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Payment mode] | 商店檢視 | 設定商店的方法或環境。 選項： [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | 商店檢視 | 您的沙箱商戶ID，會在沙箱上線期間自動產生。 |
| [!UICONTROL Production Merchant ID] | 商店檢視 | 您的生產商ID，會在沙箱上線期間自動產生。 |
| [!UICONTROL Soft Descriptor] | 網站或商店檢視 | 將軟描述符添加到您的網站和儲存視圖，以向客戶交易添加資訊，從而勾勒品牌、商店或產品線。 此 [!UICONTROL Use website] 切換應用在網站級別添加的任何軟描述符。 此 [!UICONTROL Use default] 切換應用添加為預設的任何軟描述符。 |

## 配置付款選項

現在您已為網站啟用了「支付服務」，您可以更改支付功能和店面顯示的預設設定。

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![首頁檢視](assets/payment-services-menu-small.png)

1. 按一下 **[!UICONTROL Settings]**. 請參閱 [簡介 [!DNL Payment Services] 首頁](payments-home.md) 以取得更多資訊。
1. 配置 [信用卡](#credit-card-fields), [付款按鈕](#payment-buttons)，和 [按鈕樣式](#button-style)，依照下列章節。

### 信用卡欄位

此 _[!UICONTROL Credit Card Fields]_設定為信用卡或借記卡付款方法提供簡單且安全的結帳選項。

請參閱 [付款選項](payments-options.md#credit-card-fields) 以取得更多資訊。

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![首頁檢視](assets/payment-services-menu-small.png)

1. 在 **[!UICONTROL Scope]** 要啟用付款方法的下拉式功能表。
1. 要更改結帳期間顯示的付款方法的名稱，請編輯 **[!UICONTROL Checkout title]** 欄位。
1. 結束日期 [設定付款活動](production.md#set-payment-services-as-payment-method)切換 **[!UICONTROL Payment action]** to `Authorize` 或 `Authorize and Capture`.
1. 若要啟用或停用結帳頁面上的信用卡欄位，請切換 **[!UICONTROL Show on checkout page]** 選取器。
1. 啟用或禁用 [卡卡保險](#card-vaulting)，切換 **[!UICONTROL Vault enabled]** 選取器。
1. 若要啟用或停用除錯模式，請切換 **[!UICONTROL Debug Mode]** 選取器。
1. 按一下 **[!UICONTROL Save]**.

   如果您嘗試在未儲存變更的情況下離開此檢視，會出現一個強制回應，提示您捨棄變更、繼續編輯或儲存變更。

1. [刷新快取](#flush-the-cache).

#### 配置選項

| 欄位 | 範圍 | 說明 |
|---|---|---|
| [!UICONTROL Title] | 商店檢視 | 在結帳期間，在「付款方法」視圖中添加要顯示為此付款選項標題的文本。 選項： [!UICONTROL text field] |
| [!UICONTROL Payment Action] | 網站 | 此 [付款動作](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;}，適用於指定的付款方法。 選項： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show on checkout page] | 網站 | 啟用或停用信用卡欄位以在結帳頁面上顯示。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled] | 網站 | 啟用或禁用信用卡保險儲存。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Debug Mode] | 網站 | 啟用或停用除錯模式。 選項： [!UICONTROL Yes] / [!UICONTROL No] |

### 付款按鈕

此 [!DNL PayPal Smart Buttons] 付款選項可為您的客戶提供簡單、快速且安全的結帳程式。 請參閱 [付款選項](payments-options.md#paypal-smart-buttons) 以取得更多資訊。

您可以啟用和配置PayPal智慧按鈕付款選項：

1. 在 **[!UICONTROL Scope]** 要啟用付款方法的下拉式功能表。
1. 要更改付款方法的名稱（如結帳期間所示），請編輯 **[!UICONTROL Checkout Title]** 欄位。
1. 結束日期 [設定付款活動](production.md#set-payment-services-as-payment-method)切換 **[!UICONTROL Payment action]** to `Authorize` 或 `Authorize and Capture`.
1. 使用切換選取器來啟用或停用 [!DNL PayPal smart button] 顯示功能：
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
      > 使用Apple Pay [必須有Apple開發人員帳戶](test-validate.md#test-in-sandbox-environment) （包括假信用卡和賬單資訊）以測試它。 準備好在沙箱中使用Apple Pay時 _或_ 完成任何 [測試和驗證](test-validate.md)，請連絡您的銷售代表，為您的即時商店啟用它。

      當您開啟/關閉付款按鈕或PayPal Pay Later消息的可見性時，該配置的可視預覽將顯示在「設定」頁面的底部。

1. 若要啟用除錯模式，請切換 **[!UICONTROL Debug Mode]** 選取器。
1. 按一下 **[!UICONTROL Save]**.

   如果您嘗試在未儲存變更的情況下離開此檢視，會出現一個強制回應，提示您捨棄變更、繼續編輯或儲存變更。

1. [刷新快取](#flush-the-cache).

#### 配置選項

| 欄位 | 範圍 | 說明 |
|---|---|---|
| [!UICONTROL Title] | 商店檢視 | 在結帳期間，在「付款方法」視圖中添加要顯示為此付款選項標題的文本。 選項：文字欄位 |
| [!UICONTROL Payment Action] | 網站 | 此 [付款動作](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;}，適用於指定的付款方法。 選項： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show PayPal buttons on checkout page] | 商店檢視 | 啟用或禁用 [!DNL PayPal Smart Buttons] 在結帳頁面上。 選項： [!UICONTROL  Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons on product detail page] | 商店檢視 | 啟用或禁用 [!DNL PayPal Smart Buttons] 在產品詳細資料頁面上。 選項： [!UICONTROL  Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons in mini-cart preview] | 商店檢視 | 啟用或禁用 [!DNL PayPal Smart Buttons] 在迷你購物車預覽中。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons on cart page] | 商店檢視 | 啟用或禁用 [!DNL PayPal Smart Buttons] 在購物車頁面上。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal Pay Later button] | 商店檢視 | 啟用或禁用顯示付款按鈕的稍後付款選項外觀。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal Pay Later Message] | 網站 | 在購物車、產品頁面、迷你購物車和結帳流程期間，啟用或停用「稍後付費」訊息。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show Venmo button] | 商店檢視 | 啟用或禁用顯示付款按鈕的Venmo付款選項。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show Apple Pay button] | 商店檢視 | 啟用或禁用顯示付款按鈕的Apple支付付款選項。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Debug Mode] | 網站 | 啟用或停用除錯模式。 選項： [!UICONTROL Yes] / [!UICONTROL No] |

### 按鈕樣式

您也可以設定 _[!UICONTROL Button style]_PayPal智慧按鈕的選項：

1. 若要變更 **[!UICONTROL Layout]**，選取 `Vertical` 或 `Horizontal`.

   >[!NOTE]
   >
   > 如果按鈕樣式設定為 `Horizontal` 而您的商店已設定為顯示多個PayPal智慧按鈕，則您可能只會看到產品頁面、結帳頁面和迷你購物車上顯示的兩個按鈕，以及購物車中顯示的一個按鈕。

1. 若要在水準版面中啟用標幟，請切換 **[!UICONTROL Show tagline]** 選取器。
1. 若要修改 **[!UICONTROL Color]**，請選取所需的顏色選項。
1. 若要修改 **[!UICONTROL Shape]**，選取 `Pill` 或 `Rectangle`.
1. 若要啟用按鈕高度選取器，請切換 **[!UICONTROL Responsive button height]** 選取器。
1. 若要修改 **[!UICONTROL Label]**，請選取所需的標籤選項。

   當您變更版面、顏色、形狀、高度和標籤的配置選項時，該配置的視覺預覽會顯示在「設定」頁面的底部。

1. 按一下 **[!UICONTROL Save]**.

   如果您嘗試在未儲存變更的情況下離開此檢視，會出現一個強制回應，提示您捨棄變更、繼續編輯或儲存變更。

1. [刷新快取](#flush-the-cache).

您可以設定 [!DNL PayPal Smart Buttons] 樣式 [中的「舊版」設定](configure-admin.md#configure-paypal-smart-buttons) 或此處 [!DNL Payment Services Home]. 請參閱 [PayPal的按鈕樣式指南](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) 以取得選項的詳細資訊。

#### 配置選項

| 欄位 | 範圍 | 說明 |
|--- |--- |--- |
| [!UICONTROL Layout] | 商店檢視 | 定義付款按鈕的配置樣式。 選項： [!UICONTROL Vertical] / [!UICONTROL Horizontal] |
| [!UICONTROL Tagline] | 商店檢視 | 啟用/停用標籤。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Color] | 商店檢視 | 定義付款按鈕的顏色。 選項： [!UICONTROL Blue] / [!UICONTROL Gold] / [!UICONTROL Silver] / [!UICONTROL White] / [!UICONTROL Black] |
| [!UICONTROL Shape] | 商店檢視 | 定義付款按鈕的形狀。 選項： [!UICONTROL Rectangular] / [!UICONTROL Pill] |
| [!UICONTROL Responsive Button Height] | 商店檢視 | 定義付款按鈕是否使用預設高度。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Height] | 商店檢視 | 定義付款按鈕的高度。 預設值：無 |
| [!UICONTROL Label] | 商店檢視 | 定義顯示在付款按鈕中的標籤。 選項： [!UICONTROL PayPal] / [!UICONTROL Checkout] / [!UICONTROL Buynow] / [!UICONTROL Pay] / [!UICONTROL Installment] |

## 刷新快取

若您在 _設定_，例如切換「Apple支付」、「Venmo」或「PayPal支付」按鈕，手動刷新快取，以便您的商店顯示最新配置。

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. 按一下 **[!UICONTROL Flush Cache]** 刷新所有無效快取。

如果「快取管理」表中的「快取類型」具有 `INVALIDATED` 狀態，則儲存區可能不會顯示該項目的最新設定。 刷新快取以更新儲存以顯示最新配置。

為確保您的儲存區顯示正確的配置，請定期 [刷新快取](https://docs.magento.com/user-guide/system/cache-management.html).

## 卡儲存

您可以啟用允許客戶儲存（或「保存」）其「我的帳戶」中的信用卡資訊以用於將來購買的功能。

在 [信用卡欄位設定](#credit-card-fields).

請參閱 [信用卡保險](vaulting.md) ，了解有關保險儲存的詳細資訊。

## 使用多個PayPal帳戶

在Payment Services中，您可以在 **one** 網站層級的商家帳戶。 例如，如果您在多個國家/地區(使用不同 [貨幣](https://docs.magento.com/user-guide/stores/currency.html))，或想將Adobe Commerce用於您業務的某些部分，但不想 _all_，您可以設定您的商戶帳戶，以使用多個PayPal帳戶。

請參閱 [站點、儲存和查看範圍](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html) 以取得網站、商店和商店檢視階層的詳細資訊。

您的銷售代表可以建立新 [範圍](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) 的商家帳戶，並將附加網站上的PayPal上顯示，這樣您設定為顯示的任何PayPal按鈕都會顯示在您的網站上。 請連絡您的銷售代表，以取得在您的網站上使用多個PayPal帳戶的協助。
