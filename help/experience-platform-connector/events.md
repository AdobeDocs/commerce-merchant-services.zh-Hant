---
title: 事件
description: 了解每個事件擷取並檢視完整結構定義的哪些資料。
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
source-git-commit: 589d22f488572411b6632ac37d7bc5b752f72e2d
workflow-type: tm+mt
source-wordcount: '1818'
ht-degree: 0%

---

# Experience Platform連接器事件

下列列出安裝Experience Platform連接器擴充功能時可用的商務事件。 這些事件收集的資料會傳送至Adobe Experience Platform Edge。 您也可以建立 [自訂事件](custom-events.md) 收集未隨箱提供的其他資料。

除了收集下列事件的資料外，您也會 [其他資料](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) 由Adobe Experience Platform Web SDK提供。

>[!NOTE]
>
>所有事件都包括 `personID` 欄位，此欄位是人員的唯一識別碼。

## addToCart

在產品新增至購物車或購物車中的產品數量增加時觸發。 [完整結構](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/addToCartAEP.ts).

### 類型

店面

### 收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `productListAdds` | 指出產品是否已新增至購物車。 值 `1` 表示已新增產品。 |
| `SKU` | 庫存單位。 產品的唯一識別碼。 |
| `name` | 產品的顯示名稱或人類看得懂的名稱 |
| `priceTotal` | 已應用所有折扣和稅後此訂單的合計 |
| `quantity` | 客戶已表示他們需要該產品的件數 |
| `discountAmount` | 指示應用的折扣金額 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 產品的貨幣 |
| `productImageUrl` | 產品的主影像URL |
| `selectedOptions` | 用於可配置產品的欄位。 `attribute` 標識可配置產品的屬性，例如 `size` 或 `color` 和 `value` 識別屬性的值，例如 `small` 或 `black`. |
| `cartID` | 識別客戶購物車的唯一ID |

## shoppingCartView

任何購物車頁面載入時觸發。 [完整結構](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/viewAEP.ts).

### 類型

店面

### 收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `productListViews` | 指出是否已檢視產品清單 |
| `productListItems` | 新增至購物車的產品陣列 |
| `SKU` | 庫存單位。 產品的唯一識別碼。 |
| `name` | 產品的顯示名稱或人類看得懂的名稱 |
| `priceTotal` | 已應用所有折扣和稅後此訂單的合計 |
| `quantity` | 客戶已表示他們需要該產品的件數 |
| `discountAmount` | 指示應用的折扣金額 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 產品的貨幣 |
| `productImageUrl` | 產品的主影像URL |
| `selectedOptions` | 用於可配置產品的欄位。 `attribute` 標識可配置產品的屬性，例如 `size` 或 `color` 和 `value` 識別屬性的值，例如 `small` 或 `black`. |
| `cartID` | 識別客戶購物車的唯一ID |

## pageView

在任何頁面載入時觸發。 [完整結構](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/page/viewAEP.ts).

### 類型

店面

### 收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `pageViews` | 指出是否已載入頁面。 A `value` of `1` 指出頁面已載入。 |

## productPageView

任何產品頁面載入時觸發。 [完整結構](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/viewAEP.ts).

### 類型

店面

### 收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `productViews` | 指出是否已檢視產品 |
| `productListItems` | 新增至購物車的產品陣列 |
| `SKU` | 庫存單位。 產品的唯一識別碼。 |
| `name` | 產品的顯示名稱或人類看得懂的名稱 |
| `priceTotal` | 已應用所有折扣和稅後此訂單的合計 |
| `discountAmount` | 指示應用的折扣金額 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 產品的貨幣 |
| `productImageUrl` | 產品的主影像URL |
| `selectedOptions` | 用於可配置產品的欄位。 `attribute` 標識可配置產品的屬性，例如 `size` 或 `color` 和 `value` 識別屬性的值，例如 `small` 或 `black`. |

## startCheckout

購物者按一下結帳按鈕時觸發。 [完整結構](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/initiateCheckoutAEP.ts).

### 類型

店面

### 收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `checkouts` | 指出結帳過程中是否發生動作 |
| `productListItems` | 新增至購物車的產品陣列 |
| `SKU` | 庫存單位。 產品的唯一識別碼。 |
| `name` | 產品的顯示名稱或人類看得懂的名稱 |
| `priceTotal` | 已應用所有折扣和稅後此訂單的合計 |
| `quantity` | 客戶已表示他們需要該產品的件數 |
| `discountAmount` | 指示應用的折扣金額 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 產品的貨幣 |
| `productImageUrl` | 產品的主影像URL |
| `selectedOptions` | 用於可配置產品的欄位。 `attribute` 標識可配置產品的屬性，例如 `size` 或 `color` 和 `value` 識別屬性的值，例如 `small` 或 `black`. |
| `cartID` | 識別客戶購物車的唯一ID |

## completeCheckout

購物者下訂單時觸發。 [完整結構](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/checkout/placeOrderAEP.ts).

### 類型

店面

### 收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `purchases` | 指示是否接受訂單 |
| `order` | 包含一個或多個產品的下單資訊 |
| `purchaseID` | 賣方為此採購或合同分配的唯一標識符。 無法保證ID是唯一的。 |
| `orderType` | 指出下單的類型，例如「結帳」或「立即購買」 |
| `payments` | 此訂單的付款清單 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 用於此付款項的貨幣代碼。 例如， `USD` 或 `EUR`. |
| `paymentAmount` | 付款的價值 |
| `paymentType` | 此訂單的付款方式。 選項包括： `cash`, `credit_card`, `debit_card`, `gift_card`, `check`, `paypal`, `wire_transfer`, `credit_card_reference`, `other` |
| `transactionID` | 此付款項的唯一事務處理標識符 |
| `shipping` | 一或多種產品的運送詳細資訊。 |
| `shippingMethod` | 由客戶選擇的運送方法，例如標準運送、快速運送、店內取貨等 |
| `shippingAmount` | 購物車中物料的總發運成本 |
| `promotionID` | 促銷活動的唯一識別碼（如果有） |
| `productListItems` | 新增至購物車的產品陣列 |
| `SKU` | 庫存單位。 產品的唯一識別碼。 |
| `name` | 產品的顯示名稱或人類看得懂的名稱 |
| `priceTotal` | 已應用所有折扣和稅後此訂單的合計 |
| `quantity` | 客戶已表示他們需要該產品的件數 |
| `discountAmount` | 指示應用的折扣金額 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 用於訂單總計的貨幣代碼。 |
| `productImageUrl` | 產品的主影像URL |
| `selectedOptions` | 用於可配置產品的欄位。 `attribute` 標識可配置產品的屬性，例如 `size` 或 `color` 和 `value` 識別屬性的值，例如 `small` 或 `black`. |

## 登入

購物者嘗試登入時觸發。 [完整結構](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signInAEP.ts).

>[!NOTE]
>
> 當嘗試特定動作時，就會觸發此事件。 它不表示動作成功。

### 類型

設定檔

### 收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `eventType` | 此時間系列記錄的主要事件類型，例如： `userAccount.login` |
| `person` | 個別演員、聯絡人或擁有者 |
| `accountID` | 擷取使用者帳戶ID |
| `personalEmailID` | 指定個人電子郵件的唯一標識符 |
| `address` | 例如， `name@domain.com` RFC2822和後續標準中通常定義的 |
| `userAccount` | 指出任何忠誠度詳細資訊、偏好設定、登入程式和其他帳戶偏好設定 |
| `login` | 指出訪客是否嘗試登入 |

## 登出

當購物者嘗試登出時觸發。 [完整結構](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signOutAEP.ts).

>[!NOTE]
>
> 當嘗試特定動作時，就會觸發此事件。 它不表示動作成功。

### 類型

設定檔

### 收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `eventType` | 此時間系列記錄的主要事件類型，例如： `userAccount.logout` |
| `userAccount` | 指出任何忠誠度詳細資訊、偏好設定、登入程式和其他帳戶偏好設定 |
| `logout` | 指出訪客是否嘗試登出 |

## createAccount

購物者嘗試建立帳戶時觸發。 [完整結構](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/createAccountAEP.ts).

>[!NOTE]
>
> 當嘗試特定動作時，就會觸發此事件。 它不表示動作成功。

### 類型

設定檔

### 收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `eventType` | 此時間系列記錄的主要事件類型，例如： `account.createProfile` |
| `person` | 個別演員、聯絡人或擁有者 |
| `accountID` | 擷取使用者帳戶ID |
| `accountType` | 擷取使用者帳戶類型，例如 `Personal` 或 `Company`（若適用） |
| `personalEmailID` | 指定個人電子郵件的唯一標識符 |
| `address` | 例如， `name@domain.com` RFC2822和後續標準中通常定義的 |
| `userAccount` | 指出任何忠誠度詳細資訊、偏好設定、登入程式和其他帳戶偏好設定 |
| `createProfile` | 指出使用者是否已建立帳戶設定檔 |

## editAccount

購物者嘗試編輯帳戶時觸發。 [完整結構](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/editAccountAEP.ts).

>[!NOTE]
>
> 當嘗試特定動作時，就會觸發此事件。 它不表示動作成功。

### 類型

設定檔

### 收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `eventType` | 此時間系列記錄的主要事件類型，例如： `account.updateProfile` |
| `person` | 個別演員、聯絡人或擁有者 |
| `accountID` | 擷取使用者帳戶ID |
| `accountType` | 擷取使用者帳戶類型，例如 `Personal` 或 `Company`（若適用） |
| `personalEmailID` | 指定個人電子郵件的唯一標識符 |
| `personalEmail` | 指定個人電子郵件地址 |
| `address` | 例如， `name@domain.com` RFC2822和後續標準中通常定義的 |
| `userAccount` | 指出任何忠誠度詳細資訊、偏好設定、登入程式和其他帳戶偏好設定 |
| `updateProfile` | 指出使用者是否已更新其帳戶設定檔 |

## searchRequestSent

在「輸入時搜尋」彈出視窗中，由下列事件觸發：

- 按Enter鍵
- 按一下 _查看全部_

由搜尋結果頁面上的下列事件觸發：

- 選取篩選
- 更改排序順序(_排序依據_)
- 變更排序方向（遞增或遞減）
- 變更每頁結果數(_每頁顯示數_)
- 導覽至下一頁
- 導覽至上一頁
- 導覽至不同頁面

[完整結構](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/search/searchRequestSentAEP.ts).

>[!NOTE]
>
>安裝B2B模組的Adobe Commerce Enterprise Edition不支援搜尋事件。

### 類型

搜尋

### 收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `searchRequest` | 指出是否已傳送搜尋請求 |
| `filter` | 指示是否應用了任何篩選器來限制搜索結果 |
| `attribute` （篩選） | 用於確定是否將項目包括在搜索結果中的項目的面向 |
| `value` | 用於確定搜索結果中包括哪些項的屬性值 |
| `isRange` | 若為true，則值表示可接受值範圍的端點 |
| `sort` | 指示應如何排序搜索結果 |
| `attribute` （排序） | 用於排序搜索結果中項的屬性 |
| `order` | 返回搜索結果的順序 |
| `query` | 搜索的詞 |

## searchResponseReceived

在「即時搜尋」傳回彈出視窗或搜尋結果頁面的「依您輸入時搜尋」結果時觸發。

[完整結構](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/search/searchResponseReceivedAEP.ts)

>[!NOTE]
>
>安裝B2B模組的Adobe Commerce Enterprise Edition不支援搜尋事件。

### 類型

搜尋

### 收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `searchResponse` | 指示是否已接收到搜索響應 |
| `suggestions` | 字串的陣列，包含目錄中存在且與搜尋查詢類似的產品和類別名稱 |
| `numberOfResults` | 傳回的產品數 |
| `productListItems` | 新增至購物車的一系列產品。 包括 `SKU`（庫存單位）和 `name` （顯示名稱或人類看得懂的名稱）。 |
