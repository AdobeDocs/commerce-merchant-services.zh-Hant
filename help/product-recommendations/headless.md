---
title: 無頭
description: 了解如何整合 [!DNL Product Recommendations] 在無頭的店前。
exl-id: 316d0b0c-5938-4e2f-9d0d-747746cf6056
source-git-commit: 78f226465b9d84707612596a5aa4622aa7869ee1
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---

# 無頭

您可以整合 [!DNL Product Recommendations] 在無頭的店前，使用 [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/) 或自訂前端技術，例如React或Vue JS。

[!DNL Product Recommendations] 要求 [行為與目錄資料](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/development-overview.html) 手術。 在無頭實作中，目錄資料同步程式維持不變，但行為資料收集需要變更。

要整合 [!DNL Product Recommendations] 在無頭的店面，您必須：

1. 將行為資料傳送至Adobe Sensei以分析和計算產品建議結果。 您也可以傳送其他資料以啟用產品建議 [量度報告](workspace.md).

1. 擷取產品建議結果並在頁面上呈現這些結果。

您可以使用可用的SDK來執行上述兩項動作，如下列工作流程所述。

1. [安裝](install-configure.md) the [!DNL Product Recommendations] 模組。

1. 安裝及使用 [Adobe Commerce Storefront Event SDK](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) 來開火 [行為事件](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/events.html).

   要傳回的最低必要事件 [!DNL Product Recommendations] 結果：

   | 事件 | 類別 |
   |--- | ---|
   | `view` | 產品 |
   | `add-to-cart` | 產品 |
   | `place-order` | 簽出 |

   啟用 [量度報告](workspace.md)，則需要下列其他事件：

   | 事件 | 類別 |
   |--- | ---|
   | `impression-render` | recommendation-unit |
   | `view` | recommendation-unit |
   | `rec-click` | recommendation-unit |
   | `rec-add-to-cart-click` | recommendation-unit（如果建議範本中出現「新增至購物車」按鈕） |

1. 觸發事件時，請使用 [Adobe Commerce Storefront事件收集器](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/) 來處理事件並將其傳送至Adobe Sensei。

1. 收集行為資料後，您可以 [建立](create.md) [!DNL Product Recommendations] 中。

1. 使用 [Recommendations SDK](https://developer.adobe.com/commerce/services/product-recommendations/) 來擷取店面上的建議單位。 SDK會傳回必要的產品資料，以在頁面上呈現建議單位。
