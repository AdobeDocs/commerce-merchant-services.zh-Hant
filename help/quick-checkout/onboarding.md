---
title: 「 [!DNL Quick Checkout] 適用於Adobe Commerce擴充功能」
description: 「了解 [!DNL Quick Checkout] 可讓您的Adobe Commerce執行個體受益，以及如何成功上線並設定擴充功能。」
exl-id: 8caf746c-e31b-4331-8b0d-ea0f1e545bdd
source-git-commit: bd02a8083d3f4c9cb0422b27d61bd5462187ffc3
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# [!DNL Quick Checkout] 入門

若要開始使用 [!DNL Quick Checkout] 針對Adobe Commerce擴充功能，您必須完成幾個入門步驟，才能使用我們的結帳功能連線您的執行個體。

![快速結帳](assets/overview-admin-panel.png)

1. [取得擴充功能](#get-extension).
1. [建立生產或沙箱商戶帳戶，使用 [!DNL Bolt]](#create-account-with-bolt). 提供驗證您身分的所有必要資訊。
1. [提供唯一 [!DNL API Key] 和 [!DNL Publishable Key]](#obtain-api-credentials) 產生於 [!DNL Bolt].
1. [在 [!DNL Bolt] 帳戶](#configure-payment-providers).
1. [將「啟用」下拉式清單設為「是」](#enable-extension) 啟動擴充功能。
1. [定義服務設定](#complete-admin-configuration) 若要設定 [!DNL Quick Checkout] 擴充功能。
1. [按一下儲存設定](#enable-live-quick-checkout) 按鈕以啟用擴充功能。
1. 將範圍切換為 **主要網站** 和 [按一下設定回呼URL](#check-shopper-valid-account) 按鈕。

如果Gainsight已啟用，便會觸發 **參觀** 按鈕 [!DNL Quick Checkout] 管理面板關於 [!DNL Quick Checkout] Adobe Commerce:

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** >進階：

   ![快速結帳](assets/gainsight-admin.png)

如果未啟用Gainsight，請繼續入門步驟。

請參閱 [[!DNL Quick Checkout] 管理面板](../quick-checkout/admin-panel.md) 主題以取得詳細資訊。

>[!NOTE]
>
> 如果您未設定 [!DNL Bolt] 帳戶無法設定沙箱或生產環境。

## 必要條件

若要使用 [!DNL Quick Checkout]，您必須具備下列 [!DNL Bolt]:

- 支援的支付提供商
- 中的商家和生產帳戶 [!DNL Bolt]
- API和 [!DNL Publishable key] 產生於 [!DNL Bolt]

請參閱 [必要條件](../quick-checkout/prerequisites.md) 主題以取得詳細資訊。

請參閱 [API憑證](#obtain-api-credentials) 了解如何建立或存取 [!DNL API keys] 例項。

## 取得擴充功能

請參閱 [安裝](../quick-checkout/install.md) 主題，以取得擴充功能的詳細資訊。

## 使用建立帳戶 [!DNL Bolt]

在設定 [!DNL Quick Checkout] 在您的Adobe Commerce管理員中，必須建立 [沙箱](https://merchant-sandbox.bolt.com/register?platform=magento2){target=&quot;_blank&quot;}和 [生產](https://merchant.bolt.com/register?platform=magento2){target=&quot;_blank&quot;}中的商家帳戶 [!DNL Bolt]. 提供在中建立帳戶所需的所有詳細資訊 [!DNL Bolt].

請參閱 [測試與驗證](../quick-checkout/testing.md) 主題以取得詳細資訊。

## 取得API憑證

若要使用 [!DNL Quick Checkout] 您需要 [!DNL Bolt] 唯一索引鍵和 [!DNL signing secret]. 取得下列內容 [!DNL API keys] 瀏覽至 **開發人員** > **API** > **金鑰** 在 **螺栓商家儀表板**.

- [!DNL API key]:後端用來與互動的私密金鑰 [!DNL Bolt] API。
- [!DNL Publishable key]:前端用來與 [!DNL Bolt] API。
- [!DNL Signing secret]:用於對從接收到的請求進行簽名驗證 [!DNL Bolt].

   ![快速結帳](assets/account-credentials.png)

請參閱 [[!DNL Bolt] 環境詳細資訊](https://help.bolt.com/developers/references/environment-details/#about-keys){target=&quot;_blank&quot;}頁面，以了解金鑰和簽名密碼 [!DNL Bolt] 針對 [!DNL Quick Checkout] 擴充功能。

>[!CAUTION]
>
> 您必須建立 [!DNL API keys] 適用於沙箱和生產環境。

## 配置支付提供程式

要連接您的支付服務提供商，請遵循 [處理器設定](https://help.bolt.com/integrations/adobe-quick-checkout/set-up/){target=&quot;_blank&quot;}開發人員 [!DNL Bolt] 頁面。

## 啟用擴充功能

1. 在 _管理_ 邊欄，轉到 **商店** > _設定_ > **設定**.
1. 在左側面板中，展開 **銷售** 選取 **結帳**.
1. 在 [!DNL Quick Checkout] 檢視，設定 **啟用** to `Yes`.

![快速結帳](assets/quick-checkout-view-no-enable.png)

>[!CAUTION]
>
> 只有在 **啟用** 設為 `Yes`.

1. 選取要使用的方法（沙箱或生產）。

   - 用於測試和開發用途的沙箱
   - 處理與即時支付處理者的事務處理的生產

1. 提供您的唯一API後驗證憑證，並 [!DNL Publishable keys].

![快速結帳](assets/quick-checkout-main-view-react.png)

請參閱 [設定](../quick-checkout/settings-quick-checkout.md) 主題，以取得 [!DNL Quick Checkout] Adobe Commerce擴充功能。

>[!CAUTION]
>
> 您必須提供唯一API，並 [!DNL Publishable] 在啟用擴充功能前，金鑰（否則客戶將看到付款表單，無法下訂單）。

## 完成管理配置

1. 在 _管理_ 邊欄，導覽至 **商店** > **設定** > **結帳** 存取「一般結帳管理員」設定頁面。
1. 在 _服務設定_ 一節，提供啟用擴充功能所需的所有詳細資訊。
1. 設定 _付款活動_ 至任一選項：

   - `Authorize`:請勿在授權時自動捕獲事務。
   - `Authorize and Capture`:根據授權自動捕獲事務。

如需Adobe Commerce標準結帳選項的詳細資訊，請參閱 [簽出](https://docs.magento.com/user-guide/configuration/sales/checkout.html) 主題。

## 啟用即時快速結帳

若要啟用 [!DNL Quick Checkout] Adobe Commerce擴充功能：

1. 檢查 [!UICONTROL Enable] 下拉式清單設為 **是** 啟動擴充功能。
1. 按一下 **儲存設定**.

## 檢查購物者有效帳戶

檢查購物者是否具有 [!DNL Bolt] 帳戶：

1. 將範圍切換為 **主要網站**.
1. 按一下 **設定回呼URL** 按鈕。 如此可啟用 [!DNL Bolt] 以判斷購物者是否有帳戶。 如果出現，則會顯示OTP彈出窗口。

>[!CAUTION]
>
> 將範圍切換到 **主要網站** 確保設定正確的URL。 每個網站可以有多個網域。

請參閱 [站點、儲存和查看範圍](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings){target=&quot;_blank&quot;}主題，以取得Adobe Commerce中範圍的詳細資訊。

## 取得協助

入門程式旨在引導您完成設定及啟用 [!DNL Express Checkout] 功能。

請透過以下連絡Adobe Commerce支援： [Adobe Commerce說明中心](https://support.magento.com/hc/en-us/articles/360000913794-Adobe-Commerce-Help-Center-User-Guide) 以求任何協助。

請參閱 [測試與驗證](../quick-checkout/testing.md) 主題以取得詳細資訊。
