---
title: 連線商店履行解決方案
description: 建立Adobe Commerce與Store Fulfillment解決方案之間的連線。 建立並授權Adobe Commerce整合，並將「商店履行」帳戶認證新增至Adobe Commerce服務設定。
role: Admin, Developer
level: Intermediate
feature: Shipping/Delivery, Install, Configuration, User Account, Tools and External Services
exl-id: 74c71c43-305a-4ea7-84f8-95f3ce0a9482
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# 連線商店履行解決方案

將必要的驗證憑證和連線資料新增至Adobe Commerce管理員，以連線商店履行服務與Adobe Commerce。

- **[設定 [!DNL Commerce integration settings]](#create-an-adobe-commerce-integration)** — 建立Store Fulfillment服務的Adobe Commerce整合，並產生存取權杖以驗證來自Store Fulfillment伺服器的傳入請求。

- **[設定Store Fulfillment服務的帳戶認證](#configure-store-fulfillment-account-credentials)** — 新增您的認證，以將Adobe Commerce連線至您的Store Fulfillment帳戶。

>[!NOTE]
>
>請先完成連線設定並成功驗證連線，再開始測試。

## 建立Adobe Commerce整合

若要將Adobe Commerce與Store Fulfillment服務整合，您可以建立Commerce整合併產生存取權杖，其可用於驗證來自Store Fulfillment伺服器的請求。 您也必須更新Adobe Commerce [!UICONTROL Consumer Settings] 要防止的選項 `The consumer isn't authorized to access %resources.` 回應來自Adobe Commerce的請求至的錯誤 [!DNL Store Fulfillment] 服務。

1. 從「管理員」建立「商店履行」的整合。

   - 為擴充功能命名
   - 輸入您的電子郵件地址
   - 輸入您的管理員帳戶密碼

1. 設定API資源存取許可權以便與以下專案整合：

   - 銷售> BOPIS訂單更新
   - 系統>商店履行應用程式許可權

1. 儲存並啟用整合，以產生用於驗證的存取權杖。

1. 將存取權杖複製並儲存至安全的加密位置。

1. 請與您的客戶經理合作，完成「商店履行」端的設定並授權整合。

1. 啟用Adobe Commerce [!UICONTROL Consumer Settings] 選項至 [!UICONTROL Allow OAuth Access Tokens to be used as standalone Bearer tokens].

   - 從管理員，前往 **[!UICONTROL Stores]** >  [!UICONTROL Configuration] > **[!UICONTROL Services]** >  **[!UICONTROL OAuth]** > **[!UICONTROL Consumer Settings]**

   - 設定 [!UICONTROL Allow OAuth Access Tokens to be used as standalone Bearer tokens] 選項至 **[!UICONTROL Yes]**.

>[!IMPORTANT]
>
> 整合代號是特定於環境的。 如果您使用來自不同環境的來源資料來還原環境的資料庫（例如從中繼環境還原生產資料），請排除 `oauth_token` 資料表匯出，以便在還原作業期間不會覆寫整合權杖詳細資訊。


## 設定存放區履行帳戶認證

在您完成錄取表單後，系統就會為您建立「沃爾瑪商店履行」帳戶。 下列認證可用時，您會收到這些認證：

- [!DNL Merchant ID]
- [!DNL Consumer ID]
- [!DNL Consumer Secret]
- [!DNL API Server URL]
- [!DNL Token Auth Server URL] （通常與上述設定相同）

設定和使用Store Fulfillment需要這些認證。

>[!NOTE]
>
>帳戶建立程式可能需要一些時間才能完成。 當您等待認證時， [檢閱並設定「商店履行」解決方案的其他設定](service-config-settings-overview.md).

### 新增認證以連線至「商店履行」

1. 設定 [帳戶認證](enable-general.md) 用於生產和沙箱環境。

1. 從管理員，前往 **[!UICONTROL Stores > Configuration > Services > Store Fulfillment by Walmart Commerce Technologies]**

1. 輸入為提供的帳戶認證 **[!UICONTROL Production environment]**. 所有欄位都是必填欄位。

1. 選取 **[!UICONTROL Save Config]**.

1. 選取以測試連線 **[!UICONTROL Validate Credentials]**.

>[!NOTE]
>
>如果認證無效，請確認您為每個環境輸入正確的值，然後重新驗證。 如果您在連線時仍有問題，請聯絡客戶代表。
