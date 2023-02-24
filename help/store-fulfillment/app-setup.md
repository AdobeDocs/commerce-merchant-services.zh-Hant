---
title: 應用程式設定
description: 設定 [!DNL Store Assist] 若要管理線上購買的端對端商店履行工作流程和流程，請依商店訂單提貨。
role: User, Admin
level: Intermediate
exl-id: bcb5b02b-0141-407a-ad55-6e10e8e1aa90
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 0%

---

# 應用程式設定

Store Assist是由Walmart Commerce Technologies提供技術支援的一款即成即用(FaaS)平台應用。 應用程式提供商店內完成功能，可處理 [!DNL buy online, pick up in store] (BOPIS)訂單。 借助「商店輔助」，商店關聯可以查看客戶訂購哪些物料、更快地挑選正確的物料，以及設定已履行訂單以便在店內或組織端提貨交貨給客戶。

Store Assist應用程式會接收所有訂單和客戶資訊（從訂單詳細資訊到提取時間），並通過移動設備線上儲存關聯資料。 應用程式包含 [!UICONTROL Pick], [!UICONTROL Stage], [!UICONTROL Handoff]，和 [!UICONTROL Orders] 模組，幫助儲存與完成活動相關聯，如：

- 指派訂單傳送日期和時間。
- 在客戶到達訂單提貨時收到通知。
- 下達訂單，以切換至客戶。
- 跟蹤其分配的儲存位置中所有訂單的訂單狀態。

>[!NOTE]
>
>請參閱 [儲存協助完成工作流程](store-assist-modules.md) 以進一步了解Store Assist應用程式。

## 設定Store Assist應用程式

Store Assist應用程式需要兩種配置：

- Adobe Commerce管理系統設定 [管理用戶帳戶、用戶角色、資源權限](user-setup.md)，和 [在簽入過程中，客戶可以選擇汽車製造和模型](check-in-experience-setup.md).

- 前端配置設定，以自訂Store Assist應用程式介面和其他設定，包括：

   - **為Store Assist應用程式加上品牌** — 使用您的公司標誌和顏色自訂應用程式使用者介面。

   - **更新預設指示** — 定制「商店輔助挑庫」、「預備」、「切換」和「訂單」模組中的說明，以指導Store Associates完成您公司的完成工作流的每個步驟。

   - **本地化** — 選取應用程式的可用語言。 選擇日期和時間格式，然後選取預設測量單位和預設貨幣。

   - **閒置時間** — 指定應用程式在登出前必須處於非作用中狀態的時間長度。

   - **從商店取消** — 指定是否可以從商店取消訂單，以及哪些角色具有取消權限

   - **訂單清理窗口** — 指定超過 [預計提貨提前期](enable-general.md#delivery-method-title-configuration) 在重新儲存之前，挑庫的訂單仍保留在暫存中，例如，三天。 預設值為7天。 如果此設定已開啟，則此時間過期時，訂單會自動取消。 重新儲存物品，並且商戶接收取消電子郵件。

   - 在應用程式指示中自訂全部（挑選、測試、分手）。

   - **領料通知** — 指定是否在客戶下訂單後發送推播通知以開始領料流程。

   - **簽入通知** — 指定是否在訂單選擇的簽入過程中發送推播通知（簽入後、客戶等待時間超過指定時段後）。 或者，停用通知。

   - **關閉過程** — 當Store Associate向客戶交付訂單時，啟用可選流程，例如需要客戶簽名或提示關聯人檢查客戶ID。

   - **在切換時啟用項目拒絕** — 允許客戶在訂單切換期間返回或取消訂單項目。
   與Walmart Commerce Technologies客戶服務團隊合作，為Store Assist應用程式完成前端配置。

## 應用程式下載和安裝

設定好Store Assist應用程式後，Store Associates就可以從行動裝置下載、安裝和登入Store Assist應用程式。

- 確認行動裝置符合 [硬體和軟體要求](solution-requirements.md#store-assist-app-requirements) （商店完成解決方案）。

- 從下載Store Assist應用程式 [AppleApp Store](https://apps.apple.com/us/app/store-assist-by-walmart/id1609281539){target="_blank"} or the [Google Play store](https://play.google.com/store/apps/details?id=com.walmart.faas.storeassist){target="_blank"}.

- Store Associates需要下列資訊才能登入：

   - **[!UICONTROL Company name]** 與商店協助帳戶關聯

   - **儲存協助帳戶憑證** — 其帳戶的用戶名和密碼憑據。
   Adobe Commerce管理員可以建立和管理 [!DNL Store Assist app] 所有儲存位置的用戶帳戶 [店內取貨](merchant-store-configuration.md#pickup-location-configuration) 在「管理員商店」設定中啟用。
