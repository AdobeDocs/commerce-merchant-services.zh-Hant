---
title: 設定
description: 瞭解如何更改源 [!DNL Product Recommendations] 以及如何啟用可視化建議。
source-git-commit: 8c85d26474e371d30b76499f312553a07e329a80
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# 設定

當你 [配置SaaS資料空間](https://docs.magento.com/user-guide/configuration/services/saas.html) 對於Recommendations,SaaS資料空間收集目錄資料和儲存行為資料。 [Adobe Sensei](https://www.adobe.com/sensei.html) 分析資料並計算用於為產品Recommendations服務的產品關聯。

用於測試或試運行的非生產環境通常沒有用於提供真實產品建議的儲存行為資料的數量和質量。 只有在生產環境中才能捕獲規模的實際購物行為。 為解決此問題，Adobe Commerce允許您將生產環境中的產品建議與其他非生產SaaS資料空間一起使用。 在非生產環境中使用實際的店面資料，您可以預覽購物者看到的建議，並嘗試使用不同的推薦類型和放置位置。 Recommendations的SaaS資料空間不同，顧客可以預覽，但不能點擊。

## 選擇建議來源

要更改產品建議資料的源，請選擇包含要使用的行為資料的SaaS資料空間。 在開始之前，請確保：

- 儲存前資料收集必須 [已配置和啟用](install-configure.md) 用於您的生產環境 [驗證](verify.md) 行為資料正被發送到Adobe Commerce。
- 非生產環境目錄應與生產目錄基本相同。 使用類似的目錄可確保產品推薦單元的返回與生產中的產品推薦單元非常相似。

1. 登錄到非生產性Adobe Commerce環境的管理員。

1. 在 _管理_ 邊欄，轉到 **營銷** > _促銷_ > **產品Recommendations**。

1. 按一下 **設定**。

   ![產品推薦設定](assets/settings.png)
   _設定_

1. 在 _Recommendations源_ ，啟用 **從不同的SaaS資料空間獲取建議** 的雙曲餘切值。 的 _Recommendations源_ 部分僅在非生產環境中顯示。

   清單 _可用SaaS資料空間_ 的子菜單。

   ![產品推薦設定](assets/settings-select-saas.png)
   _設定_

1. 選擇要使用購物者資料的SaaS資料空間。

1. 按一下 **保存更改**。

   Adobe Commerce現在從所選資料空間中提取建議。

   >[!NOTE]
   >
   > 雖然您可以查看從非生產商店上的另一個SaaS資料空間獲取的建議，但您無法按一下這些建議。

### 配置新的SaaS資料空間

1. 在Recommendations源部分，按一下 **編輯配置**。

1. 按照說明配置新 [商務服務]。

## 啟用可視建議

如果 [可視產品Recommendations](install-configure.md) 模組已安裝，必須啟用Visual Recommendations才能使用 [視覺相似性](type.md#visualsim) 建議類型。

在 _視覺Recommendations_ 節，設定 **啟用VisualRecommendations** 到活動位置。
