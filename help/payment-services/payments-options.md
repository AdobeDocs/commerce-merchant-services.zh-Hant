---
title: 付款選項
description: 設定付款選項，以自訂商店客戶可用的方式。
exl-id: 95e648e6-6cb8-4226-b5ea-e1857212f20a
feature: Payments, Checkout, Configuration
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '1171'
ht-degree: 0%

---

# 付款選項

替換為 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] [!DNL Payment Services]，您有多個可用的付款選項。 您可以透過以下方式設定這些付款選項：

* [首頁設定](payments-home.md)
* [存放區設定](configure-admin.md) （建議舊版付款選項或多重商店設定使用）

根據您在結帳過程中的位置，每種付款方式都有不同的行為：

* 產品頁面 — 專案的產品頁面
* 迷你購物車 — 當產品已新增至購物車時，按一下購物車圖示即可使用
* 購物車 — 按一下即可使用 _檢視和編輯購物車_ 從mini-cart
* 出庫檢視 — 按一下即可使用 _繼續結帳_ 來自迷你購物車或購物車

>[!IMPORTANT]
>
>必須先完成付款服務上線，才能處理付款。

## [!UICONTROL Credit Card Fields]

[!UICONTROL Credit Card Fields] 為信用卡或扣帳卡付款方式提供簡單安全的結帳。 當購物者使用信用卡欄位結帳時，他們會輸入他們的姓名、帳單地址以及信用卡或扣帳卡資訊來下訂單。 客戶資訊在購買工作階段期間會安全地使用，以順暢地引導他們完成結帳流程。

啟用 [信用卡保險存放](#vaulting) 讓您的商店允許購物者儲存信用卡資訊，以便稍後快速結帳。

您可以設定 [!UICONTROL Credit Card Fields] 在商店設定或支付服務首頁中。 另請參閱 [設定](settings.md#credit-card-fields) 以取得詳細資訊。

您也可以變更信用卡欄位的版面、寬度、高度和外部樣式。 另請參閱 [PayPal檔案](https://developer.paypal.com/docs/checkout/advanced/customize/card-field-style/) 以取得詳細資訊。

## [!DNL PayPal Smart Buttons]

[!DNL PayPal Smart Buttons]，會使用PayPal完成購買、儲存購物者的運送地址、帳單地址及付款詳細資料，以供日後使用。 購物者可以使用PayPal先前儲存或提供的任何付款方式。

![[!DNL PayPal Smart Buttons] 選項](assets/payment-buttons.png){width="500"}

您可以設定 [!UICONTROL PayPal Smart Buttons] 在商店設定或支付服務首頁中。  另請參閱 [設定](settings.md#payment-buttons) 以取得詳細資訊。

### [!DNL PayPal] 按鈕

客戶可以使用PayPal按鈕輕鬆自信地結帳離開。

此 [!DNL PayPal] 按鈕在產品頁面、迷你購物車、購物車和結帳檢視中可見。

### [!DNL Venmo] 按鈕

客戶可使用 [Venmo](https://venmo.com/) 按鈕。

此 [!DNL Venmo] 按鈕在產品頁面、迷你購物車、購物車和結帳檢視中可見。

### [!DNL Apple Pay] 按鈕

客戶可以在他們的裝置上使用Touch ID來使用 [[!DNL Apple Pay]](https://www.apple.com/apple-pay/)，會使用儲存在iOS或macOS裝置上的信用卡和扣帳卡付款憑證。

此 [!DNL Apple Pay] 按鈕在產品頁面、迷你購物車、購物車和結帳檢視中可見。

>[!NOTE]
>
> 使用 [!DNL Apple Pay] 針對您的商店，完成 [自行註冊 [!DNL Apple Pay]](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) (_註冊您的即時網域_ 章節)和 [為中的商店設定 [!DNL Payment Services]](settings.md#payment-buttons).

### PayPal借方或信用卡按鈕

客戶可以使用「PayPal扣款」或「信用卡」按鈕結帳。

「PayPal扣款」或「信用卡」按鈕會從結帳頁面顯示。

當您沒有其他信用卡提供者時，此選項可用來向購物者顯示PayPal扣款或信用卡付款選項。

### [!DNL Pay Later] 按鈕

為您的客戶提供短期、免息的付款和其他融資選項，以便他們現在購買後使用 [!DNL Pay Later] 按鈕。

此 [!DNL Pay Later] 按鈕在產品頁面、迷你購物車、購物車和結帳檢視中可見：

* **當客戶選擇介於$30和$600之間的產品時**，在PayPal和底下傳送訊息 [!DNL Pay Later] 按鈕可為客戶提供更多關於 [!DNL Pay in 4] 付款選項。 客戶可以點選 **瞭解更多** 以瞭解&quot;[!DNL Pay in 4]」選項 _或_ 按一下快顯視窗中的「或檢視6個月特殊融資」文字，瞭解並申請PayPal信用選項。
* **當客戶選取超過$98.99的產品時**，在PayPal和底下傳送訊息 [!DNL Pay Later] 按鈕可提供客戶有關PayPal信用支付選項的更多資訊。 客戶可以點選 **瞭解更多** 若要瞭解並申請PayPal信用額度選項， _或_ 按一下快顯視窗中的「或按4付款」文字，瞭解 [!DNL Pay in 4] 選項。

  >[!NOTE]
  >
  >以上所列金額可能會有變動。

另請參閱 [設定](settings.md#payment-buttons) 以瞭解如何停用/啟用 [!DNL Pay Later] 傳送訊息。

有兩種付款選項 [!DNL Pay Later] 按鈕：

* **以4付款** — 客戶在初次支付首期付款後，可以透過四筆免息付款（每兩週）來支付訂單餘額。 請參閱 [以4份檔案付費](https://www.paypal.com/us/digital-wallet/ways-to-pay/buy-now-pay-later) 以取得詳細資訊。
* **PayPal信用** — 客戶可在6個月內全額支付訂單餘額，且免息。 請參閱 [PayPal信用檔案](https://www.paypal.com/us/webapps/mpp/paypal-credit) 以取得詳細資訊。

### [!DNL Pay Now] 按鈕

此 [!DNL Pay Now] 當客戶按一下付款熒幕上的付款按鈕時，按鈕會顯示在PayPal彈出式視窗中。

如果最終訂單金額還不清楚（例如您還沒有送貨地址資訊），而客戶正在從產品頁面、迷你購物車或購物車結帳時，則會收到 _繼續_ 按鈕可供使用。 客戶點按時 _繼續_，在確認其付款方式後，系統會將他們導向至訂單稽核頁面，以在完成結帳前收集所需的詳細資料。

## 僅使用PayPal付款按鈕

若要快速將您的商店帶入生產模式，您可以設定 _僅限_ PayPal付款按鈕（Venmo、PayPal等） — 不要再使用PayPal信用卡付款選項。

這可讓您：

* 為您的客戶提供各種付款選項，包括Venmo和PayPal付款按鈕，以及關閉PayPal代管卡欄位，並使用現有信用卡提供者的選項。
* 使用您現有的信用卡提供者進行信用卡付款，同時利用PayPal的其他付款選項。
* 在PayPal不支援信用卡作為付款選項的地區，使用PayPal的付款按鈕。

至 **擷取付款方式 _僅限_ PayPal付款按鈕(_not_ paypal信用卡付款選項)**：

1. 確認您的存放區為 [在生產模式中](settings.md#enable-payment-services).
1. [設定所需的PayPal付款按鈕](settings.md#payment-buttons) （在設定中）。
1. 翻轉 _關閉_ 此 **[[!UICONTROL Show PayPal Credit and Debit card button]](settings.md#payment-buttons)** 中的選項 _[!UICONTROL Payment buttons]_區段。

至 **向現有的信用卡提供者擷取付款 _和_ PayPal付款按鈕**：

1. 確認您的存放區為 [在生產模式中](settings.md#enable-payment-services).
1. [設定所需的PayPal付款按鈕](settings.md#payment-buttons).
1. 翻轉 _關閉_ 此 **[[!UICONTROL PayPal Show Credit and Debit card button]](settings.md#payment-buttons)** 中的選項 _[!UICONTROL Payment buttons]_區段。
1. 翻轉 _關閉_ 此 **[[!UICONTROL Show on checkout page]](settings.md#credit-card-fields)** 中的選項 _[!UICONTROL Credit card fields]_區段並使用您的 [現有的信用卡提供者帳戶](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/payments.html#payments).

## 訂單重新計算

當客戶從迷你購物車、購物車或產品頁面進入結帳流程時，會被導向至訂單稽核頁面，他們可在PayPal快顯視窗中看到選取的送貨地址。 客戶選取出貨方式後，會適當地重新計算訂單金額，而客戶可以看到出貨成本與稅捐。

當客戶從結帳頁面進入結帳流程時，系統已知道送貨地址及最終計算金額，且總計已適當呈現。

免稅期、運費和銷售稅可能因地點而異。 晚於 [!DNL Payment Services] 會收到送貨地址與運費，然後快速重新計算所有適用成本，並在結帳的最後階段適當地加以顯示。

## 信用卡保險存放

購物者可以儲存信用卡資訊，以便日後在網站層級（同一商家帳戶內的任何商店）購買。

另請參閱 [信用卡保險存放](vaulting.md) 以取得詳細資訊。

## 安全性

另請參閱 [PCI法規遵循](security.md#pci-compliance) 以取得詳細資訊。
