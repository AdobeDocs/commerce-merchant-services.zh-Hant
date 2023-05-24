---
title: 「加入 [!DNL Quick Checkout] 適用於Adobe Commerce擴充功能」
description: 「瞭解如何 [!DNL Quick Checkout] 可能會讓您的Adobe Commerce執行個體受益，並瞭解如何成功入門和設定擴充功能。」
exl-id: 8caf746c-e31b-4331-8b0d-ea0f1e545bdd
source-git-commit: b89427124cf76e7f36076454949191ee1d88f52c
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 0%

---

# [!DNL Quick Checkout] 入門

若要開始使用 [!DNL Quick Checkout] 針對Adobe Commerce擴充功能，您必須完成一些上線步驟，將您的執行個體與我們的簽出功能連線。

![快速簽出](assets/overview-admin-panel.png)

1. [取得擴充功能](#get-extension).
1. [建立生產或沙箱商家帳戶，使用 [!DNL Bolt]](#create-account-with-bolt). 提供驗證身分的所有必要資訊。
1. [提供唯一的 [!DNL API Key] 和 [!DNL Publishable Key]](#obtain-api-credentials) 產生於 [!DNL Bolt].
1. [在中設定付款提供者 [!DNL Bolt] 帳戶](#configure-payment-providers).
1. [將「啟用」下拉式清單設定為「是」](#enable-extension) 以啟動擴充功能。
1. [定義您的服務設定](#complete-admin-configuration) 設定 [!DNL Quick Checkout] 副檔名。
1. [按一下「儲存設定」](#enable-live-quick-checkout) 按鈕以啟用擴充功能。
1. 將範圍切換至 **主要網站** 和 [按一下設定回呼URL](#check-shopper-valid-account) 按鈕。

如果啟用了Gainsight，則會觸發 **進行導覽** 中的按鈕 [!DNL Quick Checkout] 管理面板關於 [!DNL Quick Checkout] 若為Adobe Commerce：

1. 於 _管理員_ 側欄，前往 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** >進階：

   ![快速簽出](assets/gainsight-admin.png)

如果未啟用Gainsight，請繼續入門步驟。

請參閱 [[!DNL Quick Checkout] 管理面板](../quick-checkout/admin-panel.md) 主題以取得詳細資訊。

>[!NOTE]
>
> 如果您未設定 [!DNL Bolt] 無法設定沙箱或生產環境的帳戶。

## 必要條件

為了使用 [!DNL Quick Checkout]，您必須擁有下列專案可用於 [!DNL Bolt]：

- 支援的付款提供者
- 中的商家和生產帳戶 [!DNL Bolt]
- API和 [!DNL Publishable key] 產生於 [!DNL Bolt]

請參閱 [必備條件](../quick-checkout/prerequisites.md) 主題以取得詳細資訊。

另請參閱 [API認證](#obtain-api-credentials) 以瞭解如何建立或存取 [!DNL API keys] 為您的執行個體而設定。

## 取得擴充功能

請參閱 [安裝](../quick-checkout/install.md) 主題，以取得擴充功能的詳細資訊。

## 建立帳戶使用 [!DNL Bolt]

設定之前 [!DNL Quick Checkout] 在您的Adobe Commerce管理員中，必須建立 [沙箱](https://merchant-sandbox.bolt.com/register?platform=magento2){target="_blank"} and [production](https://merchant.bolt.com/register?platform=magento2){target="_blank"}  中的商家帳戶 [!DNL Bolt]. 提供所有在中建立帳戶所需的詳細資料 [!DNL Bolt].

請參閱 [測試及驗證](../quick-checkout/testing.md) 主題以取得詳細資訊。

## 取得API認證

若要使用 [!DNL Quick Checkout] 您需要 [!DNL Bolt] 唯一索引鍵和 [!DNL signing secret]. 取得下列內容 [!DNL API keys] 瀏覽至 **開發人員** > **API** > **金鑰** 在 **Bolt商家儀表板**.

- [!DNL API key]：後端用來與互動的私密金鑰 [!DNL Bolt] API。
- [!DNL Publishable key]：前端用來與互動的金鑰 [!DNL Bolt] API。
- [!DNL Signing secret]：用於對從收到的請求進行簽名驗證 [!DNL Bolt].

   ![快速簽出](assets/account-credentials.png)

請參閱 [[!DNL Bolt] 環境詳細資料](https://help.bolt.com/developers/references/environment-details/#about-keys){target="_blank"} 要瞭解金鑰和簽署密碼的頁面，請參閱 [!DNL Bolt] 的 [!DNL Quick Checkout] 副檔名。

>[!CAUTION]
>
> 您必須建立 [!DNL API keys] 適用於沙箱和生產環境。

## 設定付款提供者

若要連線您的支付服務提供者，請遵循以下說明的步驟： [處理器設定](https://help.bolt.com/integrations/adobe-quick-checkout/set-up/){target="_blank"} 開發人員 [!DNL Bolt] 頁面。

## 啟用擴充功能

1. 於 _管理員_ 側欄，前往 **商店** > _設定_ > **設定**.
1. 在左側面板中，展開 **銷售** 並選取 **簽出**.
1. 在 [!DNL Quick Checkout] 檢視，設定 **啟用** 至 `Yes`.

![快速簽出](assets/quick-checkout-view-no-enable.png)

>[!CAUTION]
>
> 快速簽出欄位僅在 **啟用** 設為 `Yes`.

1. 選取要使用的方法（沙箱或生產）。

   - 用於測試和開發目的的沙箱
   - 與即時付款處理程式處理交易的生產

1. 提供您獨特的API並驗證憑證後 [!DNL Publishable keys].

![快速簽出](assets/quick-checkout-main-view.png)

請參閱 [設定](../quick-checkout/settings-quick-checkout.md) 主題，以瞭解更多有關設定選項的 [!DNL Quick Checkout] 適用於Adobe Commerce擴充功能。

>[!CAUTION]
>
> 您必須提供唯一的API，而且 [!DNL Publishable] 金鑰，然後再啟用擴充功能，否則客戶會看到付款表單，且無法下訂單。

## 完成管理員設定

1. 於 _管理員_ 側欄，導覽至 **商店** > **設定** > **簽出** 以存取一般簽出管理設定頁面。
1. 在 _服務設定_ 區段，提供啟用擴充功能所需的所有詳細資訊。
1. 設定 _付款動作_ 至任一選項：

   - `Authorize`：請勿在授權時自動擷取交易。
   - `Authorize and Capture`：在授權時自動擷取交易。

如需Adobe Commerce標準結帳選項的詳細資訊，請參閱 [簽出](https://docs.magento.com/user-guide/configuration/sales/checkout.html) 主題。

## 啟用即時快速簽出

若要啟用 [!DNL Quick Checkout] 對於Adobe Commerce擴充功能：

1. 檢查 [!UICONTROL Enable] 下拉式清單已設定為 **是** 以啟動擴充功能。
1. 按一下 **儲存設定**.

## 檢查購物者有效帳戶

若要檢查購物者是否擁有 [!DNL Bolt] 帳戶：

1. 將範圍切換為 **主要網站**.
1. 按一下 **設定回呼URL** 按鈕。 如此可啟用 [!DNL Bolt] 以判斷購物者是否有帳戶。 如果是，就會出現OTP快顯視窗。

   >[!CAUTION]
   >
   > 將範圍切換到 **主要網站** 會確保設定正確的URL。 每個網站可以有多個網域。

請參閱 [網站、存放區和檢視範圍](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings){target="_blank"} 主題以取得有關Adobe Commerce中的範圍的詳細資訊。

## 設定服務設定

![快速簽出](assets/service-settings.png)

1. 設定 **啟用簽出追蹤** 至 `Yes`.

   >[!CAUTION]
   >
   > 停用此選項將會影響報告，因為Adobe Commerce不允許與Bolt共用簽出追蹤資訊。

1. 選取 **登入後的下一個階段** 在客戶登入後變更導覽流程的選項。 依預設，其設定為 **付款** 頁面。
1. 定義條件 [!DNL Quick Checkout] 允許用於 **自動登入** 結帳期間。 預設會啟用自動登入 [!DNL Bolt] 網路。

   >[!NOTE]
   >
   > 另請參閱 [Bolt的「啟用自動登入」檔案](https://help.bolt.com/products/embedded/direct-api/auto-login/) 以取得詳細資訊。

## 取得協助

入門流程旨在引導您完成設定和啟用 [!DNL Express Checkout] 功能。

請聯絡Adobe Commerce支援，透過 [Adobe Commerce說明中心](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html) 以取得任何協助。

請參閱 [測試及驗證](../quick-checkout/testing.md) 主題以取得詳細資訊。
