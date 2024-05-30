---
title: 使用以下專案在Real-Time CDP中建立受眾 [!DNL Commerce] 事件資料
description: 瞭解如何使用 [!DNL Commerce] 事件資料，以在Real-Time CDP中建立對象
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: fc2a7ba6891cf8affdec13b0400d75350284faa2
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 0%

---

# 使用在Real-Time CDP中建立受眾 [!DNL Commerce] 事件資料

使用從您的擷取的事件資料 [!DNL Commerce] 存放區以在Real-Time CDP中建立對象。 擷取的資料會根據瀏覽行為、過去的購買、設定檔屬性、轉換或流失的傾向、忠誠度狀態、高和低客戶價值等。

## 我應考慮使用哪些資料？

使用店面、後台和設定檔事件的資料，在Real-Time CDP中建立對象。

| 資料型別 | 店面資料（行為事件） | 後台資料（伺服器端事件） | 客戶設定檔和區段資料 |
|---|---|---|---|
| **定義** | 客戶在您網站上採取的點按或動作。 | 生命週期相關資訊和每個訂單（過去和目前）的詳細資訊。 | 您的購物者是誰，以及他們符合哪些區段的資格。 |
| **Adobe Commerce擷取的事件** | [productPageView](events.md#productpageview)<br>[addToCart](events.md#addtocart) | [placeOrder](events.md#completecheckout)<br>[已訂購](events-backoffice.md#orderplaced)<br>[orderLineItemRefreaded](events-backoffice.md#orderlineitemrefunded)<br>[訂單已取消](events-backoffice.md#ordercancelled)<br>[訂單歷史記錄](connect-data.md#send-historical-order-data) | [createAccount](events.md#createaccount)<br>[editAccount](events.md#editaccount)<br>[設定檔記錄](events-profilerecord.md) |

## 其他客戶都取得了哪些成就？

Adobe [!DNL Commerce] 客戶透過啟用內建於Real-Time CDP的受眾並將其部署至其網站，已取得顯著的業務影響。 [!DNL Commerce] 執行個體。

一家全球多品牌服裝零售商達成：

- 擁有數百萬個統一客戶設定檔的單一信任來源
- 建立40多個「高意圖客戶」的不重複受眾，以跨管道參與

一家全球飲料公司收集到：

- 來自100多個國家/地區的9,800萬個客戶設定檔

## 讓我們開始吧

在本文中，您將瞭解如何：

- 在Real-Time CDP中建立對象，根據 [!DNL Commerce] 事件收集的資料
- 為您的啟用該對象 [!DNL Commerce] 儲存
- 在中使用對象 [!DNL Commerce] 通知購物車價格規則

>[!IMPORTANT]
>
>使用您的 [!DNL Commerce] 沙箱環境。 這可確保您傳送至Experience Platform的店面和後台事件資料不會稀釋您的生產事件資料。

### 必要條件

開始之前，請確定：

- 您已布建為可使用Real-Time CDP。 如果您不確定，請洽詢您的系統整合商或管理專案和環境的開發團隊。
- 您 [已安裝](install.md) 和 [已設定](connect-data.md) 此 [!DNL Data Connection] 中的擴充功能 [!DNL Commerce].
- 您 [已確認](connect-data.md#confirm-that-event-data-is-collected) 您的 [!DNL Commerce] 事件資料已送達Experience Platform邊緣。

### 1.建立對象

受眾是一組具有類似行為或特徵的客戶。 在本練習中，您會建立受眾，使對您商店中特定產品感興趣的人員符合資格。

若要簡化此練習，您可以使用以下連結的事件資料： [productPageView](events.md#productpageview) 事件。 此事件會擷取有關已檢視產品的詳細資訊，例如產品名稱、SKU、價格等。

使用此事件資料可指定對象包含至少有一個「產品檢視」事件的個人，其中SKU （產品識別碼）等於網站上的特定產品，且該事件發生在前一天。&#x200B;URL

1. 開啟Experience Platform並選取 **[!UICONTROL Audiences]** 從左側導覽功能表。

   ![對象控制面板](assets/audience-left-rail.png)

1. 按一下 **[!UICONTROL Create Audience]**.

   ![建立對象](assets/browse-create-audience.png)

   此 **區段產生器** 工作區隨即顯示。

1. 在 **區段產生器** 工作區中，選取 **建置規則** 建立方法。

   ![建置規則](assets/build-rule.png)

   此 **區段產生器** 工作區是您定義對象規則和條件的地方&#x200B;。 這些規則和條件以您Commerce存放區中的事件和設定檔資料為基礎，並定義判斷使用者是否符合對象資格的條件。 例如，您可以建立規則，納入已檢視特定產品的使用者，或在特定時間範圍內購買的使用者。 進一步瞭解 [區段產生器](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) 以及規則和條件。

1. 選取 [活動](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder#events) 標籤。

   ![事件標籤](assets/audience-events-tab.png)

1. 搜尋「產品檢視」事件型別。 然後，將其拖放至 **區段產生器** 工作區。

1. 返回 **活動** 標籤並搜尋「SKU」(亦即 `productListItems` 欄位。 將其拖放至 **區段產生器** 工作區位於 **產品檢視** 事件。

   此 **事件規則** 區段隨即顯示，您可在其中指定要用來建立對象的特定產品。

   ![選取SKU](assets/audience-addsku.png)

1. 按一下，將時間間隔設定為一天 **任何時間** 並選取 *最近* ，值為 *1*.

   建立對象時，您可以指定擷取最近活動的時間間隔。 設定時間間隔可讓您根據使用者在特定時間範圍內最近的互動或行為來鎖定使用者。

1. 在 **對象屬性** 工作區右側的區段，提供對象的名稱、說明和評估方法來設定對象屬性。

1. 若要儲存對象，請按一下 **[!UICONTROL Save and Close]**.

   您對象的詳細資訊會顯示在 **對象** 儀表板。

### 2.將對象啟動至 [!DNL Commerce] 目的地

您讓對象可在 [!DNL Commerce] 透過為啟用 [!DNL Commerce] 目的地。

>[!IMPORTANT]
>
>如果您尚未設定 [!DNL Commerce] 作為接收資料的可用目的地，請參閱 [Adobe [!DNL Commerce] 連線](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/adobe-commerce) 主題。

1. 在 **詳細資料** 索引標籤中，按一下 **啟用到目的地**.

1. 選取您的 [!DNL Commerce] 目的地。 然後，按一下 **下一個**.

1. 按一下「 」以完成啟用程式 **[!UICONTROL Finish]**.

## 3.在「對象控制面板」中檢視對象

在 [!DNL Commerce]，您可以檢視全部 [主要](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations) 可針對您的進行個人化的對象 [!DNL Commerce] 使用下列專案的例項： **Real-Time CDP受眾** 儀表板。

若要存取 **Real-Time CDP受眾** 儀表板，前往 _管理員_ 側欄，然後前往 **[!UICONTROL Customers]** > **[!UICONTROL Real-time CDP Audience]**.

在控制面板中，尋找您建立的對象。 請注意，購物車價格規則或動態區塊中並未使用它。 在下一節中，您會將對象連結至購物車價格規則。

![Real-Time CDP受眾控制面板](assets/real-time-cdp-dashboard.png)

### 4.根據對象建立購物車價格規則

本節說明如何根據新對象建立購物車價格規則。

1. 確認您的新對象顯示在 **Real-Time CDP受眾** 儀表板。
1. [建立購物車價格規則](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-create).
1. [設定條件](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-create#use-real-time-cdp-audiences-to-set-a-condition) 使用新對象的購物車價格規則。
1. [設定動作](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-create#step-3-define-the-actions) 將產品新增至購物車時想要發生的活動。
1. 繼續設定購物車價格規則。
1. 前往沙箱執行個體的客戶檢視。
1. 將您根據對象的產品新增至購物車。 請注意，購物車價格規則已啟用。

## 總結

在本練習中，您已在Real-Time CDP中建立受眾，並將其啟動至 [!DNL Commerce] 目的地。 然後，在 [!DNL Commerce] 管理員，您已根據該對象建立購物車價格規則，並在您的沙箱環境中啟用該規則。
