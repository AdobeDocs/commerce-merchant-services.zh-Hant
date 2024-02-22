---
title: 上線和安裝
description: 「瞭解如何安裝 [!DNL Catalog Service]"
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: 6a7efbe0424e35cdec9cb00275d9a953feccaa5b
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 0%

---

# 上線和安裝

以下影片會帶您逐步瞭解 [!DNL Catalog Service] 程式。

**第1部分**：上線和安裝

>[!VIDEO](https://video.tv.adobe.com/v/3415599)

**第2部分**：使用 [!DNL Catalog Service]

>[!VIDEO](https://video.tv.adobe.com/v/3415600)

>[!BEGINSHADEBOX]

## 必要條件

的入門流程 [!DNL Catalog Service] 需要存取伺服器的命令列。 如果您不熟悉如何使用命令列，請向開發人員或系統整合商尋求協助。

**軟體需求**

- Adobe Commerce 2.4.4+
- PHP 8.1、8.2
- Composer： 2.x

**支援平台**

- 雲端基礎結構上的Adobe Commerce： 2.4.4+
- Adobe Commerce內部部署： 2.4.4+

>[!ENDSHADEBOX]

## 端點

[!DNL Catalog Service] 有兩個端點可用於上線：

- 沙箱(`https://catalog-service-sandbox.adobe.io/graphql`) — 用於在上線前進行測試和驗證
- 生產(`https://catalog-service.adobe.io/graphql`) — 用於Commerce商家和網站的即時流量

Commerce的所有測試例項都應使用沙箱端點。

只應對沙箱端點執行負載測試。 建議使用 [支援票證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) 在負載測試時開啟，以便服務團隊可以預期額外的伺服器流量。

## 安裝和設定

開始使用 [!DNL Catalog Service] 若為Adobe Commerce，需要下列步驟：

- 安裝資料匯出擴充功能
- 設定服務與資料匯出
- 存取服務

### 安裝資料匯出擴充功能

的入門流程 [!DNL Catalog Service] 需要存取伺服器的命令列。

此 [!DNL Catalog Service] 擴充功能可安裝在Adobe Commerce雲端基礎結構和內部部署執行個體上。

此 [!DNL Catalog Service] 隨連結至Commerce帳戶的撰寫器金鑰安裝 [`mageid`](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/) 在註冊過程中提供。 Composer會在Adobe Commerce的初始安裝期間，或先前未將Composer金鑰儲存至外部時，使用這些金鑰 `auth.json` 檔案。

另請參閱 [取得您的驗證金鑰](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html) 以取得有關取得撰寫器索引鍵的詳細資訊。

#### 雲端基礎結構上的Adobe Commerce

使用此方法來安裝 [!DNL Catalog Service] Commerce Cloud例項的擴充功能。

1. 在本機工作站上，變更至專案目錄。
1. 新增目錄服務模組。

   ```bash
   composer require "magento/catalog-service" "^3.0.1"
   ```

1. 更新套件相依性。

   ```bash
   composer update
   ```

1. 提交和推送程式碼變更 `composer.json` 和 `composer.lock` 檔案。

#### 內部部署

使用此方法來安裝 [!DNL Catalog Service] 內部部署執行個體的擴充功能。

1. 使用Composer將目錄服務模組新增至您的專案：

   ```bash
   composer require "magento/catalog-service" "^3.0.1"
   ```

1. 更新相依性並安裝擴充功能：

   ```bash
   composer update
   ```

1. 升級Adobe Commerce：

   ```bash
   bin/magento setup:upgrade
   ```

1. 清除快取：

   ```bash
   bin/magento cache:clean
   ```

### 設定服務與資料匯出

安裝之後 [!DNL Catalog Service]，您必須設定 [Commerce服務聯結器](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#apikey) 指定API金鑰並選取SaaS資料空間。

SaaS設定完成後，請遵循下列步驟執行初始資料同步 [目錄同步](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) 指南。

若要確保目錄匯出可正確執行：

- 確認cron工作正在執行。
- 驗證索引器是否正在執行。
- 確保 `Catalog Attributes Feed, Product Feed, Product Overrides Feed`、和 `Product Variant Feed` 索引器設為「依排程更新」。

視目錄大小而定，初始同步可能需要幾分鐘到幾小時的時間。 初始同步之後，目錄會持續將產品資料從Commerce伺服器匯出至Commerce服務，以保持服務為最新。 若要監視同步狀態，請參閱 [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html).

### 存取服務

此 [!DNL Catalog Service] 可透過HTTPS使用POST命令存取API。

若要取得API金鑰，請前往「管理員」的「商務服務聯結器」區域，並複製公開API金鑰。

閱讀 [GraphQL檔案](https://developer.adobe.com/commerce/services/graphql/) 以瞭解如何查詢及傳送產生API請求所需的標頭。

允許 [!DNL Catalog Service] 透過防火牆，新增 `commerce.adobe.io` 加入允許清單。

## 目錄服務和API網格

此 [Adobe Developer App Builder的API網格](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) 可讓開發人員使用AdobeIO將私人或第三方API和其他介面與Adobe產品整合。

請參閱  [[!DNL Catalog Service] 和API Mesh](mesh.md) 有關安裝和設定詳細資訊的主題。

## 資料管理控制面板

使用者可以參閱 [資料管理控制面板](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) 如需更多相關資料，請參閱 [!DNL Catalog Service] 資料同步。
