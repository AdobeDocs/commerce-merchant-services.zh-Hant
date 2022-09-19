---
title: 啟用 [!DNL Payment Services] 生產
description: 透過啟用 [!DNL Payment Services] 生產。
exl-id: 3b1269e8-127b-47f8-9738-9722a5737c63
source-git-commit: 7b31fe7a71c3c238e6448627b2edfe06bbfbc80e
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 0%

---

# 啟用 [!DNL Payment Services] 生產

您可以將服務投入生產，並完成 [上線程式](onboard.md)，依照本主題中的步驟，在您執行下列動作後：

* [安裝](install.md) 支付服務擴展
* [配置和連接](connect.md) 您的例項
* [設定](sandbox.md) 和 [測試](test-validate.md) 您的沙箱

## 設定 [!DNL Payment Services] 付款方式

在 [配置商務服務](connect.md#configure-commerce-services) 啟用 [沙箱測試](sandbox.md#enable-sandbox-testing) 或 [即時支付](#enable-live-payments)，您必須 [!DNL Payment Services] 作為您的付款方式。

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 按一下 **[!UICONTROL Enable Payment Services]**.

   如果您尚未設定，則會顯示此選項 [!DNL Payment Services] 作為一個或多個網站的付款方法。

   系統會將您導向至「首頁」檢視中的設定區域，並展開相關選項(**[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Settings]_)，您可在此啟用 [!DNL Payment Services] 選項 [付款方法](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html){target=&quot;_blank&quot;}。

1. 在 _[!UICONTROL General Configuration]_，設定&#x200B;**[!UICONTROL Enable]**to `Yes`.
1. 設定 **[!UICONTROL Payment Action]**，兩者皆適用 _[!UICONTROL Credit Card Fields]_和_[!UICONTROL PayPal Smart Buttons]_，變更為下列其中一項：

   | 設定 | 說明 |
   |---|---|
   | `Authorize` | 批准購買並保留資金。 在商戶&quot;捕獲&quot;該金額之前，該金額不會撤回。 |
   | `Authorize and Capture` | 核准購買，而商戶「擷取」資金。 |

1. 按一下 **[!UICONTROL Save]**.
1. 按一下 **[!UICONTROL Go to Payment Services]** 被送回 [!DNL Payment Services] 家。
1. [清除快取](https://docs.magento.com/user-guide/system/cache-management.html){target=&quot;_blank&quot;}。

   每次設定變更後，都應執行清除作業。

請參閱 [配置支付服務](settings.md) 有關配置信用卡欄位和PayPal智慧按鈕的詳細資訊。

## 完整的商家入門

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 按一下 **[!UICONTROL Live onboarding]**.

   如果您尚未完成的即時上線，則會顯示此選項 [!DNL Payment Services].

   您將看到PayPal窗口。

1. 繼續使用PayPal流程，使用您的PayPal帳戶憑證（而非您的沙箱帳戶憑證），或註冊新的PayPal帳戶。
1. 在管理員側欄上，前往 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**

   此 _[!UICONTROL Live onboarding]_按鈕不再顯示，您會看到「[!UICONTROL Live payments pending]」。

   在該文本框中，可能還會要求您使用PayPal確認您的電子郵件地址以完成上線。

1. 如果系統提示您確認電子郵件地址，請檢查您的電子郵件，以取得PayPal寄出的確認訊息，然後按一下以確認您的電子郵件地址。
1. 在管理員側欄上，前往 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 重新整理您的瀏覽器視窗。

   核准您的PayPal商家上線後，您應會看到通知，指出您的付款系統處於沙箱模式，且不處理即時付款。

   >[!IMPORTANT]
   >
   >如果您撤銷 [!DNL Payment Services] for [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 對於處理您的付款（在您的PayPal帳戶設定中），您商店中的訂單無法由 [!DNL Payment Services]. 在您的支付服務首頁上，會顯示有關已撤銷同意的警報。

## 從Adobe請求付款權利

要啟用即時上線，您必須向Adobe請求付款權利：

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 按一下 **[!UICONTROL Get Live Payments]** 在 [!DNL Payment Services] 家。

   ![要求權益](assets/request-entitlements.png)

1. 填寫表單。
1. 銷售團隊的一名成員將與您聯繫。

或者，您也可以在以下網址向Adobe申請付款權利： [business.adobe.com](https://business.adobe.com/resources/payment-services.html).

>[!IMPORTANT]
>
>**即時入門** 在核准付款權利之前無法存取。

## 配置定價層

要獲取 [!DNL Payment Services] _商家ID_:


1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 在「首頁」檢視中，按一下 **[!UICONTROL Settings]**. 請參閱 [首頁](payments-home.md) 以取得更多資訊。
1. 選取所需 _商家ID_ 並將其提交給您的銷售代表，銷售代表將配置正確的定價層。

## 啟用即時支付

A _生產商ID_ 會自動產生，並填入 [配置](configure-admin.md). 請勿變更或更改此ID。

要啟用即時付款，請執行以下操作：

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 在首頁上，按一下 **[!UICONTROL Settings]** 頁面的右上角。 請參閱 [首頁](payments-home.md) 以取得更多資訊。
1. 在 _[!UICONTROL General Configuration]_區段集&#x200B;**[!UICONTROL Payment mode]**to `Production`.
1. 按一下 **[!UICONTROL Save]**.
1. [清除快取](https://docs.magento.com/user-guide/system/cache-management.html){target=&quot;_blank&quot;}。

   >[!IMPORTANT]
   >
   >如果您未清除快取，客戶在結帳期間將看不到PayPal付款選項。

如果您導覽回 [!DNL Payment Services] 首頁，沙箱付款模式訊息不會再出現，因為您現在正在處理即時付款。

請參閱 [在管理員中進行設定](configure-admin.md) 舊版設定選項。

>[!IMPORTANT]
>
>如果您撤銷 [!DNL Payment Services] 對於處理您的付款（在您的PayPal帳戶設定中），您商店中的訂單無法由 [!DNL Payment Services]. 如果要重新啟用付款處理，必須重新完成上線。 在您的支付服務首頁上，會顯示有關已撤銷同意的警報。

## 在生產環境中測試

強烈建議您先在生產中測試Payments（使用真實信用卡和銀行），然後再向購物者顯示此功能。

請參閱 [測試和驗證](test-validate.md) 以取得更多資訊。
