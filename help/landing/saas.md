---
title: 商務服務聯結器
description: 瞭解如何使用生產和沙箱API金鑰將您的Adobe Commerce或Magento Open Source執行個體整合到服務。
exl-id: 28027a83-449b-4b96-b926-a7bfbfd883d8
source-git-commit: 506b00e72d65fbafa071476608bb658cb59404b4
workflow-type: tm+mt
source-wordcount: '862'
ht-degree: 0%

---

# [!DNL Commerce Services Connector]

部分Adobe Commerce和Magento Open Source功能由以下提供技術支援 [!DNL Commerce Services]  並部署為SaaS （軟體即服務）。 若要使用這些服務，您必須將 [!DNL Commerce] 使用生產和沙箱API金鑰的例項，並在 [設定](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html). 您只需要設定一次。

## 可用服務 {#availableservices}

以下列出 [!DNL Commerce] 您可透過存取的功能 [!DNL Commerce Services Connector]：

| 服務 | 可用性 |
| ---|--- |
| [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) 由Adobe Sensei提供 | Adobe Commerce |
| [[!DNL Live Search]](/help/live-search/overview.md) 由Adobe Sensei提供 | Adobe Commerce |
| [[!DNL Payment Services]](/help/payment-services/overview.md) | Adobe Commerce和Magento Open Source |
| [[!DNL Channel Manager]](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/intro-to-channel-manager/overview.html) | Adobe Commerce和Magento Open Source |
| [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html) | Adobe Commerce |
| [[!DNL Catalog Service]](/help/catalog-service/overview.md) | Adobe Commerce |
| [Experience Platform聯結器](/help/experience-platform-connector/overview.md) | Adobe Commerce |

## 架構

從高層面來看， [!DNL Commerce Services Connector] 由下列核心元素組成：

![Commerce Services聯結器架構](assets/saas-config-sync-workflow.png)

以下各節會更詳細地討論這些元素。

## 認證 {#apikey}

生產和沙箱API金鑰產生自 [!DNL Commerce] 授權持有者的帳戶，以唯一識別碼 [!DNL Commerce] ID (MageID)。 若要通過服務的軟體權利檔案驗證，例如 [!DNL Product Recommendations] 或 [!DNL Live Search]，商家組織的授權擁有者只要帳戶處於良好狀態，即可產生API金鑰集。 這些金鑰可在「須知」基礎上與系統整合商或代表授權持有者管理專案和環境的開發團隊分享。 此外，解決方案整合經銷商也有權使用 [!DNL Commerce Services]. 如果您是解決方案整合商， [!DNL Commerce] 合作夥伴合約應該產生API金鑰。

### 產生生產和沙箱API金鑰 {#genapikey}

1. 登入您的 [!DNL Commerce] 帳戶位置 [https://account.magento.com](https://account.magento.com/){：target=&quot;_blank&quot;}。

1. 在 **Magento** 索引標籤，選取 **api入口網站** 在側邊欄上。

1. 從 _環境_ 功能表，選取 **生產** 或 **Sandbox**.

1. 在中輸入名稱 _API金鑰_ 區段並按一下 **新增**.

   這會開啟對話方塊，供您下載新金鑰。

   ![下載私密金鑰](assets/download-api-private-key.png)

   >[!WARNING]
   >
   > 這是您必須複製或下載金鑰的唯一機會。

1. 按一下 **下載** 然後按一下 **取消**.

1. 對每個環境（生產和沙箱）重複上述步驟。

   此 **API金鑰** 區段現在會顯示您的API金鑰。 當您執行以下動作時，需要生產金鑰和沙箱金鑰 [選取或建立SaaS專案](#createsaasenv).

## SaaS設定 {#saasenv}

[!DNL Commerce] 執行個體必須設定一個SaaS專案和一個SaaS資料空間，以便 [!DNL Commerce Services] 可將資料傳送至正確的位置。 SaaS專案會將所有SaaS資料空間分組。 SaaS資料空間用於收集和儲存資料，以便 [!DNL Commerce Services] 才能運作。 其中部分資料可從匯出。 [!DNL Commerce] 例項和部分可從店面的購物者行為中收集。 然後，這些資料會持續儲存以保護雲端儲存空間。

對象 [!DNL Product Recommendations]，SaaS資料空間包含目錄和行為資料。 您可以指向 [!DNL Commerce] 執行個體到SaaS資料空間，依據 [選取它](https://docs.magento.com/user-guide/configuration/services/saas.html) 在 [!DNL Commerce] 設定。

>[!WARNING]
>
> 只在生產環境中使用您的生產SaaS資料空間 [!DNL Commerce] 安裝以避免資料衝突。 否則，您可能會用測試資料汙染生產網站資料，從而導致部署延遲。 例如，中繼資料（例如中繼URL）可能會錯誤地覆寫您的生產產品資料。

### 選取或建立SaaS專案 {#createsaasenv}

>[!NOTE]
>
> 如果您沒有看到 **[!UICONTROL Commerce Services Connector]** 中的區段 [!DNL Commerce] 設定，您必須安裝 [!DNL Commerce] 符合您需求的模組 [[!DNL Commerce] 服務](#availableservices).

若要選取或建立SaaS專案，請要求 [!DNL Commerce] 來自的API金鑰 [!DNL Commerce] 您商店的授權持有人。

1. 於 _管理員_ 側欄，前往 **系統** >服務> **商務服務聯結器**.

1. 在 _沙箱API金鑰_ 和 _生產API金鑰_ 區段，貼上您的金鑰值。

   私密金鑰必須包括 `----BEGIN PRIVATE KEY---` 在索引鍵的開頭和 `----END PRIVATE KEY----` 位於私密金鑰結尾。

1. 按一下 **儲存**.

任何與您的金鑰相關聯的SaaS專案都會顯示在 **專案** 中的欄位 **SaaS識別碼** 區段。

1. 如果沒有SaaS專案，請按一下 **建立專案**. 然後在 **專案** 欄位中，輸入SaaS專案的名稱。

   建立SaaS專案時， [!DNL Commerce] 會根據您的環境產生一或多個SaaS資料空間 [!DNL Commerce] 授權：
   - Adobe Commerce — 一個生產資料空間；兩個測試資料空間
   - Magento Open Source — 一個生產資料空間；無測試資料空間

1. 選取 **資料空間** 用於目前的設定 [!DNL Commerce] 商店。

>[!WARNING]
>
> 如果您在「我的帳戶」的「API入口網站」區段中產生新金鑰，請立即更新「管理員」設定中的API金鑰。 如果您在管理員中產生新金鑰但未更新金鑰，您的SaaS擴充功能將無法繼續運作，而您會遺失寶貴資料。

若要變更SaaS專案或資料空間名稱，請按一下 **重新命名**.

## IMS組織（選用） {#organizationid}

若要將您的Adobe Commerce執行個體連結至Adobe Experience Platform，請使用您的Adobe ID登入您的Adobe帳戶。 登入後，與您的Adobe帳戶相關聯的IMS組織會顯示在此區段中。

## 目錄同步

當您的 [!DNL Commerce] 執行個體已成功連線到 [!DNL Commerce Services]時，目錄同步程式會從您的伺服器匯出產品資料， [!DNL Commerce] 伺服器至 [!DNL Commerce Services]. 目前，只有產品Recommendations使用目錄同步服務。 [瞭解更多](catalog-sync.md) 關於目錄同步程式。
