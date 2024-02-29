---
title: 更新Commerce資料擷取的設定檔記錄結構
description: 瞭解如何建立結構、資料集和資料串流，以收集並傳送Commerce設定檔記錄資料給Experience Platform。
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 99d1097b98ea18c8a317613b2366a97db131432f
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# 更新Commerce資料擷取的設定檔記錄結構

當您的購物者在您的Commerce網站中建立設定檔時，會建立設定檔記錄並擷取資料。 您必須先建立該設定檔記錄專屬的結構描述和資料集，才能將該設定檔資料串流至Experience Platform。

1. [建立](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) 結構描述並將類別設定為 **個別設定檔**.

1. [新增](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) 下列設定檔特定欄位群組：

   - identityMap
   - 人口統計細節
   - 個人聯絡詳細資訊
   - 使用者帳戶詳細資訊

1. [啟用](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#profile) 設定檔的結構描述。

   為設定檔啟用結構描述時，從此結構描述建立的任何資料集都會參與Real-Time CDP，其會合併來自不同來源的資料，以建構每個客戶的完整檢視。

1. [建立資料集](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) 根據您建立或更新的結構描述。

   資料集是資料集合的儲存和管理結構，通常是包含結構（欄）和欄位（列）的表格。 資料集也包含中繼資料，可說明其儲存資料的各個層面。

針對客戶設定檔記錄資料設定的結構和資料集能協助您 [設定](connect-data.md#data-collection) 您的Commerce執行個體，以收集該資料並傳送給Experience Platform。

若要為行為和後台事件資料建立結構、資料集和資料流，請參閱 [更新Commerce資料擷取的時間序列事件結構](update-xdm.md).
