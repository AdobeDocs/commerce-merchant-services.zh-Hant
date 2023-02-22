---
title: 連接您的執行個體
description: 使用API金鑰和私密金鑰連線您的Commerce執行個體，並在設定中指定資料空間。
exl-id: 5038fd31-bac5-419e-a172-66919a9b5272
source-git-commit: 817a01e98876bddf5f41a253501984539b3351cd
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 0%

---

# 連接您的執行個體

[!DNL Payment Services] 由Commerce Services提供支援，並部署為SaaS（軟體即服務）。 您使用API金鑰和私密金鑰來連線您的Commerce執行個體，並使用 [商務服務連接器](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html). **您只設定此連線一次。**

* 若您有 *已連接您的實例*，取得並使用您的API憑證和設定Commerce Services，您可以繼續 [設定測試沙箱](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html).
* 如果你還 *需要連接您的執行個體*，請參閱本主題中關於 [取得API憑證](#obtain-api-credentials) 和 [配置商務服務](#configure-commerce-services).
* 如果您 *不確定您的執行個體是否已連線*，導覽至 **系統** >服務> **商務服務連接器** ，並在 [!UICONTROL Sandbox Keys] 和 [!UICONTROL Production Keys] 區段，以及 *專案* 和 *資料空間* 欄位 [!UICONTROL SaaS Identifier] 區段。 如果這些值存在，表示您的執行個體已連線。

## 取得API憑證

若要使用Commerce SaaS服務，您必須將執行個體的API金鑰（商務公開API金鑰和私密金鑰）用於沙箱和生產，這些金鑰是在您的 [我的帳戶控制面板](https://account.magento.com/customer/account/login). [金鑰組](https://docs.magento.com/user-guide/configuration/services/saas.html) 可為商務帳戶（一個用於沙箱，一個用於生產）建立，但一次只能主動使用一對。

>[!NOTE]
>
>需要存取您 [!UICONTROL My Account] 儀表板？ 請參閱 [建立商務帳戶](https://docs.magento.com/user-guide/magento/magento-account-create.html).

公開API金鑰建立後，一律可在「我的帳戶控制面板」中使用。 您可視需要加以複製或刪除。 當您為沙箱或生產環境建立公開API金鑰時，私人API金鑰便會顯示；它只能從隨後的對話框中複製或保存，以後無法訪問。

指定的API金鑰組對環境中的所有Commerce Services均有效，因此如果您已為執行個體設定Commerce Services，則您的API金鑰組已存在於Commerce Services Connector中。

如果您的API金鑰遺失，則新的API金鑰組必須 [產生](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#generate-an-api-key-and-private-key) 和 [已套用](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#configure-saas-project) 至「管理員」中的「商務服務連接器」設定。 如果配置了錯誤的密鑰或配置中不存在任何密鑰，則支付服務中將顯示帳戶驗證錯誤對話框，通知您帳戶未驗證。

請參閱 [使用API的可用商務服務清單](https://docs.magento.com/user-guide/system/saas.html#available-services).

若要了解如何為沙箱或生產環境產生API金鑰，請參閱 [憑證](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#apikey).

>[!IMPORTANT]
>建議您不要重新產生API金鑰組 *和* 更改活動生產實例上的SaaS標識符和/或資料空間。 如果修改了執行個體，您會失去其資料。

## 配置商務服務

同一個API金鑰可跨例項使用，但每個例項必須有各自的 [SaaS資料空間](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#saasenv).

現在，您已獲得了您的憑據，可以配置您的SaaS項目和Saas資料空間。

1. 在 _管理_ 邊欄，轉到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]**.
1. 按一下 **[!UICONTROL Configure Commerce Services]**.

   如果您尚未為您的帳戶設定Commerce Services，則會顯示此選項。

   系統會將您導向至管理員的設定區域， **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**>**[!UICONTROL Commerce Services Connector]**，以設定您的Commerce Services Connector。

1. 若要設定您的商務服務，請遵循 [SaaS配置](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#saasenv).
