---
title: Headless
description: 瞭解如何整合 [!DNL Product Recommendations] 在headless店面。
exl-id: 316d0b0c-5938-4e2f-9d0d-747746cf6056
source-git-commit: 521ea4fc2cce809fc12d3958e37089f3e34e1068
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# Headless

您可以整合 [!DNL Product Recommendations] 在headless店面，使用 [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/) 或自訂前端技術，例如React或Vue JS。

自訂和Headless整合經銷商應參考這些Luma和PWA指示，作為建議的實作。 有許多方式可將產品Recommendations實作至Headless解決方案，本檔案並未涵蓋所有案例。 整合經銷商必須涵蓋其實作的事件、設計和測試。

[!DNL Product Recommendations] 需要 [行為和目錄資料](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/development-overview.html) 以運作。 Headless實作中的目錄資料同步程式維持不變，但行為資料收集需要變更。

>[!NOTE]
>
>Headless執行個體必須實作事件功能，才能支援產品Recommendations儀表板。

若要整合 [!DNL Product Recommendations] 在headless店面，您必須：

1. 將行為資料傳送至Adobe Sensei，以分析和計算產品推薦結果。 您也可以傳送其他資料以啟用產品推薦 [量度報告](workspace.md).

1. 擷取產品推薦結果並在頁面上呈現這些結果。

您可以使用可用的SDK來執行這兩個動作，如下列工作流程所述。

1. [安裝](install-configure.md) 此 [!DNL Product Recommendations] 模組。

1. 安裝及使用 [Adobe Commerce店面活動SDK](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) 以引發 [行為事件](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/events.html).

   要傳回的最小必要事件 [!DNL Product Recommendations] 結果：

   | 事件 | 類別 |
   |--- | ---|
   | `view` | product |
   | `add-to-cart` | product |
   | `place-order` | 簽出 |

   若要啟用 [量度報告](workspace.md)，則需要下列其他事件：

   | 事件 | 類別 |
   |--- | ---|
   | `impression-render` | recommendation-unit |
   | `view` | recommendation-unit |
   | `rec-click` | recommendation-unit |
   | `rec-add-to-cart-click` | recommendation-unit （如果「加入購物車」按鈕出現在建議範本中） |

1. 觸發事件時，請使用 [Adobe Commerce店面事件收集器](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/) 以處理事件並傳送至Adobe Sensei。

1. 收集行為資料後，您可以 [建立](create.md) [!DNL Product Recommendations] 在Admin中。

1. 使用 [RECOMMENDATIONS SDK](https://developer.adobe.com/commerce/services/product-recommendations/) 以擷取店面上的推薦單位。 SDK會傳回必要的產品資料以轉譯頁面上的推薦單位。
