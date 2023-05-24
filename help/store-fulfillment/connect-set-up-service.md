---
title: 連線商店履行解決方案
description: 透過建立和授權Adobe Commerce整合，並將Adobe Commerce履行帳戶認證新增到Adobe Commerce服務設定，建立與Store Fulfillment解決方案之間的連線。
role: User, Admin
level: Intermediate
exl-id: 74c71c43-305a-4ea7-84f8-95f3ce0a9482
source-git-commit: e7493618e00e28e2de5043ae2d7e05a81110d8f1
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# 連線商店履行解決方案

將必要的驗證認證和連線資料新增至Adobe Commerce管理員，以連線商店履行服務與Adobe Commerce。

- **[設定 [!DNL Commerce integration settings]](#create-an-adobe-commerce-integration)** — 建立Store Fulfillment服務的Adobe Commerce整合，並產生存取權杖以驗證來自Store Fulfillment伺服器的傳入請求。

- **[設定Store Fulfillment服務的帳戶認證](#configure-store-fulfillment-account-credentials)** — 新增您的憑證以將Adobe Commerce連線至您的Store Fulfillment帳戶。

>[!NOTE]
>
>請先完成連線設定並成功驗證連線，然後再開始測試。

## 建立Adobe Commerce整合

若要將Adobe Commerce與Store Fulfillment服務整合，您可以建立Commerce整合，並產生可用於驗證Store Fulfillment伺服器請求的存取權杖。 您也必須更新Adobe Commerce [!UICONTROL Consumer Settings] 要防止的選項 `The consumer isn't authorized to access %resources.` Adobe Commerce對的請求的回應錯誤 [!DNL Store Fulfillment] 服務。

1. 從「管理員」建立「商店履行」的整合。

   - 為擴充功能命名
   - 輸入您的電子郵件地址
   - 輸入您的管理員帳戶密碼

1. 設定 [!UICONTROL API Resource Access permissions] 針對整合 — 選取 `[!UICONTROL All]`

1. 儲存並啟用整合，產生用於驗證的存取權杖。

1. 將存取權杖複製並儲存至安全的加密位置。

1. 請與您的客戶經理合作，完成「商店履行」端的設定，並授權整合。

1. 啟用Adobe Commerce [!UICONTROL Consumer Settings] 選項至 [!UICONTROL Allow OAuth Access Tokens to be used as standalone Bearer tokens].

   - 從管理員，前往 **[!UICONTROL Stores]** >  [!UICONTROL Configuration] > **[!UICONTROL Services]** >  **[!UICONTROL OAuth]** > **[!UICONTROL Consumer Settings]**

   - 設定 [!UICONTROL Allow OAuth Access Tokens to be used as standalone Bearer tokens] 選項至 **[!UICONTROL Yes]**.

>[!IMPORTANT]
>
> 整合代號是特定於環境的。 如果您使用來自不同環境的來源資料還原環境的資料庫（例如從中繼環境還原生產資料），請排除 `oauth_token` 資料庫匯出的表格，以便在還原作業期間不會覆寫整合權杖詳細資訊。


## 設定Store Fulfillment帳戶認證

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
>如果認證無效，請確認您為每個環境輸入了正確的值，然後重新驗證。 如果您在連線時仍有問題，請聯絡您的客戶代表。
