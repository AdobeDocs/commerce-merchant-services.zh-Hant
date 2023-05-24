---
title: 安裝
description: 「安裝 [!DNL Store Fulfillment solution] 使用Composer for PHP的Adobe Commerce店面。」
role: User, Admin
level: Intermediate
exl-id: 6613268a-7d22-4c54-af89-834921b7f262
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 0%

---


# 安裝

完成初始安裝 [!DNL Store Fulfillment for Adobe Commerce by Walmart Commerce Technologies] 在非生產環境中執行佇列管理員，並將快取設定為允許例外狀況處理的擴充功能。 確保您的開發環境包含開發工具，以確保操作和維護您的Adobe Commerce執行個體的最佳實務。

## 必要條件

檢閱 [需求](solution-requirements.md) ，並在安裝之前收集所需的資訊 [!DNL Store Fulfillment] Adobe Commerce的擴充功能。

如果您已安裝Adobe Commerce擴充功能的市集履行搶鮮版或測試版，請先使用以下命令將其移除，然後再安裝目前版本。

```terminal
rm -rf composer.lock vendor/walmart &&
composer require walmart/magento-bopis-metapackage:1.0.0
```

## 安裝需求

- **存取Walmart Commerce Technologies軟體封存（.zip檔案）的「商店履行」** — 在上線和啟用程式期間，請洽詢您的客戶經理，以存取Store Fulfillment擴充功能的安裝檔案。

- **Adobe Commerce帳戶資訊** — 安裝 [!DNL Store Fulfillment] 解決方案需要 [[!DNL Commerce] 帳戶](https://docs.magento.com/user-guide/magento/magento-account.html){target="_blank"}. 您需要帳戶ID和憑證，以及擁有該帳戶擁有者或管理員許可權的 [!DNL Adobe Commerce] 專案。

- 對象 [!DNL Adobe Commerce] 在雲端基礎結構專案上，軟體安裝程式必須擁有雲端專案的管理員存取權。 另請參閱 [管理使用者存取權](https://devdocs.magento.com/cloud/project/user-admin.html).

- **使用撰寫器和的體驗[!DNL Commerce CLI]** — 請參閱 [一般CLI安裝](https://devdocs.magento.com/extensions/install/){target="_blank"} 如需使用這些工具來安裝及管理擴充功能的相關資訊，請參閱 [!DNL Adobe Commerce] 平台。

- **在Adobe Commerce上安裝協力廠商擴充功能的經驗** — 如需參考，請參閱Adobe Commerce檔案。

   - [在雲端基礎結構執行個體上安裝Adobe Commerce的擴充功能](https://devdocs.magento.com/cloud/howtos/install-components.html#install-an-extension).

   - [安裝Adobe Commerce內部部署執行個體的擴充功能](https://devdocs.magento.com/extensions/install/).

### 步驟1：下載擴充功能套件組合

按照您的帳戶代表提供的指示，下載包含用於安裝Store Fulfillment Services擴充功能之Composer套件的封存檔案。

### 步驟2：將擴充功能成品擷取至您的應用程式

解壓縮包含整合套件的封存檔案，以安裝Store Fulfillment Services擴充功能。

1. 為擷取的檔案建立目標目錄。

   - 從命令列，前往網頁伺服器doc根目錄。

   - 建立 `artifacts` 目錄。

1. 將封存檔案解壓縮至新目錄。

1. 檢閱檔案清單，確認檔案已成功擷取。

   ```
   ../var/www/html/artifacts]$ ls -a
   .
   ..
   bopis-sdk.zip
   module-magento-bopis-alternate-pickup-contact-admin-ui.zip
   module-magento-bopis-alternate-pickup-contact-api.zip
   ```

### 步驟3：使用撰寫器設定您的應用程式

使用Composer設定安裝的來源目錄，並安裝Store Fulfillment Services擴充功能。

1. 設定Composer安裝的來源存放庫。

   ```bash
   composer config repositories.artifacts artifact artifacts/
   ```

1. 將Store Fulfillment Services延伸新增至 `composer.json`.

   ```bash
   composer require walmart/magento-bopis-metapackage:1.0.0
   ```

>[!NOTE]
>
>若要在Adobe Commerce內部部署執行個體上獲得更好的效能，您可以 [更新自動載入設定](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/deployment-flow.html#update-the-autoloader)： `composer dump-autoload --optimize`

### 步驟4：升級資料庫結構和資料

使用完成安裝 `bin/magento setup:upgrade` 以更新資料庫架構和資料，並變更以支援「商店履行」解決方案。

>[!NOTE]
>
>對於雲端基礎結構專案上的Adobe Commerce，您不需要註冊擴充功能。 請改為提交上一步驟的程式碼變更，並將其推送到您的環境分支。 更新資料庫架構和資料的命令會在雲端建置和部署過程中自動執行。

### 步驟5：完成安裝

1. 使用Adobe Commerce註冊擴充功能 `setup:upgrade` MagentoCLI命令。

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

1. 停用維護模式。

   ```bash
   bin/magento maintenance:disable
   ```

### 步驟6：驗證安裝

從Adobe Commerce伺服器，確認已安裝並啟用Store Fulfillment Services擴充功能的模組。

1. 登入伺服器。

   如需在雲端基礎結構上安裝Adobe Commerce， [使用SSH登入遠端環境](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh).

1. 確認「商店履行服務」模組已啟用。

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

如有需要，請使用 [設定:static-content:部署](https://experienceleague.adobe.com/docs/commerce-operations/reference/commerce-on-premises.html){target="_blank"} 用於將靜態檢視檔案部署到生產環境的CLI命令。

```terminal
php bin/magento setup:static-content:deploy -f
```

此 `-f` 如果您使用空白主題，則必須使用選項。

>[!NOTE]
>
>如需詳細資訊，請參閱 [Adobe Commerce中的靜態內容部署最佳實務](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/development/static-content-deployment.html) Adobe Commerce說明中心的文章。

