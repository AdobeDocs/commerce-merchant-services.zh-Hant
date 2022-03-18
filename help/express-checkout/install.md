---
title: 安裝 [!DNL Express Checkout] Adobe Commerce分機
description: 按照以下步驟安裝 [!DNL Upgrade Compatibility Tool] 你的Adobe Commerce計畫。
exl-id: e1dabc9a-0ab0-4f8d-98d3-7a32abbedcb8
source-git-commit: 163dd5260908b4ea3a8bfbcfdb834531d1603734
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# 安裝 [!DNL Express Checkout]

>[!IMPORTANT]
>
> 此功能僅適用於早期採用者計畫(EAP)用戶，尚不適用於所有客戶。 目前僅限於美國客戶。 請聯繫Adobe Commerce支援部門以獲取幫助和問題。

的 [!DNL Express Checkout] 對於Adobe Commerce來說，它提供了無縫的結賬體驗，旨在將一次性客戶轉變為忠誠的賬戶持有者。

的 [!DNL Express Checkout] Adobe Commerce和Magento Open Source的擴展可以安裝Composer鍵，該鍵連結到 [MagentoID(mageid)](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions)在註冊過程中提供的{target=&quot;_blank&quot;}。 Composer在初始安裝Adobe Commerce時或在以前未將Composer鍵保存到 `auth.json` 的子菜單。

請參閱 [獲取身份驗證密鑰](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html){target=&quot;_blank&quot;}，瞭解有關獲取Composer鍵的詳細資訊。

安裝此擴展有兩種方法 —  [Adobe Commerce在雲基礎架構上](#magento-commerce-cloud) 或 [本地](#on-premises) 安裝。 這些方法要求您使用命令行介面(CLI)。

## 更新最小穩定性設定

在安裝擴展之前，可以更改 `minimum-stability` 要求 `RC` （釋放候選人） `composer.json` 的子菜單。 可以使用IDE或您最喜愛的文本編輯器（如Visual Studio Code或「崇高文本」）。

在 `composer.json` 檔案，更改 `"minimum-stability": "stable"` 至 `"minimum-stability": "RC"`。

## 安裝擴展

可以安裝 [!DNL Express Checkout] 在雲基礎架構和內部實例上擴展Adobe Commerce。

### Adobe Commerce在雲基礎架構上

此方法用於安裝 [!DNL Express Checkout] Commerce Cloud實例的擴展。

1. 在本地工作站上，更改為雲項目根目錄。

1. 更新 `composer.json` 檔案：

   ```bash
   composer require magento/express-checkout --no-update
   ```

1. 更新依賴項並安裝擴展：

   ```bash
   composer update
   ```

   的 `composer update` 命令更新所有依賴關係。 如果不想同時更新所有依賴關係，請改用以下命令： `composer update magento/express-checkout`。

1. 提交並推送更改。

### 內部

此方法用於安裝 [!DNL Express Checkout] 本地實例的擴展。

1. 將快速簽出模組添加到 `require` 的下界 `composer.json` 檔案：

   ```bash
   composer require magento/express-checkout --no-update
   ```

1. 更新依賴項並安裝擴展：

   ```bash
   composer update
   ```

   的 `composer update` 命令更新所有依賴關係。 如果不想同時更新所有依賴關係，請改用以下命令： `composer update magento/express-checkout`。

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

當我們發佈 [!DNL Express Checkout]，您可以輕鬆升級擴展。

1. 要獲取包的最新版本，請執行以下操作：

   ```bash
   composer update
   ```

   的 `composer update` 命令更新所有依賴關係。 如果不想同時更新所有依賴關係，請改用以下命令： `composer update magento/express-checkout`。

1. 提交並推送更改。

## 故障排除

您可能在嘗試安裝 [!DNL Express Checkout] 擴展。

請參閱 [故障排除](../express-checkout/troubleshooting.md) 主題，以獲取詳細資訊 [!DNL Express Checkout]。

## 先決條件

查看 [先決條件](../express-checkout/prerequisites.md) 的子菜單。
