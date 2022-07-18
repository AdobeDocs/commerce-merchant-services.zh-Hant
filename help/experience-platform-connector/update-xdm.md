---
title: 將欄位組添加到XDM架構
description: 瞭解如何將特定於Adobe Commerce的欄位組添加到XDM架構。
source-git-commit: 4d6a4cec81dbb1e71718066be2ba13a4d292aea3
workflow-type: tm+mt
source-wordcount: '0'
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

   您的XDM架構現在包含特定於Commerce的欄位組，以便從Commerce儲存區收集到的資料 [事件](events.md) 在XDM中表示。
1. 你現在應該 [建立資料流](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en) 並選擇包含特定於Commerce的欄位組的XDM架構。
