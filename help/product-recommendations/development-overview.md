---
title: 產品Recommendations管理員開發
description: 產品Recommendations架構和開發功能的概觀。
exl-id: caef5e0c-dd69-4846-8f85-b1c5e1c6a28f
source-git-commit: e74bc4aeaa154e751f8d986e0426dd19d55d335e
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# 產品Recommendations管理員開發

產品Recommendations是強大的行銷工具，可用來增加轉換率、增加收入並刺激購物者參與。 產品Recommendations會以單位的形式出現在店面，例如「瀏覽過此產品的客戶也瀏覽了」、「購買此產品的客戶也購買了」、「為您推薦」等。 Adobe Commerce產品Recommendations由 [Adobe Sensei](https://www.adobe.com/sensei.html)，會使用人工智慧和機器學習演演算法，對聚集的購物者資料執行深入分析。 此資料與您的Commerce目錄結合後，可為購物者提供極為引人入勝、相關且個人化的體驗。

>[!NOTE]
>
>如果您的店面是使用PWA Studio實作，請參閱 [PWA檔案](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). 如果您使用自訂前端技術（例如React或Vue JS），請參閱使用手冊以瞭解如何在中整合產品Recommendations [headless](headless.md) 環境。 Headless執行個體必須實作事件，才能支援產品推薦工作區。

## 架構概觀

從高層面來看，商務產品Recommendations部署為SaaS。 Commerce端包括店面（其中包含事件收集器和建議版面配置範本）和後端（其中包含資料服務、SaaS匯出模組和管理UI）。 Adobe Sensei智慧服務可在SaaS端運用。

![產品推薦架構圖](assets/arch-diag-sensei.svg)

安裝及設定建議模組後，您的店面就會開始收集行為資料。 Adobe Sensei會處理此行為資料與您的目錄資料，並計算Recommendations服務所利用的產品關聯。 此時，商家可以直接從管理員UI建立、管理產品推薦單位，並將其部署至店面。

## 資料型別

產品Recommendations需要下列資料：

- **行為**  — 購物者在您網站上的參與度資料，例如產品檢視、新增到購物車的商品和購買。 Commerce和Adobe Sensei不會收集個人識別資訊。

- **目錄**  — 產品中繼資料，例如名稱、價格、可用性等。

當您安裝 `magento/product-recommendations` 模組，Adobe Sensei會彙總行為和目錄資料，並為每種建議型別建立產品Recommendations。 然後，產品Recommendations服務會將這些建議部署至您的店面。

## 後續步驟

請閱讀下列主題，以開始使用產品Recommendations：

- [如何實作產品Recommendations](implementation-workflow.md)

- [安裝及設定產品Recommendations](install-configure.md)

- [建立產品Recommendations](create.md)
