---
title: 事件
description: 瞭解哪些事件捕獲資料並查看完整的架構定義。
source-git-commit: ce1ce5a7e028d1c957a9a36c73c371eedfb1e1e8
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---

# 項目信標事件

下面列出 [!DNL Commerce] 安裝Experience Platform連接器擴展時可用的事件。 這些事件收集的資料被發送到Adobe Experience Platform邊緣。 您還可以建立 [自定義事件](custom-events.md) 收集未在機箱中提供的其他資料。

按一下事件名稱以查看完整的架構定義。

| Event | 類型 |
|---|---|---|
| [添加到購物車](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/addToCartAEP.ts) | 店面 |
| [查看購物車](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/viewAEP.ts) | 店面 |
| [查看頁面](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/page/viewAEP.ts) | 店面 |
| [查看產品](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/viewAEP.ts) | 店面 |
| [開始簽出](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/initiateCheckoutAEP.ts) | 店面 |
| 完成簽出 | 店面 |
| [登錄](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signInAEP.ts) | 配置檔案 |
| [註銷](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signOutAEP.ts) | 配置檔案 |
| [建立帳戶](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/createAccountAEP.ts) | 配置檔案 |
| [編輯帳戶](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/editAccountAEP.ts) | 配置檔案 |

>[!NOTE]
>
> 的 `Sign In`。 `Sign Out`。 `Create Account`, `Update Account` 在嘗試特定操作時觸發事件。 它不表示操作成功。
