---
title: 安裝 [!DNL Payment Services]
description: 安裝Payments Services擴展。
exl-id: babaa91a-9376-4acb-b934-a89f9df52016
source-git-commit: 4d6c9a3017575e9adbf5dc11cf0717511592dbcf
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# 安裝 [!DNL Payment Services]

下載和安裝 [!DNL Payment Services] 擴展 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 是使用 [!DNL Payment Services]。

![[!DNL Payment Services] 擴展管理員視圖](assets/admin-view.png)

## 下載擴展

必須先從下載擴展 [Commerce Marketplace](https://experienceleague.adobe.com/docs/commerce-admin/start/resources/commerce-marketplace.html) 安裝之前。

1. 導航到 [Commerce Marketplace中的付款服務擴展](https://marketplace.magento.com/magento-payment-services.html)。
1. 要選擇版本和版本，請切換 **[!UICONTROL Edition]** 和 **[!UICONTROL Your store version]** 選擇。
1. 按一下 **[!UICONTROL Add to Cart]**。
1. 完成簽出並按一下 **[!UICONTROL Place Order]**。
1. 檢查與您的Marketplace下載關聯的電子郵件以獲取訂單確認和詳細資訊。

## 安裝擴展

可以安裝 [!DNL Payment Services] 擴展 [!DNL Adobe Commerce] 在雲基礎架構和內部實例上，這些實例與您的Commerce帳戶連結 [馬吉德](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions) 在註冊過程中提供。 [!DNL Magento Open Source] 客戶使用內部說明。

Composer在初始安裝時使用這些鍵 [!DNL Adobe Commerce]，或在以前未將Composer鍵保存到 `auth.json` 的子菜單。

請參閱 [獲取您的身份驗證密鑰](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 的子菜單。

請參閱 [安裝擴展](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/extensions.html) 的子菜單。

### [!DNL Adobe Commerce] 雲基礎架構

此方法用於安裝 [!DNL Payment Services] Commerce Cloud實例的擴展。

1. 更新 `composer.json` 檔案：

   ```bash
   composer require magento/payment-services --no-update
   ```

1. 更新依賴項並安裝擴展：

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   使用 `composer update` 命令以更新所有根依賴關係。

1. 提交並推送更改。

### 本地和其他配置

此方法用於安裝 [!DNL Payment Services] 本地實例的擴展和 [!DNL Magento Open Source] 客戶。

1. 要獲取擴展，請運行以下命令：

   ```bash
   composer require magento/payment-services --no-update
   ```

1. 更新依賴項並安裝擴展：

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   使用 `composer update` 命令以更新所有根依賴關係。

1. 升級實例：

   ```bash
   bin/magento setup:upgrade
   ```

1. 清除快取：

   ```bash
   bin/magento cache:clean
   ```

1. 提交更改。
1. 要確保部署已提交的代碼，請更新實例。

## 升級擴展

當 [!DNL Payment Services] 已發佈，您可以輕鬆升級擴展。

1. 要獲取包的最新版本，請執行以下操作：

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   使用 `composer update` 命令以更新所有根依賴關係。

1. 提交並推送更改。

## 故障排除

您可能在嘗試安裝 [!DNL Payment Services] 擴展。 使用以下故障排除方法來解決錯誤。

### 合成器鍵不正確

如果您看到以下錯誤，表示您的Composer鍵不正確：

```terminal
Could not find a matching version of package magento/payment-services. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

驗證您的Composer密鑰是否有效，並且您有權訪問其他Magento包。

要查看配置了哪些Composer鍵：

1. 查找 `auth.json` 檔案：

   ```bash
   composer config --global home
   ```

1. 查看 `auth.json` 檔案：

   ```bash
   cat /path/to/auth.json
   ```

1. 請參閱 [與您的商務帳戶關聯的鍵 `MageID`](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html)。

### 記憶體不足，無法用於PHP

如果出現以下錯誤，表示您沒有足夠的記憶體用於PHP:

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[增加記憶體限制](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) 在您的環境中 `php.ini`。

或者，可以使用以下命令指定記憶體限制： `php -d memory_limit=-1 [path to composer]/composer require magento/payment-services`。

例如：

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/payment-services
```
