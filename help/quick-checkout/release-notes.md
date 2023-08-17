---
title: '[!DNL Quick Checkout] 發行說明'
description: 檢閱發行說明以瞭解全部資訊 [!DNL Quick Checkout] 發行版本。
exl-id: 511be2fc-d24d-4323-a47a-d376e38a5c47
feature: Release Notes, Services, Checkout
source-git-commit: 0c8d9498ea7a30a99f834694ef8a865ad24466ab
workflow-type: tm+mt
source-wordcount: '1422'
ht-degree: 0%

---

# 發行說明

以下版本說明說明的初始版本 [!DNL Quick Checkout] 並包含：

![新增](../assets/new.svg) 新功能
![已修正的問題](../assets/fix.svg) 修正和改良
![已知問題](../assets/bug.svg) 已知問題

另請參閱 [即將發行的版本](https://devdocs.magento.com/release/) 以瞭解發行排程和支援。

另請參閱 [可用性](https://devdocs.magento.com/release/availability.html) 開發人員檔案中，以瞭解產品相容性。

## 管理員面板更新

這些發行說明說明說明所發生的功能變更和修正，這些變更和修正是在管理員面板的定期版本化功能發行之外發行的。

+++Admin面板更新

2023年5月23日_

![已修正的問題](../assets/fix.svg)<!-- Issue BOLT-489 --> 現在， **新帳戶** 中的元件 [!DNL Quick Checkout] 報告頁面包含頻譜 [工作流程圖示](https://react-spectrum.adobe.com/react-spectrum/workflow-icons.html){target=_blank}.

_2023年4月25日_

![已修正的問題](../assets/fix.svg)<!-- Issue BOLT-452 --> 此 [!DNL Quick Checkout] **進行導覽** 按鈕現在會在游標暫留時顯示可點按的手遊標。

_2023年4月19日_

![已修正的問題](../assets/fix.svg)<!-- Issue BOLT-596 --> 此 [!DNL Quick Checkout] 現在，當將日期剖析為ISO 8601格式時，「報表」頁面可正確顯示「新帳戶」圖表。

_2022年12月14日_

![已修正的問題](../assets/fix.svg)<!-- Issue BOLT-524 --> 此 [!DNL Quick Checkout] 「管理員」面板現在會顯示正確的訂單總計和更新的報表資訊。

_2022年11月30日_

![新增](../assets/new.svg)<!-- Issue BOLT-502 --> 現在， [報告](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) 標籤有新的「去年」預設集。

![新增](../assets/new.svg)<!-- Issue BOLT-471 --> 改善的使用者體驗 [!DNL Quick Checkout] 管理面板顯示更多資訊於 [工具提示](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html).

![已修正的問題](../assets/fix.svg)<!-- Issue BOLT-514 --> 改善的使用者體驗 [!DNL Quick Checkout] 管理面板為所有圖表顯示正確的總訂單數、顏色一致性和正確圖例。

_2022年11月2日_

![新增](../assets/new.svg)<!-- Issue BOLT-293 --> 現在， [報告](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) 索引標籤中的 [!DNL Quick Checkout] 「管理員」面板會顯示商店結帳體驗統計資料的圖表和報告資訊。

![新增](../assets/new.svg)<!-- Issue BOLT-422 --> 此 [_概觀_](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#reports-overview) 「報表」主題區段的區段會顯示您商店結帳效能的詳細資訊，包括平均結帳時間、結帳期間建立的新帳戶以及結帳放棄。

![新增](../assets/new.svg)<!-- Issue BOLT-423 --> 此 [_趨勢_](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#reports-trends) 「報表」索引標籤的區段會顯示依帳戶型別篩選的結帳體驗趨勢，以及在結帳期間建立的新帳戶。

![新增](../assets/new.svg)<!-- Issue BOLT-439 --> 此 **報表** 標籤顯示 [預設篩選預設集](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#filter-data) 來顯示特定資料範圍。

![新增](../assets/new.svg)<!-- Issue BOLT-433 --> 您現在可以看到 _沒有可用的資料_ 請求未傳回任何資料時圖表警告。

![新增](../assets/new.svg)<!-- Issue BOLT-473 --> 來自的使用者體驗改善 [!DNL Quick Checkout] 管理員面板包含啟用 [結帳追蹤](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/settings-quick-checkout.html#service-settings) 此設定可讓Adobe Commerce與Bolt共用報表資訊。

_2022年10月5日_

![新增](../assets/new.svg)<!-- Issue BOLT-379 --> 現在，當新商家存取 [!DNL Quick Checkout] 第一次使用「管理員」面板 [功能導覽，由Gainsight提供技術支援](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) 隨即顯示。

![新增](../assets/new.svg)<!-- Issue BOLT-377 --> 此 **報表** 索引標籤中的 [!DNL Quick Checkout] 「管理員」面板會顯示圖表和報告分析。

![新增](../assets/new.svg)<!-- Issue BOLT-377 --> 此 **報表** 索引標籤中的 [!DNL Quick Checkout] 「管理員」面板會顯示圖表和報告分析的日期範圍和篩選預設集。

![已修正的問題](../assets/fix.svg)<!-- Issue BOLT-369 --> 現在， [[!DNL Quick Checkout] 管理面板](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 在頁尾中顯示應用程式版本。

+++

## v1.8.0

_2023年2月24日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg)<!-- Issue BOLT-520 --> 正式發行版本 — [[!DNL Quick Checkout]](https://commercemarketplace.adobe.com/magento-quick-checkout.html) 現已預先安裝在Adobe Commerce Cloud 2.4.6版及更新版本中。

![已修正的問題](../assets/fix.svg)<!-- Issue BOLT-592 --> 改善在中下訂單時的使用者體驗 [管理面板](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/create-order-admin.html) 使用 [Braintree](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/stored-payment-methods.html) 作為付款方式。 此功能可讓客戶在結帳時以Braintree作為付款方式下訂單。 [!DNL Quick Checkout] 已啟用。

## v1.7.0

_2023年2月22日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![已修正的問題](../assets/fix.svg)<!-- Issue AC-8002 --> 使用下訂單時的使用者體驗改善 [多送貨](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/multishipping-settings.html) 方法。 此功能可在結帳時顯示付款方法，當 [!DNL Quick Checkout] 已啟用。

## v1.6.0

_2023年2月9日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![已修正的問題](../assets/fix.svg)<!-- Issue BOLT-567 --> 改善使用者體驗的時機 [下訂單](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) 使用 [店內傳遞](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/delivery/basic-methods/shipping-in-store-delivery.html) 具有的方法 [!DNL Quick Checkout] 已停用。

![已修正的問題](../assets/fix.svg)<!-- Issue BOLT-569 --> 改善登出功能，讓購物者 [登出Bolt Network](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/user-session-lifetime.html).

## v1.5.0

_2023年1月18日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg)<!-- Issue BOLT-522 --> 可以啟用/停用新設定以偵測 [購物者](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/manage-checkout/checkout-options/checkout-adobe-commerce.html) 可自動登入Bolt。

![新增](../assets/new.svg)<!-- Issue BOLT-523 --> 可以啟用/停用新的設定，以允許商家指定購物者是否可以自動登入兩個網路，或僅是Bolt網路。

![已修正的問題](../assets/fix.svg)<!-- Issue BOLT-542 --> 改善使用者體驗的時機 [將卡片或地址儲存至Bolt帳戶](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) 購物者提供電子郵件時。

![已修正的問題](../assets/fix.svg)<!-- Issue BOLT-550 --> 中的使用者體驗改善 [自動登入](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#configure-service-settings) Bolt使用者提供電子郵件時。

![已修正的問題](../assets/fix.svg)<!-- Issue BOLT-544 --> 相容性改善 [回呼URL](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#check-shopper-valid-account) 替換為 [多網站](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/multi-sites/ms-overview.html) 在Bolt。

## v1.4.0

_2022年11月30日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg)<!-- Issue BOLT-513 --> 現在，當Adobe Commerce客戶在結帳過程中登入商店並擁有Bolt帳戶時，畫面會顯示登入購物者的Bolt帳戶的選項。

![新增](../assets/new.svg)<!-- Issue BOLT-512 --> 新設定會自動偵測登入的購物者是否也可登入Bolt。

![新增](../assets/new.svg)<!-- Issue BOLT-480 --> 中的新設定 [!DNL Quick Checkout] 「管理面板」可讓您將預設導覽流程變更為 **送貨** Bolt客戶登入後頁面。 依預設，它會設定為 **付款** 頁面。

## v1.3.0

_2022年11月2日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg)<!-- Issue BOLT-293 --> 現在， [!DNL Quick Checkout] 包括啟用 [結帳追蹤](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/settings-quick-checkout.html#service-settings) 此設定可讓Adobe Commerce與Bolt共用報表資訊。

![新增](../assets/new.svg)<!-- Issue BOLT-461 --> 您現在可以在中看到警告訊息 [!DNL Quick Checkout] 管理員面板，如果 [結帳追蹤](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) 設定已停用。

## v1.2.0

_2022年9月8日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg)<!-- Issue BOLT-341 --> 正式發行版本 — [[!DNL Quick Checkout]](https://commercemarketplace.adobe.com/magento-quick-checkout.html) 現在與Adobe Commerce 2.4.5版相容。

![新增](../assets/new.svg)<!-- Issue BOLT-328 --> [!DNL Quick Checkout] 對於Adobe Commerce，Magento Open Source提供 [管理面板檢視](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) 提供設定及使用擴充功能所需的所有資訊。

![新增](../assets/new.svg)<!-- Issue BOLT-364 --> 管理員使用者 [可以設定使用者角色和許可權](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/user-roles-setup.html) 允許其他使用者檢視 [!DNL Quick Checkout] 管理面板。

![新增](../assets/new.svg)<!-- Issue BOLT-377 --> [!DNL Quick Checkout] 「管理」面板現在包含頁面標頭，其中包含特定區段，例如 **概觀**， **報表**、和 **設定**.

![新增](../assets/new.svg)<!-- Issue BOLT-379 --> 當新商家存取 [!DNL Quick Checkout] 歡迎Widget首次出現時管理面板，提供功能導覽。

![新增](../assets/new.svg)<!-- Issue BOLT-378 --> [!DNL Quick Checkout] [管理面板檢視](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) 整合一個 **設定** 中未提供API和可發佈金鑰時顯示的步驟 [設定](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 檢視。

![新增](../assets/new.svg)<!-- Issue BOLT-380 --> [!DNL Quick Checkout] [管理面板檢視](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) 整合一個 **資源** 區段會根據上線階段而改變。

![新增](../assets/new.svg)<!-- Issue BOLT-381 --> [!DNL Quick Checkout] [管理面板檢視](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) 包含 **說明與支援** 區段。

![已修正的問題](../assets/fix.svg)<!-- Issue BOLT-369 --> 此 [[!DNL Quick Checkout] 管理面板](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 現在會在頁尾中顯示擴充功能版本。

## v1.1.0

_2022年8月12日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![已修正的問題](../assets/fix.svg)<!-- Issue BOLT-375 --> 中的使用者體驗改善 [[!DNL Quick Checkout] 管理面板](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 現在僅包含啟用擴充功能時可見及驗證的引數。

![已修正的問題](../assets/fix.svg)<!-- Issue BOLT-349 --> 改善現有送貨地址與Bolt公事包的相容性。

## v1.0.0

_2022年8月9日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg)<!-- Issue BOLT-341 --> 正式發行版本 — [[!DNL Quick Checkout]](https://commercemarketplace.adobe.com/magento-quick-checkout.html) 現在與Adobe Commerce版本2.4.1至2.4.4相容。

![新增](../assets/new.svg)<!-- Issue BOLT-340 --> 此 [!DNL Quick Checkout] 適用於Adobe Commerce的，可安裝適用於Adobe Commerce的 [在雲端基礎結構上](install.md#adobe-commerce-on-cloud-infrastructure) 或 [內部部署](install.md#on-premises) 執行個體。 這些方法需要使用命令列介面。

![新增](../assets/new.svg)<!-- Issue BOLT-1 --> 此 [!DNL Quick Checkout] (適用於Adobe Commerce)提供最佳化的店面，允許 [一鍵式結帳體驗](overview.md) 沒有消費者所需的填寫欄位。

![新增](../assets/new.svg)<!-- Issue BOLT-1 --> 此 [!DNL Quick Checkout] for Adobe Commerce會自動辨識其網路中的每個購物者， [一鍵式購買](checkout-flow.md) 直接在您的網站上。

![新增](../assets/new.svg)<!-- Issue BOLT-1 --> 此 [!DNL Quick Checkout] (適用於Adobe Commerce)可讓購物者同時 [已同時登入Adobe Commerce和Bolt網路](checkout-flow.md/#quick-checkout-use-cases) 提供更優異的 `one-click checkout` 體驗。

![新增](../assets/new.svg)<!-- Issue BOLT-218 --> [!DNL Quick Checkout] 適用於Adobe Commerce支援 [沙箱帳戶](testing.md#testing-in-sandbox) 可讓商家在測試模式中評估擴充功能。

![新增](../assets/new.svg)<!-- Issue BOLT-780 --> 您的購物者可透過 [[!DNL Quick Checkout]](checkout-page.md) 擴充功能或透過 [手動建立訂單](create-order-admin.md).

![新增](../assets/new.svg)<!-- Issue BOLT-666 --> 商家可設定 [!DNL Quick Checkout] 具有基本付款動作，例如 [`Authorize and Capture` 或 `Authorize`](onboarding.md#complete-admin-configuration)，或在沙箱和生產環境之間切換。

![新增](../assets/new.svg)<!-- Issue BOLT-288 --> 自訂 [使用者工作階段期限](user-session-lifetime.md) 的 [!DNL Quick Checkout] 適用於Adobe Commerce。

![已修正的問題](../assets/fix.svg)<!-- Issue BOLT-375 --> 中的使用者體驗改善 [[!DNL Quick Checkout] 管理面板](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 可讓您在提供所有必要引數時儲存設定。

![已知問題](../assets/bug.svg)<!-- Issue BOLT-342 --> 通用 [疑難排解](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) 安裝期間的問題 [!DNL Quick Checkout].
