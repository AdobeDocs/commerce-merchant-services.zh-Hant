---
title: '"安裝 [!DNL Quick Checkout] Adobe Commerce分機」'
description: 「按照這些步驟安裝 [!DNL Quick Checkout] 你的Adobe Commerce計畫"
exl-id: e1dabc9a-0ab0-4f8d-98d3-7a32abbedcb8
source-git-commit: d28e8ccd4362b4e32b2eb8c6e1faf38d7c99a4c2
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# 安裝 [!DNL Quick Checkout]

的 [!DNL Quick Checkout] Adobe Commerce和 [!DNL Magento Open Source] 可安裝 [!DNL Composer keys]，它們與Commerce帳戶連結 [`mageid`](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions){target="_blank"} 在註冊過程中提供。 Composer在初始安裝Adobe Commerce時或在 [!DNL Composer keys] 以前未保存到 `auth.json` 的子菜單。

請參閱 [獲取身份驗證密鑰](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html){target="_blank"} 主題有關獲取的詳細資訊 [!DNL Composer keys]。

安裝此擴展有兩種方法 —  [Adobe Commerce在雲基礎架構上](#magento-commerce-cloud) 或 [本地](#on-premises) 安裝。 這些方法要求您使用命令行介面(CLI)。

## 更新最小穩定性設定

安裝擴展之前，請確保 `minimum-stability` 的 `composer.json` 檔案設定為 `"stable"`:

`"minimum-stability": "stable"`

## 安裝擴展

可以安裝 [!DNL Quick Checkout] 在雲基礎架構和內部實例上擴展Adobe Commerce。

### Adobe Commerce在雲基礎架構上

此方法用於安裝 [!DNL Quick Checkout] Commerce Cloud實例的擴展。

1. 在本地工作站上，更改為雲項目根目錄。

1. 更新 `composer.json` 檔案：

   ```bash
   composer require magento/quick-checkout --no-update
   ```

1. 更新依賴項並安裝擴展：

   ```bash
   composer update
   ```

   的 `composer update` 命令更新所有依賴關係。 如果不想同時更新所有依賴關係，請改用以下命令： `composer update magento/quick-checkout`。

1. 提交並推送更改。

### 內部

此方法用於安裝 [!DNL Quick Checkout] 本地實例的擴展。

1. 將「快速簽出」模組添加到 `require` 的下界 `composer.json` 檔案：

   ```bash
   composer require magento/quick-checkout --no-update
   ```

1. 更新依賴項並安裝擴展：

   ```bash
   composer update
   ```

   的 `composer update` 命令更新所有依賴關係。 如果不想同時更新所有依賴關係，請改用以下命令： `composer update magento/quick-checkout`。

1. 升級Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. 清除快取：

   ```bash
   bin/magento cache:clean
   ```

1. 提交更改。
1. 更新您的內部實例，以確保部署已提交的代碼。

## 升級擴展

當我們發佈 [!DNL Quick Checkout]，您可以輕鬆升級擴展。

1. 要獲取包的最新版本，請執行以下操作：

   ```bash
   composer update
   ```

   的 `composer update` 命令更新所有依賴關係。 如果不想同時更新所有依賴關係，請改用以下命令： `composer update magento/quick-checkout`。

1. 提交並推送更改。

## 故障排除

您可能在嘗試安裝 [!DNL Quick Checkout] 擴展。

如果您在 [!DNL Quick Checkout] 安裝過程，請參見 [排除快速簽出問題](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) 在Adobe Commerce幫助中心。

## 先決條件

查看 [先決條件](../quick-checkout/prerequisites.md) 的子菜單。
