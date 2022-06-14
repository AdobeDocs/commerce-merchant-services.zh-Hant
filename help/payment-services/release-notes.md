---
title: '"[!DNL Payment Services] 發行說明"'
description: 查看發行說明以瞭解有關所有 [!DNL Payment Services] 版本。
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
source-git-commit: 6fc2db2ff842244af6a3c52b575b26233540931b
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 1%

---

# 發行說明

本發行說明描述了 [!DNL Payment Services] 包括：

![新建](../assets/new.svg) 新功能
![已修復問題](../assets/fix.svg) 修復和改進
![已知問題](../assets/bug.svg) 已知問題

請參閱 [即將發佈的版本](https://devdocs.magento.com/release/) 瞭解發行計畫和支援。

請參閱 [可用性](https://devdocs.magento.com/release/availability.html) 以瞭解產品相容性。

## v1.1.0

![新建](../assets/new.svg)<!-- Issue PAY-2127 --> 一般可用性發佈 — [!DNL Payment Services] 現在 [相容 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 版本2.4.0至2.4.4](https://devdocs.magento.com/release/availability.html#compatibility)。

![新建](../assets/new.svg)<!-- Issue PAY-2682 --> 的 [!DNL Payment Services] 擴展 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 現在可供加拿大商家使用。 商家可以查看其中任何一個 [法語](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.md#accepted-credit-cards-and-currencies) 或 [英語](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.md#accepted-credit-cards-and-currencies)。

![新建](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] 支援 [加元](overview.md#accepted-credit-cards-and-currencies) 信用卡和PayPal交易。

![新建](../assets/new.svg)<!-- Issue PAY-2680 --> 商家可以 [板 [!DNL Payment Services]](onboard.md) 英文或法文的分機。

![新建](../assets/new.svg)<!-- Issue PAY-2678 --> 商戶現在可以查看財務報表， [訂單付款狀態](order-payment-status.md) 和 [支付報告](payouts.md)，以加元表示。

![已修復問題](../assets/fix.svg)<!-- Issue PAY-2710 --> [!DNL Payment Services] 現在與 [八點一菲律賓比索](https://www.php.net/releases/8.1/en.php)。

![已修復問題](../assets/fix.svg)<!-- Issue PAY-3017 --> 改進的沙盒模式警報，可顯示具有多個儲存的正確警報。

![已修復問題](../assets/fix.svg)<!-- Issue PAY-2742 --> 您現在可以在商店視圖層啟用和禁用可用的付款方法（如Venmo）。 以前，您只能按網站配置付款方式。

![已修復問題](../assets/fix.svg)<!-- Issue PAY-2277 --> 你現在可以選擇 [啟用或禁用單個PayPal智慧按鈕](settings.md#paypal-smart-buttons)。

![已修復問題](../assets/fix.svg)<!-- Issue PAY-2561 --> 以前刪除的產品不會出現在購物車中 _審閱訂單_ 的子菜單。

![已知問題](../assets/bug.svg)<!-- Issue PAY-2842 --> Test信用卡交易記錄 [可能因PayPal而失敗](https://support.magento.com/hc/en-us/articles/5201041963917) 在沙箱環境中處理付款時。

## v1.0.0

![新建](../assets/new.svg)<!-- Issue PAY-2127 --> 一般可用性發佈 — [[!DNL Payment Services]](https://marketplace.magento.com/magento-payment-services.html) 現在與 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 版本2.4.0到2.4.3-p1。

![新建](../assets/new.svg)<!-- Issue PAY-124 --> 的 [!DNL Payment Services] 擴展 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 可以安裝 [[!DNL Adobe Commerce] 雲基礎架構](install.md#adobe-commerce-on-cloud-infrastructure) 或 [內部](install.md#on-premises) 實例。 這些方法需要使用命令行介面。

![新建](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] 支援 [沙盒帳戶](sandbox.md) 允許商戶在test模式下評估擴展。

![新建](../assets/new.svg)<!-- Issue PAY-666 --> 商家可以 [配置Payment Services](settings.md) 基本支付行為的擴展 [`Authorize and Capture`](production.md#set-payment-services-as-payment-method) 在沙盒或生產環境之間切換。

![新建](../assets/new.svg)<!-- Issue PAY-780 --> 您的購物者可以 [!DNL Payment Services] 或 [手動訂單建立](create-order.md)。

![新建](../assets/new.svg)<!-- Issue PAY-1856 --> 全面報告，通過 [訂單付款狀態](order-payment-status.md) 和 [支付報告](payouts.md)，可用於 [!DNL Payment Services] 讓你清楚地瞭解你商店的訂單和相關付款。

![新建](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] 支援基於總處理量的靈活分層定價，適用於任何商家。

![新建](../assets/new.svg)<!-- Issue PAY-1443 --> 您可以輕鬆 [定制外觀](payments-options.md) 支付服務擴展的PayPal智慧按鈕和信用卡欄位。

![已知問題](../assets/bug.svg)<!-- Issue PAY-2473 --> 使用 [合成器密鑰不正確](https://support.magento.com/hc/en-us/articles/4406603542541) 在安裝擴展時防止用戶 [驗證](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 正確 `MAGEID`。

![已知問題](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] 報告 [無法立即同步](https://support.magento.com/hc/en-us/articles/4406114741517)。

![已知問題](../assets/bug.svg)<!-- Issue PAY-2475 --> 您 [PayPal沙盒帳戶](https://support.magento.com/hc/en-us/articles/4406954952461) 為 [!DNL Payment Services] 如果在登錄期間建立該帳戶，則無法驗證。
