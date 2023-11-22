---
title: 連線您的執行個體
description: 使用API金鑰和私密金鑰連線您的Commerce執行個體，並在設定中指定資料空間。
exl-id: 5038fd31-bac5-419e-a172-66919a9b5272
feature: Payments, Checkout, Configuration, Saas
source-git-commit: 6769e29a4ae07b8cf15aa2da3cac2fe8583497e0
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 0%

---

# 連線您的執行個體

[!DNL Payment Services] 由Commerce Services提供技術支援，並部署為SaaS （軟體即服務）。 您可以使用API金鑰和私密金鑰來連線您的Commerce執行個體，並使用在設定中指定資料空間 [Commerce服務聯結器](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html). **您只設定一次此連線。**

* 如果您有 *已連線您的執行個體*，透過取得及使用您的API憑證並設定Commerce Services，您可以繼續前往 [設定您的測試沙箱](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html).
* 如果您仍然 *需要連線您的執行個體*，請參閱本主題中關於以下內容的資訊： [取得API認證](#obtain-api-credentials) 和 [設定Commerce服務](#configure-commerce-services).
* 如果您是 *不確定您的執行個體是否已連線*，導覽至 **系統** >服務> **Commerce服務聯結器** 並檢視中的公開和私人API金鑰值 [!UICONTROL Sandbox Keys] 和 [!UICONTROL Production Keys] 區段，以及 *專案* 和 *資料空間* 中的欄位 [!UICONTROL SaaS Identifier] 區段。 如果這些值存在，表示您的執行個體已連線。

## 取得API認證

若要使用Commerce SaaS服務，您必須在沙箱和生產中使用執行個體的API金鑰（Commerce公開API金鑰和私密金鑰），這些是在您的中建立和管理的。 [我的帳戶儀表板](https://account.magento.com/customer/account/login). [金鑰組](https://docs.magento.com/user-guide/configuration/services/saas.html) 可為Commerce帳戶建立（一個用於沙箱，一個用於生產），但一次只能主動使用一組。

>[!NOTE]
>
>需要協助存取 [!UICONTROL My Account] 儀表板？ 另請參閱 [建立Commerce帳戶](https://docs.magento.com/user-guide/magento/magento-account-create.html).

公開API金鑰一經建立，即可在您的「我的帳戶控制面板」中使用。 您可以視需要複製或刪除它。 當您為沙箱或生產環境建立公用API金鑰時，私用API金鑰會變成可見；它只能從後續的對話方塊中複製或儲存，並且之後無法存取。

指定的API金鑰組對環境中的所有Commerce服務有效，因此，如果您已針對執行個體設定了Commerce服務，則Commerce Services聯結器中已存在您的API金鑰組。

如果您的API金鑰遺失，則新的API金鑰組必須為 [已產生](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#generate-an-api-key-and-private-key) 和 [已套用](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#configure-saas-project) 至管理員中的Commerce Services聯結器設定。 如果設定了錯誤的金鑰或設定中沒有金鑰，則付款服務中會顯示帳戶驗證錯誤對話方塊，通知您帳戶未驗證。

檢視 [使用API的可用Commerce服務清單](https://docs.magento.com/user-guide/system/saas.html#available-services).

若要瞭解如何為沙箱或生產環境產生API金鑰，請參閱 [認證](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#apikey).

>[!IMPORTANT]
>
>建議您不要重新產生API金鑰組 *和* 變更作用中生產執行個體上的SaaS識別碼和/或資料空間。 如果修改執行個體的資料，您將會遺失這些資料。

## 設定Commerce服務

執行個體間可以使用相同的API金鑰，但每個執行個體都必須有自己的 [SaaS資料空間](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#saasenv).

>[!NOTE]
>
>商家必須使用針對MageID產生的相同金鑰來取得其付款權益。

現在您已取得認證，您可以設定SaaS專案和Saas資料空間。

1. 在 _管理員_ 側欄，前往 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]**.
1. 按一下 **[!UICONTROL Configure Commerce Services]**.

   如果您尚未為帳戶設定Commerce Services，便會顯示此選項。

   您會被導向至「管理員」中的設定區域， **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**>**[!UICONTROL Commerce Services Connector]**，以設定您的Commerce Services聯結器。

1. 若要設定您的Commerce服務，請遵循中所述的步驟 [SaaS設定](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#saasenv).
