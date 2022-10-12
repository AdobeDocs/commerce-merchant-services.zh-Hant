---
title: 新增欄位群組至XDM結構
description: 了解如何將Adobe Commerce專用欄位群組新增至XDM結構。
exl-id: 4401bbe7-1ccc-4349-a998-9e9ee9db590f
source-git-commit: f5d1c39fe1b02d2a661b92f971fba5b3e836dd6a
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# 新增欄位群組至XDM結構

其中 [入門步驟](overview.md#onboarding-steps) 使用「Experience Platform」連接器是存取datastream workspace和 [建立資料流](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) 是Adobe Commerce專屬的。 建立該資料流時，您也必須選取代表您計畫內嵌資料的XDM架構。 本主題提供您XDM結構必須包含的欄位群組，才能成功收集Adobe Commerce storefront提供的資料 [事件](events.md).

1. 如果您尚未建立XDM架構， [建立](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) 一個。 否則， [編輯](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#edit) Adobe Experience Platform UI中現有的XDM結構。

1. [新增](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) 下列特定於商務的欄位組：

   - 網站搜尋
   - 瀏覽網頁
   - 用戶登錄過程
   - 參考索引鍵
   - 個人聯繫人詳細資訊
   - 商務詳細資訊
   - Adobe Analytics體驗事件商務(如果您想要將資料傳送至Adobe Analytics)
   - 人員識別碼

   >[!NOTE]
   >
   > 請勿將任何特定於商務的欄位群組設為 `Primary identity`. 這樣會視需要識別欄位，而Experience Platform會在每個事件中預期該欄位。 如果該欄位不存在，資料擷取會失敗。

   您的XDM結構現在包含商務專用欄位群組，以便從商務店面收集資料 [事件](events.md) 在XDM中表示。

1. [建立資料流](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) 並選取包含「商務」專用欄位群組的XDM結構。
