---
title: 付款服務設定
description: 安裝後，您可以設定 [!DNL Payment Services] 在首頁中。
role: Admin, User
level: Intermediate
exl-id: 108f2b24-39c1-4c87-8deb-d82ee1c24d55
source-git-commit: c28b86f3a0ff0aae06a4ee8a60b2b9f304295ff8
workflow-type: tm+mt
source-wordcount: '2036'
ht-degree: 0%

---

# 設定

您可以自訂 [!DNL Payment Services] 利用「 」中的實用設定來滿足您的需求 [!DNL Payment Services] 首頁。

進行設定 [!DNL Payment Services] 的 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 按一下 **[!UICONTROL Settings]**. 這些設定選項僅適用於中設定的環境。 _[!UICONTROL Payment mode]_的欄位[_&#x200B;一般&#x200B;_設定選項](#configure-general-settings).

如需多存放區或舊版設定，請參閱 [在管理員中設定](configure-admin.md).

## 設定一般設定

此 [!UICONTROL General] 設定可讓您啟用或停用「付款服務」作為付款方式，以及新增資訊至客戶交易，以使用自訂資訊標籤或加上網站或商店檢視的字首。

### 啟用付款服務

您可以啟用 [!DNL Payment Services] ，並啟用沙箱測試或即時付款。

1. 於 _管理員_ 側欄，前往 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![首頁檢視](assets/payment-services-menu-small.png)

1. 按一下 **[!UICONTROL Settings]**. 另請參閱 [簡介 [!DNL Payment Services] 首頁](payments-home.md) 以取得詳細資訊。

   此 _[!UICONTROL General]_區段包含用於啟用的設定 [!DNL Payment Services] 作為付款方式。

1. 若要啟用 [!DNL Payment Services] 作為商店的付款方式，在 _[!UICONTROL General]_區段，切換&#x200B;**[!UICONTROL Enable Payment Services as payment method]**至 `Yes`.

1. 如果您仍在測試 [!DNL Payment Services] 針對您的商店，設定 **付款模式** 至 `Sandbox`. 如果您已準備好啟用即時付款，請將其設為 `Production`.

   >[!NOTE]
   >
   >您的 _[!UICONTROL Sandbox Merchant ID]_和_[!UICONTROL Production Merchant ID]_ 都是自動產生的，當您完成沙箱和/或生產環境上線時，會顯示在其受人尊敬的欄位中。

1. 按一下 **[!UICONTROL Save]**.

   如果您嘗試離開此檢視而不儲存變更，會出現一個強制回應視窗，提示您捨棄變更、繼續編輯或儲存變更。

1. 導覽至 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 並按一下 **[!UICONTROL Flush Cache]** 以重新整理所有無效的快取。

您現在可以繼續變更的預設設定 [付款選項](#configure-payment-options) 功能和店面顯示器。

### 新增軟性描述項

您可以新增 [!UICONTROL Soft Descriptor] 至您的網站或個別商店檢視的設定。 軟性描述元會顯示在客戶交易銀行對帳單上。 例如，如果您有多個商店/品牌/目錄，您可以透過將自訂文字新增至 [!UICONTROL Soft Descriptor] 欄位。

1. 於 _管理員_ 側欄，前往 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![首頁檢視](assets/payment-services-menu-small.png)

1. 按一下 **[!UICONTROL Settings]**. 另請參閱 [簡介 [!DNL Payment Services] 首頁](payments-home.md) 以取得詳細資訊。
1. 選取網站或商店檢視，在 **[!UICONTROL Scope]** 下拉式選單，您要為其建立軟性描述項。 對於初始設定，請將此項保留為 **[!UICONTROL Default]** 以設定預設值。
1. 在文字欄位中新增自訂文字（最多22個字元），取代 `Custom descriptor`.
1. 按一下 **[!UICONTROL Save]**.
1. 若要為網站或商店檢視建立非預設值的可變描述項：
   1. 選取網站或商店檢視，在 **[!UICONTROL Scope]** 下拉式選單，您要為其建立軟性描述項。
   1. 切換 _關閉_ **[!UICONTROL Use website]** (或 **[!UICONTROL Use default]**，視您選取的範圍而定)。
   1. 在文字欄位中新增自訂文字。
   1. 按一下 **[!UICONTROL Save]**.
1. 若要為網站或商店啟用檢視預設軟性描述項 _或_ 用於上層網站的軟性描述項：
   1. 選取網站或商店檢視，在 **[!UICONTROL Scope]** 下拉式功能表，您要啟用現有的軟性描述項。
   1. 切換 _於_ **[!UICONTROL Use website]** (或 **[!UICONTROL Use default]**，視您選取的範圍而定)。
   1. 按一下 **[!UICONTROL Save]**.

   如果您嘗試離開此檢視而不儲存變更，會出現一個強制回應視窗，提示您捨棄變更、繼續編輯或儲存變更。

### 設定選項

| 欄位 | 範圍 | 說明 |
|---|---|---|
| [!UICONTROL Enable] | 網站 | 啟用或停用 [!DNL Payment Services] （適用於您的網站）。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Payment mode] | 存放區檢視 | 設定商店的方法或環境。 選項： [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | 存放區檢視 | 您的沙箱商家ID，會在沙箱上線期間自動產生。 |
| [!UICONTROL Production Merchant ID] | 存放區檢視 | 您的生產廠商ID，會在沙箱上線時自動產生。 |
| [!UICONTROL Soft Descriptor] | 網站或商店檢視 | 新增軟性描述項至您的網站和商店檢視，以將資訊新增至客戶交易，其中描述品牌、商店或產品線。 此 [!UICONTROL Use website] 切換會套用網站層級新增的任何軟性描述項。 此 [!UICONTROL Use default] 切換會套用新增為預設的任何軟性描述項。 |

## 設定付款選項

現在您已啟用 [!UICONTROL Payment Services] 對於您的網站，您可以變更付款功能和店面顯示的預設設定。

1. 於 _管理員_ 側欄，前往 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![首頁檢視](assets/payment-services-menu-small.png)

1. 按一下 **[!UICONTROL Settings]**. 另請參閱 [簡介 [!DNL Payment Services] 首頁](payments-home.md) 以取得詳細資訊。
1. 設定付款選項 [信用卡](#credit-card-fields)， [付款按鈕](#payment-buttons)、和 [按鈕樣式](#button-style)，詳見以下章節。

### 信用卡欄位

此 _[!UICONTROL Credit Card Fields]_設定提供簡單且安全的結帳選項，適用於信用卡或扣帳卡付款方式。

另請參閱 [付款選項](payments-options.md#credit-card-fields) 以取得詳細資訊。

1. 於 _管理員_ 側欄，前往 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![首頁檢視](assets/payment-services-menu-small.png)

1. 選取商店檢視，在 **[!UICONTROL Scope]** 下拉式功能表，您要為其啟用付款方式。
1. 若要變更結帳時顯示的付款方式名稱，請編輯 **[!UICONTROL Checkout title]** 欄位。
1. 至 [設定付款作業](production.md#set-payment-services-as-payment-method)，切換 **[!UICONTROL Payment action]** 至 `Authorize` 或 `Authorize and Capture`.
1. 若要啟用 [3DS安全驗證](security.md#3ds) (`Off` 依預設)切換 **[!UICONTROL 3DS Secure authentication]** 選擇器至 `Always` 或 `When required`.
1. 若要啟用或停用結帳頁面上的信用卡欄位，請切換 **[!UICONTROL Show on checkout page]** 選擇器。
1. 啟用或停用 [卡片儲存庫](#card-vaulting)，切換 **[!UICONTROL Vault enabled]** 選擇器。
1. 啟用或停用 [Admin中的存放式付款方法](#card-vaulting) （商戶若要使用「管理員」中的保管式付款方式完成客戶的訂單），請切換 **[!UICONTROL Show vaulted methods in Admin]** 選擇器。
1. 若要啟用或停用偵錯模式，請切換 **[!UICONTROL Debug Mode]** 選擇器。
1. 按一下 **[!UICONTROL Save]**.

   如果您嘗試離開此檢視而不儲存變更，會出現一個強制回應視窗，提示您捨棄變更、繼續編輯或儲存變更。

1. [清除快取](#flush-the-cache).

#### 設定選項

| 欄位 | 範圍 | 說明 |
|---|---|---|
| [!UICONTROL Title] | 存放區檢視 | 在結帳期間，在「付款方式」檢視中，新增文字以顯示為此付款選項的標題。 選項： [!UICONTROL text field] |
| [!UICONTROL Payment Action] | 網站 | 此 [付款動作](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} 指定付款方式的。 選項： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL 3DS Secure authentication] | 網站 | 啟用或停用 [3DS安全驗證](security.md#3ds). 選項： [!UICONTROL Always] / [!UICONTROL When Required] / [!UICONTROL Off] |
| [!UICONTROL Show on checkout page] | 網站 | 啟用或停用要在結帳頁面上顯示的信用卡欄位。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled] | 存放區檢視 | 啟用或停用 [信用卡保險存放](vaulting.md). 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show vaulted payment methods in Admin] | 存放區檢視 | 啟用或停用商家在管理員中為客戶完成訂單的功能 [使用儲存的付款方式](vaulting.md). 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Debug Mode] | 網站 | 啟用或停用偵錯模式。 選項： [!UICONTROL Yes] / [!UICONTROL No] |

### 付款按鈕

此 [!DNL PayPal Smart Buttons] 付款選項可為您的客戶提供簡單、快速且安全的結帳程式。 另請參閱 [付款選項](payments-options.md#paypal-smart-buttons) 以取得詳細資訊。

您可以啟用和設定PayPal智慧按鈕付款選項：

1. 選取商店檢視，在 **[!UICONTROL Scope]** 下拉式功能表，您要為其啟用付款方式。
1. 若要變更結帳時顯示的付款方式名稱，請編輯 **[!UICONTROL Checkout Title]** 欄位。
1. 至 [設定付款作業](production.md#set-payment-services-as-payment-method)，切換 **[!UICONTROL Payment action]** 至 `Authorize` 或 `Authorize and Capture`.
1. 使用切換選擇器來啟用或停用 [!DNL PayPal smart button] 顯示功能：

   - **[!UICONTROL Show PayPal buttons on product checkout page]**
   - **[!UICONTROL Show PayPal buttons on product detail page]**
   - **[!UICONTROL Show PayPal buttons in mini-cart preview]**
   - **[!UICONTROL Show PayPal buttons on cart page]**
   - **[!UICONTROL Show PayPal Pay Later button]**
   - **[!UICONTROL Show PayPal Pay Later message]**
   - **[!UICONTROL Show Venmo button]**
   - **[!UICONTROL Show Apple Pay button]**
   - **[!UICONTROL Show PayPal Credit and Debit Card button]**

     >[!NOTE]
     >
     > 若要使用Apple支付給您 [必須具有Apple sandbox tester帳戶](https://developer.apple.com/apple-pay/sandbox-testing/#create-a-sandbox-tester-account) （包含假信用卡和帳單資訊）進行測試。 當您準備好在沙箱中使用Apple Pay時 _或_ 生產模式，完成任何 [測試和驗證](test-validate.md#test-in-sandbox-environment)，完成 [自行註冊 [!DNL Apple Pay]](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) (_註冊您的即時網域_ 章節)和 [為中的商店設定 [!DNL Payment Services]](settings.md#payment-buttons).

     當您開啟/關閉付款按鈕或PayPal Pay Later訊息的可見度時，「設定」頁面底部會顯示該設定的視覺預覽。

1. 若要啟用偵錯模式，請切換 **[!UICONTROL Debug Mode]** 選擇器。
1. 按一下 **[!UICONTROL Save]**.

   如果您嘗試離開此檢視而不儲存變更，會出現一個強制回應視窗，提示您捨棄變更、繼續編輯或儲存變更。

1. [清除快取](#flush-the-cache).

#### 設定選項

| 欄位 | 範圍 | 說明 |
|---|---|---|
| [!UICONTROL Title] | 存放區檢視 | 結帳期間，在「付款方式」檢視中，新增要顯示為此付款選項標題的文字。 選項：文字欄位 |
| [!UICONTROL Payment Action] | 網站 | 此 [付款動作](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} 指定付款方式的。 選項： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show PayPal buttons on checkout page] | 存放區檢視 | 啟用或停用 [!DNL PayPal Smart Buttons] 在結帳頁面上。 選項： [!UICONTROL  Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons on product detail page] | 存放區檢視 | 啟用或停用 [!DNL PayPal Smart Buttons] 在產品詳細資料頁面上。 選項： [!UICONTROL  Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons in mini-cart preview] | 存放區檢視 | 啟用或停用 [!DNL PayPal Smart Buttons] 在迷你購物車預覽中。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons on cart page] | 存放區檢視 | 啟用或停用 [!DNL PayPal Smart Buttons] 在購物車頁面上。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal Pay Later button] | 存放區檢視 | 啟用或停用顯示付款按鈕的稍後付款選項外觀。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal Pay Later Message] | 網站 | 在購物車、產品頁面、迷你購物車和結帳流程中啟用或停用「稍後付款」訊息。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show Venmo button] | 存放區檢視 | 啟用或停用顯示付款按鈕的Venmo付款選項。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show Apple Pay button] | 存放區檢視 | 啟用或停用顯示付款按鈕的Apple Pay付款選項。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal Credit and Debit card button] | 存放區檢視 | 啟用或停用顯示付款按鈕的「信用卡與借記卡」付款選項。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Debug Mode] | 網站 | 啟用或停用偵錯模式。 選項： [!UICONTROL Yes] / [!UICONTROL No] |

### 按鈕樣式

您也可以設定 _[!UICONTROL Button style]_paypal智慧型按鈕的選項：

1. 若要變更 **[!UICONTROL Layout]**，選取 `Vertical` 或 `Horizontal`.

   >[!NOTE]
   >
   > 如果按鈕樣式設定為 `Horizontal` 而且您的商店已設定為顯示多個PayPal智慧型按鈕，您只能看見產品頁面、結帳頁面和迷你購物車上顯示兩個按鈕，以及購物車中顯示的一個按鈕。

1. 若要在水準版面配置中啟用標語，請切換 **[!UICONTROL Show tagline]** 選擇器。
1. 若要修改 **[!UICONTROL Color]**，選取所需的顏色選項。
1. 若要修改 **[!UICONTROL Shape]**，選取 `Pill` 或 `Rectangle`.
1. 若要啟用按鈕高度選擇器，請切換 **[!UICONTROL Responsive button height]** 選擇器。
1. 若要修改 **[!UICONTROL Label]**，選取所需的標籤選項。

   當您變更版面、顏色、形狀、高度和標籤的組態選項時，該組態的視覺預覽會顯示在「設定」頁面底部。

   ![[!DNL PayPal Smart Buttons] 選項](assets/payment-buttons.png){width="500"}

1. 按一下 **[!UICONTROL Save]**.

   如果您嘗試離開此檢視而不儲存變更，會出現一個強制回應視窗，提示您捨棄變更、繼續編輯或儲存變更。

1. [清除快取](#flush-the-cache).

您可以設定 [!DNL PayPal Smart Buttons] 樣式 [在Admin的舊版設定中](configure-admin.md#configure-paypal-smart-buttons) 或在此輸入 [!DNL Payment Services Home]. 另請參閱 [PayPal按鈕風格指南](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) 以取得選項的詳細資訊。

#### 設定選項

| 欄位 | 範圍 | 說明 |
|--- |--- |--- |
| [!UICONTROL Layout] | 存放區檢視 | 定義付款按鈕的版面配置樣式。 選項： [!UICONTROL Vertical] / [!UICONTROL Horizontal] |
| [!UICONTROL Tagline] | 存放區檢視 | 啟用/停用標語。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Color] | 存放區檢視 | 定義付款按鈕的色彩。 選項： [!UICONTROL Blue] / [!UICONTROL Gold] / [!UICONTROL Silver] / [!UICONTROL White] / [!UICONTROL Black] |
| [!UICONTROL Shape] | 存放區檢視 | 定義付款按鈕的形狀。 選項： [!UICONTROL Rectangular] / [!UICONTROL Pill] |
| [!UICONTROL Responsive Button Height] | 存放區檢視 | 定義付款按鈕是否使用預設高度。 選項： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Height] | 存放區檢視 | 定義付款按鈕的高度。 預設值：無 |
| [!UICONTROL Label] | 存放區檢視 | 定義出現在付款按鈕中的標籤。 選項： [!UICONTROL PayPal] / [!UICONTROL Checkout] / [!UICONTROL Buynow] / [!UICONTROL Pay] / [!UICONTROL Installment] |

## 設定角色

為確保管理員使用者能在商務管理員中建立和管理訂單，請啟用 [!DNL Payment Services] — 使用者角色的特定資源。

另請參閱 [使用者角色](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions-user-roles.html) 以瞭解如何管理角色。

將資源指派給角色時，您必須選取：

- **付款方式[!DNL Payment Services]** — 此資源可確保當您在Admin中建立訂單時， [!DNL Payment Services] 信用卡可作為付款方式使用。 如果您選取 **動作** 上層資源，也會選取此資源。
- **[!DNL Payment Services]** — 此資源包括 **儀表板** 和 **SaaS服務Proxy** 資源，也必須選取它。 它們可確保 [!DNL Payment Services] 出現在 _銷售_ 功能表。

  ![付款服務資源](assets/roles-payments.png)

## 清除快取

如果您變更設定 _設定_&#x200B;例如，切換Apple Pay、Venmo或PayPal PayLater按鈕，手動清除快取，讓您的商店顯示最新設定。

1. 於 _管理員_ 側欄，前往 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. 按一下 **[!UICONTROL Flush Cache]** 以重新整理所有無效的快取。

如果「快取管理」表格中的快取型別有 `INVALIDATED` 狀態，您的存放區可能不會顯示該專案的最新設定。 排清快取以更新您的存放區以顯示最新設定。

為確保您的存放區顯示正確的設定，請定期進行 [清除快取](https://docs.magento.com/user-guide/system/cache-management.html).

## 卡片儲存庫

您可以啟用可讓客戶將信用卡資訊儲存在「我的帳戶」中（或「儲存」），以便用於未來購買的功能。

您也可以在「管理員」中使用卡儲存庫，以完成現有客戶的後續訂單。

啟用或停用中的資訊卡儲存庫 [信用卡欄位設定](#credit-card-fields).

另請參閱 [信用卡保險存放](vaulting.md) 以取得詳細資訊。

## 3DS

3DS可保護客戶與商戶免受店內詐騙活動的傷害，並可符合歐盟(EU)標準。

啟用或停用3DS於 [信用卡欄位設定](#credit-card-fields).

另請參閱 [安全性中的3DS](security.md#3ds) 以取得詳細資訊。

## 使用多個PayPal帳戶

在 [!UICONTROL Payment Services]，您可在內使用多個PayPal帳戶 **一** 網站層級的商家帳戶。 例如，如果您在多個國家/地區經營商店(這些國家使用不同的 [貨幣](https://docs.magento.com/user-guide/stores/currency.html))或想將Adobe Commerce用於部分業務，但不想使用 _全部_，您可以將商家帳戶設定為使用多個PayPal帳戶。

另請參閱 [網站、存放區和檢視範圍](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html) 有關網站、商店和商店檢視階層的詳細資訊。

您的銷售代表可以建立 [範圍](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) ，並使用PayPal加入其他網站，以便您設定為顯示的任何PayPal按鈕都會顯示在您的網站上。 請聯絡您的銷售代表，以取得使用您網站的多個PayPal帳戶的相關協助。
