---
title: 付款選項
description: 設定付款選項以自定義可用於商店客戶的方法。
exl-id: 95e648e6-6cb8-4226-b5ea-e1857212f20a
source-git-commit: 9bc392f2ae12269ded6174b830562444d6827f5f
workflow-type: tm+mt
source-wordcount: '1041'
ht-degree: 0%

---

# 付款選項

與 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] [!DNL Payment Services]，您可以使用多個付款選項。 您可以通過以下方式配置這些付款選項：

* [首頁設定](payments-home.md)
* [儲存配置](configure-admin.md) （建議使用舊式付款選項或多商店設定）

根據您在結帳流程中的位置，每種付款方式有不同的行為：

* 產品頁 — 物料的產品頁
* 迷你購物車 — 在將產品添加到購物車中時，按一下購物車表徵圖可用
* 購物車 — 按一下時可用 _查看和編輯購物車_ 從小車上
* 檢出視圖(Checkout view) — 按一下時可用 _繼續簽出_ 從小車或購物車

>[!IMPORTANT]
>
>在處理付款之前，必須先完成登機付款服務。

## [!UICONTROL Credit Card Fields]

[!UICONTROL Credit Card Fields] 為信用卡或借記卡付款方法提供簡單而安全的結帳。 當購物者使用信用卡欄位簽出時，他們會輸入自己的姓名、帳單地址以及信用卡或借記卡資訊，以下單。 客戶資訊在購買會話期間被安全地使用，以無縫地引導客戶通過結帳流程。

啟用 [信用卡保險](#vaulting) 讓購物者能夠保存（保存）他們的信用卡資訊，以便以後快速結帳。

您可以配置 [!UICONTROL Credit Card Fields] 在儲存配置或支付服務主目錄中。 請參閱 [設定](settings.md#credit-card-fields) 的子菜單。

您還可以更改信用卡欄位的佈局、寬度、高度和外部樣式。 請參閱 [PayPal文檔](https://developer.paypal.com/docs/checkout/advanced/customize/card-field-style/) 的子菜單。

## [!DNL PayPal Smart Buttons]

[!DNL PayPal Smart Buttons]使用PayPal完成購買，儲存購物者的送貨地址、帳單地址和付款詳細資訊以供以後使用。 購物者可以使用PayPal以前儲存或提供的任何支付方式。

![[!DNL PayPal Smart Buttons] 選項](assets/buttons-md.png)

您可以配置 [!UICONTROL PayPal Smart Buttons] 在儲存配置或支付服務主目錄中。  請參閱 [設定](settings.md#payment-buttons) 的子菜單。

### [!DNL PayPal] 按鈕

客戶可以使用PayPal按鈕輕鬆、自信地結賬。

的 [!DNL PayPal] 按鈕可從產品頁面、迷你購物車、購物車和結帳視圖中看到。

### [!DNL Venmo] 按鈕

客戶可以使用 [文莫](https://venmo.com/) 按鈕

的 [!DNL Venmo] 按鈕可從產品頁面、迷你購物車、購物車和結帳視圖中看到。

### [!DNL Apple Pay] 按鈕

客戶可以在其設備上使用Touch ID [[!DNL Apple Pay]](https://www.apple.com/apple-pay/)它使用儲存在其iOS或macOS設備上的信用卡和借記卡付款憑證。

的 [!DNL Apple Pay] 按鈕可從產品頁面、迷你購物車、購物車和結帳視圖中看到。

>[!NOTE]
>
> 要使用 [!DNL Apple Pay] 對於您的商店，完成 [自註冊 [!DNL Apple Pay]](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) (_註冊您的活動域_ 僅限部分和 [將其配置為 [!DNL Payment Services]](settings.md#payment-buttons)。

### [!DNL Pay Later] 按鈕

為您的客戶提供短期、免息的付款和其他融資選項，以便他們可以立即購買並隨後使用 [!DNL Pay Later] 按鈕

的 [!DNL Pay Later] 按鈕可從產品頁面、迷你購物車、購物車和結帳視圖中看到：

* **當客戶選擇介於$30到$600之間的產品時**，在PayPal和 [!DNL Pay Later] 按鈕為客戶提供了有關 [!DNL Pay in 4] 付款選項。 客戶可以按一下 **瞭解更多資訊** 瞭解&quot;[!DNL Pay in 4]&quot;選項 _或_ 按一下彈出菜單中的「或查看6個月特殊融資」文本，瞭解並申請PayPal信用選項。
* **當客戶選擇超過$98.99的產品時**，在PayPal和 [!DNL Pay Later] 按鈕可為客戶提供有關PayPal信用付款選項的詳細資訊。 客戶可以按一下 **瞭解更多資訊** 瞭解並申請PayPal信用選項， _或_ 按一下彈出式菜單中的「或查看按4支付」文本，瞭解 [!DNL Pay in 4] 的雙曲餘切值。

   >[!NOTE]
   >
   >上述金額可予更改。

請參閱 [設定](settings.md#payment-buttons) 瞭解如何禁用/啟用 [!DNL Pay Later] 消息。

有兩個付款選項 [!DNL Pay Later] 按鈕：

* **在4內支付** — 客戶在首次首付後可以以四筆免息付款（每兩週）支付訂單餘額。 查看 [按4份文檔支付](https://www.paypal.com/us/digital-wallet/ways-to-pay/buy-now-pay-later) 的子菜單。
* **PayPal信用** — 客戶可以在6個月內全額支付訂單餘額，無息。 查看 [PayPal信用文檔](https://www.paypal.com/us/webapps/mpp/paypal-credit) 的子菜單。

### [!DNL Pay Now] 按鈕

的 [!DNL Pay Now] 當客戶按一下付款螢幕上的付款按鈕時，PayPal彈出窗口中將顯示該按鈕。

如果最終訂單金額尚未知曉（例如，您尚未獲得發運地址資訊時），並且客戶正在從產品頁面、迷你購物車或購物車簽出，則 _繼續_ 按鈕。 當客戶按一下 _繼續_，在確認其付款方式後，他們將被引導至訂單複查頁以在完成結帳之前收集所需的詳細資訊。

## 重新計算訂單

當客戶從mini-cart、購物車或產品頁進入結帳流時，他們將被引導到訂單複查頁，在該頁中，他們可以在PayPal彈出窗口中查看選定的發運地址。 在客戶選擇發運方法後，將相應地重新計算訂單金額，並且客戶可以查看發運成本和稅。

當客戶從結帳頁輸入結帳流時，系統已經知道發運地址和最終計算金額，並且總額會被適當表示。

免稅期、運輸成本和銷售稅因地而異。 之後 [!DNL Payment Services] 接收發運地址和費率後，它會快速重新計算所有適用成本，並在結帳的最後階段適當顯示這些成本。

## 從產品頁面簽出

當客戶直接從產品頁面簽出時，使用PayPal或 [!DNL Pay Later] 按鈕，只購買當前產品頁中表示的項目。 已駐留在客戶購物車中的物料不會添加到結帳流中，也不會購買。

如果客戶取消訂單，則當前產品頁中的物料將添加到客戶的購物車中，並加入購物車中存在的任何其它物料。 此功能允許客戶快速購買他們當前正在查看的項目，同時保留以前在瀏覽產品時添加到購物車中的任何其他項目。

當客戶從產品頁面輸入結帳流時，結帳頁會被簡化 — 該視圖僅顯示與訂單相關的資料和選項。

## 信用卡保險儲存

購物者可以在網站級別（同一商戶帳戶內的任何商店）保存他們的信用卡資訊，以備將來購買。

請參閱 [信用卡保險儲存](vaulting.md) 的子菜單。

## 安全

請參閱 [PCI合規性](security.md#pci-compliance) 的子菜單。
