---
title: '" [!DNL Quick Checkout] Adobe Commerce分機」'
description: 「瞭解 [!DNL Quick Checkout] 將有利於您的Adobe Commerce實例以及如何成功安裝和設定擴展。」
exl-id: 8caf746c-e31b-4331-8b0d-ea0f1e545bdd
source-git-commit: ac55bf6354c8f5569ad83dc0ac2671b34c98d303
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# [!DNL Quick Checkout] 登機

開始使用 [!DNL Quick Checkout] 對於Adobe Commerce分機，您必須完成幾個單機步驟，以便將您的實例與我們的簽出功能連接起來。

1. [獲取擴展](#get-extension)。
1. [使用建立生產或沙盒商戶帳戶 [!DNL Bolt]](#create-account-with-bolt)。 提供驗證您身份所需的所有資訊。
1. [提供唯一 [!DNL API Key] 和 [!DNL Publishable Key] 生成 [!DNL Bolt]](#obtain-api-credentials)。
1. [在 [!DNL Bolt] 帳戶](#configure-payment-providers)。
1. [將「啟用」下拉清單設定為「是」](#enable-extension) 來激活擴展。
1. [定義服務設定](#complete-admin-configuration) 配置 [!DNL Quick Checkout] 擴展。
1. [按一下「Save Config（保存配置）」按鈕](#enable-live-quick-checkout) 啟用擴展。

>[!NOTE]
>
> 如果未配置 [!DNL Bolt] 無法設定沙盒或生產環境的帳戶。

## 先決條件

為了使用 [!DNL Quick Checkout]，您必須具有以下 [!DNL Bolt]:

- 支援的付款提供方
- 中的商家和生產帳戶 [!DNL Bolt]
- API和 [!DNL Publishable key] 生成 [!DNL Bolt]

請參閱 [先決條件](../quick-checkout/prerequisites.md) 的子菜單。

請參閱 [API憑據](#obtain-api-credentials) 瞭解如何建立或訪問 [!DNL API keys] 比如你。

## 獲取擴展

查看 [安裝](../quick-checkout/install.md) 主題，瞭解有關獲取擴展的詳細資訊。

## 建立帳戶 [!DNL Bolt]

在配置 [!DNL Quick Checkout] 在您的Adobe Commerce管理員中，需要建立 [沙坑](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;和 [生產](https://merchant.bolt.com/register){target=&quot;_blank&quot;中的商家帳戶 [!DNL Bolt]。 提供建立帳戶所需的所有詳細資訊 [!DNL Bolt]。

請參閱 [test和驗證](../quick-checkout/testing.md) 的子菜單。

## 獲取API憑據

使用 [!DNL Quick Checkout] 你需要 [!DNL Bolt] 唯一鍵。 獲取以下內容 [!DNL API keys] 通過導航 **開發人員** > **API** > **鍵** 的 **螺栓商家儀表板**。

- [!DNL API key]:後端用於與交互的私鑰 [!DNL Bolt] API。
- [!DNL Publishable key]:前端用於與交互的密鑰 [!DNL Bolt] API。

查看 [[!DNL Bolt] 環境詳細資訊](https://help.bolt.com/developers/references/environment-details/#about-keys){target=&quot;_blank&quot;}頁，以瞭解API和 [!DNL Publishable keys] 為 [!DNL Quick Checkout] 擴展。

>[!CAUTION]
>
> 必須建立 [!DNL API keys] 用於沙盒和生產環境。

## 配置付款提供方

要連接您的支付服務提供商，請按照 [處理器設定](https://help.bolt.com/integrations/adobe-quick-checkout/set-up/){target=&quot;_blank&quot;開發人員 [!DNL Bolt] 的子菜單。

## 啟用擴展

1. 在 _管理_ 邊欄，轉到 **商店** > _設定_ > **配置**。
1. 在左面板中，展開 **銷售** 選擇 **簽出**。

   ![快速簽出](assets/admin-view.png)

1. 在 [!DNL Quick Checkout] 視圖，設定 **啟用** 至 `Yes`。
1. 選擇要使用的方法（沙盒或生產）。

   - 用於測試和開發目的的沙盒
   - 使用即時付款處理器處理交易記錄的生產

1. 在提供您的唯一API和 [!DNL Publishable keys]。

>[!CAUTION]
>
> 必須提供唯一的API和 [!DNL Publishable keys] 在啟用分機之前，否則客戶將看到付款表，無法下訂單。

## 完成管理配置

1. 在 _管理_ 邊欄，導航 **商店** > **配置** > **簽出** 訪問常規「簽出管理」配置頁。
1. 在 _服務設定_ 部分，提供啟用擴展所需的所有詳細資訊。
1. 設定 _付款活動_ 選項之一：

   - `Authorize`:不要在授權時自動捕獲事務。
   - `Authorize and Capture`:在授權時自動捕獲事務。

有關Adobe Commerce標準結帳選項的詳細資訊，請參閱 [簽出](https://docs.magento.com/user-guide/configuration/sales/checkout.html) 主題。

## 啟用即時快速簽出

啟用 [!DNL Quick Checkout] 對於Adobe Commerce分機：

1. 檢查 [!UICONTROL Enable] 下拉清單設定為 **是** 來激活擴展。
1. 按一下 **保存配置**。

## 獲取幫助

登機過程旨在指導您完成設定和啟用 [!DNL Express Checkout] 功能。 通過您指定的Slack聯繫Adobe Commerce工程團隊 [AdobeBeta程式渠道](http://adobe-beta-programs.slack.com/) 幫助渠道。

查看 [test和驗證](../quick-checkout/testing.md) 的子菜單。
