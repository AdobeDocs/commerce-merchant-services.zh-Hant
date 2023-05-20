---
title: 登機和安裝
description: 瞭解如何安裝 [!DNL Catalog Service]
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: 3d7a38fc81265897615896812d49a164a21d1d84
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# 登機和安裝

請參閱目錄服務進程的逐步。

第1部分：

>[!VIDEO](https://video.tv.adobe.com/v/3415599)

第二部分：

>[!VIDEO](https://video.tv.adobe.com/v/3415600)

## 先決條件

登機過程 [!DNL Catalog Service] 需要訪問伺服器的命令行。 如果您不熟悉從命令行工作，請咨詢開發人員或系統整合商以獲得幫助。

### 軟體要求

- Adobe Commerce2.4.4+
- 8.1、8.2菲律賓比索
- 作曲家：2.x

### 支援的平台

- Adobe Commerce在雲基礎架構方面：2.4.4+
- Adobe Commerce駐地：2.4.4+

## 環境

目錄服務有兩個可供登錄的環境：

- 沙盒(https://catalog-service-sandbox.adobe.io/graphql) — 用於上線前的測試和驗證
- 製作(https://catalog-service.adobe.io/graphql)-用於商戶和網站的即時流量

## 安裝和配置

要開始使用Adobe Commerce的目錄服務，需要執行以下步驟：

- 安裝資料導出擴展
- 配置服務和資料導出
- 訪問服務

### 安裝資料導出擴展

目錄服務的登錄過程需要訪問伺服器的命令行。

目錄服務擴展可安裝在Adobe Commerce雲基礎架構和本地實例上。

目錄服務隨Composer鍵一起安裝，這些鍵連結到Commerce帳戶 [馬吉德](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-personal/#field-descriptions) 在註冊過程中提供。 Composer在初始安裝Adobe Commerce時或在以前未將Composer鍵保存到外部時使用這些鍵 `auth.json` 的子菜單。

請參閱 [獲取您的身份驗證密鑰](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html) 的子菜單。

#### Adobe Commerce在雲基礎架構上

使用此方法為Commerce Cloud實例安裝目錄服務擴展。

1. 開啟 `<Commerce_root>/composer.json` 在文本編輯器中建立檔案，並按如下方式更新require節：

```json
"require": {
  "magento/catalog-service": "^2.1.0"
}
```

1. Test新配置並更新依賴項：

```bash
composer update
```

該命令更新所有依賴關係。

1. 提交和推送更改 `composer.json` 和 `composer.lock`。

#### 內部

使用此方法為本地實例安裝目錄服務擴展。

1. 開啟 `<Commerce_root>/composer.json` 在文本編輯器中建立檔案，並按如下方式更新require節：

```json
"require": {
    "magento/catalog-service": "^2.1.0"
}
```

1. 更新依賴項並安裝擴展：

```bash
composer update
```

該命令更新所有依賴關係。

1. 升級Adobe Commerce:

```bash
bin/magento setup:upgrade
```

1. 清除快取：

```bash
bin/magento cache:clean
```

### 配置服務和資料導出

安裝目錄服務後，必須配置 [Commerce Services連接器](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#apikey) 指定API鍵並選擇SaaS資料空間。

完成SaaS配置後，按照 [目錄同步](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) 的子菜單。

要確保目錄導出正確運行，請執行以下操作：

- 確認cron作業正在運行。
- 驗證索引器是否正在運行。
- 確保 `Catalog Attributes Feed, Product Feed, Product Overrides Feed`, `Product Variant Feed` 索引器設定為「按計畫更新」。

初始同步可能需要幾分鐘到幾小時，具體取決於目錄大小。 初始同步後，目錄會持續將產品資料從Commerce伺服器導出到Commerce服務，以使服務保持最新。

### 訪問服務

可通過HTTPS使用POST命令訪問目錄服務API。

要獲取api-key，請轉到管理員中的Commerce Service Connector區域並複製公共API密鑰。

閱讀 [GraphQL文檔](https://developer.adobe.com/commerce/webapi/graphql/) 瞭解如何查詢和發送生成API請求所需的標頭。

## 目錄服務和API網格

的 [用於Adobe Developer應用生成器的API網格](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) 使開發人員能夠使用AdobeIO將專用或第三方API和其他介面與Adobe產品整合。

查看  [目錄服務和API網格](mesh.md) 安裝和配置詳細資訊的主題。
