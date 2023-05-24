---
title: 將Commerce資料連線至Adobe Experience Platform
description: 瞭解如何將您的Commerce資料連結至Adobe Experience Platform。
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: 386d5e4245401695d7123a87b7dfb703f1f849e9
workflow-type: tm+mt
source-wordcount: '1307'
ht-degree: 0%

---

# 將Commerce資料連線至Adobe Experience Platform

安裝Experience Platform聯結器時，兩個新設定頁面會出現在 **系統** 下的選單 **服務** 在商務中 _管理員_.

- 商務服務聯結器
- Experience Platform聯結器

若要將您的Adobe Commerce執行個體連線到Adobe Experience Platform，您必須設定兩個聯結器，從Commerce Services聯結器開始，然後使用Experience Platform聯結器完成。

## 更新Commerce服務聯結器

如果您先前已安裝Adobe Commerce服務，則您可能已設定Commerce Services聯結器。 如果沒有，您必須在 [Commerce服務聯結器](../landing/saas.md) 頁面：

1. 登入您的Commerce帳戶至 [擷取您的生產和沙箱API金鑰](../landing/saas.md#credentials).
1. 選取 [SaaS資料空間](../landing/saas.md#saas-configuration).
1. 登入您的Adobe帳戶至 [擷取您的組織ID](../landing/saas.md#ims-organization-optional).

設定Commerce Services聯結器後，再設定Experience Platform聯結器。

## 更新Experience Platform聯結器

在本節中，您會使用組織ID將Adobe Commerce執行個體連結至Adobe Experience Platform。 然後，您可以指定要傳送至Experience Platform邊緣的資料型別（店面或後台）。

![Experience Platform聯結器設定](assets/epc-config-dc.png)

## 一般

1. 在登入您的Adobe帳戶 [商務服務聯結器](../landing/saas.md#organizationid) 並選取您的組織ID。

   >[!NOTE]
   >
   >如果您先前已設定Commerce Services聯結器，則可以跳過此步驟，因為已選取您的組織ID。

1. 在Admin中，前往 **系統** >服務> **Experience Platform聯結器**.

1. 在 **範圍** 下拉式清單，將內容設定為 **網站**.

1. 在 **組織ID** 欄位中，驗證與您的Adobe Experience Platform帳戶相關聯的ID (如 [商務服務聯結器](../landing/saas.md#organizationid). 組織ID為全域。 每個Adobe Commerce執行個體只能關聯一個組織ID。

1. （選用）如果您已有 [AEP Web SDK (alloy)](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html) 部署至您的網站，啟用核取方塊並新增AEP Web SDK的名稱。 否則，請將這些欄位留空，Experience Platform聯結器會為您部署一個欄位。

   >[!NOTE]
   >
   >如果您指定自己的AEP Web SDK，Experience Platform聯結器會使用與該SDK相關聯的資料流ID，而不是此頁面上指定的資料流ID （如果有的話）。

## 資料彙集

您可以在此段落中指定您要傳送至Experience Platform邊緣的資料型別。 有兩種型別的資料：使用者端和伺服器端。

使用者端資料是在店面擷取的資料。 這包括購物者互動，例如 `View Page`， `View Product`， `Add to Cart`、和 [請購單清單](events.md#b2b-events) 資訊（適用於B2B商家）。 伺服器端資料（或後端辦公室資料）是擷取到Commerce伺服器的資料。 這包括訂單狀態的相關資訊，例如，訂單是否已下達、取消、退款、已出貨或完成。

在 **資料彙集** 區段，選取您要傳送至Experience Platform邊緣的資料型別。 為確保您的Adobe Commerce執行個體可以開始資料收集，請檢閱 [必備條件](overview.md#prerequisites).

請參閱事件主題以深入瞭解 [店面](events.md#storefront-events) 和 [後台](events.md#back-office-events) 事件。

>[!NOTE]
>
>所有欄位 **資料彙集** 區段套用至 **網站** 範圍或更高。

1. 選取 **店面活動** 如果您想要傳送店面行為資料。

   >[!NOTE]
   >
   >此 **店面活動** 如果AEP Web SDK和組織ID有效，則會自動啟用核取方塊。

1. 選取 **後台活動** 如果您要傳送訂單狀態資訊，例如訂單是否已下達、取消、退款或出貨。

   >[!NOTE]
   >
   >如果您選取 **後台活動**，所有後台資料都會傳送至Experience Platform邊緣。 如果購物者選擇退出資料收集，您必須在Experience Platform中明確設定購物者的隱私權偏好設定。 這與店面事件不同，店面事件收集器已根據購物者偏好設定處理同意。 [瞭解更多](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/consent/adobe/dataset.html) 關於在Experience Platform中設定購物者的隱私權偏好設定。

1. 確保後台事件資料會根據排程更新 [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) 工作，您必須變更 `Sales Orders Feed` 索引至 `Update by Schedule`.

   1. 於 _管理員_ 側欄，前往 **[!UICONTROL System]** > _[!UICONTROL Tools]_>**[!UICONTROL Index Management]**.

   1. 選取的核取方塊 `Sales Orders Feed` 索引器。

   1. 設定 **[!UICONTROL Actions]** 至 `Update by Schedule`.

   1. 如果您是第一次啟用後台資料，請執行以下命令來重新索引並觸發重新同步。 後續的重新同步只要符合下列條件就會自動進行： [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) 工作已正確設定。

      ```bash
      bin/magento index:reindex sales_order_data_exporter_v2
      ```

      ```bash
      bin/magento saas:resync --feed orders
      ```

1. （如果您使用自己的AEP Web SDK，請略過此步驟。） [建立](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/configure.html#create) Adobe Experience Platform中的資料流，或選取您要用於收集的現有資料流。

1. （如果您使用自己的AEP Web SDK，請略過此步驟。） 在 **資料串流ID** 欄位，貼上新資料流或現有資料流的ID。

## 欄位說明

| 欄位 | 說明 |
|--- |--- |
| 範圍 | 您要套用組態設定的特定網站。 |
| 組織ID （全域） | 屬於購買AdobeDX產品的組織的ID。 此ID會將您的Adobe Commerce執行個體連結至Adobe Experience Platform。 |
| AEP Web SDK是否已部署至您的網站 | 如果您已將自己的AEP Web SDK部署到網站，請選取此核取方塊 |
| AEP Web SDK名稱（全域） | 如果您已將Experience PlatformWeb SDK部署至網站，請在此欄位中指定該SDK的名稱。 這可讓店面事件收集器和店面事件SDK使用您的Experience PlatformWeb SDK，而不是Experience Platform聯結器部署的版本。 如果您未將Experience PlatformWeb SDK部署到網站，請將此欄位留空，Experience Platform聯結器會為您部署一個。 |
| 店面活動 | 只要組織ID和資料流ID有效，就會預設勾選。 店面活動會在購物者瀏覽您的網站時，從他們那裡收集匿名的行為資料。 |
| 後台活動 | 若勾選，事件有效負載會包含匿名處理的訂單狀態資訊，例如訂單是否已下達、取消、退款或出貨。 |
| 資料串流ID （網站） | 可讓資料從Adobe Experience Platform流向其他AdobeDX產品的ID。 此ID必須與您特定Adobe Commerce執行個體中的特定網站相關聯。 如果您指定自己的Experience PlatformWeb SDK，請勿在此欄位中指定資料串流ID。 Experience Platform聯結器會使用與該SDK相關聯的資料流ID，並忽略此欄位中指定的任何資料流ID （如果有的話）。 |

>[!NOTE]
>
>上線後，店面資料開始流入Experience Platform邊緣。 後端辦公室資料大約需要5分鐘才會顯示在邊緣。 後續更新會根據cron排程顯示在邊緣。

## 確認已收集事件資料

若要確認系統正在從Commerce商店收集資料，請使用 [Adobe Experience Platform debugger](https://experienceleague.adobe.com/docs/experience-platform/debugger/home.html) 檢查您的Commerce網站。 確認資料正在收集後，您可以透過執行查詢，從傳回資料，確認店面和後台事件資料出現在邊緣 [您建立的資料集](overview.md#prerequisites).

1. 選取 **查詢** 在Experience Platform的左側導覽列中，然後按一下 [!UICONTROL Create Query].

   ![查詢編輯器](assets/query-editor.png)

1. 當查詢編輯器開啟時，輸入從資料集中選取資料的查詢。

   ![建立查詢](assets/create-query.png)

   例如，您的查詢可能如下所示：

   ```sql
   SELECT * from `your_dataset_name` ORDER by TIMESTAMP DESC
   ```

1. 查詢執行後，結果會顯示在 **結果** 標籤，在 **主控台** 標籤。 此檢視顯示查詢的表格輸出。

   ![查詢編輯器](assets/query-results.png)

在此範例中，您會看到以下專案中的事件資料： [`commerce.productListAdds`](events.md#addtocart)， [`commerce.productViews`](events.md#productpageview)， [`web.webpagedetails.pageViews`](events.md#pageview)、等等。 此檢視可讓您驗證您的Commerce資料是否到達邊緣。

如果結果與預期不符，請開啟資料集並尋找任何失敗的批次匯入。 進一步瞭解 [疑難排解批次匯入](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/troubleshooting.html).
