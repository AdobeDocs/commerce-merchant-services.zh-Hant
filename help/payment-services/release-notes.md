---
title: '"[!DNL Payment Services] 發行說明」'
description: 查看發行說明以瞭解有關所有 [!DNL Payment Services] 版本。
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
source-git-commit: e076864a117be007eeb8003d9d6a472b704996ba
workflow-type: tm+mt
source-wordcount: '1758'
ht-degree: 0%

---

# 發行說明

本發行說明描述了 [!DNL Payment Services] 包括：

![新建](../assets/new.svg) 新功能
![已修復問題](../assets/fix.svg) 修復和改進
![已知問題](../assets/bug.svg) 已知問題

有關在常規版本控制功能版本之外發佈的功能更改和修復，請參閱「托管服務更新」部分。

請參閱 [即將發佈的版本](https://devdocs.magento.com/release/) 瞭解發行計畫和支援。

請參閱 [可用性](https://devdocs.magento.com/release/availability.html) 以瞭解產品相容性。

## 托管服務更新

這些發行說明描述了在托管服務的常規版本控制功能版本之外所發生和發佈的功能更改和修復。

+++托管服務更新

_2023年1月25日_

![已知問題](../assets/bug.svg)<!-- Issue PAY-4102 --> Payment Services的新安裝無法配置Commerce Services，使Payment Services無法運行。 要解決此問題，請將Payment Services擴展更新為1.5.3版。

_2022年9月12日_

![新建](../assets/new.svg)<!-- Issue PAY-3705 --> 的 `increment_id` 現在可用於調節外部ERP系統的支出。 它傳播到 [`custom_id` _和_ `invoice_id`](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/data.html#reconcile-with-erp-system)，在PayPal網頁掛接和支付的商家活動詳細資訊中都可見。

_2022年8月31日_

![已修復問題](../assets/fix.svg)<!-- Issue PAY-3629 --> 當新商戶首次訪問付款服務首頁時，該頁面現在會立即載入以顯示內容，而不需要刷新頁面。

_2021年8月9日_

![新建](../assets/new.svg)<!-- Issue PAY-3420 --> Apple支付現已作為PayPal智慧按鈕提供。 此 [付款選項](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-options.html#apple-pay-button) 使客戶能夠在其iOS或macOS設備上使用觸摸ID功能來選擇Apple支付。 Apple支付使用儲存在設備上的信用卡和借記卡付款憑證處理付款。

_2021年6月28日_

![新建](../assets/new.svg)<!-- Issue PAY-1720 --> 商店訂單的爭議現可在 [訂單付款狀態報表](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#view-disputes)。 您可以通過直接導航至PayPal解決中心，對爭議採取行動 [!DNL Payment Services]。

![新建](../assets/new.svg)<!-- Issue PAY-2854 --> 用戶體驗改進 [!DNL Payment Services] 首頁包括修改當前繼承級別上的配置的功能，以及對標題和導航顯示的改進。

![新建](../assets/new.svg)<!-- Issue PAY-2854 --> 現在，當您從沙盒模式切換到生產模式，以及您嘗試使用尚未保存的更新從視圖中導航時，您可以看到警告。

![新建](../assets/new.svg)<!-- Issue PAY-2761 --> 現在，您可以自定義 [訂單付款狀態報表](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#show-and-hide-columns) 和 [支付報告](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/payouts.html#show-and-hide-columns) 使用「列設定」控制項顯示或隱藏列。

+++

## v2.0.0

_2023年3月10日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg)<!-- Issue PAY-4152 --> 又支援八點二菲律賓比索和Adobe Commerce2.4.6。與PHP 7.x不相容。

## v1.6.1

_2023年3月10日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![修復](../assets/fix.svg)<!-- Issue PAY-4226 --> 已修復阻止新Payment Services商戶在管理員中使用結帳的問題。 Payment Services以前使用的是Commerce客戶ID，新客戶不存在該ID。

![修復](../assets/fix.svg)<!-- Issue PAY-4205 --> 已修復在使用 [PayPal選項](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#paypal-smart-buttons)。 現在，客戶可以將其訂單發運至除在商家稅收設定中配置為預設狀態之外的其他狀態。

![修復](../assets/fix.svg)<!-- Issue PAY-4202 --> 解決了防止客戶使用卡保險儲存完成購買或刪除商店的保險支付方法的問題 [使用 `Authorize and Capture` 付款操作](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/production.html#set-payment-services-as-payment-method)。 以前，當客戶嘗試使用或修改其保險儲存卡時，出現「找不到供應商保管庫ID」錯誤。

## v1.6.0

_2023年2月17日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg)<!-- Issue PAY-3540 --> 已添加 [歐盟(EU)和英國的商家交易的PCI 3DS合規性功能](security.md#3ds)。 這一額外的安全層要求買家向其信用卡發行商進行身份驗證，有助於防止線上欺詐，並且是歐盟（歐盟）合規條例的一部分。

![新建](../assets/new.svg)<!-- Issue PAY-3609 --> 已添加 [啟用管理員卡保險儲存](vaulting.md#use-vaulting-in-the-admin)。 這允許商家使用其拱形付款方法為管理員中的客戶建立訂單。

## v1.5.4

_2023年1月29日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![已修復問題](../assets/fix.svg)<!-- Issue PAY-4110 --> 修復了使用產品頁、迷你購物車和購物車上的智慧按鈕阻止買家下訂單的問題。 買家現在可以成功完成訂單。

## v1.5.3

_2023年1月25日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![已修復問題](../assets/fix.svg)<!-- Issue PAY-4102 --> 已針對向後不相容的已知問題釋放修復。 此版本將服務ID擴展版本鎖定到最新的穩定版本，從而重新啟用新的Payment Services安裝以配置Commerce Services。

## v1.5.2

_2022年12月22日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![已修復問題](../assets/fix.svg)<!-- Issue PAY-3992 --> 當拒絕付款方法時，付款服務中的開票改進。

![已修復問題](../assets/fix.svg)<!-- Issue PAY-3999 --> Payment Services現在正確顯示商戶使用的PayPal智慧按鈕 [Fire Checkout的](https://marketplace.magento.com/swissup-firecheckout.html){target=_blank} 簽出頁的自定義模板。 以前，迷你圖間歇性地顯示按鈕。

## v1.5.1

_2022年11月23日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg)<!-- Issue PAY-3923 --> Payment Services現在在用戶代理標頭中包含版本號，以便能夠跟蹤、篩選或棄用未使用的終結點。

![已修復問題](../assets/fix.svg)<!-- Issue PAY-3968 --> 當使用智慧按鈕從產品頁面下達訂單時，Oracle Payment Services現在可以正確顯示訂單資料。

## v1.5.0

_2022年11月18日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg)<!-- Issue PAY-3880 --> 購物者現在可以 [保管庫（在結帳期間保存其信用卡資訊）](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting.html) 在以後的購買中用於同一商戶帳戶內的相同或其他商店。

![新建](../assets/new.svg)<!-- Issue PAY-3950 --> 商家現在可以啟用 [即時採購商務功能](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/checkout-instant-purchase.html) 供購物者使用 [保險信用卡資訊](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting.html))以加快結帳。

## v1.4.1

_2022年10月14日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![修復](../assets/fix.svg)<!-- Issue PAY-3766 --> 當客戶的付款方式被拒絕時，可見的錯誤消息將更具描述性。 它建議客戶重新輸入付款資訊並重試、嘗試其他付款方法或聯繫其銀行有關已拒絕交易的資訊。

## v1.4.0

_2022年9月30日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg)<!-- Issue PAY-784 --> 支付服務現在包括將商戶帳戶設定為 [使用多個PayPal業務帳戶](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#use-multiple-paypal-accounts)。 這使商家能夠使用不同貨幣在多個國家/地區經營您的商店，或將Adobe Commerce用於您的部分業務。

![新建](../assets/new.svg)<!-- Issue PAY-3231 --> 商家可以 [添加 [!UICONTROL Soft Descriptor]](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#add-soft-descriptor) 顯示在客戶交易銀行對帳單上的網站或單個商店視圖配置，以勾勒品牌、商店或產品線。

![新建](../assets/new.svg)<!-- Issue PAY-3707 --> [啟用或禁用信用卡欄位和PayPal智慧按鈕](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#configure-payment-options) 在付款服務設定中籤出。

![已修復問題](../assets/fix.svg)<!-- Issue PAY-3546 --> 當客戶按一下 **[!UICONTROL Edit cart]**，該頁面將重定向到購物車頁面並顯示更新的項目，而不是顯示空購物車。

## v1.3.1

_2022年9月6日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![已修復問題](../assets/fix.svg)<!-- Issue PAY-3663 --> 現在，當商家商店捕獲使用非全局貨幣授權的訂單時，捕獲過程將完成，不會顯示任何錯誤。

## v1.3.0

_2022年8月9日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg)<!-- Issue PAY-XX --> 一般可用性發佈 — [!DNL Payment Services] 現在 [相容 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 版本2.4.0至2.4.5](https://devdocs.magento.com/release/availability.html#compatibility)。

![已修復問題](../assets/fix.svg)<!-- Issue PAY-x --> Apple支付現在與移動和案頭上的Safari瀏覽器v15.5相容。

## v1.2.0

_2022年6月29日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![已知問題](../assets/bug.svg)<!-- Issue PAY-x --> Apple支付與移動和案頭上的Safari瀏覽器v15.5不相容。 使用Safari 15.5版時，您無法使用Apple支付完成結帳。

![已修復問題](../assets/fix.svg)<!-- Issue PAY-3264 --> 以前，當登錄用戶為其帳戶選擇了除預設地址之外的其他計費/發運地址時，簽出失敗。 我們解決了此問題，現在已發送選定的開單/發運地址（而不是預設保存的地址），並且結帳已成功完成。

![已修復問題](../assets/fix.svg)<!-- Issue PAY-3314 --> 如果禁用PayPal智慧按鈕進行簽出，則不顯示任何錯誤。

![已修復問題](../assets/fix.svg)<!-- Issue PAY-3330 --> 當來賓用戶輸入包含短划線的電話號碼時，付款在結帳期間不再失敗。

![已修復問題](../assets/fix.svg)<!-- Issue PAY-3338 PAY-2502 --> 當Commerce Services憑據無效時， [!DNL Payment Services] 現在，首頁將出現在管理員中。 出現憑據錯誤，警告您憑據無效。

![已知問題](../assets/bug.svg)<!-- Issue PAY-0 --> [!DNL Payment Services] 當前與不相容 `commerce-data-export` v101.20及更高版本，使其與 [[!DNL Channel manager] 擴展](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/guide-overview.html)。

## v1.1.0

_2022年3月31日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg)<!-- Issue PAY-2127 --> 一般可用性發佈 — [!DNL Payment Services] 現在 [相容 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 版本2.4.0至2.4.4](https://devdocs.magento.com/release/availability.html#compatibility)。

![新建](../assets/new.svg)<!-- Issue PAY-2682 --> 的 [!DNL Payment Services] 擴展 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 現在可供加拿大商家使用。 商家可以查看其中任何一個 [法語](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html?lang=fr#carte-de-cr%C3%A9dit-et-devises-accept%C3%A9es) 或 [英語](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html#accepted-credit-cards-and-currencies)。

![新建](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] 支援 [加元](overview.md#accepted-credit-cards-and-currencies) 信用卡和PayPal交易。

![新建](../assets/new.svg)<!-- Issue PAY-2680 --> 商家可以 [板 [!DNL Payment Services]](onboard.md) 英文或法文的分機。

![新建](../assets/new.svg)<!-- Issue PAY-2678 --> 商戶現在可以查看財務報表， [訂單付款狀態](order-payment-status.md) 和 [支付報告](payouts.md)，以加元表示。

![已修復問題](../assets/fix.svg)<!-- Issue PAY-2710 --> [!DNL Payment Services] 現在與 [八點一菲律賓比索](https://www.php.net/releases/8.1/en.php)。

![已修復問題](../assets/fix.svg)<!-- Issue PAY-3017 --> 改進的沙盒模式警報，可顯示具有多個儲存的正確警報。

![已修復問題](../assets/fix.svg)<!-- Issue PAY-2742 --> 您現在可以在商店視圖層啟用和禁用可用的付款方法（如Venmo）。 以前，您只能按網站配置付款方式。

![已修復問題](../assets/fix.svg)<!-- Issue PAY-2277 --> 你現在可以選擇 [啟用或禁用單個PayPal智慧按鈕](settings.md#payment-buttons)。

![已修復問題](../assets/fix.svg)<!-- Issue PAY-2561 --> 以前刪除的產品不會出現在購物車中 _審閱訂單_ 的子菜單。

![已知問題](../assets/bug.svg)<!-- Issue PAY-2842 --> Test信用卡交易記錄 [可能因PayPal而失敗](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-cc-sandbox-failure.html) 在沙箱環境中處理付款時。

## v1.0.0

_2021年11月29日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg)<!-- Issue PAY-2127 --> 一般可用性發佈 — [[!DNL Payment Services]](https://marketplace.magento.com/magento-payment-services.html) 現在與 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 版本2.4.0到2.4.3-p1。

![新建](../assets/new.svg)<!-- Issue PAY-124 --> 的 [!DNL Payment Services] 擴展 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 可以安裝 [[!DNL Adobe Commerce] 雲基礎架構](install.md#adobe-commerce-on-cloud-infrastructure) 或 [內部](install.md#on-premises) 實例。 這些方法需要使用命令行介面。

![新建](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] 支援 [沙盒帳戶](sandbox.md) 允許商戶在test模式下評估擴展。

![新建](../assets/new.svg)<!-- Issue PAY-666 --> 商家可以 [配置Payment Services](settings.md) 基本支付行為的擴展 [`Authorize and Capture`](production.md#set-payment-services-as-payment-method) 在沙盒或生產環境之間切換。

![新建](../assets/new.svg)<!-- Issue PAY-780 --> 您的購物者可以 [!DNL Payment Services] 或 [手動訂單建立](create-order.md)。

![新建](../assets/new.svg)<!-- Issue PAY-1856 --> 全面報告，通過 [訂單付款狀態](order-payment-status.md) 和 [支付報告](payouts.md)，可用於 [!DNL Payment Services] 讓你清楚地瞭解你商店的訂單和相關付款。

![新建](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] 支援基於總處理量的靈活分層定價，適用於任何商家。

![新建](../assets/new.svg)<!-- Issue PAY-1443 --> 您可以輕鬆 [定制外觀](payments-options.md) 的PayPal智慧按鈕和信用卡欄位 [!DNL Payment Services] 擴展。

![已知問題](../assets/bug.svg)<!-- Issue PAY-2473 --> 使用 [合成器密鑰不正確](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-install.html) 在安裝擴展時防止用戶 [驗證](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 正確 `MAGEID`。

![已知問題](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] 報告 [無法立即同步](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-report-info-delayed.html)。

![已知問題](../assets/bug.svg)<!-- Issue PAY-2475 --> 您 [PayPal沙盒帳戶](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-paypal-acct.html) 為 [!DNL Payment Services] 如果在登錄期間建立該帳戶，則無法驗證。
