---
title: 訂單付款狀態報表
description: 使用「訂單付款狀態」報表可查看訂單的付款狀態，並識別任何潛在問題。
role: User
level: Intermediate
exl-id: 192e47b9-d52b-4dcf-a720-38459156fda4
source-git-commit: 39c0140961fa9de5075087bbc3fbec0e14560860
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 訂單付款狀態報表

[!DNL Payment Services] for [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 提供全面的報告，以便您能夠清楚地查看您商店的訂單和付款。

![財務報告視圖](assets/report-view.png)

訂單付款狀態報表可幫助您輕鬆了解特定訂單在現金處理流程訂單中的位置。 此報表可讓您快速檢視訂單的付款狀態，並識別任何潛在問題。

您不必開啟多個視圖才能人工交叉參考訂單和付款。 [!DNL Payment Services] for [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 使您能夠從訂單和付款的全局視圖中查看所有訂單和付款，這些都在訂單付款狀態報表中。

請參閱管理員中的此報表中的付款狀態、開票和發運狀態、退款狀態、爭議狀態等。

您可以下載.csv檔案格式的訂單付款狀態交易記錄，以用於現有的會計或訂單管理軟體。

>[!NOTE]
>
>如果您沒有 [已上線和已啟動的即時模式](production.md#enable-live-payments) for [!DNL Payment Services].

## 報表中使用的資料

此 [!DNL Payment Services] 模組使用訂單資料，並將其與來自其他來源（包括PayPal）的匯總付款資料結合，以提供有意義且高度有用的報表。

訂單資料會匯出並保存在付款服務中。 當您 [更改或添加訂單狀態](https://docs.magento.com/user-guide/sales/order-status-custom.html){target=&quot;_blank&quot;}或 [編輯商店檢視](https://docs.magento.com/user-guide/stores/stores-all-view-edit.html){target=&quot;_blank&quot;}, [商店](https://docs.magento.com/user-guide/stores/store-information.html){target=&quot;_blank&quot;}或網站名稱，該資料與付款資料結合，訂單付款狀態報表會填入結合的資訊。

此程式中有兩個步驟：

1. 索引已更改資料 `ON SAVE` （每次訂單資訊或商店資訊變更時）或 `BY SCHEDULE` （依預先設定的cron排程），視其在 [索引管理](https://docs.magento.com/user-guide/system/index-management.html)管理中的{target=&quot;_blank&quot;}。

   預設情況下，會進行資料索引 `ON SAVE`，這表示每當有項目變更順序、訂單狀態、存放區檢視、存放區或網站時，重新索引程式就會立即發生。

1. 索引資料會傳送至付款服務，然後填入訂單付款狀態報表。

為報告目的導出和整理的唯一資料是「訂單付款狀態」報表使用的資料。

>[!NOTE]
>
>此表格中顯示的資料會以遞減順序排序(`DESC`)，預設為使用 `ORDER DATE`. 此 `ORDER DATE` 是建立訂單的日期時間戳記。

### 設定資料匯出

即使依預設，重新索引會發生在 `ON SAVE` 模式，建議您在 `BY SCHEDULE` 模式。 此 `BY SCHEDULE` 索引在1分鐘的cron排程中執行，任何變更的資料會在資料變更後的2分鐘內顯示在「訂單狀態」報表中。 此計畫的重新索引有助於減少您的商店的任何壓力，尤其是如果您有大量傳入訂單，因為它是按計畫進行的（而不是在下單時）。

你可以更改索引模式 — `ON SAVE` 或 `BY SCHEDULE`—[在管理員中](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode){target=&quot;_blank&quot;}。

若要了解如何設定資料匯出，請參閱 [命令行配置](configure-cli.md#configure-data-export).

## 可用性

在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Order payment status]** ，查看訂單的付款狀態。

![管理員中的訂單付款狀態](assets/order-payment-status-report.png)

## 選擇資料源

在訂單付款狀態報表視圖中，您可以選擇資料源 — _[!UICONTROL Live]_或_[!UICONTROL Sandbox]_ — 您想查看其報告結果。

![資料來源選取](assets/datasource.png)

若 _[!UICONTROL Live]_是選取的資料來源，您就會看到使用的商店的報表資訊 [!DNL Payment Services] in_[!UICONTROL Live]_ 模式。 若 [!UICONTROL Sandbox]_是選取的資料來源，您可以看到沙箱環境的報表資訊。

資料源選擇的工作方式如下：

* 如果您沒有任何商店使用 [!DNL Payment Services] 在即時模式中，資料來源選取項目預設為 _[!UICONTROL Sandbox]_.
* 如果您有任何使用 [!DNL Payment Services] 在即時模式中，資料來源選取項目預設為 _[!UICONTROL Live]_.
* 報表匯出一律會遵循資料來源的選取。

為 [!UICONTROL Order Payment Status] 報告：

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. 按一下 **[!UICONTROL Data source]** 選取 _[!UICONTROL Live]_或_[!UICONTROL Sandbox]_.

   報表結果會根據選取的資料來源重新產生。

## 自訂日期時間範圍

從「訂單付款狀態」報表視圖，您可以通過選擇特定日期自定義要查看的狀態的時間範圍。 預設情況下，30天的訂單付款狀態將顯示在網格中。

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. 按一下 **[!UICONTROL Order dates]** 日曆選擇器篩選器。
1. 選擇適用的日期範圍。
1. 在網格中查看指定日期的訂單付款狀態。

## 顯示和隱藏列

預設情況下，「訂單付款狀態」報表將顯示所有可用的資訊列。 不過，您可以自訂在報表中看到的欄。

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. 按一下 _欄設定_ 圖示(![欄設定圖示](assets/column-settings.png))。
1. 若要自訂您在報表中看到的欄，請核取或取消勾選清單中的欄。

   訂單付款狀態報表將立即顯示您在「欄設定」功能表中所做的任何變更。 欄偏好設定會儲存，且如果您離開報表檢視，將保持有效。

## 檢視狀態

「訂單付款狀態」報表視圖顯示每個「付款服務」訂單的綜合事務處理狀態和付款狀態資訊。

### 交易狀態

預設情況下，30天的訂單付款狀態將顯示在網格中。

向左和向右滾動以查看 [訂單付款狀態資訊](#column-descriptions)，包括訂單日期、授權日期、開票、發運、支付狀態等。

在搜索中返回的行數，或在預設的30天訂單付款狀態中顯示的行數，將與「訂單日期日曆選擇器」篩選器一起顯示在「訂單付款狀態」視圖網格上方。

### 支付狀態

「支付狀態」列顯示任何付款的當前狀態。 A `Capture failed` 付款顯示紅色警報狀態和 `Voided` 付款顯示灰色警報狀態。

### 退款狀態

「退款狀態」列顯示任何退款的當前狀態。 A `Capture failed` 付款顯示紅色警報狀態和 `Voided` 付款顯示灰色警報狀態。

## 更新報表資料

訂單付款狀態報表視圖顯示 _[!UICONTROL Last updated]_顯示上次更新報表資訊的時間戳記。 預設情況下，每三小時自動刷新訂單付款狀態報表資料。

您也可以手動強制重新整理訂單付款狀態報表資料，以查看最新的報表資訊。

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. 按一下 _重新整理_ 圖示(![重新整理圖示](assets/refresh-button-med.png))。

   訂單付款狀態報表資料將刷新， *[!UICONTROL Update complete]* 確認隨即顯示，且網格中會顯示最新資訊。

## 查看爭議

您可以查看您商店訂單上的任何爭議，並從訂單付款狀態報表中定位至PayPal解決中心以對其採取操作。

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. 導覽至 **[!UICONTROL Disputes column]**.
1. 查看特定訂單的任何爭議，並查看 [爭議狀況](#order-payment-status-information).
1. 按一下爭議ID連結(從 _PP-D-_)前往 [PayPal解決中心](https://www.paypal.com/us/smarthelp/article/what-is-the-resolution-center-faq3327).
1. 視需要對爭端採取適當行動。

   要按狀態排序訂單爭議，請按一下「爭議」列標題。

## 下載訂單付款狀態

無論您是檢視預設的30天狀態或自訂時間範圍，您都可以下載.csv檔案，且所有狀態都會顯示在訂單付款狀態檢視格線中。

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. 如果您想查看過去30天以外的時間範圍狀態， [自訂狀態的日期範圍時間範圍](#customize-dates-timeframe).
1. 按一下 _下載_ (![下載圖示](assets/icon-download.png))圖示。

您的訂單付款狀態會以.csv格式下載。

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

訂單付款狀態視圖顯示網格中顯示的每個狀態的詳細資訊。

### 欄說明

訂單付款狀態報表包括以下資訊。

| 欄 | 說明 |
| ------------ | -------------------- |
| [!UICONTROL Order ID] | 商務訂單ID<br> <br>查看相關 [訂購資訊](https://docs.magento.com/user-guide/sales/orders.html){target=&quot;_blank&quot;}，按一下ID。 |
| [!UICONTROL Order Date] | 訂單日期時間戳記 |
| [!UICONTROL Authorized Date] | 付款授權的日期時間戳記 |
| [!UICONTROL Order Status] | 當前商務 [訂單狀態](https://docs.magento.com/user-guide/sales/order-status.html){target=&quot;_blank&quot;} |
| [!UICONTROL Invoiced] | 訂單的發票狀態 — *[!UICONTROL No]*, *[!UICONTROL Partial]*，或 *[!UICONTROL Yes]* |
| [!UICONTROL Shipped] | 訂單的發運狀態 — *[!UICONTROL No]*, *[!UICONTROL Partial]*，或 *[!UICONTROL Yes]* |
| [!UICONTROL Order Amt] | 訂單的總金額 |
| [!UICONTROL Cur] | 訂單的貨幣類型 |
| [!UICONTROL Pay Status] | 特定訂單的付款狀態 |
| [!UICONTROL Paid Amt] | 訂單支付的金額 |
| [!UICONTROL Cur] | 訂單支付金額的貨幣類型 |
| [!UICONTROL Refund Status] | 訂單的退款狀態（如退貨資訊、RMA和貸項通知單） —    *[!UICONTROL Requires refund]*, *[!UICONTROL Refund requested]*, *[!UICONTROL Refunded]*, *[!UICONTROL Refund failed]*，或 *[!UICONTROL Voided]* |
| [!UICONTROL Refund Amount] | 訂單的退款總額 |
| [!UICONTROL Cur] | 訂單退款金額的幣種類型 |
| [!UICONTROL Disputes] | 訂單上任何爭議的狀況（來自爭議和拖欠的資訊） — *[!UICONTROL Open]*, *[!UICONTROL Waiting for buyer response]*, *[!UICONTROL Waiting for seller response]*, *[!UICONTROL Under review]*, *[!UICONTROL Resolved]*，或 *[!UICONTROL Other]* |
| [!UICONTROL Payment Method] | 用於訂單的商務交易記錄的付款方法 |
| [!UICONTROL Website] | 下訂單的網站 |
| [!UICONTROL Store] | 下訂單的儲存 |
| [!UICONTROL Store View] | 從中下單的儲存視圖 |
