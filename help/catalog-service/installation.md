---
title: 上線和安裝
description: 「瞭解如何安裝 [!DNL Catalog Service]"
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: c33ec5a10f9f2570e971e968efd1524e0d384ecd
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---

# 上線和安裝

安裝目錄服務，使用向Commerce執行個體要求及接收產品資料 [目錄服務GraphQL API](https://developer.adobe.com/commerce/services/graphql/catalog-service/).

>[!NOTE]
>
>如果您的Commerce執行個體使用即時搜尋或產品Recommendations，當您啟動或升級這些服務時，目錄服務會自動安裝或更新。 如需詳細資訊，請參閱 [即時搜尋](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/install) 和 [產品Recommendations](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/getting-started/install-configure).

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

所有Commerce測試執行個體都使用沙箱端點。

在沙箱端點上執行所有載入測試。 開始載入測試前，請先提交 [支援票證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) 以便服務團隊能夠預測額外的伺服器流量。

## 安裝和設定

開始使用 [!DNL Catalog Service] 若為Adobe Commerce，需要下列步驟：

- 安裝資料匯出擴充功能
- 設定服務與資料匯出
- 存取服務

### 安裝資料匯出擴充功能

您必須能存取伺服器的命令列，才能完成 [!DNL Catalog Service] 上線流程。

此 [!DNL Catalog Service] 隨連結至Commerce帳戶的撰寫器金鑰安裝 [`mageid`](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/) 在註冊過程中提供。 Composer會在Adobe Commerce的初始安裝期間，或先前未將Composer金鑰儲存至外部時，使用這些金鑰 `auth.json` 檔案。

另請參閱 [取得您的驗證金鑰](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html) 以取得有關取得撰寫器索引鍵的詳細資訊。

此 [!DNL Catalog Service] 擴充功能可安裝在Adobe Commerce雲端基礎結構和內部部署執行個體上。

>[!BEGINTABS]

>[!TAB 雲端基礎結構]

使用此方法來安裝 [!DNL Catalog Service] Commerce Cloud例項的擴充功能。

1. 在本機工作站上，變更至雲端基礎結構專案上Adobe Commerce的專案目錄。

   >[!NOTE]
   >
   >如需有關在本機管理Commerce專案環境的資訊，請參閱 [使用CLI管理分支](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches) 在 _雲端基礎結構上的Adobe Commerce使用手冊_.

1. 檢視環境分支，以使用Adobe Commerce Cloud CLI進行更新。

   ```shell
   magento-cloud environment:checkout <environment-id>
   ```

1. 新增目錄服務模組。

   ```bash
   composer require "magento/catalog-service" "^3.0.1" --no-update
   ```

1. 更新套件相依性。

   ```bash
   composer update "magento/catalog-service"
   ```

1. 提交和推送程式碼變更 `composer.json` 和 `composer.lock` 檔案。

1. 新增、提交和推送程式碼變更 `composer.json` 和 `composer.lock` 檔案至雲端環境。

   ```shell
   git add -A
   git commit -m "Add catalog service module"
   git push origin <branch-name>
   ```

   推送更新會啟動 [Commerce雲端部署程式](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process) 以套用變更。 從檢視部署狀態 [部署記錄](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log).

>[!TAB 內部部署]

使用此方法來安裝 [!DNL Catalog Service] 內部部署執行個體的擴充功能。

1. 使用Composer將目錄服務模組新增至您的專案：

   ```bash
   composer require "magento/catalog-service" "^3.0.1"  --no-update
   ```

1. 更新相依性並安裝擴充功能：

   ```bash
   composer update  "magento/catalog-service"
   ```

1. 升級Adobe Commerce：

   ```bash
   bin/magento setup:upgrade
   ```

1. 清除快取：

   ```bash
   bin/magento cache:clean
   ```

   >[!TIP]
   >
   >在某些情況下，特別是部署到生產時，您可能希望避免清除編譯的程式碼，因為可能需要一些時間。 在進行任何變更之前，請務必先備份系統。

>[!ENDTABS]

### 設定服務與資料匯出

安裝之後 [!DNL Catalog Service]，請完成下列工作來整合目錄服務與您的Adobe Commerce執行個體。 此整合可讓您在Commerce執行個體、目錄服務和其他支援服務之間同步資料和通訊。

1. 設定 [Commerce服務聯結器](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/integration-services/saas) 指定API金鑰並選取SaaS資料空間。

   Commerce服務聯結器設定是使用Adobe Commerce服務(例如目錄服務、即時搜尋和產品Recommendations)所需的一次性程式。 如果您已經為另一個服務設定了聯結器，請略過此步驟。

1. 從執行初始資料同步 [資料管理控制面板](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard).

   視目錄大小而定，初始同步可能需要幾分鐘到幾小時的時間。 您可以從「資料管理」控制面板監視同步化狀態。 初始同步後，「目錄」會持續匯出產品資料，以保持服務在最新狀態。

若要確保目錄匯出可正確執行：

- [確認cron工作正在執行](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues).
- 確認索引子是從以下位置執行： [管理員](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) 或使用Commerce CLI命令 `bin/magento indexer:info`.
- 確認 `Catalog Attributes Feed, Product Feed, Product Overrides Feed`、和 `Product Variant Feed` 索引子設定為 `Update by Schedule`.

### 存取服務

此 [!DNL Catalog Service] GraphQL API可從存取： ` https://catalog-service.adobe.io/graphql` 端點透過HTTPS使用POST命令。

在您的GraphQL查詢中，您必須指定多個HTTP標頭，包括您在「管理員」中新增到Adobe Commerce Services Connector設定的公開API金鑰。 如需詳細資訊，請參閱 [店面服務GraphQL](https://developer.adobe.com/commerce/services/graphql/) 檔案。

### 防火牆設定

允許 [!DNL Catalog Service] 透過防火牆，新增 `commerce.adobe.io` 加入允許清單。

## 目錄服務和API網格

此 [Adobe Developer App Builder的API網格](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) 可讓開發人員使用AdobeIO將私人或第三方API和其他介面與Adobe產品整合。

請參閱 [[!DNL Catalog Service] 和API Mesh](mesh.md) 有關安裝和設定詳細資訊的主題。

## 資料管理控制面板

有關詳細資訊 [!DNL Catalog Service] 資料同步，請參閱 [資料管理控制面板](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard).
