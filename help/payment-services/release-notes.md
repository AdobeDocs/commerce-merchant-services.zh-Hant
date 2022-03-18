---
title: '"[!DNL Payment Services] 發行說明"'
description: 查看發行說明以瞭解有關所有 [!DNL Payment Services] 版本。
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
source-git-commit: eb8fdba65b4b64730d0ad4fa6e0c9b64bdadc7df
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 1%

---

# 發行說明

本發行說明描述了 [!DNL Payment Services] 包括：

![新建](../assets/new.svg) 新功能
![已修復問題](../assets/fix.svg) 修復和改進
![已知問題](../assets/bug.svg) 已知問題

## v1.0.0

![新建](../assets/new.svg)<!-- Issue PAY-2127 --> 一般可用性版本。 [付款服務](https://marketplace.magento.com/magento-payment-services.html) 現在與Adobe Commerce和Magento Open Source2.4.0至2.4.3-p1版相容。

![新建](../assets/new.svg)<!-- Issue PAY-124 --> 的 [!DNL Payment Services] 可以安裝Adobe Commerce擴展和Magento Open Source [Adobe Commerce在雲基礎架構上](install.md#magento-commerce-cloud) 或 [內部](install.md#on-premises) 實例。 這些方法需要使用命令行介面。

![新建](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] 支援 [沙盒帳戶](onboard.md#enable-sandbox-testing) 允許商戶在test模式下評估擴展。

![新建](../assets/new.svg)<!-- Issue PAY-666 --> 商家可以 [配置付款服務](configure-admin.md) 具有基本付款行為的擴展（例如將身份驗證捕獲和在沙箱或生產環境之間切換）。

![新建](../assets/new.svg)<!-- Issue PAY-780 --> 購物者可以 [!DNL Payment Services] 或者你可以通過電話接下訂單 [建立整個訂單](create-order.md) 在管理員中。

![新建](../assets/new.svg)<!-- Issue PAY-1856 --> [!DNL Payment Services] 為商家提供全面的報告，以便您能夠清楚地查看您的商店訂單和付款。

![新建](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] 支援適合任何商家的分層定價（基於TPV）。

![新建](../assets/new.svg)<!-- Issue PAY-1443 --> 您可以為PayPal按鈕和CC欄位定制外觀和感覺 [付款服務](https://devdocs.magento.com/payment-services/customize-buttons-messaging.html) 擴展。

![已知問題](../assets/bug.svg)<!-- Issue PAY-2473 --> 使用 [不正確的作曲家密鑰](https://support.magento.com/hc/en-us/articles/4406603542541) 在安裝擴展時，用戶 [驗證](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 正確 `MAGEID`。

![已知問題](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] [報告](https://support.magento.com/hc/en-us/articles/4406114741517) 付款和訂單付款狀態可能無法立即同步。

![已知問題](../assets/bug.svg)<!-- Issue PAY-2475 --> [PayPal沙盒帳戶](https://support.magento.com/hc/en-us/articles/4406954952461) 為 [!DNL Payment Services] 無法驗證。
