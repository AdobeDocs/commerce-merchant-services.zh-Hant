---
title: 收集資料
description: 瞭解事件如何收集產品建議的資料。
exl-id: b827d88c-327f-4986-8239-8f1921d8383c
source-git-commit: e74bc4aeaa154e751f8d986e0426dd19d55d335e
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# 收集資料

安裝和配置基於SaaS的Adobe Commerce功能時，如 [產品Recommendations](install-configure.md) 或 [即時搜索](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html)，模組將行為資料收集部署到您的儲存前端。 該機制從購物者收集匿名行為資料，並為產品建議提供支援。 例如， `view` 事件用於計算 `Viewed this, viewed that` 建議類型和 `place-order` 事件用於計算 `Bought this, bought that` 建議類型。

>[!NOTE]
>
>為產品建議目的收集的資料不包括個人身份資訊(PII)。 所有用戶標識符，如cookie ID和IP地址，都是嚴格匿名的。 [瞭解更多資訊](https://www.adobe.com/privacy/experience-cloud.html)。

以下事件不是產品Recommendations特有的，但需要返回結果：

- `view`
- `add-to-cart`
- `place-order`

的 [Adobe Commerce店面事件收集器](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/#quick-start) 列出了部署到您的店面的所有事件。 但是，從該清單中，有特定於產品Recommendations的事件的子集。 當購物者與店面的推薦單元交互時，這些事件會收集資料，並為用來幫助您分析推薦執行情況的指標提供電力。

| 事件 | 說明 | [是否用於度量？](workspace.md) |
| --- | --- | --- |
| `impression-render` | 建議單元在頁面上呈現。 | 是 |
| `rec-add-to-cart-click` | 客戶按一下 **添加到購物車** 按鈕 | 是的，當 **添加到購物車** 按鈕。 |
| `rec-click` | 客戶按一下推薦單元中的產品。 | 是 |
| `view` | 建議單元在頁面上變為可視，例如滾動到視圖中。 | 是 |

如果您的店面是使用PWA Studio實現的，請參閱 [PWA文檔](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/)。 如果您使用自定義前端技術（如React或Vue JS），請參閱使用手冊瞭解如何將產品Recommendations整合到 [頭](headless.md) 環境。

## 警告

廣告阻止程式和隱私設定可以阻止 `magento/product-recommendations` 模組來捕獲事件，並可能導致項目和收入 [度量](workspace.md) 被低報。

事件不會捕獲商家網站上發生的每筆交易。 活動旨在讓商家大致瞭解現場正在發生的活動。

無頭實施必須實施事件以為產品Recommendations儀表板供電。

>[!NOTE]
>
>如果 [Cookie限制模式](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) 啟用，Adobe Commerce在購物者同意使用cookie之前不會收集行為資料。 如果禁用Cookie限制模式，則預設情況下Adobe Commerce會收集行為資料。
