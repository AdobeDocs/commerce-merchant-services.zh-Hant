---
title: 處理Cookie限制
description: 瞭解產品建議如何處理cookie限制。
exl-id: 2f48c47c-569b-455c-a589-8f99b7b74064
source-git-commit: 78f226465b9d84707612596a5aa4622aa7869ee1
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 0%

---

# 處理Cookie限制

Adobe Commerce和Magento Open Source在將資料儲存到瀏覽器Cookie中之前都要求同意。 有關詳細資訊，請參閱 [Cookie限制模式](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html)。

部署 `magento/product-recommendations` 模組到生產，它開始收集你店面的購物者互動事件。 由於這些事件的資料可以儲存在瀏覽器cookie或本地儲存中，因此該功能支援cookie限制模式，因為在購物者獲得cookie許可之前不會收集事件。

這可能不適用於第三方cookie同意解決方案。 每個商戶都有責任確保在獲得cookie同意之前不進行資料收集，法律通常要求這樣做。 如果您使用自定義代碼管理cookie同意，則可以使用名為「Cookie」的不跟蹤cookie `mg_dnt` 限制資料收集。

- Cookie的名稱：

   ```text
   `const DNT_COOKIE = "mg_dnt";`
   ```

- 設定「不跟蹤」cookie以禁用資料收集：

   ```text
   `$.mage.cookies.set(DNT_COOKIE, true);`
   ```

- 要在用戶接受Cookie時清除Cookie:

   ```text
   `$.mage.cookies.clear(DNT_COOKIE);`
   ```
