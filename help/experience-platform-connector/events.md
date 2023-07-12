---
title: 事件
description: 瞭解每個事件會擷取哪些資料。
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
source-git-commit: 1484a465f3ce5b5578a7c5cf3f5f3b7d68d69c41
workflow-type: tm+mt
source-wordcount: '4605'
ht-degree: 0%

---

# Experience Platform聯結器事件

以下列出您在安裝Experience Platform聯結器擴充功能時可用的Commerce事件。 這些事件收集的資料會傳送至Adobe Experience Platform Edge。 您也可以建立 [自訂事件](custom-events.md) 以收集未立即提供的其他資料。

除了下列事件收集的資料外，您也會收到 [其他資料](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) 由Adobe Experience Platform Web SDK提供。

## 店面活動

店面活動會收集購物者瀏覽您網站時的匿名行為資料。 您可以使用這些事件收集到的資料，建立以特定購物者集為目標的促銷活動和行銷活動。 店面事件資料僅包含簡單且可設定的產品。

>[!NOTE]
>
>所有店面活動都包括 [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) 欄位，包含購物者的電子郵件地址（若有）和ECID。 將這個設定檔資料納入每個事件，您就不需要從Adobe Commerce匯入個別的使用者帳戶。

### addToCart

| 說明 | XDM事件名稱 |
|---|---|
| 當產品新增到購物車或購物車中的產品數量增加時觸發。 | `commerce.productListAdds` |

#### 從addToCart收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `productListAdds` | 表示是否已將產品新增至購物車。 值 `1` 表示已新增產品。 |
| `productListItems` | 加入購物車的一系列產品 |
| `SKU` | 庫存單位。 產品的唯一識別碼。 |
| `name` | 產品的顯示名稱或人類看得懂的名稱 |
| `priceTotal` | 產品明細專案的總價 |
| `quantity` | 加入購物車的產品單位數 |
| `discountAmount` | 表示已套用的折扣金額 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 產品的貨幣 |
| `productImageUrl` | 產品的主要影像URL |
| `selectedOptions` | 用於可設定產品的欄位。 `attribute` 會識別可設定產品的屬性，例如 `size` 或 `color` 和 `value` 會識別屬性的值，例如 `small` 或 `black`. |
| `cartID` | 識別客戶購物車的唯一ID |

### openCart

| 說明 | XDM事件名稱 |
|---|---|
| 建立新購物車時觸發，亦即當產品新增至空白購物車時觸發。 | `commerce.productListOpens` |

#### 從openCart收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `productListOpens` | 指出是否已建立購物車。 值 `1` 表示已建立購物車。 |
| `productListItems` | 加入購物車的一系列產品 |
| `SKU` | 庫存單位。 產品的唯一識別碼。 |
| `name` | 產品的顯示名稱或人類看得懂的名稱 |
| `priceTotal` | 產品明細專案的總價 |
| `quantity` | 加入購物車的產品單位數 |
| `discountAmount` | 表示已套用的折扣金額 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 產品的貨幣 |
| `productImageUrl` | 產品的主要影像URL |
| `selectedOptions` | 用於可設定產品的欄位。 `attribute` 會識別可設定產品的屬性，例如 `size` 或 `color` 和 `value` 會識別屬性的值，例如 `small` 或 `black`. |
| `cartID` | 識別客戶購物車的唯一ID |

### removeFromCart

| 說明 | XDM事件名稱 |
|---|---|
| 每次移除產品或購物車中的產品數量減少時觸發。 | `commerce.productListRemovals` |

#### 從removeFromCart收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `productListRemovals` | 表示產品是否已從購物車中移除。 值 `1` 表示產品已從購物車中移除。 |
| `productListItems` | 從購物車移除的一系列產品 |
| `SKU` | 庫存單位。 產品的唯一識別碼。 |
| `name` | 產品的顯示名稱或人類看得懂的名稱 |
| `priceTotal` | 產品明細專案的總價 |
| `quantity` | 從購物車中移除的產品單位數 |
| `discountAmount` | 表示已套用的折扣金額 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 產品的貨幣 |
| `productImageUrl` | 產品的主要影像URL |
| `selectedOptions` | 用於可設定產品的欄位。 `attribute` 會識別可設定產品的屬性，例如 `size` 或 `color` 和 `value` 會識別屬性的值，例如 `small` 或 `black`. |
| `cartID` | 識別客戶購物車的唯一ID |

### shoppingCartView

| 說明 | XDM事件名稱 |
|---|---|
| 任何購物車頁面載入時觸發。 | `commerce.productListViews` |

#### 從shoppingCartView收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `productListViews` | 顯示是否檢視過產品清單 |
| `productListItems` | 購物車中的一系列產品 |
| `SKU` | 庫存單位。 產品的唯一識別碼。 |
| `name` | 產品的顯示名稱或人類看得懂的名稱 |
| `priceTotal` | 產品明細專案的總價 |
| `quantity` | 購物車中的產品單位數 |
| `discountAmount` | 表示已套用的折扣金額 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 產品的貨幣 |
| `productImageUrl` | 產品的主要影像URL |
| `selectedOptions` | 用於可設定產品的欄位。 `attribute` 會識別可設定產品的屬性，例如 `size` 或 `color` 和 `value` 會識別屬性的值，例如 `small` 或 `black`. |
| `cartID` | 識別客戶購物車的唯一ID |

### pageView

| 說明 | XDM事件名稱 |
|---|---|
| 任何頁面載入時觸發。 | `web.webpagedetails.pageViews` |

#### 從pageView收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `pageViews` | 指出頁面是否已載入。 A `value` 之 `1` 表示頁面已載入。 |

### productPageView

| 說明 | XDM事件名稱 |
|---|---|
| 任何產品頁面載入時觸發。 | `commerce.productViews` |

#### 從productPageView收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `productViews` | 顯示是否檢視過產品 |
| `productListItems` | 購物車中的一系列產品 |
| `SKU` | 庫存單位。 產品的唯一識別碼。 |
| `name` | 產品的顯示名稱或人類看得懂的名稱 |
| `priceTotal` | 產品明細專案的總價 |
| `discountAmount` | 表示已套用的折扣金額 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 產品的貨幣 |
| `productImageUrl` | 產品的主要影像URL |
| `selectedOptions` | 用於可設定產品的欄位。 `attribute` 會識別可設定產品的屬性，例如 `size` 或 `color` 和 `value` 會識別屬性的值，例如 `small` 或 `black`. |

### startCheckout

| 說明 | XDM事件名稱 |
|---|---|
| 購物者按一下結帳按鈕時觸發。 | `commerce.checkouts` |

#### 從startCheckout收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `checkouts` | 表示在結帳過程中是否發生動作 |
| `productListItems` | 購物車中的一系列產品 |
| `SKU` | 庫存單位。 產品的唯一識別碼。 |
| `name` | 產品的顯示名稱或人類看得懂的名稱 |
| `priceTotal` | 產品明細專案的總價 |
| `quantity` | 購物車中的產品單位數 |
| `discountAmount` | 表示已套用的折扣金額 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 產品的貨幣 |
| `productImageUrl` | 產品的主要影像URL |
| `selectedOptions` | 用於可設定產品的欄位。 `attribute` 會識別可設定產品的屬性，例如 `size` 或 `color` 和 `value` 會識別屬性的值，例如 `small` 或 `black`. |
| `cartID` | 識別客戶購物車的唯一ID |

### completeCheckout

| 說明 | XDM事件名稱 |
|---|---|
| 購物者下訂單時觸發。 | `commerce.order` |

#### 從completeCheckout收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `purchases` | 表示是否已接受訂單 |
| `order` | 包含一或多個產品已下訂單的相關資訊 |
| `purchaseID` | 賣家為此購買或合約所指派的唯一識別碼。 無法保證ID是唯一的。 |
| `orderType` | 指示已下訂單的型別，例如「結帳」或「立即購買」 |
| `payments` | 此訂單的付款清單 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 用於此付款專案的幣別代碼。 例如， `USD` 或 `EUR`. |
| `paymentAmount` | 付款值 |
| `paymentType` | 此訂單的付款方式。 選項包括： `cash`， `credit_card`， `debit_card`， `gift_card`， `check`， `paypal`， `wire_transfer`， `credit_card_reference`， `other` |
| `transactionID` | 此付款專案的唯一交易識別碼 |
| `shipping` | 一或多個產品的送貨詳細資料。 |
| `shippingMethod` | 客戶選擇的配送方式，例如標準配送、加急配送、到店取貨等 |
| `shippingAmount` | 購物車中專案的總送貨成本 |
| `promotionID` | 促銷的唯一識別碼（若有） |
| `personalEmail` | 指定個人電子郵件地址 |
| `address` | 技術地址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義 |
| `productListItems` | 購物車中的一系列產品 |
| `SKU` | 庫存單位。 產品的唯一識別碼。 |
| `name` | 產品的顯示名稱或人類看得懂的名稱 |
| `priceTotal` | 產品明細專案的總價 |
| `quantity` | 購物車中的產品單位數 |
| `discountAmount` | 表示已套用的折扣金額 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 用於訂單總計的貨幣代碼。 |
| `productImageUrl` | 產品的主要影像URL |
| `selectedOptions` | 用於可設定產品的欄位。 `attribute` 會識別可設定產品的屬性，例如 `size` 或 `color` 和 `value` 會識別屬性的值，例如 `small` 或 `black`. |

## 設定檔事件

設定檔事件包含帳戶資訊，例如 `signIn`， `signOut`， `createAccount`、和 `editAccount`. 此資料用於協助填入重要客戶詳細資訊，這些詳細資訊是更好定義區段或執行行銷活動所需的資訊，例如，如果您想要鎖定居住在紐約的購物者。

### 登入

| 說明 | XDM事件名稱 |
|---|---|
| 購物者嘗試登入時觸發。 | `userAccount.login` |

>[!NOTE]
>
> 嘗試特定動作時會觸發此事件。 這並不表示動作成功。

#### 從登入收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `person` | 個別執行者、連絡人或擁有者 |
| `accountID` | 擷取使用者帳戶ID |
| `accountType` | 擷取使用者帳戶型別，例如 `Personal` 或 `Company`，如適用 |
| `personalEmailID` | 技術地址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義 |
| `personalEmail` | 擷取連絡人詳細資料 — 電子郵件和相關資訊 |
| `address` | 技術地址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義 |
| `userAccount` | 表示任何忠誠度詳細資料、偏好設定、登入程式和其他帳戶偏好設定 |
| `login` | 顯示訪客是否嘗試登入 |

### 登出

| 說明 | XDM事件名稱 |
|---|---|
| 購物者嘗試登出時觸發。 | `userAccount.logout` |

>[!NOTE]
>
> 嘗試特定動作時會觸發此事件。 這並不表示動作成功。

#### 從登出收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `userAccount` | 表示任何忠誠度詳細資料、偏好設定、登入程式和其他帳戶偏好設定 |
| `logout` | 顯示訪客是否嘗試登出 |

### createAccount

| 說明 | XDM事件名稱 |
|---|---|
| 購物者嘗試建立帳戶時觸發。 | `userAccount.createProfile` |

>[!NOTE]
>
> 嘗試特定動作時會觸發此事件。 這並不表示動作成功。

#### 從createAccount收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `person` | 個別執行者、連絡人或擁有者 |
| `accountID` | 擷取使用者帳戶ID |
| `accountType` | 擷取使用者帳戶型別，例如 `Personal` 或 `Company`，如適用 |
| `personalEmailID` | 技術地址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義 |
| `personalEmail` | 擷取連絡人詳細資料 — 電子郵件和相關資訊 |
| `address` | 技術地址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義 |
| `userAccount` | 表示任何忠誠度詳細資料、偏好設定、登入程式和其他帳戶偏好設定 |
| `createProfile` | 顯示使用者是否已建立帳戶設定檔 |

### editAccount

| 說明 | XDM事件名稱 |
|---|---|
| 購物者嘗試編輯帳戶時觸發。 | `userAccount.updateProfile` |

>[!NOTE]
>
> 嘗試特定動作時會觸發此事件。 這並不表示動作成功。

#### 從editAccount收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `person` | 個別執行者、連絡人或擁有者 |
| `accountID` | 擷取使用者帳戶ID |
| `accountType` | 擷取使用者帳戶型別，例如 `Personal` 或 `Company`，如適用 |
| `personalEmailID` | 技術地址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義 |
| `personalEmail` | 擷取連絡人詳細資料 — 電子郵件和相關資訊 |
| `address` | 技術地址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義 |
| `userAccount` | 表示任何忠誠度詳細資料、偏好設定、登入程式和其他帳戶偏好設定 |
| `updateProfile` | 顯示使用者是否已更新其帳戶設定檔 |

## 搜尋事件

搜尋事件會提供與購物者意圖相關的資料。 深入瞭解購物者的意圖，有助於商戶瞭解購物者如何搜尋商品、點選什麼，以及最終購買或放棄。 如何使用此資料的範例是，如果您想要鎖定搜尋您最暢銷產品但從未購買產品的現有購物者。

使用 `uniqueIdentifier` 在下列兩個欄位中找到： `searchRequestSent` 和 `searchResponseReceived` 將搜尋要求交叉參照至對應搜尋回應的事件。

### searchRequestSent

| 說明 | XDM事件名稱 |
|---|---|
| 由「依輸入搜尋」彈出視窗中的下列事件觸發：<br><br>按Enter，按一下 _檢視全部_<br><br>&#x200B;由搜尋結果頁面上的下列事件觸發：<br><br>選取篩選器，變更排序順序(_排序方式_)、變更排序方向（遞增或遞減）、變更每頁結果數(_每頁顯示#_)、導覽至下一頁、導覽至上一頁、導覽至其他頁面 | `searchRequest` |

>[!NOTE]
>
>已安裝B2B擴充功能的Adobe Commerce Enterprise Edition不支援搜尋事件。

#### 從searchRequestSent收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `searchRequest` | 顯示是否已傳送搜尋要求 |
| `id` | 此特定搜尋請求的唯一ID |
| `filter` | 顯示是否套用任何篩選器來限制搜尋結果 |
| `attribute` （篩選） | 用於確定是否將其包含在搜尋結果中的專案面向 |
| `value` | 用於確定搜尋結果中包含哪些專案的屬性值 |
| `isRange` | 為true時，值表示可接受值範圍的端點 |
| `sort` | 指出搜尋結果的排序方式 |
| `attribute` （排序） | 用於對搜尋結果中的專案進行排序的屬性 |
| `order` | 傳回搜尋結果的順序 |
| `query` | 搜尋的字詞 |

### searchResponseReceived

| 說明 | XDM事件名稱 |
|---|---|
| 當「即時搜尋」傳回「輸入時搜尋」彈出視窗或搜尋結果頁面結果時觸發。 | `searchResponse` |

>[!NOTE]
>
>已安裝B2B擴充功能的Adobe Commerce Enterprise Edition不支援搜尋事件。

#### 從searchResponseReceived收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `searchResponse` | 表示是否已收到搜尋回應 |
| `id` | 此特定搜尋回應的唯一ID |
| `suggestions` | 字串陣列，其中包含存在於目錄中且與搜尋查詢類似的產品和類別名稱 |
| `numberOfResults` | 傳回的產品數 |
| `productListItems` | 購物車中的一系列產品。 |
| `SKU` | 庫存單位。 產品的唯一識別碼。 |
| `name` | 產品的顯示名稱或人類看得懂的名稱 |
| `productImageUrl` | 產品的主要影像URL |

## B2B事件

![Adobe Commerce的B2B](../assets/b2b.svg) 針對B2B商家，您必須 [安裝](install.md#install-the-b2b-extension) 此 `experience-platform-connector-b2b` 擴充功能以啟用這些事件。

B2B事件包含 [請購單清單](https://experienceleague.adobe.com/docs/commerce-admin/b2b/requisition-lists/requisition-lists.html) 資訊，例如，是否建立、新增或從中刪除請購單清單。 透過追蹤請購單清單的特定事件，您可以檢視客戶經常購買哪些產品，並根據該資料建立行銷活動。

### createRequisitionList

| 說明 | XDM事件名稱 |
|---|---|
| 當購物者建立新的請購單清單時觸發。 | `commerce.requisitionListOpens` |

#### 從createRequisitionList收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `requisitionList` | 客戶建立的請購單屬性 |
| `ID` | 請購單清單的唯一識別碼 |
| `name` | 客戶指定的請購單清單名稱 |
| `description` | 客戶指定的請購單清單摘要 |

### addToRequisitionList

| 說明 | XDM事件名稱 |
|---|---|
| 購物者將產品新增至現有請購單清單或建立新清單時觸發。 | `commerce.requisitionListAdds` |

>[!NOTE]
>
>`addToRequisitionList` 類別檢視頁面或可設定產品不支援。 產品檢視頁面和簡單產品都支援此功能。

#### 從addToRequisitionList收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `requisitionList` | 客戶建立的請購單屬性 |
| `ID` | 請購單清單的唯一識別碼 |
| `name` | 客戶指定的請購單清單名稱 |
| `description` | 客戶指定的請購單清單摘要 |
| `productListItems` | 已新增至請購單清單的產品陣列 |
| `name` | 產品的顯示名稱或人類看得懂的名稱 |
| `SKU` | 庫存單位。 產品的唯一識別碼。 |
| `quantity` | 新增的產品單位數 |
| `priceTotal` | 產品明細專案的總價 |
| `discountAmount` | 表示已套用的折扣金額 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 用於此付款專案的幣別代碼 |
| `selectedOptions` | 用於可設定產品的欄位。 `attribute` 會識別可設定產品的屬性，例如 `size` 或 `color` 和 `value` 會識別屬性的值，例如 `small` 或 `black`. |

### removeFromRequisitionList

| 說明 | XDM事件名稱 |
|---|---|
| 當購物者從請購單清單移除產品時觸發。 | `commerce.requisitionListRemovals` |

#### 從removeFromRequisitionList收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `requisitionList` | 客戶建立的請購單屬性 |
| `ID` | 請購單清單的唯一識別碼 |
| `name` | 客戶指定的請購單清單名稱 |
| `description` | 客戶指定的請購單清單摘要 |
| `productListItems` | 已新增至請購單清單的產品陣列 |
| `name` | 產品的顯示名稱或人類看得懂的名稱 |
| `SKU` | 庫存單位。 產品的唯一識別碼。 |
| `quantity` | 新增的產品單位數 |
| `priceTotal` | 產品明細專案的總價 |
| `discountAmount` | 表示已套用的折扣金額 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 用於此付款專案的幣別代碼 |
| `selectedOptions` | 用於可設定產品的欄位。 `attribute` 會識別可設定產品的屬性，例如 `size` 或 `color` 和 `value` 會識別屬性的值，例如 `small` 或 `black`. |

## 後台活動

後台事件包含有關訂單狀態的資訊，例如訂單是否已下達、取消、退款、已出貨或完成。 這些伺服器端事件收集的資料會顯示購物者訂單的360度檢視。 此檢視可協助商家在開發行銷活動時，更妥善地鎖定目標或分析整個訂單狀態。 例如，您可以在一年中不同時間表現良好的特定產品類別中找出趨勢。 例如，在較冷的月份銷售較佳的冬季服裝，或多年來消費者感興趣的某些產品顏色。 此外，訂單狀態資料可協助您瞭解購物者根據先前訂單的轉換傾向，進而計算期限客戶值。

>[!NOTE]
>
>所有後台活動都包括 [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) 欄位，提供購物者的電子郵件地址。 將這個設定檔資料納入每個事件，您就不需要從Adobe Commerce匯入個別的使用者帳戶。

### orderPlaced

| 說明 | XDM事件名稱 |
|---|---|
| 購物者下訂單時觸發。 | `commerce.backofficeOrderPlaced` |

#### 從orderPlaced收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `address` | 技術地址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義 |
| `productListItems` | 訂單中的一系列產品 |
| `id` | 此產品專案的明細專案識別碼。 產品本身可透過以下方式識別 `product` 欄位。 |
| `name` | 產品的顯示名稱或人類看得懂的名稱 |
| `SKU` | 庫存單位。 產品的唯一識別碼。 |
| `quantity` | 購物車中的產品單位數 |
| `priceTotal` | 產品明細專案的總價 |
| `discountAmount` | 表示已套用的折扣金額 |
| `order` | 包含訂單的相關資訊 |
| `purchaseID` | 賣家為此購買或合約所指派的唯一識別碼。 無法保證ID是唯一的 |
| `priceTotal` | 此訂單套用所有折扣和稅金後的總價 |
| `currencyCode` | 用於訂單總額的ISO 4217貨幣代碼 |
| `purchaseOrderNumber` | 購買者為此購買或合約所指派的唯一識別碼 |
| `payments` | 此訂單的付款清單 |
| `paymentType` | 此訂單的付款方式。 列舉，允許自訂值。 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 用於此付款專案的幣別代碼 |
| `paymentAmount` | 付款值 |
| `taxAmount` | 買方支付作為最終付款一部分的稅捐金額 |
| `createdDate` | 在商務系統中建立新訂單的時間和日期。 例如， `2022-10-15T20:20:39+00:00` |
| `shipping` | 一或多個產品的送貨詳細資料 |
| `shippingMethod` | 客戶選擇的配送方式，例如標準配送、加急配送、到店取貨等 |
| `shippingAmount` | 客戶必須支付的運費金額。 |
| `address` | 實際送貨地址 |
| `street1` | 主要街道層級資訊、公寓號碼、街道號碼和街道名稱 |
| `street2` | 街道層級資訊的其他欄位 |
| `city` | 城市名稱 |
| `state` | 狀態名稱。 此為自由格式的欄位。 |
| `postalCode` | 地點的郵遞區號。 郵遞區號並非適用於所有國家/地區。 在某些國家/地區，這僅包含部分郵遞區號。 |
| `country` | 政府管理地區的名稱。 除了 `xdm:countryCode`，這是自由格式的欄位，可以有任何語言的國家/地區名稱。 |
| `billingAddress` | 帳單郵寄地址 |
| `street1` | 主要街道層級資訊、公寓號碼、街道號碼和街道名稱 |
| `street2` | 街道層級資訊的其他欄位 |
| `city` | 城市名稱 |
| `state` | 狀態名稱。 此為自由格式的欄位。 |
| `postalCode` | 地點的郵遞區號。 郵遞區號並非適用於所有國家/地區。 在某些國家/地區，這僅包含部分郵遞區號。 |
| `country` | 政府管理地區的名稱。 除了 `xdm:countryCode`，這是自由格式的欄位，可以有任何語言的國家/地區名稱。 |
| `personalEmail` | 個人電子郵件地址 |
| `address` | 技術位址，例如，RFC2822和後續標準中通常定義的「name@domain.com」 |

### orderItemsShipped

| 說明 | XDM事件名稱 |
|---|---|
| 在訂單出貨時觸發。 | `commerce.backofficeOrderItemsShipped` |

#### 從orderItemsShipped收集的資料

下表說明為此事件收集的資料。
|欄位|說明| |—|—| |`address`|技術位址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義| |`productListItems`|訂單中的一系列產品| |`id`|此產品專案的明細專案識別碼。 產品本身可透過以下方式識別 `product` 欄位。| |`name`|產品的顯示名稱或人類看得懂的名稱| |`SKU`|庫存單位。 產品的唯一識別碼。| |`quantity`|購物車中的產品件數| |`priceTotal`|產品明細專案的總價| |`discountAmount`|指示已套用的折扣金額| |`order`|包含訂單的相關資訊| |`purchaseID`|賣家為此購買或合約所指派的唯一識別碼。 無法保證ID是唯一的| |`priceTotal`|此訂單套用所有折扣和稅金後的總價| |`currencyCode`|用於訂單總額的ISO 4217貨幣代碼| |`purchaseOrderNumber`|購買者為此購買或合約指派的唯一識別碼| |`payments`|此訂單的付款清單| |`paymentType`|此訂單的付款方式。 列舉，允許自訂值。| |`currencyCode`|此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 用於此付款專案的貨幣代碼| |`paymentAmount`|付款值| |`lastUpdatedDate`|在商務系統中上次更新特定訂單記錄的時間| |`shipping`|一或多個產品的送貨詳細資料| |`shippingMethod`|客戶選擇的送貨方式，例如標準配送、加速配送、到店取貨等| |`trackingNumber`|出貨承運人為訂單料號出貨提供的追蹤編號| |`trackingURL`|追蹤訂單專案運送狀態的URL| |`shipDate`|訂單中一或多個專案出貨的日期| |`address`|實際運送地址| |`street1`|主要街道層級資訊、公寓號碼、街道號碼和街道名稱| |`street2`|街道層級資訊的其他欄位| |`city`|城市名稱| |`state`|狀態名稱。 此為自由格式的欄位。| |`postalCode`|地點的郵遞區號。 郵遞區號並非適用於所有國家/地區。 在某些國家/地區，這僅包含部分郵遞區號。| |`country`|政府管理地區的名稱。 除了 `xdm:countryCode`，這是自由格式的欄位，可以有任何語言的國家/地區名稱。| |`shippingAmount`|客戶必須支付的運費金額。| |`billingAddress`|帳單郵寄地址| |`street1`|主要街道層級資訊、公寓號碼、街道號碼和街道名稱| |`street2`|街道層級資訊的其他欄位| |`city`|城市名稱| |`state`|狀態名稱。 此為自由格式的欄位。| |`postalCode`|地點的郵遞區號。 郵遞區號並非適用於所有國家/地區。 在某些國家/地區，這僅包含部分郵遞區號。| |`country`|政府管理地區的名稱。 除了 `xdm:countryCode`，這是自由格式的欄位，可以有任何語言的國家/地區名稱。| |`personalEmail`|個人電子郵件地址| |`address`|技術位址，例如，「name@domain.com」，通常定義於RFC2822和後續標準|

### orderCanceled

| 說明 | XDM事件名稱 |
|---|---|
| 購物者取消訂單時觸發。 | `commerce.backofficeOrderCancelled` |

#### 從orderCanceled收集的資料

下表說明為此事件收集的資料。
|欄位|說明| |—|—| |`address`|技術位址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義| |`productListItems`|訂單中的一系列產品| |`id`|此產品專案的明細專案識別碼。 產品本身可透過以下方式識別 `product` 欄位。| |`name`|產品的顯示名稱或人類看得懂的名稱| |`SKU`|庫存單位。 產品的唯一識別碼。| |`quantity`|購物車中的產品件數| |`priceTotal`|產品明細專案的總價| |`discountAmount`|指示已套用的折扣金額| |`order`|包含訂單的相關資訊| |`purchaseID`|賣家為此購買或合約所指派的唯一識別碼。 無法保證ID是唯一的| |`purchaseOrderNumber`|購買者為此購買或合約指派的唯一識別碼| |`cancelDate`|購物者取消訂單的日期和時間| |`lastUpdatedDate`|在商務系統中上次更新特定訂單記錄的時間| |`personalEmail`|個人電子郵件地址| |`address`|技術位址，例如，「name@domain.com」，通常定義於RFC2822和後續標準|

### creditMemoIssued

| 說明 | XDM事件名稱 |
|---|---|
| 購物者傳回訂單中的專案時觸發。 | `commerce.backofficeCreditMemoIssued` |

#### 從已核發的銷退折讓單收集的資料

下表說明為此事件收集的資料。
|欄位|說明| |—|—| |`address`|技術位址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義| |`productListItems`|訂單中的一系列產品| |`id`|此產品專案的明細專案識別碼。 產品本身可透過以下方式識別 `product` 欄位。| |`name`|產品的顯示名稱或人類看得懂的名稱| |`SKU`|庫存單位。 產品的唯一識別碼。| |`quantity`|購物車中的產品件數| |`priceTotal`|產品明細專案的總價| |`discountAmount`|指示已套用的折扣金額| |`order`|包含訂單的相關資訊| |`purchaseID`|賣家為此購買或合約所指派的唯一識別碼。 無法保證ID是唯一的| |`purchaseOrderNumber`|購買者為此購買或合約指派的唯一識別碼| |`lastUpdatedDate`|在商務系統中上次更新特定訂單記錄的時間| |`personalEmail`|個人電子郵件地址| |`address`|技術位址，例如，「name@domain.com」，通常定義於RFC2822和後續標準|

### orderShipmentCompleted

| 說明 | XDM事件名稱 |
|---|---|
| 購物者傳回訂單中的專案時觸發。 | `commerce.backofficeOrderShipmentCompleted` |

#### 從orderShipmentCompleted收集的資料

下表說明為此事件收集的資料。
|欄位|說明| |—|—| |`address`|技術位址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義| |`productListItems`|訂單中的一系列產品| |`id`|此產品專案的明細專案識別碼。 產品本身可透過以下方式識別 `product` 欄位。| |`name`|產品的顯示名稱或人類看得懂的名稱| |`SKU`|庫存單位。 產品的唯一識別碼。| |`quantity`|購物車中的產品件數| |`priceTotal`|產品明細專案的總價| |`discountAmount`|指示已套用的折扣金額| |`order`|包含訂單的相關資訊| |`purchaseID`|賣家為此購買或合約所指派的唯一識別碼。 無法保證ID是唯一的| |`priceTotal`|此訂單套用所有折扣和稅金後的總價| |`currencyCode`|用於訂單總額的ISO 4217貨幣代碼| |`purchaseOrderNumber`|購買者為此購買或合約指派的唯一識別碼| |`taxAmount`|買方支付作為最終付款一部分的稅捐金額。| |`createdDate`|在商務系統中建立新訂單的時間和日期。 例如， `2022-10-15T20:20:39+00:00`| |`payments`|此訂單的付款清單| |`paymentType`|此訂單的付款方式。 列舉，允許自訂值。| |`currencyCode`|此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 用於此付款專案的貨幣代碼| |`paymentAmount`|付款值| |`shipping`|一或多個產品的送貨詳細資料| |`shippingMethod`|客戶選擇的送貨方式，例如標準配送、加速配送、到店取貨等| |`address`|實際運送地址| |`street1`|主要街道層級資訊、公寓號碼、街道號碼和街道名稱| |`street2`|街道層級資訊的其他欄位| |`city`|城市名稱| |`state`|狀態名稱。 此為自由格式的欄位。| |`postalCode`|地點的郵遞區號。 郵遞區號並非適用於所有國家/地區。 在某些國家/地區，這僅包含部分郵遞區號。| |`country`|政府管理地區的名稱。 除了 `xdm:countryCode`，這是自由格式的欄位，可以有任何語言的國家/地區名稱。| |`shippingAmount`|客戶必須支付的運費金額。| |`address`|技術位址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義| |`billingAddress`|帳單郵寄地址| |`street1`|主要街道層級資訊、公寓號碼、街道號碼和街道名稱| |`street2`|街道層級資訊的其他欄位| |`city`|城市名稱| |`state`|狀態名稱。 此為自由格式的欄位。| |`postalCode`|地點的郵遞區號。 郵遞區號並非適用於所有國家/地區。 在某些國家/地區，此資料僅包含郵遞區號的一部分。| |`country`|政府管理地區的名稱。 除了 `xdm:countryCode`，這是自由格式的欄位，可以有任何語言的國家/地區名稱。| |`personalEmail`|個人電子郵件地址| |`address`|技術位址，例如，「name@domain.com」，通常定義於RFC2822和後續標準|
