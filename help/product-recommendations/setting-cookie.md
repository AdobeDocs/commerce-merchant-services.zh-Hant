---
title: 處理Cookie限制
description: 瞭解產品建議如何處理Cookie限制。
exl-id: 2f48c47c-569b-455c-a589-8f99b7b74064
source-git-commit: 78f226465b9d84707612596a5aa4622aa7869ee1
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 0%

---

# 處理Cookie限制

Adobe Commerce和Magento Open Source都會在資料儲存至瀏覽器Cookie前要求使用者同意。 如需詳細資訊，請參閱 [Cookie限制模式](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html).

當您部署 `magento/product-recommendations` 模組到生產環境，它會開始收集店面上的購物者互動事件。 因為這些事件的資料可以儲存在瀏覽器Cookie或本機儲存體中，此功能會在購物者同意Cookie之前不收集事件，從而支援Cookie限制模式。

這可能不適用於第三方Cookie同意解決方案。 每個商家都有責任確保Cookie同意前不會進行資料收集，法律通常要求如此。 如果您透過自訂程式碼管理Cookie同意，則可使用不追蹤Cookie，稱為 `mg_dnt` 以限制資料收集。

- Cookie的名稱：

   ```text
   `const DNT_COOKIE = "mg_dnt";`
   ```

- 設定do-not-track Cookie以停用資料收集：

   ```text
   `$.mage.cookies.set(DNT_COOKIE, true);`
   ```

- 若要在使用者接受Cookie時清除Cookie：

   ```text
   `$.mage.cookies.clear(DNT_COOKIE);`
   ```
