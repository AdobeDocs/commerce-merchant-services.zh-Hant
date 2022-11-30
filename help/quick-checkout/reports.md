---
title: '[!DNL Quick Checkout] 報告'
description: '''[!DNL Quick Checkout] 提供全面的報告資訊。'
exl-id: 91c687f4-9953-4c2f-b240-73430603e6a1
source-git-commit: bdfac90aa221f39dfc53eee833c473c7dcb0a042
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 報表

[!DNL Quick Checkout] 針對Adobe Commerce和「Magento Open Source」，提供全方位的報表，以便取得您商店結帳體驗統計資料的詳細資訊。

![報表檢視](assets/reports-view-big-checkout.png)

>[!WARNING]
>
> 若要允許Adobe Commerce與Bolt共用結帳資訊，請 [**結帳追蹤**](../quick-checkout/settings-quick-checkout.md)  必須在「管理」中啟用。 預設情況下，此配置選項設定為 **是**. 如果此選項設為 **否**，則報表會受到影響。 Bolt每天在東部標準時間(EST)凌晨03:00刷新報告資訊一次。

## 概述報表

「綜覽」區段中的圖表顯示有關您商店結帳效能的詳細資訊，包括平均結帳時間、結帳或結帳放棄期間建立的新帳戶。

![報表概觀](assets/overview-report-checkout.png)

| 圖表 | 說明 |
|---|---|
| [!UICONTROL Checkout abandonment] | 未完成購買就退出結帳程式的訪客百分比。 |
| [!UICONTROL Checkout abandonment breakdown] | 結帳放棄率除以訪客類型。 工具提示顯示「螺栓」和「來賓」之間的百分比差異。 選項： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Average checkout time] | 訪客完成結帳程式所花費的平均時間。 |
| [!UICONTROL Average checkout time breakdown] | 平均結帳時間除以訪客類型。 工具提示顯示「螺栓」和「來賓」之間的百分比差異。 選項： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Orders by account type] | 下單數除以訪客類型。 選項： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |

## 趨勢報表

趨勢區段中的圖表會依帳戶類型或結帳期間建立的新帳戶，顯示您的結帳體驗趨勢篩選器。

![報表趨勢](assets/trends-report-checkout.png)

| 圖表 | 說明 |
|---|---|
| [!UICONTROL Checkout abandonment by account type] | 結帳放棄趨勢除以訪客類型。 選項： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Orders by account type] | 下單趨勢除以訪客類型。 選項： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL New accounts on your store] | 您商店趨勢的新帳戶。 |

## 篩選資料

您可以依日期或現有預設集(例如 **最近30天**.

![篩選檢視](assets/filter-view.png)

| 欄位 | 說明 |
|---|---|
| [!UICONTROL Preset] | 顯示預設預設集的下拉式清單，可用來顯示特定的資料範圍。 依預設：最近30天 |
| [!UICONTROL Date range] | 下拉式清單可讓您根據選取的日期選取特定的資料範圍。 |
