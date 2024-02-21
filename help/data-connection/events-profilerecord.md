---
title: 設定檔記錄
description: 瞭解設定檔記錄擷取哪些資料。
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: 655b5d18a4fb77232523c9c18a9fb362de93c70a
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# [!DNL Data Connection] 設定檔記錄(Beta)

>[!NOTE]
>
>此功能為測試版。 如果您想要加入Beta版計畫，請傳送要求至 [dataconnection@adobe.com](mailto:dataconnection@adobe.com).

以下說明安裝時可用的Commerce設定檔記錄資料 [!DNL Data Connection] 副檔名。 設定檔記錄中的資料會傳送至Adobe Experience Platform。

## 設定檔記錄

建立、更新或刪除新設定檔時，Experience Platform中會提供設定檔記錄更新。

### 從設定檔記錄收集的資料

以下說明為設定檔記錄擷取的資料。

| 欄位 | 說明 |
|---|---|
| `channel` | 包含資料來源的相關資訊。 兩者 `_id` 和 `_type` contain [名稱空間值](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | 管道的唯一識別碼，例如 `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | 識別管道資料的來源，例如 `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `person` | 包含有關客戶的資訊。 |
| `person.name` | 包含客戶名稱的相關資訊。 |
| `person.name.firstName` | 包含客戶的名字。 |
| `person.name.lastName` | 包含客戶的姓氏。 |
| `person.birthDate` | 購物者的出生日期。 |
| `personalEmail` | 個人電子郵件地址。 |
| `personalEmail.address` | 技術地址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義。 |
| `userAccount` | 表示任何熟客方案細節、偏好設定、登入流程和其他帳戶偏好設定。 |
| `userAccount.startDate` | 首次建立設定檔的日期。 |

>[!NOTE]
>
>每個設定檔記錄也包含 [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) 欄位，其中包含購物者的電子郵件地址（若有）和ECID。

瞭解如何 [建立設定檔記錄專屬的結構描述](profile-data.md) 可以從您的設定檔記錄中擷取資料。
