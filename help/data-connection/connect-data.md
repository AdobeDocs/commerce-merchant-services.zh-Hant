---
title: 將Commerce資料連線至Adobe Experience Platform
description: 瞭解如何將您的Commerce資料連結至Adobe Experience Platform。
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
feature: Personalization, Integration, Configuration
source-git-commit: 540c423ecf7e50a36c1137f43a9cf9673658c805
workflow-type: tm+mt
source-wordcount: '2501'
ht-degree: 0%

---

# 將Commerce資料連線至Adobe Experience Platform

當您安裝 [!DNL Data Connection] 擴充功能上，兩個新設定頁面會出現在 **系統** 下的選單 **服務** 在商務中 _管理員_.

- Commerce服務聯結器
- [!DNL Data Connection]

若要將您的Adobe Commerce執行個體連線到Adobe Experience Platform，您必須設定兩個聯結器，從商務服務聯結器開始，然後使用 [!DNL Data Connection] 副檔名。

## 設定Commerce服務聯結器

如果您先前已安裝Adobe Commerce服務，您可能已設定Commerce Services聯結器。 如果沒有，則您必須在 [Commerce服務聯結器](../landing/saas.md) 頁面：

1. 登入您的Commerce帳戶至 [擷取您的生產和沙箱API金鑰](../landing/saas.md#credentials).
1. 選取 [SaaS資料空間](../landing/saas.md#saas-configuration).
1. 登入您的Adobe帳戶至 [擷取您的組織ID](../landing/saas.md#ims-organization-optional).

設定Commerce Services聯結器後，再設定 [!DNL Data Connection] 副檔名。

## 設定 [!DNL Data Connection] 副檔名

在本節中，您將瞭解如何設定 [!DNL Data Connection] 副檔名。

### 新增服務帳戶和認證詳細資料

如果您計畫收集並傳送 [歷史訂單資料](#send-historical-order-data) 或 [(Beta)客戶設定檔資料](#send-customer-profile-data)，您必須新增服務帳戶和認證詳細資料。 此外，如果您要設定 [Audience Activation](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html) 擴充功能上，您必須完成這些步驟。

如果您只收集及傳送店面或後台資料，可跳至 [一般](#general) 區段。

#### 步驟1：在Adobe Developer Console中建立專案

在Adobe Developer Console中建立可驗證Commerce的專案，以便進行Experience PlatformAPI呼叫。

若要建立專案，請遵循以下概述的步驟： [驗證及存取Experience PlatformAPI](https://experienceleague.adobe.com/docs/experience-platform/landing/platform-apis/api-authentication.html) 教學課程。

進行教學課程的過程中，請確定您的專案具備下列專案：

- 存取以下專案 [產品設定檔](https://experienceleague.adobe.com/docs/experience-platform/landing/platform-apis/api-authentication.html#select-product-profiles)： **預設的生產所有存取權** 和 **AEP預設所有存取**.
- 正確 [角色和許可權已設定](https://experienceleague.adobe.com/docs/experience-platform/landing/platform-apis/api-authentication.html#assign-api-to-a-role).
- 如果您決定使用JSON Web權杖(JWT)作為伺服器對伺服器的驗證方法，您也必須上傳私密金鑰。

此步驟的結果會建立您在下一步中使用的組態檔。

#### 步驟2：下載設定檔

下載 [工作區組態檔](https://developer.adobe.com/commerce/extensibility/events/project-setup/#download-the-workspace-configuration-file). 將此檔案的內容複製並貼到 **服務帳戶/認證詳細資料** 商務管理員頁面。

1. 在商務管理員中，瀏覽至 **商店** >設定> **設定** > **服務** > **[!DNL Data Connection]**.

1. 選取您從伺服器對伺服器執行的授權方法 **Adobe Developer授權型別** 功能表。 Adobe建議使用OAuth。 已棄用JWT。 [瞭解更多](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/).

1. （僅限JWT）複製並貼上您的內容至 `private.key` 將檔案移入 **使用者端密碼** 欄位。 使用下列指令來複製內容。

   ```bash
   cat config/private.key | pbcopy
   ```

   另請參閱 [服務帳戶(JWT)驗證](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/) 以取得有關 `private.key` 檔案。

1. 複製 `<workspace-name>.json` 將檔案移入 **服務帳戶/認證詳細資料** 欄位。

   ![[!DNL Data Connection] 管理員設定](./assets/epc-admin-config.png){width="700" zoomable="yes"}

1. 按一下 **儲存設定**.

### 一般

1. 在Admin中，前往 **系統** >服務> **[!DNL Data Connection]**.

1. 在 **設定** 標籤下的 **一般**，確認與您的Adobe Experience Platform帳戶相關聯的ID （如中所設定） [Commerce服務聯結器](../landing/saas.md#organizationid). 組織ID為全域。 每個Adobe Commerce例項只能關聯一個組織ID。

1. 在 **範圍** 下拉式清單，將內容設定為 **網站**.

1. （選用）如果您已有 [AEP Web SDK (alloy)](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html) 部署至您的網站，啟用核取方塊並新增AEP Web SDK的名稱。 否則，請將這些欄位留空，並且 [!DNL Data Connection] 擴充功能會為您部署一個。

   >[!NOTE]
   >
   >如果您指定自己的AEP Web SDK，請 [!DNL Data Connection] 擴充功能使用與該SDK相關聯的資料串流ID，而非此頁面上指定的資料串流ID （如果有的話）。

### 資料彙集

您可以在此段落中指定您要收集並傳送至Experience Platform邊緣的資料型別。 有三種型別的資料：

- **行為** （使用者端資料）是在店面擷取的資料。 這包括購物者互動，例如 `View Page`， `View Product`， `Add to Cart`、和 [請購單清單](events.md#b2b-events) 資訊（適用於B2B商家）。

- **後台** （伺服器端資料）是在Commerce伺服器中擷取的資料。 這包括訂單狀態的相關資訊，例如，訂單是否已下達、取消、退款、出貨或完成。 其中也包含 [歷史訂單資料](#send-historical-order-data).

- (**測試版**) **個人資料** 是與購物者的設定檔資訊相關的資料。 瞭解 [更多](#send-customer-profile-data).

為確保您的Adobe Commerce執行個體可以開始資料收集，請檢閱 [必備條件](overview.md#prerequisites).

請參閱活動主題以深入瞭解 [店面](events.md#storefront-events)， [後台](events.md#back-office-events)、和 [設定檔](events.md#customer-profile-events-server-side) 事件。

>[!NOTE]
>
>此欄位中的所有欄位 **資料彙集** 區段套用至 **網站** 範圍或更高版本。

1. 選取 **店面活動** 如果您想要傳送店面行為資料。

1. 選取 **後台活動** 如果您要傳送訂單狀態資訊，例如，訂單是否已下單、已取消、已退款或已出貨。

   >[!NOTE]
   >
   >如果您選取 **後台活動**，所有後台資料都會傳送至Experience Platform邊緣。 如果購物者選擇退出資料收集，您必須在Experience Platform中明確設定購物者的隱私權偏好設定。 這與店面事件不同，店面事件收集器已根據購物者偏好設定處理同意。 瞭解 [更多](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/consent/adobe/dataset.html) 關於在Experience Platform中設定購物者的隱私權偏好設定。

1. （如果您使用自己的AEP Web SDK，請略過此步驟。） [建立](https://experienceleague.adobe.com/docs/experience-platform/datastreams/configure.html#create) Adobe Experience Platform中的資料流，或選取您要用於收集的現有資料流。 輸入資料串流ID於 **資料串流ID** 欄位。

1. 輸入 **資料集ID** 要包含Commerce資料的資訊。 若要尋找資料集ID：

   1. 開啟Experience PlatformUI並選取 **資料集** 在左側導覽以開啟 **資料集** 儀表板。 控制面板會列出貴組織的所有可用資料集。 系統會顯示每個列出資料集的詳細資料，包括其名稱、資料集所遵守的結構描述，以及最近一次擷取執行的狀態。
   1. 開啟與資料流相關聯的資料集。
   1. 在右側窗格中，檢視資料集的詳細資訊。 複製資料集ID

1. 若要根據排程確保後台事件資料得以更新 [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) 工作，您必須變更 `Sales Orders Feed` 索引至 `Update by Schedule`.

   1. 在 _管理員_ 側欄，前往 **[!UICONTROL System]** > _[!UICONTROL Tools]_>**[!UICONTROL Index Management]**.

   1. 選取「 」的核取方塊 `Sales Orders Feed` 索引器。

   1. 設定 **[!UICONTROL Actions]** 至 `Update by Schedule`.

   1. 如果您是第一次啟用後台資料，請執行以下命令來重新索引並觸發重新同步。 後續的重新同步會自動進行，只要 [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) 工作已正確設定。

      ```bash
      bin/magento index:reindex sales_order_data_exporter_v2
      ```

      ```bash
      bin/magento saas:resync --feed orders
      ```

#### 欄位說明

| 欄位 | 說明 |
|--- |--- |
| 範圍 | 您要套用組態設定的特定網站。 |
| 組織ID （全域） | 屬於購買AdobeDX產品的組織的ID。 此ID會將您的Adobe Commerce執行個體連結至Adobe Experience Platform。 |
| AEP Web SDK是否已部署至您的網站 | 如果您已將自己的AEP Web SDK部署到網站，請選取此核取方塊 |
| AEP Web SDK名稱（全域） | 如果您已將Experience PlatformWeb SDK部署至網站，請在此欄位中指定該SDK的名稱。 這可讓店面事件收集器和店面事件SDK使用您的Experience PlatformWeb SDK，而不是由部署的版本 [!DNL Data Connection] 副檔名。 如果您未將Experience Platform Web SDK部署至網站，請將此欄位留空，然後 [!DNL Data Connection] 擴充功能會為您部署一個。 |
| 店面活動 | 只要組織ID和資料流ID有效，就會預設勾選。 店面活動會在購物者瀏覽您的網站時，從他們那裡收集匿名的行為資料。 |
| 後台活動 | 若勾選，事件裝載會包含匿名處理的訂單狀態資訊，例如訂單是否已下達、取消、退款或出貨。 |
| 資料串流ID （網站） | 可讓資料從Adobe Experience Platform流向其他AdobeDX產品的ID。 此ID必須與您特定Adobe Commerce執行個體中的特定網站相關聯。 如果您指定自己的Experience PlatformWeb SDK，請勿在此欄位中指定資料串流ID。 此 [!DNL Data Connection] 擴充功能會使用與該SDK相關聯的資料流ID，並忽略此欄位中指定的任何資料流ID （如果有的話）。 |
| 資料集ID （網站） | 包含您的Commerce資料之資料集的ID。 除非您已取消選取 **店面活動** 或 **後台活動** 核取方塊。 此外，如果您使用自己的Experience PlatformWeb SDK，並因此未指定資料流ID，您仍須新增與資料流相關聯的資料集ID。 否則，您無法儲存此表單。 |

上線後，店面資料開始流入Experience Platform邊緣。 後端辦公室資料大約需要5分鐘才會顯示在邊緣。 後續更新會根據cron排程顯示在邊緣。

### 傳送客戶設定檔資料

>[!IMPORTANT]
>
>此功能為測試版。 如果您想要加入Beta版計畫，請傳送要求至 [dataconnection@adobe.com](mailto:dataconnection@adobe.com).

您可傳送兩種型別的設定檔資料至Experience Platform：設定檔記錄和時間序列設定檔事件。

個人資料記錄包含購物者在Commerce執行個體中建立個人資料時所儲存的資料，例如購物者的姓名。 當您的結構和資料集為 [已正確設定](profile-data.md)，則會將設定檔記錄傳送至Experience Platform，並轉送至Adobe的設定檔管理和細分服務： [Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/intro/rtcdp-intro/overview.html).

時間序列設定檔事件包含購物者設定檔資訊的相關資料，例如是否他們在您的網站上建立、編輯或刪除帳戶。 將設定檔事件資料傳送至Experience Platform時，該資料會位於資料集中，以供其他DX產品使用。

1. 確定您擁有 [已提供](#add-service-account-and-credential-details) 服務帳戶和認證詳細資料。

1. 請確定您已為以下專案指定結構描述和資料集： [設定檔記錄資料擷取](profile-data.md) 和 [時間序列設定檔事件資料擷取](update-xdm.md#time-series-profile-event-data).

1. 在中放置核取記號 **客戶設定檔** Experience Platform核取方塊。

1. 輸入 **設定檔資料集ID**.

   個人檔案記錄資料使用的資料集必須與您目前用於行為和後台事件資料的資料集不同。

1. 如果您不想透過用於行為和後台資料的相同資料流ID來串流設定檔事件，請從 **透過相同的資料流ID串流客戶設定檔** 並輸入您要改用的資料流ID。

在Real-Time CDP中使用設定檔記錄大約需要10分鐘。 設定檔事件會立即開始串流。

#### 欄位說明

| 欄位 | 說明 |
|--- |--- |
| 客戶設定檔 | 如果您想要收集並傳送客戶設定檔記錄，請選取此核取方塊。 |
| 設定檔資料集ID | 個人資料記錄所使用的資料集，必須與行為與後台事件所使用的資料集不同。 |
| 透過相同的資料流ID串流客戶設定檔 | 決定是否想要使用目前用於行為與後台事件的相同資料流。 |
| 客戶設定檔的資料流 | 指定客戶設定檔記錄特定的資料流。 |

### 傳送歷史訂單資料

Adobe Commerce最多收集五年的 [歷史訂單資料與狀態](events.md#back-office-events). 您可以使用 [!DNL Data Connection] 擴充功能可將歷史資料傳送至Experience Platform，讓您的客戶設定檔更為豐富，並根據這些過去的訂單個人化客戶體驗。 資料儲存在Experience Platform內的資料集中。

雖然Commerce已收集歷史訂單資料，但您必須完成數個步驟才能將該資料傳送至Experience Platform。

觀看此影片以進一步瞭解歷史訂單，然後完成下列步驟以實施歷史訂單收集。

>[!VIDEO](https://video.tv.adobe.com/v/3424672)

#### 設定Order Sync服務

訂單同步服務使用 [訊息佇列架構](https://developer.adobe.com/commerce/php/development/components/message-queues/) 和RabbitMQ。 完成這些步驟後，訂單狀態資料可以同步至SaaS，這會在傳送至Experience Platform之前是必要的。

1. 確定您擁有 [已提供](#add-service-account-and-credential-details) 服務帳戶和認證詳細資料。

1. [啟用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/rabbitmq.html) RabbitMQ。

   >[!NOTE]
   >
   >RabbitMQ已設定為Commerce 2.4.7版及更新版本，但您必須啟用消費者。

1. 透過中的cron工作啟用訊息佇列取用者 `.magento.env.yaml` 使用 `CRON_CONSUMERS_RUNNER` 環境變數。

   ```yaml
      stage:
        deploy:
          CRON_CONSUMERS_RUNNER:
            cron_run: true
   ```

   >[!NOTE]
   >
   >請參閱 [部署變數檔案](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#cron_consumers_runner) 以瞭解所有可用的設定選項。

啟用訂單同步服務後，您就可以在 **[!UICONTROL [!DNL Data Connection]]** 頁面。

#### 指定訂單歷史記錄日期範圍

指定您要傳送給Experience Platform之歷史訂單的日期範圍。

1. 在Admin中，前往 **系統** >服務> **[!DNL Data Connection]**.

1. 選取 **訂單歷史記錄** 標籤。

1. 在 **訂單歷史記錄同步**，則 **從設定複製資料集ID** 核取方塊已啟用。 這可確保您使用的資料集與 **設定** 標籤。

1. 在 **從** 和 **至** 欄位，指定您要傳送之歷史訂單資料的日期範圍。 您無法選取超過五年的日期範圍。

1. 選取 **[!UICONTROL Start Sync]** 以觸發同步處理開始。 歷史訂單資料是批次處理資料，而非使用串流資料的店面和後台資料。 批次資料需約45分鐘才能送達Experience Platform。

##### 欄位說明

| 欄位 | 說明 |
|--- |--- |
| 從設定複製資料集ID | 複製您在上輸入的資料集ID **設定** 標籤。 |
| 資料集ID （網站） | 包含您的Commerce資料之資料集的ID。 除非您已取消選取 **店面活動** 或 **後台活動** 核取方塊。 此外，如果您使用自己的Experience PlatformWeb SDK，並因此未指定資料流ID，您仍須新增與資料流相關聯的資料集ID。 否則，您無法儲存此表單。 |
| 從 | 您要開始收集訂單歷史記錄資料的日期。 |
| 至 | 您要結束收集訂單歷史記錄資料的開始日期。 |
| 開始同步 | 開始將訂單歷史記錄資料同步至Experience Platform邊緣的程式。 如果 **[!UICONTROL Dataset ID]** 欄位空白或資料集ID無效。 |

## 確認已收集事件資料

若要確認資料是從Commerce商店收集，請使用 [Adobe Experience Platform debugger](https://experienceleague.adobe.com/docs/experience-platform/debugger/home.html) 以檢查您的Commerce網站。 確認資料正在收集後，您可以透過執行查詢來確認店面和後台事件資料是否顯示在邊緣，該查詢會從以下來源傳回資料： [您建立的資料集](overview.md#prerequisites).

1. 選取 **查詢** 在Experience Platform的左側導覽列中，按一下 [!UICONTROL Create Query].

   ![查詢編輯器](assets/query-editor.png)

1. 當查詢編輯器開啟時，輸入從資料集中選取資料的查詢。

   ![建立查詢](assets/create-query.png)

   例如，您的查詢可能如下所示：

   ```sql
   SELECT * from `your_dataset_name` ORDER by TIMESTAMP DESC
   ```

1. 查詢執行之後，結果會顯示在 **結果** 標籤，在 **主控台** 標籤。 此檢視顯示查詢的表格輸出。

   ![查詢編輯器](assets/query-results.png)

在此範例中，您會看到以下專案中的事件資料： [`commerce.productListAdds`](events.md#addtocart)， [`commerce.productViews`](events.md#productpageview)， [`web.webpagedetails.pageViews`](events.md#pageview)、等等。 此檢視可讓您驗證您的Commerce資料是否到達邊緣。

如果結果不符合您的預期，請開啟您的資料集並尋找任何失敗的批次匯入。 進一步瞭解 [疑難排解批次匯入](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/troubleshooting.html).

## 後續步驟

將Commerce資料傳送至Experience Platform邊緣時，其他Adobe Experience Cloud產品(例如Adobe Journey Optimizer)可以使用該資料。 例如，您可以設定Journey Optimizer監聽特定事件，並根據該事件資料為首次使用者或如果有捨棄的購物車時，觸發電子郵件。 瞭解如何透過以下方式擴充您的Commerce平台 [建立客戶歷程](using-ajo.md) 在Journey Optimizer中。
