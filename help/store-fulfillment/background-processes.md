---
title: 後台進程配置
description: '"配置 [!DNL Store Fulfillment] 後台流程，用於將資料與履行服務同步。」                   '
role: User, Admin
level: Intermediate
exl-id: 742ae59e-77a0-4db6-b156-2992d4403be7
source-git-commit: 42b0118b427b1e04186793b4a57c058bc1cabdd4
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---


# 後台進程配置

儲存完成整合使用後台流程和消息隊列來實現最佳效能和擴展。 為您的Adobe Commerce商店構建環境 [部署變數](https://devdocs.magento.com/cloud/env/variables-deploy.html#cron_consumers_runner) 自動啟動 [消息隊列管理者](https://devdocs.magento.com/guides/v2.4/config-guide/mq/rabbitmq-overview.html)。

後台進程使用標準Adobe Commerce [計畫任務](https://docs.magento.com/user-guide/system/cron.html) 功能。 這些進程負責將訂單和商家商店配置資料與商店履行Web服務同步。

## 管理儲存完成的計畫任務

從管理員，轉到 **[!UICONTROL Stores > Configuration > Advanced > System > Cron (Scheduled Tasks) > Cron configuration options for group:store_fulfillment]**。

查看Store Fulfillment服務的預設配置。 根據您的訂單處理量和資源可用性，您可能需要調整這些設定。
