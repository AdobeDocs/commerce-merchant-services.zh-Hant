---
title: 發行說明
description: 的最新版本資訊 [!DNL Data Connection] 來自Adobe Commerce的擴充功能。
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
feature: Personalization, Integration, Release Notes
source-git-commit: d54b7e894df4e6f64607afcfc6754b5a560b91e2
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 0%

---

# 發行說明

>[!IMPORTANT]
>
>Experience Platform聯結器已重新命名為 [!DNL Data Connection].

本發行說明包含 [!DNL Data Connection] 擴充功能並包含：

![新增](../assets/new.svg)  — 新功能
![修正](../assets/fix.svg)  — 修正和改良
![錯誤](../assets/bug.svg)  — 已知問題

有關使用的擴充功能的功能變更和修正， [!DNL Data Connection] 擴充功能，請參閱 **支援的服務更新**.

另請參閱 [即將發行的版本](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) 以瞭解發行排程和支援。

請參閱開發人員檔案以 [瞭解哪些Commerce版本支援此單元](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## 支援的服務更新

以下發行說明說明說明使用的擴充功能相關功能變更和修正 [!DNL Data Connection] 副檔名。

+++支援的服務更新

_2024年1月24日_

![新增](../assets/new.svg)  — 已更新 `data-services-b2b` 擴充功能，以包含名為的新請購單事件 [deleteRequisitionList](events.md#deleterequisitionlist) 適用於B2B商家。

_2023年11月16日_

![修正](../assets/fix.svg)  — 修正您下有多重送貨地址的訂單時，錯誤訊息不正確顯示的問題。
![修正](../assets/fix.svg)  — 修正 [productPageView](events.md#productpageview) 事件，其中 `productListItems.priceTotal` 在商店檢視上切換貨幣後，事件欄位未轉換價格。
![修正](../assets/fix.svg)  — 修正 `productListItems` 商戶切換商店檢視時，貨幣代碼未更新的事件欄位。

_2023年10月10日_

![新增](../assets/new.svg)  — 新增訂單狀態事件： [已開立商業發票的訂單](events-backoffice.md#orderinvoiced)， [已起始訂單料號退貨](events.md#orderitemsreturninitiated)、和 [訂單專案退貨已完成](events.md#orderitemreturncompleted).
![修正](../assets/fix.svg)  — 修正重新整理快取後，貨幣設定變更未反映在事件中的問題。
![修正](../assets/fix.svg)  — 修正啟用非同步下單時未顯示訂單確認訊息的錯誤。
![新增](../assets/new.svg)  — 新增資料至 [addToRequisitionList](events.md#addtorequisitionlist) 類別檢視頁面上的簡單產品事件。
![修正](../assets/fix.svg)  — 修正 `selectedOptions` 中的資料 [addToRequisitionList](events.md#addtorequisitionlist) 從訂購確認頁面新增產品時的事件。
![新增](../assets/new.svg)  — 已將產品資料新增至 [addToRequisitionList](events.md#addtorequisitionlist) 從「類別」檢視頁面將產品新增至請購單清單時的事件。
![新增](../assets/new.svg)  — 已新增 [addToRequisitionList](events.md#addtorequisitionlist) 從「產品檢視」頁面將可設定產品新增至請購單清單時的事件。
![新增](../assets/new.svg)  — 已新增 [addToRequisitionList](events.md#addtorequisitionlist) 和 [removeFromRequisitionList](events.md#removefromrequisitionlist) 當產品數量從請購單清單增加及/或減少時的事件。

_2023年6月10日_

![修正](../assets/fix.svg)  — 修正以下問題： `orderId` 由於商務訂單識別碼中的前置詞，內容中未傳遞。
![修正](../assets/fix.svg)  — 更新內容安全性原則設定。

_2023年3月30日_

![新增](../assets/new.svg)  — 新增擴充功能，稱為 `data-services-b2b` 其中包括 [請購單清單事件](events.md#b2b-events) 適用於B2B商家。
![新增](../assets/new.svg)  — 新增 `uniqueIdentifier` 欄位至 [搜尋](events.md#search-events) 事件。 此新欄位可讓商家交叉參考搜尋要求與搜尋回應。

_2022年10月12日_

![新增](../assets/new.svg)  — 新增兩個 [店面活動](events.md)， `openCart` 和 `removeFromCart`，前往Adobe Commerce店面事件SDK和收集器。
![新增](../assets/new.svg)  — 新增 [AEM店面](overview.md#aem-support).

+++

## 3.2.0-beta1

_2024年2月16日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg)  — 如果您正在參與Beta版測試，請確定您的 `composer.json` 檔案的根層級如下： ` "minimum-stability": "beta"`.
![新增](../assets/new.svg)  — 新增以下功能： [新增自訂屬性](update-xdm.md#update-schema-with-time-series-behavioral-and-back-office-event-data).
![新增](../assets/new.svg)  — 新增以下功能： [收集和傳送設定檔記錄](connect-data.md#send-customer-profile-data) 和資料進行Experience Platform。

## 3.1.0

_2023年11月16日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

![新增](../assets/new.svg) -Experience Platform聯結器已重新命名為 [!DNL Data Connection].
![修正](../assets/new.svg)  — 新增在Adobe IMS無法產生存取權杖時記錄錯誤回應的功能。
![修正](../assets/new.svg)  — 如果您嘗試同步處理歷史訂單，但尚未指定帳戶認證，則新增通知訊息。

## 3.0.0

_2023年10月10日_

[!BADGE 相容性]{type=Informative tooltip="相容性"}

此為主要版本發行版本。 [編輯](install.md#update-the-data-connection) 您專案的根composer.json檔案。

![新增](../assets/new.svg)  — 正式發行 [傳送歷史訂單](connect-data.md#send-historical-order-data) Experience Platform的資料和狀態。
![新增](../assets/new.svg)  — 新增當您使用OAuth 2.0時 [設定](connect-data.md#connect-commerce-data-to-adobe-experience-platform) 此 [!DNL Data Connection] 副檔名。
![新增](../assets/new.svg)  — 終止支援Adobe Commerce 2.4.3。

## 2.3.0

_2023年6月27日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg)  — 新增以下功能： [關閉傳送店面活動](connect-data.md#data-collection) 到Experience Platform。
![修正](../assets/fix.svg)  — 更新內容安全性原則設定。
![修正](../assets/fix.svg)  — 修正Commerce 2.4.7版本對後端辦公室事件的支援。
![新增](../assets/new.svg)  — 新增將變更儲存至時快取失效的通知訊息 [!DNL Data Connection] 擴充功能表單。


## 3.0.0-beta1 （僅限內部）

_2023年6月13日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg) - （測試版）新增以下功能： [傳送歷史訂單](connect-data.md#beta-send-historical-order-data) Experience Platform的資料和狀態。 此功能僅供測試版使用者使用。 您可以傳送電子郵件至下列地址，以加入Beta版： `dataconnection@adobe.com`.

## 2.2.0

_2023年3月30日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg)  — 套件式 `commerce-data-export` 和 `saas-export` 的相依性 `experience-platform-connector` 副檔名。 之前，您必須分別安裝這些相依性。 這些相依性及商家設定可讓伺服器端處理 [後台活動](events-backoffice.md).
![新增](../assets/new.svg)  — 已新增名為的新後台事件 [`orderShipmentCompleted`](events-backoffice.md#ordershipmentcompleted).

## 2.1.1

_2023年2月28日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg)  — 新增對所有PHP 8.2的支援 [!DNL Data Connection] 擴充功能。

## 2.1.0

_2023年1月17日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg)  — 已更新 [[!DNL Data Connection] 擴充功能管理員](connect-data.md) 以便您指定自己的AEP Web SDK (alloy)。
![修正](../assets/fix.svg) 變更為使用 `identityMap` 而非 `personID` 為推送至邊緣的任何資料設定主要身分時。

## 2.0.1

_2022年11月10日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![修正](../assets/fix.svg)  — 現在Adobe Experience Platform內容僅在Storefront事件收集器和店面事件SDK成功載入後設定。

## 2.0.0

_2022年10月12日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg)  — 新增在下列情況下指定您自己的AEP Web SDK的功能 [正在連線](connect-data.md) 將您的Adobe Commerce例項轉移至Experience Platform。
![修正](../assets/fix.svg)  — 更新資料流範圍要求，以便資料流ID的範圍必須限制在網站而非儲存檢閱。

## 1.0.0

_2022年8月9日_

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/new.svg)  — 正式發行版本。
