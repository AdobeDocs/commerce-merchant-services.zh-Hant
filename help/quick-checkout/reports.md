---
title: 『[!DNL Quick Checkout] 報告
description: 『[!DNL Quick Checkout] 提供完整的報表資訊。'
exl-id: 91c687f4-9953-4c2f-b240-73430603e6a1
feature: Checkout, Services
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 1%

---

# 報表

[!DNL Quick Checkout] 適用於Adobe Commerce和Magento Open Source，提供您全方位的報告，好讓您取得商店結帳體驗統計資料的詳細資訊。

![報表檢視](assets/reports-view-big-checkout.png)

>[!WARNING]
>
> 若要允許Adobe Commerce與Bolt共用簽出資訊， [**結帳追蹤**](../quick-checkout/settings-quick-checkout.md)  必須在Admin中啟用設定。 根據預設，此組態選項設為 **是**. 如果此選項設定為 **否**，報告將受到影響。 Bolt會在東部標準時間(EST)凌晨03:00，每日重新整理一次報表資訊。

## 概述報表

「概述」區段中的圖表顯示關於存放區結帳效能的詳細資訊，包括平均結帳時間、結帳期間建立的新帳戶或結帳放棄期間。

![報表概觀](assets/overview-report-checkout.png)

| 圖表 | 說明 |
|---|---|
| [!UICONTROL Checkout abandonment] | 未完成購買就退出結帳程式的訪客百分比。 |
| [!UICONTROL Checkout abandonment breakdown] | 結帳放棄除以訪客型別。 工具提示顯示Bolt和Guest之間的百分比差異。 選項： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Average checkout time] | 訪客完成結帳程式的平均時間。 |
| [!UICONTROL Average checkout time breakdown] | 平均結帳時間除以訪客型別。 工具提示顯示Bolt和Guest之間的百分比差異。 選項： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Orders by account type] | 下訂單數除以訪客型別。 選項： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |

## 趨勢報表

Trends區段中的圖表會顯示依帳戶型別篩選的結帳體驗趨勢，或在結帳期間建立的新帳戶。

![報表趨勢](assets/trends-report-checkout.png)

| 圖表 | 說明 |
|---|---|
| [!UICONTROL Checkout abandonment by account type] | 結帳放棄趨勢除以訪客型別。 選項： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Orders by account type] | 已下訂單趨勢除以訪客型別。 選項： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL New accounts on your store] | 有關您商店趨勢的新帳戶。 |

## 篩選資料

您可以依日期或現有預設集篩選顯示的結果，例如 **過去30天**.

![篩選器檢視](assets/filter-view.png)

| 欄位 | 說明 |
|---|---|
| [!UICONTROL Preset] | 顯示預設預設預設集的下拉式清單，可用來顯示特定範圍的資料。 依預設：過去30天 |
| [!UICONTROL Date range] | 允許您根據所選日期選擇特定資料範圍的下拉式清單。 |
