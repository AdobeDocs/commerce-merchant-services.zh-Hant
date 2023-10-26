---
title: 簡介 [!DNL Live Search]
description: '"[!DNL Live Search] Adobe Commerce提供超快、超相關和直覺式的搜尋體驗。」'
exl-id: aca0ef19-ead1-4c79-90c3-db5ec48cb3c1
recommendations: noCatalog
source-git-commit: 3352bd1390704646f4c21599ebf204eda2e1488c
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# 簡介 [!DNL Live Search]

[!DNL Live Search] 是一項適用於Adobe Commerce的服務，可取代標準搜尋功能。 此 [!DNL Live Search] 模組已與Composer一起安裝，並連線 [!DNL Commerce] 安裝至 [!DNL Live Search] [服務](../landing/saas.md). 設定後，預設搜尋文字欄位會取代為 [!DNL Live Search] 文字欄位。

[!DNL Live Search] 顯示在 *行銷* 下的選單 *SEO與搜尋* 在 [!DNL Commerce] *管理員*.

架構的Adobe Commerce端包含託管搜尋 *管理員*，同步目錄資料，以及執行查詢服務。 晚於 [!DNL Live Search] 安裝與設定完成時，Adobe Commerce會開始與SaaS服務共用搜尋和目錄資料。 此時，管理員使用者可以設定、自訂及管理搜尋 [Facet](facets.md)， [同義字](synonyms.md)、和 [銷售規則](category-merch.md).

![即時搜尋架構圖](assets/architecture-diagram.svg)

## Live Search元件

* [!DNL Live Search] [彈出視窗](storefront-popover.md) 是在包含搜尋結果的搜尋欄位下開啟的方塊。
* [產品清單頁面Widget](plp-styling.md) 提供可搜尋的產品清單頁面，支援多面向和同義字。
* AEM CIF元件： [彈出視窗Widget](https://github.com/adobe/aem-cif-guides-venia/pull/319) 和 [PLP Widget](https://github.com/adobe/aem-cif-guides-venia/pull/320) 允許AEM網站利用 [!DNL Live Search].
* [[!DNL Live Search] 管理員](workspace.md) 是設定規則、多面向和同義字的位置。
* Search Adapter為的預設實作 [!DNL Live Search].

## [!DNL Live Search] 示範

觀看此影片以瞭解 [!DNL Live Search]：

>[!VIDEO](https://video.tv.adobe.com/v/3418679?quality=12&learn=on)

如需有關如何使用和設定「即時搜尋」的更深入影片，請參閱 [完整示範： [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/marketing/live-search-full-demonstration.html) 主題。
