---
title: 將欄位組添加到XDM架構
description: 瞭解如何將特定於Adobe Commerce的欄位組添加到XDM架構。
exl-id: 4401bbe7-1ccc-4349-a998-9e9ee9db590f
source-git-commit: 06499893f6cad4d920a231f5b22417d3044b2319
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# 將欄位組添加到XDM架構

其中 [先決條件](overview.md#prereqs) 使用Experience Platform連接器是訪問資料流工作區和 [建立資料流](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en) 是專門針對Adobe Commerce的。 建立該資料流時，還必須選擇一個XDM架構，該架構表示您計畫接收的資料。 本主題提供了XDM架構必須包括的欄位組，以成功收集Adobe Commerce店面提供的資料 [事件](events.md)。

1. 如果尚沒有XDM架構， [建立](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=en#create) 一個。 否則， [編輯](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=en#edit) 您在Adobe Experience PlatformUI中的現有XDM架構。

1. [添加](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=en#add-field-groups) 以下特定於Commerce的欄位組：

   - 商業
   - 站點搜索
   - 訪問網頁
   - 用戶登錄過程
   - 引用鍵
   - 個人聯繫人詳細資訊
   - 商業詳細資訊
   - Adobe Analytics體驗活動商務(如果您要向Adobe Analytics發送資料)
   - 人員標識符

   >[!NOTE]
   >
   > 不將任何特定於Commerce的欄位組設定為 `Primary identity`。 這樣可將欄位標識為必需欄位，Experience Platform在每個事件中都希望該欄位。 如果該欄位不存在，則資料接收失敗。

   您的XDM架構現在包含特定於Commerce的欄位組，以便從Commerce儲存區收集到的資料 [事件](events.md) 在XDM中表示。

1. [建立資料流](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) 並選擇包含特定於Commerce的欄位組的XDM架構。
