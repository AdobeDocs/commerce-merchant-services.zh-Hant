---
title: 啟用 [!DNL Payment Services] 用於生產
description: 啟用以完成入門流程 [!DNL Payment Services] 用於生產。
exl-id: 3b1269e8-127b-47f8-9738-9722a5737c63
feature: Payments, Checkout, Configuration, Install
source-git-commit: 5fe23b5aba9ad0a2a6c995fa6ade78f46fe7e3e1
workflow-type: tm+mt
source-wordcount: '1006'
ht-degree: 0%

---

# 啟用 [!DNL Payment Services] 用於生產

您可以將服務投入生產並完成 [上線流程](onboard.md)，依照本主題中的步驟，在您：

* [安裝](install.md) 支付服務擴充功能
* [設定並連線](connect.md) 您的執行個體
* [設定](sandbox.md) 和 [測試](test-validate.md) 您的沙箱

## 設定 [!DNL Payment Services] 作為付款方式

在您之後 [設定您的Commerce服務](connect.md#configure-commerce-services) 並啟用 [沙箱測試](sandbox.md#enable-sandbox-testing) 或 [即時付款](#enable-live-payments)，您必須設定 [!DNL Payment Services] 作為您的付款方式。

1. 在 _管理員_ 側欄，前往 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 按一下 **[!UICONTROL Enable Payment Services]**.

   如果您尚未設定，便會顯示此選項 [!DNL Payment Services] 作為一或多個網站的付款方式。

   您將被導向至「首頁」檢視中的設定區域，相關的選項會展開(**[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Settings]_)，您可以在此處啟用 [!DNL Payment Services] 選項作為您的 [付款方法](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html){target="_blank"}.

1. 在 _[!UICONTROL General Configuration]_，設定&#x200B;**[!UICONTROL Enable]**至 `Yes`.
1. 設定 **[!UICONTROL Payment Action]**，二者 _[!UICONTROL Credit Card Fields]_和_[!UICONTROL PayPal payment buttons]_，變更為下列其中一項：

   | 設定 | 說明 |
   |---|---|
   | `Authorize` | 核准購買並保留資金。 此金額必須等到商家「擷取」後才會提取。 |
   | `Authorize and Capture` | 核准購買且商家「擷取」資金。 |

   >[!IMPORTANT]
   >
   >[!DNL Payment Services] 支援部分擷取。 商家可以部份擷取訂單的（商業發票）部分。 例如，您可以分別擷取每個專案，或現在擷取一個專案，稍後擷取其餘的專案。

1. 按一下 **[!UICONTROL Save]**.
1. 按一下 **[!UICONTROL Go to Payment Services]** 將重新導向至 [!DNL Payment Services] 首頁。
1. [清除您的快取](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cache-management.html).

   應在每次設定變更後進行清除。

另請參閱 [設定付款服務](settings.md) 有關設定信用卡欄位和PayPal付款按鈕的詳細資訊。

## 完成商家入門

若要讓您的商店上線付款服務，下一步就是完成上線。

支付服務提供 [**進階** （完整支援）和 **標準** （快速結帳）付款選項](../payment-services/payments-options.md#standard-vs-advanced-payments-experience) 和上線流程，取決於您營運的國家/地區以及您偏好的付款體驗。

1. 在 _管理員_ 側欄，前往 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 按一下 **[!UICONTROL Live onboarding]**.

   如果您尚未完成的即時上線，即可看到此選項 [!DNL Payment Services].

1. 在 _選取您的國家/地區_ 強制回應視窗，選取您營業的來源國家/地區。

   「付款服務」針對以下專案的所有付款選項提供完整支援： [五個國家/地區](../payment-services/overview.md#availability) 目前。 Payment Services為國家/地區清單中代表的所有其他國家/地區提供快速結帳功能（付款選項的子集）。

   您從清單中選擇的國家/地區將決定支付選項和上線流程 — [進階](#advanced-onboarding) （完整支援）或 [標準](#standard-onboarding) （快速出庫） — 可供您使用。

>[!TIP]
>
> 選擇並繼續上線選項（標準或進階）後，您必須重新完成上線，才能從初始選擇升級或降級。

### 進階上線

此上線流程適用於以下市場的商家： [完全支援的國家/地區](../payment-services/overview.md#availability).

選取國家/地區後：

1. 在出現的強制回應視窗中，選取 **進階**.

   對於 **標準** 選項，繼續前往 [標準上線流程](#standard-onboarding).

1. 按一下 **繼續**.
1. 繼續使用PayPal流程，以使用您的PayPal帳戶認證（而非沙箱帳戶認證），完成完全支援的進階上線 _或_ 註冊新的PayPal帳戶。

>[!IMPORTANT]
>
>**進階上線** 要求商家 [要求付款權益](#request-payments-entitlement-from-adobe) 以啟用即時上線。

### 標准入門

此標准入門流程適用於適用國家/地區的商家 [僅支援快速簽出](../payment-services/overview.md#availability) 已提供。

選取國家/地區後：

1. 在 _付款服務合約_ 強制回應視窗中，按一下 **付款服務合約** 檢視Adobe Commerce支付服務合約的連結。
1. 在 _付款服務合約_ 強制回應視窗，按一下 **我接受**.
1. 繼續使用您的PayPal帳戶認證（不是沙箱帳戶認證）或註冊新的PayPal帳戶，進行PayPal快速登入流程。

>[!IMPORTANT]
>
>[Apple Pay和信用卡欄位](../payment-services/payments-options.md) 不適用於 **標准入門**.

## 確認電子郵件地址

1. 在管理員側邊欄上，前往 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**

   此 _[!UICONTROL Live onboarding]_按鈕不再顯示，且您看到「[!UICONTROL Live payments pending]「文字方塊。

   在該文字方塊中，系統可能會要求您確認使用PayPal的電子郵件地址，以便完成上線。

1. 如果系統提示您確認您的電子郵件地址，請檢查您的電子郵件是否有從PayPal傳送的確認訊息，然後按一下以確認您的電子郵件地址。
1. 在管理員側邊欄上，前往 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 重新整理您的瀏覽器視窗。

   當您的PayPal商家上線獲得核準時，您應該會看到一則通知，指出您的付款系統處於沙箱模式，且未處理即時付款。

   >[!IMPORTANT]
   >
   >如果您撤銷對 [!DNL Payment Services] 的 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 為了處理您的付款（在您的PayPal帳戶設定中），您商店中的訂單無法由處理 [!DNL Payment Services]. 在您的「付款服務首頁」上，會出現有關撤銷同意的警報。

## 向Adobe要求付款權益

若要讓您的商店上線，請向Adobe要求付款權利(針對 [僅限進階上線](#advanced-onboarding))：

1. 在 _管理員_ 側欄，前往 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 按一下 **[!UICONTROL Get Live Payments]** 在您的 [!DNL Payment Services] 首頁。

   ![要求權益](assets/request-entitlements.png){width="500" zoomable="yes"}

1. 完成表單。
1. 銷售團隊的成員將會與您連絡。

或者，您可以向Adobe索取付款權利，網址為 [business.adobe.com](https://business.adobe.com/resources/payment-services.html).

>[!IMPORTANT]
>
>**即時上線** 在核准付款權益之前無法存取。

## 設定定價層

取得您的 [!DNL Payment Services] _商家ID_：

1. 在 _管理員_ 側欄，前往 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 在「首頁」檢視中，按一下 **[!UICONTROL Settings]**. 另請參閱 [首頁](payments-home.md) 以取得詳細資訊。
1. 選取所需的 _商家ID_ 然後提交給您的銷售代表，銷售代表會設定正確的定價層級。

## 啟用即時付款

A _生產商家識別碼_ 是自動產生，並填入 [設定](configure-admin.md). 請勿變更或變更此ID。

啟用即時付款：

1. 在 _管理員_ 側欄，前往 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 在首頁上，按一下 **[!UICONTROL Settings]** ，位於頁面右上方。 另請參閱 [首頁](payments-home.md) 以取得詳細資訊。
1. 在 _[!UICONTROL General Configuration]_區段集&#x200B;**[!UICONTROL Payment mode]**至 `Production`.
1. 按一下 **[!UICONTROL Save]**.
1. [清除您的快取](https://docs.magento.com/user-guide/system/cache-management.html){target="_blank"}.

   >[!IMPORTANT]
   >
   >如果您未清除快取，客戶在結帳時就無法看到PayPal付款選項。

如果您導覽回 [!DNL Payment Services] 首頁，沙箱付款模式訊息不再顯示，因為您現在正在處理即時付款。

另請參閱 [在管理員中設定](configure-admin.md) 舊版組態選項。

>[!IMPORTANT]
>
>如果您撤銷對 [!DNL Payment Services] 為了處理您的付款（在您的PayPal帳戶設定中），您商店中的訂單無法由處理 [!DNL Payment Services]. 如果您想要重新啟用付款處理功能，必須重新完成上線。 在您的「付款服務首頁」上，會出現有關撤銷同意的警報。

## 在生產環境中測試

強烈建議您先在生產環境中測試付款，並使用真正的信用卡和銀行，然後再向購物者公開此功能。

另請參閱 [測試及驗證](test-validate.md) 以取得詳細資訊。
