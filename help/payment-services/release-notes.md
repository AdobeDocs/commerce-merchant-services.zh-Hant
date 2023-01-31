---
title: '"[!DNL Payment Services] 發行說明」'
description: 請參閱發行說明，了解 [!DNL Payment Services] 版本。
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
source-git-commit: 4bd3e4bb791ac3688206dd2d671bae5c47dfa7c8
workflow-type: tm+mt
source-wordcount: '1476'
ht-degree: 0%

---

# 發行說明

以下版本說明的初始版本 [!DNL Payment Services] 包括：

![新增](../assets/new.svg) 新功能
![修正問題](../assets/fix.svg) 修正和改良
![已知問題](../assets/bug.svg) 已知問題

如需在一般版本化功能版本以外發行的功能變更和修正，請參閱托管服務更新區段。

請參閱 [即將發行的版本](https://devdocs.magento.com/release/) 了解發行計畫和支援。

請參閱 [可用性](https://devdocs.magento.com/release/availability.html) 請參閱開發人員檔案，了解產品相容性。

## 托管服務更新

以下版本說明說明已發生且在托管服務的一般版本化功能版本之外發行的功能變更和修正。

+++托管服務更新

_2023年1月25日_

![已知問題](../assets/bug.svg)<!-- Issue PAY-4102 --> 新安裝的Payment Services無法配置Commerce Services，導致Payment Services無法運行。 若要修正此問題，請將您的Payment Services擴充功能更新至1.5.3版。

_2022年9月12日_

![新增](../assets/new.svg)<!-- Issue PAY-3705 --> 此 `increment_id` 現在可用於調節外部ERP系統的支付。 會傳播至 [`custom_id` _和_ `invoice_id`](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/data.html#reconcile-with-erp-system)，可在PayPal網頁鈎點和商家活動詳細資訊中顯示，以支付款項。

_2022年8月31日_

![修正問題](../assets/fix.svg)<!-- Issue PAY-3629 --> 當新商家首次存取「付款服務首頁」時，頁面現在會立即載入以顯示內容，而不需要重新整理頁面。

_2021年8月9日_

![新增](../assets/new.svg)<!-- Issue PAY-3420 --> Apple Pay現在以PayPal智慧按鈕的形式提供。 此 [付款選項](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-options.html#apple-pay-button) 可讓客戶使用其iOS或macOS裝置上的觸控ID功能來選取Apple Pay。 Apple Pay會使用儲存在裝置上的信用卡和借記卡付款憑證來處理付款。

_2021年6月28日_

![新增](../assets/new.svg)<!-- Issue PAY-1720 --> 商店訂單的爭議現在可在 [訂單付款狀態報表](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#view-disputes). 您可以直接從以下位置導覽至PayPal解決中心，以針對爭議採取行動 [!DNL Payment Services].

![新增](../assets/new.svg)<!-- Issue PAY-2854 --> 改善以下項目的使用者體驗： [!DNL Payment Services] 首頁包括在當前繼承級別修改配置的功能，以及改進頭部和導航的顯示。

![新增](../assets/new.svg)<!-- Issue PAY-2854 --> 現在當您從沙箱模式切換至生產模式，以及嘗試從檢視導覽至尚未儲存的更新時，畫面會顯示警告。

![新增](../assets/new.svg)<!-- Issue PAY-2761 --> 您現在可以自訂顯示在 [訂單付款狀態報表](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#show-and-hide-columns) 和 [支付報告](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/payouts.html#show-and-hide-columns) 使用「欄設定」控制項顯示或隱藏欄。

+++

## v1.5.4

_2023年1月29日_

![修正問題](../assets/fix.svg)<!-- Issue PAY-4110 --> 修正購買者無法使用產品頁面、迷你購物車和購物車上的智慧按鈕下單的問題。 買家現在可以成功完成訂單。

## v1.5.3

_2023年1月25日_

![修正問題](../assets/fix.svg)<!-- Issue PAY-4102 --> 已針對不相容的已知問題發行修正。 此版本會將服務ID擴充功能版本鎖定至最新穩定版本，重新啟用新的Payment Services安裝以設定Commerce Services。

## v1.5.2

_2022年12月22日_

![修正問題](../assets/fix.svg)<!-- Issue PAY-3992 --> 改進當拒絕付款方法時在付款服務中的開票。

![修正問題](../assets/fix.svg)<!-- Issue PAY-3999 --> Payment Services現在可正確顯示商戶使用的PayPal智慧按鈕 [引發結帳](https://marketplace.magento.com/swissup-firecheckout.html){target=_blank} 結帳頁面的自訂範本。 以前，迷你圖會間歇性顯示按鈕。

## v1.5.1

_2022年11月23日_

![新增](../assets/new.svg)<!-- Issue PAY-3923 --> Payment Services現在會在使用者代理標題中納入版本號碼，以便要求能夠追蹤、篩選或淘汰未使用的端點。

![修正問題](../assets/fix.svg)<!-- Issue PAY-3968 --> 使用智慧按鈕從產品頁面下訂單時，Payment Services現在可正確顯示訂單資料。

## v1.5.0

_2022年11月18日_

![新增](../assets/new.svg)<!-- Issue PAY-3880 --> 購物者現在可以 [在結帳期間保存其信用卡資訊](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting.html) 用於以後購買同一商家帳戶內的同一商店或其他商店。

![新增](../assets/new.svg)<!-- Issue PAY-3950 --> 商戶現在可以啟用 [即時購買商務功能](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/checkout-instant-purchase.html) 以供購物者(使用 [保險信用卡資訊](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting.html))以加速結帳。

## v1.4.1

_2022年10月14日_

![修正](../assets/fix.svg)<!-- Issue PAY-3766 --> 當客戶的付款方法被拒絕時，可見的錯誤消息將更具描述性。 它建議客戶重新輸入付款資訊，然後重試，嘗試其他付款方法，或聯繫其銀行，了解拒絕的交易。

## v1.4.0

_2022年9月30日_

![新增](../assets/new.svg)<!-- Issue PAY-784 --> 支付服務現在包括設定商家帳戶的能力 [使用多個PayPal業務帳戶](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#use-multiple-paypal-accounts). 這可讓商家使用不同貨幣在多個國家/地區經營您的商店，或將Adobe Commerce用於您的部分業務。

![新增](../assets/new.svg)<!-- Issue PAY-3231 --> 商家可以 [新增 [!UICONTROL Soft Descriptor]](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#add-soft-descriptor) 至網站或個別商店檢視顯示於客戶交易銀行對帳單的設定，以勾勒品牌、商店或產品線。

![新增](../assets/new.svg)<!-- Issue PAY-3707 --> [啟用或禁用信用卡欄位和PayPal智慧按鈕](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#configure-payment-options) ，以在「支付服務」設定中結帳。

![修正問題](../assets/fix.svg)<!-- Issue PAY-3546 --> 客戶點按 **[!UICONTROL Edit cart]**，頁面會重新導向至購物車頁面並顯示更新的項目，而非顯示空的購物車。

## v1.3.1

_2022年9月6日_

![修正問題](../assets/fix.svg)<!-- Issue PAY-3663 --> 現在，當商家的商店擷取授權使用非全域貨幣的訂單時，擷取程式會完成，不會顯示錯誤。

## v1.3.0

_2022年8月9日_

![新增](../assets/new.svg)<!-- Issue PAY-XX --> 正式發行 — [!DNL Payment Services] 現在 [相容 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 版本2.4.0至2.4.5](https://devdocs.magento.com/release/availability.html#compatibility).

![修正問題](../assets/fix.svg)<!-- Issue PAY-x --> Apple Pay現在與行動裝置和案頭版的Safari瀏覽器v15.5相容。

## v1.2.0

_2022年6月29日_

![已知問題](../assets/bug.svg)<!-- Issue PAY-x --> Apple Pay與行動裝置和案頭版上的Safari瀏覽器v15.5不相容。 使用Safari 15.5版時，您無法使用Apple Pay完成結帳。

![修正問題](../assets/fix.svg)<!-- Issue PAY-3264 --> 以前，當登入的使用者為其帳戶選取了其他帳單/運送位址，而非預設位址時，結帳失敗。 我們已修正此問題，現在已傳送選取的帳單/運送地址（而非預設的儲存地址），結帳已成功完成。

![修正問題](../assets/fix.svg)<!-- Issue PAY-3314 --> 如果您停用結帳的PayPal智慧按鈕，則不會顯示錯誤。

![修正問題](../assets/fix.svg)<!-- Issue PAY-3330 --> 當來賓用戶輸入包含破折號的電話號碼時，付款在結帳期間不再失敗。

![修正問題](../assets/fix.svg)<!-- Issue PAY-3338 PAY-2502 --> 當商務服務憑據無效時， [!DNL Payment Services] 首頁現在會顯示在管理員中。 出現憑證錯誤，提醒您您的憑證無效。

![已知問題](../assets/bug.svg)<!-- Issue PAY-0 --> [!DNL Payment Services] 目前與不相容 `commerce-data-export` v101.20及更新版本，因此與 [[!DNL Channel manager] 擴充功能](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/guide-overview.html).

## v1.1.0

_2022年3月31日_

![新增](../assets/new.svg)<!-- Issue PAY-2127 --> 正式發行 — [!DNL Payment Services] 現在 [相容 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 版本2.4.0至2.4.4](https://devdocs.magento.com/release/availability.html#compatibility).

![新增](../assets/new.svg)<!-- Issue PAY-2682 --> 此 [!DNL Payment Services] 擴充功能 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 現在可供加拿大商人使用。 商戶可以在以下任一 [法文](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html?lang=fr#carte-de-cr%C3%A9dit-et-devises-accept%C3%A9es) 或 [英文](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html#accepted-credit-cards-and-currencies).

![新增](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] 支援 [加元(CAD)](overview.md#accepted-credit-cards-and-currencies) 信用卡和PayPal交易。

![新增](../assets/new.svg)<!-- Issue PAY-2680 --> 商家可以 [板載 [!DNL Payment Services]](onboard.md) 擴充功能使用英文或法文。

![新增](../assets/new.svg)<!-- Issue PAY-2678 --> 商戶現在可以檢視財務報表，兩者 [訂單付款狀態](order-payment-status.md) 和 [支付報告](payouts.md)，加元(CAD)。

![修正問題](../assets/fix.svg)<!-- Issue PAY-2710 --> [!DNL Payment Services] 現在與 [PHP 8.1](https://www.php.net/releases/8.1/en.php).

![修正問題](../assets/fix.svg)<!-- Issue PAY-3017 --> 改善沙箱模式警報，可顯示具有多個存放區的適當警報。

![修正問題](../assets/fix.svg)<!-- Issue PAY-2742 --> 您現在可以在商店檢視層級啟用和停用可用的付款方法，例如Venmo。 以前，您只能根據網站設定付款方法。

![修正問題](../assets/fix.svg)<!-- Issue PAY-2277 --> 您現在可以有選擇地 [啟用或禁用單個PayPal智慧按鈕](settings.md#payment-buttons).

![修正問題](../assets/fix.svg)<!-- Issue PAY-2561 --> 先前移除的產品不會出現在購物車上 _審核訂單_ 頁面。

![已知問題](../assets/bug.svg)<!-- Issue PAY-2842 --> 測試信用卡交易記錄 [可能因PayPal而失敗](https://support.magento.com/hc/en-us/articles/5201041963917) 在沙箱環境中處理付款時。

## v1.0.0

_2021年11月29日_

![新增](../assets/new.svg)<!-- Issue PAY-2127 --> 正式發行 — [[!DNL Payment Services]](https://marketplace.magento.com/magento-payment-services.html) 現在與 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 2.4.0版至2.4.3-p1版。

![新增](../assets/new.svg)<!-- Issue PAY-124 --> 此 [!DNL Payment Services] 擴充功能 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 可為 [[!DNL Adobe Commerce] 雲基礎架構](install.md#adobe-commerce-on-cloud-infrastructure) 或 [內部部署](install.md#on-premises) 例項。 這些方法需要使用命令行介面。

![新增](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] 支援a [沙箱帳戶](sandbox.md) 可讓商戶在測試模式中評估擴充功能。

![新增](../assets/new.svg)<!-- Issue PAY-666 --> 商家可以 [配置支付服務](settings.md) 具有基本支付行為的擴展，例如利用 [`Authorize and Capture`](production.md#set-payment-services-as-payment-method) 在沙箱或生產環境之間切換。

![新增](../assets/new.svg)<!-- Issue PAY-780 --> 您的購物者可以 [!DNL Payment Services] 或 [手動訂單建立](create-order.md).

![新增](../assets/new.svg)<!-- Issue PAY-1856 --> 全面報告，通過 [訂單付款狀態](order-payment-status.md) 和 [支付報告](payouts.md)，可供 [!DNL Payment Services] 讓您清楚了解您商店的訂單和相關付款。

![新增](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] 支援基於總處理量的靈活分層定價，適用於任何商家。

![新增](../assets/new.svg)<!-- Issue PAY-1443 --> 您可以輕鬆 [自訂外觀和風格](payments-options.md) 的PayPal智慧按鈕和信用卡欄位 [!DNL Payment Services] 擴充功能。

![已知問題](../assets/bug.svg)<!-- Issue PAY-2473 --> 使用 [撰寫器密鑰不正確](https://support.magento.com/hc/en-us/articles/4406603542541) 在安裝擴充功能期間，使用者無法 [驗證](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 正確 `MAGEID`.

![已知問題](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] 報告 [不能立即同步](https://support.magento.com/hc/en-us/articles/4406114741517).

![已知問題](../assets/bug.svg)<!-- Issue PAY-2475 --> 您的 [PayPal沙箱帳戶](https://support.magento.com/hc/en-us/articles/4406954952461) for [!DNL Payment Services] 如果您在上線期間建立該帳戶，則無法驗證。
