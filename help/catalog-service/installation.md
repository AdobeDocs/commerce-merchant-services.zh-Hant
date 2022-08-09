---
title: '"登機和安裝"'
description: '"瞭解如何安裝 [!DNL Catalog Service]"'
source-git-commit: 7f6955ffc52669ff3b95957642b3a115bf1eb741
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 登機和安裝

歡迎合作夥伴和客戶開始使用 [!DNL Catalog Service] 2022年8月9日發佈的Adobe CommerceBeta版。 要參與，您必須閱讀並同意我們 [Adobe CommerceBeta計畫術語](https://experiencecloudpanel.adobe.com/h/s/6eGskQlHvLSHztsNmKCWMy)。

簽署協定後，請與我們的團隊聯繫 [#storefront服務](https://magentocommeng.slack.com/archives/C03HVPG8RS4) 公共Slack頻道。 我們將提供與 [!DNL Catalog Service] 測試版。

## 先決條件

登機過程 [!DNL Catalog Service] 需要訪問伺服器的命令行。 如果您不熟悉從命令行工作，請咨詢開發人員或系統整合商以獲得幫助。

### 軟體要求

- Adobe Commerce2.4.x
- 8.1、7.4、7.3菲律賓比索
- 作曲家：2.x,1.x

### 支援的平台

- Adobe Commerce在雲基礎架構方面：2.4.x
- Adobe Commerce駐地：2.4.x

## 安裝擴展

可以安裝 [!DNL Catalog Service] 在雲基礎架構和內部實例上擴展Adobe Commerce。

的 [!DNL Catalog Service] 與連結到MagentoID([馬吉德](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-personal/#field-descriptions) 在註冊過程中提供。 Composer在初始安裝時使用這些鍵 [!DNL Adobe Commerce]，或在以前未將Composer鍵保存到 `auth.json` 的子菜單。

請參閱 [獲取您的身份驗證密鑰](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 的子菜單。

### Adobe Commerce在雲基礎架構上

使用此方法安裝 [!DNL Catalog Service] Commerce Cloud實例的擴展。

1. 開啟 `<Commerce_root>/composer.json` 文本編輯器中的檔案，並更新 `require` 下列各節：

   ```json
   "require": {
     "magento/magento-cloud-metapackage": ">=2.4.3 <2.4.4",
     "magento/composer-root-update-plugin": "~1.1",
     "magento/saas-export": "^101.3.1",
     "magento/commerce-data-export": "^101.2.4",    
     "magento/commerce-data-export-ee": "^101.2.4",
     "magento/services-id": "^3.0.0",
     "magento/services-connector": "1.2.1"
   }
   ```

   <!-- What if the customer already has other services installed, and some of these lines are already present? Do they need to delete the duplications? What if the version numbers are different? -->

1. 更新依賴項並安裝擴展：

   ```bash
   composer update
   ```

   該命令更新所有依賴關係。

1. 提交並推送更改。

### 內部

使用此方法安裝 [!DNL Catalog Service] 本地實例的擴展。

1. 開啟 `<Commerce_root>/composer.json` 文本編輯器中的檔案，並更新 `require` 下列各節：

   ```json
   "require": {
     "magento/magento-cloud-metapackage": ">=2.4.3 <2.4.4",
     "magento/composer-root-update-plugin": "~1.1",
     "magento/saas-export": "^101.3.1",
     "magento/commerce-data-export": "^101.2.4",    
     "magento/commerce-data-export-ee": "^101.2.4",
     "magento/services-id": "^3.0.0",
     "magento/services-connector": "1.2.1"
   }
   ```

1. 更新依賴項並安裝擴展：

   ```bash
   composer update
   ```

   該命令更新所有依賴關係。

1. 升級Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. 清除快取：

   ```bash
   bin/magento cache:clean
   ```

## 配置目錄導出

安裝後 [!DNL Catalog Service]，必須配置 [Commerce Services連接器](../landing/saas.md) 指定API密鑰並選擇SaaS資料空間。

要確保目錄導出正確運行，請確認 [瘋狂的工作](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) 和 [索引器](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) 正在運行，並且Product Feed索引器已設定為「按計畫更新」。
