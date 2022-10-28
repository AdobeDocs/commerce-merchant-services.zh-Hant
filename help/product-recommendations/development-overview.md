---
title: 產品Recommendations管理員開發
description: 概略介紹產品Recommendations架構和開發功能。
source-git-commit: 81ab2e22b0ec81e97d27ee135c88b50731a3986d
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# 產品Recommendations管理員開發

產品Recommendations是功能強大的行銷工具，可用來增加轉換、增加收入及刺激購物者參與。 產品Recommendations會以「瀏覽過此產品的客戶也瀏覽過」、「購買此產品的客戶也購買過」、「為您建議」等單位呈現在店面上。 Adobe Commerce產品Recommendations由 [Adobe Sensei](https://www.adobe.com/sensei.html)，它使用人工智慧和機器學習演算法，對匯整的購物者資料執行深入分析。 此資料與您的商務目錄結合後，可為購物者提供高度吸引人、相關且個人化的體驗。

>[!NOTE]
>
>如果您的店面是使用PWA Studio實作，請參閱 [PWA檔案](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). 如果您使用自訂前端技術，例如React或Vue JS，請參閱使用手冊，了解如何將產品Recommendations整合至 [無頭](headless.md) 環境。

## 架構概觀

從高層面講，Commerce Product Recommendations部署為SaaS。 商務端包括店面（包含事件收集器和建議配置模板）和後端（包括資料服務、SaaS導出模組和管理員UI）。 Adobe Sensei情報服務在SaaS端得到利用。

![產品建議架構圖](assets/arch-diag-sensei.svg)

安裝並設定建議模組後，您的店面就會開始收集行為資料。 Adobe Sensei會處理此行為資料與您的目錄資料，並計算recommendations服務運用的產品關聯。 此時，商家可以直接從管理員UI建立、管理產品建議單位，並將其部署至店面。

## 資料類型

產品Recommendations需要下列資料：

- **行為**  — 購物者在您網站上參與的資料，例如產品檢視、新增至購物車的項目和購買。 商務和Adobe Sensei不會收集個人識別資訊。

- **目錄**  — 產品中繼資料，例如名稱、價格、可用性等。

安裝 `magento/product-recommendations` 模組，Adobe Sensei會匯總行為和目錄資料，並針對每個建議類型建立產品Recommendations。 產品Recommendations服務接著會將這些建議部署至您的店面。

## 後續步驟

請參閱下列主題以開始使用產品Recommendations:

- [如何實作產品Recommendations](implementation-workflow.md)

- [安裝及設定產品Recommendations](install-configure.md)

- [建立產品Recommendations](create.md)
