---
title: 指南概觀
description: 瞭解如何使用整合Adobe Commerce資料與Adobe Experience Platform [!DNL Data Connection] 副檔名。
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
recommendations: noCatalog
source-git-commit: 7d93b556881b3af5f6c8bceb5c9bb6af9ec0bc1c
workflow-type: tm+mt
source-wordcount: '1685'
ht-degree: 0%

---

# [!DNL Data Connection] 簡介

>[!IMPORTANT]
>
>Experience Platform聯結器已重新命名為 [!DNL Data Connection].

此 [!DNL Data Connection] 擴充功能可將Adobe Commerce網頁執行個體連線至Adobe Experience Platform和Edge Network。 瞭解如何 [整合](./mobile-sdk-epc.md) 具Commerce的Adobe Experience Platform Mobile SDK。

您的Commerce商店包含豐富的資料。 有關您的購物者如何瀏覽、檢視及最終在您網站上購買產品的資訊，可揭示建立更個人化購物體驗的機會。 雖然這些資料可告知原生Commerce功能，例如購物車價格規則和動態區塊，但資料仍會定位於您的Commerce執行個體中。

Adobe Experience Platform提供了一套技術，可在與您Commerce商店的資料結合後，透過Edge Network將該資料發佈到其他AdobeDX產品，以解鎖有關購物者購買行為的洞察資訊。 透過這些深入分析，您可以跨所有管道建立更加個人化的購物體驗。

下圖顯示您的Commerce資料如何從您的商店流向其他AdobeDX產品：

![資料如何流向Experience Platform邊緣](assets/commerce-edge.png)

在上圖中，您的店面和後台資料是使用SDK、API和來源聯結器傳送到Experience Platform邊緣。 您不需要完全瞭解這些元件的運作方式，因為擴充功能可處理資料共用的複雜性。 當事件資料位於邊緣時，您可以將該資料提取到其他Experience Platform應用程式中。 例如：

| 應用 | 用途 | 使用案例 |
|---|---|---|
| [Adobe [!DNL Real-Time CDP]](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/overview.html?lang=zh-Hant) | 設定檔管理和細分服務 | **購買記錄細分**：商家可以根據特定時段（每月、每季、每年等）識別購買專案的客戶。 商家可以接著為這些客戶建立區段，並鎖定這些客戶作為促銷活動、促銷活動和 _漏斗頂端_ 適用於訂閱服務潛在客戶的資料。<br> **類別型細分**：商家可以檢視購買的產品類別。<br> **優惠方案型細分**：商戶可識別持續傳回產品的客戶。 提供給他們的優惠和折扣現在可能更具智慧。 例如，對於一直退貨的客戶，可移除免運費。<br> **相似對象目標定位**：A _相似對象_ 是商家為了促銷活動而採用的方法，以便觸及可能會對其業務感興趣的新人，因為他們與現有客戶具有類似的特性。 可以根據行為和異動資料建立相似區段。<br> **客戶傾向**：可從交易資料建立更深入的客戶設定檔，藉此可識別客戶行為變更。 由於有更多資料流入計算（例如產品退貨和產品組態），傾向分數會有較高的信賴度。<br> **交叉銷售**：商家可以從Commerce中擷取的精細資訊找出強大的交叉銷售和向上銷售機會。 |
| [客戶 [!DNL Journey Analytics]](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-overview.html) | 對整個Commerce歷程的深入分析 | **季節性趨勢**：商家可以識別季節性趨勢，這有助於他們為特定產品的週期性需求變化做好準備。 此外，商家可以識別任何產品在不同年份的整體人氣變化。<br> **轉換分析**：瞭解產品購買時間，搭配存取店面印象事件，商戶便能產生豐富的客戶個人檔案，以執行轉換分析。 |
| [Adobe [!DNL Analytics]](https://experienceleague.adobe.com/docs/analytics/analyze/admin-overview/analytics-overview.html) | 深入分析客戶行為與行銷活動績效 | **訂單退貨**：商戶可識別有回訪產品模式的客戶和大型客戶區段。 這有助於商家改善他們的商業策略，因為他們瞭解他們的客戶基礎行為是什麼樣子。<br> **訂單地址**：根據送貨地址，商家可以瞭解訂單是由客戶自行下達，還是由其他個人或實體下達。<br> **季節性趨勢**：商家可以識別季節性趨勢，這有助於他們為特定產品的週期性需求變化做好準備。 此外，商家可以識別任何產品在不同年份的整體人氣變化。<br> **轉換分析**：瞭解產品購買時間，搭配存取店面印象事件，商戶便能產生豐富的客戶個人檔案，以執行轉換分析。 **注意** Adobe Analytics僅支援行為（店面）事件資料。 Adobe Analytics不支援異動(Backoffice)事件資料。 |
| [Adobe [!DNL Journey Optimizer]](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html) | 跨管道的行銷活動協調 | **行為型歷程**：兩年前購買行動電話的客戶現在可能正在尋找新的行動電話，因此可能會成為購買新行動電話的目標。 此外，個人化行銷活動和促銷活動可用於鎖定這類客戶。 [!DNL Journey Optimizer] 可使用其電子郵件和簡訊功能來聯絡這些客戶。 歷史訂單資料與行為資料可用於識別趨勢。 如果客戶過去曾購買特定組態的專案，而現在又希望購買相同的產品，可以讓他們輕鬆檢視/存取相同的產品組態，藉此增強購買歷程。<br> **個人化**：存取客戶設定檔資訊時， [!DNL Journey Optimizer] 可解鎖高度個人化的歷程，讓商家透過多個不同管道聯絡客戶。<br> **已建立新的設定檔**：歡迎電子郵件和促銷活動可鼓勵並影響新客戶的購物歷程。<br> **設定檔已刪除**：商家可選擇停止傳送促銷電子郵件給已關閉帳戶的客戶。 或者，商家也可以建立行銷活動，以贏回失去的客戶。 |

## 將Experience Platform資料提取回Commerce

使用將您的Commerce資料傳送到Experience Platform [!DNL Data Connection] 擴充功能是Commerce資料共用功能的一部分。 另一端（選用的擴充功能）稱為 [Audience Activation](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html). 此擴充功能可讓您在Real-Time CDP中建立受眾，並將這些受眾部署至您的Commerce商店，以告知購物車價格規則及動態區塊。

從高層面來看，從Commerce商店到Experience Platform並透過Audience Activation擴充功能返回的資料流程如下所示：

![[!DNL Data Connection] 流量](assets/data-connection.png)

在您設定Commerce到Experience Platform和Experience Platform到Commerce之間的連線後，資料會繼續流動。 除非升級時需要，否則您不需要重新連線。

## 概念

在這兩個系統之間共用資料需要您瞭解數個概念。

* **資料**  — 與Experience Platform共用的資料是從店面的瀏覽器事件和伺服器上的後台事件收集而得。 店面活動是從購物者在網站上的互動中擷取的，並包括如下事件 [`addToCart`](events.md#addtocart)， [`pageView`](events.md#pageview)， [`createAccount`](events.md#createaccount)， [`editAccount`](events.md#editaccount)， [`startCheckout`](events.md#startcheckout)， [`completeCheckout`](events.md#completecheckout)， [`signIn`](events.md#signin)， [`signOut`](events.md#signout)、等等。 另請參閱 [店面活動](events.md#storefront-events) 以取得店面活動的完整清單。 伺服器端或後台事件，包括 [訂單狀態](events.md#back-office-events) 資訊，例如 [`orderPlaced`](events.md#orderplaced)， [`orderReturned`](events.md#orderitemreturncompleted)， [`orderShipped`](events.md#ordershipmentcompleted)， [`orderCancelled`](events.md#ordercancelled)、等等。 另請參閱 [後台活動](events.md#back-office-events) 以取得後台事件的完整清單。

* **Experience Platform和Edge Network**  — 大部分AdobeDX產品的資料倉儲。 傳送至Experience Platform的資料會透過Experience PlatformEdge Network傳播至AdobeDX產品。 例如，您可以啟動Journey Optimizer、從邊緣擷取您的特定Commerce事件資料，以及在Journey Optimizer中建立捨棄的購物車電子郵件。 如果Commerce商店中有任何放棄的購物車，Journey Optimizer就可以傳送該電子郵件。 進一步瞭解 [Experience Platform與Edge Network](https://experienceleague.adobe.com/docs/platform-learn/data-collection/web-sdk/overview.html).

* **結構描述**  — 結構描述是描述所傳送資料的結構。 在Experience Platform可以內嵌Commerce資料之前，您必須撰寫結構描述資料結構，並對可包含在每個欄位中的資料型別提供限制。 結構描述包含一個基底類別和零個或多個結構描述欄位群組。 此結構描述會使用XDM結構，所有AdobeDX產品都可以讀取該結構。 因此，當您傳送資料給Experience Platform時，可以確定所有DX產品都能瞭解您的資料。 進一步瞭解 [結構描述](https://experienceleague.adobe.com/docs/experience-platform/xdm/home.html).

* **資料集**  — 資料集合的儲存和管理結構，通常是包含結構（欄）和欄位（列）的表格。 資料集也包含中繼資料，可說明其儲存資料的各個層面。 所有成功擷取至Adobe Experience Platform的資料都包含在資料集中。 進一步瞭解 [資料集](https://experienceleague.adobe.com/docs/experience-platform/catalog/datasets/overview.html).

* **資料流**  — 可讓資料從Adobe Experience Platform流向其他AdobeDX產品的ID。 此ID必須與您特定Adobe Commerce執行個體中的特定網站相關聯。 當您建立此資料流時，請指定您在上面建立的XDM結構描述。 進一步瞭解 [資料串流](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html).

## 支援的架構

此 [!DNL Data Connection] 擴充功能適用於下列架構：

* PHP/Luma
* [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/)
* [AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/aep.html)

## 必要條件

若要使用 [!DNL Data Connection] 擴充功能上，您必須具備下列條件：

* Adobe Commerce 2.4.4或更新版本
* Adobe ID和組織ID
* [Adobe使用者端資料層(ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html)，這是收集店面事件資料的必要條件
* 其他AdobeDX產品的權益。

## 入門步驟

在高層面上，啟用 [!DNL Data Connection] 擴充功能涉及下列步驟：

1. [安裝](install.md) 此 [!DNL Data Connection] 副檔名。
1. [登入](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) 至您的Adobe帳戶及 [檢視以確認](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255) 您的組織ID。 組織ID是與已布建Experience Cloud公司相關聯的ID。 此ID是24個字元的英數字串，後面接著（而且必須包含） `@AdobeOrg`.
1. [建立或更新](update-xdm.md) 您的XDM結構描述和商務特定欄位群組。
1. [建立資料集](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) 根據您建立或更新的結構描述。 此資料集包含您傳送的Commerce資料。
1. [建立資料串流](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) 並選取包含商務特定欄位群組的XDM結構描述。
1. [連線至Commerce Services](../landing/saas.md).
1. [連線至Adobe Experience Platform](connect-data.md).

本指南的其餘部分將更詳細地引導您完成所有這些步驟，以便您快速入門，並開始在您的Commerce商店中使用AdobeDX產品的強大功能。

>[!NOTE]
>
>對於行動開發人員而言，瞭解如何 [整合](./mobile-sdk-epc.md) 具Commerce的Adobe Experience Platform Mobile SDK。

## 對象

本指南是專為想要擴充Commerce商店並加以個人化以提升客戶購物體驗的Adobe Commerce商家所設計。

## 支援

如果您需要本指南未涵蓋的資訊或問題，請使用下列資源：

* [說明中心](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html){target="_blank"}
* [支援票證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket){target="_blank"} — 提交票證以接收其他說明。
