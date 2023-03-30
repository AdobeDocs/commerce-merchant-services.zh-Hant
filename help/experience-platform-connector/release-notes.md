---
title: 發行說明
description: 來自Adobe Commerce的Adobe Experience Platform連接器最新發行資訊。
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
source-git-commit: 735fd14fad22826b04320644e120d296de19a211
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 1%

---

# 發行說明

以下版本說明包含Experience Platform連接器的更新，並包含：

* ![新增](../assets/new.svg)  — 新功能
* ![修正](../assets/fix.svg)  — 修正和改良
* ![錯誤](../assets/bug.svg)  — 已知問題

如需與Experience Platform連接器所使用擴充功能相關的功能變更和修正，請參閱 **支援的服務更新**.

請參閱 [即將發行的版本](https://experienceleague.adobe.com/docs/commerce-operations/release/schedule.html) 了解發行計畫和支援。

請參閱開發人員檔案，以 [了解產品相容性](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## 支援的服務更新

以下版本說明說明與Experience Platform連接器使用的擴充功能相關的功能變更和修正。

+++支援的服務更新

_2023年3月30日_

* ![新增](../assets/new.svg)  — 新增新的擴充功能，稱為 `data-services-b2b` 包括 [申請清單事件](events.md#b2b-events) 針對B2B商戶
* ![新增](../assets/new.svg)  — 新增 `uniqueIdentifier` 欄位至 [搜尋](events.md#search-events) 事件。 此新欄位可讓商家交叉參考哪些搜尋請求與哪些搜尋回應相對應。

_2022年10月12日_

* ![新增](../assets/new.svg)  — 新增兩個 [storefront事件](events.md): `openCart` 和 `removeFromCart` 至Adobe Commerce Storefront事件SDK和收集器
* ![新增](../assets/new.svg)  — 新增對 [AEM storefront](overview.md#aem-support)

+++

## 2.2.0

_2023年3月30日_

* ![新增](../assets/new.svg)  — 捆綁 `commerce-data-export` 和 `saas-export` 相依性 `experience-platform-connector` 擴充功能。 之前，您必須個別安裝這些相依性。 這些相依性以及商戶配置可讓伺服器端處理 [後台事件](events.md#back-office-events).
* ![新增](../assets/new.svg)  — 新增名為 [`orderShipmentCompleted`](events.md#ordershipmentcompleted).

## 2.1.1

_2023年2月28日_

* ![新增](../assets/new.svg)  — 新增對PHP 8.2的支援，用於所有Experience Platform連接器模組

## 2.1.0

_2023年1月17日_

* ![新增](../assets/new.svg)  — 更新 [Experience Platform連接器管理員](connect-data.md) 以便您能指定自己的AEP Web SDK(alloy)。 此外，新增可讓已註冊後台測試版計畫的商家傳送 [後台事件資料](connect-data.md#data-collection) 到邊緣。 這些事件包含 [訂單狀態資訊](events.md#beta-order-status-events) 訂單，例如訂單被下放、取消、退貨或發運。
* ![修正](../assets/fix.svg) 變更為使用 `identityMap` 而非 `personID` 設定推送至邊緣之任何資料的主要身分時。

## 2.0.1

_2022年11月10日_

* ![修正問題](../assets/fix.svg)  — 現在，Adobe Experience Platform內容僅在成功載入「Storefront事件收集器」和「Storefront事件SDK」後設定。

## 2.0.0

_2022年10月12日_

* ![新增](../assets/new.svg)  — 新增在 [連接](connect-data.md) 您的Adobe Commerce例項至Experience Platform
* ![修正](../assets/fix.svg)  — 更新資料流範圍要求，讓資料流ID必須限定在網站的範圍，而非儲存檢視

## 1.0.0

_2022年8月9日_

* ![新增](../assets/new.svg)  — 正式發行

## 檔案

若要深入了解：

* [Adobe Commerce開發人員檔案](https://devdocs.magento.com/)
* [Adobe Commerce使用手冊](https://docs.magento.com/user-guide/)
