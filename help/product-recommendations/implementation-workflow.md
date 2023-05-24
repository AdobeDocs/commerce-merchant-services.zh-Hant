---
title: 實作工作流程
description: 瞭解成功實作的步驟 [!DNL Product Recommendations] 在店面。
exl-id: 766e1191-0330-4515-9331-e45318539dc9
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# 實作工作流程

[!DNL Product Recommendations] 同時使用行為和目錄資料：

- 行為 — 購物者在您網站上的參與度資料，例如產品檢視、新增到購物車的專案以及購買。 Adobe Commerce和Adobe Sensei不會收集個人識別資訊。

- 目錄 — 產品中繼資料，例如名稱、價格和可用性。

當您安裝 `magento/product-recommendations module`，Adobe Sensei會彙總行為和目錄資料並建立 [!DNL Product Recommendations] 適用於每種建議型別。 此 [!DNL Product Recommendations] 然後將這些建議部署至您的店面。 為協助您在店面實作產品推薦，請使用以下工作流程：

>[!NOTE]
>
> 如果您的店面是使用PWA Studio實作，請參閱 [PWA檔案](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). 如果您使用自訂前端技術，例如React或Vue JS，請瞭解如何 [整合](headless.md) [!DNL Product Recommendations] 進入您的headless店面。

## 工作流程

1. **將資料收集部署至生產環境**

   部署 [!DNL Product Recommendations] 需要兩個主要 [資料來源](type.md)：目錄和行為。 由於生產是擷取和分析購物者動作的唯一環境，因此儘早在生產上開始資料收集最符合您的利益。 [瞭解](behavioral-data.md) Adobe Sensei如何訓練產生更高品質推薦的機器學習模型。 另外一項好處是，當您開始在生產環境中收集行為資料時，可以 [擷取建議](verify.md) 根據此生產資料，而在非生產環境中作業時。 接著，您可以測試和實驗根據生產環境中收集的實際購物者資料計算而來的不同建議。

   若要將資料收集部署至生產環境，您必須 [安裝與設定](install-configure.md) 此 [!DNL Product Recommendations] 模組，提供 [API金鑰](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html).

   >[!TIP]
   >
   > 部署資料彙集不會變更店面外觀或購物者的體驗。 只有建立和部署建議單位，才能改變店面的客戶體驗。 請務必先在非生產環境中進行測試，然後再部署到生產環境。 此外，在自訂範本之前，請勿建立建議單位。 請參閱下一個步驟。

1. **自訂範本以符合您的樣式**

   您的店面代表您的品牌，因此請務必修改產品推薦範本以符合您的網站主題。

   >[!TIP]
   >
   > 透過自訂範本，您可以指定樣式表、覆寫建議單位在頁面上的顯示位置等。

   另請參閱 [自訂](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/customize.html) ，瞭解如何完成此步驟。

1. **在您的非生產環境中測試建議**

   在將技術部署到生產環境之前，最好的做法是在非生產環境中測試新技術。 在非生產環境中測試建議可讓您使用不同的建議單位型別、位置和頁面。 您可以在非生產環境中進行測試時，根據生產上已收集的行為資料提取建議，讓建議結果以實際客戶的購物行為為基礎。

   >[!TIP]
   >
   > 確保您的非生產環境目錄與生產環境中的目錄大致相同。 使用類似的目錄，可確保建議單位中傳回的產品與生產時的產品極為相似。

   另請參閱 [擷取](staging-environment.md) 生產環境中的行為資料，以瞭解如何完成此步驟。

1. **建立建議並部署至您的生產店面**

   現在您已在生產環境中部署行為資料收集、修改產品建議範本，以及使用實際購物者行為來測試建議，您已準備好將所有程式碼提升至生產環境並 [建立](create.md) 即時產品推薦。
