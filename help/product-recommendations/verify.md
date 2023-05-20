---
title: 驗證事件集合
description: 瞭解如何驗證行為資料是否正被發送到Adobe Commerce。
exl-id: c8c34db4-9d87-4012-b8f0-e9b1da214305
source-git-commit: d8be88f47f103c5d632540dae743ede398a9b7ad
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# 驗證事件集合

在你之後 [安裝和配置](install-configure.md) 這樣 `magento/product-recommendations` 模組，您可以驗證行為資料是否正在發送到Adobe Commerce。 您可以使用Chrome中提供的開發人員工具，或安裝Snowplough Chrome擴展。 如果需要其他幫助，請參閱 [故障排除 [!DNL Product Recommendations] 模組](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-product-recommendations-module-in-magento-commerce.html) 的子菜單。

## 在Chrome中使用開發人員工具驗證

要確保事件收集器JS檔案正在載入到所有網站頁：

1. 在Chrome中，選擇 **定制和控制GoogleChrome** 選擇 **更多工具** > **開發人員工具**。
1. 選擇 **網路** 頁籤 **JS** 的雙曲餘切值。
1. 篩選 `ds.`
1. 重新載入頁面。
1. 你應該看到 `ds.js` 或 `ds.min.js` 的 **名稱** 的雙曲餘切值。

![事件收集器JS](assets/filter-ds.png)
_事件收集器JS_

要確保事件在您的站點（首頁、產品、簽出等）的頁面上激發：

1. 確保禁用瀏覽器上的任何廣告攔截程式並接受站點上的cookie。
1. 在Chrome中，選擇 **定制和控制GoogleChrome** （瀏覽器右上角的三個垂直點），然後選擇 **更多工具** > **開發人員工具**。
1. 選擇 **網路** 頁籤和篩選器 `tp2`。
1. 重新載入頁面。
1. 您應在 `tp2` 的 **名稱** 的雙曲餘切值。

![激發事件](assets/filter-tp2.png)
_驗證事件是否正在激發_

## 使用Snowploogh Chrome擴展驗證

安裝 [Chrome的雪犁分析調試器擴展](https://chrome.google.com/webstore/detail/snowplow-analytics-debugg/jbnlcgeengmijcghameodeaenefieedm)。 此擴展顯示正在收集併發送到Adobe Commerce的事件。

1. 確保禁用瀏覽器上的任何廣告攔截程式並接受站點上的cookie。

1. 在Chrome中，選擇 **定制和控制GoogleChrome** （瀏覽器右上角的三個垂直點），然後選擇 **更多工具** > **開發人員工具**。

1. 選擇 **雪犁分析調試器** 頁籤。

1. 在 **事件** 列，選擇 **結構化事件**。

1. 向下滾動，直到您看到 **上下文資料 _n_**。 在&#x200B;**架構**。

1. 驗證 [SaaS資料空間ID](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) 設定正確。

![雪犁過濾器](assets/snowplow-filter.png)
_雪犁過濾器_

>[!NOTE]
>
> 值 `Data validity : NOT FOUND` 在調試器中指示內部架構。 Snowplough Chrome插件無法使用內部架構驗證事件。 這對實際功能沒有影響。

## 驗證事件是否正確觸發

要驗證用於度量的事件是否正確觸發，請查找 `impression-render`。 `view`, `rec-click` 雪犁分析調試器中的事件。 查看 [完整事件清單](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/events.html)。

>[!NOTE]
>
> 如果 [Cookie限制模式](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) 啟用，Adobe Commerce在購物者同意前不收集行為資料。 如果禁用Cookie限制模式，則預設情況下會收集行為資料。
