---
title: 產品Recommendations管理員開發
description: 產品Recommendations架構和開發功能的概觀。
exl-id: caef5e0c-dd69-4846-8f85-b1c5e1c6a28f
source-git-commit: 4a5c3550b03651279c24de6b6361ffa6dc28776e
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# 產品Recommendations管理員開發

產品Recommendations是強大的行銷工具，可用來增加轉換次數、增加收入及刺激購物者參與。 產品Recommendations會以單位的形式出現在商店中，例如「檢視過此產品的客戶也檢視過」、「購買此產品的客戶也購買過」、「為您推薦」等。 Adobe Commerce產品Recommendations由[Adobe Sensei](https://www.adobe.com/sensei.html)提供技術支援，其使用人工智慧和機器學習演演算法來對彙總的購物者資料執行深入分析。 此資料與您的Commerce目錄結合後，可為購物者提供極為引人入勝、相關且個人化的體驗。

>[!NOTE]
>
>如果店面是使用PWA Studio實作，請參閱[PWA檔案](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/)。 如果您使用自訂前端技術，例如React或Vue JS，請參閱使用指南以瞭解如何在[headless](headless.md)環境中整合產品Recommendations。 Headless執行個體必須實作事件，才能支援產品推薦工作區。

## 架構概觀

從高層面來看，Commerce產品Recommendations部署為SaaS。 Commerce端包括店面（其中包含事件收集器和建議版面配置範本）和後端（其中包含資料服務、SaaS匯出模組和管理UI）。 Adobe Sensei情報服務會在SaaS端運用。

![產品建議架構圖](assets/arch-diag-sensei.svg)

安裝及設定建議模組後，您的店面就會開始收集行為資料。 Adobe Sensei會處理此行為資料與目錄資料，並計算Recommendations服務所利用的產品關聯。 此時，商家可以直接從管理UI建立、管理產品推薦單位，並將其部署至店面。

## 後續步驟

請閱讀下列主題，以開始使用產品Recommendations：

- [如何實作產品Recommendations](implementation-workflow.md)

- [安裝及設定產品Recommendations](install-configure.md)

- [建立產品Recommendations](create.md)
