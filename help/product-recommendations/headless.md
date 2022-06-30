---
title: 無頭
description: 瞭解如何整合 [!DNL Product Recommendations] 在無頭的店面。
exl-id: 316d0b0c-5938-4e2f-9d0d-747746cf6056
source-git-commit: ce437d7a991affd2665c86c9e91bb7f39ec626c0
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# 無頭

您可以整合 [!DNL Product Recommendations] 在無頭店裡 [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/) 或定制前端技術，如React或Vue JS。

[!DNL Product Recommendations] 要求 [行為和目錄資料](https://devdocs.magento.com/recommendations/product-recs.html#typesofdata) 手術。 目錄資料同步過程在無頭實現中保持不變，但行為資料收集需要更改。

整合 [!DNL Product Recommendations] 在無頭店面，你必須：

1. 將行為資料發送到Adobe Sensei以分析和計算產品推薦結果。 您還可以發送其他資料以啟用產品建議 [度量報告](workspace.md)。

1. 獲取產品建議結果並在頁面上呈現這些結果。

可以使用以下工作流中所述的可用SDK執行這兩個操作。

1. [安裝](install-configure.md) 這樣 [!DNL Product Recommendations] 中。

1. 安裝和使用 [Adobe Commerce店面事件SDK](https://devdocs.magento.com/shared-services/storefront-events-sdk.html) 開火 [行為事件](https://devdocs.magento.com/recommendations/events.html)。

   要返回的最小必需事件 [!DNL Product Recommendations] 結果：

   | Event | 類別 |
   |--- | ---|
   | `view` | 產品 |
   | `add-to-cart` | 產品 |
   | `place-order` | 簽出 |

   啟用 [度量報告](workspace.md)，需要以下附加事件：

   | 事件 | 類別 |
   |--- | ---|
   | `impression-render` | 推薦單元 |
   | `view` | 推薦單元 |
   | `rec-click` | 推薦單元 |
   | `rec-add-to-cart-click` | 建議單元（如果建議模板中存在「添加到購物車」按鈕） |

1. 激發事件時，使用 [Adobe Commerce店面事件收集器](https://devdocs.magento.com/shared-services/storefront-event-collector.html) 來處理這些事件，並送到Adobe Sensei。

1. 收集行為資料後，您可以 [建立](create.md) [!DNL Product Recommendations] 的子菜單。

1. 使用 [RecommendationsSDK](https://devdocs.magento.com/recommendations/recs-api.html) 去取店面的推薦單位。 SDK返回必要的產品資料以在頁面上呈現建議單元。
