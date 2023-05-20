---
title: 安裝
description: '"安裝 [!DNL Store Fulfillment solution] 使用Composer for PHP的Adobe Commerce店面。」'
role: User, Admin
level: Intermediate
exl-id: 6613268a-7d22-4c54-af89-834921b7f262
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 0%

---


# 安裝

完成初始安裝 [!DNL Store Fulfillment for Adobe Commerce by Walmart Commerce Technologies] 在非生產環境中擴展，隊列管理器運行並快取配置為允許異常處理。 確保您的開發環境包括開發工具，以確保操作和維護您的Adobe Commerce實例的最佳做法。

## 先決條件

查看 [要求](solution-requirements.md) 在您安裝 [!DNL Store Fulfillment] 延期到Adobe Commerce。

如果已安裝用於Adobe Commerce擴展的Store Fulfillment的預發行版或測試版，請在安裝當前版本之前使用以下命令將其刪除。

```terminal
rm -rf composer.lock vendor/walmart &&
composer require walmart/magento-bopis-metapackage:1.0.0
```

## 安裝要求

- **Walmart Commerce Technologies軟體存檔（.zip檔案）對商店訂單的訪問** — 在啟動和啟用過程中，請與客戶經理合作，以訪問儲存完成擴展的安裝檔案。

- **Adobe Commerce帳戶資訊** — 安裝 [!DNL Store Fulfillment] 解決方案需要 [[!DNL Commerce] 帳戶](https://docs.magento.com/user-guide/magento/magento-account.html){target="_blank"}。 您需要具有「所有者」或「管理員」訪問權限的帳戶ID和憑據 [!DNL Adobe Commerce] 項目。

- 對於 [!DNL Adobe Commerce] 在雲基礎架構項目上，軟體安裝程式必須具有對雲項目的管理員權限。 請參閱 [管理用戶訪問](https://devdocs.magento.com/cloud/project/user-admin.html)。

- **使用Composer和[!DNL Commerce CLI]** — 請參閱 [常規CLI安裝](https://devdocs.magento.com/extensions/install/){target="_blank"} 有關使用這些工具在上安裝和配置擴展的資訊 [!DNL Adobe Commerce] 平台。

- **在Adobe Commerce安裝第三方擴展的體驗** — 有關參考，請參閱Adobe Commerce文檔。

   - [在雲基礎架構實例上安裝Adobe Commerce的擴展](https://devdocs.magento.com/cloud/howtos/install-components.html#install-an-extension)。

   - [為Adobe Commerce本地實例安裝擴展](https://devdocs.magento.com/extensions/install/)。

### 步驟1:下載擴展包

按照您的客戶代表提供的說明下載包含用於安裝Store Fulfilment Services擴展的Composer軟體包的存檔檔案。

### 步驟2:將擴展對象提取到應用程式

提取包含整合包的存檔檔案以安裝Store Fulfilment Services擴展。

1. 為提取的檔案建立目標目錄。

   - 從命令行轉到Web伺服器文檔根目錄。

   - 建立 `artifacts` 的子菜單。

1. 將存檔檔案解壓到新目錄。

1. 通過查看檔案清單，驗證是否成功提取了檔案。

   ```
   ../var/www/html/artifacts]$ ls -a
   .
   ..
   bopis-sdk.zip
   module-magento-bopis-alternate-pickup-contact-admin-ui.zip
   module-magento-bopis-alternate-pickup-contact-api.zip
   ```

### 第3步：使用Composer配置你的應用

使用Composer配置安裝的源目錄並安裝Store Fulfilment Services擴展。

1. 配置Composer安裝的源儲存庫。

   ```bash
   composer config repositories.artifacts artifact artifacts/
   ```

1. 將Store Fulfillment Services擴展添加到 `composer.json`。

   ```bash
   composer require walmart/magento-bopis-metapackage:1.0.0
   ```

>[!NOTE]
>
>為了在Adobe Commerce內部實例上獲得更佳效能，您可以 [更新自動載入配置](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/deployment-flow.html#update-the-autoloader): `composer dump-autoload --optimize`

### 第4步：升級資料庫架構和資料

使用 `bin/magento setup:upgrade` 用更改來更新資料庫模式和資料，以支援儲存履行解決方案。

>[!NOTE]
>
>對於Adobe Commerce的雲基礎架構項目，您不必註冊擴展。 相反，提交上一步中的代碼更改，並將它們推送到您的環境分支。 在雲構建和部署過程中，自動更新資料庫架構和資料的命令將自動運行。

### 第5步：完成安裝

1. 使用 `setup:upgrade` MagentoCLI命令。

   ```terminal
   bin/magento setup:upgrade
   ```

1. 如果出現提示，請重新編譯 [!DNL Commerce] 項目。

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

在Adobe Commerce伺服器上，驗證是否已安裝並啟用了Store Fullimment Services擴展模組。

1. 登錄到伺服器。

   對於在Adobe Commerce的雲基礎架構上安裝， [使用SSH登錄到遠程環境](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh)。

1. 驗證是否啟用了Store Fullimment Services模組。

   ```bash
   bin/magento module:status  --enabled | grep Walmart
   ```

   輸出應包括以下模組：

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

如果需要，請使用 [設定:static-content:部署](https://experienceleague.adobe.com/docs/commerce-operations/reference/commerce-on-premises.html){target="_blank"} CLI命令，用於將靜態視圖檔案部署到生產環境。

```terminal
php bin/magento setup:static-content:deploy -f
```

的 `-f` 的子菜單。

>[!NOTE]
>
>有關詳細資訊，請參見 [靜態內容部署Adobe Commerce最佳做法](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/development/static-content-deployment.html) 在Adobe Commerce幫助中心。

