---
title: 訂單付款狀態報表
description: 使用「訂單付款狀態」報表可查看訂單的付款狀態並確定任何潛在問題。
role: User
level: Intermediate
exl-id: 192e47b9-d52b-4dcf-a720-38459156fda4
source-git-commit: 59cceb1cab1ed2bcfaa7d59c54a40255a38dea29
workflow-type: tm+mt
source-wordcount: '1436'
ht-degree: 0%

---

# 訂單付款狀態報表

[!DNL Payment Services] 為 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 提供全面的報告，以便您能夠清楚地查看您商店的訂單和付款。

![財務報告視圖](assets/reports-view.png)

「訂單付款狀態」報表可幫助您輕鬆瞭解特定訂單在訂單至現金處理流程中的位置。 此報表允許您快速查看訂單的付款狀態並確定任何潛在問題。

您不必開啟多個視圖來人工交叉參考訂單和付款。 [!DNL Payment Services] 為 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 使您可以查看訂單和付款的概覽 — 所有這些都在訂單付款狀態報表中。

請參閱「管理員」中此報表中的付款狀態、開票和發運狀態、退款狀態、爭議狀態等。

您可以以.csv檔案格式下載訂單付款狀態交易記錄，以用於現有會計或訂單管理軟體。

>[!NOTE]
>
>如果您沒有 [已掛接和激活的即時模式](production.md#enable-live-payments) 為 [!DNL Payment Services]。

## 報表中使用的資料

的 [!DNL Payment Services] 模組使用訂單資料，並將其與來自其他來源（包括PayPal）的匯總付款資料組合，以提供有意義且非常有用的報告。

訂單資料被導出並保留在付款服務中。 當你 [更改或添加訂單狀態](https://docs.magento.com/user-guide/sales/order-status-custom.html){target=&quot;_blank&quot;或 [編輯商店視圖](https://docs.magento.com/user-guide/stores/stores-all-view-edit.html){target=&quot;_blank&quot;, [商店](https://docs.magento.com/user-guide/stores/store-information.html){target=&quot;_blank&quot;}或網站名稱，該資料與付款資料組合，並且訂單付款狀態報表已填充組合資訊。

此過程中有兩個步驟：

1. 索引已更改資料 `ON SAVE` （每次訂單資訊或儲存資訊更改時）或 `BY SCHEDULE` （根據預配置的cron計畫），具體取決於 [索引管理](https://docs.magento.com/user-guide/system/index-management.html)管理中的{target=&quot;_blank&quot;}。

   預設情況下，資料索引發生 `ON SAVE`，這意味著只要訂單、訂單狀態、儲存視圖、儲存或網站中的某些內容發生更改，重新索引過程就會立即發生。

1. 索引資料將發送到付款服務，然後將其填入訂單付款狀態報表。

為報告目的導出和整理的唯一資料是訂單付款狀態報表使用的資料。

>[!NOTE]
>
>此表中顯示的資料按降序排序(`DESC`) `ORDER DATE`。 的 `ORDER DATE` 是建立訂單的日期時間戳。

### 配置資料導出

儘管在預設情況下，重新編製索引發生在 `ON SAVE` 模式，建議您在 `BY SCHEDULE` 的子菜單。 的 `BY SCHEDULE` 索引在cron計畫下運行1分鐘，任何更改的資料在任何資料更改後的兩分鐘內出現在「訂單狀態」報告中。 此計畫的重新索引有助於您減少商店的任何壓力，尤其是如果您有大量傳入訂單，因為它是按計畫進行的（而不是按每個訂單進行）。

可以更改索引模式……`ON SAVE` 或 `BY SCHEDULE`—[管理員](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode){target=&quot;_blank&quot;}。

要瞭解如何配置資料導出，請參見 [命令行配置](configure-cli.md#configure-data-export)。

## 可用性

在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Order payment status]** 查看訂單的付款狀態。

![管理員中的訂單付款狀態](assets/order-payment-status-report.png)

## 選擇資料源

在「訂單付款狀態」報表視圖中，您可以選擇資料源 — _[!UICONTROL Live]_或_[!UICONTROL Sandbox]_ — 要查看其報告結果。

![資料源選擇](assets/datasource.png)

如果 _[!UICONTROL Live]_是選定的資料源，您可以查看使用的儲存的報告資訊 [!DNL Payment Services] 在_[!UICONTROL Live]_ 的子菜單。 如果 [!UICONTROL Sandbox]_是選定的資料源，您可以查看沙盒環境的報告資訊。

資料源選擇的工作方式如下：

* 如果你沒有商店 [!DNL Payment Services] 在即時模式下，資料源選擇預設為 _[!UICONTROL Sandbox]_。
* 如果您有使用 [!DNL Payment Services] 在即時模式下，資料源選擇預設為 _[!UICONTROL Live]_。
* 報告導出始終遵循資料源選擇。

為您的 [!UICONTROL Order Payment Status] 報告：

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**。
1. 按一下 **[!UICONTROL Data source]** 選擇 _[!UICONTROL Live]_或_[!UICONTROL Sandbox]_。

   根據所選資料源重新生成報告結果。

## 自定義日期時間範圍

從「訂單付款狀態」報表視圖中，您可以通過選擇特定日期來自定義要查看的狀態的時間範圍。 預設情況下，在網格中顯示30天的訂單付款狀態。

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**。
1. 按一下 **[!UICONTROL Order dates]** 日曆選擇器篩選器。
1. 選擇適用的日期範圍。
1. 在網格中查看指定日期的訂單付款狀態。

## 顯示和隱藏列

預設情況下，「訂單付款狀態」報表顯示所有可用的資訊列。 但是，您可以自定義在報告中看到的列。

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**。
1. 按一下 _列設定_ 表徵圖。![列設定表徵圖](assets/column-settings.png))。
1. 要自定義您在報表中看到的列，請選中或取消選中清單中的列。

   訂單付款狀態報表將立即顯示您在「列設定」菜單中所做的任何更改。 列首選項將被保存，並且如果您從報表視圖中導航，將保持有效。

## 查看狀態

「訂單付款狀態」報表視圖顯示每個付款服務訂單的全面事務處理狀態和付款狀態資訊。

### 交易記錄狀態

預設情況下，在網格中顯示30天的訂單付款狀態。

向左和向右滾動以查看 [訂單付款狀態資訊](#column-descriptions)，包括訂單日期、授權日期、開票、發運、支付狀態等。

在搜索中返回或在預設的30天訂單付款狀態中顯示的行數顯示在「訂單付款狀態」視圖網格的上方以及「訂單日期日曆」選擇器篩選器。

### 付薪狀態

「支付狀態」列顯示任何付款的當前狀態。 A `Capture failed` 付款顯示紅色警報狀態和 `Voided` 付款顯示灰色警報狀態。

### 退款狀態

「退款狀態」列顯示任何退款的當前狀態。 A `Capture failed` 付款顯示紅色警報狀態和 `Voided` 付款顯示灰色警報狀態。

## 更新報表資料

訂單付款狀態報表視圖顯示 _[!UICONTROL Last updated]_顯示上次更新報告資訊的時間的時間戳。 預設情況下，訂單付款狀態報表資料每三小時自動刷新一次。

您還可以人工強制刷新訂單付款狀態報表資料，以查看最新報表資訊。

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**。
1. 按一下 _刷新_ 表徵圖。![刷新表徵圖](assets/refresh-button-med.png))。

   將刷新訂單付款狀態報表資料， *[!UICONTROL Update complete]* 將顯示確認，並且網格中會顯示最新資訊。

## 查看爭議

您可以查看有關商店訂單的任何爭議，並從「訂單付款狀態」報表定位至「PayPal解決中心」以對其採取措施。

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**。
1. 導航到 **[!UICONTROL Disputes column]**。
1. 查看特定訂單的任何爭議，並查看 [爭端狀況](#order-payment-status-information)。
1. 按一下爭議ID連結(以 _PP-D-_)轉到 [PayPal解決中心](https://www.paypal.com/us/smarthelp/article/what-is-the-resolution-center-faq3327)。
1. 根據需要對爭端採取適當行動。

   要按狀態對爭議排序，請按一下「爭議」列標題。

## 下載訂單付款狀態

無論您是查看預設的30天狀態還是自定義的時間範圍，都可以下載所有狀態都可見的.csv檔案。

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**。
1. 如果要查看過去30天以外的時間段的狀態， [自定義狀態的日期範圍時間範圍](#customize-dates-timeframe)。
1. 按一下 _下載_ (![下載表徵圖](assets/icon-download.png))。

您的訂單付款狀態以.csv格式下載。

<!-- ## Default order payment status timeframes

These order payment status timeframes are currently available in [!DNL Payment Services].

| Report       | Description          |
| ------------ | -------------------- |
| Yesterday | Available from the Order payment status dates selector, this shows information for the prior date. |
| | Today | Available from the Order payment status dates selector, this shows information for the current day. |
| Last 7 days | Available from the Order payment status dates selector, this shows information for the last seven days. |
| Last 30 days | Available from the Order payment status dates selector and by default in the Order payment statuses view, this shows information for the last 30 days. |
| Last 90 days | Available from the Order payment status dates selector, this shows information for the last 90 days. |
| Year to date | Available from the Order payment status dates selector, this shows information for the the entire year to date. |
| Custom range | Available from the Order payment status dates selector, this can be filtered to show a custom date range. |
-->

## 訂單付款狀態資訊

「訂單付款狀態」視圖顯示網格中顯示的每個狀態的詳細資訊。

### 列說明

訂單付款狀態報表包括以下資訊。

| 列 | 說明 |
| ------------ | -------------------- |
| [!UICONTROL Order ID] | 商業訂單ID<br> <br>查看相關 [訂單資訊](https://docs.magento.com/user-guide/sales/orders.html){target=&quot;_blank&quot;}，按一下ID。 |
| [!UICONTROL Order Date] | 訂單日期時間戳 |
| [!UICONTROL Authorized Date] | 付款授權的日期時間戳 |
| [!UICONTROL Order Status] | 當前商業 [訂單狀態](https://docs.magento.com/user-guide/sales/order-status.html){target=&quot;_blank&quot; |
| [!UICONTROL Invoiced] | 訂單的發票狀態 — *[!UICONTROL No]*。 *[!UICONTROL Partial]*&#x200B;或 *[!UICONTROL Yes]* |
| [!UICONTROL Shipped] | 訂單的發運狀態 — *[!UICONTROL No]*。 *[!UICONTROL Partial]*&#x200B;或 *[!UICONTROL Yes]* |
| [!UICONTROL Order Amt] | 訂單總金額 |
| [!UICONTROL Cur] | 訂單的幣種類型 |
| [!UICONTROL Pay Status] | 特定訂單的付款狀態 |
| [!UICONTROL Paid Amt] | 訂單上支付的金額 |
| [!UICONTROL Cur] | 訂單上支付金額的幣種類型 |
| [!UICONTROL Refund Status] | 訂單上的退款狀態（如退貨、RMA和貸項通知單中的資訊） —    *[!UICONTROL Requires refund]*。 *[!UICONTROL Refund requested]*。 *[!UICONTROL Refunded]*。 *[!UICONTROL Refund failed]*&#x200B;或 *[!UICONTROL Voided]* |
| [!UICONTROL Refund Amount] | 訂單的退款總額 |
| [!UICONTROL Cur] | 訂單退還金額的幣種類型 |
| [!UICONTROL Disputes] | 對訂單的任何爭議的狀態（來自爭議和拖欠的資訊） — *[!UICONTROL Open]*。 *[!UICONTROL Waiting for buyer response]*。 *[!UICONTROL Waiting for seller response]*。 *[!UICONTROL Under review]*。 *[!UICONTROL Resolved]*&#x200B;或 *[!UICONTROL Other]* |
| [!UICONTROL Payment Method] | 訂單的Commerce交易記錄中使用的付款方法 |
| [!UICONTROL Website] | 從中下達訂單的網站 |
| [!UICONTROL Store] | 從中下訂單的商店 |
| [!UICONTROL Store View] | 從中下訂單的儲存視圖 |
