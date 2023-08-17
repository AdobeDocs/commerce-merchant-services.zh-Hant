---
title: 驗證事件集合
description: 瞭解如何確認行為資料是否正傳送至Adobe Commerce。
exl-id: c8c34db4-9d87-4012-b8f0-e9b1da214305
source-git-commit: d8be88f47f103c5d632540dae743ede398a9b7ad
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# 驗證事件集合

在您之後 [安裝與設定](install-configure.md) 此 `magento/product-recommendations` 模組，您即可驗證行為資料是否已傳送至Adobe Commerce。 您可以使用Chrome中提供的開發人員工具，或安裝Snowplow Chrome擴充功能。 如果您需要其他說明，請參閱 [疑難排解 [!DNL Product Recommendations] 模組](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-product-recommendations-module-in-magento-commerce.html) 位於支援知識庫中。

## 使用Chrome中的開發人員工具進行驗證

若要確保事件收集器JS檔案正在所有網站頁面上載入：

1. 在Chrome中，選擇 **自訂和控制Google Chrome** 然後選取 **更多工具** > **開發人員工具**.
1. 選擇 **網路** 索引標籤，然後選取 **JS** 型別。
1. 篩選對象 `ds.`
1. 重新載入頁面。
1. 您應該會看到 `ds.js` 或 `ds.min.js` 在 **名稱** 欄。

![事件收集器JS](assets/filter-ds.png)
_事件收集器JS_

若要確保您的網站上的頁面（首頁、產品、結帳等）都會觸發事件：

1. 請務必停用瀏覽器上的任何廣告封鎖程式，並接受網站上的Cookie。
1. 在Chrome中，選擇 **自訂和控制Google Chrome** （瀏覽器右上角的三個垂直點），然後選取 **更多工具** > **開發人員工具**.
1. 選擇 **網路** 標籤並篩選 `tp2`.
1. 重新載入頁面。
1. 您應該會在下方看到呼叫 `tp2` 在 **名稱** 欄。

![正在引發事件](assets/filter-tp2.png)
_確認事件正在引發_

## 使用Snowplow Chrome擴充功能進行驗證

安裝 [Chrome適用的Snowplow Analytics Debugger擴充功能](https://chrome.google.com/webstore/detail/snowplow-analytics-debugg/jbnlcgeengmijcghameodeaenefieedm). 此擴充功能會顯示正在收集並傳送至Adobe Commerce的事件。

1. 請務必停用瀏覽器上的任何廣告封鎖程式，並接受網站上的Cookie。

1. 在Chrome中，選擇 **自訂和控制Google Chrome** （瀏覽器右上角的三個垂直點），然後選取 **更多工具** > **開發人員工具**.

1. 選擇 **Snowplow Analytics Debugger** 標籤。

1. 在 **事件** 欄，選取 **結構化事件**.

1. 向下捲動，直到您看到 **內容資料 _n_**. 尋找中的店面例項&#x200B;**結構描述**.

1. 確認 [SaaS資料空間ID](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) 已正確設定。

![雪鏟濾鏡](assets/snowplow-filter.png)
_雪鏟濾鏡_

>[!NOTE]
>
> 值 `Data validity : NOT FOUND` 在debugger中會指出內部結構描述。 Snowplow Chrome外掛程式無法驗證具有內部結構描述的事件。 這對實際功能沒有影響。

## 驗證事件是否正確引發

若要驗證用於量度的事件是否正確引發，請尋找 `impression-render`， `view`、和 `rec-click` Snowplow Analytics Debugger中的事件。 請參閱 [事件的完整清單](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/events.html).

>[!NOTE]
>
> 如果 [Cookie限制模式](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) 已啟用，在購物者同意前，Adobe Commerce不會收集行為資料。 如果「Cookie限制模式」已停用，系統會依預設收集行為資料。
