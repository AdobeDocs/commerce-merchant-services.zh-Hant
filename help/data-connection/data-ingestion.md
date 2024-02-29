---
title: 商務資料型別
description: 瞭解您可以收集並傳送給Experience Platform的資料型別。
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 99d1097b98ea18c8a317613b2366a97db131432f
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# 商務資料型別

此 [資料連線擴充功能](overview.md) 將您的Commerce資料連線到Experience Platform。 打算用於Experience Platform的資料分為兩種行為型別：時間序列資料，屬於 **體驗事件** 類別並記錄屬於下列專案的資料： **個別設定檔** 類別。

進一步瞭解 [資料行為](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#data-behaviors) 和 [類別](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#class) 在Experience Platform中。

## 時間序列資料

時間序列資料提供記錄主體直接或間接執行動作時的系統快照。 例如，當購物者瀏覽您網站上的產品時、新增產品至購物車、下訂單等等。 使用類別設定為的結構描述將時間序列資料擷取到Experience Platform中 **體驗事件**.

### 已擷取的時間序列資料

另請參閱 [行為事件](events.md) 和 [後台活動](events-backoffice.md) 以瞭解在產生時間序列事件時擷取了哪些資料。

### 擷取時間序列事件資料所需的結構描述

瞭解如何 [建立結構描述](update-xdm.md) 可以擷取行為和後台時間序列事件資料。

## 記錄資料

記錄資料提供有關主旨屬性的資訊。 主旨可以是組織或個人。 例如，您網站上的購物者會建立帳戶，並產生記錄資料。 系統會使用類別設定為的結構描述，將此資料擷取到Experience Platform中 **個別設定檔**. 您可以將該記錄資料傳送至Adobe的設定檔管理和細分服務： [Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/intro/rtcdp-intro/overview.html?lang=zh-Hant).

### 已擷取的設定檔記錄資料

另請參閱 [客戶設定檔記錄資料](events-profilerecord.md) 以瞭解在產生設定檔記錄時擷取哪些資料。

### 擷取設定檔記錄資料所需的結構描述

瞭解如何 [建立結構描述](profile-data.md) 可以內嵌設定檔記錄資料的伺服器。
