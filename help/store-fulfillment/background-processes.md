---
title: 背景程式設定
description: 「設定排程 [!DNL Store Fulfillment] 與履行服務同步資料所使用的背景程式。」
role: User, Admin
level: Intermediate
exl-id: 742ae59e-77a0-4db6-b156-2992d4403be7
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---


# 背景程式設定

Store Fulfillment整合使用背景程式和訊息佇列，以獲得最佳效能和規模。 使用為您的Adobe Commerce商店建立環境 [部署變數](https://devdocs.magento.com/cloud/env/variables-deploy.html#cron_consumers_runner) 自動啟動 [訊息佇列執行者](https://devdocs.magento.com/guides/v2.4/config-guide/mq/rabbitmq-overview.html).

背景程式是使用標準Adobe Commerce來管理 [已排程任務](https://docs.magento.com/user-guide/system/cron.html) 功能。 這些程式負責將訂單和商家商店設定資料與商店履行Web服務同步。

## 管理「商店履行」的排程任務

從管理員，前往 **[!UICONTROL Stores > Configuration > Advanced > System > Cron (Scheduled Tasks) > Cron configuration options for group:store_fulfillment]**.

複查「商店履行」服務的預設設定。 根據您的訂單處理量及資源可用性，您可能需要調整這些設定。
