---
title: 登機
description: 瞭解中的要求和支援的平台 [!DNL Product Recommendations]。
exl-id: ad47ac39-8f6f-4765-84ad-9e3d104385db
source-git-commit: 209bdf9c69ff81481d6df7cb8e8832deef13c9f4
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# 登機

登機過程 [!DNL Product Recommendations] 需要訪問伺服器的命令行，並包括以下步驟。 如果您不熟悉從命令行工作，請咨詢開發人員或系統整合商以獲得幫助。

- [實施工作流](implementation-workflow.md)
- [安裝和配置](install-configure.md)
- [設定](settings.md)
- [驗證](verify.md)
- [暫存環境](staging-environment.md)

## 要求

- Adobe Commerce2.4.4+
- 8.1、8.2菲律賓比索
- 作曲家2

### 支援的平台

- Adobe Commerce駐地：2.4.4+
- Adobe Commerce雲(ECE):2.4.4+

### 頁面生成器支援

[!DNL Product Recommendations] 可以作為頁面生成器內容類型添加到頁面。 要將頁面生成器支援添加到產品Recommendations，請參閱 [安裝和配置](install-configure.md)。

請參閱 [[!DNL Page Builder] 整合](page-builder.md) 有關如何添加的說明 [!DNL Product Recommendations] 入 [!DNL Page Builder] 內容。

### SaaS價格索引

產品建議客戶可以使用 [SaaS價格索引](../price-index/index.md)提供更快的價格更新和同步時間。

### B2B支援 {#b2bsupport}

B2B店面往往需要複雜的邏輯，要求每個購物者或顧客群體都能看到產品並確定價格。 [!DNL Product Recommendations] 現在 [支援](release-notes.md) 此功能 [類別權限](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/category-permissions.html)。 [共用目錄](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared.html), [特定於客戶組的定價](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html)。 例如，如果您在零售客戶細分市場中隱藏了某些類別，則該細分市場中的購物者將不會為這些類別中的產品顯示推薦資訊。 此外，當您為特定客戶組和公司定義共用目錄時，這些購物者只會看到他們可以訪問的產品的建議。 所有推薦產品均反映基於每位顧客客戶群的正確客戶群價格。

>[!NOTE]
>
>商戶可通過使用 [目錄服務](../catalog-service/overview.md) Storefront API，但任何自定義都超出了Adobe支援團隊的範圍。
