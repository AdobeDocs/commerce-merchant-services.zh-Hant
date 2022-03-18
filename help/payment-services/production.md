---
title: 啟用 [!DNL Payment Services] 生產
description: 通過啟用 [!DNL Payment Services] 生產。
exl-id: 3b1269e8-127b-47f8-9738-9722a5737c63
source-git-commit: fd818dadbaa2a58efd7313ce888c7dda27d25f14
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 0%

---

# 啟用 [!DNL Payment Services] 生產

在Oracle Payments Services擴展後 [已安裝](install.md)，您的實例 [已配置和連接](connect.md)，你 [設定沙盒](sandbox.md) 經過測試後，您可以繼續將服務投入生產並完成 [聯機](onboard.md)。

## 設定 [!DNL Payment Services] 作為付款方式

在你之後 [配置Commerce Services](connect.md#configure-commerce-services) 啟用 [沙盒測試](sandbox.md#enable-sandbox-testing) 或 [活支付](#enable-live-payments)，必須設定 [!DNL Payment Services] 作為付款方式。

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**。
1. 按一下 **[!UICONTROL Enable Payment Services]**.

   如果尚未配置，則此選項可見 [!DNL Payment Services] 作為一個或多個Magento網站的付款方式。

   您將被引導到管理中的配置區域，並展開相關選項(**[!UICONTROL Sales]** > **[!UICONTROL Payment Methods]** > _[!UICONTROL Recommended Solutions]_>_[!UICONTROL Payment Services]_)，在其中可以啟用 [!DNL Payment Services] 選項 [付款方式](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html){target=&quot;_blank&quot;}。

1. 在 _[!UICONTROL General Configuration]_。**[!UICONTROL Enable]**至 `Yes`。
1. 設定 **[!UICONTROL Payment Action]**，同時 _[!UICONTROL Credit Card Fields]_和_[!UICONTROL PayPal Smart Buttons]_，至以下項之一：

   | 設定 | 說明 |
   |---|---|
   | `Authorize` | 批准採購並暫停資金。 在被商戶「捕獲」之前，不提取該金額。 |
   | `Authorize and Capture` | 批准購買，商家「捕獲」資金。 |

1. 按一下 **[!UICONTROL Save Config]**.
1. 按一下 **[!UICONTROL Go to Payment Services]** 被引導回 [!DNL Payment Services] 家。
1. [清除快取](https://docs.magento.com/user-guide/system/cache-management.html){target=&quot;_blank&quot;}。

   應在每次配置更改後進行清除。

請參閱 [配置付款服務](configure-admin.md) 的子菜單。

## 完整的商戶登機

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**。
1. 按一下 **[!UICONTROL Live onboarding]**.

   如果尚未完成的即時登錄，則此選項可見 [!DNL Payment Services]。

   您會看到一個PayPal窗口。

1. 繼續使用PayPal流，使用PayPal帳戶憑據（而不是沙盒帳戶憑據）或註冊新的PayPal帳戶。
1. 在管理員側欄上，轉到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**

   的 _[!UICONTROL Live onboarding]_按鈕不再可見，您會看到「[!UICONTROL Live payments pending]的子菜單。

   在該文本框中，可能還會要求您確認您與PayPal的電子郵件地址以完成登錄。

1. 如果系統提示您確認您的電子郵件地址，請檢查您的電子郵件以獲取從PayPal發送的確認消息，然後按一下以確認您的電子郵件地址。
1. 在管理員側欄上，轉到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**。
1. 刷新瀏覽器窗口。

   當您的PayPal商戶登機獲得批准時，您應看到一則通知，指出您的付款系統處於沙箱模式且未處理即時付款。

   >[!IMPORTANT]
   >
   >如果撤消對 [!DNL Payment Services] 對於Adobe Commerce和Magento Open Source來處理您的付款（在PayPal帳戶設定中），您的商店中的訂單無法由 [!DNL Payment Services]。

## 從Adobe請求付款權利

要啟用即時登機，必須從 [Adobe](https://business.adobe.com/resources/payment-services.html)。

>[!IMPORTANT]
>
>**現場登機** 在批准付款權限之前無法訪問。

## 配置定價層

為了 [!DNL Payment Services] _商戶ID_:

1. 在 _管理_ 邊欄，導航 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**。
1. 在左面板中，展開 **[!UICONTROL Sales]** 選擇 **[!UICONTROL Payment Methods]**。
1. 展開 _[!UICONTROL Recommended Solutions]_的子菜單。
1. 在 _[!UICONTROL Payment Services]_的_[!UICONTROL General Configuration]_ 的子菜單。
1. 選擇所需 _商戶ID_ 並將其提交給銷售代表，銷售代表將配置正確的定價層。

## 啟用即時付款

A _生產商ID_ 在 [配置](configure-admin.md)。 不要更改或更改此ID。

要啟用即時付款，請執行以下操作：

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**。
1. 在左面板中，展開 **[!UICONTROL Sales]** 選擇 **[!UICONTROL Payment Methods]**。
1. 展開 _[!UICONTROL Recommended Solutions]_的子菜單。
1. 在 _[!UICONTROL Payment Services]_的_[!UICONTROL General Configuration]_ 的子菜單。
1. 設定 **[!UICONTROL Method]** 至 `Production`。
1. 按一下 **[!UICONTROL Save Config]**.
1. [清除快取](https://docs.magento.com/user-guide/system/cache-management.html){target=&quot;_blank&quot;}。

   >[!IMPORTANT]
   >
   >如果您未清除快取，則客戶在結帳期間無法看到PayPal付款選項。

如果導航回 [!DNL Payment Services] 「首頁」，「沙盒付款模式」消息將不再顯示，因為您正在處理即時付款。

請參閱 [在管理員中配置](configure-admin.md) 的子菜單。

>[!IMPORTANT]
>
>如果撤消對 [!DNL Payment Services] 處理付款時（在PayPal帳戶設定中），您的商店中的訂單無法由 [!DNL Payment Services]。 如果要重新啟用付款處理，必須再次完成登記。

## Test

強烈建議您在將此功能向購物者公開之前，先將付款test到生產中，再使用真實信用卡和銀行。

請參閱 [Test和驗證](test-validate.md) 的子菜單。
