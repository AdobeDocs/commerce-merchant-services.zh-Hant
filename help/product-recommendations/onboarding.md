---
title: 登機
description: 瞭解中的要求和支援的平台 [!DNL Product Recommendations]。
source-git-commit: 4ad607c8595b25d01b5f5020b787fc1d35d4df25
workflow-type: tm+mt
source-wordcount: '222'
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

- Adobe Commerce2.3.x,2.4.x
- 7.3菲律賓比索/7.4
- 作曲家

### 支援的平台

- Adobe Commerce在prem(EE):2.4.x
- Adobe Commerce雲(ECE):2.4.x

### 頁面生成器支援

[!DNL Product Recommendations] 可以作為頁面生成器內容類型添加到頁面。 要將頁面生成器支援添加到產品Recommendations，請參閱 [安裝和配置](install-configure.md)。

### B2B支援 {#b2bsupport}

B2B店面往往需要複雜的邏輯，要求每個購物者或顧客群體都能看到產品並確定價格。 [!DNL Product Recommendations] 現在 [支援](release-notes.md) 此功能 [類別權限](https://docs.magento.com/user-guide/catalog/category-permissions.html)。 [共用目錄](https://docs.magento.com/user-guide/catalog/catalog-shared.html), [特定於客戶組的定價](https://docs.magento.com/user-guide/catalog/pricing-advanced.html)。 例如，如果您在零售客戶細分市場中隱藏了某些類別，則該細分市場中的購物者將不會為這些類別中的產品顯示推薦資訊。 此外，當您為特定客戶組和公司定義共用目錄時，這些購物者只會看到他們可以訪問的產品的建議。 所有推薦產品均反映基於每位顧客客戶群的正確客戶群價格。
