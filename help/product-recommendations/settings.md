---
title: 設定
description: 了解如何變更 [!DNL Product Recommendations] 資料及如何啟用視覺建議。
exl-id: 8c074e11-e0cb-4d55-b646-30279c79bbc2
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# 設定

當您 [配置SaaS資料空間](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) 對於Recommendations,SaaS資料空間收集目錄資料和儲存行為資料。 [Adobe Sensei](https://www.adobe.com/sensei.html) 分析該資料並計算用於提供產品Recommendations的產品關聯。

用於測試或測試的非生產環境通常沒有店面行為資料的數量或品質，無法提供實際的產品建議。 實際規模購物者行為只能在生產環境中擷取。 為解決此問題，Adobe Commerce允許您將生產環境的產品建議與其他非生產SaaS資料空間搭配使用。 在非生產環境中使用實際的店面資料，可讓您預覽購物者所看到的建議，並試驗不同的建議類型和放置位置。 來自不同SaaS資料空間的Recommendations可由購物者預覽，但無法點按。

## 選擇建議來源

要更改產品建議資料的源，請選擇SaaS資料空間以及要使用的行為資料。 開始之前，請確定：

- Storefront資料收集必須 [已設定及啟用](install-configure.md) 適用於您的生產環境 [已驗證](verify.md) 行為資料正在傳送至Adobe Commerce。
- 您的非生產環境目錄應與生產目錄基本相同。 使用類似的目錄可確保產品建議單位傳回的內容與生產環境相近。

1. 登入非生產Adobe Commerce環境的管理員。

1. 在 _管理_ 邊欄，轉到 **行銷** > _促銷活動_ > **產品Recommendations**.

1. 按一下 **設定**.

   ![產品建議設定](assets/settings.png)
   _設定_

1. 在 _Recommendations來源_ 部分，啟用 **從不同的SaaS資料空間擷取建議** 選項。 此 _Recommendations來源_ 區段只會顯示在非生產環境中。

   清單 _可用的SaaS資料空間_ 框。

   ![產品建議設定](assets/settings-select-saas.png)
   _設定_

1. 選擇要使用購物者資料的SaaS資料空間。

1. 按一下 **儲存變更**.

   Adobe Commerce現在會從選取的資料空間擷取建議。

   >[!NOTE]
   >
   > 雖然您可以在非生產店面上檢視從其他SaaS資料空間擷取的建議，但您無法按一下建議。

### 配置新的SaaS資料空間

1. 在Recommendations來源區段中，按一下 **編輯配置**.

1. 依照指示設定新 [[!DNL Commerce] 服務](/help/landing/saas.md).

## 啟用視覺建議

若 [Visual Product Recommendations](install-configure.md) 模組已安裝，您必須啟用Visual Recommendations才能使用 [視覺相似度](type.md#visualsim) 建議類型。

在 _Visual Recommendations_ 區段，設定 **啟用Visual Recommendations** 到活動位置。
