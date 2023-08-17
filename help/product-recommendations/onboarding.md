---
title: 入門
description: 瞭解中的需求與支援平台 [!DNL Product Recommendations].
exl-id: ad47ac39-8f6f-4765-84ad-9e3d104385db
source-git-commit: 209bdf9c69ff81481d6df7cb8e8832deef13c9f4
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# 入門

的入門流程 [!DNL Product Recommendations] 需要存取伺服器的命令列，且包含下列步驟。 如果您不熟悉如何使用命令列，請向開發人員或系統整合商尋求協助。

- [實作工作流程](implementation-workflow.md)
- [安裝與設定](install-configure.md)
- [設定](settings.md)
- [驗證](verify.md)
- [中繼環境](staging-environment.md)

## 需求

- Adobe Commerce 2.4.4+
- PHP 8.1、8.2
- Composer 2

### 支援平台

- Adobe Commerce內部部署(EE) ：2.4.4+
- 雲端上的Adobe Commerce (ECE) ： 2.4.4+

### 頁面產生器支援

[!DNL Product Recommendations] 可新增至頁面作為頁面產生器內容型別。 若要在產品Recommendations中新增頁面產生器支援，請參閱 [安裝與設定](install-configure.md).

另請參閱 [[!DNL Page Builder] 整合](page-builder.md) 以取得如何新增的指示 [!DNL Product Recommendations] 到 [!DNL Page Builder] 內容。

### SaaS價格索引

客戶能使用的產品推薦 [SaaS價格索引](../price-index/index.md)，提供更快的價格變更更新和同步化時間。

### B2B支援 {#b2bsupport}

B2B店面通常需要複雜的邏輯，這些邏輯會指定每個購物者或客戶群組的產品可見度和價格。 [!DNL Product Recommendations] now [支援](release-notes.md) 此功能藉由接受 [類別許可權](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/category-permissions.html)， [共用目錄](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared.html)、和 [客戶群組特定定價](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html). 例如，如果您隱藏零售客戶區段中的某些類別，則該區段中的購物者不會看到這些類別中產品的建議。 此外，當您為特定客戶群組和公司定義共用目錄時，這些購物者只會看到他們可存取之產品的建議。 所有建議產品都會根據每位購物者的客戶群組，反映正確的客戶群組特定價格。

>[!NOTE]
>
>商家可使用以下工具來自訂和延伸Widget或店面元素： [目錄服務](../catalog-service/overview.md) 店面API，但任何自訂都超出了Adobe支援團隊的範圍。
