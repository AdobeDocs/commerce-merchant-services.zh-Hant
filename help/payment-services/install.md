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

下載和安裝 [!DNL Payment Services] 擴充功能 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 使用的先決條件步驟 [!DNL Payment Services].

![[!DNL Payment Services] 擴充功能管理檢視](assets/admin-view.png)

## 下載擴充功能

您必須先從下載擴充功能 [Commerce Marketplace](https://experienceleague.adobe.com/docs/commerce-admin/start/resources/commerce-marketplace.html) 安裝之前。

1. 導覽至 [Commerce Marketplace中的支付服務擴充功能](https://marketplace.magento.com/magento-payment-services.html).
1. 若要選擇版本和版本，請切換 **[!UICONTROL Edition]** 和 **[!UICONTROL Your store version]** 至您偏好的選取專案。
1. 按一下 **[!UICONTROL Add to Cart]**.
1. 完成結帳並按一下 **[!UICONTROL Place Order]**.
1. 檢查與您的Marketplace下載相關聯的電子郵件，以取得訂單確認和詳細資訊。

## 安裝擴充功能

您可以安裝 [!DNL Payment Services] 兩者的副檔名 [!DNL Adobe Commerce] 連結至您的Commerce帳戶的雲端基礎結構和內部部署執行個體上 [mageid](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions) 在註冊程式中提供。 [!DNL Magento Open Source] 客戶使用內部部署指示。

Composer會在初始安裝期間使用這些金鑰 [!DNL Adobe Commerce]，或先前未將撰寫器索引鍵儲存至的情況 `auth.json` 檔案。

另請參閱 [取得您的驗證金鑰](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 以取得有關取得撰寫器金鑰的詳細資訊。

另請參閱 [安裝擴充功能](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/extensions.html) 如需在下載和安裝擴充功能之前需考量的詳細資訊。

### [!DNL Adobe Commerce] 在雲端基礎結構上

此方法用於安裝 [!DNL Payment Services] Commerce Cloud例項的擴充功能。

1. 更新您的 `composer.json` 檔案：

   ```bash
   composer require magento/payment-services --no-update
   ```

1. 更新相依性並安裝擴充功能：

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   使用 `composer update` 更新所有根相依性的命令。

1. 提交並推送您的變更。

### 內部部署和其他設定

此方法用於安裝 [!DNL Payment Services] 內部部署執行個體的擴充功能和 [!DNL Magento Open Source] 客戶。

1. 若要取得擴充功能，請執行以下命令：

   ```bash
   composer require magento/payment-services --no-update
   ```

1. 更新相依性並安裝擴充功能：

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   使用 `composer update` 更新所有根相依性的命令。

1. 升級您的執行個體：

   ```bash
   bin/magento setup:upgrade
   ```

1. 清除快取：

   ```bash
   bin/magento cache:clean
   ```

1. 認可變更。
1. 為確保已提交程式碼已部署，請更新您的執行個體。

## 升級擴充功能

當有新版本的 [!DNL Payment Services] 已發行，您可輕鬆升級擴充功能。

1. 若要取得最新版本的套件：

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   使用 `composer update` 更新所有根相依性的命令。

1. 提交並推送您的變更。

## 疑難排除

嘗試安裝時，您可能會看到錯誤 [!DNL Payment Services] 副檔名。 使用下列疑難排解方法來解決錯誤。

### 不正確的撰寫器金鑰

如果您看到以下錯誤，指出您的撰寫器索引鍵不正確：

```terminal
Could not find a matching version of package magento/payment-services. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

確認您的Composer金鑰有效，並且您有權存取其他Magento套件。

若要檢視已設定的撰寫器金鑰：

1. 尋找的位置 `auth.json` 檔案：

   ```bash
   composer config --global home
   ```

1. 檢視 `auth.json` 檔案：

   ```bash
   cat /path/to/auth.json
   ```

1. 另請參閱 [哪些金鑰與您的Commerce帳戶相關聯 `MageID`](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

### PHP的記憶體不足

如果看到以下錯誤，表示您沒有足夠的記憶體來使用PHP：

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[增加記憶體限制](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) 適用於PHP，位於您的環境中 `php.ini`.

或者，您也可以使用此指令指定記憶體限制： `php -d memory_limit=-1 [path to composer]/composer require magento/payment-services`.

例如：

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/payment-services
```
