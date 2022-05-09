---
title: 連接實例
description: 使用API密鑰和私鑰連接您的Commerce實例，並在配置中指定資料空間。
exl-id: 5038fd31-bac5-419e-a172-66919a9b5272
source-git-commit: 9596815e31402f23b399b223f3221074331c1773
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 0%

---

# 連接實例

[!DNL Payment Services] 由Commerce Services提供支援，並部署為SaaS（軟體即服務）。 您可以使用API密鑰和私鑰連接您的Commerce實例，並在配置中指定資料空間。 您只設定一次此連接。

請參閱 [Commerce Services連接器](https://docs.magento.com/user-guide/system/saas.html)有關此服務的詳細資訊，請參閱核心使用手冊中的{target=&quot;_blank&quot;}。

## 獲取API憑據

要使用Commerce SaaS服務，必須使用實例的API密鑰，這些密鑰是在您的 [我的帳戶儀表板](https://account.magento.com/customer/account/login){target=&quot;_blank&quot;}。 可以為Commerce帳戶建立兩個不同的API密鑰對 — 一個用於沙盒，一個用於生產（即時支付） — 儘管一次只能主動使用一對。

>[!NOTE]
>
>需要有關訪問 [!UICONTROL My Account] 儀表板？ 請參閱 [建立Commerce帳戶](https://docs.magento.com/user-guide/magento/magento-account-create.html)核心使用手冊中的{target=&quot;_blank&quot;}。

給定的API密鑰對對環境中的所有Commerce Services都有效，因此，如果已為Commerce實例配置了Commerce Services，則Admin中已存在API密鑰對。 如果私有API密鑰丟失，則必須生成新的API密鑰對，並將其應用於管理中的Commerce Services配置。

要瞭解如何為沙盒或生產環境生成API密鑰，請參見 [Commerce Services連接器](https://docs.magento.com/user-guide/system/saas.html)核心使用手冊中的{target=&quot;_blank&quot;}。

>[!IMPORTANT]
>
>如果重新生成API密鑰對並更改SaaS標識符，則此實例使用的所有Commerce Services都會連接到其他資料儲存區，您的訪問（包括以前儲存的資料）將丟失。 建議不要重新生成API密鑰對並更改活動生產實例上的SaaS標識符。

### Commerce API密鑰和私鑰

部分 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 功能部署為SaaS（軟體即服務），即Commerce Services。 要使用這些服務，您必須使用API密鑰和私鑰將Commerce實例連接到這些服務，並在 [配置](https://docs.magento.com/user-guide/configuration/services/saas.html){target=&quot;_blank&quot;}。

建立由MageID標識的Commerce帳戶時，可以生成Commerce API密鑰和私鑰。 使用Commerce Services，如 [!DNL Payment Services]。 [!DNL Product Recommendations]或 [!DNL Live Search]，許可證持有者必須生成這些密鑰才能通過權利驗證。 然後，這些密鑰可以傳遞給代表許可證持有者管理項目和環境的系統整合商或開發團隊。 如果您是解決方案整合商，您也有權根據自己的需要使用這些服務。 在這種情況下，商業夥伴合同的簽名者應生成密鑰。

### 生成API密鑰和私鑰

1. 登錄到您的Commerce帳戶，地址為 [https://account.magento.com/customer/account/login](https://account.magento.com/customer/account/login)。
1. 在 **[!UICONTROL Magento]** 頁籤 **[!UICONTROL API Portal]** 欄。
1. 從 _[!UICONTROL Environment]_菜單，選擇&#x200B;**[!UICONTROL Sandbox]**，則&#x200B;**[!UICONTROL Production]**。

   >[!IMPORTANT]
   >
   >兩個環境都需要API密鑰。

1. 在 _[!UICONTROL API Keys]_的&#x200B;**[!UICONTROL Add New]**。

   此操作將開啟一個對話框，用於下載新密鑰。

   >[!IMPORTANT]
   >
   >此對話框是您複製或下載密鑰的唯一機會。

1. 按一下 **[!UICONTROL Download]** 按一下 **[!UICONTROL Cancel]**。

   的 _[!UICONTROL API Keys]_部分現在顯示API密鑰。

1. 選擇或建立SaaS項目時，請同時複製API密鑰和私鑰。

   請參閱 [SaaS](https://docs.magento.com/user-guide/system/saas.html)有關詳細資訊，請參閱核心使用手冊中的{target=&quot;_blank&quot;}。

同一API密鑰可以跨實例使用，但每個實例必須有其自己的SaaS資料空間。

建立SaaS項目時，Commerce會根據您的Commerce許可證生成一個或多個SaaS資料空間：

* [!DNL Adobe Commerce]  — 一個生產資料空間；兩個測試資料空間
* [!DNL Magento Open Source]  — 一個生產資料空間；無測試資料空間

### 配置SaaS項目

>[!NOTE]
>
>如果你看不到 _[!UICONTROL Commerce Services Connector]_在Commerce配置中，必須為所需的Commerce Service安裝Commerce模組，如 [[!DNL Payment Services]](install.md)。

要選擇或建立SaaS項目，請從Commerce許可證持有者為您的商店請求Commerce API密鑰。

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**。
1. 在左面板中，展開 **[!UICONTROL Services]** 選擇 **[!UICONTROL Commerce Services Connector]**。
1. 在 _[!UICONTROL API Keys]_鍵。

   >[!IMPORTANT]
   >
   >添加兩者的鍵值 **[!UICONTROL sandbox]** 和 **[!UICONTROL production]** 環境。

1. 按一下 **[!UICONTROL Save Config]**.

   保存時，如果存在與API密鑰關聯的任何SaaS項目，則這些項目將顯示在 _[!UICONTROL SaaS Project]_的_[!UICONTROL SaaS Identifier]_ 的子菜單。

1. 如果沒有SaaS項目，請按一下 **[!UICONTROL Create Project]**。 然後，在中輸入SaaS項目的名稱 **[!UICONTROL Project Name]** 的子菜單。
1. 要用於Commerce儲存的當前配置，請選擇 **[!UICONTROL SaaS Data Space]**。

>[!IMPORTANT]
>
>如果在「我的帳戶」的「API門戶」部分重新生成密鑰，請立即更新管理配置中的API密鑰。 如果您生成新密鑰，並且不在管理員中更新它們，則您的SaaS擴展將不再工作，您將丟失寶貴的資料。

通過按一下 **[!UICONTROL Rename this Project]** 或 **[!UICONTROL Rename Data Space]** 按鈕。

## 配置Commerce Services

登機的第一步 [!DNL Payment Services] 即在管理中配置Commerce Services。

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]**。
1. 按一下 **[!UICONTROL Configure Commerce Services]**.

   如果尚未為帳戶配置Commerce Services，則此選項可見。

   您將被定向到管理中的配置區域， **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**>**[!UICONTROL Commerce Services Connector]**，以配置Commerce Services連接器。

1. 要配置Commerce Services，請按照中介紹的步驟操作 [商務服務](https://docs.magento.com/user-guide/system/saas.html#createsaasenv){target=&quot;_blank&quot;}。
