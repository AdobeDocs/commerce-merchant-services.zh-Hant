---
title: 連接實例
description: 使用API密鑰和私鑰連接您的Commerce實例，並在配置中指定資料空間。
exl-id: 5038fd31-bac5-419e-a172-66919a9b5272
source-git-commit: 817a01e98876bddf5f41a253501984539b3351cd
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 0%

---

# 連接實例

[!DNL Payment Services] 由Commerce Services提供支援，並部署為SaaS（軟體即服務）。 您可以使用API密鑰和私鑰連接您的Commerce實例，並使用 [Commerce Services連接器](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html)。 **您只設定一次此連接。**

* 如果 *已連接實例*，通過獲取和使用API憑據並配置Commerce Services，您可以繼續 [設定測試沙盒](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html)。
* 如果你還 *需要連接實例*，請參閱本主題中有關 [獲取API憑據](#obtain-api-credentials) 和 [配置Commerce Services](#configure-commerce-services)。
* 如果 *不確定實例是否已連接*，導航 **系統** >服務> **Commerce Services連接器** 並在 [!UICONTROL Sandbox Keys] 和 [!UICONTROL Production Keys] 的 *項目* 和 *資料空間* 的 [!UICONTROL SaaS Identifier] 的子菜單。 如果存在這些值，則連接實例。

## 獲取API憑據

要使用Commerce SaaS服務，您必須將實例的API密鑰（Commerce公用API密鑰和私鑰）用於沙盒和生產，這些密鑰在您的環境中建立和管理 [我的帳戶儀表板](https://account.magento.com/customer/account/login)。 [密鑰對](https://docs.magento.com/user-guide/configuration/services/saas.html) 可以為Commerce帳戶建立一個用於沙盒的帳戶和一個用於生產的帳戶，但一次只能使用一對。

>[!NOTE]
>
>需要有關訪問 [!UICONTROL My Account] 儀表板？ 請參閱 [建立Commerce帳戶](https://docs.magento.com/user-guide/magento/magento-account-create.html)。

公共API密鑰一旦建立，就始終可在「我的帳戶」儀表板中使用。 可以根據需要複製或刪除它。 為沙盒或生產建立公共API密鑰時，專用API密鑰將變為可見；它只能從隨後的對話框中複製或保存，以後無法訪問。

給定的API密鑰對對環境中的所有Commerce Services都有效，因此，如果已為實例配置了Commerce Services，則您的API密鑰對已存在於Commerce Services連接器中。

如果API密鑰丟失，則必須有新的API密鑰對 [生成](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#generate-an-api-key-and-private-key) 和 [應用](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#configure-saas-project) 到Admin中的Commerce Services連接器配置。 如果配置了錯誤的密鑰，或配置中不存在，則Payment Services中將顯示帳戶驗證錯誤對話框，通知您帳戶未驗證。

查看 [使用API的可用Commerce Services清單](https://docs.magento.com/user-guide/system/saas.html#available-services)。

要瞭解如何為沙盒或生產環境生成API密鑰，請參見 [憑據](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#apikey)。

>[!IMPORTANT]
>建議不要重新生成API密鑰對 *和* 更改活動生產實例上的SaaS標識符和/或資料空間。 如果實例被修改，則會丟失資料。

## 配置Commerce Services

同一API密鑰可以跨實例使用，但每個實例必須有其自己的 [SaaS資料空間](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#saasenv)。

現在您已獲得憑據，您可以配置SaaS項目和Saas資料空間。

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]**。
1. 按一下 **[!UICONTROL Configure Commerce Services]**。

   如果尚未為帳戶配置Commerce Services，則此選項可見。

   您將被定向到管理中的配置區域， **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**>**[!UICONTROL Commerce Services Connector]**，以配置Commerce Services連接器。

1. 要配置Commerce Services，請按照中介紹的步驟操作 [SaaS配置](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#saasenv)。
