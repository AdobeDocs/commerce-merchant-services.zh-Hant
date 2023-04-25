---
title: 付款選項
description: 設定付款選項以自訂商店客戶可用的方法。
exl-id: 95e648e6-6cb8-4226-b5ea-e1857212f20a
source-git-commit: fac3efb74cdfdb855a3706d84cdca2dcde959940
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 付款選項

使用 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] [!DNL Payment Services]，您可以使用多個付款選項。 您可以通過以下方式配置這些付款選項：

* [首頁設定](payments-home.md)
* [儲存配置](configure-admin.md) （建議使用舊式付款選項或多商店設定）

根據您處於結帳流程的位置，每種付款方法都有不同的行為：

* 產品頁 — 項目的產品頁
* 迷你購物車 — 產品新增至購物車時，按一下購物車圖示即可使用
* 購物車 — 點按後即可使用 _檢視和編輯購物車_ 從迷你購物車
* 簽出視圖 — 按一下 _繼續結帳_ 從迷你購物車或購物車

>[!IMPORTANT]
>
>必須先完成Payment Services上線，然後才能處理付款。

## [!UICONTROL Credit Card Fields]

[!UICONTROL Credit Card Fields] 為信用卡或借記卡付款方法提供簡單而安全的結帳。 購物者使用信用卡欄位結帳時，會輸入其名稱、帳單地址、信用卡或借記卡資訊，以下單。 購買工作階段期間會安全地使用客戶資訊，順暢地引導客戶完成結帳流程。

啟用 [信用卡保險](#vaulting) 讓購物者儲存（儲存）其信用卡資訊，以便稍後快速結帳。

您可以設定 [!UICONTROL Credit Card Fields] 在儲存配置或支付服務首頁中。 請參閱 [設定](settings.md#credit-card-fields) 以取得更多資訊。

您也可以變更信用卡欄位的版面、寬度、高度和外部樣式。 請參閱 [PayPal檔案](https://developer.paypal.com/docs/checkout/advanced/customize/card-field-style/) 以取得更多資訊。

## [!DNL PayPal Smart Buttons]

[!DNL PayPal Smart Buttons],PayPal可完成購買、儲存購物者的運送地址、帳單地址和付款詳細資訊以供日後使用。 購物者可使用PayPal先前儲存或提供的任何付款方法。

![[!DNL PayPal Smart Buttons] 選項](assets/buttons-md.png)

您可以設定 [!UICONTROL PayPal Smart Buttons] 在儲存配置或支付服務首頁中。  請參閱 [設定](settings.md#payment-buttons) 以取得更多資訊。

### [!DNL PayPal] 按鈕

客戶可以使用PayPal按鈕輕鬆而放心地結帳。

此 [!DNL PayPal] 按鈕可從產品頁面、迷你購物車、購物車和結帳檢視中顯示。

### [!DNL Venmo] 按鈕

客戶可以使用 [文莫](https://venmo.com/) 按鈕。

此 [!DNL Venmo] 按鈕可從產品頁面、迷你購物車、購物車和結帳檢視中顯示。

### [!DNL Apple Pay] 按鈕

客戶可在其裝置上使用觸控式ID，以使用 [[!DNL Apple Pay]](https://www.apple.com/apple-pay/)，會利用儲存在其iOS或macOS裝置上的信用卡和借記卡付款憑證。

此 [!DNL Apple Pay] 按鈕可從產品頁面、迷你購物車、購物車和結帳檢視中顯示。

>[!NOTE]
>
> 若要使用Apple Pay，請連絡您的銷售代表或Adobe帳戶團隊，為您的即時商店啟用它。

### [!DNL Pay Later] 按鈕

為您的客戶提供短期、免息付款和其他融資選項，以便他們現在購買並稍後使用 [!DNL Pay Later] 按鈕。

此 [!DNL Pay Later] 按鈕可從產品頁面、迷你購物車、購物車和結帳檢視中顯示：

* **當客戶選擇介於$30和$600之間的產品時**，在PayPal和 [!DNL Pay Later] 按鈕可讓客戶進一步了解 [!DNL Pay in 4] 付款選項。 客戶可按一下 **深入了解** 了解「[!DNL Pay in 4]&quot;選項 _或_ 按一下彈出式功能表中的「或查看6個月特殊融資」文字，了解並套用PayPal信用選項。
* **當客戶選擇的產品或產品超過$98.99時**，在PayPal和 [!DNL Pay Later] 按鈕為客戶提供了有關PayPal信用付款選項的更多資訊。 客戶可按一下 **深入了解** 要了解並申請PayPal信用選項， _或_ 按一下彈出式功能表中的「或查看4中的付費」文字，了解 [!DNL Pay in 4] 選項。

   >[!NOTE]
   >
   >上述金額可能有所變動。

請參閱 [設定](settings.md#payment-buttons) 了解如何停用/啟用 [!DNL Pay Later] 傳訊。

有兩個付款選項 [!DNL Pay Later] 按鈕：

* **4分** — 客戶可在首次首付後，以四次免息付款（每兩週）支付訂單餘額。 請參閱 [4份文檔](https://www.paypal.com/us/digital-wallet/ways-to-pay/buy-now-pay-later) 以取得更多資訊。
* **PayPal信用** — 客戶可以在6個月內全額支付訂單餘額，無息。 請參閱 [PayPal信用文檔](https://www.paypal.com/us/webapps/mpp/paypal-credit) 以取得更多資訊。

### [!DNL Pay Now] 按鈕

此 [!DNL Pay Now] 當客戶按一下付款螢幕上的付款按鈕時，按鈕將顯示在PayPal彈出窗口中。

如果最終訂單金額尚未知（例如，您尚未取得運送地址資訊時），且客戶正在從產品頁面、迷你購物車或購物車結帳， _繼續_ 按鈕。 客戶點按 _繼續_，在他們確認其付款方法後，會將他們導向至訂單審核頁面，以在結帳前收集所需的詳細資訊。

## 重新計算訂單

當客戶從迷你購物車、購物車或產品頁面進入結帳流程時，系統會將其導向至訂單審核頁面，客戶可在PayPal快顯視窗中查看所選的運送地址。 在客戶選擇發運方法後，將適當地重新計算訂單金額，客戶可以查看發運成本和稅。

當客戶從結帳頁面進入結帳流程時，系統已知出貨地址和最終計算金額，且總計會適當顯示。

免稅期、運費和銷售稅因地點而異。 之後 [!DNL Payment Services] 接收發運地址和費率後，它會快速重新計算所有適用的成本，並在最後的結帳階段適當顯示這些成本。

## 從產品頁面結帳

當客戶直接從產品頁面結帳時，請使用PayPal或 [!DNL Pay Later] 按鈕，則僅購買當前產品頁面中表示的項目。 已駐留在客戶購物車中的項目不會新增至結帳流程，也不會購買。

如果客戶取消訂單，則當前產品頁面中的項目將添加到客戶的購物車中，並加入購物車中出現的任何其他項目。 此功能可讓客戶快速購買目前檢視的項目，同時保留先前在瀏覽產品時新增至購物車的任何其他項目。

當客戶從產品頁面進入結帳流程時，結帳頁面會簡化，檢視只會顯示與訂單相關的資料和選項。

## 信用卡保險

購物者可以在網站層級（同一商家帳戶內的任何商店）保管其信用卡資訊，以供日後購買。

請參閱 [信用卡保險](vaulting.md) 以取得更多資訊。

## 安全性

請參閱 [PCI合規性](security.md#pci-compliance) 以取得更多資訊。
