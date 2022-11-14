---
title: '"安裝 [!DNL Quick Checkout] 適用於Adobe Commerce擴充功能」'
description: 「請依照下列步驟安裝 [!DNL Quick Checkout] 在您的Adobe Commerce專案中。」
exl-id: e1dabc9a-0ab0-4f8d-98d3-7a32abbedcb8
source-git-commit: d28e8ccd4362b4e32b2eb8c6e1faf38d7c99a4c2
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# 安裝 [!DNL Quick Checkout]

此 [!DNL Quick Checkout] Adobe Commerce和 [!DNL Magento Open Source] 可與 [!DNL Composer keys]，連結至商務帳戶 [`mageid`](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions)註冊過程中提供的{target=&quot;_blank&quot;}。 撰寫器在初始安裝Adobe Commerce期間或在 [!DNL Composer keys] 之前未儲存至 `auth.json` 檔案。

請參閱 [獲取驗證密鑰](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html){target=&quot;_blank&quot;}主題，以了解有關獲取的詳細資訊 [!DNL Composer keys].

安裝此擴充功能有兩種方式： [Adobe Commerce雲基礎架構](#magento-commerce-cloud) 或 [內部](#on-premises) 安裝。 這些方法要求您使用命令行介面(CLI)。

## 更新最小穩定性設定

安裝擴充功能前，請確定 `minimum-stability` 欄位 `composer.json` 檔案設為 `"stable"`:

`"minimum-stability": "stable"`

## 安裝擴充功能

您可以安裝 [!DNL Quick Checkout] 雲端基礎架構和內部部署執行個體上Adobe Commerce的擴充功能。

### Adobe Commerce雲基礎架構

此方法用於安裝 [!DNL Quick Checkout] Commerce Cloud例項的擴充功能。

1. 在本機工作站上，變更為雲端專案根目錄。

1. 更新您的 `composer.json` 檔案：

   ```bash
   composer require magento/quick-checkout --no-update
   ```

1. 更新相依性並安裝擴充功能：

   ```bash
   composer update
   ```

   此 `composer update` 命令更新所有依賴項。 如果您不想同時更新所有相依性，請改用以下命令： `composer update magento/quick-checkout`.

1. 提交並推送您的變更。

### 內部部署

此方法用於安裝 [!DNL Quick Checkout] 內部部署實例的擴展。

1. 將快速結帳模組新增至 `require` 區段 `composer.json` 檔案：

   ```bash
   composer require magento/quick-checkout --no-update
   ```

1. 更新相依性並安裝擴充功能：

   ```bash
   composer update
   ```

   此 `composer update` 命令更新所有依賴項。 如果您不想同時更新所有相依性，請改用以下命令： `composer update magento/quick-checkout`.

1. 升級Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. 清除快取：

   ```bash
   bin/magento cache:clean
   ```

1. 提交更改。
1. 更新您的內部部署執行個體，以確保已部署已提交的程式碼。

## 升級擴充功能

當我們發行 [!DNL Quick Checkout]，您可以輕鬆升級擴充功能。

1. 若要取得套件的最新版本：

   ```bash
   composer update
   ```

   此 `composer update` 命令更新所有依賴項。 如果您不想同時更新所有相依性，請改用以下命令： `composer update magento/quick-checkout`.

1. 提交並推送您的變更。

## 疑難排解

嘗試安裝時，您可能會看到錯誤 [!DNL Quick Checkout] 擴充功能。

若您在 [!DNL Quick Checkout] 安裝程式，請參閱 [疑難排解快速結帳問題](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) Adobe Commerce幫助中心。

## 必要條件

請參閱 [必要條件](../quick-checkout/prerequisites.md) 主題以取得詳細資訊。
