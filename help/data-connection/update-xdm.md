---
title: 更新Commerce資料擷取的時間序列事件結構
description: 瞭解如何建立結構、資料集和資料串流，以收集和傳送用於Commerce資料擷取的時間序列事件資料。
exl-id: 4401bbe7-1ccc-4349-a998-9e9ee9db590f
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: d5824e11b4961b518e35fcf56ff2c7ee00480617
workflow-type: tm+mt
source-wordcount: '997'
ht-degree: 0%

---

# 更新Commerce資料擷取的時間序列事件結構

其中一項 [入門步驟](overview.md#onboarding-steps) 若使用 [!DNL Data Connection] 擴充功能是存取資料流工作區並 [建立資料串流](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) 特定於Adobe Commerce的資訊。 當您建立該資料流時，也必須選取描述您計畫擷取之資料的結構描述。 該結構描述必須包含商務特定欄位群組。

本文提供結構描述必須包含的欄位群組，才能成功收集Adobe Commerce事件提供的下列時間序列資料：

- [行為](events.md)  — 包括店面、設定檔、搜尋和B2B事件。
- [後台](events-backoffice.md)  — 包含訂單狀態和設定檔事件。

進一步瞭解 [時間序列資料](data-ingestion.md).

進一步瞭解 [結構描述組合的基本面](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html).

## 使用時間序列行為和後台事件資料更新結構描述

在本節中，您將瞭解如何更新現有的結構描述或建立結構描述，以包含行為和後台事件資料。

>[!NOTE]
>
>另請參閱 [時間序列設定檔事件資料](#time-series-profile-event-data) 以瞭解如何新增設定檔特定欄位。

1. 如果您還沒有結構描述， [建立](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) 類別設定為 **體驗事件**.

1. [新增](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) 以下特定於Commerce的欄位群組（或編輯現有結構並新增這些欄位群組）：

   - 網站搜尋
   - 造訪網頁
   - 使用者登入程式
   - 參考索引鍵
   - 個人聯絡詳細資訊
   - 管道詳細資料
   - 商業細節
   - Adobe Analytics ExperienceEvent Commerce (如果您想要傳送資料給Adobe Analytics)

   >[!NOTE]
   >
   > 請勿將任何Commerce專用欄位群組設為 `Primary identity`. 這樣做會將欄位識別為必填欄位，而Experience Platform會在每個事件中預期該欄位。 如果此欄位不存在，資料擷取會失敗。

   您的結構描述現在包含Commerce專用欄位群組，以便從Commerce收集的時間序列資料 [行為](events.md) 和 [後台](events-backoffice.md) 事件會在結構描述中呈現。

1. [啟用](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#profile) 設定檔的結構描述。

   為設定檔啟用結構描述時，從此結構描述建立的任何資料集都會參與Real-Time CDP，其會合併來自不同來源的資料，以建構每個客戶的完整檢視。

1. [建立資料集](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) 根據您建立或更新的結構描述。

   資料集是資料集合的儲存和管理結構，通常是包含結構（欄）和欄位（列）的表格。 資料集也包含中繼資料，可說明其儲存資料的各個層面。

1. [建立資料串流](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) 並選取包含Commerce特定欄位群組和對應資料集的結構描述。

   資料流會將收集的資料轉送至資料集。 資料會根據所選的結構描述顯示在資料集中。

1. **測試版** （選用）如果您想要將自訂後台事件資料從您的商務執行個體傳遞至Experience Platform，則可以使用自訂屬性。 此功能為測試版。 如果您想要加入Beta版計畫，請傳送要求至 [dataconnection@adobe.com](mailto:dataconnection@adobe.com). 在您的請求中，加入下列專案：

   - 您的 [Adobe組織ID](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255). 例如 `organization_id@AdobeOrg`.
   - Order層級自訂屬性的清單。
   - 「訂單料號」層次屬性清單。

   Adobe Commerce團隊將與您聯絡以取得更多資訊和後續步驟。

為行為和後台資料設定的結構描述、資料集和資料流可以 [設定](connect-data.md#data-collection) 您的Commerce執行個體，以收集該資料並傳送給Experience Platform。

若要包含購物者的設定檔資訊，請參閱下一節。

## 時間序列設定檔事件資料

>[!NOTE]
>
>此功能為測試版。 如果您想要加入Beta版計畫，請傳送要求至 [dataconnection@adobe.com](mailto:dataconnection@adobe.com).

時間序列設定檔事件資料產生自下列事件：

- [&#39;accountCreated&#39;](events-backoffice.md#accountcreated)
- [&#39;帳戶已更新&#39;](events-backoffice.md#accountupdated)
- [&#39;帳戶已刪除&#39;](events-backoffice.md#accountdeleted)

如果您想要將客戶的設定檔事件資料擷取至Experience Platform，您可以更新現有的Commerce結構描述，並使用已設定的相同資料流，或者您可以建立設定檔特定的資料流和結構描述。 該決定取決於您公司的資料控管。 接下來的兩個區段將引導您瞭解這兩種情況。

### 使用您現有的資料流將時間序列設定檔事件資料傳送至Experience Platform

如果您想要新增時間序列 [伺服器端設定檔事件資料](events-backoffice.md#customer-profile-events-server-side) 將新增至您現有的Commerce資料流 `Demographic Details` 欄位群組至您的結構描述。 您的結構描述現在包含下列商務專用欄位群組：

- 網站搜尋
- 造訪網頁
- 使用者登入程式
- 參考索引鍵
- 個人聯絡詳細資訊
- 管道詳細資料
- 商業細節
- Adobe Analytics ExperienceEvent Commerce (如果您想要傳送資料給Adobe Analytics)
- 新增： **人口統計細節**

新增 `Demographic Details` 欄位群組，則已與您商務結構描述相關聯的資料集和資料流會用於此時間序列設定檔資料。

### 傳送時間序列設定檔事件資料至個別資料流中的Experience Platform

如果您想要新增 [伺服器端設定檔事件資料](events-backoffice.md#customer-profile-events-server-side) 至新的設定檔特定資料流和結構描述，請完成以下步驟。

1. [建立](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) 結構描述並將類別設定為 **體驗事件**.

1. [新增](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) 下列設定檔特定欄位群組：

   - 人口統計細節
   - 個人聯絡詳細資訊
   - 管道詳細資料
   - 商業細節

1. [啟用](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#profile) 設定檔的結構描述。

   為設定檔啟用結構描述時，從此結構描述建立的任何資料集都會參與Real-Time CDP，其會合併來自不同來源的資料，以建構每個客戶的完整檢視。

1. [建立資料集](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) 根據您建立的結構描述。

   資料集是資料集合的儲存和管理結構，通常是包含結構（欄）和欄位（列）的表格。 資料集也包含中繼資料，可說明其儲存資料的各個層面。

1. [建立資料串流](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) 並選取包含商務特定欄位群組和對應資料集的XDM結構描述。

   資料流會將收集的資料轉送至資料集。 資料會根據所選的結構描述顯示在資料集中。

針對客戶設定檔資料設定的結構描述、資料集和資料串流可以 [設定](connect-data.md#data-collection) 您的Commerce執行個體，以收集該資料並傳送給Experience Platform。

若要為設定檔記錄資料建立結構描述、資料集和資料流，請參閱 [將設定檔記錄資料傳送至Experience Platform](profile-data.md).
