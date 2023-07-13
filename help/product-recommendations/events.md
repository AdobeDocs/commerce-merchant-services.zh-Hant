---
title: 收集資料
description: 瞭解事件如何收集產品建議的資料。
exl-id: b827d88c-327f-4986-8239-8f1921d8383c
feature: Services, Recommendations, Eventing
source-git-commit: 9ae4aff1851e9ce9920c4fbf11d2616d6f0f6307
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# 收集資料

安裝及設定SaaS型Adobe Commerce功能時，例如 [產品Recommendations](install-configure.md) 或 [即時搜尋](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html)，模組會將行為資料收集部署至您的店面。 此機制會從購物者收集匿名行為資料，並提供產品建議。 例如， `view` 事件是用來計算 `Viewed this, viewed that` 建議型別，以及 `place-order` 事件是用來計算 `Bought this, bought that` 建議型別。

>[!NOTE]
>
>為產品推薦目的收集的資料不包括個人識別資訊(PII)。 所有使用者識別碼（例如Cookie ID和IP位址）都需嚴格匿名處理。 [瞭解更多](https://www.adobe.com/privacy/experience-cloud.html).

以下事件並非產品Recommendations特有，而是傳回結果的必要事件：

- `view`
- `add-to-cart`
- `place-order`

此 [Adobe Commerce店面事件收集器](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/#quick-start) 列出部署至店面的所有事件。 但是，從該清單中，有一個產品Recommendations專屬的事件子集。 當購物者與店面的推薦單位互動時，這些活動會收集資料，並支援用於協助您分析建議執行成效的量度。

| 事件 | 說明 | [用於量度？](workspace.md) |
| --- | --- | --- |
| `impression-render` | 建議單位會呈現在頁面上。 | 是 |
| `rec-add-to-cart-click` | 客戶按一下 **加入購物車** 建議單位中專案的按鈕。 | 是，當 **加入購物車** 「建議」範本中會顯示按鈕。 |
| `rec-click` | 客戶按一下建議單位中的產品。 | 是 |
| `view` | 建議單位可在頁面上檢視，例如透過捲動至檢視。 | 是 |

如果您的店面是透過PWA Studio實作，請參閱 [PWA檔案](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). 如果您使用自訂前端技術（例如React或Vue JS），請參閱使用手冊以瞭解如何在中整合產品Recommendations [headless](headless.md) 環境。

## 注意事項

廣告封鎖程式和隱私權設定可防止 `magento/product-recommendations` 擷取事件中的模組，而此模組可能會導致參與和收入 [量度](workspace.md) 將被低報。

事件不會擷取商家網站上發生的每個交易。 事件旨在讓商家大致瞭解網站上發生的事件。

Headless實作必須實作事件功能，才能支援產品Recommendations儀表板。

>[!NOTE]
>
>若 [Cookie限制模式](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) 啟用，在購物者同意使用Cookie之前，Adobe Commerce不會收集行為資料。 如果「Cookie限制模式」已停用，Adobe Commerce會依預設收集行為資料。
