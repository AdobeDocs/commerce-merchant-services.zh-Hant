---
title: 將商務資料連結至Adobe Experience Platform
description: 了解如何將您的Commerce資料連結至Adobe Experience Platform。
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: 386d5e4245401695d7123a87b7dfb703f1f849e9
workflow-type: tm+mt
source-wordcount: '1307'
ht-degree: 0%

---

# 將商務資料連結至Adobe Experience Platform

安裝Experience Platform連接器時， **系統** 菜單 **服務** 在商務中 _管理_.

- 商務服務連接器
- Experience Platform連接器

若要將您的Adobe Commerce執行個體連結至Adobe Experience Platform，您必須設定兩個連接器，從「商務服務」連接器開始，然後使用Experience Platform連接器完成。

## 更新Commerce Services連接器

如果您先前已安裝Adobe Commerce服務，則您可能已設定Commerce Services連接器。 否則，您必須在 [商務服務連接器](../landing/saas.md) 頁面：

1. 登入您的商務帳戶以 [擷取您的生產與沙箱API金鑰](../landing/saas.md#credentials).
1. 選取 [SaaS資料空間](../landing/saas.md#saas-configuration).
1. 登入您的Adobe帳戶以 [擷取組織ID](../landing/saas.md#ims-organization-optional).

設定商務服務連接器後，接著設定Experience Platform連接器。

## 更新Experience Platform連接器

在本節中，您使用組織ID將Adobe Commerce執行個體連結至Adobe Experience Platform。 然後，您可以指定要傳送至Experience Platform邊緣的資料類型（前端或後端）。

![Experience Platform連接器配置](assets/epc-config-dc.png)

## 一般

1. 登入您的Adobe帳戶，位於 [商務服務連接器](../landing/saas.md#organizationid) 並選取您的組織ID。

   >[!NOTE]
   >
   >如果您先前已設定Commerce Services連接器，則可略過此步驟，因為已選取您的組織ID。

1. 在管理員中，前往 **系統** >服務> **Experience Platform連接器**.

1. 在 **範圍** 下拉式清單，將內容設為 **網站**.

1. 在 **組織ID** 欄位，驗證與您的Adobe Experience Platform帳戶相關聯的ID，如 [商務服務連接器](../landing/saas.md#organizationid). 組織ID為全域。 每個Adobe Commerce例項只能關聯一個組織ID。

1. （選用）如果您已有 [AEP Web SDK(alloy)](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html) 已部署至您的網站，請啟用核取方塊並新增AEP Web SDK的名稱。 否則，請將這些欄位留空，Experience Platform連接器就會為您部署一個欄位。

   >[!NOTE]
   >
   >如果您指定自己的AEP Web SDK,Experience Platform連接器會使用與該SDK相關聯的資料流ID，而非本頁所指定的資料流ID（如果有的話）。

## 資料收集

在本節中，您可指定要傳送至Experience Platform邊緣的資料類型。 資料類型有兩種：用戶端和伺服器端。

用戶端資料是在店面上擷取的資料。 這包括購物者互動，例如 `View Page`, `View Product`, `Add to Cart`，和 [申請表](events.md#b2b-events) 資訊（適用於B2B商戶）。 伺服器端資料或後台資料是在商務伺服器中擷取的資料。 這包括訂單狀態的相關資訊，例如訂單是否已下達、已取消、已退還、已發運或已完成。

在 **資料收集** 區段，選取您要傳送至Experience Platform邊緣的資料類型。 若要確保您的Adobe Commerce例項可以開始資料收集，請檢閱 [必要條件](overview.md#prerequisites).

請參閱事件主題以深入了解 [店面](events.md#storefront-events) 和 [後台](events.md#back-office-events) 事件。

>[!NOTE]
>
>中的所有欄位 **資料收集** 區段 **網站** 範圍或更高。

1. 選擇 **店面事件** 如果您想要傳送storefront行為資料。

   >[!NOTE]
   >
   >此 **店面事件** 如果AEP Web SDK和組織ID有效，則會自動啟用核取方塊。

1. 選擇 **後台事件** 如果您想要發送訂單狀態資訊，例如，已下單、取消、退貨或已發運訂單。

   >[!NOTE]
   >
   >如果您選取 **後台事件**，所有後台資料都會傳送至Experience Platform邊緣。 如果購物者選擇退出資料收集，您必須在Experience Platform中明確設定購物者的隱私權偏好設定。 這與店面事件不同，在店面事件中，收集者已根據購物者偏好處理同意。 [深入了解](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/consent/adobe/dataset.html) 關於在Experience Platform中設定購物者的隱私偏好設定。

1. 確保後台事件資料根據 [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) 工作，你必須改變 `Sales Orders Feed` 索引 `Update by Schedule`.

   1. 在 _管理_ 邊欄，轉到 **[!UICONTROL System]** > _[!UICONTROL Tools]_>**[!UICONTROL Index Management]**.

   1. 選取 `Sales Orders Feed` 索引器。

   1. 設定 **[!UICONTROL Actions]** to `Update by Schedule`.

   1. 如果您是首次啟用後台資料，請運行以下命令以重新索引並觸發重新同步。 只要 [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) 作業設定正確。

      ```bash
      bin/magento index:reindex sales_order_data_exporter_v2
      ```

      ```bash
      bin/magento saas:resync --feed orders
      ```

1. （如果您是使用自己的AEP Web SDK，請略過此步驟。） [建立](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/configure.html#create) Adobe Experience Platform中的資料流，或選取您要用於收集的現有資料流。

1. （如果您是使用自己的AEP Web SDK，請略過此步驟。） 在 **資料流ID** 欄位，貼上新資料流或現有資料流的ID。

## 欄位說明

| 欄位 | 說明 |
|--- |--- |
| 範圍 | 您要套用組態設定的特定網站。 |
| 組織ID（全域） | 屬於購買AdobeDX產品的組織的ID。 此ID會將您的Adobe Commerce執行個體連結至Adobe Experience Platform。 |
| AEP Web SDK是否已部署至您的網站 | 如果您已將自己的AEP Web SDK部署至網站，請選取此核取方塊 |
| AEP Web SDK名稱（全域） | 如果您的網站已部署Experience PlatformWeb SDK，請在此欄位中指定該SDK的名稱。 這可讓「店面事件收集器」和「店面事件SDK」使用您的Experience PlatformWeb SDK，而非Experience Platform連接器部署的版本。 如果您的網站未部署Experience PlatformWeb SDK，請將此欄位留空，Experience Platform連接器就會為您部署一個。 |
| 店面事件 | 只要組織ID和資料流ID有效，就預設會勾選此選項。 店面事件會在購物者瀏覽您的網站時，從他們收集匿名的行為資料。 |
| 後台事件 | 如果勾選此選項，事件裝載會包含匿名的訂單狀態資訊，例如訂單已下、已取消、已退還或已發運。 |
| 資料流ID（網站） | 允許資料從Adobe Experience Platform流向其他AdobeDX產品的ID。 此ID必須與您特定Adobe Commerce例項內的特定網站相關聯。 如果您指定自己的Experience PlatformWeb SDK，請勿在此欄位中指定資料流ID。 Experience Platform連接器會使用與該SDK相關聯的資料流ID，並忽略此欄位中指定的任何資料流ID（如果有的話）。 |

>[!NOTE]
>
>上線後，店面資料會開始流向Experience Platform邊緣。 後台資料需要5分鐘才會出現在邊緣。 後續更新會根據cron排程顯示在邊緣。

## 確認已收集事件資料

若要確認正從您的商務商店收集資料，請使用 [Adobe Experience Platform debugger](https://experienceleague.adobe.com/docs/experience-platform/debugger/home.html) 來檢查您的商務網站。 確認正在收集資料後，您可以執行會傳回來自 [建立的資料集](overview.md#prerequisites).

1. 選擇 **查詢** 在Experience Platform的左側導覽中，然後按一下 [!UICONTROL Create Query].

   ![查詢編輯器](assets/query-editor.png)

1. 查詢編輯器開啟時，輸入可從資料集中選取資料的查詢。

   ![建立查詢](assets/create-query.png)

   例如，您的查詢可能如下所示：

   ```sql
   SELECT * from `your_dataset_name` ORDER by TIMESTAMP DESC
   ```

1. 查詢執行後，結果會顯示在 **結果** 標籤，在 **主控台** 標籤。 此視圖顯示查詢的表格輸出。

   ![查詢編輯器](assets/query-results.png)

在此範例中，您會看到 [`commerce.productListAdds`](events.md#addtocart), [`commerce.productViews`](events.md#productpageview), [`web.webpagedetails.pageViews`](events.md#pageview)等。 此檢視可讓您驗證您的商務資料是否到達邊緣。

如果結果不符合預期，請開啟資料集並尋找任何失敗的批次匯入。 深入了解 [疑難排解批次匯入](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/troubleshooting.html).
