---
title: 設定
description: 瞭解如何變更的來源 [!DNL Product Recommendations] 資料以及如何啟用視覺化建議。
exl-id: 8c074e11-e0cb-4d55-b646-30279c79bbc2
source-git-commit: 48e350167611a2737d79bf5decccd7f6f24c714c
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# 設定

當您 [設定SaaS資料空間](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) 對於Recommendations，SaaS資料空間會收集目錄資料和店面行為資料。 [Adobe Sensei](https://www.adobe.com/sensei.html) 會分析該資料，並計算用於提供產品Recommendations的產品關聯。

測試或測試的非生產環境通常沒有店面行為資料的數量或品質，無法提供逼真的產品建議。 實際購物者行為規模只能在生產環境中擷取。 為解決此問題，Adobe Commerce可讓您將生產環境中的產品推薦與其他非生產SaaS資料空間搭配使用。 在非生產環境中使用實際的店面資料可讓您預覽購物者看到的建議，並實驗不同的建議型別和放置位置。 購物者可以預覽不同SaaS資料空間的Recommendations，但無法點選。

>[!NOTE]
>
>透過REST使用產品Recommendations時， `alternateEnvironmentId` 引數可用來指定其他資料空間。 透過GraphQL使用產品Recommendations時，此引數無法使用。

## 選擇建議來源

若要變更產品建議資料的來源，請搭配您要使用的行為資料選擇SaaS資料空間。 開始之前，請確定：

- 店面資料收集必須 [已設定並啟用](install-configure.md) 為您的生產環境和 [已驗證](verify.md) 行為資料正在傳送至Adobe Commerce。
- 您的非生產環境目錄應該與生產目錄基本相同。 使用類似的目錄可確保產品推薦單位會非常接近生產時的推薦單位。

1. 登入非生產Adobe Commerce環境的管理員。

1. 於 _管理員_ 側欄，前往 **行銷** > _促銷活動_ > **產品Recommendations**.

1. 按一下 **設定**.

   ![產品推薦設定](assets/settings.png)
   _設定_

1. 在 _Recommendations來源_ 區段，啟用 **從不同的SaaS資料空間擷取建議** 選項。 此 _Recommendations來源_ 區段只會出現在非生產環境中。

   清單 _可用的SaaS資料空間_ 出現。

   ![產品推薦設定](assets/settings-select-saas.png)
   _設定_

1. 選取具有您要使用的購物者資料的SaaS資料空間。

1. 按一下 **儲存變更**.

   Adobe Commerce現在會從選取的資料空間擷取建議。

   >[!NOTE]
   >
   > 雖然您可以檢視從非生產存放區上的其他SaaS資料空間擷取的建議，但您無法按一下建議。

### 設定新的SaaS資料空間

1. 在Recommendations來源區段中，按一下 **編輯設定**.

1. 依照指示設定新的 [[!DNL Commerce] 服務](/help/landing/saas.md).

## 啟用視覺建議

如果 [視覺產品Recommendations](install-configure.md) 模組已安裝，您必須啟用Visual Recommendations才能使用 [視覺相似度](type.md#visualsim) 建議型別。

在 _Visual Recommendations_ 部分，設定 **啟用Visual Recommendations** 至使用中位置。
