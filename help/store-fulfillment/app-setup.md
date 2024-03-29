---
title: 應用程式設定
description: 設定 [!DNL Store Assist] 應用程式來管理線上購買、商店訂單取貨的端對端商店履行工作流程和流程。
level: Intermediate
role: Admin
feature: Shipping/Delivery, Configuration, Tools and External Services
exl-id: bcb5b02b-0141-407a-ad55-6e10e8e1aa90
source-git-commit: 78b09113e72382053b01d6016276bae3aa545fa3
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 0%

---

# 應用程式設定

Store Assist是由Walmart Commerce Technologies提供支援的以服務方式履行(FaaS)平台應用程式。 應用程式提供店內履行功能，供您處理 [!DNL buy online, pick up in store] (BOPIS)訂單。 透過「商店協助」，店舖夥伴可以檢視客戶訂購的料號、更快地挑選正確的料號，以及設定已履行訂單，以便店內或路邊取貨交貨給客戶。

Store Assist應用程式會接收所有訂單和客戶資訊 — 從訂單詳細資料到取貨時間，並透過行動裝置將資料提供給線上商店夥伴。 應用程式包含 [!UICONTROL Pick]， [!UICONTROL Stage]， [!UICONTROL Handoff]、和 [!UICONTROL Orders] 模組可協助Store Associates進行如下的履行活動：

- 指定訂單交貨日期和時間。
- 當客戶抵達取貨地點時，接收他們的通知。
- 中繼客戶移交訂單。
- 追蹤其指定商店位置中所有訂單的訂單狀態。

>[!NOTE]
>
>進一步瞭解Store Assist應用程式，請檢閱 [商店協助履行工作流程](store-assist-modules.md) 主題。

## 設定商店協助應用程式

Store Assist應用程式需要兩種設定型別：

- Adobe Commerce管理系統設定至 [管理使用者帳號、使用者角色、資源許可權](user-setup.md)、和 [客戶在入庫過程中可用的汽車製造及模型選擇](check-in-experience-setup.md).

- 前端組態設定可自訂Store Assist應用程式介面和其他設定，包括：

   - **品牌化Store Assist應用程式** — 使用您公司的標誌和顏色，自訂應用程式使用者介面。

   - **更新預設指示** — 自訂「商店協助挑選」、「預備」、「移交」和「訂購」模組中的指示，以引導「商店夥伴」完成公司履行工作流程的每一個步驟。

   - **本地化** — 選取應用程式的可用語言。 選擇您的日期和時間格式，並選取您的預設度量單位和預設貨幣。

   - **非使用中時間** — 指定應用程式在登出前必須處於非使用中狀態的時間長度。

   - **從商店取消** — 指定是否可以從商店取消訂單，以及哪些角色具有取消許可權

   - **訂單清理視窗** — 指定經過 [預估取車前置時間](enable-general.md#delivery-method-title-configuration) 撿料訂單在重新存貨之前會保留在暫存中，例如3天。 預設值為七天。 如果開啟此設定，則當此時間到期時，會自動取消訂單。 商品已補充庫存，商家會收到取消電子郵件。

   - 自訂所有應用程式內指示（挑選、分段、交出）。

   - **領料通知** — 指定是否傳送推播通知，以在客戶下訂單後開始撿料流程。

   - **簽到通知** — 指定是否要在取貨簽到程式期間傳送推播通知 — 簽到後、客戶等待時間超過指定時段後。 或者，停用通知。

   - **移交程式** — 當「商店關聯」將訂單交付給客戶時，啟用可選程式，例如，需要客戶簽名或提示關聯檢查客戶ID。

   - **在移交時啟用專案拒絕** — 允許客戶在訂單移交期間退回或取消訂單專案。

  與Walmart Commerce Technologies Client Services團隊合作，完成Store Assist應用程式的前端設定。

## 應用程式下載和安裝

設定Store Assist應用程式後，Store Associates可以從行動裝置下載、安裝並登入Store Assist應用程式。

- 確認行動裝置符合 [硬體與軟體需求](solution-requirements.md#store-assist-app-requirements) 以取得Store Fulfillment解決方案。

- 從下載「商店協助」應用程式 [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id1609281539){target="_blank"} or the [Google Play store](https://play.google.com/store/apps/details?id=com.walmart.faas.storeassist){target="_blank"}.

- 存放區關聯需要下列資訊才能登入：

   - **[!UICONTROL Company name]** 與Store Assist帳戶相關聯

   - **儲存協助帳戶認證** — 其帳戶的使用者名稱和密碼認證。

  Adobe Commerce管理員可以建立和管理 [!DNL Store Assist app] 具有下列條件的所有商店位置的使用者帳戶： [店內取貨](merchant-store-configuration.md#pickup-location-configuration) 已啟用「 Admin Stores 」設定。
