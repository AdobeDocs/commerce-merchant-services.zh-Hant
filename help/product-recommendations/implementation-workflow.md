---
title: 實施工作流
description: 瞭解成功實施的步驟 [!DNL Product Recommendations] 在你的店面。
exl-id: 766e1191-0330-4515-9331-e45318539dc9
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# 實施工作流

[!DNL Product Recommendations] 同時使用行為和目錄資料：

- 行為 — 來自您站點上購物者預訂的資料，如產品視圖、添加到購物車的物品和購買。 Adobe Commerce和Adobe Sensei不收集個人身份資訊。

- 目錄 — 產品元資料，如名稱、價格和可用性。

安裝 `magento/product-recommendations module`,Adobe Sensei聚合行為和目錄資料並建立 [!DNL Product Recommendations] 為每個建議類型。 的 [!DNL Product Recommendations] 然後將這些建議部署到您的店面。 要幫助您在店面上實施產品建議，請使用以下工作流：

>[!NOTE]
>
> 如果您的店面是使用PWA Studio實現的，請參閱 [PWA文檔](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/)。 如果您使用自定義前端技術（如React或Vue JS），請瞭解如何 [整合](headless.md) [!DNL Product Recommendations] 進你的無頭店。

## 工作流

1. **將資料收集部署到生產**

   部署 [!DNL Product Recommendations] 需要兩個主 [資料源](type.md):目錄和行為。 因為生產是捕獲和分析購物者行為的唯一環境，所以盡早開始收集生產資料符合您的最大利益。 [學習](behavioral-data.md) Adobe Sensei如何訓練機器學習模型，從而得到更高質量的建議。 作為附加優勢，當您開始收集生產上的行為資料時，您可以 [提取建議](verify.md) 在非生產環境中運行時基於此生產資料。 然後，您可以test和試驗不同的建議，這些建議是根據生產中收集的真實購物者資料計算的。

   要將資料收集部署到生產，您必須 [安裝和配置](install-configure.md) 這樣 [!DNL Product Recommendations] 模組 [API密鑰](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html)。

   >[!TIP]
   >
   > 部署資料收集不會更改店面的外觀或購物者的體驗。 只有建立和部署推薦單元才能改變您店面的客戶體驗。 在部署到生產環境之前，請確保在非生產環境中test。 此外，在自定義模板之前不要建立建議單元。 請參閱下一步。

1. **自定義模板以匹配樣式**

   您的店面代表您的品牌，因此請確保修改產品推薦模板以匹配您的網站主題。

   >[!TIP]
   >
   > 通過自定義模板，可以指定樣式表、覆蓋建議單元在頁面上的顯示位置等。

   請參閱 [自定義](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/customize.html) 以瞭解如何完成此步驟。

1. **Test關於非生產環境的建議**

   在部署到生產環境之前，先在非生產環境中test新技術，這始終是一種最佳做法。 在非生產環境上測試建議允許您播放不同的建議單元類型、定位和頁面。 您可以根據在非生產環境中測試時收集到的生產行為資料來提取建議，以便建議結果基於實際客戶的購物行為。

   >[!TIP]
   >
   > 確保您的非生產環境目錄與您在生產環境中的目錄大致相同。 使用類似的目錄可確保在推薦單元中返回的產品與生產上的產品緊密相仿。

   請參閱 [獲取](staging-environment.md) 從生產環境中獲取行為資料，以瞭解如何完成此步驟。

1. **建立建議並將其部署到生產庫**

   現在，您已在生產中部署了行為資料收集、修改了產品建議模板，並使用實際購物者行為測試了建議，您已準備好將所有代碼推廣到生產和 [建立](create.md) 即時產品建議。
