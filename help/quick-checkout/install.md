---
title: 「安裝 [!DNL Quick Checkout] 適用於Adobe Commerce擴充功能」
description: 「請依照下列步驟安裝 [!DNL Quick Checkout] (位於您的Adobe Commerce專案中)。」
exl-id: e1dabc9a-0ab0-4f8d-98d3-7a32abbedcb8
source-git-commit: d28e8ccd4362b4e32b2eb8c6e1faf38d7c99a4c2
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# 安裝 [!DNL Quick Checkout]

此 [!DNL Quick Checkout] Adobe Commerce和擴充功能 [!DNL Magento Open Source] 可安裝有 [!DNL Composer keys]，連結至Commerce帳戶 [`mageid`](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions){target="_blank"} 在註冊程式中提供。 Composer在Adobe Commerce的初始安裝期間或以下情況下使用這些金鑰： [!DNL Composer keys] 之前未儲存至 `auth.json` 檔案。

另請參閱 [取得您的驗證金鑰](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html){target="_blank"} 主題，以取得相關資訊 [!DNL Composer keys].

安裝此擴充功能的方法有兩種： [雲端基礎結構上的Adobe Commerce](#magento-commerce-cloud) 或 [內部部署](#on-premises) 安裝。 這些方法需要您使用命令列介面(CLI)。

## 更新最低穩定性設定

在安裝擴充功能之前，請確定 `minimum-stability` 中的欄位 `composer.json` 檔案已設定為 `"stable"`：

`"minimum-stability": "stable"`

## 安裝擴充功能

您可以安裝 [!DNL Quick Checkout] 適用於雲端基礎結構及內部部署例項上Adobe Commerce的擴充功能。

### 雲端基礎結構上的Adobe Commerce

此方法用於安裝 [!DNL Quick Checkout] Commerce Cloud例項的擴充功能。

1. 在本機工作站上，變更至雲端專案根目錄。

1. 更新您的 `composer.json` 檔案：

   ```bash
   composer require magento/quick-checkout --no-update
   ```

1. 更新相依性並安裝擴充功能：

   ```bash
   composer update
   ```

   此 `composer update` 命令會更新所有相依性。 如果您不想同時更新所有相依性，請改用此命令： `composer update magento/quick-checkout`.

1. 提交並推送您的變更。

### 內部部署

此方法用於安裝 [!DNL Quick Checkout] 內部部署執行個體的擴充功能。

1. 將「快速簽出」模組新增至 `require` 部分 `composer.json` 檔案：

   ```bash
   composer require magento/quick-checkout --no-update
   ```

1. 更新相依性並安裝擴充功能：

   ```bash
   composer update
   ```

   此 `composer update` 命令會更新所有相依性。 如果您不想同時更新所有相依性，請改用此命令： `composer update magento/quick-checkout`.

1. 升級Adobe Commerce：

   ```bash
   bin/magento setup:upgrade
   ```

1. 清除快取：

   ```bash
   bin/magento cache:clean
   ```

1. 認可變更。
1. 更新您的內部部署執行個體，以確保已提交的程式碼已部署。

## 升級擴充功能

當我們發行新版的 [!DNL Quick Checkout]，即可輕鬆升級擴充功能。

1. 若要取得最新版本的套件：

   ```bash
   composer update
   ```

   此 `composer update` 命令會更新所有相依性。 如果您不想同時更新所有相依性，請改用此命令： `composer update magento/quick-checkout`.

1. 提交並推送您的變更。

## 疑難排除

嘗試安裝時，您可能會看到錯誤 [!DNL Quick Checkout] 副檔名。

如果您在期間遇到任何問題 [!DNL Quick Checkout] 安裝程式，請參閱 [疑難排解Quick Checkout問題](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) (位於Adobe Commerce說明中心)。

## 必要條件

請參閱 [必備條件](../quick-checkout/prerequisites.md) 主題以取得詳細資訊。
