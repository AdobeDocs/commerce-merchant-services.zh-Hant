---
title: 安裝 [!DNL Payment Services]
description: 安裝Payments Services擴充功能。
exl-id: babaa91a-9376-4acb-b934-a89f9df52016
source-git-commit: 4d6c9a3017575e9adbf5dc11cf0717511592dbcf
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# 安裝 [!DNL Payment Services]

下載和安裝 [!DNL Payment Services] 擴充功能 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 是使用的先決條件步驟 [!DNL Payment Services].

![[!DNL Payment Services] 擴充功能管理檢視](assets/admin-view.png)

## 下載擴充功能

您必須先從下載擴充功能 [Commerce Marketplace](https://experienceleague.adobe.com/docs/commerce-admin/start/resources/commerce-marketplace.html) 安裝之前。

1. 導覽至 [Commerce Marketplace中的Payment Services擴展](https://marketplace.magento.com/magento-payment-services.html).
1. 若要選擇版本和版本，請切換 **[!UICONTROL Edition]** 和 **[!UICONTROL Your store version]** 到您偏好的選取項目。
1. 按一下 **[!UICONTROL Add to Cart]**.
1. 完成結帳並按一下 **[!UICONTROL Place Order]**.
1. 查看與您的Marketplace下載相關的電子郵件，以取得訂單確認和詳細資訊。

## 安裝擴充功能

您可以安裝 [!DNL Payment Services] 兩者的擴充功能 [!DNL Adobe Commerce] 雲基礎架構和內部部署實例，這些實例連結到您的Commerce帳戶 [馬吉德](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions) 在註冊過程中提供。 [!DNL Magento Open Source] 客戶使用內部部署指示。

撰寫器在初始安裝期間使用這些金鑰 [!DNL Adobe Commerce]，或在撰寫器金鑰先前未儲存至的情況下 `auth.json` 檔案。

請參閱 [取得驗證金鑰](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 以取得關於取得撰寫器金鑰的詳細資訊。

請參閱 [安裝擴充功能](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/extensions.html) 以取得下載和安裝擴充功能前，應考慮事項的詳細資訊。

### [!DNL Adobe Commerce] 雲基礎架構

此方法用於安裝 [!DNL Payment Services] Commerce Cloud例項的擴充功能。

1. 更新您的 `composer.json` 檔案：

   ```bash
   composer require magento/payment-services --no-update
   ```

1. 更新相依性並安裝擴充功能：

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   使用 `composer update` 命令更新所有根依賴項。

1. 提交並推送您的變更。

### 內部部署和其他配置

此方法用於安裝 [!DNL Payment Services] 內部部署實例和 [!DNL Magento Open Source] 客戶。

1. 若要取得擴充功能，請執行下列命令：

   ```bash
   composer require magento/payment-services --no-update
   ```

1. 更新相依性並安裝擴充功能：

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   使用 `composer update` 命令更新所有根依賴項。

1. 升級您的執行個體：

   ```bash
   bin/magento setup:upgrade
   ```

1. 清除快取：

   ```bash
   bin/magento cache:clean
   ```

1. 提交更改。
1. 若要確保已部署已提交的程式碼，請更新您的執行個體。

## 升級擴充功能

若 [!DNL Payment Services] 發行後，您就可輕鬆升級擴充功能。

1. 若要取得套件的最新版本：

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   使用 `composer update` 命令更新所有根依賴項。

1. 提交並推送您的變更。

## 疑難排解

嘗試安裝時，您可能會看到錯誤 [!DNL Payment Services] 擴充功能。 使用下列疑難排解方法來解決錯誤。

### 撰寫器密鑰不正確

如果您看見下列錯誤，指出您有不正確的撰寫器金鑰：

```terminal
Could not find a matching version of package magento/payment-services. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

確認您的撰寫器金鑰有效，且您擁有其他Magento套件的存取權。

若要查看已設定哪些撰寫器金鑰：

1. 尋找 `auth.json` 檔案：

   ```bash
   composer config --global home
   ```

1. 檢視 `auth.json` 檔案：

   ```bash
   cat /path/to/auth.json
   ```

1. 請參閱 [與您的商務帳戶相關聯的金鑰 `MageID`](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

### 記憶體不足，無法用於PHP

如果您看到以下錯誤，表示您沒有足夠的記憶體用於PHP:

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[增加記憶體限制](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) 的PHP `php.ini`.

或者，您也可以使用以下命令指定記憶體限制： `php -d memory_limit=-1 [path to composer]/composer require magento/payment-services`.

例如：

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/payment-services
```
