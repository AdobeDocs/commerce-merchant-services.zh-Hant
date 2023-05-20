---
title: 無頭
description: 瞭解如何整合 [!DNL Product Recommendations] 在無頭的店面。
exl-id: 316d0b0c-5938-4e2f-9d0d-747746cf6056
source-git-commit: 521ea4fc2cce809fc12d3958e37089f3e34e1068
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# 無頭

您可以整合 [!DNL Product Recommendations] 在無頭店裡 [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/) 或定制前端技術，如React或Vue JS。

定制和無頭整合商應參考這些Luma和PWA說明作為建議的實施。 在無頭解決方案中實施產品Recommendations有多種方法，本文檔不涵蓋所有情形。 整合商必須為其實施提供活動、設計和測試。

[!DNL Product Recommendations] 要求 [行為和目錄資料](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/development-overview.html) 手術。 目錄資料同步過程在無頭實現中保持不變，但行為資料收集需要更改。

>[!NOTE]
>
>無頭實例必須實施事件才能為產品Recommendations儀表板供電。

整合 [!DNL Product Recommendations] 在無頭店面，你必須：

1. 將行為資料發送到Adobe Sensei以分析和計算產品推薦結果。 您還可以發送其他資料以啟用產品建議 [度量報告](workspace.md)。

1. 獲取產品建議結果並在頁面上呈現這些結果。

可以使用以下工作流中所述的可用SDK執行這兩個操作。

1. [安裝](install-configure.md) 這樣 [!DNL Product Recommendations] 中。

1. 安裝和使用 [Adobe Commerce店面事件SDK](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) 開火 [行為事件](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/events.html)。

   要返回的最小必需事件 [!DNL Product Recommendations] 結果：

   | 事件 | 類別 |
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

1. 激發事件時，使用 [Adobe Commerce店面事件收集器](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/) 來處理這些事件，並送到Adobe Sensei。

1. 收集行為資料後，您可以 [建立](create.md) [!DNL Product Recommendations] 的子菜單。

1. 使用 [RecommendationsSDK](https://developer.adobe.com/commerce/services/product-recommendations/) 去取店面的推薦單位。 SDK返回必要的產品資料以在頁面上呈現建議單元。
