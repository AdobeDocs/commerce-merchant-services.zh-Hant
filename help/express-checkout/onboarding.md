---
title: 在 [!DNL Express Checkout] Adobe Commerce分機
description: 瞭解 [!DNL Express Checkout] 將有利於您的Adobe Commerce實例以及如何成功安裝和設定擴展。
exl-id: 8caf746c-e31b-4331-8b0d-ea0f1e545bdd
source-git-commit: d8302d2d652b4e2380cc862183e58cbd2cca831b
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 0%

---

# [!DNL Express Checkout] 登機

>[!IMPORTANT]
>
> 此功能僅適用於早期採用者計畫(EAP)用戶，尚不適用於所有客戶。 目前僅限於美國客戶。 請聯繫Adobe Commerce支援部門以獲取幫助和問題。

開始使用 [!DNL Express Checkout] 對於Adobe Commerce分機，您必須完成幾個單機步驟，以便將您的實例與我們的簽出功能連接起來。

1. [獲取擴展](#get-extension)。
1. [使用Bolt建立生產或沙盒商戶帳戶](#create-account-with-bolt)。 提供驗證您身份所需的所有資訊。
1. [提供在Bolt中生成的唯一API密鑰和可發佈密鑰](#obtain-api-credentials)。
1. [在Bolt帳戶中設定付款提供商](#configure-payment-providers)。
1. [將「啟用」下拉清單設定為「是」](#enable-extension) 來激活擴展。
1. [定義服務設定](#complete-admin-configuration) 配置 [!DNL Express Checkout] 擴展。
1. [按一下「Save Config（保存配置）」按鈕](#enable-live-express-checkout) 啟用擴展。

>[!NOTE]
>
> 如果未配置螺栓帳戶（上面的步驟2），則無法設定沙箱或生產環境。

## 先決條件

為了使用 [!DNL Express Checkout]，對於「螺栓」(Bolt)，必須具有以下功能：

- 支援的付款提供方
- Bolt中的商家和生產帳戶
- API和在Bolt中生成的可發佈密鑰

請參閱 [先決條件](../express-checkout/prerequisites.md) 的子菜單。

請參閱 [API憑據](#obtain-api-credentials) 瞭解如何為實例建立或訪問API密鑰。

## 獲取擴展

查看 [安裝](../express-checkout/install.md) 主題，瞭解有關獲取擴展的詳細資訊。

## 使用Bolt建立帳戶

在配置 [!DNL Express Checkout] 在您的Adobe Commerce管理員中，需要建立 [生產](https://merchant.bolt.com/register){target=&quot;_blank&quot;和 [沙坑](https://merchant-sandbox.bolt.com/register)Bolt中的{target=&quot;_blank&quot;}商戶帳戶。 提供在Bolt中建立帳戶所需的所有詳細資訊。

請參閱 [test和驗證](../express-checkout/testing.md) 的子菜單。

## 獲取API憑據

使用 [!DNL Express Checkout] 需要Bolt的唯一鍵。 導航至 **開發人員** > **API** > **鍵** 的 **螺栓商家儀表板**。

- API密鑰：後端用於與Bolt API交互的私鑰。
- 可發佈密鑰：前端用於與Bolt API交互的密鑰。

查看 [螺栓環境詳細資訊](https://help.bolt.com/developers/references/environment-details/#about-keys){target=&quot;_blank&quot;}頁，以瞭解API和可發佈的鍵 [!DNL Express Checkout] 擴展。

>[!CAUTION]
>
> 必須為沙盒和生產環境建立API密鑰。

## 配置付款提供方

要連接您的支付服務提供商，請按照 [處理器設定](https://help.bolt.com/integrations/adobe-express-checkout/set-up/){target=&quot;_blank&quot;}開發人員Bolt頁。

## 啟用擴展

1. 在 _管理_ 邊欄，導航 **商店** > **配置** > **簽出** 訪問「簽出管理」配置頁。

![快速結帳](../assets/admin-view.png)

1. 在 [!DNL Express Checkout] 視圖，設定 **啟用** 至 `Yes`。
1. 選擇要使用的方法（生產或沙盒）。
1. 提供唯一API和可發佈密鑰後驗證憑據。

>[!CAUTION]
>
> 在啟用擴展之前，必須提供唯一的API和可發佈密鑰，否則客戶將看到付款表單，無法下訂單。

## 完成管理配置

1. 在 _管理_ 邊欄，導航 **商店** > **配置** > **簽出** 訪問常規「簽出管理」配置頁。
1. 在 _服務設定_ 部分，提供啟用擴展所需的所有詳細資訊。
1. 設定 _付款活動_ 為：

   - 授權：不要在授權時自動捕獲事務。
   - 授權和捕獲：在授權時自動捕獲事務。

有關Adobe Commerce標準結帳選項的詳細資訊，請參閱 [簽出](https://docs.magento.com/user-guide/configuration/sales/checkout.html) 主題。

## 啟用Live Express結帳

啟用 [!DNL Express Checkout] 對於Adobe Commerce分機：

1. 按一下 **保存配置**。

## 獲取幫助

登機過程旨在指導您完成設定和啟用所有 [!DNL Express Checkout] 功能。 請聯繫Adobe Commerce支援部門以獲取幫助和問題。

請參閱 [test和驗證](../express-checkout/testing.md) 的子菜單。
