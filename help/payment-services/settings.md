---
title: 付款服務設定
description: 安裝後，您可以配置 [!DNL Payment Services] 的下一頁。
role: Admin, User
level: Intermediate
source-git-commit: 9596815e31402f23b399b223f3221074331c1773
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---

# 在「首頁」視圖中配置

您可以自定義 [!DNL Payment Services] 在「首頁」視圖中設定。

配置 [!DNL Payment Services] 為 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 按一下 **[!UICONTROL Settings]**。 這些配置選項僅適用於在 _[!UICONTROL Payment mode]_的子菜單。

查看 [[!UICONTROL General] 設定部分](#general-settings) 的子菜單。

>[!IMPORTANT]
>
> 有關多儲存或舊式配置，請參閱 [在管理員中配置](configure-admin.md) 主題。

## 配置付款服務

您可以啟用 [!DNL Payment Services] 為您的網站啟用沙盒測試或即時付款 [!UICONTROL General] 的子菜單。

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**。

   ![首頁視圖](assets/payment-services-menu-small.png)

1. 在「首頁」視圖中，按一下 **[!UICONTROL Settings]**。 請參閱 [首頁](payments-home.md) 的子菜單。

   的 _[!UICONTROL General]_部分包括用於設定 [!DNL Payment Services] 付款方式。

1. 對於頂部的切換選項(**[!UICONTROL Enable Payment Services as payment method]**) `Yes` 啟用 [!DNL Payment Services] 的子菜單。

1. 對於 **付款模式**，將其設定為 `Sandbox` 如果你還在測試 [!DNL Payment Services] 你的商店 `Production` 如果您已準備好啟用即時付款。

   >[!WARNING]
   >
   >您 _[!UICONTROL Sandbox Merchant ID]_和_[!UICONTROL Production Merchant ID]_ 在您完成沙箱和/或生產後，自動生成並呈現在他們受人尊重的領域。 不要刪除或更改這些ID。

1. 要更改付款功能和店面顯示的預設設定，請根據需要設定附加選項：

   - [信用卡欄位](#credit-card-fields)
   - [PayPal智慧按鈕](#paypal-smart-buttons)
   - [按鈕樣式](#button-style)

1. 要保存更改，請按一下 **[!UICONTROL Save]** 頁面右上角。

   如果嘗試在不保存更改的情況下從此視圖中導航，則會出現一個模式，提示您放棄更改、繼續編輯或保存更改。

1. 導航到 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 按一下 **[!UICONTROL Flush Cache]** 刷新所有無效的快取。

### 信用卡欄位

的 _[!UICONTROL Credit Card Fields]_付款選項為信用卡或借記卡付款方法提供簡單而安全的結帳。

請參閱 [付款選項](payments-options.md#paypal-smart-buttons) 的子菜單。

1. 對於 **[!UICONTROL Checkout title]**，輸入文本（如果需要）以更改在結帳期間顯示的付款方法的名稱。
1. 至 [設定付款活動](production.md#set-payment-services-as-payment-method)。 **[!UICONTROL Payment action]** 至 `Authorize` 或 `Authorize and Capture`。
1. 對於 **[!UICONTROL Debug Mode]**，切換選擇器以啟用調試模式。
1. 要保存更改，請按一下 **[!UICONTROL Save]** 頁面右上角。

   如果嘗試在不保存更改的情況下從此視圖中導航，則會出現一個模式，提示您放棄更改、繼續編輯或保存更改。

1. 導航到 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 按一下 **[!UICONTROL Flush Cache]** 刷新所有無效的快取。

### PayPal智慧按鈕

的 [!DNL PayPal Smart Buttons] 付款選項可為客戶提供簡單、快速和安全的結帳流程。 請參閱 [付款選項](payments-options.md#paypal-smart-buttons) 的子菜單。

您可以在「首頁：

1. 要更改在結帳期間顯示的付款方法的名稱，請在 **[!UICONTROL Checkout Title]** 的子菜單。
1. 至 [設定付款活動](production.md#set-payment-services-as-payment-method)。 **[!UICONTROL Payment action]** 至 `Authorize` 或 `Authorize and Capture`。
1. 使用切換選擇器啟用或禁用 [!DNL PayPal smart button] 顯示功能：
   - **[!UICONTROL Show buttons on product detail page]**
   - **[!UICONTROL Show buttons in mini cart preview]**
   - **[!UICONTROL Show buttons on cart page]**
   - **[!UICONTROL Show Venmo button]**。
   - **[!UICONTROL PayPal Pay Later enabled]** 啟用選項以在簽出期間顯示按鈕。

1. 更改 [稍後付費消息](payments-options.md#pay-later-button) （如果需要），切換 **[!UICONTROL Display Pay Later message]** 的雙曲餘切值。
1. 要啟用調試模式，請按一下 **[!UICONTROL Debug Mode]**。
1. 要保存更改，請按一下 **[!UICONTROL Save]** 頁面右上角。

   如果嘗試在不保存更改的情況下從此視圖中導航，則會出現一個模式，提示您放棄更改、繼續編輯或保存更改。

1. 導航到 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 按一下 **[!UICONTROL Flush Cache]** 刷新所有無效的快取。

### 按鈕樣式

您還可以配置 _[!UICONTROL Button style]_家庭中PayPal智慧按鈕的選項：

1. 更改 **[!UICONTROL Layout]**&#x200B;選中 `Vertical` 或 `Horizontal`。
1. 要在水準佈局中啟用標籤線，請按一下 **[!UICONTROL Show tagline]**。
1. 修改 **[!UICONTROL Color]**，則選擇所需的顏色選項。
1. 更改 **[!UICONTROL Shape]**&#x200B;選中 `Pill` 或 `Rect`。
1. 要啟用按鈕高度選擇器，請按一下 **[!UICONTROL Responsive button height]**。
1. 修改 **[!UICONTROL Label]**，選擇所需的標籤選項。
1. 要保存更改，請按一下 **[!UICONTROL Save]** 頁面右上角。

   如果嘗試在不保存更改的情況下從此視圖中導航，則會出現一個模式，提示您放棄更改、繼續編輯或保存更改。

1. 導航到 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 按一下 **[!UICONTROL Flush Cache]** 刷新所有無效的快取。

您可以配置 [!DNL PayPal Smart Buttons] 樣式。 請參閱 [PayPal的按鈕樣式指南](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) 的子菜單。
