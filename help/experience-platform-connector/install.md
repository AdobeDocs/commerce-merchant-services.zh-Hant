---
title: 從Adobe Commerce安裝和配置Adobe Experience Platform連接器
description: 瞭解如何從Adobe Commerce安裝、配置、更新和卸載Adobe Experience Platform連接器。
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
source-git-commit: 898d49cbeb4711862a47693a0d608b74730dc845
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# 安裝和配置Experience Platform連接器

在安裝擴展之前， [查看先決條件](overview.md#prereqs)。

## 安裝擴展

Experience Platform連接器擴展可從 [Adobe市場](https://marketplace.magento.com/magento-experience-platform-connector.html)。 從伺服器的命令行安裝此擴展時，它將作為 [服務](../landing/saas.md)。 完成後， **Experience Platform連接器** 和 **Commerce Services連接器** 在 **系統** 菜單 **服務** 中 _管理_。

>[!NOTE]
>
>![Adobe CommerceB2B](../assets/b2b.svg) 對於B2B商家，必須安裝單獨的擴展。 此擴展增加了對B2B特定事件的支援。 [瞭解更多資訊](#install-the-b2b-extension)。


1. 下載 `experience-platform-connector` 軟體包，從命令行運行以下命令：

   ```bash
   composer require magento/experience-platform-connector
   ```

   此元包包含以下模組和擴展：

   * `module-experience-connector-admin`  — 更新管理員UI，以便您可以為特定的Adobe Commerce實例選擇資料流ID
   * `module-experience-connector`  — 設定 `Organization ID` 和 `datastreamId` 在Storefront事件SDK中
   * `data-services`  — 為店面事件提供屬性上下文。 例如，當發生簽出事件時，將包括有關購物車中有多少物料的資訊以及這些物料的產品屬性資料。
   * `services-id`  — 將您的Adobe Commerce實例連接到 [Adobe CommerceSaaS](../landing/saas.md) 使用沙盒和生產API密鑰，並將密鑰發送到Adobe Experience Platform以檢索IMS組織ID

1. （可選）要包括 [!DNL Live Search] 資料，包括搜索事件，安裝 [[!DNL Live Search]](../live-search/install.md) 擴展。

### 安裝B2B擴展

對於B2B商家，請安裝以下擴展以包括 [申請表](events.md#b2b-events) 事件資料。

下載 `magento/experience-platform-connector-b2b` 擴展，從命令行運行以下命令：

```bash
composer require magento/experience-platform-connector-b2b
```

## 更新Experience Platform連接器 {#update}

要更新Experience Platform連接器，請從命令行運行以下命令：

```bash
composer update magento/experience-platform-connector --with-dependencies
```

或者，對於B2B商戶：

```bash
composer update magento/experience-platform-connector-b2b --with-dependencies
```

要更新到主版本，如從1.0.0到2.0.0，請編輯項目的根 [!DNL Composer] `.json` 檔案，如下所示：

1. 開啟根 `composer.json` 檔案和搜索 `magento/platform-connector`。

1. 在 `require` 部分，按如下方式更新版本號：

   ```json
   "require": {
      ...
      "magento/experience-platform-connector": "^2.0",
      ...
    }
   ```

1. **保存** `composer.json`。 然後，從命令行運行以下命令：

   ```bash
   composer update magento/experience-platform-connector –-with-dependencies
   ```

   或者，對於B2B商戶：

   ```bash
   composer update magento/experience-platform-connector-b2b --with-dependencies
   ```

## 卸載Experience Platform連接器 {#uninstall}

要卸載Experience Platform連接器，請參閱 [卸載模組](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html)。
