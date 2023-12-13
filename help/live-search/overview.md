---
title: 簡介 [!DNL Live Search]
description: '"[!DNL Live Search] Adobe Commerce提供超快、超相關和直覺式的搜尋體驗。」'
exl-id: aca0ef19-ead1-4c79-90c3-db5ec48cb3c1
recommendations: noCatalog
source-git-commit: 9460d7cf2de677557ee3792665c65d2a52a52569
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---

# 簡介 [!DNL Live Search]

[!DNL Live Search] 是一項適用於Adobe Commerce的服務，可取代標準搜尋功能。 此 [!DNL Live Search] 模組已與Composer一起安裝，並連線 [!DNL Commerce] 安裝至 [!DNL Live Search] [服務](../landing/saas.md). 設定後，預設搜尋文字欄位會取代為 [!DNL Live Search] 文字欄位。 [!DNL Live Search] 也會安裝產品清單頁面(PLP) Widget，在瀏覽搜尋結果時提供強大的篩選功能。

[!DNL Live Search] 顯示在 *行銷* 下的選單 *SEO與搜尋* 在 [!DNL Commerce] *管理員*.

架構的Adobe Commerce端包含託管搜尋 *管理員*，同步目錄資料，以及執行查詢服務。 晚於 [!DNL Live Search] 安裝與設定完成時，Adobe Commerce會開始與SaaS服務共用搜尋和目錄資料。 此時，管理員使用者可以設定、自訂及管理搜尋 [Facet](facets.md)， [同義字](synonyms.md)、和 [銷售規則](category-merch.md).

## Live Search元件

* [!DNL Live Search] [彈出視窗Widget](storefront-popover.md) 是在包含搜尋結果的搜尋欄位下開啟的方塊。
* [產品清單頁面Widget](plp-styling.md) 提供可搜尋的產品清單頁面，支援多面向和同義字。
* AEM CIF元件： [彈出視窗Widget](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/live-search-popover.html?lang=en) 和 [PLP Widget](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/live-search-plp.html) 允許AEM網站利用 [!DNL Live Search].
* [[!DNL Live Search] 管理員](workspace.md) 是設定規則、多面向和同義字的位置。

## 工作流程概觀

[!DNL Live Search] 的運作方式是將目錄資料移至Adobe Commerce SaaS基礎結構，並建立索引，以便根據使用者型別快速提供搜尋結果。

### 1.安裝

[!DNL Live Search] 是 [已安裝](install.md) 至您的Adobe Commerce執行個體，透過 [作曲者](https://getcomposer.org/). 這會安裝連線至服務的必要模組，並設定Commerce執行個體以覆寫預設搜尋欄位。 此外也會安裝設定服務的Commerce管理選項。

### 2.同步資料

[!DNL Live Search] 將目錄資料移至Adobe的SaaS基礎結構。 資料會編制索引，而搜尋結果會從此索引直接傳送到店面。 根據大小和複雜性，索引可能需要30分鐘到數小時的時間。

### 3.設定資料

正確設定您的產品資料可確保為您的客戶帶來良好的搜尋結果。 需要執行數個設定步驟：指派類別和設定屬性。

#### 指派類別

產品傳回 [!DNL Live Search] 必須指派給 [類別](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/categories.html). 例如，在Luma中，產品分為「男性」、「女性」和「齒輪」等類別。 也會為「Top」、「Bottoms」和「Watch」設定子類別。 這可提供更精細的篩選粒度。

#### 可搜尋和可篩選的欄位

已指派產品 [屬性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) 可用於搜尋和篩選的規則。 屬性包括「顏色」、「尺寸」、「材質型別」等。 透過這些屬性，使用者可以尋找「綠色頂端」。 每個產品可能有許多在Commerce管理員中定義的屬性。

每一個屬性都可以定義為 [&quot;searchable&quot;](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html) 在管理員中。 當設為「可搜尋」時，這些屬性便可供搜尋 [!DNL Live Search].

[Facet](facets.md) 是在中定義的產品屬性 [!DNL Live Search] 可篩選。 任何可篩選的屬性都可以設定為Facet於 [!DNL Live Search] 但一次可以搜尋的面向數量存在限制。

[同義字](synonyms.md) 是您可以定義的術語，以協助引導使用者使用正確的產品。 尋找褲子的使用者可能會輸入「trousers」或「slacks」。 您可以設定同義字，讓這些搜尋詞將使用者帶到「褲子」結果。

## [!DNL Live Search] 工作區

此 [!DNL Live Search] [工作區](workspace.md) 是管理員中您設定的 [!DNL Live Search] 同義字、多面向和類別銷售等功能。

## 活動

[!DNL Live Search] 使用 [事件](events.md) 以計算 [智慧型銷售](category-merch.md) 和 [績效](performance.md) 控制面板。 事件會隨預設實施提供。 Headless店面事件應手動啟用。

## 自訂Widget

大部分的店舖擁有者會想要確保 [!DNL Live Search] Widget符合其商店外觀和風格。

您可以視需要定義自訂CSS規則，以設定彈出視窗和PLP Widget的樣式。 另請參閱 [樣式彈出視窗元素](storefront-popover-styling.md) 和 [產品清單頁面Widget](plp-styling.md).

如果您想要擴充Widget的功能，每個元件的原始碼都可在公用存放庫中取得。
在此案例中，您可以根據自己的需求自訂JavaScript，然後在您的網站上託管您的自訂程式碼。 此自訂指令碼會與 [!DNL Live Search] 並傳回正常結果，讓您控制Widget的功能。

* [PLP Widget存放庫](https://github.com/adobe/storefront-product-listing-page)
* [搜尋列存放庫](https://github.com/adobe/storefront-search-as-you-type)

取得更多關於以下內容的詳細資訊： [!DNL Live Search] 在 [技術概覽](technical-overview.md).

## [!DNL Live Search] 示範

觀看此影片以瞭解 [!DNL Live Search]：

>[!VIDEO](https://video.tv.adobe.com/v/3418679?quality=12&learn=on)

如需有關如何使用和設定「即時搜尋」的更深入影片，請參閱 [完整示範： [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/marketing/live-search-full-demonstration.html) 主題。
