---
title: 事件
description: 了解每個事件擷取的資料。
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
source-git-commit: 975854dbdae32e5e51bb57593cf122627d01571f
workflow-type: tm+mt
source-wordcount: '3141'
ht-degree: 0%

---

# Experience Platform連接器事件

下列列出安裝Experience Platform連接器擴充功能時可用的商務事件。 這些事件收集的資料會傳送至Adobe Experience Platform Edge。 您也可以建立 [自訂事件](custom-events.md) 收集未隨箱提供的其他資料。

除了收集下列事件的資料外，您也會 [其他資料](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) 由Adobe Experience Platform Web SDK提供。

## 店面事件

+++ 店面事件會在購物者瀏覽您的網站時，從他們收集匿名的行為資料。 這些事件收集的資料可用來建立針對特定一組購物者的促銷活動和促銷活動。

>[!NOTE]
>
>所有店面事件包括 `identityMap` 欄位，此欄位是人員的唯一識別碼。

### addToCart

| 說明 | XDM事件名稱 |
|---|---|
| 在產品新增至購物車或購物車中的產品數量增加時觸發。 | `commerce.productListAdds` |

#### 從addToCart收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `productListAdds` | 指出產品是否已新增至購物車。 值 `1` 表示已新增產品。 |
| `productListItems` | 新增至購物車的產品陣列 |
| `SKU` | 庫存單位。 產品的唯一識別碼。 |
| `name` | 產品的顯示名稱或人類看得懂的名稱 |
| `priceTotal` | 產品行項目的總價 |
| `quantity` | 新增至購物車的產品件數 |
| `discountAmount` | 指示應用的折扣金額 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 產品的貨幣 |
| `productImageUrl` | 產品的主影像URL |
| `selectedOptions` | 用於可配置產品的欄位。 `attribute` 標識可配置產品的屬性，例如 `size` 或 `color` 和 `value` 識別屬性的值，例如 `small` 或 `black`. |
| `cartID` | 識別客戶購物車的唯一ID |

### openCart

| 說明 | XDM事件名稱 |
|---|---|
| 建立新購物車時觸發，即產品新增至空購物車時。 | `commerce.productListOpens` |

#### 從openCart收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `productListOpens` | 指出是否已建立購物車。 值 `1` 表示已建立購物車。 |
| `productListItems` | 新增至購物車的產品陣列 |
| `SKU` | 庫存單位。 產品的唯一識別碼。 |
| `name` | 產品的顯示名稱或人類看得懂的名稱 |
| `priceTotal` | 產品行項目的總價 |
| `quantity` | 新增至購物車的產品件數 |
| `discountAmount` | 指示應用的折扣金額 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 產品的貨幣 |
| `productImageUrl` | 產品的主影像URL |
| `selectedOptions` | 用於可配置產品的欄位。 `attribute` 標識可配置產品的屬性，例如 `size` 或 `color` 和 `value` 識別屬性的值，例如 `small` 或 `black`. |
| `cartID` | 識別客戶購物車的唯一ID |

### removeFromCart

| 說明 | XDM事件名稱 |
|---|---|
| 每次移除產品或每次減少購物車中的產品數量時觸發。 | `commerce.productListRemovals` |

#### 從removeFromCart收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `productListRemovals` | 指出是否從購物車中移除產品。 值 `1` 表示產品已從購物車中移除。 |
| `productListItems` | 從購物車移除的一系列產品 |
| `SKU` | 庫存單位。 產品的唯一識別碼。 |
| `name` | 產品的顯示名稱或人類看得懂的名稱 |
| `priceTotal` | 產品行項目的總價 |
| `quantity` | 從購物車移除的產品件數 |
| `discountAmount` | 指示應用的折扣金額 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 產品的貨幣 |
| `productImageUrl` | 產品的主影像URL |
| `selectedOptions` | 用於可配置產品的欄位。 `attribute` 標識可配置產品的屬性，例如 `size` 或 `color` 和 `value` 識別屬性的值，例如 `small` 或 `black`. |
| `cartID` | 識別客戶購物車的唯一ID |

### shoppingCartView

| 說明 | XDM事件名稱 |
|---|---|
| 任何購物車頁面載入時觸發。 | `commerce.productListViews` |

#### 從shoppingCartView收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `productListViews` | 指出是否已檢視產品清單 |
| `productListItems` | 購物車中的一系列產品 |
| `SKU` | 庫存單位。 產品的唯一識別碼。 |
| `name` | 產品的顯示名稱或人類看得懂的名稱 |
| `priceTotal` | 產品行項目的總價 |
| `quantity` | 購物車中的產品件數 |
| `discountAmount` | 指示應用的折扣金額 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 產品的貨幣 |
| `productImageUrl` | 產品的主影像URL |
| `selectedOptions` | 用於可配置產品的欄位。 `attribute` 標識可配置產品的屬性，例如 `size` 或 `color` 和 `value` 識別屬性的值，例如 `small` 或 `black`. |
| `cartID` | 識別客戶購物車的唯一ID |

### pageView

| 說明 | XDM事件名稱 |
|---|---|
| 在任何頁面載入時觸發。 | `web.webpagedetails.pageViews` |

#### 從pageView收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `pageViews` | 指出是否已載入頁面。 A `value` of `1` 指出頁面已載入。 |

### productPageView

| 說明 | XDM事件名稱 |
|---|---|
| 任何產品頁面載入時觸發。 | `commerce.productViews` |

#### 從productPageView收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `productViews` | 指出是否已檢視產品 |
| `productListItems` | 購物車中的一系列產品 |
| `SKU` | 庫存單位。 產品的唯一識別碼。 |
| `name` | 產品的顯示名稱或人類看得懂的名稱 |
| `priceTotal` | 產品行項目的總價 |
| `discountAmount` | 指示應用的折扣金額 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 產品的貨幣 |
| `productImageUrl` | 產品的主影像URL |
| `selectedOptions` | 用於可配置產品的欄位。 `attribute` 標識可配置產品的屬性，例如 `size` 或 `color` 和 `value` 識別屬性的值，例如 `small` 或 `black`. |

### startCheckout

| 說明 | XDM事件名稱 |
|---|---|
| 購物者按一下結帳按鈕時觸發。 | `commerce.checkouts` |

#### 從startCheckout收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `checkouts` | 指出結帳過程中是否發生動作 |
| `productListItems` | 購物車中的一系列產品 |
| `SKU` | 庫存單位。 產品的唯一識別碼。 |
| `name` | 產品的顯示名稱或人類看得懂的名稱 |
| `priceTotal` | 產品行項目的總價 |
| `quantity` | 購物車中的產品件數 |
| `discountAmount` | 指示應用的折扣金額 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 產品的貨幣 |
| `productImageUrl` | 產品的主影像URL |
| `selectedOptions` | 用於可配置產品的欄位。 `attribute` 標識可配置產品的屬性，例如 `size` 或 `color` 和 `value` 識別屬性的值，例如 `small` 或 `black`. |
| `cartID` | 識別客戶購物車的唯一ID |

### completeCheckout

| 說明 | XDM事件名稱 |
|---|---|
| 購物者下訂單時觸發。 | `commerce.order` |

#### 從completeCheckout收集的資料

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
| `personalEmail` | 指定個人電子郵件地址 |
| `address` | 例如， `name@domain.com` RFC2822和後續標準中通常定義的 |
| `productListItems` | 購物車中的一系列產品 |
| `SKU` | 庫存單位。 產品的唯一識別碼。 |
| `name` | 產品的顯示名稱或人類看得懂的名稱 |
| `priceTotal` | 產品行項目的總價 |
| `quantity` | 購物車中的產品件數 |
| `discountAmount` | 指示應用的折扣金額 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 用於訂單總計的貨幣代碼。 |
| `productImageUrl` | 產品的主影像URL |
| `selectedOptions` | 用於可配置產品的欄位。 `attribute` 標識可配置產品的屬性，例如 `size` 或 `color` 和 `value` 識別屬性的值，例如 `small` 或 `black`. |
+++

## 設定檔事件

+++
設定檔事件包含帳戶資訊，例如 `signIn`, `signOut`, `createAccount`，和 `editAccount`. 此資料可協助填入更妥善定義區段或執行行銷活動所需的重要客戶詳細資訊，例如您想要鎖定居住在紐約的購物者。

### 登入

| 說明 | XDM事件名稱 |
|---|---|
| 購物者嘗試登入時觸發。 | `userAccount.login` |

>[!NOTE]
>
> 當嘗試特定動作時，就會觸發此事件。 它不表示動作成功。

#### 從signIn收集的資料

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

### 登出

| 說明 | XDM事件名稱 |
|---|---|
| 當購物者嘗試登出時觸發。 | `userAccount.logout` |

>[!NOTE]
>
> 當嘗試特定動作時，就會觸發此事件。 它不表示動作成功。

#### 從signOut收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `eventType` | 此時間系列記錄的主要事件類型，例如： `userAccount.logout` |
| `userAccount` | 指出任何忠誠度詳細資訊、偏好設定、登入程式和其他帳戶偏好設定 |
| `logout` | 指出訪客是否嘗試登出 |

### createAccount

| 說明 | XDM事件名稱 |
|---|---|
| 購物者嘗試建立帳戶時觸發。 | `userAccount.createProfile` |

>[!NOTE]
>
> 當嘗試特定動作時，就會觸發此事件。 它不表示動作成功。

#### 從createAccount收集的資料

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

### editAccount

| 說明 | XDM事件名稱 |
|---|---|
| 購物者嘗試編輯帳戶時觸發。 | `userAccount.updateProfile` |

>[!NOTE]
>
> 當嘗試特定動作時，就會觸發此事件。 它不表示動作成功。

#### 從editAccount收集的資料

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
+++

## 搜尋事件

+++ 搜尋事件提供與購物者意圖相關的資料。 洞察購物者的意圖，可協助商戶了解購物者如何搜尋項目、點按內容，以及最終購買或放棄。 如果您想要鎖定搜尋您最暢銷產品、但絕不購買產品的現有購物者，即可使用此資料。

### searchRequestSent

| 說明 | XDM事件名稱 |
|---|---|
| 在「輸入時搜尋」彈出視窗中，由下列事件觸發：<br>按Enter鍵，按一下 _查看全部_<br>&#x200B;由搜尋結果頁面上的下列事件觸發：<br>選取篩選，變更排序順序(_排序依據_)、變更排序方向（遞增或遞減）、變更每頁結果數(_每頁顯示數_)，導覽至下一頁，導覽至上一頁，導覽至不同頁面 | `searchRequest` |

>[!NOTE]
>
>安裝B2B模組的Adobe Commerce Enterprise Edition不支援搜尋事件。

#### 從searchRequestSent收集的資料

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

### searchResponseReceived

| 說明 | XDM事件名稱 |
|---|---|
| 在「即時搜尋」傳回彈出視窗或搜尋結果頁面的「依您輸入時搜尋」結果時觸發。 | `searchResponse` |

>[!NOTE]
>
>安裝B2B模組的Adobe Commerce Enterprise Edition不支援搜尋事件。

#### 從searchResponseReceived收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `searchResponse` | 指示是否已接收到搜索響應 |
| `suggestions` | 字串的陣列，包含目錄中存在且與搜尋查詢類似的產品和類別名稱 |
| `numberOfResults` | 傳回的產品數 |
| `productListItems` | 購物車中的一系列產品。 |
| `SKU` | 庫存單位。 產品的唯一識別碼。 |
| `name` | 產品的顯示名稱或人類看得懂的名稱 |
| `productImageUrl` | 產品的主影像URL |

+++

## （測試版）後台活動

>[!NOTE]
>
>對於已註冊我們後台測試版的商戶，您可以訪問後台活動。 如果您想參加後台測試計畫，請聯繫 [drios@adobe.com](mailto:drios@adobe.com).

+++ 後台事件包含有關訂單狀態的資訊，例如訂單被下放、取消、退貨或發運。 這些伺服器端事件收集的資料會顯示購物者訂單的360檢視。 這可協助商戶在開發行銷活動時，更佳地鎖定或分析整個訂單狀態。 例如，您可以找出某些產品類別中的趨勢，這些趨勢在一年中的不同時間表現良好。 例如，在寒冷的月份賣得更好的冬裝，或是一些消費者對這些年感興趣的產品顏色。 此外，訂單狀態資料可協助您透過了解購物者根據先前訂單進行轉換的傾向，來計算期限客戶值。

### orderPlaced

| 說明 | XDM事件名稱 |
|---|---|
| 購物者下訂單時觸發。 | `commerce.orderPlaced` |

#### 從orderPlaced收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `identityMap` | 包含識別客戶的電子郵件地址 |
| `address` | 例如， `name@domain.com` RFC2822和後續標準中通常定義的 |
| `eventType` | `commerce.orderPlaced` |
| `productListItems` | 順序中的產品陣列 |
| `name` | 產品的顯示名稱或人類看得懂的名稱 |
| `SKU` | 庫存單位。 產品的唯一識別碼。 |
| `quantity` | 購物車中的產品件數 |
| `priceTotal` | 產品行項目的總價 |
| `discountAmount` | 指示應用的折扣金額 |
| `order` | 包含訂單的相關資訊 |
| `purchaseID` | 賣方為此採購或合同分配的唯一標識符。 無法保證ID是唯一的 |
| `purchaseOrderNumber` | 由購買者為此購買或合同分配的唯一標識符 |
| `payments` | 此訂單的付款清單 |
| `paymentType` | 此訂單的付款方式。 枚舉，允許自定義值。 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 用於此付款項的幣種代碼 |
| `paymentAmount` | 付款的價值 |
| `shipping` | 一個或多個產品的發運詳細資訊 |
| `shippingMethod` | 由客戶選擇的運送方法，例如標準運送、快速運送、店內取貨等 |
| `shippingAddress` | 實際運送地址 |
| `street1` | 主要街道級別資訊、公寓編號、街道編號和街道名稱 |
| `shippingAmount` | 客戶需要支付的運費。 |
| `billingAddress` | 帳單郵遞區號 |
| `street1` | 主要街道級別資訊、公寓編號、街道編號和街道名稱 |
| `street2` | 街道級別資訊的其他欄位 |
| `city` | 城市名稱 |
| `state` | 州名。 這是自由格式欄位。 |
| `postalCode` | 位置的郵遞區號。 郵遞區號不適用於所有國家/地區。 在某些國家/地區，這只會包含部分郵遞區號。 |
| `country` | 政府管理領土的名稱。 除 `xdm:countryCode`，此為自由格式欄位，可以使用任何語言提供國家/地區名稱。 |

### orderShipped

| 說明 | XDM事件名稱 |
|---|---|
| 在發運訂單時觸發。 | `commerce.orderLineItemShipped` |

#### 從orderShipped收集的資料

下表說明為此事件收集的資料。
|欄位|說明| |—|—| |`identityMap`|包含識別客戶的電子郵件地址| |`address`|例如， `name@domain.com` 如RFC2822和後續標準中通常定義| |`eventType`|`commerce.orderLineItemShipped`| |`productListItems`|按順序排列的產品陣列| |`name`|產品的顯示名稱或人類看得懂的名稱| |`SKU`|庫存單位。 產品的唯一識別碼。| |`quantity`|購物車中的產品件數| |`priceTotal`|產品行項目的總價| |`discountAmount`|指示應用的折扣金額| |`order`|包含有關訂單的資訊| |`purchaseID`|賣方為此採購或合同分配的唯一標識符。 無法保證ID是唯一的| |`purchaseOrderNumber`|購買者為此購買或合同分配的唯一標識符| |`payments`|此訂單的付款清單| |`paymentType`|此訂單的付款方式。 枚舉，允許自定義值。| |`currencyCode`| [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 用於此付款項的貨幣代碼| |`paymentAmount`|付款的價值| |`shipping`|一個或多個產品的發運詳細資訊| |`shippingMethod`|客戶選擇的發運方法，如標準交貨、快速交貨、在商店取貨等| |`shippingAddress`|實際運送地址| |`street1`|主要街道級別資訊、公寓號、街號和街道名稱| |`shippingAmount`|客戶需要支付的運費。| |`billingAddress`|帳單郵遞區號| |`street1`|主要街道級別資訊、公寓號、街號和街道名稱| |`street2`|街道資訊的其他欄位| |`city`|城市名稱| |`state`|狀態名稱。 這是自由格式欄位。| |`postalCode`|位置的郵遞區號。 郵遞區號不適用於所有國家/地區。 在某些國家/地區，這只會包含部分郵遞區號。| |`country`|政府管理領土的名稱。 除 `xdm:countryCode`，這是自由格式欄位，可以使用任何語言提供國家/地區名稱。|

### orderCancelled

| 說明 | XDM事件名稱 |
|---|---|
| 購物者取消訂單時觸發。 | `commerce.orderCancelled` |

#### 從orderCancelled收集的資料

下表說明為此事件收集的資料。
|欄位|說明| |—|—| |`identityMap`|包含識別客戶的電子郵件地址| |`address`|例如， `name@domain.com` 如RFC2822和後續標準中通常定義| |`eventType`|`commerce.orderCancelled`| |`productListItems`|按順序排列的產品陣列| |`name`|產品的顯示名稱或人類看得懂的名稱| |`SKU`|庫存單位。 產品的唯一識別碼。| |`quantity`|購物車中的產品件數| |`priceTotal`|產品行項目的總價| |`discountAmount`|指示應用的折扣金額| |`order`|包含有關訂單的資訊| |`purchaseID`|賣方為此採購或合同分配的唯一標識符。 無法保證ID是唯一的| |`purchaseOrderNumber`|購買者為此購買或合同分配的唯一標識符|

### orderRequied

| 說明 | XDM事件名稱 |
|---|---|
| 購物者以訂單傳回項目時觸發。 | `commerce.creditMemoIssued` |

#### 從orderRevayed收集的資料

下表說明為此事件收集的資料。
|欄位|說明| |—|—| |`identityMap`|包含識別客戶的電子郵件地址| |`address`|例如， `name@domain.com` 如RFC2822和後續標準中通常定義| |`eventType`|`commerce.creditMemoIssued`| |`productListItems`|按順序排列的產品陣列| |`order`|包含有關訂單的資訊| |`purchaseID`|賣方為此採購或合同分配的唯一標識符。 無法保證ID是唯一的| |`purchaseOrderNumber`|購買者為此購買或合同分配的唯一標識符|
+++
