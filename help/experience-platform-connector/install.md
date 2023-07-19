---
title: 從Adobe Commerce安裝及設定Adobe Experience Platform聯結器
description: 瞭解如何從Adobe Commerce安裝、設定、更新及解除安裝Adobe Experience Platform Connector。
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
role: Admin, Developer
feature: Install
source-git-commit: 64273ad4c1a54b150746a54896caf73ed612c2d1
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# 安裝及設定Experience Platform聯結器

安裝擴充功能之前， [檢閱先決條件](overview.md#prereqs).

## 安裝擴充功能

Experience Platform聯結器擴充功能可從 [Adobe市集](https://marketplace.magento.com/magento-experience-platform-connector.html). 當您從伺服器的命令列安裝此擴充功能時，會以身分連線至您的Adobe Commerce安裝 [服務](../landing/saas.md). 程式完成時， **Experience Platform聯結器** 和 **商務服務聯結器** 出現在 **系統** 下的選單 **服務** 在商務中 _管理員_.

>[!NOTE]
>
>![Adobe Commerce的B2B](../assets/b2b.svg) 對於B2B商家，您必須安裝個別擴充功能。 此擴充功能新增對B2B特定事件的支援。 [瞭解更多](#install-the-b2b-extension).


1. 若要下載 `experience-platform-connector` 封裝，從命令列執行以下命令：

   ```bash
   composer require magento/experience-platform-connector
   ```

   此中繼包含下列模組和擴充功能：

   * `module-experience-connector-admin`  — 更新管理員UI，讓您能夠選取特定Adobe Commerce執行個體的資料流ID
   * `module-experience-connector`  — 設定 `Organization ID` 和 `datastreamId` 在店面事件SDK中
   * `data-services`  — 提供店面事件的屬性內容。 例如，發生結帳事件時，包含有關購物車中有多少商品的資訊以及這些商品的產品屬性資料。
   * `services-id`  — 將您的Adobe Commerce執行個體連線至 [Adobe Commerce SaaS](../landing/saas.md) 使用沙箱和生產API金鑰並前往Adobe Experience Platform以擷取IMS組織ID

1. （選用）若要包含 [!DNL Live Search] data （包含搜尋事件）安裝 [[!DNL Live Search]](../live-search/install.md) 副檔名。

### 安裝B2B擴充功能

針對B2B商家，安裝下列擴充功能以包含 [請購單清單](events.md#b2b-events) 事件資料。

下載 `magento/experience-platform-connector-b2b` 擴充功能，從命令列執行下列動作：

```bash
composer require magento/experience-platform-connector-b2b
```

## 更新Experience Platform聯結器 {#update}

若要更新Experience Platform聯結器，請從命令列執行下列動作：

```bash
composer update magento/experience-platform-connector --with-dependencies
```

或者，對於B2B商家：

```bash
composer update magento/experience-platform-connector-b2b --with-dependencies
```

若要更新至主要版本（例如從1.0.0到2.0.0），請編輯專案的根目錄 [!DNL Composer] `.json` 檔案如下所示：

1. 開啟根目錄 `composer.json` 檔案和搜尋 `magento/experience-platform-connector`.

1. 在 `require` 區段，更新版本號碼，如下所示：

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

   或者，對於B2B商家：

   ```bash
   composer update magento/experience-platform-connector-b2b --with-dependencies
   ```

## 解除安裝Experience Platform聯結器 {#uninstall}

若要解除安裝Experience Platform聯結器，請參閱 [解除安裝模組](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
