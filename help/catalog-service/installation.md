---
title: 入門和安裝
description: 了解如何安裝 [!DNL Catalog Service]
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: 3d7a38fc81265897615896812d49a164a21d1d84
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 入門和安裝

請參閱目錄服務程式的逐步說明。

第1部分：

>[!VIDEO](https://video.tv.adobe.com/v/3415599)

第2部分：

>[!VIDEO](https://video.tv.adobe.com/v/3415600)

## 必要條件

的上線程式 [!DNL Catalog Service] 需要訪問伺服器的命令行。 如果您不熟悉從命令列進行工作，請要求開發人員或系統整合商提供協助。

### 軟體需求

- Adobe Commerce 2.4.4+
- PHP 8.1、8.2
- 撰寫器：2.x

### 支援平台

- Adobe Commerce雲基礎架構：2.4.4+
- Adobe Commerce駐地：2.4.4+

## 環境

目錄服務有兩種環境可供上線：

- 沙箱(https://catalog-service-sandbox.adobe.io/graphql) — 用於上線前的測試和驗證
- 生產(https://catalog-service.adobe.io/graphql)-)用於商務商家和網站的即時流量

## 安裝與設定

若要開始使用Adobe Commerce的目錄服務，需執行下列步驟：

- 安裝資料匯出擴充功能
- 設定服務和資料匯出
- 存取服務

### 安裝資料匯出擴充功能

目錄服務的上線過程需要訪問伺服器的命令行。

目錄服務擴充功能可安裝在Adobe Commerce雲端基礎架構和內部部署執行個體上。

目錄服務會安裝有連結至商務帳戶的撰寫器金鑰 [馬吉德](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-personal/#field-descriptions) 在註冊過程中提供。 撰寫器在初始安裝Adobe Commerce期間或在先前未將撰寫器金鑰儲存至外部的情況下使用這些金鑰 `auth.json` 檔案。

請參閱 [取得驗證金鑰](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html) 以取得關於取得撰寫器金鑰的詳細資訊。

#### Adobe Commerce雲基礎架構

使用此方法來安裝Commerce Cloud例項的目錄服務擴充功能。

1. 開啟 `<Commerce_root>/composer.json` 檔案，並依照下列方式更新所需區段：

```json
"require": {
  "magento/catalog-service": "^2.1.0"
}
```

1. 在本機測試新設定並更新相依性：

```bash
composer update
```

命令會更新所有相依性。

1. 提交並推送您的更改 `composer.json` 和 `composer.lock`.

#### 內部部署

使用此方法為本地實例安裝目錄服務擴展。

1. 開啟 `<Commerce_root>/composer.json` 檔案，並依照下列方式更新所需區段：

```json
"require": {
    "magento/catalog-service": "^2.1.0"
}
```

1. 更新相依性並安裝擴充功能：

```bash
composer update
```

命令會更新所有相依性。

1. 升級Adobe Commerce:

```bash
bin/magento setup:upgrade
```

1. 清除快取：

```bash
bin/magento cache:clean
```

### 設定服務和資料匯出

安裝目錄服務後，您必須設定 [商務服務連接器](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#apikey) 指定API密鑰並選擇SaaS資料空間。

完成SaaS配置後，請按照 [目錄同步](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) 指南。

若要確保目錄匯出正確執行：

- 確認cron作業正在執行。
- 驗證索引器是否正在運行。
- 確保 `Catalog Attributes Feed, Product Feed, Product Overrides Feed`，和 `Product Variant Feed` 索引器設定為「按計畫更新」。

根據目錄大小，初始同步可能需要幾分鐘到數小時。 初次同步後，目錄會持續將產品資料從商務伺服器匯出至商務服務，讓服務保持最新。

### 存取服務

可透過HTTPS使用POST命令存取目錄服務API。

若要取得api金鑰，請前往管理員中的商務服務連接器區域，並複製公用API金鑰。

閱讀 [GraphQL檔案](https://developer.adobe.com/commerce/webapi/graphql/) 了解如何查詢及傳送產生API請求所需的標題。

## 目錄服務和API網格

此 [Adobe Developer App Builder的API Mesh](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) 使開發人員能夠使用AdobeIO將專用或第三方API和其他介面與Adobe產品整合。

請參閱  [目錄服務和API網格](mesh.md) 安裝和配置詳細資訊主題。
