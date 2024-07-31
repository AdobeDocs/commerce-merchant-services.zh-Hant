---
title: 收集資料
description: 瞭解事件如何收集產品建議的資料。
exl-id: b827d88c-327f-4986-8239-8f1921d8383c
feature: Services, Recommendations, Eventing
source-git-commit: 67296ea42bfddb10b0c86cb1ca47324f5fec7825
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# 收集資料

當您安裝及設定SaaS型Adobe Commerce功能(例如[產品Recommendations](install-configure.md)或[即時搜尋](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html))時，模組會將行為資料收集部署至您的店面。 此機制會從購物者收集匿名行為資料，並提供產品建議。 例如，`view`事件是用來計算`Viewed this, viewed that`建議型別，`place-order`事件是用來計算`Bought this, bought that`建議型別。

>[!NOTE]
>
>為產品推薦目的而收集的資料不包含個人識別資訊(PII)。 所有使用者識別碼（例如Cookie ID和IP位址）都需嚴格匿名處理。 瞭解[更多](https://www.adobe.com/privacy/experience-cloud.html)。

以下事件並非產品Recommendations所特有，而是傳回結果的必要專案：

- `view`
- `add-to-cart`
- `place-order`

[Adobe Commerce店面事件收集器](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/#quick-start)會列出所有部署到店面的事件。 但是，從該清單中，會有產品Recommendations專屬的事件子集。 當購物者與店面的推薦單位互動時，這些活動會收集資料，並支援用於協助您分析建議執行效果的量度。

| 事件 | 說明 | 用於量度？ |
| --- | --- | --- |
| `impression-render` | 建議單位會呈現在頁面上。 | 是 |
| `rec-add-to-cart-click` | 客戶按一下建議單位中專案的&#x200B;**加入購物車**&#x200B;按鈕。 | 是，當&#x200B;**加入購物車**&#x200B;按鈕出現在建議範本中時。 |
| `rec-click` | 客戶按一下建議單位中的產品。 | 是 |
| `view` | 建議單位可在頁面上檢視，例如透過捲動至檢視中。 | 是 |

若要正確填入控制面板，必須執行下列事件。

| 儀表板欄 | 活動 | 加入欄位 |
| ---------------- | --------- | ----------- |
| 曝光數 | `page-view`，`recs-request-sent`，`recs-response-received`，`recs-unit-render` | unitId |
| 檢視 | `page-view`，`recs-request-sent`，`recs-response-received`，`recs-unit-render`，`recs-unit-view` | unitId |
| 點按次數 | `page-view`，`recs-request-sent`，`recs-response-received`，`recs-item-click`，`recs-add-to-cart-click` | unitId |
| 收入 | `page-view`，`recs-request-sent`，`recs-response-received`，`recs-item-click`，`recs-add-to-cart-click`，`place-order` | unitId， sku |
| LT收入 | `page-view`，`recs-request-sent`，`recs-response-received`，`recs-item-click`，`recs-add-to-cart-click`，`place-order` | unitId， sku |
| CTR | `page-view`，`recs-request-sent`，`recs-response-received`，`recs-unit-render`，`recs-item-click`，`recs-add-to-cart-click` | unitId， sku |
| vCTR | `page-view`，`recs-request-sent`，`recs-response-received`，`recs-unit-render`，`recs-unit-view`，`recs-item-click`，`recs-add-to-cart-click` | unitId， sku |

如果您的店面是以PWA Studio實作，請參閱[PWA檔案](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/)。 如果您使用自訂前端技術，例如React或Vue JS，請參閱使用手冊以瞭解如何在Headless](headless.md)環境中整合[產品Recommendations。

## 警告

廣告封鎖程式和隱私權設定可能會阻止`magento/product-recommendations`模組擷取事件，並可能導致參與和收入[量度](workspace.md)少報。

事件不會擷取商家網站上發生的每個交易。 事件旨在讓商家大致瞭解網站上發生的事件。

Headless實施必須實施事件以支援產品Recommendations儀表板。

>[!NOTE]
>
>如果啟用[Cookie限制模式](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html)，Adobe Commerce不會收集行為資料，直到購物者同意使用Cookie為止。 如果「Cookie限制模式」已停用，Adobe Commerce會依預設收集行為資料。
