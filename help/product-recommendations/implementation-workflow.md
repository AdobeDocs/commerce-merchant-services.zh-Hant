---
title: 實作工作流程
description: 了解成功實作的步驟 [!DNL Product Recommendations] 在你的店裡。
exl-id: 766e1191-0330-4515-9331-e45318539dc9
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# 實作工作流程

[!DNL Product Recommendations] 同時使用行為和目錄資料：

- 行為 — 購物者在您網站上參與的資料，例如產品檢視、新增至購物車的項目和購買。 Adobe Commerce和Adobe Sensei不會收集個人識別資訊。

- 目錄 — 產品中繼資料，例如名稱、價格和可用性。

安裝 `magento/product-recommendations module`, Adobe Sensei會匯總行為和目錄資料並建立 [!DNL Product Recommendations] 針對每個建議類型。 此 [!DNL Product Recommendations] 服務接著會將這些建議部署至您的店面。 若要協助您在店面上實作產品建議，請使用下列工作流程：

>[!NOTE]
>
> 如果您的店面是使用PWA Studio實作，請參閱 [PWA檔案](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). 如果您使用自訂前端技術，例如React或Vue JS，請了解如何 [整合](headless.md) [!DNL Product Recommendations] 進你的無頭店。

## 工作流程

1. **將資料收集部署到生產環境**

   部署 [!DNL Product Recommendations] 需要兩個主要 [資料來源](type.md):目錄和行為。 由於生產環境是擷取和分析購物者動作的唯一環境，因此盡早開始生產資料收集符合您的最佳利益。 [學習](behavioral-data.md) Adobe Sensei如何訓練機器學習模型，以產生更優質的建議。 另外，當您開始收集生產上的行為資料時，可以 [擷取建議](verify.md) 根據此生產資料，而在非生產環境中運作。 然後，您可以根據生產中收集的實際購物者資料來測試和試驗不同的建議。

   若要將資料收集部署至生產環境，您必須 [安裝和配置](install-configure.md) the [!DNL Product Recommendations] 模組 [API金鑰](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html).

   >[!TIP]
   >
   > 部署資料收集不會變更店面的外觀或購物者的體驗。 只有建立和部署建議單位，才會改變店面上的客戶體驗。 部署至生產環境之前，請務必先在非生產環境上進行測試。 此外，在自訂範本之前，請勿建立建議單位。 請參閱下一步。

1. **自訂範本以符合您的樣式**

   您的店面代表您的品牌，因此請務必修改產品建議範本以符合您的網站主題。

   >[!TIP]
   >
   > 通過自定義模板，可以指定樣式表、覆蓋建議單元在頁面上的顯示位置等。

   請參閱 [自訂](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/customize.html) 請參閱開發人員檔案，了解如何完成此步驟。

1. **在您的非生產環境上測試建議**

   在部署至生產環境之前，在非生產環境上測試新技術始終是最佳做法。 在非生產環境上測試建議可讓您播放不同的建議單元類型、定位和頁面。 您可以在非生產環境中測試時，根據已收集到的生產行為資料提取建議，以便建議結果以實際客戶的購物行為為基礎。

   >[!TIP]
   >
   > 確保您的非生產環境目錄與您在生產環境中的目錄大致相同。 使用類似的目錄可確保建議單位中傳回的產品與生產上的產品緊密相似。

   請參閱 [擷取](staging-environment.md) 生產環境的行為資料，了解如何完成此步驟。

1. **建立建議並部署至生產店面**

   現在您已在生產環境中部署行為資料收集、修改產品建議範本，並使用實際購物者行為測試建議，您就可以將所有程式碼推廣至生產環境，並 [建立](create.md) 即時產品建議。
