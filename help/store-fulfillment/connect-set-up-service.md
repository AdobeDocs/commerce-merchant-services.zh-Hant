---
title: 連接儲存履行解決方案
description: 通過建立和授權Adobe Commerce整合併將商店履行帳戶憑據添加到Adobe Commerce服務配置，建立Adobe Commerce與商店履行解決方案之間的聯繫。
role: User, Admin
level: Intermediate
source-git-commit: 42b0118b427b1e04186793b4a57c058bc1cabdd4
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# 連接儲存履行解決方案

通過配置管理員所需的身份驗證憑據和連接資料，建立Adobe Commerce和儲存履行服務之間的連接。

- **[配置 [!DNL Commerce integration settings]](#create-the-commerce-integration)** — 為儲存履行服務建立Adobe Commerce整合併生成訪問令牌以驗證來自儲存履行伺服器的傳入請求。

- **[配置Store Fulfilment Services的帳戶憑據](#configure-store-fulfillment-account-credentials)** — 添加憑據以將Adobe Commerce連接到您的Store Fullimment帳戶。

>[!NOTE]
>
>在開始測試之前，請完成連接配置並成功驗證連接。

## 建立Adobe Commerce整合

要將Adobe Commerce與Store Fulfillment服務整合，請建立Commerce整合併生成訪問令牌，這些令牌可用於驗證來自Store Fullimment伺服器的請求。

1. 從管理員中，建立Store Fulfillment的整合。

   - 命名副檔名
   - 輸入您的電子郵件地址
   - 輸入管理員帳戶密碼

1. 配置 [!UICONTROL API Resource Access permissions] 對於整合 — 選擇 `[!UICONTROL All]`

1. 通過保存和激活整合來生成用於驗證的訪問令牌。

1. 將訪問令牌複製並保存到安全的加密位置。

1. 與您的客戶經理合作，在「商店履行」端完成配置並授權整合。


>[!NOTE]
>
>有關詳細說明，請參見 [整合](https://docs.magento.com/user-guide/system/integrations.html) 的 _Adobe Commerce使用手冊_。

## 配置儲存履行帳戶憑據

完成進貨單後，將為您建立Walmart Store Fulfillment帳戶。 當以下憑據可用時，您將收到這些憑據：

- [!DNL Merchant ID]
- [!DNL Consumer ID]
- [!DNL Consumer Secret]
- [!DNL API Server URL]
- [!DNL Token Auth Server URL] （通常與上述配置相同）

配置和使用Store Fulfilment需要這些憑據。

>[!NOTE]
>
>帳戶建立過程可能需要一些時間才能完成。 等待憑據時， [查看amd為「商店履行」解決方案配置其他設定](service-config-settings-overview.md)。

### 添加憑據以連接到儲存履行

1. 配置 [帳戶憑證](enable-general.md) 生產和沙盒環境。

1. 從管理員，轉到 **[!UICONTROL Stores > Configuration > Services > Store Fulfillment by Walmart Commerce Technologies]**

1. 輸入為 **[!UICONTROL Production environment]**。 所有欄位都是必填欄位。

1. 選擇 **[!UICONTROL Save Config]**。

1. Test連接，方法是 **[!UICONTROL Validate Credentials]**。

>[!NOTE]
>
>如果憑據無效，請驗證您為每個環境輸入了正確的值並重新驗證。 如果連接仍有問題，請與客戶代表聯繫。








