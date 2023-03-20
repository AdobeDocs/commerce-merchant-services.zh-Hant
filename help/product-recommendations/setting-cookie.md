---
title: 處理Cookie限制
description: 了解產品建議如何處理Cookie限制。
exl-id: 2f48c47c-569b-455c-a589-8f99b7b74064
source-git-commit: 78f226465b9d84707612596a5aa4622aa7869ee1
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 0%

---

# 處理Cookie限制

Adobe Commerce和Magento Open Source都會在資料儲存至瀏覽器Cookie前要求同意。 如需詳細資訊，請參閱 [Cookie限制模式](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html).

部署 `magento/product-recommendations` 模組傳送至生產環境，即會開始在店面上收集購物者互動事件。 由於這些事件的資料可儲存在瀏覽器Cookie或本機儲存空間中，因此在購物者取得Cookie同意前，不會收集事件，因此此功能支援Cookie限制模式。

第三方Cookie同意解決方案可能無法使用。 如法律通常要求，每家商戶都應負責確保在同意Cookie之前不會進行資料收集。 如果您使用自訂程式碼管理Cookie同意，則可使用名為 `mg_dnt` 限制資料收集。

- Cookie名稱：

   ```text
   `const DNT_COOKIE = "mg_dnt";`
   ```

- 設定do-not-track Cookie以停用資料收集：

   ```text
   `$.mage.cookies.set(DNT_COOKIE, true);`
   ```

- 若要在使用者接受Cookie時清除Cookie:

   ```text
   `$.mage.cookies.clear(DNT_COOKIE);`
   ```
