---
title: 事件
description: 瞭解哪些事件捕獲資料並查看完整的架構定義。
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
source-git-commit: 2b735c292920bb0e9052d86bf152748e7ce96079
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Experience Platform連接器事件

下面列出了安裝Experience Platform連接器擴展時可用的Commerce事件。 這些事件收集的資料被發送到Adobe Experience Platform邊緣。 您還可以建立 [自定義事件](custom-events.md) 收集未在機箱中提供的其他資料。

按一下事件名稱以查看完整的架構定義。

| Event | 類型 |
|---|---|
| [添加到購物車](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/addToCartAEP.ts) | 店面 |
| [查看購物車](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/viewAEP.ts) | 店面 |
| [查看頁面](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/page/viewAEP.ts) | 店面 |
| [查看產品](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/viewAEP.ts) | 店面 |
| [開始簽出](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/initiateCheckoutAEP.ts) | 店面 |
| [完成簽出](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/checkout/placeOrderAEP.ts) | 店面 |
| [登錄](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signInAEP.ts) | 配置檔案 |
| [註銷](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signOutAEP.ts) | 配置檔案 |
| [建立帳戶](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/createAccountAEP.ts) | 配置檔案 |
| [編輯帳戶](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/editAccountAEP.ts) | 配置檔案 |
| [已發送搜索請求](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/search/searchRequestSentAEP.ts) | 搜索 |
| [已接收搜索響應](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/search/searchResponseReceivedAEP.ts) | 搜索 |

>[!NOTE]
>
> 的 `Sign In`。 `Sign Out`。 `Create Account`, `Update Account` 在嘗試特定操作時觸發事件。 它不表示操作成功。
