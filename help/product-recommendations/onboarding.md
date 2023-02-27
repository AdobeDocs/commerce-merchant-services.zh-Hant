---
title: 入門
description: 了解 [!DNL Product Recommendations].
exl-id: ad47ac39-8f6f-4765-84ad-9e3d104385db
source-git-commit: d56fd57281a5b675e128cca75d4057756a0bf4bf
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---

# 入門

的上線程式 [!DNL Product Recommendations] 需要訪問伺服器的命令行，並包含以下步驟。 如果您不熟悉從命令列進行工作，請要求開發人員或系統整合商提供協助。

- [實作工作流程](implementation-workflow.md)
- [安裝和配置](install-configure.md)
- [設定](settings.md)
- [驗證](verify.md)
- [中繼環境](staging-environment.md)

## 需求

- Adobe Commerce 2.3.x、2.4.x
- PHP 7.3 / 7.4 / 8.1
- 撰寫器

### 支援平台

- Adobe Commerce on premise(EE):2.4.x
- Adobe Commerce on Cloud(ECE):2.4.x

### 頁面產生器支援

[!DNL Product Recommendations] 可新增至頁面作為「頁面產生器」內容類型。 若要將頁面產生器支援新增至產品Recommendations，請參閱 [安裝和配置](install-configure.md).

請參閱 [[!DNL Page Builder] 整合](page-builder.md) 有關如何添加 [!DNL Product Recommendations] into [!DNL Page Builder] 內容。

### B2B支援 {#b2bsupport}

B2B店面通常需要複雜的邏輯，以決定每個購物者或客戶群的產品可見度和定價。 [!DNL Product Recommendations] now [支援](release-notes.md) 本功能 [類別權限](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/category-permissions.html), [共用目錄](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared.html)，和 [客戶群特定定價](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html). 例如，如果您已從零售客戶區段隱藏特定類別，則該區段中的購物者將不會顯示這些類別中產品的建議。 此外，當您為特定客戶群組和公司定義共用目錄時，這些購物者只會看到他們可存取之產品的建議。 所有建議的產品都會根據每個購物者的客戶群組，反映正確的客戶群組特定價格。
