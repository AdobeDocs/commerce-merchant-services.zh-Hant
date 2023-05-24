---
title: 連線您的執行個體
description: 使用API金鑰和私密金鑰連線您的Commerce執行個體，並在設定中指定資料空間。
exl-id: 5038fd31-bac5-419e-a172-66919a9b5272
source-git-commit: 817a01e98876bddf5f41a253501984539b3351cd
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 0%

---

# 連線您的執行個體

[!DNL Payment Services] 由Commerce Services提供技術支援，並部署為SaaS （軟體即服務）。 您可以使用API金鑰和私密金鑰來連線Commerce執行個體，並使用在設定中指定資料空間 [商務服務聯結器](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html). **您只設定一次此連線。**

* 如果您有 *已連線您的執行個體*，透過取得及使用您的API憑證並設定Commerce Services，您可以繼續前往 [設定您的測試沙箱](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html).
* 如果您仍然 *需要連線您的執行個體*，請參閱本主題中有關以下內容的資訊： [取得API認證](#obtain-api-credentials) 和 [設定Commerce服務](#configure-commerce-services).
* 如果您是 *不確定您的執行個體是否已連線*，導覽至 **系統** >服務> **商務服務聯結器** 和檢視中的公開和私人API金鑰值 [!UICONTROL Sandbox Keys] 和 [!UICONTROL Production Keys] 區段，以及 *專案* 和 *資料空間* 中的欄位 [!UICONTROL SaaS Identifier] 區段。 如果這些值存在，則表示您的執行個體已連線。

## 取得API認證

若要使用Commerce SaaS服務，您必須將執行個體的API金鑰（Commerce公開API金鑰和私密金鑰）用於沙箱和生產，這會在您的中建立和管理。 [我的帳戶儀表板](https://account.magento.com/customer/account/login). [金鑰組](https://docs.magento.com/user-guide/configuration/services/saas.html) 可為Commerce帳戶建立（一個用於沙箱，一個用於生產），但一次只能主動使用一組。

>[!NOTE]
>
>需要協助存取您的 [!UICONTROL My Account] 儀表板？ 另請參閱 [建立Commerce帳戶](https://docs.magento.com/user-guide/magento/magento-account-create.html).

公開API金鑰一經建立，即可在您的「我的帳戶」控制面板中使用。 您可以視需要複製或刪除它。 當您為沙箱或生產環境建立公開API金鑰時，私人API金鑰會變成可見；它只能從後續的對話方塊複製或儲存，並且之後無法存取。

指定的API金鑰組對環境中的所有Commerce Services有效，因此，如果您已針對執行個體設定了Commerce Services，您的API金鑰組已存在於Commerce Services Connector中。

如果您的API金鑰遺失，新的API金鑰組必須為 [已產生](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#generate-an-api-key-and-private-key) 和 [已套用](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#configure-saas-project) 至管理員中的Commerce Services聯結器設定。 如果設定的金鑰有誤或設定中沒有任何金鑰，則付款服務中會出現帳戶驗證錯誤對話方塊，通知您該帳戶未驗證。

參閱 [使用API的可用Commerce Services清單](https://docs.magento.com/user-guide/system/saas.html#available-services).

若要瞭解如何為沙箱或生產環境產生API金鑰，請參閱 [認證](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#apikey).

>[!IMPORTANT]
>建議您不要重新產生API金鑰組 *和* 變更作用中生產執行個體上的SaaS識別碼和/或資料空間。 如果修改執行個體的資料，您將會遺失這些資料。

## 設定Commerce服務

執行個體間可以使用相同的API金鑰，但每個執行個體都必須有自己的金鑰 [SaaS資料空間](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#saasenv).

現在您已取得認證，您可以設定SaaS專案和Saas資料空間。

1. 於 _管理員_ 側欄，前往 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]**.
1. 按一下 **[!UICONTROL Configure Commerce Services]**.

   如果您尚未為帳戶設定Commerce Services，則會顯示此選項。

   系統會將您導向至「管理員」中的設定區域， **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**>**[!UICONTROL Commerce Services Connector]**，以設定您的Commerce Services聯結器。

1. 若要設定Commerce Services，請依照中所述的步驟操作 [SaaS設定](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#saasenv).
