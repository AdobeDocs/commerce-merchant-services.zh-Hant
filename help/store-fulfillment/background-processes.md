---
title: 後台進程配置
description: '"配置 [!DNL Store Fulfillment] 用於將資料與履行服務同步的後台過程。」'
role: User, Admin
level: Intermediate
exl-id: 742ae59e-77a0-4db6-b156-2992d4403be7
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---


# 後台進程配置

「儲存完成」整合使用後台進程和消息隊列來獲得最佳效能和規模。 使用為Adobe Commerce商店建置環境 [部署變數](https://devdocs.magento.com/cloud/env/variables-deploy.html#cron_consumers_runner) 自動啟動 [消息隊列管理者](https://devdocs.magento.com/guides/v2.4/config-guide/mq/rabbitmq-overview.html).

使用標準Adobe Commerce來管理背景程式 [排程任務](https://docs.magento.com/user-guide/system/cron.html) 功能。 這些進程負責將訂單和商家儲存配置資料與儲存履行Web服務同步。

## 管理儲存完成的計畫任務

從管理員，前往 **[!UICONTROL Stores > Configuration > Advanced > System > Cron (Scheduled Tasks) > Cron configuration options for group:store_fulfillment]**.

查看儲存履行服務的預設配置。 根據您的訂單處理量和資源可用性，您可能需要調整這些設定。
