---
title: 應用程式設定
description: '"設定 [!DNL Store Assist] app管理端到端商店履行工作流和線上購買流程，在商店訂單中提貨。」 '
role: User, Admin
level: Intermediate
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# 應用程式設定

Store Assist是由Walmart Commerce Technologies支援的「按服務完成」(FaaS)平台應用。 該應用提供了店內履行功能以處理 [!DNL buy online]。 [!DNL pick up in store] (BOPIS)訂單。

該應用接收所有訂單和客戶資訊 — 從訂單詳細資訊到提貨時間 — 並通過移動設備線上儲存關聯資訊。 使用Store Assist ，儲存關聯可以查看客戶訂購的物料、更快地挑選正確的物料，以及設定已履行訂單以在商店內或在路邊向客戶提貨。

儲存關聯使用儲存協助 [!UICONTROL Pick]。 [!UICONTROL Stage]。 [!UICONTROL Handoff], [!UICONTROL Orders] 完成以下管理交付和切換過程：

- 分配訂單交貨日期和時間
- 在客戶到達商店時獲取訂單提貨通知
- 階段訂單以切換至客戶
- 跟蹤其分配的儲存位置中所有訂單的訂單狀態

請參閱 [儲存協助履行工作流](store-assist-modules.md) 瞭解有關Store Assist應用的詳細資訊。


## 配置Store Assist應用

Store Assist應用需要兩種配置：

- Adobe Commerce管理員配置設定 [從Adobe Commerce管理系統設定管理用戶帳戶、用戶角色和資源權限](user-setup.md)。

- 前端配置設定可自定義Store Assist應用介面和其他設定，包括：

   - **將應用商店幫助應用品牌化** — 使用公司徽標和顏色自定義應用程式用戶介面

   - **更新預設說明** — 為挑庫、階段、切換和訂單模組定制在「儲存協助」介面中顯示的說明，以便您的聯繫人確切知道在完成流程的每個步驟中要執行什麼操作。

   - **本地化** — 為應用選擇可用語言，選擇日期和時間格式，選擇預設度量單位，選擇預設貨幣

   - **不活動時間** — 指定應用程式在註銷之前必須處於非活動狀態的時間

   - **從商店取消** — 指定是否可以從儲存中取消訂單以及哪些角色具有取消權限

   - **訂單清理窗口** — 指定在重新貯存之前已挑庫訂單在轉移中的計畫裝貨時間（例如，三天）的過去時間。

   - 在應用說明中自定義所有內容（領料、轉移、轉移）

   - **領料通知** — 如果希望推送通知在下訂單後開始挑庫，則設定

   - **簽入通知** — 如果希望在客戶簽入/等待X分鐘/或根本沒有通知後有推送通知，則設定

   - **切換過程** — 啟用客戶簽名，在交出訂單前提示檢查客戶ID

   - **在切換時啟用項目拒絕**

   與Walmart Commerce Technologies客戶服務團隊合作，為Store Assist應用完成Frontend配置。

## 應用下載和安裝

完成Store Assist應用程式配置後，Store Associates可以在其移動設備上下載並安裝Store Assist應用程式並登錄。

- 從下載Store Assist應用 [AppleApp Store](https://apps.apple.com/us/app/store-assist-by-walmart/id16092815390) 或者Google Play店。

- 儲存關聯需要以下資訊才能登錄：

   - 與您的Store Assist帳戶關聯的公司名稱

   - 儲存Assist帳戶憑據 — 其帳戶的用戶名和密碼憑據。
   Adobe Commerce管理員可以為具有 [店內裝貨](merchant-store-configuration.md#pickup-location-configuration) 在「管理儲存」設定中啟用。

