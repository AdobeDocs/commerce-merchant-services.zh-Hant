---
title: '"[!DNL Quick Checkout] 報告`'
description: '"[!DNL Quick Checkout] 提供全面的報告資訊。'
exl-id: 91c687f4-9953-4c2f-b240-73430603e6a1
source-git-commit: bdfac90aa221f39dfc53eee833c473c7dcb0a042
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# 報告

[!DNL Quick Checkout] 對於Adobe Commerce和Magento Open Source，您可以提供全面的報告，以便您能夠獲得有關您商店結帳體驗統計的詳細資訊。

![報告視圖](assets/reports-view-big-checkout.png)

>[!WARNING]
>
> 為允許Adobe Commerce與Bolt共用結帳資訊， [**簽出跟蹤**](../quick-checkout/settings-quick-checkout.md)  必須在管理中啟用設定。 預設情況下，此配置選項設定為 **是**。 如果此選項設定為 **否**，報告將受到影響。 Bolt每天在東部標準時間(EST)上午3:00刷新一次報告資訊。

## 概覽報告

「概述」部分中的圖表顯示有關您商店的結帳效能的詳細資訊，包括平均結帳時間、結帳或結帳放棄期間建立的新帳戶。

![報告概述](assets/overview-report-checkout.png)

| 圖表 | 說明 |
|---|---|
| [!UICONTROL Checkout abandonment] | 未完成採購而退出結帳流程的訪問者百分比。 |
| [!UICONTROL Checkout abandonment breakdown] | 結帳放棄按訪客類型劃分。 工具提示顯示「螺栓」和「來賓」之間的百分比差異。 選項： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Average checkout time] | 訪問者完成結帳過程所花的平均時間。 |
| [!UICONTROL Average checkout time breakdown] | 平均結帳時間除以訪問者類型。 工具提示顯示「螺栓」和「來賓」之間的百分比差異。 選項： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Orders by account type] | 按訪問者類型劃分的訂單。 選項： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |

## 趨勢報告

「趨勢」部分中的圖表顯示按帳戶類型或在結帳期間建立的新帳戶篩選的結帳體驗趨勢。

![報告趨勢](assets/trends-report-checkout.png)

| 圖表 | 說明 |
|---|---|
| [!UICONTROL Checkout abandonment by account type] | 結賬放棄趨勢按訪客類型劃分。 選項： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Orders by account type] | 訂單按訪問者類型劃分趨勢。 選項： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL New accounts on your store] | 你的商店趨勢上的新帳戶。 |

## 篩選資料

可以篩選按日期顯示的結果或現有預設，如 **最後三十天**。

![篩選器視圖](assets/filter-view.png)

| 欄位 | 說明 |
|---|---|
| [!UICONTROL Preset] | 一個下拉清單，顯示可用於顯示特定資料範圍的預設預設。 預設情況下：最後三十天 |
| [!UICONTROL Date range] | 一個下拉清單，允許您根據選定日期選擇特定的資料範圍。 |
