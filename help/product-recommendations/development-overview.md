---
title: 產品Recommendations管理員開發
description: 產品Recommendations體系結構和開發功能概述。
exl-id: caef5e0c-dd69-4846-8f85-b1c5e1c6a28f
source-git-commit: e74bc4aeaa154e751f8d986e0426dd19d55d335e
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# 產品Recommendations管理員開發

產品Recommendations是一個強大的營銷工具，您可以用它來增加轉換、增加收入和刺激購物者的參與。 產品Recommendations以「查看此產品的客戶也查看」、「購買此產品的客戶也購買」、「推薦給您」等單位形式出現在店面。 Adobe Commerce產品Recommendations由 [Adobe Sensei](https://www.adobe.com/sensei.html)它利用人工智慧和機器學習算法對聚集的購物者資料進行深入分析。 這些資料與您的Commerce目錄結合後，將為購物者帶來高度吸引力、相關性和個性化的體驗。

>[!NOTE]
>
>如果您的店面是使用PWA Studio實現的，請參閱 [PWA文檔](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/)。 如果您使用自定義前端技術（如React或Vue JS），請參閱使用手冊瞭解如何將產品Recommendations整合到 [頭](headless.md) 環境。 無頭實例必須實施事件以為「產品建議」工作區供電。

## 體系結構概述

在高層， Commerce ProductRecommendations部署為SaaS。 商務端包括儲存端，其中包含事件收集器和建議佈局模板；後端包括資料服務、SaaS導出模組和管理員UI。 Adobe Sensei的情報服務在SaaS一方得到利用。

![產品建議體系結構圖](assets/arch-diag-sensei.svg)

一旦安裝和配置了建議模組，您的儲存將開始收集行為資料。 Adobe Sensei處理此行為資料以及目錄資料，並計算建議服務利用的產品關聯。 此時，商戶可以直接從管理員UI建立、管理產品推薦單元並將其部署到其店面。

## 資料類型

產品Recommendations需要以下資料：

- **行為**  — 站點上購物者訂購的資料，如產品視圖、添加到購物車的物品和購買。 商業和Adobe Sensei不收集個人身份資訊。

- **目錄**  — 產品元資料，如名稱、價格、可用性等。

安裝 `magento/product-recommendations` 模組，Adobe Sensei聚合行為和目錄資料，為每個推薦類型建立產品Recommendations。 然後產品Recommendations服務會將這些建議部署到您的店面。

## 後續步驟

閱讀以下主題以開始使用產品Recommendations:

- [如何實施產品Recommendations](implementation-workflow.md)

- [安裝和配置產品Recommendations](install-configure.md)

- [建立產品Recommendations](create.md)
