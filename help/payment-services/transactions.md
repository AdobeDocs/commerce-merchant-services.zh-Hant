---
title: 交易報表
description: 使用「交易」報表來瞭解交易授權率及交易趨勢。
role: User
level: Intermediate
source-git-commit: 6ba5a283d9138b4c1be11b80486826304c63247f
workflow-type: tm+mt
source-wordcount: '1162'
ht-degree: 0%

---

# 交易報表

[!DNL Payment Services] 的 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 提供您完整的報表，讓您清楚瞭解商店的交易、訂單及付款。

![交易報表](assets/transactions-report.png){width="700" zoomable="yes"}

「交易」報表可顯示交易授權率及負面的交易趨勢，因此您可以有效監控商店的健康狀況，並預先識別及解決任何交易問題。

檢視店面訂單的個別交易及其付款方式、結果、付款回應代碼等。

「交易」報表中提供的資訊僅供商家使用。 請勿與客戶或其他潛在的詐騙者共用此資訊。 交易資訊可用於略過安全性檢查或下單導致借項衝回。

您可以下載.csv檔案格式的「交易」報表，以於現有的會計或訂單管理軟體中使用。

>[!NOTE]
>
>如果沒有，您將無法檢視財務報表 [已上線和已啟動的即時模式](production.md#enable-live-payments) 的 [!DNL Payment Services].

## 交易報表檢視

「交易」報表檢視可在「付款服務」的「交易」檢視中使用。 其中包含您商店中所有可用的交易資訊。

在 _管理員_ 側欄，前往 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**以檢視詳細的表格「交易」報表檢視。

![交易報表檢視](assets/transactions-report-detail.png){width="600" zoomable="yes"}

您可以根據本主題中的章節設定此檢視，以最理想的方式呈現您想要檢視的資料。

請參閱此報表中的連結商務訂單與提供者交易ID、交易金額、每筆交易的付款方式及其他。

並非所有支付方法都提供相同的資訊粒度。 例如，信用卡交易會在「交易」報表中提供回應、AVS和CCV代碼；PayPal智慧型按鈕則否。

您可以 [下載交易](#download-transactions) .csv檔案格式，用於現有的會計或訂單管理軟體。

### 選取資料來源

在「交易」報表檢視中，您可以選取資料來源 — **[!UICONTROL Live]** 或 **[!UICONTROL Sandbox]** — 您想要檢視其報告結果。

![資料來源選擇](assets/datasource.png){width="300" zoomable="yes"}

如果 _[!UICONTROL Live]_是選取的資料來源，您可以檢視使用的存放區報表資訊 [!DNL Payment Services] 在生產模式中。 如果_[!UICONTROL Sandbox]_ 是選取的資料來源，您可以看到沙箱模式的報表資訊。

資料來源選取專案的工作方式如下：

* 如果您沒有任何使用的商店 [!DNL Payment Services] 在生產模式中，資料來源選項預設為 _[!UICONTROL Sandbox]_.
* 如果您有任何商店（一或多個）使用 [!DNL Payment Services] 在生產模式中，資料來源選項預設為 _[!UICONTROL Live]_.
* 報表匯出一律遵循資料來源選擇。

若要為您的選取資料來源 [!UICONTROL Transactions] 報告：

1. 在 _管理員_ 側欄，前往 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. 按一下 **[!UICONTROL Data source]** 並選取 **[!UICONTROL Live]** 或 **[!UICONTROL Sandbox]**.

   報表結果會根據選取的資料來源重新產生。

### 自訂日期時間範圍

從「交易」報表檢視中，您可以選取特定日期，以自訂您要檢視的交易的時間範圍。 依預設，網格中會顯示30天的交易。

1. 在 _管理員_ 側欄，前往 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. 按一下 **[!UICONTROL Transaction dates]** 行事曆選擇器篩選器。
1. 選擇適用的日期範圍。
1. 在網格中檢視指定日期的交易。

### 篩選報表資訊

從「交易」報表檢視中，您可以選取篩選條件，以篩選您要檢視的狀態結果。

1. 在 _管理員_ 側欄，前往 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. 按一下 **[!UICONTROL Filter]** 選擇器。
1. 切換 _[!UICONTROL Transaction Result]_選項以僅檢視所選訂單異動的報告結果。
1. 切換 _[!UICONTROL Payment Method]_選項，僅針對選取的付款方式檢視報表結果。
1. 輸入 _最小訂單金額_ 或 _最大訂單金額_ 以在該訂單金額範圍內檢視報表結果。
1. 輸入 _[!UICONTROL Order ID]_以搜尋特定交易。
1. 按一下 **[!UICONTROL Hide filters]** 以隱藏篩選器。

### 顯示和隱藏欄

依預設，「交易」報表會顯示所有可用的資訊欄。 不過，您可以自訂您在報表中看到的欄。

1. 在 _管理員_ 側欄，前往 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. 按一下 **[!UICONTROL Column settings]** 圖示 ![欄設定圖示](assets/column-settings.png){width="20" zoomable="yes"}.
1. 若要自訂您在報表中看到的欄，請核取或取消核取清單中的欄。

   「交易」報表會立即顯示您在「欄設定」功能表中所做的任何變更。 欄偏好設定會儲存，如果您離開報表檢視，偏好設定仍會維持有效。

### 更新報表資料

「交易」報表檢視會顯示 _[!UICONTROL Last updated]_顯示上次更新報告資訊的時間戳記。 依預設，交易報告資料每三小時自動重新整理一次。

您也可以手動強制重新整理報表資料，以檢視最新的報表資訊。

1. 在 _管理員_ 側欄，前往 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. 按一下 _重新整理_ 圖示(![重新整理圖示](assets/refresh-button-med.png){width="20" zoomable="yes"})。

   交易報表資料會重新整理， *[!UICONTROL Update complete]* 確認功能會出現，而格線中會顯示最新的資訊。

### 下載交易

您可以下載.csv檔案，其中包含交易檢視格線中顯示的所有交易，無論您是檢視預設的30天交易還是自訂的時間範圍。

1. 在 _管理員_ 側欄，前往 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Transactions]**.
1. 如果您想檢視過去30天以外時間範圍的交易， [自訂狀態的日期範圍時間範圍](#customize-dates-timeframe).
1. 按一下 _下載_ ![下載圖示](assets/icon-download.png){width="20" zoomable="yes"} 圖示。

您的交易會以.csv格式下載。

### 欄說明

「交易」報表包含下列資訊。

| 欄 | 說明 |
| ------------ | -------------------- |
| [!UICONTROL Order ID] | 商務訂單ID （僅包含成功交易的值，且對於已拒絕的交易為空白）<br> <br>若要檢視相關專案，請執行下列動作： [訂購資訊](https://docs.magento.com/user-guide/sales/orders.html){target="_blank"}，按一下ID。 |
| [!UICONTROL Provider Transaction ID] | 付款提供者提供的交易ID；僅包含成功交易的值，並包含拒絕交易的破折號。 |
| [!UICONTROL Transaction Date] | 交易日期時間戳記 |
| [!UICONTROL Payment Method] | 交易的付款方法；適用於Payment Services 1.6.0或更新版本 |
| [!UICONTROL Result] | 交易的結果 — *[!UICONTROL OK]* （成功的交易）， *[!UICONTROL Rejected by Payment Provider]* （被PayPal拒絕）， *[!UICONTROL Rejected by Bank]* （已遭發卡銀行拒絕） |
| [!UICONTROL Response Code] | 提供付款提供者或銀行拒絕原因的錯誤代碼；請參閱可能的回應代碼清單與說明 [`Rejected by Bank` 狀態](https://developer.paypal.com/docs/api/orders/v2/#definition-processor_response) 和 [`Rejected by Payment Provider` 狀態](https://developer.paypal.com/api/rest/reference/orders/v2/errors/). |
| [!UICONTROL AVS Code] | 地址驗證服務代碼；付款請求的處理器回應資訊。 另請參閱 [可能的程式碼和說明清單](https://developer.paypal.com/docs/api/orders/v2/#definition-processor_response) 以取得詳細資訊。 |
| [!UICONTROL CVV Code] | 信用卡與借記卡的卡片驗證值代碼；請參閱 [可能的程式碼和說明清單](https://developer.paypal.com/docs/api/orders/v2/#definition-processor_response) 以取得詳細資訊。 |
| [!UICONTROL Amount] | 交易的訂單金額 |
| [!UICONTROL Currency] | 用於交易訂單的貨幣 |
| [!UICONTROL Type] | [付款動作](../payment-services/production.md#set-payment-services-as-payment-method) 交易 — `Authorize` 或 `Authorize and Capture` |

### 錯誤回應代碼

此 _回應代碼_ 欄會顯示與交易相關的特定錯誤或成功代碼。 您可能會看到的一些常見錯誤代碼包括：

* `PAYMENT_DENIED`—PayPal拒絕交易，因為懷疑是詐騙。
* `INTERNAL_SERVER_ERROR` — 交易遭到PayPal拒絕，並發生PayPal伺服器錯誤。 可以重試交易。
* `INSTRUMENT_DECLINED`—PayPal已根據選取的付款方式拒絕客戶。 可以使用不同的付款方式重試交易。
* `9500` — 關聯銀行拒絕交易，因為懷疑交易是詐騙。
* `5120` — 關聯銀行拒絕交易，因為客戶沒有足夠的資金進行付款。
* `5650` — 關聯銀行拒絕交易，因為銀行需要強大的客戶驗證([3DS](security.md#3ds))。

2023年6月1日以後交易的失敗交易有詳細的錯誤回應代碼。 2023年6月1日之前發生的交易會顯示部分報表資料。

