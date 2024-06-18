---
title: '邊界和限制'
description: 瞭解的界限和限制 [!DNL Live Search] 以確保符合您的業務需求。
role: Admin, Developer
exl-id: ad6737f9-6ecd-4d82-89e7-d95425e4ba53
source-git-commit: 0a54c1715b076a7dea70632fcffeacc7de517760
workflow-type: tm+mt
source-wordcount: '698'
ht-degree: 0%

---

# 邊界和限制

在網站搜尋方面，Adobe Commerce會提供您選項。 請檢閱下列邊界和限制，以確保 [!DNL Live Search] 和 [!DNL Catalog Service] 符合您的業務需求。 如果您需要進階搜尋功能，例如內容搜尋、自備演演算法(BYOA)或屬性型銷售，請考慮使用協力廠商搜尋解決方案。

## 一般

- 此 [進階搜尋](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) 模組停用時機 [!DNL Live Search] 已安裝，且店面頁尾中的進階搜尋連結已移除。
- [層級定價](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-tier) 和 [特殊定價](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-special) 不支援 [!DNL Live Search] 欄位與產品清單頁面Widget。
- 產品價格不含增值稅(VAT)。
- 不支援內容搜尋。
- 可分頁的產品上限為10,000件。
- 搜尋配接卡不支援使用自訂來源模型建立並當作Facet使用的產品屬性。 若要支援此功能，您必須使用 [產品清單頁面Widget](plp-styling.md).

## 索引

- [!DNL Live Search] [索引](indexing.md) 每個商店檢視最多總共450個產品屬性。 其分佈如下：
   - 50個可排序屬性
   - 200個可篩選屬性
   - 200個可搜尋屬性
- [!DNL Live Search] 僅索引Adobe Commerce資料庫中的產品。
- CMS頁面未編制索引。
- SKU、名稱和類別屬性預設可搜尋，且無法從搜尋中排除。 如果您不打算將產品歸入這些類別，請務必從這些類別中取消指派產品。

## Facet

- 最多可以將100個屬性設定為Facet，這些屬性來自可以編制索引的200個可篩選屬性。
- 在一個Facet中，最多可傳回30個值區。 如果需要傳回30個以上的貯體， [建立支援票證](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) 因此，Adobe可以分析效能影響，並判斷為您的環境提高此限制是否可行。
- 動態Facet可能會在大型索引和高序數的索引中造成效能問題。 如果您已建立動態Facet，且發現任何效能降低或頁面未載入時發生逾時錯誤，請嘗試將您的Facet變更為Pined ，以判斷這是否會解決您的效能問題。
- 庫存狀態(`quantity_and_stock_status`)不支援當作Facet。 您可以使用 `inStock: 'true'` 以篩選出無庫存的產品。 這在中可立即使用 `LiveSearchAdapter` 模組（當「顯示無庫存產品」設定為「True」） [!DNL Commerce] 管理員。
- 日期型別屬性不支援為Facet。

## 查詢

- [!DNL Live Search] 使用唯一 [GraphQL端點](https://developer.adobe.com/commerce/services/graphql/live-search/) 用於支援「動態Faceting」和「依型別搜尋」等功能的查詢。 雖然與 [GRAPHQL API](https://developer.adobe.com/commerce/webapi/graphql/)存在一些差異，並且某些欄位可能不完全相容。
- 搜尋查詢中可傳回的結果數量上限為10,000。
- 無法使用日期型別屬性來篩選結果。

## 規則

- 搜尋銷售的最大數量 [規則](rules.md) 每個商店檢視為50個。
- 類別銷售在每個類別中可以有一個規則。
- 每個規則的條件數上限為10。
- 每個規則的事件數上限為25。

## 同義字

- [!DNL Live Search] 最多可管理200個 [同義字](synonyms.md) 每個商店檢視。
- 每個商店檢視的多字同義字限製為20個。

## 類別銷售

- 可以為每個商店檢視為每個類別建立一個規則。 每個規則可以具有：
   - 最多10個條件
   - 最多25個事件

## B2B和類別許可權

- 產品若未新增至預設共用目錄，則不會顯示。
- 若要使用「型錄」許可權限制客戶群組，請執行下列動作：
   - 必須將產品指派給根類別。
   - 必須向「未登入」客戶群組提供「允許」瀏覽許可權。
   - 若要將產品限制在「未登入」客戶群組，請移至每個類別，並為每個客戶群組設定許可權。
- 目前不支援使用「即時搜尋」PWA Studio的B2B。
- 中的類別Facet [!DNL Live Search] 可能會顯示無法顯示給特定客戶群組的類別。

## [!DNL Storefront popover]

- 此 [[!DNL popover]](storefront-popover.md) 僅適用於使用 *Luma* 佈景主題，或根據此佈景主題的自訂佈景主題 *Luma*. 搜尋結果頁面上的階層連結不會 *Luma* 樣式。
- 此 [!DNL popover] 不支援 *空白* 主題。
- 此 [!DNL popover] 不支援快速訂購表單。
- 不支援願望清單和產品比較。
