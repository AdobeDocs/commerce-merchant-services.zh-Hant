---
title: '[!DNL Live Search]個事件'
description: 瞭解事件如何收集 [!DNL Live Search]的資料。
feature: Services, Eventing
exl-id: b0c72212-9be0-432d-bb8d-e4c639225df3
source-git-commit: 0d966c8dbd788563fa453912961fdc62a5a6c23e
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# [!DNL Live Search]個事件

[!DNL Live Search]會使用事件來增強搜尋演演算法，例如「檢視次數最多」和「已檢視這個專案，已檢視那個專案」。 雖然LUMA使用者可立即使用事件，但Headless和其他自訂實作仍必須根據自己的需求實作事件。

由於[!DNL Live Search]和[!DNL Product Recommendations]使用相同的後端演演算法，因此某些事件會由這兩個服務共用。 有些產品Recommendations事件需要填入Recommendations控制面板。

此表格說明[!DNL Live Search]策略使用的事件。

| 策略 | 產品 | 活動 | 頁面 |
| --- | --- | --- | ---|
| 檢視次數最多 | 即時搜尋<br>產品記錄 | 頁面檢視<br>產品檢視 | 產品詳細資料頁面 |
| 購買最多 | 即時搜尋<br>產品記錄 | 頁面檢視<br>完成簽出 | 購物車/結帳 |
| 加入購物車次數最多 | 即時搜尋<br>產品記錄 | 頁面檢視<br>加入購物車 | 產品詳細資料頁面<br>產品清單頁面<br>購物車<br>願望清單 |
| 已檢視這個專案，已檢視那個專案 | 即時搜尋<br>產品記錄 | 頁面檢視<br>產品檢視 | 產品詳細資料頁面 |
| 趨勢 | 即時搜尋<br>產品記錄 | 頁面檢視<br>產品檢視 | 產品詳細資料頁面 |
| 已檢視此專案，但購買了其他專案 | 產品推薦 | 頁面檢視<br>產品檢視 | 產品詳細資料頁面<br>購物車/結帳 |
| 已購買此專案，已購買該專案 | 產品推薦 | 頁面檢視<br>產品檢視 | 產品詳細資料頁面 |
| 轉換：檢視以購買 | 產品推薦 | 頁面檢視<br>產品檢視 | 產品詳細資料頁面 |
| 轉換：檢視以購買 | 產品推薦 | 頁面檢視<br>完成簽出 | 購物車/結帳 |
| 轉換：檢視到購物車 | 產品推薦 | 頁面檢視<br>產品檢視 | 產品詳細資料頁面 |
| 轉換：檢視到購物車 | 產品推薦 | 頁面檢視<br>加入購物車 | 產品詳細資料頁面<br>產品清單頁面<br>購物車<br>願望清單 |

>[!NOTE]
>
>以[!DNL Live Search]為目的的資料收集不包含個人識別資訊(PII)。 所有使用者識別碼（例如Cookie ID和IP位址）都需嚴格匿名處理。 [深入瞭解](https://www.adobe.com/privacy/experience-cloud.html)。

## 必要的儀表板事件

有些事件需要填入[即時搜尋儀表板](performance.md)

| 儀表板區域 | 活動 | 加入欄位 |
| ------------------- | ------------- | ---------- |
| 不重複搜尋 | `page-view`，`search-request-sent`， | searchRequestId |
| 零結果搜尋 | `page-view`，`search-request-sent`， | searchRequestId |
| 零結果率 | `page-view`，`search-request-sent`， | searchRequestId |
| 熱門搜尋 | `page-view`，`search-request-sent`， | searchRequestId |
| 平均 按一下位置 | `page-view`，`search-request-sent`，`search-response-received`，`search-results-view`，`search-product-click` | searchRequestId |
| 點進率 | `page-view`，`search-request-sent`，`search-response-received`，`search-results-view`，`search-product-click` | searchRequestId， sku |
| 轉換率 | `page-view`，`search-request-sent`，`search-response-received`，`search-results-view`，`search-product-click`，`product-view`，`add-to-cart`，`place-order` | searchRequestId， sku |

### 必要內容

所有事件都需要`Page`和`Storefront`內容。 這應該發生在頁面層級/店面應用程式層，而不是產生個別事件時（例如，在PHP店面中，PHP應用程式容器負責在執行階段設定它們）。

## 使用狀況

以下是`search-request-sent`事件的實作範例：

```javascript
const mse = window.magentoStorefrontEvents;

/* set in application container */
// mse.context.page(pageCtx);
// mse.context.setStorefrontInstance(storefrontCtx);

/* set before firing event */
mse.context.setSearchInput(searchInputCtx);
mse.publish.searchRequestSent("search-bar");
```

## 警告

廣告封鎖程式和隱私權設定可能會防止擷取事件，且可能導致參與和收入[量度](workspace.md)少報。

事件不會擷取商家網站上發生的每個交易。 事件旨在讓商家大致瞭解網站上發生的事件。

Headless實作必須實作事件以支援[產品Recommendations儀表板](../product-recommendations/events.md)。

>[!NOTE]
>
>如果啟用[Cookie限制模式](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html)，Adobe Commerce不會收集行為資料，直到購物者同意使用Cookie為止。 如果「Cookie限制模式」已停用，Adobe Commerce會依預設收集行為資料。
