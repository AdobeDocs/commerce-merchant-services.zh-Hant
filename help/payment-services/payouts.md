---
title: 支付報告
description: 使用「支付」報告可以完全透明地記錄支付金額、已處理數量以及財務對帳的交易級別詳細報告。
role: User
level: Intermediate
exl-id: f3f99474-cd28-4c8f-b0ea-dca8e014b108
source-git-commit: 9596815e31402f23b399b223f3221074331c1773
workflow-type: tm+mt
source-wordcount: '857'
ht-degree: 0%

---

# 支付報告

[!DNL Payment Services] 為 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 提供全面的報告，以便您能夠清楚地查看您商店的訂單和付款。

![財務報告視圖](assets/reports-view.png)

「支付」報告一覽式顯示了全面的支付資訊，使您對支付金額、處理量以及財務調節的交易級別的詳細報告具有完全的透明度。

您不必開啟多個視圖以交叉參考訂單和付款或調節帳戶。 [!DNL Payment Services] 為 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 使您能夠從一個位置執行所有這些操作 — 支付報告 — 以便您能夠高效地查看和管理支付。

請參閱管理員的「支付」報表中的連結商業訂單和交易ID、交易金額、每筆交易的付款方法等。

您可以以.csv檔案格式下載支付交易記錄，以用於現有會計或訂單管理軟體。

>[!NOTE]
>
>此表中顯示的資料按降序排序(`DESC`) `TRANS DATE`。 的 `TRANS DATE` 是事務處理的啟動日期和時間。

## 可用性

在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**。

![管理員中的支付事務](assets/payouts-report.png)

## 選擇資料源

在「支付」報表視圖中，您可以選擇資料源 — _[!UICONTROL Live]_或 [!UICONTROL Sandbox]_ — 您希望查看其報告結果。

![資料源選擇](assets/datasource.png)

如果 _[!UICONTROL Live]_是選定的資料源，您可以查看即時商店的報告資訊。 如果 [!UICONTROL Sandbox]_是選定的資料源，您可以查看沙盒環境的報告資訊。

資料源選擇的工作方式如下：

* 如果沒有處於「即時」模式的儲存，則資料源選擇的預設值為 _[!UICONTROL Sandbox]_。
* 如果在「即時」模式下有任何儲存（一個或多個），則資料源選擇的預設值為 _[!UICONTROL Live]_。
* 報告導出始終遵循資料源選擇。

要為「訂單付款狀態」報表選擇資料源，請執行以下操作：

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**。
1. 按一下 **[!UICONTROL Data source]** 選擇 _[!UICONTROL Live]_或 [!UICONTROL Sandbox]_。

   根據所選資料源重新生成報告結果。

## 查看交易記錄

預設情況下，30天的事務顯示在網格中。

在搜索中返回或在預設的30天交易中顯示的行數顯示在「支付」視圖網格的上方，並與「交易日期」日曆選擇器篩選器一起顯示。

向左和向右滾動以查看 [每個支付交易記錄的資訊](#column-descriptions) 日報表中，包括交易記錄日期、參考ID、發票編號和付款方法詳細資訊。

### 自定義交易時間範圍

在「支付」視圖中，您可以通過輸入特定日期或從日期選取器中選擇日期範圍來自定義要查看的支付事務處理的時間範圍：

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**。
1. 按一下「事務處理日期日曆」選擇器篩選器。
1. 選擇適用的日期範圍。
1. 在網格中查看指定日期的支付狀態。

## 下載交易記錄

您可以下載一個.csv檔案，其中包含「支付」視圖網格中可見的所有交易。

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**。
1. [自定義交易記錄的日期範圍時間範圍](#customize-transactions-timeframe)。
1. 按一下 _下載_ (![](assets/icon-download.png))。

您的支付交易以.csv格式下載。

## 交易記錄資訊

「支付」視圖顯示網格中顯示的每項交易的詳細資訊。

### 列說明

付款報表包括以下資訊。

| 列 | 說明 |
| ------------ | -------------------- |
| [!UICONTROL Provider] | 付款提供方 |
| [!UICONTROL Provider trans] | 事務ID |
| [!UICONTROL Trans date] | 啟動交易記錄的日期和時間 |
| [!UICONTROL Type] | 事務類型 — *[!UICONTROL PAYMENT]*。 *[!UICONTROL AUTH]*。 *[!UICONTROL BONUS]*。 *[!UICONTROL CHARGEBACK]*。 *[!UICONTROL CORRECTION]*。 *[!UICONTROL CURRENCY_CONVERSATION]*。 *[!UICONTROL DEPOSIT]*。 *[!UICONTROL DISBURSEMENT]*。 *[!UICONTROL DISPUTE]*。 *[!UICONTROL FEES]*。 *[!UICONTROL HOLD]*。 *[!UICONTROL HOLD_RELEASE]*。 *[!UICONTROL INCENTIVES]*。 *[!UICONTROL OTHERS]*。 *[!UICONTROL RECOUP]*。 *[!UICONTROL REFUND]*。 *[!UICONTROL REVERSAL]*。 *[!UICONTROL WITHDRAWAL]* <br> <br>請參閱 [交易記錄類型](#transaction-types) 的子菜單。 |
| [!UICONTROL Status] | 交易記錄的當前狀態 — *[!UICONTROL SUCCESS]*。 *[!UICONTROL DENIED]*。 *[!UICONTROL PENDING]* |
| [!UICONTROL Code] | 指示貸項(*CR*)或借方(*DR*) |
| [!UICONTROL Reference ID] | 此事件相關的原始事務ID |
| [!UICONTROL Invoice] | 交易記錄的發票ID（每張訂單一張） |
| [!UICONTROL Commerce order] | 商業訂單ID <br> <br>查看相關 [訂單資訊](https://docs.magento.com/user-guide/sales/orders.html){target=&quot;_blank&quot;}，按一下ID。 |
| [!UICONTROL Commerce trans] | 商務交易記錄ID <br> <br>查看相關 [事務資訊](https://docs.magento.com/user-guide/sales/transactions.html){target=&quot;_blank&quot;}，按一下ID。 |
| [!UICONTROL Pay method] | 信用卡類型 — *[!UICONTROL BANK]*。 *[!UICONTROL PAYPAL]*。 *[!UICONTROL CREDIT_CARD]* — 和關聯的卡提供商(例如 *維薩* 或 *萬事達*) |
| [!UICONTROL Trans amt] | 交易記錄的金額 |
| [!UICONTROL Cur] | 交易記錄金額的幣種單位 |
| [!UICONTROL Pending] | 尚未支付的金額 |
| [!UICONTROL Cur] | 待定金額的幣種單位 |
| [!UICONTROL Seller amt] | 轉入或轉出客戶的資金金額 <br> <br>從賣方帳戶移出的資金顯示破折號(-)前置詞。 |
| [!UICONTROL Cur] | 賣方金額的幣種單位 |
| [!UICONTROL Partner fee] | 與交易關聯的合作夥伴費用 <br> <br>從合作夥伴費用帳戶中移出的資金顯示一個破折號(-)前置詞。 |
| [!UICONTROL Cur] | 合作夥伴費用的幣種單位 |
| [!UICONTROL Prov fees] | 與交易關聯的費用 <br> <br>從提供商的費用帳戶中移出的資金顯示破折號(-)前置詞。 |
| [!UICONTROL Cur] | 供應商費用的幣種單位 |
| [!UICONTROL Fee %] | 作為費用收取的交易金額的百分比 |
| [!UICONTROL Fixed fee] | 固定提供商費用金額 |
| [!UICONTROL Chbk fee] | 與交易關聯的拖欠款項費用 <br> <br>破折號(-)前置詞表示已衝銷按儲存容量使用計費費用。 |
| [!UICONTROL Cur] | 按儲存容量使用計費費用的幣種單位 |
| [!UICONTROL Hold amt] | 暫掛或從暫掛中釋放的金額 <br> <br>短划線(-)前置詞表示正在釋放暫掛資金。 |
| [!UICONTROL Cur] | 暫掛金額的幣種單位 |
| [!UICONTROL Recoup amt] | 從收回帳戶中回收的金額 <br> <br>從收回帳戶中移出的資金顯示一個破折號(-)前置詞。 |
| [!UICONTROL Cur] | 收回金額的幣種單位 |

### 交易記錄類型

這些交易類型可以在支付交易中記錄。

| 報告 | 說明 |
| ------------ | -------------------- |
| [!UICONTROL PAYMENT] | 在訂單的買方和賣方之間轉移的錢 |
| [!UICONTROL AUTH] | 授權和授權撤消交易 |
| [!UICONTROL BONUS] | — |
| [!UICONTROL CHARGEBACK] | 按儲存容量使用計費費用和按儲存容量使用計費費用衝銷交易記錄 |
| [!UICONTROL CORRECTION] | — |
| [!UICONTROL CURRENCY_CONVERSION] | — |
| [!UICONTROL DEPOSIT] | — |
| [!UICONTROL DISBURSEMENT] | — |
| [!UICONTROL DISPUTE] | — |
| [!UICONTROL FEES] | 合作夥伴費用、付款費用和費用衝銷交易記錄 |
| [!UICONTROL HOLD] | — |
| [!UICONTROL HOLD_RELEASE] | — |
| [!UICONTROL INCENTIVES] | — |
| [!UICONTROL OTHERS] | — |
| [!UICONTROL RECOUP] | 從銀行或虧損帳戶中收回 |
| [!UICONTROL REFUND] | — |
| [!UICONTROL REVERSAL] | — |
| [!UICONTROL WITHDRAWAL] | — |
