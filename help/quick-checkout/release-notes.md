---
title: '"[!DNL Quick Checkout] 發行說明"'
description: 查看發行說明以瞭解有關所有 [!DNL Quick Checkout] 版本。
source-git-commit: dc13c1e38c92341cfd3221a72e6568220b44690a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 發行說明

本發行說明描述了 [!DNL Quick Checkout] 包括：

![新建](../assets/new.svg) 新功能
![已修復問題](../assets/fix.svg) 修復和改進
![已知問題](../assets/bug.svg) 已知問題

請參閱 [即將發佈的版本](https://devdocs.magento.com/release/) 瞭解發行計畫和支援。

請參閱 [可用性](https://devdocs.magento.com/release/availability.html) 以瞭解產品相容性。

## v1.0.0

![新建](../assets/new.svg)<!-- Issue BOLT-341 --> 一般可用性發佈 — [[!DNL Quick Checkout]](https://marketplace.magento.com/magento-quick-checkout.html) 現在與Adobe Commerce版2.4.1至2.4.4相容。

![新建](../assets/new.svg)<!-- Issue BOLT-340 --> 的 [!DNL Quick Checkout] Adobe Commerce可以為Adobe Commerce [雲基礎架構](install.md#adobe-commerce-on-cloud-infrastructure) 或 [本地](install.md#on-premises) 實例。 這些方法需要使用命令行介面。

![新建](../assets/new.svg)<!-- Issue BOLT-1 --> 的 [!DNL Quick Checkout] 為Adobe Commerce提供了優化的店面 [按一下簽出體驗](overview.md) 沒有為消費者需要的填充欄位。

![新建](../assets/new.svg)<!-- Issue BOLT-1 --> 的 [!DNL Quick Checkout] Adobe Commerce自動識別網路中的每個購物者 [按一下購買](checkout-flow.md) 就在你的網站上。

![新建](../assets/new.svg)<!-- Issue BOLT-218 --> [!DNL Quick Checkout] Adobe Commerce支援 [沙盒帳戶](testing.md#testing-in-sandbox) 允許商戶在test模式下評估擴展。

![新建](../assets/new.svg)<!-- Issue BOLT-780 --> 您的購物者可以通過 [[!DNL Quick Checkout]](checkout-page.md) 或通過 [手動訂單建立](create-order-admin.md)。

![新建](../assets/new.svg)<!-- Issue BOLT-666 --> 商家可以配置 [!DNL Quick Checkout] 基本付款活動，如 [`Authorize and Capture` 或 `Authorize` ](onboarding.md#complete-admin-configuration)或在沙盒和生產環境之間切換。

![已知問題](../assets/bug.svg)<!-- Issue BOLT-342 --> 使用 [合成器密鑰不正確](https://support.magento.com/hc/en-us/articles/6909450342541) 安裝期間 [!DNL Quick Checkout] 阻止用戶 [驗證](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 正確 `MAGEID`。
