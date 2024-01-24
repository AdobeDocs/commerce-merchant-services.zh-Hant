---
title: 安裝 [!DNL Data Connection]
description: 瞭解如何安裝、更新及解除安裝 [!DNL Data Connection] 來自Adobe Commerce的擴充功能。
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
role: Admin, Developer
feature: Install
source-git-commit: 688eabddaf4b3faab98c60cf440fe6e9c6772790
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# 安裝 [!DNL Data Connection]

安裝擴充功能之前， [檢閱先決條件](overview.md#prereqs).

## 安裝擴充功能

此 [!DNL Data Connection] 擴充功能可從以下網址取得： [Adobe市集](https://commercemarketplace.adobe.com/magento-experience-platform-connector.html). 當您從伺服器的命令列安裝此擴充功能時，會連結至您的Adobe Commerce安裝，做為 [服務](../landing/saas.md). 當程式完成時， **[!DNL Data Connection]** 和 **Commerce服務聯結器** 出現在 **系統** 下的選單 **服務** 在商務中 _管理員_.

>[!IMPORTANT]
>
>當擴充功能的名稱從Experience Platform聯結器變更為 [!DNL Data Connection]，封裝名稱會保留 `experience-platform-connector` 以支援回溯相容性。

1. 若要下載 `experience-platform-connector` 封裝，從命令列執行下列動作：

   ```bash
   composer require magento/experience-platform-connector
   ```

   此中繼資料包含以下模組和擴充功能：

   * `module-experience-connector-admin`  — 更新Admin UI，讓您能夠選取特定Adobe Commerce執行個體的資料流ID。
   * `module-experience-connector`  — 設定 `Organization ID` 和 `datastreamId` （在Storefront Events SDK中）。
   * `data-services`  — 提供店面事件的屬性內容。 例如，發生結帳事件時，包含有關購物車中有多少商品的資訊以及這些商品的產品屬性資料。
   * `services-id`  — 將您的Adobe Commerce執行個體連線至 [Adobe Commerce SaaS](../landing/saas.md) 使用沙箱和生產API金鑰並前往Adobe Experience Platform以擷取IMS組織ID。
   * `orders-connector`  — 將訂單狀態服務連線到您的Adobe Commerce執行個體。

1. （選用）若要包含 [!DNL Live Search] 資料，包含 [搜尋事件](events.md#search-events)，安裝 [[!DNL Live Search]](../live-search/install.md) 副檔名。

1. （選用）加入B2B資料，包括 [請購單事件](events.md#b2b-events)，安裝 [B2B擴充功能](#install-the-b2b-extension).

### 安裝Adobe I/O事件

安裝之後 `experience-platform-connector` 擴充功能上，您必須安裝Adobe Commerce的Adobe I/O事件。

下列步驟適用於雲端基礎結構上的Adobe Commerce和內部部署安裝。

1. 如果您執行Commerce 2.4.4或2.4.5，請使用以下命令載入事件模組：

   ```bash
   composer require magento/commerce-eventing=^1.0 --no-update
   ```

   Commerce 2.4.6及更新版本會自動載入這些模組。

1. 更新專案相依性。

   ```bash
   composer update
   ```

1. 啟用新模組：

   ```bash
   bin/magento module:enable Magento_AdobeCommerceEventsClient Magento_AdobeCommerceEventsGenerator Magento_AdobeIoEventsClient Magento_AdobeCommerceOutOfProcessExtensibility
   ```

根據部署型別完成安裝：內部部署或雲端基礎結構上的Adobe Commerce 。

#### 內部部署

在內部部署環境中，您必須手動啟用程式碼產生和Adobe Commerce事件：

```bash
bin/magento events:generate:module
bin/magento module:enable Magento_AdobeCommerceEvents
bin/magento setup:upgrade
bin/magento setup:di:compile
bin/magento config:set adobe_io_events/eventing/enabled 1
```

#### 在雲端基礎結構上

在雲端基礎結構上的Adobe Commerce中，啟用 `ENABLE_EVENTING` 中的全域變數 `.magento.env.yaml`. [瞭解更多](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-global.html#enable_eventing).

```bash
stage:
   global:
      ENABLE_EVENTING: true
```

提交更新檔案並將其推播到雲端環境。 部署完成後，使用以下命令啟用傳送事件：

```bash
bin/magento config:set adobe_io_events/eventing/enabled 1
```

### 安裝B2B擴充功能

針對B2B商家，安裝下列擴充功能以包含 [請購單清單](events.md#b2b-events) 事件資料。

下載 `magento/experience-platform-connector-b2b` 擴充功能，從命令列執行下列動作：

```bash
composer require magento/experience-platform-connector-b2b
```

## 更新 [!DNL Data Connection] 副檔名 {#update}

若要更新 [!DNL Data Connection] 擴充功能中，從命令列執行以下命令：

```bash
composer update magento/experience-platform-connector --with-dependencies
```

或者，對於B2B商家：

```bash
composer update magento/experience-platform-connector-b2b --with-dependencies
```

若要更新至主要版本，例如從2.0.0到3.0.0，請編輯專案的根目錄 [!DNL Composer] `.json` 檔案如下所示：

1. 開啟根 `composer.json` 檔案和搜尋 `magento/experience-platform-connector`.

1. 在 `require` 區段，更新版本號碼，如下所示：

   ```json
   "require": {
      ...
      "magento/experience-platform-connector": "^3.0",
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

## 解除安裝 [!DNL Data Connection] 副檔名 {#uninstall}

若要解除安裝 [!DNL Data Connection] 副檔名，請參閱 [解除安裝模組](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
