---
title: 收集資料
description: 了解事件如何收集產品建議的資料。
exl-id: b827d88c-327f-4986-8239-8f1921d8383c
source-git-commit: 78f226465b9d84707612596a5aa4622aa7869ee1
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# 收集資料

安裝和配置基於SaaS的Adobe Commerce功能時，例如 [產品Recommendations](install-configure.md) 或 [即時搜尋](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html)，模組會將行為資料收集部署至您的店面。 此機制會收集購物者的匿名行為資料，並提供產品建議。 例如， `view` 事件用於計算 `Viewed this, viewed that` 建議類型和 `place-order` 事件用於計算 `Bought this, bought that` 建議類型。

>[!NOTE]
>
>用於產品建議的資料收集不包含個人識別資訊(PII)。 所有使用者識別碼（例如Cookie ID和IP位址）都會嚴格進行匿名處理。 [深入了解](https://www.adobe.com/privacy/experience-cloud.html).

下列事件並非產品Recommendations專屬，而是傳回結果所需：

- `view`
- `add-to-cart`
- `place-order`

此 [Adobe Commerce Storefront事件收集器](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/#quick-start) 列出部署到店面的所有事件。 不過，該清單中有一個事件子集，專屬於產品Recommendations。 當購物者與店面上的建議單位互動時，這些事件會收集資料，並為用來協助您分析建議執行狀況的量度提供動力。

| 事件 | 說明 | [用於量度？](workspace.md) |
| --- | --- | --- |
| `impression-render` | 建議單位會呈現在頁面上。 | 是 |
| `rec-add-to-cart-click` | 客戶點按 **新增至購物車** 按鈕，查看建議單位中的項目。 | 是，當 **新增至購物車** 「建議」範本中顯示按鈕。 |
| `rec-click` | 客戶按一下建議單位中的產品。 | 是 |
| `view` | 建議單元可在頁面上檢視，例如透過捲動至檢視。 | 是 |

如果您的店面是以PWA Studio實作，請參閱 [PWA檔案](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). 如果您使用自訂前端技術，例如React或Vue JS，請參閱使用手冊，了解如何將產品Recommendations整合至 [無頭](headless.md) 環境。

廣告封鎖程式和隱私權設定可防止 `magento/product-recommendations` 模組來擷取事件，並可能導致參與和收入 [量度](workspace.md) 被低估。

>[!NOTE]
>
>若 [Cookie限制模式](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) 啟用後，Adobe Commerce才會收集行為資料，直到購物者同意使用cookie為止。 如果停用Cookie限制模式，Adobe Commerce會依預設收集行為資料。
