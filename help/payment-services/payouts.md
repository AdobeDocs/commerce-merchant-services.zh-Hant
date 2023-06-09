---
title: 支付報表
description: 使用「付款」報表，可完全透明地顯示付款金額、已處理數量及財務調節之交易層次的詳細報表。
role: User
level: Intermediate
exl-id: f3f99474-cd28-4c8f-b0ea-dca8e014b108
source-git-commit: 8295b7c4ea407f0528d6be69655a8b12f7defe15
workflow-type: tm+mt
source-wordcount: '1326'
ht-degree: 0%

---

# 支付報表

[!DNL Payment Services] 的 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 提供您完整的報告，讓您清楚瞭解商店的訂購與付款。

有兩個可用的「付款」報告檢視表，可讓您檢視所有付款的深入資訊：

* **[支付資料視覺效果檢視](#payouts-data-visualization-view)** — 可在「付款服務首頁」上使用的圖表，以視覺化方式呈現付款報表檢視中的每日彙總金額
* **[支付報表檢視](#payouts-report-view)** — 可顯示在「付款」中的報表，其中顯示所有交易的詳細付款資訊

「付款」檢視表一目瞭然地顯示完整的付款資訊，可讓您完全透明地顯示付款金額、處理數量及財務調節之交易層次的詳細報表。

>[!NOTE]
>
>付款報表只會顯示已抓取的訂單(付款作業設為 [`Authorize and Capture`](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/production.html#set-payment-services-as-payment-method)) — 或 [標示為 `Invoiced`](https://docs.magento.com/user-guide/sales/invoice-create.html).

## 支付資料視覺效果檢視

付款服務首頁提供「付款」資料視覺效果檢視。 這是詳細表格中每日彙總金額的視覺化表示法 [支付報表檢視](#payouts-report-view).

於 _管理員_ 側欄，前往 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** 檢視信用與借項的資料視覺化圖表，以及一段時間內的移動平均。

![管理員中的支付資料視覺效果](assets/payouts-report.png){zoomable=yes}

按一下 **[!UICONTROL View Report]** 導覽至詳細的表格 [支付報表檢視](#payouts-report-view).

### 自訂交易時間範圍

依預設，會顯示30天的交易。

從「付款資料」視覺效果檢視中，您可以選取日期範圍，以自訂您要檢視之付款交易的時間範圍：

1. 於 _管理員_ 側欄，前往 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**. 「付款」資料視覺效果檢視會顯示在「付款」區段中。
1. 按一下 **[!UICONTROL Range]** 選擇器篩選器。
1. 選擇適用的日期範圍 — 30天、15天或7天。
1. 檢視指定日期的交易資訊。

### 交易資訊

所選日期範圍的交易金額會顯示在「付款」資料視覺效果檢視的左側。 所選日期範圍的日期會顯示在檢視底部。 如果特定日期沒有付款，該日期將不會顯示。

「付款」資料視覺效果檢視包含下列資訊。

| 資料 | 說明 |
| ------------ | -------------------- |
| [!UICONTROL Transaction amount] | 指定時間範圍內交易的金額範圍；Y軸上的資料（左） |
| 日期範圍 | 指定時間範圍的日期範圍；X軸（底部）的資料 |
| 信用 | 指定時間範圍的付款 |
| 借方 | 指定時間範圍內的借方（退款） |
| 移動平均 | 表示指定時間範圍內每個日期的平均派息 |
| 範圍的淨值 | 指定時間範圍（範圍）的淨支付金額 |

## 支付報表檢視

「付款服務」的「付款」檢視表中會提供「付款」報表檢視表。 它包含有關您商店付款的所有可用資訊。 此 [支付資料視覺效果檢視](#payouts-data-visualization-view) 在「付款服務首頁」中，可在此更詳細的報表檢視中，以視覺化方式呈現每日彙總金額。

於 _管理員_ 側欄，前往 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]** 若要檢視詳細的表格化付款報表檢視，請執行下列步驟：

![管理員中的支付交易](assets/payouts-report-new.png){zoomable=yes}

您可以依據本主題中的章節，設定此檢視，以最佳方式呈現您想要檢視的資料。

請參閱連結的商務訂單與交易ID、交易金額、每筆交易的付款方式等，這些全都在「管理員」的「付款」報表中。

您可以 [下載支付交易](#download-transactions) .csv檔案格式，用於現有的會計或訂單管理軟體。

>[!NOTE]
>
>此表格中顯示的資料會依遞減順序排序(`DESC`)預設情況下，使用 `TRANS DATE`. 此 `TRANS DATE` 是啟動交易的日期和時間。

### 選取資料來源

在「付款」報表檢視中，您可以選取資料來源 — _[!UICONTROL Live]_或_[!UICONTROL Sandbox]_ — 您想要檢視其報告結果。

![資料來源選擇](assets/datasource.png){width=400px}

若 _[!UICONTROL Live]_是選取的資料來源，您可以檢視生產模式中存放區的報表資訊。 若_[!UICONTROL Sandbox]_ 是選取的資料來源，您會看到報表資訊以沙箱模式儲存。

資料來源選取專案的工作方式如下：

* 如果您沒有任何處於即時模式的存放區，資料來源選取範圍會預設為 _[!UICONTROL Sandbox]_.
* 如果您在「即時」模式中有任何存放區（一或多個），資料來源選項預設為 _[!UICONTROL Live]_.
* 報表匯出一律遵循資料來源選擇。

若要選取「訂單付款狀態」報表的資料來源，請執行下列步驟：

1. 於 _管理員_ 側欄，前往 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. 按一下 **[!UICONTROL Data source]** 並選取 _[!UICONTROL Live]_或_[!UICONTROL Sandbox]_.

   報表結果會根據選取的資料來源重新產生。

### 檢視交易

依預設，會顯示30天的交易。

搜尋中傳回或顯示在預設30天交易中的列數，會與「交易日期」行事曆選取器篩選器一起顯示在「付款」檢視網格上方。

向左向右捲動以檢視 [每個支付交易的資訊](#column-descriptions) 在每日報表中，包含交易日期、參考識別碼、商業發票號碼及付款方式明細。

#### 自訂交易時間範圍

在「付款報表」檢視中，您可以輸入特定日期或從日期選擇器選取日期範圍，以自訂您要檢視之付款交易的時間範圍：

1. 於 _管理員_ 側欄，前往 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. 按一下「交易日期」行事曆選擇器篩選器。
1. 選擇適用的日期範圍。
1. 檢視指定日期之網格中的付款狀態。

### 顯示和隱藏欄

依預設，「付款」報表檢視會顯示大部分可用的資訊欄。 不過，您可以自訂您在報表中看到的欄。

1. 於 _管理員_ 側欄，前往 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Payouts]**.
1. 按一下 _欄設定_ 圖示(![欄設定圖示](assets/column-settings.png))。
1. 若要自訂您在報表中看到的欄，請核取或取消核取清單中的欄。

   「付款」報表檢視會立即顯示您在「欄設定」功能表中所做的任何變更。 欄偏好設定將會儲存，而且如果您離開報表檢視，偏好設定將保持有效。

### 下載交易

您可以下載包含「付款」檢視格線中所有可見交易的.csv檔案。

1. 於 _管理員_ 側欄，前往 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. [自訂交易的日期範圍時間範圍](#customize-transactions-timeframe).
1. 按一下 _下載_ (![](assets/icon-download.png))圖示。

您的付款交易會以.csv格式下載。

### 欄說明

支付報表包含下列資訊。

| 欄 | 說明 |
| ------------ | -------------------- |
| [!UICONTROL Provider] | 付款提供者 |
| [!UICONTROL Provider trans] | 交易ID |
| [!UICONTROL Trans date] | 啟動交易的日期和時間 |
| [!UICONTROL Type] | 交易型別 — *[!UICONTROL PAYMENT]*， *[!UICONTROL BONUS]*， *[!UICONTROL CHARGEBACK]*， *[!UICONTROL CORRECTION]*， *[!UICONTROL CURRENCY_CONVERSATION]*， *[!UICONTROL DEPOSIT]*， *[!UICONTROL DISBURSEMENT]*， *[!UICONTROL DISPUTE]*， *[!UICONTROL FEES]*， *[!UICONTROL HOLD]*， *[!UICONTROL HOLD_RELEASE]*， *[!UICONTROL INCENTIVES]*， *[!UICONTROL OTHERS]*， *[!UICONTROL RECOUP]*， *[!UICONTROL REFUND]*， *[!UICONTROL REVERSAL]*， *[!UICONTROL WITHDRAWAL]* <br> <br>另請參閱 [交易型別](#transaction-types) 以取得詳細資訊。 |
| [!UICONTROL Status] | 交易的目前狀態 — *[!UICONTROL SUCCESS]*， *[!UICONTROL DENIED]*， *[!UICONTROL PENDING]* |
| [!UICONTROL Code] | 表示貸方(*CR*)或借方(*DR*) |
| [!UICONTROL Reference ID] | 與此事件相關的原始交易ID |
| [!UICONTROL Invoice] | 交易的商業發票ID （每筆訂單一個） |
| [!UICONTROL Commerce order] | 商務訂單ID <br> <br>若要檢視相關專案，請執行下列動作 [訂購資訊](https://docs.magento.com/user-guide/sales/orders.html)，按一下ID。 |
| [!UICONTROL Commerce trans] | 商務交易ID |
| [!UICONTROL Pay method] | 信用卡型別 — *[!UICONTROL BANK]*， *[!UICONTROL PAYPAL]*， *[!UICONTROL CREDIT_CARD]* — 和相關聯的卡片提供者(例如 *Visa* 或 *主卡*) |
| [!UICONTROL TRANS AMT] | 交易金額 |
| [!UICONTROL CUR] | 交易金額的幣別單位 |
| [!UICONTROL PENDING] | 尚未支付的金額 |
| [!UICONTROL CUR] | 暫緩金額的幣別單位 |
| [!UICONTROL SELLER AMT] | 轉帳至客戶或從客戶轉帳的資金金額 <br> <br>資金移出賣家帳戶會顯示破折號(-)首碼。 |
| [!UICONTROL CUR] | 賣家金額的貨幣單位 |
| [!UICONTROL PARTNER FEE] | 與交易相關的合作夥伴費用 <br> <br>從合作夥伴費用帳戶移出的基金會顯示破折號(-)首碼。 |
| [!UICONTROL CUR] | 合作夥伴費用的貨幣單位 |
| [!UICONTROL PROV FEES] | 與交易相關的費用 <br> <br>資金移出提供者的費用帳戶時，會顯示破折號(-)前置詞。 |
| [!UICONTROL CUR] | 提供者費用的貨幣單位 |
| [!UICONTROL FEE %] | 收取費用的交易金額百分比 |
| [!UICONTROL FIXED FEE] | 固定提供者費用金額 |
| [!UICONTROL CHBK FEE] | 與交易相關的借項衝回費用 <br> <br>破折號(-)首碼表示已反轉借項衝回費用。 |
| [!UICONTROL CUR] | 借項衝回費用的貨幣單位 |
| [!UICONTROL HOLD AMT] | 保留或解除保留的金額 <br> <br>破折號(-)首碼表示正在核發保留資金。 |
| [!UICONTROL CUR] | 保留金額的幣別單位 |
| [!UICONTROL RECOUP AMT] | 從回收帳戶中回收的金額 <br> <br>從回收帳戶移出的資金會顯示破折號(-)首碼。 |
| [!UICONTROL CUR] | 扣除金額的貨幣單位 |

### 交易型別

這些交易型態可在支付交易中註明。

| 報告 | 說明 |
| ------------ | -------------------- |
| [!UICONTROL PAYMENT] | 訂單的金額在買家和賣家之間移動 |
| [!UICONTROL AUTH] | 授權與授權作廢交易 |
| [!UICONTROL BONUS] | -- |
| [!UICONTROL CHARGEBACK] | 借項衝回費用與借項衝回費用迴轉交易 |
| [!UICONTROL CORRECTION] | -- |
| [!UICONTROL CURRENCY_CONVERSION] | -- |
| [!UICONTROL DEPOSIT] | -- |
| [!UICONTROL DISBURSEMENT] | -- |
| [!UICONTROL DISPUTE] | -- |
| [!UICONTROL FEES] | 合作夥伴費用、付款費用和費用迴轉交易 |
| [!UICONTROL HOLD] | -- |
| [!UICONTROL HOLD_RELEASE] | -- |
| [!UICONTROL INCENTIVES] | -- |
| [!UICONTROL OTHERS] | -- |
| [!UICONTROL RECOUP] | 從銀行或損失帳戶中收回 |
| [!UICONTROL REFUND] | -- |
| [!UICONTROL REVERSAL] | -- |
| [!UICONTROL WITHDRAWAL] | -- |
