---
title: 安裝
description: '"安裝 [!DNL Store Fulfillment solution] 用於使用PHP的撰寫器的Adobe Commerce店面。」'
role: User, Admin
level: Intermediate
exl-id: 6613268a-7d22-4c54-af89-834921b7f262
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 0%

---


# 安裝

完成初始安裝 [!DNL Store Fulfillment for Adobe Commerce by Walmart Commerce Technologies] 在非生產環境中的擴充功能，且佇列管理器會執行並設定快取以允許例外狀況處理。 確保您的開發環境包含開發工具，以確保運作和維護您的Adobe Commerce例項的最佳實務。

## 必要條件

檢閱 [需求](solution-requirements.md) ，並在安裝 [!DNL Store Fulfillment] Adobe Commerce的擴充功能。

如果您已安裝Store Fullment for Adobe Commerce擴充功能的搶鮮版或測試版，請在安裝目前版本之前，使用下列命令將其移除。

```terminal
rm -rf composer.lock vendor/walmart &&
composer require walmart/magento-bopis-metapackage:1.0.0
```

## 安裝需求

- **通過Walmart Commerce Technologies軟體歸檔（.zip檔案）訪問商店完成** — 在入門和啟用程式期間，請與您的客戶經理合作，以存取商店履行擴充功能的安裝檔案。

- **Adobe Commerce帳戶資訊** — 安裝 [!DNL Store Fulfillment] 解決方案需要 [[!DNL Commerce] 帳戶](https://docs.magento.com/user-guide/magento/magento-account.html){target="_blank"}. 您需要帳戶ID和憑證，且擁有 [!DNL Adobe Commerce] 專案。

- 針對 [!DNL Adobe Commerce] 在雲基礎架構項目上，軟體安裝程式必須具有對雲項目的管理員訪問權限。 請參閱 [管理使用者存取](https://devdocs.magento.com/cloud/project/user-admin.html).

- **使用撰寫器和的體驗[!DNL Commerce CLI]** — 請參閱 [一般CLI安裝](https://devdocs.magento.com/extensions/install/){target="_blank"} 如需有關使用這些工具來安裝及管理擴充功能的資訊，請參閱 [!DNL Adobe Commerce] 平台。

- **在Adobe Commerce上安裝協力廠商擴充功能的體驗** — 如需參考，請參閱Adobe Commerce檔案。

   - [在雲端基礎架構例項上安裝Adobe Commerce的擴充功能](https://devdocs.magento.com/cloud/howtos/install-components.html#install-an-extension).

   - [安裝Adobe Commerce內部部署執行個體的擴充功能](https://devdocs.magento.com/extensions/install/).

### 步驟1:下載擴充功能套件組合

請依照您的帳戶代表提供的指示下載包含用於安裝商店履行服務擴展的撰寫器包的存檔檔案。

### 步驟2:將擴充功能成品擷取至您的應用程式

解壓包含整合套件的存檔檔案，以安裝Store Fulfillment Services擴展。

1. 為提取的檔案建立目標目錄。

   - 從命令行，轉到Web伺服器文檔根目錄。

   - 建立 `artifacts` 目錄。

1. 將存檔檔案解壓縮到新目錄。

1. 檢閱檔案清單，確認已成功擷取檔案。

   ```
   ../var/www/html/artifacts]$ ls -a
   .
   ..
   bopis-sdk.zip
   module-magento-bopis-alternate-pickup-contact-admin-ui.zip
   module-magento-bopis-alternate-pickup-contact-api.zip
   ```

### 步驟3:使用撰寫器設定您的應用程式

使用Composer配置安裝的源目錄，並安裝Store Fulfillment Services擴展。

1. 配置源儲存庫以安裝Composer。

   ```bash
   composer config repositories.artifacts artifact artifacts/
   ```

1. 將Store Fulfillment Services擴充功能新增至 `composer.json`.

   ```bash
   composer require walmart/magento-bopis-metapackage:1.0.0
   ```

>[!NOTE]
>
>為了在Adobe Commerce內部部署執行個體上提供更佳效能，您可以 [更新自動載入配置](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/deployment-flow.html#update-the-autoloader): `composer dump-autoload --optimize`

### 步驟4:升級資料庫架構和資料

使用 `bin/magento setup:upgrade` 更新資料庫架構和資料，並更改以支援儲存完成解決方案。

>[!NOTE]
>
>若是雲端基礎架構專案上的Adobe Commerce，您不需要註冊擴充功能。 請改為提交上一步驟的程式碼變更，並將它們推送至您的環境分支。 在雲構建和部署過程中，將自動運行更新資料庫架構和資料的命令。

### 步驟5:完成安裝

1. 使用 `setup:upgrade` MagentoCLI命令。

   ```terminal
   bin/magento setup:upgrade
   ```

1. 如果出現提示，請重新編譯 [!DNL Commerce] 專案。

   ```bash
   bin/magento setup:di:compile
   ```

1. 清除快取。

   ```bash
   bin/magento cache:clean
   ```

1. 禁用維護模式。

   ```bash
   bin/magento maintenance:disable
   ```

### 步驟6:驗證安裝

在Adobe Commerce伺服器中，驗證是否已安裝並啟用Store Fulfillment Services擴展模組。

1. 登入伺服器。

   若要安裝Adobe Commerce雲端基礎架構， [使用SSH登錄遠程環境](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh).

1. 驗證是否已啟用「儲存完成服務」模組。

   ```bash
   bin/magento module:status  --enabled | grep Walmart
   ```

   輸出應包括下列模組：

   ```
   Walmart_BopisBase
   Walmart_BopisAlternatePickupContact
   Walmart_BopisAlternatePickupContactFrontend
   Walmart_BopisApiConnector
   Walmart_BopisAlternatePickupContactAdminUi
   Walmart_BopisCheckoutPickInStoreApi
   Walmart_BopisInventorySourceAdminUi
   Walmart_BopisCheckoutPickInStore
   Walmart_BopisInventoryCatalogApi
   Walmart_BopisPreferredLocationApi
   Walmart_BopisHomeDeliveryApi
   Walmart_BopisHomeDelivery
   Walmart_BopisPreferredLocation
   Walmart_BopisInventoryCatalog
   Walmart_BopisPreferredLocationFrontend
   Walmart_BopisCheckoutPickInStoreAdminUi
   Walmart_BopisInventorySourceApi
   Walmart_BopisInventorySourceFaasSync
   Walmart_BopisInventorySourceReservation
   Walmart_BopisLocationCheckInApi
   Walmart_BopisLogging
   Walmart_BopisStoreAssociateApi
   Walmart_BopisLocationCheckInFrontend
   Walmart_BopisStoreAssociate
   Walmart_BopisOperationQueue
   Walmart_BopisOperationQueueAdminUi
   Walmart_BopisOperationQueueApi
   Walmart_BopisOrderFaasSync
   Walmart_BopisOrderUpdateApi
   Walmart_BopisLocationCheckIn
   Walmart_BopisInventoryCatalogAdminUi
   Walmart_BopisPreferredLocationAdminUi
   Walmart_BopisDeliverySelection
   Walmart_BopisCheckoutPickInStoreFrontend
   Walmart_BopisLocationCheckInAdminUi
   Walmart_BopisStoreAssociateAdminUi
   Walmart_BopisOrderUpdate
   Walmart_BopisStoreAssociateTfa
   Walmart_BopisStoreAssociateTfaApi
   ```

### 其他步驟

如有需要，請使用 [設定:static-content:部署](https://experienceleague.adobe.com/docs/commerce-operations/reference/commerce-on-premises.html){target="_blank"} CLI命令將靜態視圖檔案部署到生產環境。

```terminal
php bin/magento setup:static-content:deploy -f
```

此 `-f` 選項。

>[!NOTE]
>
>如需詳細資訊，請參閱 [靜態內容在Adobe Commerce中部署最佳實務](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/development/static-content-deployment.html) 文章(在Adobe Commerce說明中心)。

