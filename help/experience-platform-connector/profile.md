---
title: 將購物者個人資料上載到Adobe Experience Platform
description: 瞭解如何將購物者資料上傳到Adobe Experience Platform。
source-git-commit: 93133019f8004437ef85db32ff336bfd0e8c6fc2
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# 將購物者個人資料上載到Adobe Experience Platform

Adobe Commerce商戶可以將客戶概要資料上傳到 [即時客戶配置檔案](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html)屬於Adobe Experience Platform。 配置檔案允許您將客戶資料整合到一個統一視圖中，為每個客戶交互提供一個可操作且時間戳記的帳戶。

>[!NOTE]
>
> 個人資料資料必須包括電子郵件地址，因為這就是如何建立購物者與其店面行為資料之間的連結。

在您上傳購物者的個人資料後，與購物者在網站上進行的任何互動相關聯的事件資料會通過Experience Platform連接器發送到個人資料並連結到該購物者的個人資料。

>[!NOTE]
>
> 的 `createAccount` [storefront事件](events.md) 不會在配置檔案中自動建立客戶配置檔案。 出於安全原因，這是故意的。

在本主題中，您將學習如何在Experience Platform中將您的Adobe Commerce客戶配置檔案上載到即時客戶配置檔案。

1. 確定您儲存客戶資料的位置。 對於一些商戶，這些資料儲存在Adobe Commerce [導出](https://docs.magento.com/user-guide/system/data-export.html) 檔案。 對於其他客戶，它可能位於單獨的客戶關係管理(CRM)系統中。

1. 在確定儲存客戶資料的位置後，找到相應的 [源連接器](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=en) 根據客戶資料的儲存位置。 如果未看到相應的源連接器，則使用 [本地檔案上載](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/local-system/local-file-upload.html) 連接器，並從CSV檔案導入購物者配置檔案。

   >[!NOTE]
   >
   > 如果使用本地檔案上載連接器，則必須啟用 **配置檔案資料集** 選項 [定義資料集](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/local-system/local-file-upload.html#use-an-existing-dataset)。 這將資料集標識為配置檔案資料。

在Profile中建立購物者配置檔案後，與該購物者關聯的所有店面資料都將連結到他們的配置檔案。

## 頻繁上載配置檔案

為確保顧客體驗的增強，您應定期導入個人資料資料。 某些源連接器允許您按計畫導入配置檔案資料。
