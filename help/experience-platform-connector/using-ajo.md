---
title: 使用Adobe Journey Optimizer傳送捨棄的購物車電子郵件
description: 瞭解如何使用Adobe Journey Optimizer傳送捨棄的購物車電子郵件。
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 261416654773470edfa3cc22058cccf92ef29cdb
workflow-type: tm+mt
source-wordcount: '1049'
ht-degree: 0%

---

# 使用Adobe Journey Optimizer傳送捨棄的購物車電子郵件

[Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html) 協助您為購物者打造個人化的商務體驗。 例如，您可以使用Journey Optimizer建立並傳送排程行銷活動（例如零售商店的每週促銷活動），或如果客戶將產品加入購物車但未完成結帳程式，則產生放棄的購物車電子郵件。

按照以下步驟操作，您可以瞭解如何聆聽 `checkout` 從您的Commerce執行個體產生的事件並在Journey Optimizer中回應該事件，以建立捨棄的購物車電子郵件。

>[!IMPORTANT]
>
>為了示範，請務必使用您的Commerce沙箱環境。 這可確保您傳送至Experience Platform的店面和後台事件資料不會稀釋您的生產事件資料。

## 必要條件

開始這些步驟之前，請確定：

- 您已布建為可使用Adobe Journey Optimizer
- 您 [已設定](connect-data.md) Experience Platform聯結器
- 您 [已確認](connect-data.md#confirm-that-event-data-is-collected) 您的Commerce事件資料已送達Experience Platform邊緣

## 步驟1：在您的Commerce沙箱環境中建立使用者

在您的沙箱環境中建立使用者，並確認使用者帳戶資訊會顯示在Experience Platform中。 請確認您指定的電子郵件有效，如同稍後在本節中用來傳送捨棄的購物車電子郵件一樣。

1. 在您的Commerce沙箱環境中登入或建立帳戶。

   ![登入您的測試帳戶](assets/sign-in-account.png){width="700" zoomable="yes"}

   在安裝及設定Experience Platform聯結器後，此帳戶資訊會作為設定檔傳送給Experience Platform。

1. 確認您的使用者帳戶資訊出現在 **[!UICONTROL Profile]** 區段的Experience Platform。

   前往 **[!UICONTROL Profiles]** Adobe Experience Platform中。 按一下 **[!UICONTROL Detail]** 在設定檔中，以檢視您建立的設定檔。

   ![確認設定檔](assets/check-event-profile.png){width="700" zoomable="yes"}

## 步驟2：在Journey Optimizer中檢視事件

在您的Commerce沙箱環境中，檢視產品頁面、將專案新增到購物車，以及購物者將執行的各種其他活動。 這些活動會在您的店面觸發事件。 您現在可以確認這些事件正流入Journey Optimizer。

1. Launch [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/user-interface.html).
1. 選取 **[!UICONTROL Profiles]**.
1. 設定 **[!UICONTROL Identity namespace]** 至 `Email`.
1. 設定 **[!UICONTROL Identity value]** 至您的電子郵件地址。
1. 選取您的設定檔，然後選取 **[!UICONTROL Events]** 標籤。

   ![檢查事件詳細資料](assets/check-event-details.png){width="700" zoomable="yes"}

   尋找 `commerce.checkouts` 事件並檢查事件裝載：

   ```json
   "personID": "84281643067178465783746543501073369488", 
   "eventType": "commerce.checkouts", 
   "_id": "4b41703f-e42e-485b-8d63-7001e3580856-0", 
   "commerce": { 
       "cart": {}, 
       "checkouts": { 
           "value": 1 
       } 
   ```

   如您所見，完整的事件裝載包含豐富的事件資料。 在下一節中，您將設定Journey Optimizer中的事件以監聽和回應 `commerce.checkouts` 從您的Commerce店面產生的事件。

## 步驟3：在Journey Optimizer中設定事件

在Journey Optimizer中設定兩個事件：一個事件監聽 `commerce.checkouts` 來自Commerce的事件，另一個是基本逾時事件，會等待經過特定時間量後，才觸發捨棄的購物車電子郵件。

### 建立監聽器事件

1. Launch [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/user-interface.html).

1. 按一下 **[!UICONTROL Configurations]** 在 **[!UICONTROL Administration]** 區段。

1. 在 **[!UICONTROL Events]** 圖磚，按一下 **[!UICONTROL Manage]**.

   ![Journey Optimizer事件設定](assets/ajo-config.png){width="700" zoomable="yes"}

1. 在 **[!UICONTROL Events]** 頁面，按一下 **[!UICONTROL Create Event]**.

1. 在右側導覽區域中，設定您的事件，如下所示：

   1. 設定 **[!UICONTROL Name]** 至： `firstname_lastname_checkout`.
   1. 設定 **[!UICONTROL Type]** 至 **[!UICONTROL Unitary]**.
   1. 設定 **[!UICONTROL Event id typ]è** 至 **[!UICONTROL Rule based]**.
   1. 設定 **[!UICONTROL Schema]** 至您的商務 [綱要](update-xdm.md).
   1. 選取 **[!UICONTROL Fields]** 和 **[!UICONTROL Fields]** 在出現的頁面中，選取對此事件有用的欄位。

      例如，選取「 」下 **[!UICONTROL Product list items]**， **[!UICONTROL Commerce]**， **[!UICONTROL eventType]**、和 **[!UICONTROL Web]**.

   1. 按一下 **[!UICONTROL OK]** 以儲存選取的欄位。
   1. 按一下 **[!UICONTROL Event id condition]** 欄位並建立條件 `eventType` 等於 `commerce.checkouts` 和 `personalEmail.address` 等於您在上一節建立設定檔時使用的電子郵件地址。

      ![Journey Optimizer設定條件](assets/ajo-set-condition.png){width="700" zoomable="yes"}

   1. 按一下 **[!UICONTROL OK]**.
   1. 按一下 **[!UICONTROL Save]** 以儲存您的事件。

### 建立逾時事件

1. 在Journey Optimizer中建立事件，就像您之前做的那樣。

1. 在右側導覽區域中，設定您的事件，如下所示：

   1. 設定 **[!UICONTROL Name]** 至： `firstname_lastname_timeout`.
   1. 設定 **[!UICONTROL Type]** 至 **[!UICONTROL Unitary]**.
   1. 設定 **[!UICONTROL Event id typ]è** 至 **[!UICONTROL Rule based]**.
   1. 設定 **[!UICONTROL Schema]** 至您的商務 [綱要](update-xdm.md).
   1. 設定 **[!UICONTROL Schema]**， **[!UICONTROL Fields]**、和 **[!UICONTROL Event id condition]** 與上述相同。
   1. 按一下 **[!UICONTROL Save]** 以儲存您的事件。

在設定這兩個事件後，建立傳送捨棄購物車電子郵件的歷程。

## 步驟4：建立結帳歷程

建立聆聽的歷程 `commerce.checkouts` 事件，然後在指定的時間流逝後傳送捨棄的購物車電子郵件。

1. 在Journey Optimizer中，選取 **[!UICONTROL Journeys]** 在 **J[!UICONTROL OURNEY MANAGEMENT]**.
1. 按一下 **[!UICONTROL Create Journey]**.
1. 指定歷程的名稱。
1. 按一下 **[!UICONTROL OK]** 以儲存歷程。
1. 在左側導覽列中的 **[!UICONTROL EVENTS]** 區段，搜尋您先前建立的結帳事件： `firstname_lastname_checkout` 並將它拖放到畫布上。

   >[!TIP]
   >
   >連按兩下事件會自動將其新增至畫布。

1. 搜尋逾時事件並將其新增至畫布。
1. 按兩下逾時事件。

   1. 在 **[!UICONTROL Timeout]** 區段，選取 **[!UICONTROL Define the event time]** 核取方塊。
   1. 在 **[!UICONTROL Wait for]** 欄位輸入 `1` 和 `Minute`.
   1. 選取 **[!UICONTROL Set a timeout path]** 核取方塊。

   透過此逾時設定，執行結帳但未在一分鐘內完成訂單的購物者會觸發此逾時分支。 在實際生產環境中，您可以設定較長的時間，例如24小時。

1. 在左側導覽列中的 **[!UICONTROL ACTIONS]**，新增 **[!UICONTROL Email]** 逾時分支的動作。 您的歷程應如下所示：

   ![Journey Optimizer畫布](assets/ajo-canvas.png){width="700" zoomable="yes"}

### 建立捨棄的購物車電子郵件

建立捨棄的購物車電子郵件，在偵測到捨棄的購物車時傳送。

1. 在您上述建立的歷程中，按兩下 **[!UICONTROL Email]** 圖示來識別。

1. 請遵循 [步驟](https://experienceleague.adobe.com/docs/journey-optimizer/using/content-management/personalization/personalization-use-cases/personalization-use-case-helper-functions.html#configure-email) 在Journey Optimizer指南中，建立捨棄的購物車電子郵件。

您現在在Journey Optimizer中有一個聆聽 `commerce.checkouts` Commerce商店中的事件，以及一段時間後傳送的捨棄購物車電子郵件。 在下一節中，您將測試歷程。

## 步驟5：即時觸發結帳事件

在本節中，您將即時測試事件。

1. 在Journey Optimizer中，切換為測試模式。

   ![啟用測試模式](assets/ajo-enable-test.png){width="700" zoomable="yes"}

1. 若要即時測試此歷程，請開啟另一個瀏覽器索引標籤，並前往您的沙箱Commerce網站。

   1. 新增產品至購物車。
   1. 前往結帳頁面。
   1. 從結帳頁面，返回首頁面或關閉標籤以捨棄購物車。

      歷程現在已觸發。 若要確認，請在Journey Optimizer中開啟擁有您歷程的標籤。 您應該會看到綠色箭頭，顯示使用者瀏覽的路徑。

1. 檢查您的收件匣中是否有電子郵件。
