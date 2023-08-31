---
title: 發行說明
description: Adobe CommerceAdobe Experience Platform聯結器的最新發行資訊。
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
feature: Personalization, Integration, Release Notes
source-git-commit: 4b192fad63ce046bd8f77c513483bf095e249528
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 2%

---

# 發行說明

這些發行說明包含Experience Platform聯結器的更新，並包括：

* ![新增](../assets/new.svg)  — 新功能
* ![修正](../assets/fix.svg)  — 修正和改良
* ![錯誤](../assets/bug.svg)  — 已知問題

有關Experience Platform聯結器所用擴充功能的功能變更和修正，請參閱 **支援的服務更新**.

另請參閱 [即將發行的版本](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) 以瞭解發行排程和支援。

請參閱開發人員檔案以 [瞭解哪些Commerce版本支援此單元](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## 支援的服務更新

以下發行說明說明Experience Platform聯結器使用之擴充功能的相關功能變更和修正。

+++支援的服務更新

_2023年6月10日_

* ![修正](../assets/fix.svg)  — 修正以下問題： `orderId` 由於Commerce訂單識別碼中的前置詞，並未在內容中傳遞。
* ![修正](../assets/fix.svg)  — 更新內容安全性原則設定。

_2023年3月30日_

* ![新增](../assets/new.svg)  — 新增名為的新擴充功能 `data-services-b2b` 其中包括 [請購單清單事件](events.md#b2b-events) 適用於B2B商家。
* ![新增](../assets/new.svg)  — 新增 `uniqueIdentifier` 欄位至 [搜尋](events.md#search-events) 事件。 此新欄位可讓商家交叉參考哪些搜尋要求對應到哪些搜尋回應。

_2022年10月12日_

* ![新增](../assets/new.svg)  — 新增兩個 [店面活動](events.md)： `openCart` 和 `removeFromCart` 前往Adobe Commerce店面事件SDK和收集器。
* ![新增](../assets/new.svg)  — 新增 [AEM店面](overview.md#aem-support).

+++

## 2.3.0

_2023年6月27日_

[!BADGE 支援]{type=Informative tooltip="支援"}

* ![新增](../assets/new.svg)  — 新增以下功能： [關閉傳送店面活動](connect-data.md#data-collection) 到Experience Platform。
* ![修正](../assets/fix.svg)  — 更新內容安全性原則設定。
* ![修正](../assets/fix.svg)  — 修正Commerce 2.4.7版本對後端辦公室事件的支援。
* ![新增](../assets/new.svg)  — 新增在儲存對Experience Platform聯結器表單的變更時，有關快取失效的通知訊息。


## 3.0.0-beta1 （僅限內部）

_2023年6月13日_

[!BADGE 支援]{type=Informative tooltip="支援"}

* ![新增](../assets/new.svg) - （測試版）新增以下功能： [傳送歷史訂單](connect-data.md#beta-send-historical-order-data) Experience Platform的資料和狀態。 此功能僅供測試版使用者使用。 您可以傳送電子郵件至下列地址，以加入Beta版： `dataconnection@adobe.com`.

## 2.2.0

_2023年3月30日_

[!BADGE 支援]{type=Informative tooltip="支援"}

* ![新增](../assets/new.svg)  — 套件式 `commerce-data-export` 和 `saas-export` 的相依性 `experience-platform-connector` 副檔名。 之前，您必須分別安裝這些相依性。 這些相依性及商家設定可讓伺服器端處理 [後台活動](events.md#back-office-events).
* ![新增](../assets/new.svg)  — 已新增名為的新後台事件 [`orderShipmentCompleted`](events.md#ordershipmentcompleted).

## 2.1.1

_2023年2月28日_

[!BADGE 支援]{type=Informative tooltip="支援"}

* ![新增](../assets/new.svg)  — 新增所有Experience Platform聯結器延伸模組對PHP 8.2的支援。

## 2.1.0

_2023年1月17日_

[!BADGE 支援]{type=Informative tooltip="支援"}

* ![新增](../assets/new.svg)  — 已更新 [Experience Platform聯結器管理員](connect-data.md) 以便您指定自己的AEP Web SDK (alloy)。
* ![修正](../assets/fix.svg) 變更為使用 `identityMap` 而非 `personID` 為推送至邊緣的任何資料設定主要身分時。

## 2.0.1

_2022年11月10日_

[!BADGE 支援]{type=Informative tooltip="支援"}

* ![已修正的問題](../assets/fix.svg)  — 現在Adobe Experience Platform內容僅在Storefront事件收集器和店面事件SDK成功載入後設定。

## 2.0.0

_2022年10月12日_

[!BADGE 支援]{type=Informative tooltip="支援"}

* ![新增](../assets/new.svg)  — 新增在下列情況下指定您自己的AEP Web SDK的功能 [正在連線](connect-data.md) 將您的Adobe Commerce例項轉移至Experience Platform。
* ![修正](../assets/fix.svg)  — 更新資料流範圍要求，以便資料流ID的範圍必須限制在網站而非儲存檢閱。

## 1.0.0

_2022年8月9日_

[!BADGE 支援]{type=Informative tooltip="支援"}

* ![新增](../assets/new.svg)  — 正式發行版本。
