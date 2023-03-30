---
title: 從Adobe Commerce安裝及設定Adobe Experience Platform Connector
description: 了解如何從Adobe Commerce安裝、設定、更新和解除安裝Adobe Experience Platform Connector。
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
source-git-commit: 76bc0650f32e99f568c061e67290de6c380f46a4
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# 安裝及配置Experience Platform連接器

安裝擴充功能前， [檢閱必要條件](overview.md#prereqs).

## 安裝擴充功能

Experience Platform連接器擴充功能會從伺服器的命令列安裝，並以 [服務](../landing/saas.md). 程式完成後， **Experience Platform連接器** 顯示於 **系統** 菜單 **服務** 在商務中 _管理_.

Experience Platform連接器是以 [Adobe市集](https://marketplace.magento.com/magento-experience-platform-connector.html).

![適用於Adobe Commerce的B2B](../assets/b2b.svg) 若為B2B商戶，您必須安裝個別的擴充功能。 此擴充功能新增對B2B特定事件的支援。 [深入了解](#install-the-b2b-extension).

1. 若要下載 `experience-platform-connector` 軟體包，從命令行運行以下內容：

   ```bash
   composer require magento/experience-platform-connector
   ```

   此元包含下列模組和擴充功能：

   * `module-experience-connector-admin`  — 更新管理員UI，以便您選取特定Adobe Commerce例項的資料流ID
   * `module-experience-connector`  — 設定 `Organization ID` 和 `datastreamId` 在Storefront Events SDK中
   * `data-services`  — 為店面事件提供屬性上下文。 例如，發生結帳事件時，會納入關於購物車中有多少項目和這些項目的產品屬性資料的資訊。
   * `services-id`  — 將您的Adobe Commerce執行個體連線至 [Adobe Commerce SaaS](../landing/saas.md) 使用沙箱和生產API金鑰並傳至Adobe Experience Platform以擷取IMS組織ID

1. （選用）納入 [!DNL Live Search] 資料，包括搜尋事件，安裝 [[!DNL Live Search]](../live-search/install.md) 擴充功能。

### 安裝B2B擴充功能

若為B2B商戶，請安裝下列擴充功能以包含 [申請表](events.md#b2b-events) 事件資料。

下載 `magento/experience-platform-connector-b2b` 擴充功能，從命令列執行下列項目：

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

若要更新為主要版本，例如從1.0.0更新為2.0.0，請編輯專案的根 [!DNL Composer] `.json` 檔案如下：

1. 開啟根 `composer.json` 檔案和搜索 `magento/platform-connector`.

1. 在 `require` 部分，請按如下方式更新版本號：

   ```json
   "require": {
      ...
      "magento/experience-platform-connector": "^2.0",
      ...
    }
   ```

1. **儲存** `composer.json`. 然後，從命令列執行下列動作：

   ```bash
   composer update magento/experience-platform-connector –-with-dependencies
   ```

或者，對於B2B商戶：

```bash
composer update magento/experience-platform-connector-b2b --with-dependencies
```

## 卸載Experience Platform連接器 {#uninstall}

要卸載Experience Platform連接器，請參閱 [解除安裝模組](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
