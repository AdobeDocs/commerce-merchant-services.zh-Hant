---
title: 上傳購物者設定檔至Adobe Experience Platform
description: 了解如何將購物者設定檔上傳至Adobe Experience Platform。
exl-id: fd0ee7fa-5274-4640-ba00-bcb2ec78f314
source-git-commit: 9bf28159fdac3a7237956a536f6a522b4e2918fe
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# 將購物者設定檔上傳至Adobe Experience Platform

Adobe Commerce商家可將客戶設定檔資料上傳至 [即時客戶個人檔案](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html)，屬於Adobe Experience Platform。 設定檔可讓您將客戶資料併入統一檢視中，為每個客戶互動提供可操作且具時間戳記的帳戶。

>[!NOTE]
>
> 描述檔資料必須包含電子郵件地址，因為這是建立購物者與其店面行為資料之間連結的方式。

上傳購物者的設定檔後，與購物者在您網站上進行的任何互動相關聯的事件資料會透過Experience Platform連接器傳送至設定檔，並連結至該購物者的設定檔。

>[!NOTE]
>
> 此 `createAccount` [店面事件](events.md) 不會自動在「設定檔」中建立客戶設定檔。 出於安全原因，這是有意的。

在本主題中，您將學習如何以Experience Platform將Adobe Commerce客戶設定檔上傳至即時客戶設定檔。

1. 決定客戶資料的儲存位置。 對於某些商戶，此資料會儲存在Adobe Commerce中，並可 [匯出](https://docs.magento.com/user-guide/system/data-export.html) 檔案。 對於其他客戶，則可能位於個別的客戶關係管理(CRM)系統中。

1. 決定客戶資料的儲存位置後，請尋找適當的 [來源連接器](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html) 根據客戶資料的儲存位置。 如果您沒有看到適當的源連接器，請使用 [本機檔案上傳](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/local-system/local-file-upload.html) 連接器，並從CSV檔案匯入您的購物者設定檔。

   >[!NOTE]
   >
   > 如果您使用本機檔案上傳連接器，則必須啟用 **設定檔資料集** 選項 [定義資料集](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/local-system/local-file-upload.html#use-an-existing-dataset). 這會將資料集識別為設定檔資料。

在您於描述檔中建立購物者描述檔後，與該購物者相關聯的所有店面資料都會連結至其描述檔。

## 經常上傳設定檔

為確保增強的購物者體驗，您應定期匯入設定檔資料。 有些來源連接器可讓您依排程匯入設定檔資料。
