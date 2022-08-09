---
title: 應用程式設定
description: 設定 [!DNL Store Assist] app用於管理端到端商店履行工作流和線上購買流程，在商店訂單中提貨。
role: User, Admin
level: Intermediate
exl-id: bcb5b02b-0141-407a-ad55-6e10e8e1aa90
source-git-commit: 68e615671f4e465d7fe89794613dbf129ae66dbf
workflow-type: tm+mt
source-wordcount: '606'
ht-degree: 0%

---

# 應用程式設定

Store Assist是由Walmart Commerce Technologies支援的「按服務完成」(FaaS)平台應用。 該應用提供了店內履行功能以處理 [!DNL buy online]。 [!DNL pick up in store] (BOPIS)訂單。  使用Store Assist ，儲存關聯可以查看客戶訂購的物料、更快地挑選正確的物料，以及設定已履行訂單以在商店內或在路邊向客戶提貨。

Store Assist應用程式接收所有訂單和客戶資訊 — 從訂單詳細資訊到提取時間 — 並通過移動設備線上儲存關聯資料。 該應用包括 [!UICONTROL Pick]。 [!UICONTROL Stage]。 [!UICONTROL Handoff], [!UICONTROL Orders] 幫助Store Associates進行履行活動的模組，如下：

- 分配訂單交貨日期和時間。
- 在客戶到達要接收訂單的地點時接收通知。
- 為客戶切換階段訂單。
- 跟蹤其分配的儲存位置中所有訂單的訂單狀態。

>[!NOTE]
>
>請參閱 [儲存協助履行工作流](store-assist-modules.md) 瞭解有關Store Assist應用的詳細資訊。

## 配置Store Assist應用

Store Assist應用需要兩種配置：

- Adobe Commerce管理員配置設定 [從Adobe Commerce管理系統設定管理用戶帳戶、用戶角色和資源權限](user-setup.md)。

- 前端配置設定可自定義Store Assist應用介面和其他設定，包括：

   - **將應用商店幫助應用品牌化** — 使用公司徽標和顏色自定義應用程式用戶介面。

   - **更新預設說明** — 自定義Store Assist介面中Pick 、 Stage 、 Handown和Order模組的說明，以符合您公司的策略和過程，並指導Store Associates完成工作流的每個步驟。

   - **本地化** — 選擇應用的可用語言。 選擇日期和時間格式，然後選擇預設度量單位和預設幣種。

   - **不活動時間** — 指定應用程式在註銷之前必須處於非活動狀態的時間。

   - **從商店取消** — 指定是否可以從儲存中取消訂單以及哪些角色具有取消權限

   - **訂單清理窗口** — 指定在重新貯存之前已挑庫訂單在轉移中的計畫裝貨時間（例如，三天）的過去時間。

   - 在應用說明中自定義所有內容（領料、轉移、轉移）。

   - **領料通知** — 指定是否在客戶下訂單後發送推式通知以啟動挑庫流程。

   - **簽入通知** — 指定在客戶等待時間超過指定時間段後，是否在訂單挑庫的簽入過程中發送推送通知。 或者，禁用通知。

   - **切換過程** — 當Store Associate將訂單交付給客戶時啟用可選流程，例如，要求客戶簽名或提示關聯檢查客戶ID。

   - **在切換時啟用項目拒絕** — 允許客戶在訂單切換期間返回或取消訂單項。
   與Walmart Commerce Technologies客戶服務團隊合作，為Store Assist應用程式完成前端配置。

## 應用下載和安裝

完成Store Assist應用程式配置後，Store Associates可以從其移動設備下載、安裝和登錄Store Assist應用程式。

- 驗證移動設備是否滿足 [硬體和軟體要求](solution-requirements.md#store-assist-app-requirements) 的XML。

- 從下載Store Assist應用 [AppleApp Store](https://apps.apple.com/us/app/store-assist-by-walmart/id1609281539){target=&quot;_blank&quot;}或 [Google Play店](https://play.google.com/store/apps/details?id=com.walmart.faas.storeassist){target=&quot;_blank&quot;}。

- 儲存關聯需要以下資訊才能登錄：

   - **[!UICONTROL Company name]** 與Store Assist帳戶關聯

   - **儲存協助帳戶憑據** — 其帳戶的用戶名和密碼憑據。
   Adobe Commerce管理員可以建立用戶帳戶並為具有以下條件的儲存位置的Store Assist應用用戶帳戶設定權限 [店內裝貨](merchant-store-configuration.md#pickup-location-configuration) 在「管理儲存」設定中啟用。
