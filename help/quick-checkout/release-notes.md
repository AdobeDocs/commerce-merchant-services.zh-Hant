---
title: '[!DNL Quick Checkout] 發行說明'
description: 請參閱發行說明，了解 [!DNL Quick Checkout] 版本。
exl-id: 511be2fc-d24d-4323-a47a-d376e38a5c47
source-git-commit: 66082614ffe6456e2c24a1e8d9baaa1113fb7ffb
workflow-type: tm+mt
source-wordcount: '1241'
ht-degree: 0%

---

# 發行說明

以下版本說明的初始版本 [!DNL Quick Checkout] 包括：

![新增](../assets/new.svg) 新功能
![修正問題](../assets/fix.svg) 修正和改良
![已知問題](../assets/bug.svg) 已知問題

請參閱 [即將發行的版本](https://devdocs.magento.com/release/) 了解發行計畫和支援。

請參閱 [可用性](https://devdocs.magento.com/release/availability.html) 請參閱開發人員檔案，了解產品相容性。

## 管理面板更新

以下版本說明說明在「管理面板」的一般版本控制功能版本之外所發生和發行的功能變更和修正。

+++管理面板更新

_2022年12月14日_

![修正問題](../assets/fix.svg)<!-- Issue BOLT-524 --> 此 [!DNL Quick Checkout] 「管理面板」現在會顯示正確的訂單總數和更新的報表資訊。

_2022年11月30日_

![新增](../assets/new.svg)<!-- Issue BOLT-502 --> 現在， [報告](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) 索引標籤有新的「去年」預設集。

![新增](../assets/new.svg)<!-- Issue BOLT-471 --> 改善 [!DNL Quick Checkout] 管理面板會顯示 [工具提示](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html).

![修正問題](../assets/fix.svg)<!-- Issue BOLT-514 --> 改善 [!DNL Quick Checkout] 「管理面板」會顯示正確的訂單總數、色彩的一致性，以及所有圖表的正確圖例。

_2022年11月2日_

![新增](../assets/new.svg)<!-- Issue BOLT-293 --> 現在， [報告](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) 標籤 [!DNL Quick Checkout] 「管理員」面板會顯示您商店結帳體驗統計資料的圖表和報表資訊。

![新增](../assets/new.svg)<!-- Issue BOLT-422 --> 此 [_概述_](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#reports-overview) 「報表」主題區段的區段會顯示您商店結帳效能的詳細資訊，包括平均結帳時間、結帳期間建立的新帳戶，以及結帳放棄。

![新增](../assets/new.svg)<!-- Issue BOLT-423 --> 此 [_趨勢_](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#reports-trends) 「報表」標籤的區段會顯示依帳戶類型篩選的結帳體驗趨勢，以及結帳期間建立的新帳戶。

![新增](../assets/new.svg)<!-- Issue BOLT-439 --> 此 **報表** 顯示 [預設篩選器預設集](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#filter-data) 可用來顯示特定資料範圍。

![新增](../assets/new.svg)<!-- Issue BOLT-433 --> 您現在可以看到 _無可用資料_ 當請求未傳回任何資料時，圖表會顯示警告。

![新增](../assets/new.svg)<!-- Issue BOLT-473 --> 改善 [!DNL Quick Checkout] 管理面板包含啟用 [結帳追蹤](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/settings-quick-checkout.html#service-settings) 可讓Adobe Commerce與Bolt共用報表資訊的設定。

_2022年10月5日_

![新增](../assets/new.svg)<!-- Issue BOLT-379 --> 現在，當新商家 [!DNL Quick Checkout] 管理員面板 [Gainsight支援的功能導覽](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) 框。

![新增](../assets/new.svg)<!-- Issue BOLT-377 --> 此 **報表** 標籤 [!DNL Quick Checkout] 「管理員」面板會顯示圖表和報表分析。

![新增](../assets/new.svg)<!-- Issue BOLT-377 --> 此 **報表** 標籤 [!DNL Quick Checkout] 「管理面板」會顯示圖表和報表分析的日期範圍和篩選預設集。

![修正問題](../assets/fix.svg)<!-- Issue BOLT-369 --> 現在， [[!DNL Quick Checkout] 管理面板](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 在頁尾中顯示應用程式版本。

+++

## v1.6.0

_2023年2月9日_

![修正問題](../assets/fix.svg)<!-- Issue BOLT-567 --> 改善使用者體驗，當 [下訂單](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) 使用 [店內傳遞](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/delivery/basic-methods/shipping-in-store-delivery.html) 方法 [!DNL Quick Checkout] 已停用。

![修正問題](../assets/fix.svg)<!-- Issue BOLT-569 --> 改善登出功能，讓購物者可 [從Bolt網路註銷](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/user-session-lifetime.html).

## v1.5.0

_2023年1月18日_

![新增](../assets/new.svg)<!-- Issue BOLT-522 --> 可啟用/停用新設定，以偵測 [購物者](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/manage-checkout/checkout-options/checkout-adobe-commerce.html) 可自動登入Bolt。

![新增](../assets/new.svg)<!-- Issue BOLT-523 --> 可以啟用/禁用新配置，允許商家指定購物者是否可以自動登錄到兩個網路，或僅登錄到Bolt網路。

![修正問題](../assets/fix.svg)<!-- Issue BOLT-542 --> 改善使用者體驗，當 [將卡或地址保存到Bolt帳戶](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) 購物者提供電子郵件時。

![修正問題](../assets/fix.svg)<!-- Issue BOLT-550 --> 改善 [自動登入](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#configure-service-settings) 當Bolt用戶提供電子郵件時。

![修正問題](../assets/fix.svg)<!-- Issue BOLT-544 --> 相容性改善 [回呼URL](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#check-shopper-valid-account) with [多站點](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/multi-sites/ms-overview.html) 在博爾特。

## v1.4.0

_2022年11月30日_

![新增](../assets/new.svg)<!-- Issue BOLT-513 --> 現在，當Adobe Commerce客戶在結帳程式期間登入商店且有Bolt帳戶時，便會顯示登入購物者Bolt帳戶的選項。

![新增](../assets/new.svg)<!-- Issue BOLT-512 --> 新的設定會自動偵測登入的購物者是否也可登入Bolt。

![新增](../assets/new.svg)<!-- Issue BOLT-480 --> 中的新設定 [!DNL Quick Checkout] 「管理面板」可讓您將預設導覽流程變更為 **裝運** Bolt客戶登入後的頁面。 依預設，會設定為 **付款** 頁面。

## v1.3.0

_2022年11月2日_

![新增](../assets/new.svg)<!-- Issue BOLT-293 --> 現在， [!DNL Quick Checkout] 包括啟用 [結帳追蹤](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/settings-quick-checkout.html#service-settings) 可讓Adobe Commerce與Bolt共用報表資訊的設定。

![新增](../assets/new.svg)<!-- Issue BOLT-461 --> 您現在可以在 [!DNL Quick Checkout] 若 [結帳追蹤](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) 已停用設定。

## v1.2.0

_2022年9月8日_

![新增](../assets/new.svg)<!-- Issue BOLT-341 --> 正式發行 — [[!DNL Quick Checkout]](https://marketplace.magento.com/magento-quick-checkout.html) 現在與Adobe Commerce 2.4.5版相容。

![新增](../assets/new.svg)<!-- Issue BOLT-328 --> [!DNL Quick Checkout] Adobe Commerce和Magento Open Source提供 [管理面板檢視](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) 以及設定和使用擴充功能的所有必要資訊。

![新增](../assets/new.svg)<!-- Issue BOLT-364 --> 管理員使用者 [可以設定使用者角色和權限](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/user-roles-setup.html) 允許其他使用者檢視 [!DNL Quick Checkout] 管理面板。

![新增](../assets/new.svg)<!-- Issue BOLT-377 --> [!DNL Quick Checkout] 「管理面板」現在包含包含特定區段的頁首，例如 **概述**, **報表**，和 **設定**.

![新增](../assets/new.svg)<!-- Issue BOLT-379 --> 當新商家訪問 [!DNL Quick Checkout] 「管理」面板首次出現歡迎介面工具集，提供功能導覽。

![新增](../assets/new.svg)<!-- Issue BOLT-378 --> [!DNL Quick Checkout] [管理面板檢視](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) 併入 **設定** 步驟，此步驟會在未於 [設定](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 檢視。

![新增](../assets/new.svg)<!-- Issue BOLT-380 --> [!DNL Quick Checkout] [管理面板檢視](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) 併入 **資源** 區段，視入門階段而變更。

![新增](../assets/new.svg)<!-- Issue BOLT-381 --> [!DNL Quick Checkout] [管理面板檢視](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) 包括 **說明與支援** 區段。

![修正問題](../assets/fix.svg)<!-- Issue BOLT-369 --> 此 [[!DNL Quick Checkout] 管理面板](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 現在會在頁尾中顯示擴充功能版本。

## v1.1.0

_2022年8月12日_

![修正問題](../assets/fix.svg)<!-- Issue BOLT-375 --> 改善 [[!DNL Quick Checkout] 管理面板](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 現在僅包含啟用擴充功能時可見和驗證的參數。

![修正問題](../assets/fix.svg)<!-- Issue BOLT-349 --> 改進現有發運地址與Bolt錢包的相容性。

## v1.0.0

_2022年8月9日_

![新增](../assets/new.svg)<!-- Issue BOLT-341 --> 正式發行 — [[!DNL Quick Checkout]](https://marketplace.magento.com/magento-quick-checkout.html) 現在與Adobe Commerce 2.4.1至2.4.4版相容。

![新增](../assets/new.svg)<!-- Issue BOLT-340 --> 此 [!DNL Quick Checkout] 適用於Adobe Commerce，可為Adobe Commerce安裝 [雲基礎架構](install.md#adobe-commerce-on-cloud-infrastructure) 或 [內部](install.md#on-premises) 例項。 這些方法需要使用命令列介面。

![新增](../assets/new.svg)<!-- Issue BOLT-1 --> 此 [!DNL Quick Checkout] Adobe Commerce提供最佳化的店面， [一鍵式結帳體驗](overview.md) 無需為消費者填寫欄位。

![新增](../assets/new.svg)<!-- Issue BOLT-1 --> 此 [!DNL Quick Checkout] for Adobe Commerce會自動辨識其網路中的每位購物者 [一鍵式購買](checkout-flow.md) 直接在您的網站上。

![新增](../assets/new.svg)<!-- Issue BOLT-1 --> 此 [!DNL Quick Checkout] Adobe Commerce允許購物者同時 [同時登入Adobe Commerce和Bolt網路](checkout-flow.md/#quick-checkout-use-cases) 提供更好的 `one-click checkout` 體驗。

![新增](../assets/new.svg)<!-- Issue BOLT-218 --> [!DNL Quick Checkout] Adobe Commerce支援 [沙箱帳戶](testing.md#testing-in-sandbox) 可讓商戶在測試模式中評估擴充功能。

![新增](../assets/new.svg)<!-- Issue BOLT-780 --> 購物者可透過 [[!DNL Quick Checkout]](checkout-page.md) 擴充功能或透過 [手動訂單建立](create-order-admin.md).

![新增](../assets/new.svg)<!-- Issue BOLT-666 --> 商戶可以設定 [!DNL Quick Checkout] 具有基本付款動作，例如 [`Authorize and Capture` 或 `Authorize` ](onboarding.md#complete-admin-configuration)，或在沙箱和生產環境之間切換。

![新增](../assets/new.svg)<!-- Issue BOLT-288 --> 自訂 [使用者工作階段期限](user-session-lifetime.md) for [!DNL Quick Checkout] Adobe Commerce。

![修正問題](../assets/fix.svg)<!-- Issue BOLT-375 --> 改善 [[!DNL Quick Checkout] 管理面板](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 可讓您在提供所有必要參數時儲存設定。

![已知問題](../assets/bug.svg)<!-- Issue BOLT-342 --> 常見 [疑難排解](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) 安裝期間發生的問題 [!DNL Quick Checkout].
