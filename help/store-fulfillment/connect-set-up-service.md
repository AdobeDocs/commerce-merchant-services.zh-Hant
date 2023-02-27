---
title: 連接商店完成解決方案
description: 建立和授權Adobe Commerce整合，並將存放履行帳戶憑證新增至Adobe Commerce服務設定，以建立Adobe Commerce與存放區履行解決方案之間的連線。
role: User, Admin
level: Intermediate
exl-id: 74c71c43-305a-4ea7-84f8-95f3ce0a9482
source-git-commit: e7493618e00e28e2de5043ae2d7e05a81110d8f1
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# 連接商店完成解決方案

將必要的驗證憑證和連線資料新增至Adobe Commerce管理員，將Store Fullment Services與Adobe Commerce連線。

- **[設定 [!DNL Commerce integration settings]](#create-an-adobe-commerce-integration)** — 為Store Fullment Services建立Adobe Commerce整合，並生成訪問令牌，以驗證來自Store Fullment Server的傳入請求。

- **[配置Store Fullment Services的帳戶憑據](#configure-store-fulfillment-account-credentials)** — 新增憑證，將Adobe Commerce連線至您的商店履行帳戶。

>[!NOTE]
>
>請先完成連線設定並成功驗證連線，再開始測試。

## 建立Adobe Commerce整合

若要將Adobe Commerce與商店完成服務整合，您需建立商務整合，並產生存取權杖，以用於驗證來自商店完成伺服器的請求。 您也必須更新Adobe Commerce [!UICONTROL Consumer Settings] 防止 `The consumer isn't authorized to access %resources.` 從Adobe Commerce到 [!DNL Store Fulfillment] 服務。

1. 從管理員建立商店履行的整合。

   - 為擴充功能命名
   - 輸入您的電子郵件地址
   - 輸入您的管理員帳戶密碼

1. 設定 [!UICONTROL API Resource Access permissions] 對於整合 — 選取 `[!UICONTROL All]`

1. 儲存並啟動整合，以產生存取權杖以進行驗證。

1. 將存取權杖複製並儲存至安全的加密位置。

1. 請與您的帳戶管理員合作，完成商店履行端的設定，並授權整合。

1. 啟用Adobe Commerce [!UICONTROL Consumer Settings] 選項 [!UICONTROL Allow OAuth Access Tokens to be used as standalone Bearer tokens].

   - 從管理員，前往 **[!UICONTROL Stores]** >  [!UICONTROL Configuration] > **[!UICONTROL Services]** >  **[!UICONTROL OAuth]** > **[!UICONTROL Consumer Settings]**

   - 設定 [!UICONTROL Allow OAuth Access Tokens to be used as standalone Bearer tokens] 選項 **[!UICONTROL Yes]**.

>[!IMPORTANT]
>
> 整合代號是環境專屬的。 如果您從不同環境（例如從中繼環境還原生產資料）中還原具有源資料的環境的資料庫，則排除 `oauth_token` 表，以便在還原操作期間不會覆蓋整合令牌詳細資訊。


## 配置儲存履行帳戶憑據

完成進門表後，將為您建立一個Walmart Store Fullment帳戶。 您會在憑證可用時收到下列憑證：

- [!DNL Merchant ID]
- [!DNL Consumer ID]
- [!DNL Consumer Secret]
- [!DNL API Server URL]
- [!DNL Token Auth Server URL] （通常與上述設定相同）

配置和使用「儲存完成」時需要這些憑據。

>[!NOTE]
>
>帳戶建立程式可能需要一些時間才能完成。 等候憑證時， [查看並配置商店完成解決方案的其他設定](service-config-settings-overview.md).

### 添加憑據以連接到儲存履行

1. 設定 [帳戶憑證](enable-general.md) 適用於生產和沙箱環境。

1. 從管理員，前往 **[!UICONTROL Stores > Configuration > Services > Store Fulfillment by Walmart Commerce Technologies]**

1. 輸入為 **[!UICONTROL Production environment]**. 所有欄位都是必填欄位。

1. 選擇 **[!UICONTROL Save Config]**.

1. 選取 **[!UICONTROL Validate Credentials]**.

>[!NOTE]
>
>如果憑證無效，請確認您為每個環境輸入了正確的值，然後重新驗證。 如果您在連線時仍有問題，請連絡您的客戶代表。
