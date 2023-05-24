---
title: '[!DNL Quick Checkout] 報告'
description: '''[!DNL Quick Checkout] 提供完整的報告資訊。」'
exl-id: 91c687f4-9953-4c2f-b240-73430603e6a1
source-git-commit: bdfac90aa221f39dfc53eee833c473c7dcb0a042
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# 報表

[!DNL Quick Checkout] 適用於Adobe Commerce和Magento Open Source的全方位報表，讓您可獲得商店結帳體驗統計資料的詳細資訊。

![報表檢視](assets/reports-view-big-checkout.png)

>[!WARNING]
>
> 若要允許Adobe Commerce與Bolt共用簽出資訊， [**結帳追蹤**](../quick-checkout/settings-quick-checkout.md)  必須在「管理員」中啟用設定。 依預設，此組態選項設為 **是**. 如果此選項設定為 **否**，報告將受到影響。 Bolt會在東部標準時間(EST)凌晨03:00，每天重新整理一次報表資訊。

## 概述報表

「概述」區段中的圖表顯示有關您商店結帳效能的詳細資訊，包括平均結帳時間、結帳期間建立的新帳戶或結帳放棄期間。

![報表概觀](assets/overview-report-checkout.png)

| 圖表 | 說明 |
|---|---|
| [!UICONTROL Checkout abandonment] | 未完成購買就退出結帳程式的訪客百分比。 |
| [!UICONTROL Checkout abandonment breakdown] | 放棄結帳除以訪客型別。 工具提示顯示Bolt和Guest之間的百分比差異。 選項： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Average checkout time] | 訪客完成結帳程式的平均時間。 |
| [!UICONTROL Average checkout time breakdown] | 平均結帳時間除以訪客型別。 工具提示顯示Bolt和Guest之間的百分比差異。 選項： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Orders by account type] | 下訂單數除以訪客型別。 選項： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |

## 趨勢報表

「趨勢」區段中的圖表會顯示依帳戶型別篩選的結帳體驗趨勢，或在結帳期間建立的新帳戶。

![報表趨勢](assets/trends-report-checkout.png)

| 圖表 | 說明 |
|---|---|
| [!UICONTROL Checkout abandonment by account type] | 結帳放棄趨勢除以訪客型別。 選項： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Orders by account type] | 已下訂單的趨勢除以訪客型別。 選項： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL New accounts on your store] | 您商店趨勢中的新帳戶。 |

## 篩選資料

您可以篩選按日期或現有預設集顯示的結果，例如 **過去30天**.

![篩選器檢視](assets/filter-view.png)

| 欄位 | 說明 |
|---|---|
| [!UICONTROL Preset] | 顯示預設預設集的下拉式清單，可用來顯示特定範圍的資料。 預設值：過去30天 |
| [!UICONTROL Date range] | 下拉式清單，可讓您根據選取的日期選取特定的資料範圍。 |
