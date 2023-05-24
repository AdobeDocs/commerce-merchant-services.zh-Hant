---
title: '"[!DNL Quick Checkout] 發行說明'''
description: 查看發行說明以瞭解有關所有 [!DNL Quick Checkout] 版本。
exl-id: 511be2fc-d24d-4323-a47a-d376e38a5c47
source-git-commit: 169b3e365d7f4c0c4cef19fa1941dfa0a95ea58b
workflow-type: tm+mt
source-wordcount: '1422'
ht-degree: 0%

---

# 發行說明

本發行說明描述了 [!DNL Quick Checkout] 包括：

![新建](../assets/new.svg) 新功能
![已修復問題](../assets/fix.svg) 修復和改進
![已知問題](../assets/bug.svg) 已知問題

請參閱 [即將發佈的版本](https://devdocs.magento.com/release/) 瞭解發行計畫和支援。

請參閱 [可用性](https://devdocs.magento.com/release/availability.html) 以瞭解產品相容性。

## 管理面板更新

這些發行說明描述了在「管理」面板的常規版本控制功能版本之外所發生和發佈的功能更改和修復。

+++管理面板更新

2023年5月23日_

![已修復問題](../assets/fix.svg)<!-- Issue BOLT-489 --> 現在， **新帳戶** 元件 [!DNL Quick Checkout] 報告頁包括頻譜 [工作流表徵圖](https://react-spectrum.adobe.com/react-spectrum/workflow-icons.html){target=_blank}。

_2023年4月25日_

![已修復問題](../assets/fix.svg)<!-- Issue BOLT-452 --> 的 [!DNL Quick Checkout] **參觀** 按鈕現在在滑鼠懸停時顯示可點擊的手指游標。

_2023年4月19日_

![已修復問題](../assets/fix.svg)<!-- Issue BOLT-596 --> 的 [!DNL Quick Checkout] 現在，「報告」頁在分析ISO 8601格式的日期時正確顯示「新帳戶」圖表。

_2022年12月14日_

![已修復問題](../assets/fix.svg)<!-- Issue BOLT-524 --> 的 [!DNL Quick Checkout] 管理面板現在顯示正確的訂單總數和更新的報告資訊。

_2022年11月30日_

![新建](../assets/new.svg)<!-- Issue BOLT-502 --> 現在， [報告](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) 頁籤具有新的「去年」預設。

![新建](../assets/new.svg)<!-- Issue BOLT-471 --> 在 [!DNL Quick Checkout] 「管理」面板顯示中的詳細資訊 [工具提示](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html)。

![已修復問題](../assets/fix.svg)<!-- Issue BOLT-514 --> 在 [!DNL Quick Checkout] 「管理」面板顯示正確的總訂單編號、顏色的一致性以及所有圖表的正確圖例。

_2022年11月2日_

![新建](../assets/new.svg)<!-- Issue BOLT-293 --> 現在， [報告](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) 的 [!DNL Quick Checkout] 「管理」面板顯示您商店的結帳體驗統計資訊的圖表和報告資訊。

![新建](../assets/new.svg)<!-- Issue BOLT-422 --> 的 [_概述_](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#reports-overview) 「報告」主題部分的部分顯示有關您商店的結帳效能的詳細資訊，包括平均結帳時間、結帳期間建立的新帳戶以及結帳放棄。

![新建](../assets/new.svg)<!-- Issue BOLT-423 --> 的 [_趨勢_](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#reports-trends) 「報告」頁籤的部分顯示按帳戶類型和在結帳期間建立的新帳戶篩選的結帳體驗趨勢。

![新建](../assets/new.svg)<!-- Issue BOLT-439 --> 的 **報告** 頁籤 [預設濾鏡預設](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#filter-data) 可用於顯示特定資料範圍。

![新建](../assets/new.svg)<!-- Issue BOLT-433 --> 你現在可以看到 _無可用資料_ 請求未返回任何資料時的圖表警告。

![新建](../assets/new.svg)<!-- Issue BOLT-473 --> 從 [!DNL Quick Checkout] 管理面板包括啟用 [簽出跟蹤](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/settings-quick-checkout.html#service-settings) 允許Adobe Commerce與博爾特共用報告資訊的設定。

_2022年10月5日_

![新建](../assets/new.svg)<!-- Issue BOLT-379 --> 現在，當新商戶 [!DNL Quick Checkout] 管理員面板 [由Gainsight支援的功能教程](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) 的子菜單。

![新建](../assets/new.svg)<!-- Issue BOLT-377 --> 的 **報告** 的 [!DNL Quick Checkout] 管理面板顯示圖表和報告分析。

![新建](../assets/new.svg)<!-- Issue BOLT-377 --> 的 **報告** 的 [!DNL Quick Checkout] 「管理」面板顯示圖表和報告分析的日期範圍和篩選器預設。

![已修復問題](../assets/fix.svg)<!-- Issue BOLT-369 --> 現在， [[!DNL Quick Checkout] 管理面板](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 在頁腳中顯示應用版本。

+++

## v1.8.0

_2023年2月24日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg)<!-- Issue BOLT-520 --> 一般可用性發佈 — [[!DNL Quick Checkout]](https://marketplace.magento.com/magento-quick-checkout.html) 現在已預裝在Adobe Commerce Cloud2.4.6版和更新版本中。

![已修復問題](../assets/fix.svg)<!-- Issue BOLT-592 --> 在中下訂單時用戶體驗的改善 [管理面板](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/create-order-admin.html) 使用 [Braintree](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/stored-payment-methods.html) 付款方式。 此功能允許客戶在結帳時將Braintree作為付款方式下單 [!DNL Quick Checkout] 的子菜單。

## v1.7.0

_2023年2月22日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![已修復問題](../assets/fix.svg)<!-- Issue AC-8002 --> 使用 [多發運](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/multishipping-settings.html) 的雙曲餘切值。 此功能允許在結帳時顯示付款方法 [!DNL Quick Checkout] 的子菜單。

## v1.6.0

_2023年2月9日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![已修復問題](../assets/fix.svg)<!-- Issue BOLT-567 --> 用戶體驗改善 [下訂單](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) 使用 [店內交貨](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/delivery/basic-methods/shipping-in-store-delivery.html) 方法 [!DNL Quick Checkout] 已禁用。

![已修復問題](../assets/fix.svg)<!-- Issue BOLT-569 --> 對允許購物者註銷功能的改進 [從Bolt網路註銷](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/user-session-lifetime.html)。

## v1.5.0

_2023年1月18日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg)<!-- Issue BOLT-522 --> 可以啟用/禁用新配置以檢測 [購物者](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/manage-checkout/checkout-options/checkout-adobe-commerce.html) 可以自動登錄到Bolt。

![新建](../assets/new.svg)<!-- Issue BOLT-523 --> 可以啟用/禁用新配置，允許商家指定購物者是可以自動登錄到兩個網路，還是只登錄到Bolt網路。

![已修復問題](../assets/fix.svg)<!-- Issue BOLT-542 --> 用戶體驗改善 [將卡或地址保存到Bolt帳戶](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) 當購物者提供電子郵件時。

![已修復問題](../assets/fix.svg)<!-- Issue BOLT-550 --> 用戶體驗改善 [自動登錄](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#configure-service-settings) 當Bolt用戶提供電子郵件時。

![已修復問題](../assets/fix.svg)<!-- Issue BOLT-544 --> 相容性改進 [回調URL](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#check-shopper-valid-account) 與 [多站點](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/multi-sites/ms-overview.html) 在博爾特。

## v1.4.0

_2022年11月30日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg)<!-- Issue BOLT-513 --> 現在，當Adobe Commerce客戶在結帳過程中登錄到商店，並且擁有Bolt帳戶時，將顯示一個登錄購物者Bolt帳戶的選項。

![新建](../assets/new.svg)<!-- Issue BOLT-512 --> 新配置會自動檢測登錄的購物者是否也可以登錄Bolt。

![新建](../assets/new.svg)<!-- Issue BOLT-480 --> 中的新配置 [!DNL Quick Checkout] 管理面板允許您將預設導航流更改為 **裝運** Bolt客戶登錄後，即可進行頁面訪問。 預設情況下，它配置為 **付款** 的子菜單。

## v1.3.0

_2022年11月2日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg)<!-- Issue BOLT-293 --> 現在， [!DNL Quick Checkout] 包括啟用 [簽出跟蹤](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/settings-quick-checkout.html#service-settings) 允許Adobe Commerce與博爾特共用報告資訊的設定。

![新建](../assets/new.svg)<!-- Issue BOLT-461 --> 您現在可以在 [!DNL Quick Checkout] 如果 [簽出跟蹤](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) 配置已禁用。

## v1.2.0

_2022年9月8日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg)<!-- Issue BOLT-341 --> 一般可用性發佈 — [[!DNL Quick Checkout]](https://marketplace.magento.com/magento-quick-checkout.html) 現在與Adobe Commerce2.4.5版相容。

![新建](../assets/new.svg)<!-- Issue BOLT-328 --> [!DNL Quick Checkout] Adobe Commerce和Magento Open Source [管理面板視圖](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) 以及設定和使用擴展所需的所有資訊。

![新建](../assets/new.svg)<!-- Issue BOLT-364 --> 管理員用戶 [可以設定用戶角色和權限](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/user-roles-setup.html) 允許其他用戶查看 [!DNL Quick Checkout] 管理面板。

![新建](../assets/new.svg)<!-- Issue BOLT-377 --> [!DNL Quick Checkout] 管理面板現在包含包含特定部分的頁眉，如 **概述**。 **報告**, **設定**。

![新建](../assets/new.svg)<!-- Issue BOLT-379 --> 當新商家訪問 [!DNL Quick Checkout] 首次出現提供功能教程的歡迎小部件的管理面板。

![新建](../assets/new.svg)<!-- Issue BOLT-378 --> [!DNL Quick Checkout] [管理面板視圖](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) 合併 **配置** 在中未提供API和可發佈鍵時顯示的步驟 [設定](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 的子菜單。

![新建](../assets/new.svg)<!-- Issue BOLT-380 --> [!DNL Quick Checkout] [管理面板視圖](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) 合併 **資源** 在登機階段更改。

![新建](../assets/new.svg)<!-- Issue BOLT-381 --> [!DNL Quick Checkout] [管理面板視圖](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) 包括 **幫助和支援** 的子菜單。

![已修復問題](../assets/fix.svg)<!-- Issue BOLT-369 --> 的 [[!DNL Quick Checkout] 管理面板](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 現在在頁腳中顯示擴展版本。

## v1.1.0

_2022年8月12日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![已修復問題](../assets/fix.svg)<!-- Issue BOLT-375 --> 用戶體驗改善 [[!DNL Quick Checkout] 管理面板](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 現在只包括啟用擴展時可見和已驗證的參數。

![已修復問題](../assets/fix.svg)<!-- Issue BOLT-349 --> 現有發運地址與Bolt Wallet的相容性改進。

## v1.0.0

_2022年8月9日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新建](../assets/new.svg)<!-- Issue BOLT-341 --> 一般可用性發佈 — [[!DNL Quick Checkout]](https://marketplace.magento.com/magento-quick-checkout.html) 現在與Adobe Commerce版2.4.1至2.4.4相容。

![新建](../assets/new.svg)<!-- Issue BOLT-340 --> 的 [!DNL Quick Checkout] Adobe Commerce可以為Adobe Commerce [雲基礎架構](install.md#adobe-commerce-on-cloud-infrastructure) 或 [本地](install.md#on-premises) 實例。 這些方法需要使用命令行介面。

![新建](../assets/new.svg)<!-- Issue BOLT-1 --> 的 [!DNL Quick Checkout] 為Adobe Commerce提供了優化的店面 [按一下簽出體驗](overview.md) 沒有為消費者需要的填充欄位。

![新建](../assets/new.svg)<!-- Issue BOLT-1 --> 的 [!DNL Quick Checkout] Adobe Commerce自動識別網路中的每個購物者 [按一下購買](checkout-flow.md) 就在你的網站上。

![新建](../assets/new.svg)<!-- Issue BOLT-1 --> 的 [!DNL Quick Checkout] Adobe Commerce允許購物者同時 [登錄Adobe Commerce和博爾特網路](checkout-flow.md/#quick-checkout-use-cases) 提供更好的 `one-click checkout` 體驗。

![新建](../assets/new.svg)<!-- Issue BOLT-218 --> [!DNL Quick Checkout] Adobe Commerce支援 [沙盒帳戶](testing.md#testing-in-sandbox) 允許商戶在test模式下評估擴展。

![新建](../assets/new.svg)<!-- Issue BOLT-780 --> 您的購物者可以通過 [[!DNL Quick Checkout]](checkout-page.md) 或通過 [手動訂單建立](create-order-admin.md)。

![新建](../assets/new.svg)<!-- Issue BOLT-666 --> 商家可以配置 [!DNL Quick Checkout] 基本付款活動，如 [`Authorize and Capture` 或 `Authorize` ](onboarding.md#complete-admin-configuration)或在沙盒和生產環境之間切換。

![新建](../assets/new.svg)<!-- Issue BOLT-288 --> 自定義 [用戶會話生存期](user-session-lifetime.md) 為 [!DNL Quick Checkout] Adobe Commerce。

![已修復問題](../assets/fix.svg)<!-- Issue BOLT-375 --> 用戶體驗改善 [[!DNL Quick Checkout] 管理面板](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 允許您在提供所有必需參數時保存配置。

![已知問題](../assets/bug.svg)<!-- Issue BOLT-342 --> 常用 [故障排除](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) 安裝過程中的問題 [!DNL Quick Checkout]。
