---
title: 發行說明
description: Adobe CommerceAdobe Experience Platform連接器的最新發佈資訊。
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
source-git-commit: 22823b662eefa953fcca6ae78f6c37ee8abff3d1
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 1%

---

# 發行說明

本發行說明包含對Experience Platform連接器的更新，並包括：

* ![新建](../assets/new.svg)  — 新功能
* ![修復](../assets/fix.svg)  — 修復和改進
* ![蟲](../assets/bug.svg)  — 已知問題

有關與Experience Platform連接器使用的擴展相關的功能更改和修復，請參見 **支援的服務更新**。

請參閱 [即將發佈的版本](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) 瞭解發行計畫和支援。

請參閱開發人員文檔以 [瞭解產品相容性](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html)。

## 支援的服務更新

本發行說明描述了與Experience Platform連接器使用的擴展相關的功能更改和修復。

+++支援的服務更新

_2023年3月30日_

* ![新建](../assets/new.svg)  — 已添加名為 `data-services-b2b` 包括 [申請清單事件](events.md#b2b-events) B2B商戶
* ![新建](../assets/new.svg)  — 已添加 `uniqueIdentifier` 欄位 [搜索](events.md#search-events) 事件。 此新欄位允許商家交叉引用哪些搜索請求與哪些搜索響應相對應。

_2022年10月12日_

* ![新建](../assets/new.svg)  — 添加2 [儲存事件](events.md): `openCart` 和 `removeFromCart` 到Adobe Commerce店面事件SDK和收集器
* ![新建](../assets/new.svg)  — 為 [AEM店面](overview.md#aem-support)

+++

## 2.2.0

_2023年3月30日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

* ![新建](../assets/new.svg)  — 捆綁 `commerce-data-export` 和 `saas-export` 與 `experience-platform-connector` 擴展。 以前，您必須單獨安裝這些依賴項。 這些依賴項以及商家配置支援伺服器端處理 [後辦公室事件](events.md#back-office-events)。
* ![新建](../assets/new.svg)  — 已添加名為 [`orderShipmentCompleted`](events.md#ordershipmentcompleted)。

## 2.1.1

_2023年2月28日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

* ![新建](../assets/new.svg)  — 為所有Experience Platform連接器模組添加了對PHP 8.2的支援

## 2.1.0

_2023年1月17日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

* ![新建](../assets/new.svg)  — 已更新 [Experience Platform連接器管理](connect-data.md) 這樣您就可以指定自己的AEP Web SDK（合金）。
* ![修復](../assets/fix.svg) 已更改為使用 `identityMap` 而不是 `personID` 為已推送到邊緣的任何資料設定主標識時。

## 2.0.1

_2022年11月10日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

* ![已修復問題](../assets/fix.svg)  — 現在，只有在成功載入Storefront事件收集器和Storefront事件SDK後，才設定Adobe Experience Platform上下文。

## 2.0.0

_2022年10月12日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

* ![新建](../assets/new.svg)  — 增加了指定您自己的AEP Web SDK的功能 [連接](connect-data.md) 你對Adobe Commerce案的Experience Platform
* ![修復](../assets/fix.svg)  — 更新了資料流範圍要求，以便資料流ID必須限定到網站，而不是儲存視圖

## 1.0.0

_2022年8月9日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

* ![新建](../assets/new.svg)  — 一般可用性版本
