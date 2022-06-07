---
title: 「故障排除 [!DNL Quick Checkout]"
description: 「疑難解答錯誤，您在使用 [!DNL Quick Checkout] Adobe Commerce分機"
exl-id: a379ff81-360d-4cb9-a123-47e8cbc0cdbd
source-git-commit: 9841db7616c8aa6d5bc5af3e6e92c0abe9a4a1e2
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# 故障排除 [!DNL Quick Checkout] 為Adobe Commerce

使用以下故障排除方法來解決這些特定問題。

## 錯誤 [!DNL Composer keys]

如果您看到以下錯誤，表示您有錯誤 [!DNL Composer keys]:

```terminal
Could not find a matching version of package magento/quick-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (RC).
```

驗證 [!DNL Composer keys] 連結到「快速簽出」註冊期間使用的MagentoID。

查看 [!DNL Composer keys] 已配置：

1. 查找 `auth.json` 檔案：

   ```bash
   composer config --global home
   ```

1. 查看 `auth.json` 檔案：

   ```bash
   cat /path/to/auth.json
   ```

1. 請參閱 [與您的MagentoID關聯的鍵](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html)。

## 在 `composer.json` 設定為穩定

如果您看到以下錯誤，表示您有錯誤 [!DNL Composer keys]:

```terminal
Could not find a matching version of package magento/quick-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

將最小穩定性設定為 `RC` 的 `composer.json` 的子菜單。

## 記憶體不足，無法用於PHP

如果出現以下錯誤，表示您沒有足夠的記憶體用於PHP:

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[增加記憶體限制](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) 在您的環境中 `php.ini`。

或者，可以使用以下命令指定記憶體限制： `php -d memory_limit=-1 [path to composer]/composer require magento/quick-checkout`。

例如：

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/quick-checkout
```

## 無效的裝運地址

有已知問題 [!DNL Quick Checkout]。

當預設發運地址無效時，客戶將重定向到發運地址步驟。 Storefront僅顯示有效的發運地址。

>[!WARNING]
>
> 如果沒有有效的發運地址，客戶將看不到任何可用的發運地址。

請參閱 [發運詳細資訊](../quick-checkout/shipping-details.md) 的子菜單。

## 添加具有新發運地址的街道地址行

有已知問題 [!DNL Quick Checkout]。

當你 [使用登錄 [!DNL Bolt] 帳戶](https://help.bolt.com/shoppers/guides/checkout/log-in/) 您可以添加新的發運地址，每個街道地址最多4行。

Adobe Commerce通常可以配置為支援多達20條街道地址線。

## 複選框 `enable terms and conditions` 未正確顯示

有已知問題 [!DNL Quick Checkout]。

啟用 `Enable terms and conditions` 複選框，然後使用 [!DNL Bolt] 帳戶， `Enable terms and conditions` 複選框在簽出過程中不顯示。 請參閱 [登錄](https://help.bolt.com/shoppers/account/login-dashboard/) [!DNL Bolt] 的子菜單。

請參閱 [條款和條件](https://docs.magento.com/user-guide/sales/terms-and-conditions.html) 主題，瞭解有關管理配置的詳細資訊。

## 意外行為 `Display Billing Address On` 設定為 `payment page`

有已知問題 [!DNL Quick Checkout]。

如果您設定 `Display Billing Address On` 參數 `payment page` 和 [使用 [!DNL Bolt] 帳戶](https://help.bolt.com/shoppers/guides/checkout/log-in/) 當您檢查 `My billing and shipping address are the same` 複選框 `use existing card`。

![同一地址](assets/checked-address.png)

查看 [簽出](https://docs.magento.com/user-guide/configuration/sales/checkout.html) 主題，瞭解有關 `Display Billing Address On` 的下界。

## 翻譯 [!DNL Quick Checkout] 擴展

Adobe Commerce使您能夠將您的商店本地化為多個地區和市場。 您甚至可以在「管理員」視圖中本地化錯誤消息。

請參閱 [翻譯和本地化](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/xlate.html) 的子菜單。

## 刷新快取

1. 導航到 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 按一下 **[!UICONTROL Flush Cache]** 刷新所有無效的快取。

## 獲取幫助

聯繫人 [Adobe Commerce支援](mailto:quick-checkout-support@adobe.com) 尋求幫助。
