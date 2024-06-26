---
title: '"[!DNL Payment Services] 發行說明」'
description: 檢閱發行說明以瞭解全部資訊 [!DNL Payment Services] 發行版本。
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
feature: Payments, Release Notes
source-git-commit: 9b4ce379728b126390177d64c10d57b2c587619c
workflow-type: tm+mt
source-wordcount: '2502'
ht-degree: 0%

---

# 發行說明

以下版本說明說明的初始版本 [!DNL Payment Services] 並包含：

![新增](../assets/new.svg) 新功能
![已修正的問題](../assets/fix.svg) 修正和改良
![已知問題](../assets/bug.svg) 已知問題

如需在功能發行版本之外發行的功能變更和修正，請檢閱 _託管服務更新_ 區段。

進一步瞭解即將發行的版本、產品支援，以及哪些Adobe Commerce版本支援 [!DNL Payment Services] 擴充功能，請參閱Adobe Commerce [發行排程](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/schedule) 和 [產品可用性](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability) 主題。

## 託管服務更新

這些發行說明說明說明所發生的功能變更和修正，這些變更和修正是在託管服務的定期功能發行之外發行的。

+++託管服務更新

_2024年3月5日_

![已修正的問題](../assets/fix.svg)<!-- Issue PAY-5252 --> 現在，商家可以選取單一儲存格的內容，從「控制面板」網格複製資料。

_2023年10月10日_

![新問題](../assets/fix.svg)<!-- Issue PAY-4888 --> 現在，商家可以篩選信用卡與借記卡交易，篩選條件為 [交易報表](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/transactions.html).

_2023年7月12日_

![已修正的問題](../assets/fix.svg)<!-- Issue PAY-4587 --> 中引入的問題 [!DNL Payment Services] 2.1.0版已解決舊版擴充功能所導致的授權無效問題。 使用任何版本的商家 [!DNL Payment Services] 會使授權失效。

_2023年6月9日_

![新增](../assets/new.svg)<!-- Issue PAY-4288 --> 現在，商家可以 [設定 _僅限_ PayPal付款按鈕](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#use-only-paypal-payment-buttons) — 和 _非_ 使用PayPal信用卡付款選項。 這可讓商家提供各種付款選項，包括Venmo和PayPal付款按鈕，並使用現有的信用卡提供者，而非PayPal信用卡付款選項。

![新增](../assets/new.svg)<!-- Issue PAY-4050 --> 已新增 [資料視覺效果檢視](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#order-payment-status-data-visualization-view)，此頁面會顯示在「付款服務首頁」的「訂單付款狀態」報表中。

![已修正的問題](../assets/fix.svg)<!-- Issue PAY-4486--> 之前，PayPal PayLater按鈕未出現在英國商家的結帳中。 該問題已解決。

![已修正的問題](../assets/fix.svg)<!-- Issue PAY-4485--> 報表資料視覺效果檢視現在顯示於 [!DNL Payment Services] 首頁時間[!DNL Payment Services] 已停用。

_2023年1月25日_

![已知問題](../assets/bug.svg)<!-- Issue PAY-4102 --> 全新安裝 [!DNL Payment Services] 無法設定Commerce服務，轉譯 [!DNL Payment Services] 無法操作。 若要修正此問題，請更新您的 [!DNL Payment Services] 擴充功能至1.5.3版。

_2022年9月12日_

![新增](../assets/new.svg)<!-- Issue PAY-3705 --> 此 `increment_id` 現在可用於調節外部ERP系統中的付款。 它會傳播至 [`custom_id` _和_ `invoice_id`](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/data.html#reconcile-with-erp-system)，可在PayPal webhook和商家活動詳細資訊中看到賠付。

_2022年8月31日_

![已修正的問題](../assets/fix.svg)<!-- Issue PAY-3629 --> 當新商家存取 [!DNL Payment Services] 首頁，頁面現在會立即載入以顯示內容，而不需要重新整理頁面。

_2021年8月9日_

![新增](../assets/new.svg)<!-- Issue PAY-3420 --> Apple Pay現在能以PayPal智慧型按鈕形式使用。 這個 [付款選項](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-options.html#apple-pay-button) 可讓客戶在其iOS或macOS裝置上使用觸控式ID功能，以選取Apple Pay。 Apple Pay會使用儲存在裝置上的信用卡和扣帳卡付款憑證來處理付款。

_2021年6月28日_

![新增](../assets/new.svg)<!-- Issue PAY-1720 --> 商店訂單的糾紛現在可在 [訂單付款狀態報表](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#view-disputes). 您可以直接從導覽至PayPal解決中心，解決爭議 [!DNL Payment Services].

![新增](../assets/new.svg)<!-- Issue PAY-2854 --> 來自以下專案的使用者體驗改善： [!DNL Payment Services] 首頁包含了在目前繼承層級修改設定的能力，並改善了標題和導覽的顯示方式。

![新增](../assets/new.svg)<!-- Issue PAY-2854 --> 現在，當您從沙箱模式切換到生產模式，並嘗試離開檢視且有尚未儲存的更新時，您會看到警告。

![新增](../assets/new.svg)<!-- Issue PAY-2761 --> 您現在可以自訂顯示在 [訂單付款狀態報表](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#show-and-hide-columns) 和 [付款報表](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/payouts.html#show-and-hide-columns) 使用「欄」設定控制項來顯示或隱藏欄。

+++

## v2.6.0

_2024年6月4日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg)<!-- PAY-4877 --> 現在， [!DNL Payment Services] 支援 [L2/L3定價功能](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/levels-card-payment-transactions.html). 此功能僅適用於 [!DNL Payment Services] 已啟用IC++定價的客戶。 如果您想要使用L2/L3處理資料 [!DNL Payment Services]，請聯絡您的 [!DNL Payment Services] 客戶經理。

![修正](../assets/fix.svg)<!-- PAY-5455 -->[!DNL Payment Services] 可讓您直接從擴充功能啟用Apple Pay，而不需下載及託管 [網域關聯檔案](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain).

## v2.5.0

_2024年4月23日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![修正](../assets/fix.svg)<!-- Issue PAY-5396 -->[!DNL Payment Services] 現在支援 [Adobe Commerce指南 `--db-prefix` 引數](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/advanced#install-from-the-command-line) 適用於Adobe Commerce 2.4.7版及更新版本。

## v2.4.3

_2024年4月16日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![修正](../assets/fix.svg)<!-- Issue PAY-5106 --> 修正在PayPal和Adobe Commerce之間結帳時錯誤填入訂單金額總計的問題。 現在，商家可以在下訂單時確保訂單金額總計正確無誤。

## v2.4.2

_2024年4月11日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg)<!-- Issue xxx --> 新增對Adobe Commerce 2.4.7的支援。

## v2.4.1

_2024年4月4日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![修正](../assets/fix.svg)<!-- PAY-5322 --> 已修正較新Adobe Commerce版本的PCI相容性問題。 現在， [!DNL Payment Services] 以付款選項形式調整以符合Adobe Commerce的結帳要求。

![修正](../assets/fix.svg)<!-- PAY-5323 --> PayLater和Venmo可正確顯示在Adobe Commerce中。 修正管理員無法顯示PayLater和Venmo切換選項的錯誤。

## v2.4.0

_2024年3月20日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg)<!-- PAY-4868 --> 商家可以成功 [在購買體驗中設定Google Pay](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html)，類似於中的其他付款按鈕[!DNL Payment Services] 透過Admin.

![新增](../assets/new.svg)<!-- PAY-4381 --> [支付服務透過GraphQL支援Google Pay](https://developer.adobe.com/commerce/webapi/graphql/payment-services/) 可讓商家透過Google Pay支付方式取得Headless Commerce體驗。

![新增](../assets/new.svg)<!-- PAY-4878 --> 現在， [!DNL Payment Services] Adobe Commerce和Magento Open Source商戶隨附基本結帳功能。[!DNL Payment Services] 現在可支援業務遍及全球200個地區的商家。[!DNL Payment Services] 基本結帳功能在自助入門中提供借記/貸記、PayPal、Venmo （可用時）和PayLater （可用時）選項。

![修正](../assets/fix.svg)<!-- PAY-5291 --> 某些交易的收款確認可能會延遲。 在這種情況下，商家現在可以獲得訂單的更新付款狀態。 [付款服務會偵測付款交易的擱置狀態](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html) 藉由偵測暫緩異動，並主動監控這些異動，並在擷取暫緩狀態時進行更新，以排序待定異動。

## v2.3.4

_2024年3月1日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg)<!-- PAY-5244 --> 修正非同步簽出相容性。

![修正](../assets/fix.svg)<!-- PAY-5253 --> 修正儲存庫權杖不所屬的錯誤 [!DNL Payment Services] 無法刪除。

## v2.3.3

_2024年2月14日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg)<!-- PAY-5048 --> 新增對PHP 8.3的支援

![修正](../assets/fix.svg)<!-- PAY-5048 --> 修正的錯誤 `is_deleted` 標幟。 現在，訂單不會因為 `Rejected` 從擴充功能傳送的狀態。

## v2.3.2

_2024年1月26日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![修正](../assets/fix.svg)<!-- PAY-5183 --> 修正REST/GraphQL效能問題。 現在，透過API擷取時，信用卡按鈕會呈現。

## v2.3.1

_2023年12月7日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg)<!-- PAY-5047 --> 現在可從下列位置取得信用/扣帳卡品牌或付款方式型別：
- 店面的客戶訂單頁面
- 訂單確認電子郵件已傳送給購物者
- 從 [訂單詳細資料檢視](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-processing.html#view-an-order) (在Commerce管理員中)。

## v2.3.0

_2023年12月1日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg)<!-- PAY-4381 --> [Payment Services現在支援GraphQL整合](https://developer.adobe.com/commerce/webapi/graphql/payment-services/). 透過GraphQL對PayPal付款按鈕、託管欄位和Apple Pay的支援，[!DNL Payment Services] 現在支援Headless Commerce設定。

## v2.2.1

_2023年9月27日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![已修正的問題](../assets/fix.svg)<!-- Issue PAY-4870 --> 修正傳送具有最新版本的擴充功能版本時，Storefront中正確填入新標題屬性的問題。 先前，使用 `1.3.0` 發行Commerce服務聯結器，您無法延伸 `User-Agent header` 從 [!DNL Payment Services] 副檔名。

## v2.2.0

_2023年8月30日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg)<!-- PAY-4638 --> 已新增 [與Signifyd整合](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/security-compliance/fraud-protection.html)，提供自動的詐騙防護服務。

![新增](../assets/new.svg)<!-- PAY-3981 --> [將Apple Pay升級為個別付款選項](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html?lang=en#apple-pay-button)，位於PayPal付款按鈕之外，可增加購物者對付款選項的可見度，並允許商家控制Apple Pay的位置和樣式。

![新增](../assets/new.svg)<!-- PAY-4002 --> 改善信用卡欄位結帳的使用者體驗，包括樣式增強功能，例如新增付款圖示，以降低購物者的認知負載並提高轉換率。

![新增](../assets/new.svg)<!-- PAY-4002 --> 新增功能以允許商家 [排序其付款選項的順序](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#payment-buttons) 以排定特定付款選項的優先順序。 此功能可提高結帳對話率。

![新增](../assets/new.svg)<!-- PAY-4035 --> 商戶現在可以有效地監控其店舖的健康狀況，並使用新的識別任何交易問題 [交易報表](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/transactions.html) 可從以下網址取得：[!DNL Payment Services] 管理首頁。 此報表也會顯示有關交易授權率及負數交易趨勢的資料。

## v2.1.0

_2023年6月9日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg)<!-- Issue xxx --> 新增對Adobe Commerce 2.4.7-beta1的支援。

![新增](../assets/new.svg)<!-- Issue xxx --> 已新增 [下列國家和相關貨幣的可用性](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html#availability)：澳洲、法國、英國。

![新增](../assets/new.svg)<!-- Issue PAY-4296 --> 已新增 [管理員角色的擴充資源](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#configure-roles) 以確保管理員使用者可以建立和管理客戶的訂單，並且可以[!DNL Payment Services] 在「銷售」功能表中。

![新增](../assets/new.svg)<!-- Issue PAY-4236 --> 已新增 [結帳期間發生錯誤的訂單自動作廢](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/checkout.html#order-auto-voided-if-error).

![新增](../assets/new.svg)<!-- Issue PAY-4183 --> 已建立的功能 [顯示「信用卡/扣帳卡付款選項」按鈕](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#debit-or-credit-card-button) 在結帳頁面上。

## v2.0.0

_2023年3月10日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg)<!-- Issue PAY-4152 --> 新增對PHP 8.2和Adobe Commerce 2.4.6的支援。與PHP 7.x不相容。

## v1.6.1

_2023年3月10日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![修正](../assets/fix.svg)<!-- Issue PAY-4226 --> 修正無法新增的問題 [!DNL Payment Services] 商戶在「管理員」中使用簽出。[!DNL Payment Services] 之前使用Commerce客戶ID，新客戶沒有此ID。

![修正](../assets/fix.svg)<!-- Issue PAY-4205 --> 修正在使用「 」結帳時，導致指定的送貨地址狀態被預設稅捐設定中的狀態取代的問題 [PayPal選項](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#paypal-smart-buttons). 現在，客戶可以將訂單運送至商戶稅捐設定中設定為預設狀態以外的其他狀態。

![修正](../assets/fix.svg)<!-- Issue PAY-4202 --> 修正客戶無法使用卡儲存庫完成購買或刪除商店的儲存庫付款方式的問題 [使用 `Authorize and Capture` 付款動作](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/production.html#set-payment-services-as-payment-method). 以前，當客戶嘗試使用或修改其存放的信用卡時，會出現「找不到提供者儲存庫ID」錯誤。

## v1.6.0

_2023年2月17日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg)<!-- Issue PAY-3540 --> 已新增 [PCI 3DS法規遵循功能，適用於在歐盟(EU)及英國進行交易的商家](security.md#3ds). 此額外的安全性層級要求購買者必須向其信用卡簽發者進行驗證，有助於防止線上詐騙，並且是歐盟(EU)法規要求的一部分。

![新增](../assets/new.svg)<!-- Issue PAY-3609 --> 新增以下功能： [在「管理員」中啟用卡片儲存機制](vaulting.md#use-vaulting-in-the-admin). 這可讓商戶使用存放的付款方式，為「管理員」中的客戶建立訂單。

## v1.5.4

_2023年1月29日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![已修正的問題](../assets/fix.svg)<!-- Issue PAY-4110 --> 修正買家無法使用產品頁面、迷你購物車及購物車上的付款按鈕下單的問題。 買家現在可以成功完成訂單。

## v1.5.3

_2023年1月25日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![已修正的問題](../assets/fix.svg)<!-- Issue PAY-4102 --> 已發行修正回溯不相容的已知問題。 此發行版本會將服務ID擴充功能版本鎖定至最新穩定版本，這會重新啟用新版本 [!DNL Payment Services] 安裝以設定Commerce服務。

## v1.5.2

_2022年12月22日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![已修正的問題](../assets/fix.svg)<!-- Issue PAY-3992 --> 改善開立商業發票於 [!DNL Payment Services] 當拒絕付款方式時。

![已修正的問題](../assets/fix.svg)<!-- Issue PAY-3999 -->[!DNL Payment Services] 現在正確顯示商戶使用的PayPal付款按鈕 [引發籤出](https://commercemarketplace.adobe.com/swissup-firecheckout.html){target=_blank} 結帳頁面的自訂範本。 之前，迷你圖會斷斷續續地顯示按鈕。

## v1.5.1

_2022年11月23日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg)<!-- Issue PAY-3923 -->[!DNL Payment Services] 現在，使用者代理標題中包含版本號碼，以便請求可以追蹤、篩選或淘汰未使用的端點。

![已修正的問題](../assets/fix.svg)<!-- Issue PAY-3968 -->[!DNL Payment Services] 現在，當使用付款按鈕從產品頁面下訂單時，可以正確顯示訂單資料。

## v1.5.0

_2022年11月18日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg)<!-- Issue PAY-3880 --> 購物者現在可以 [在結帳時儲存其信用卡資訊](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting.html) 用於相同或相同商家帳戶內其他商店的後續購買。

![新增](../assets/new.svg)<!-- Issue PAY-3950 --> 商戶現在可以啟用 [立即購買Commerce功能](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/checkout-instant-purchase.html) ，讓購物者可以(使用 [存放的信用卡資訊](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting.html))以加快結帳速度。

## v1.4.1

_2022年10月14日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![修正](../assets/fix.svg)<!-- Issue PAY-3766 --> 當客戶的付款方式遭到拒絕時，顯示的錯誤訊息更具描述性。 它建議客戶重新輸入付款資訊，然後再試一次、嘗試其他付款方式，或就拒絕的交易聯絡其銀行。

## v1.4.0

_2022年9月30日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg)<!-- Issue PAY-784 -->[!DNL Payment Services] 現在包含設定商家帳戶以 [使用多個PayPal企業帳戶](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#use-multiple-paypal-accounts). 這可讓商家使用不同的貨幣在多個國家經營您的商店，或是將Adobe Commerce用於您的一部分業務。

![新增](../assets/new.svg)<!-- Issue PAY-3231 --> 商戶可以 [新增 [!UICONTROL Soft Descriptor]](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#add-soft-descriptor) 至客戶交易銀行對帳單上顯示的網站或個別商店檢視設定，以描述品牌、商店或產品線。

![新增](../assets/new.svg)<!-- Issue PAY-3707 --> [啟用或停用信用卡欄位和PayPal付款按鈕](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#configure-payment-options) 以簽入[!DNL Payment Services] 設定。

![已修正的問題](../assets/fix.svg)<!-- Issue PAY-3546 --> 客戶點按時 **[!UICONTROL Edit cart]**，頁面會重新導向至購物車頁面，並顯示更新後的專案，而非顯示空白購物車。

## v1.3.1

_2022年9月6日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![已修正的問題](../assets/fix.svg)<!-- Issue PAY-3663 --> 現在，當商戶的商店擷取以非全域貨幣授權的訂單時，擷取處理作業會完成，且不會顯示錯誤。

## v1.3.0

_2022年8月9日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg)<!-- Issue PAY-XX --> 正式發行版本 — [!DNL Payment Services] 為現在 [支援者 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 版本2.4.0至2.4.5](https://devdocs.magento.com/release/availability.html#compatibility).

![已修正的問題](../assets/fix.svg)<!-- Issue PAY-x --> Apple Pay現在相容於行動裝置和桌上型電腦上的Safari瀏覽器v15.5。

## v1.2.0

_2022年6月29日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![已知問題](../assets/bug.svg)<!-- Issue PAY-x --> Apple Pay與行動裝置和桌上型電腦上的Safari瀏覽器v15.5不相容。 使用Safari 15.5版時，您無法透過Apple Pay完成結帳。

![已修正的問題](../assets/fix.svg)<!-- Issue PAY-3264 --> 先前，當登入使用者為其帳戶選取預設地址以外的帳單/運送地址時，結帳失敗。 現在會傳送選取的帳單/運送地址（而不是預設的儲存地址），並成功完成結帳。

![已修正的問題](../assets/fix.svg)<!-- Issue PAY-3314 --> 如果您停用結帳的PayPal付款按鈕，則不會顯示錯誤。

![已修正的問題](../assets/fix.svg)<!-- Issue PAY-3330 --> 當訪客使用者輸入包含破折號的電話號碼時，結帳期間付款不再失敗。

![已修正的問題](../assets/fix.svg)<!-- Issue PAY-3338 PAY-2502 --> 當Commerce服務憑證無效時，[!DNL Payment Services] 現在顯示認證錯誤，提醒您從 [!DNL Payment Services] 在Admin中的首頁。

![已知問題](../assets/bug.svg)<!-- Issue PAY-0 --> [!DNL Payment Services] 與不相容 `commerce-data-export` v101.20及更高版本，因此與 [[!DNL Channel manager] 副檔名](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/guide-overview.html).

## v1.1.0

_2022年3月31日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg)<!-- Issue PAY-2127 --> 正式發行版本 — [!DNL Payment Services] 為現在 [支援者 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 版本2.4.0至2.4.4](https://devdocs.magento.com/release/availability.html#compatibility).

![新增](../assets/new.svg)<!-- Issue PAY-2682 --> 此 [!DNL Payment Services] 延伸模組 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 現在加拿大商戶可使用。 商戶可在下列位置檢視付款設定： [法文](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html?lang=fr#carte-de-cr%C3%A9dit-et-devises-accept%C3%A9es) 或 [英文](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html#accepted-credit-cards-and-currencies).

![新增](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] 支援 [加幣(CAD)](overview.md#accepted-credit-cards-and-currencies) 用於信用卡和PayPal交易。

![新增](../assets/new.svg)<!-- Issue PAY-2680 --> 商戶可以 [板載 [!DNL Payment Services]](onboard.md) 英文或法文擴充功能。

![新增](../assets/new.svg)<!-- Issue PAY-2678 --> 商戶現在可以檢視財務報表，包括 [訂單付款狀態](order-payment-status.md) 和 [支付報表](payouts.md)，加元(CAD)。

![已修正的問題](../assets/fix.svg)<!-- Issue PAY-2710 -->[!DNL Payment Services] 現在相容於 [PHP 8.1](https://www.php.net/releases/8.1/en.php).

![已修正的問題](../assets/fix.svg)<!-- Issue PAY-3017 --> 改善沙箱模式警報，以便在多個存放區中顯示適當的警報。

![已修正的問題](../assets/fix.svg)<!-- Issue PAY-2742 --> 您現在可以在商店檢視層級啟用或停用可用的付款方法，例如Venmo。 之前，您只能為每個網站設定付款方法。

![已修正的問題](../assets/fix.svg)<!-- Issue PAY-2277 --> 您現在可以選擇 [啟用或停用個別PayPal付款按鈕](settings.md#payment-buttons).

![已修正的問題](../assets/fix.svg)<!-- Issue PAY-2561 --> 先前移除的產品不會出現在的購物車中 _檢閱訂單_ 頁面。

![已知問題](../assets/bug.svg)<!-- Issue PAY-2842 --> 測試信用卡交易 [可能因PayPal而失敗](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-cc-sandbox-failure.html) 在沙箱環境中處理付款時。

## v1.0.0

_2021年11月29日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg)<!-- Issue PAY-2127 --> 正式發行版本 — [[!DNL Payment Services]](https://commercemarketplace.adobe.com/magento-payment-services.html) 現已支援 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 版本2.4.0至2.4.3-p1。

![新增](../assets/new.svg)<!-- Issue PAY-124 --> 此 [!DNL Payment Services] 延伸模組 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 可以安裝為 [[!DNL Adobe Commerce] 在雲端基礎結構上](install.md#adobe-commerce-on-cloud-infrastructure) 或 [內部部署](install.md#on-premises) 執行個體。 這些方法需要使用指令行介面。

![新增](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] 支援 [沙箱帳戶](sandbox.md) 可讓商家在測試模式中評估擴充功能。

![新增](../assets/new.svg)<!-- Issue PAY-666 --> 商戶可以 [設定支付服務](settings.md) 具有基本付款行為的擴充功能，例如利用 [`Authorize and Capture`](production.md#set-payment-services-as-payment-method) 在沙箱或生產環境之間切換。

![新增](../assets/new.svg)<!-- Issue PAY-780 --> 您的購物者可以結帳使用 [!DNL Payment Services] 或透過 [手動建立訂單](create-order.md).

![新增](../assets/new.svg)<!-- Issue PAY-1856 --> 完整的報告，透過 [訂單付款狀態](order-payment-status.md) 和 [支付報表](payouts.md)，可用於 [!DNL Payment Services] 讓您清楚瞭解商店的訂單與相關付款。

![新增](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] 根據總處理量，支援彈性的階層式定價，適用於任何商家。

![新增](../assets/new.svg)<!-- Issue PAY-1443 --> 您可以 [自訂外觀](payments-options.md) 的PayPal付款按鈕和信用卡欄位 [!DNL Payment Services] 副檔名。

![已知問題](../assets/bug.svg)<!-- Issue PAY-2473 --> 使用 [不正確的撰寫器索引鍵](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-install.html) 在安裝擴充功能期間，防止使用者 [驗證](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 具有正確的 `MAGEID`.

![已知問題](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] 報表 [可能不會立即同步](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-report-info-delayed.html).

![已知問題](../assets/bug.svg)<!-- Issue PAY-2475 --> 您的 [PayPal沙箱帳戶](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-paypal-acct.html) 的 [!DNL Payment Services] 如果您在上線期間建立該帳戶，則無法驗證。
