---
title: 安裝 [!DNL Payment Services]
description: 安裝Payments Services擴展。
exl-id: babaa91a-9376-4acb-b934-a89f9df52016
source-git-commit: bcb817775fe9cd9ac7096931dd40d5ec0c4a5cfc
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---

# 安裝 [!DNL Payment Services]

安裝 [!DNL Payment Services] Adobe Commerce和Magento Open Source的擴展是使用 [!DNL Payment Services]。

![[!DNL Payment Services] 擴展管理員視圖](assets/admin-view.png)

的 [!DNL Payment Services] Adobe Commerce和Magento Open Source的擴展可以與連結到MagentoID([馬吉德](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions) 在註冊過程中提供。 Composer在初始安裝Adobe Commerce時或在以前未將Composer鍵保存到 `auth.json` 的子菜單。

請參閱 [獲取您的身份驗證密鑰](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 的子菜單。

安裝此擴展有兩種方法 —  [Adobe Commerce在雲基礎架構上](https://devdocs.magento.com/payment-services/install-payments.html#magento-commerce-cloud) 或 [內部](https://devdocs.magento.com/payment-services/install-payments.html#on-premises) 安裝。 這些方法要求您使用命令行介面(CLI)。

## 更新最小穩定性設定

安裝擴展之前，必須更改 `minimum-stability` 要求 `RC` （釋放候選人） `composer.json` 的子菜單。 可以使用IDE或您最喜愛的文本編輯器（如Visual Studio Code或「崇高文本」）。

在 `composer.json` 檔案，更改 `"minimum-stability": "stable"` 至 `"minimum-stability": "RC"`。

## 安裝擴展

可以安裝 [!DNL Payment Services] 在雲基礎架構和內部實例上擴展Adobe Commerce。

### Adobe Commerce在雲基礎架構上

此方法用於安裝 [!DNL Payment Services] Commerce Cloud實例的擴展。

1. 更新 `composer.json` 檔案：

   ```bash
   composer require magento/payment-services --no-update
   ```

1. 更新依賴項並安裝擴展：

   ```bash
   composer update
   ```

   的 `composer update` 命令更新所有依賴關係。 如果不想同時更新所有依賴關係，請改用以下命令： `composer require magento/payment-services`。

1. 提交並推送更改。

### 內部

此方法用於安裝 [!DNL Payment Services] 本地實例的擴展。

1. 要獲取擴展，請運行以下命令：

   ```bash
   composer require magento/payment-services --no-update
   ```

1. 更新依賴項並安裝擴展：

   ```bash
   composer update
   ```

   的 `composer update` 命令更新所有依賴關係。 如果不想同時更新所有依賴關係，請改用以下命令： `composer require magento/payment-services`。

1. 升級Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. 清除快取：

   ```bash
   bin/magento cache:clean
   ```

1. 提交更改。
1. 要確保部署已提交的代碼，請更新您的本地實例。

## 升級擴展

當 [!DNL Payment Services] 已發佈，您可以輕鬆升級擴展。

1. 要獲取包的最新版本，請執行以下操作：

   ```bash
   composer update
   ```

   的 `composer update` 命令更新所有依賴關係。 如果不想同時更新所有依賴關係，請改用以下命令： `composer update magento/payment-services`。

1. 提交並推送更改。

## 故障排除

您可能在嘗試安裝 [!DNL Payment Services] 擴展。 使用以下故障排除方法來解決錯誤。

### 合成器鍵不正確

如果您看到以下錯誤，表示您的Composer鍵不正確：

```terminal
Could not find a matching version of package magento/payment-services. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

驗證您的Composer鍵是否連結到在Composer中使用的MagentoID [!DNL Payment Services] 註冊。

要查看配置了哪些Composer鍵：

1. 查找 `auth.json` 檔案：

   ```bash
   composer config --global home
   ```

1. 查看 `auth.json` 檔案：

   ```bash
   cat /path/to/auth.json
   ```

1. 請參閱 [與您的MagentoID關聯的鍵](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html)。

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
