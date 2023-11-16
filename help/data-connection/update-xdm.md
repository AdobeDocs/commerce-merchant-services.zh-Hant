---
title: 新增欄位群組至XDM結構描述
description: 瞭解如何將Adobe Commerce特定的欄位群組新增到XDM結構描述。
exl-id: 4401bbe7-1ccc-4349-a998-9e9ee9db590f
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 4a5877d6e1a5c7d840e36f4913306b0c440bbac5
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# 新增欄位群組至XDM結構描述

其中一項 [入門步驟](overview.md#onboarding-steps) 若使用 [!DNL Data Connection] 擴充功能是存取資料流工作區並 [建立資料串流](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) 特定於Adobe Commerce的資訊。 當您建立該資料流時，還必須選取代表您計畫擷取之資料的XDM結構描述。 本主題提供您的XDM結構描述必須包含的欄位群組，才能成功收集Adobe Commerce提供的資料 [事件](events.md).

1. 如果您還沒有XDM結構描述， [建立](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) 一。 否則， [編輯](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#edit) Adobe Experience Platform UI中現有的XDM結構描述。

1. [新增](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) 以下特定於Commerce的欄位群組：

   - 網站搜尋
   - 造訪網頁
   - 使用者登入程式
   - 參考索引鍵
   - 個人聯絡詳細資訊
   - 商業細節
   - Adobe Analytics ExperienceEvent Commerce (如果您想要傳送資料給Adobe Analytics)
   - 身分對應

   >[!NOTE]
   >
   > 請勿將任何Commerce專用欄位群組設為 `Primary identity`. 這樣做會將欄位識別為必填欄位，而Experience Platform會在每個事件中預期該欄位。 如果此欄位不存在，資料擷取會失敗。

   您的XDM結構描述現在包含Commerce專用欄位群組，以便從Commerce收集的資料 [事件](events.md) 在XDM中呈現。

1. [建立資料集](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) 根據您建立或更新的結構描述。

   資料集是資料集合的儲存和管理結構，通常是包含方案（欄）和欄位（列）的表格。 資料集也包含中繼資料，可說明其儲存資料的各個層面。

1. [建立資料串流](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) 並選取包含商務特定欄位群組和對應資料集的XDM結構描述。

   資料流會將收集的資料轉送至資料集。 資料會根據所選的結構描述顯示在資料集中。
