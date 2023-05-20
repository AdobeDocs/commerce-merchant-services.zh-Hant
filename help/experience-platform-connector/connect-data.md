---
title: 將Commerce資料連接到Adobe Experience Platform
description: 瞭解如何將您的Commerce資料連接到Adobe Experience Platform。
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: 386d5e4245401695d7123a87b7dfb703f1f849e9
workflow-type: tm+mt
source-wordcount: '1307'
ht-degree: 0%

---

# 將Commerce資料連接到Adobe Experience Platform

安裝Experience Platform連接器時，在 **系統** 菜單 **服務** 中 _管理_。

- Commerce Services連接器
- Experience Platform連接器

要將Adobe Commerce實例連接到Adobe Experience Platform，必須配置兩個連接器，從Commerce Services連接器開始，然後使用Experience Platform連接器完成。

## 更新Commerce Services連接器

如果您以前安裝過Adobe Commerce服務，則可能已配置了Commerce Services連接器。 否則，必須在 [Commerce Services連接器](../landing/saas.md) 頁：

1. 登錄到您的Commerce帳戶 [檢索您的生產和沙盒API密鑰](../landing/saas.md#credentials)。
1. 選擇 [SaaS資料空間](../landing/saas.md#saas-configuration)。
1. 登錄到Adobe帳戶 [檢索組織ID](../landing/saas.md#ims-organization-optional)。

配置Commerce Services連接器後，配置Experience Platform連接器。

## 更新Experience Platform連接器

在本節中，您使用組織ID將Adobe Commerce實例連接到Adobe Experience Platform。 然後，可以指定要發送到Experience Platform邊緣的資料類型（儲存前端或後端辦公室）。

![Experience Platform連接器配置](assets/epc-config-dc.png)

## 常規

1. 登錄到您的Adobe帳戶 [Commerce Services連接器](../landing/saas.md#organizationid) 並選擇您的組織ID。

   >[!NOTE]
   >
   >如果您以前配置了Commerce Services連接器，則可以跳過此步驟，因為您的組織ID已被選擇。

1. 在管理員中，轉到 **系統** >服務> **Experience Platform連接器**。

1. 在 **範圍** 下拉清單，將上下文設定為 **網站**。

1. 在 **組織ID** 欄位中，驗證與您的Adobe Experience Platform帳戶關聯的ID(如 [Commerce Services連接器](../landing/saas.md#organizationid)。 組織ID為全局。 每個Adobe Commerce實例只能關聯一個組織ID。

1. （可選）如果您已 [AEP Web SDK（合金）](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html) 部署到您的站點，啟用複選框並添加AEP Web SDK的名稱。 否則，將這些欄位留空，Experience Platform連接器將為您部署一個欄位。

   >[!NOTE]
   >
   >如果指定您自己的AEP Web SDK，則Experience Platform連接器將使用與該SDK關聯的資料流ID，而不是此頁上指定的資料流ID（如果有）。

## 資料收集

在本節中，您指定要發送到Experience Platform邊的資料類型。 有兩種類型的資料：客戶端和伺服器端。

客戶端資料是在儲存端捕獲的資料。 這包括購物者之間的互動，例如 `View Page`。 `View Product`。 `Add to Cart`, [申請表](events.md#b2b-events) 資訊（針對B2B商戶）。 伺服器端資料或後台辦公室資料是在Commerce伺服器中捕獲的資料。 這包括有關訂單狀態的資訊，例如訂單是否已下達、取消、退還、發運或完成。

在 **資料收集** 的子菜單。 要確保您的Adobe Commerce實例可以開始資料收集，請查看 [先決條件](overview.md#prerequisites)。

查看事件主題以瞭解有關 [店面](events.md#storefront-events) 和 [後台辦公室](events.md#back-office-events) 事件。

>[!NOTE]
>
>中的所有欄位 **資料收集** 文本 **網站** 範圍或更高。

1. 選擇 **店面事件** 的子菜單。

   >[!NOTE]
   >
   >的 **店面事件** 如果AEP Web SDK和組織ID有效，則會自動啟用複選框。

1. 選擇 **後台辦公室事件** 如果要發送訂單狀態資訊，例如訂單已下達、取消、退貨或已發運。

   >[!NOTE]
   >
   >如果選擇 **後台辦公室事件**，所有後台辦公室資料都發送到Experience Platform邊緣。 如果購物者選擇不收集資料，則必須在Experience Platform中明確設定購物者的隱私偏好。 這不同於收購者已根據購物者偏好處理同意的店面事件。 [瞭解更多資訊](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/consent/adobe/dataset.html) 在Experience Platform中設定購物者的隱私偏好。

1. 確保後台辦公室事件資料根據 [克隆](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) 工作，你必須改變 `Sales Orders Feed` 索引 `Update by Schedule`。

   1. 在 _管理_ 邊欄，轉到 **[!UICONTROL System]** > _[!UICONTROL Tools]_>**[!UICONTROL Index Management]**。

   1. 選中 `Sales Orders Feed` 索引器。

   1. 設定 **[!UICONTROL Actions]** 至 `Update by Schedule`。

   1. 如果首次啟用後台辦公室資料，請運行以下命令重新編製索引並觸發重新同步。 只要 [克隆](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) 作業設定正確。

      ```bash
      bin/magento index:reindex sales_order_data_exporter_v2
      ```

      ```bash
      bin/magento saas:resync --feed orders
      ```

1. （如果您正在使用自己的AEP Web SDK，請跳過此步驟。） [建立](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/configure.html#create) Adobe Experience Platform中的資料流，或選擇要用於收集的現有資料流。

1. （如果您正在使用自己的AEP Web SDK，請跳過此步驟。） 在 **資料流ID** 欄位，貼上該新資料流或現有資料流的ID。

## 欄位說明

| 欄位 | 說明 |
|--- |--- |
| 範圍 | 要應用配置設定的特定網站。 |
| 組織ID（全局） | 屬於購買AdobeDX產品的組織的ID。 此ID將你的Adobe Commerce實例連結到Adobe Experience Platform。 |
| AEP Web SDK是否已部署到您的站點 | 如果已將自己的AEP Web SDK部署到您的站點，請選中此複選框 |
| AEP Web SDK名稱（全局） | 如果已將Experience PlatformWeb SDK部署到您的站點，請在此欄位中指定該SDK的名稱。 這允許Storefront事件收集器和Storefront事件SDK使用您的Experience PlatformWeb SDK，而不是Experience Platform連接器部署的版本。 如果您沒有將Experience PlatformWeb SDK部署到您的站點，請將此欄位留空，Experience Platform連接器將為您部署一個。 |
| 店面事件 | 如果組織ID和資料流ID有效，則預設選中。 店面事件在顧客瀏覽你的網站時收集匿名行為資料。 |
| 後台辦公室事件 | 如果選中，則事件負載包含匿名訂單狀態資訊，例如，訂單是否被放置、取消、退還或發運。 |
| 資料流ID（網站） | 允許資料從Adobe Experience Platform流到其他AdobeDX產品的ID。 此ID必須與您特定Adobe Commerce實例中的特定網站關聯。 如果指定您自己的Experience PlatformWeb SDK，請不要在此欄位中指定資料流ID。 Experience Platform連接器使用與該SDK關聯的資料流ID，並忽略此欄位中指定的任何資料流ID（如果有）。 |

>[!NOTE]
>
>登錄後，儲存的資料開始流向Experience Platform邊緣。 後台辦公室資料在邊緣顯示大約需要5分鐘。 隨後的更新基於cron計畫在邊上可見。

## 確認已收集事件資料

要確認正在從您的Commerce儲存中收集資料，請使用 [Adobe Experience Platform調試器](https://experienceleague.adobe.com/docs/experience-platform/debugger/home.html) 查看您的商業網站。 在確認正在收集資料後，您可以通過運行一個查詢來驗證儲存前端和後台辦公室事件資料是否出現在邊緣 [建立的資料集](overview.md#prerequisites)。

1. 選擇 **查詢** 在Experience Platform的左側導航中，按一下 [!UICONTROL Create Query]。

   ![查詢編輯器](assets/query-editor.png)

1. 開啟查詢編輯器時，輸入從資料集中選擇資料的查詢。

   ![建立查詢](assets/create-query.png)

   例如，您的查詢可能如下所示：

   ```sql
   SELECT * from `your_dataset_name` ORDER by TIMESTAMP DESC
   ```

1. 運行查詢後，結果將顯示在 **結果** 頁籤 **控制台** 頁籤。 此視圖顯示查詢的表格輸出。

   ![查詢編輯器](assets/query-results.png)

在此示例中，您將看到 [`commerce.productListAdds`](events.md#addtocart)。 [`commerce.productViews`](events.md#productpageview)。 [`web.webpagedetails.pageViews`](events.md#pageview)等等。 此視圖允許您驗證您的Commerce資料是否到達邊緣。

如果結果不是您期望的結果，請開啟資料集並查找所有失敗的批處理導入。 瞭解有關 [疑難解答批處理導入](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/troubleshooting.html)。
