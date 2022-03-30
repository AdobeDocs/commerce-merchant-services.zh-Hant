---
title: Commerce Services連接器
description: 瞭解如何使用API密鑰和私鑰將您的Adobe Commerce或Magento Open Source實例整合到服務。
source-git-commit: 8789bd21362109325d0d7b23d9b130067390eeae
workflow-type: tm+mt
source-wordcount: '830'
ht-degree: 0%

---

# [!DNL Commerce Services Connector]

某些Adobe Commerce和Magento Open Source功能由 [!DNL Commerce Services]  部署為SaaS（軟體即服務）。 要使用這些服務，必須連接 [!DNL Commerce] 實例使用API密鑰和私鑰，並在 [配置](https://docs.magento.com/user-guide/configuration/services/saas.html)。 你只需設定一次。

## 可用服務

下面列出 [!DNL Commerce] 可通過 [!DNL Commerce Services Connector]:

| 服務 | 可用性 |
| ---|--- |
| [!DNL Product Recommendations] 由Adobe Sensei提供 | Adobe Commerce |
| [!DNL Live Search] 由Adobe Sensei提供 | Adobe Commerce |
| [!DNL Payment Services] | Adobe Commerce和Magento Open Source |

## 建築

在高層， [!DNL Commerce Services Connector] 由以下核心元素組成：

![Commerce Services連接器體系結構](assets/saas-config-sync-workflow.png)

以下各節將更詳細地討論這些元素中的每一個。

## 憑據 {#apikey}

API密鑰和私鑰是從 [!DNL Commerce] 許可證持有人的帳戶，該帳戶由 [!DNL Commerce] ID(MageID)。 通過服務(如 [!DNL Product Recommendations] 或 [!DNL Live Search]而只要該帳戶完好，該商戶組織的許可證持有者就可以生成API密鑰集。 密鑰可以與代表許可證持有者管理項目和環境的系統整合商或開發團隊「需要知道」地共用。 此外，解決方案整合商也有權使用 [!DNL Commerce Services]。 如果您是解決方案整合商，則 [!DNL Commerce] 合作夥伴合同應生成API密鑰。

### 生成API密鑰和私鑰 {#genapikey}

1. 登錄到 [!DNL Commerce] 帳戶 [https://account.magento.com](https://account.magento.com/){:target=&quot;_blank&quot;}。

1. 在 **Magento** 頁籤 **API門戶** 欄。

1. 從 _環境_ 菜單，選擇 **生產** 或 **沙盒**。

   >[!NOTE]
   >
   > 對於 [!DNL _產品Recommendations_] 和 [!DNL _即時搜索_]&#x200B;選中 **生產**。 生產密鑰使您可以訪問生產和非生產資料空間。 沙盒密鑰不用於這些服務。

1. 在 _API密鑰_ 的 **添加新**。

   這將開啟一個對話框，用於下載新密鑰。

   ![下載私鑰](assets/download-api-private-key.png)

   >[!WARNING]
   >
   > 這是您必須複製或下載密鑰的唯一機會。

1. 按一下 **下載** 按一下 **取消**。

   的 **API密鑰** 部分現在顯示API密鑰。 在您 [選擇或建立SaaS項目](#createsaasenv)。

## SaaS配置 {#saasenv}

[!DNL Commerce] 實例必須配置SaaS項目和SaaS資料空間，以便 [!DNL Commerce Services] 可以將資料發送到正確的位置。 SaaS項目將所有SaaS資料空間組合。 SaaS資料空間用於收集和儲存資料，從而 [!DNL Commerce Services] 工作。 某些資料可能從 [!DNL Commerce] 有的可以從店面的購物行為中收集。 然後，該資料將被保留以保護雲儲存。

對於 [!DNL Product Recommendations],SaaS資料空間包含目錄和行為資料。 你可以指出 [!DNL Commerce] 實例到SaaS資料空間 [選擇](https://docs.magento.com/user-guide/configuration/services/saas.html) 的 [!DNL Commerce] 配置。

>[!WARNING]
>
> 僅在生產上使用生產SaaS資料空間 [!DNL Commerce] 安裝以避免資料衝突。 否則，您可能會用測試資料污染生產站點資料，這會導致部署延遲。 例如，生產產品資料可能會錯誤地從暫存資料（如暫存URL）中覆蓋。

### 選擇或建立SaaS項目 {#createsaasenv}

>[!NOTE]
>
> 如果你看不到 **Commerce Services連接器** 的 [!DNL Commerce] 配置，必須安裝 [!DNL Commerce] 模組 [!DNL Commerce Service]，例如 [!DNL Product Recommendations]。

要選擇或建立SaaS項目，請請求 [!DNL Commerce] 來自 [!DNL Commerce] 你商店的許可證持有者。

1. 在 _管理_ 邊欄，轉到 **商店** > _設定_ > **配置**。

1. 在左面板中，展開 **服務** 選擇 **Commerce Services連接器**。

1. 在 _API密鑰_ ，貼上鍵值 **生產API密鑰** 和 **生產私鑰**。

   私鑰必須包括 `----BEGIN PRIVATE KEY---` 在鍵和 `----END PRIVATE KEY----` 在私鑰末尾。

1. 按一下 **保存配置**。

與您的API密鑰關聯的任何SaaS項目都將顯示在 **SaaS項目** 的子菜單。

1. 如果沒有SaaS項目，請按一下 **建立項目**。 在 **項目名稱** 欄位，輸入SaaS項目的名稱。

   建立SaaS項目時， [!DNL Commerce] 根據您的 [!DNL Commerce] 許可證：
   - Adobe Commerce — 一個生產資料空間；兩個測試資料空間
   - Magento Open Source — 一個生產資料空間；無測試資料空間

1. 選擇 **SaaS資料空間** 用於當前配置 [!DNL Commerce] 商店。

>[!WARNING]
>
> 如果在「我的帳戶」的「API門戶」部分生成新密鑰，請立即更新管理配置中的API密鑰。 如果生成新密鑰，並且不在管理員中更新它們，則您的SaaS擴展將不再工作，您將丟失寶貴的資料。

要更改SaaS項目或資料空間名稱，請按一下 **更名此項目** 或 **更名資料空間** 分別進行。

## 目錄同步

當 [!DNL Commerce] 實例成功連接到 [!DNL Commerce Services]，目錄同步進程將產品資料從 [!DNL Commerce] 伺服器 [!DNL Commerce Services]。 [瞭解更多資訊](catalog-sync.md) 關於目錄同步進程。
