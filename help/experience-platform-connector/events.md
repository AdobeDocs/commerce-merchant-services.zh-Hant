---
title: 活動
description: 瞭解每個事件擷取哪些資料。
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: 0be39c5d46289a12bc2cfa704e942dc594fbded2
workflow-type: tm+mt
source-wordcount: '6126'
ht-degree: 0%

---

# Experience Platform聯結器事件

下表列出您在安裝Commerce聯結器擴充功能時可用的Experience Platform事件。 這些事件收集的資料會傳送至Adobe Experience Platform Edge。 您也可以建立 [自訂事件](custom-events.md) 以立即收集未提供的其他資料。

除了下列事件收集的資料外，您也會收到 [其他資料](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) 由Adobe Experience Platform Web SDK提供。

## 店面活動

店面活動會在購物者瀏覽您的網站時，從他們那裡收集匿名的行為資料。 您可以使用這些事件收集到的資料，建立以特定購物者集為目標的促銷活動和行銷活動。 店面事件資料僅包含簡單且可設定的產品。

>[!NOTE]
>
>所有店面活動包括 [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) 欄位，其中包含購物者的電子郵件地址（若有）和ECID。 將這個設定檔資料包含在每個事件中，您就不需要從Adobe Commerce匯入個別的使用者帳戶。

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
| `quantity` | 加入購物車的產品件數 |
| `discountAmount` | 表示套用的折扣金額 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR` |
| `productImageUrl` | 產品的主要影像URL |
| `selectedOptions` | 用於可設定產品的欄位。 |
| `attribute` | 識別可設定產品的屬性，例如 `size` 或 `color` |
| `value` | 識別屬性值，例如 `small` 或 `black`. |
| `cartID` | 識別客戶購物車的唯一ID |
| `commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |

### openCart

| 說明 | XDM事件名稱 |
|---|---|
| 建立新購物車時觸發，亦即將產品新增至空白購物車時。 | `commerce.productListOpens` |

#### 從openCart收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `productListOpens` | 指出是否已建立購物車。 值 `1` 表示已建立購物車。 |
| `productListItems` | 加入購物車的一系列產品 |
| `SKU` | 庫存單位。 產品的唯一識別碼。 |
| `name` | 產品的顯示名稱或人類看得懂的名稱 |
| `priceTotal` | 產品明細專案的總價 |
| `quantity` | 加入購物車的產品件數 |
| `discountAmount` | 表示套用的折扣金額 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR` |
| `productImageUrl` | 產品的主要影像URL |
| `selectedOptions` | 用於可設定產品的欄位。 |
| `attribute` | 識別可設定產品的屬性，例如 `size` 或 `color` |
| `value` | 識別屬性值，例如 `small` 或 `black`. |
| `cartID` | 識別客戶購物車的唯一ID |
| `commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |

### removeFromCart

| 說明 | XDM事件名稱 |
|---|---|
| 每次移除產品或每次購物車中的產品數量減少時觸發。 | `commerce.productListRemovals` |

#### 從removeFromCart收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `productListRemovals` | 表示產品是否已從購物車移除。 值 `1` 表示產品已從購物車移除。 |
| `productListItems` | 從購物車移除的一系列產品 |
| `SKU` | 庫存單位。 產品的唯一識別碼。 |
| `name` | 產品的顯示名稱或人類看得懂的名稱 |
| `priceTotal` | 產品明細專案的總價 |
| `quantity` | 從購物車移除的產品單位數 |
| `discountAmount` | 表示套用的折扣金額 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR` |
| `productImageUrl` | 產品的主要影像URL |
| `selectedOptions` | 用於可設定產品的欄位。 |
| `attribute` | 識別可設定產品的屬性，例如 `size` 或 `color` |
| `value` | 識別屬性值，例如 `small` 或 `black`. |
| `cartID` | 識別客戶購物車的唯一ID |
| `commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |

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
| `quantity` | 購物車中的產品件數 |
| `discountAmount` | 表示套用的折扣金額 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR` |
| `productImageUrl` | 產品的主要影像URL |
| `selectedOptions` | 用於可設定產品的欄位。 |
| `attribute` | 識別可設定產品的屬性，例如 `size` 或 `color` |
| `value` | 識別屬性值，例如 `small` 或 `black`. |
| `cartID` | 識別客戶購物車的唯一ID |
| `commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |

### pageView

| 說明 | XDM事件名稱 |
|---|---|
| 任何頁面載入時觸發。 | `web.webpagedetails.pageViews` |

#### 從pageView收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `pageViews` | 指出是否已載入頁面。 A `value` 之 `1` 表示頁面已載入。 |
| `commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |

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
| `discountAmount` | 表示套用的折扣金額 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR` |
| `productImageUrl` | 產品的主要影像URL |
| `selectedOptions` | 用於可設定產品的欄位。 |
| `attribute` | 識別可設定產品的屬性，例如 `size` 或 `color` |
| `value` | 識別屬性值，例如 `small` 或 `black`. |
| `commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |

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
| `quantity` | 購物車中的產品件數 |
| `discountAmount` | 表示套用的折扣金額 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR` |
| `productImageUrl` | 產品的主要影像URL |
| `selectedOptions` | 用於可設定產品的欄位。 |
| `attribute` | 識別可設定產品的屬性，例如 `size` 或 `color` |
| `value` | 識別屬性值，例如 `small` 或 `black`. |
| `cartID` | 識別客戶購物車的唯一ID |
| `commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |

### completeCheckout

| 說明 | XDM事件名稱 |
|---|---|
| 購物者下訂單時觸發。 | `commerce.order` |

#### 從completeCheckout收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `purchases` | 顯示是否已接受訂單 |
| `order` | 包含一或多個產品已下訂單的相關資訊 |
| `purchaseID` | 賣家為此購買或合約所指派的唯一識別碼。 無法保證ID是唯一的。 |
| `orderType` | 表示所下訂單的型別，例如「結帳」或「立即購買」 |
| `payments` | 此訂單的付款清單 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR` |
| `paymentAmount` | 付款的值 |
| `paymentType` | 此訂單的付款方式。 選項包括： `cash`， `credit_card`， `debit_card`， `gift_card`， `check`， `paypal`， `wire_transfer`， `credit_card_reference`， `other` |
| `transactionID` | 此付款專案的唯一交易識別碼 |
| `shipping` | 一或多個產品的運送詳細資料。 |
| `shippingMethod` | 客戶選擇的配送方式，例如標準配送、加速配送、到店取貨等 |
| `shippingAmount` | 購物車中專案的總運送成本 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR` |
| `promotionID` | 促銷的唯一識別碼（如有） |
| `personalEmail` | 指定個人電子郵件地址 |
| `address` | 技術地址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義 |
| `productListItems` | 購物車中的一系列產品 |
| `SKU` | 庫存單位。 產品的唯一識別碼。 |
| `name` | 產品的顯示名稱或人類看得懂的名稱 |
| `priceTotal` | 產品明細專案的總價 |
| `quantity` | 購物車中的產品件數 |
| `discountAmount` | 表示套用的折扣金額 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR` |
| `productImageUrl` | 產品的主要影像URL |
| `selectedOptions` | 用於可設定產品的欄位。 |
| `attribute` | 識別可設定產品的屬性，例如 `size` 或 `color` |
| `value` | 識別屬性值，例如 `small` 或 `black`. |
| `commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |

## 設定檔事件

設定檔事件包含帳戶資訊，例如 `signIn`， `signOut`， `createAccount`、和 `editAccount`. 這些資料可用來協助填入重要客戶詳細資訊，以便更妥善地定義區段或執行行銷活動，例如如果您想要鎖定在紐約的購物者。

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
| `userAccount` | 表示任何熟客方案細節、偏好設定、登入流程和其他帳戶偏好設定 |
| `login` | 顯示訪客是否嘗試登入 |
| `commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |

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
| `userAccount` | 表示任何熟客方案細節、偏好設定、登入流程和其他帳戶偏好設定 |
| `logout` | 顯示訪客是否嘗試登出 |
| `commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |

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
| `userAccount` | 表示任何熟客方案細節、偏好設定、登入流程和其他帳戶偏好設定 |
| `createProfile` | 顯示使用者是否已建立帳戶設定檔 |
| `commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |

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
| `userAccount` | 表示任何熟客方案細節、偏好設定、登入流程和其他帳戶偏好設定 |
| `updateProfile` | 顯示使用者是否已更新其帳戶設定檔 |
| `commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |

## 搜尋事件

搜尋事件會提供與購物者意圖相關的資料。 深入瞭解購物者的意圖，有助於商戶瞭解購物者如何搜尋商品、點選內容，以及最終購買或放棄。 此資料如何使用的範例是，如果您想要鎖定搜尋您最熱門產品但從未購買產品的現有購物者。

使用 `uniqueIdentifier` 欄位中找到了 `searchRequestSent` 和 `searchResponseReceived` 將搜尋要求交叉參照至對應搜尋回應的事件。

### searchRequestSent

| 說明 | XDM事件名稱 |
|---|---|
| 在「輸入時搜尋」彈出視窗中的下列事件觸發：<br><br>按下Enter，按一下 _檢視全部_<br><br>&#x200B;由搜尋結果頁面上的下列事件觸發：<br><br>選取篩選器，變更排序順序(_排序方式_)、變更排序方向（遞增或遞減）、變更每頁結果數(_每頁顯示#_)，導覽至下一頁，導覽至上一頁，導覽至其他頁面 | `searchRequest` |

>[!NOTE]
>
>已安裝B2B擴充功能的Adobe Commerce Enterprise Edition不支援搜尋事件。

#### 從searchRequestSent收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `searchRequest` | 顯示是否已傳送搜尋要求 |
| `id` | 此特定搜尋請求的唯一ID |
| `filter` | 顯示是否套用任何篩選器以限制搜尋結果 |
| `attribute` （篩選） | 用於確定是否將其納入搜尋結果的專案面向 |
| `value` | 用於確定搜尋結果中包含哪些專案的屬性值 |
| `isRange` | 為true時，值表示可接受值範圍的端點 |
| `sort` | 指出搜尋結果的排序方式 |
| `attribute` （排序） | 用於對搜尋結果中的專案進行排序的屬性 |
| `order` | 傳回搜尋結果的順序 |
| `query` | 搜尋的字詞 |
| `commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |

### searchResponseReceived

| 說明 | XDM事件名稱 |
|---|---|
| 當「即時搜尋」傳回「鍵入時搜尋」彈出視窗或搜尋結果頁面結果時觸發。 | `searchResponse` |

>[!NOTE]
>
>已安裝B2B擴充功能的Adobe Commerce Enterprise Edition不支援搜尋事件。

#### 從searchResponseReceived收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `searchResponse` | 顯示是否已收到搜尋回應 |
| `id` | 此特定搜尋回應的唯一ID |
| `suggestions` | 字串陣列，其中包含存在於目錄中且與搜尋查詢類似的產品和類別名稱 |
| `numberOfResults` | 傳回的產品數 |
| `productListItems` | 購物車中的一系列產品。 |
| `SKU` | 庫存單位。 產品的唯一識別碼。 |
| `name` | 產品的顯示名稱或人類看得懂的名稱 |
| `productImageUrl` | 產品的主要影像URL |
| `commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |

## B2B事件

![適用於Adobe Commerce的B2B](../assets/b2b.svg) 針對B2B商家，您必須 [安裝](install.md#install-the-b2b-extension) 此 `experience-platform-connector-b2b` 擴充功能以啟用這些事件。

B2B事件包含 [請購單清單](https://experienceleague.adobe.com/docs/commerce-admin/b2b/requisition-lists/requisition-lists.html) 資訊，例如，是否已建立、新增或從中刪除請購單清單。 透過追蹤請購單清單的特定事件，您可以檢視客戶經常購買哪些產品，並根據該資料建立行銷活動。

### createRequisitionList

| 說明 | XDM事件名稱 |
|---|---|
| 當購物者建立新的請購單清單時觸發。 | `commerce.requisitionListOpens` |

#### 從createRequisitionList收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `requisitionList` | 客戶建立的請購單清單屬性 |
| `ID` | 請購單清單的唯一識別碼 |
| `name` | 客戶指定的請購單清單名稱 |
| `description` | 客戶指定的請購單清單摘要 |
| `commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |

### addToRequisitionList

| 說明 | XDM事件名稱 |
|---|---|
| 購物者將產品新增至現有請購單清單或建立新清單時觸發。 | `commerce.requisitionListAdds` |

>[!NOTE]
>
>`addToRequisitionList` 類別檢視頁面或可設定的產品不支援。 產品檢視頁面和簡單產品都支援此功能。

#### 從addToRequisitionList收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `requisitionList` | 客戶建立的請購單清單屬性 |
| `ID` | 請購單清單的唯一識別碼 |
| `name` | 客戶指定的請購單清單名稱 |
| `description` | 客戶指定的請購單清單摘要 |
| `productListItems` | 已新增至請購單清單的產品陣列 |
| `name` | 產品的顯示名稱或人類看得懂的名稱 |
| `SKU` | 庫存單位。 產品的唯一識別碼。 |
| `quantity` | 新增的產品單位數 |
| `priceTotal` | 產品明細專案的總價 |
| `discountAmount` | 表示套用的折扣金額 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR` |
| `selectedOptions` | 用於可設定產品的欄位。 |
| `attribute` | 識別可設定產品的屬性，例如 `size` 或 `color` |
| `value` | 識別屬性值，例如 `small` 或 `black`. |
| `commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |

### removeFromRequisitionList

| 說明 | XDM事件名稱 |
|---|---|
| 當購物者從請購單清單移除產品時觸發。 | `commerce.requisitionListRemovals` |

#### 從removeFromRequisitionList收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `requisitionList` | 客戶建立的請購單清單屬性 |
| `ID` | 請購單清單的唯一識別碼 |
| `name` | 客戶指定的請購單清單名稱 |
| `description` | 客戶指定的請購單清單摘要 |
| `productListItems` | 已新增至請購單清單的產品陣列 |
| `name` | 產品的顯示名稱或人類看得懂的名稱 |
| `SKU` | 庫存單位。 產品的唯一識別碼。 |
| `quantity` | 新增的產品單位數 |
| `priceTotal` | 產品明細專案的總價 |
| `discountAmount` | 表示套用的折扣金額 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR` |
| `selectedOptions` | 用於可設定產品的欄位。 |
| `attribute` | 識別可設定產品的屬性，例如 `size` 或 `color` |
| `value` | 識別屬性值，例如 `small` 或 `black`. |
| `commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |

## 後台活動

後台事件包含有關訂單狀態的資訊，例如訂單是否已下達、取消、退款、已出貨或完成。 這些伺服器端事件收集的資料會顯示購物者訂單的360度檢視。 此檢視可協助商家在開發行銷活動時，更妥善地鎖定目標或分析整個訂單狀態。 例如，您可以找出某些產品類別中在一年中不同時間表現良好的趨勢。 例如，在較冷的月份銷售較佳的冬季服飾，或購物者多年來感興趣的特定產品顏色。 此外，訂單狀態資料可協助您瞭解購物者根據先前訂單轉換的傾向，進而計算期限客戶值。

>[!NOTE]
>
>所有後台活動包括 [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) 欄位，提供購物者的電子郵件地址。 將這個設定檔資料包含在每個事件中，您就不需要從Adobe Commerce匯入個別的使用者帳戶。

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
| `id` | 此產品條目的明細專案識別碼。 產品本身可透過 `product` 欄位。 |
| `name` | 產品的顯示名稱或人類看得懂的名稱 |
| `SKU` | 庫存單位。 產品的唯一識別碼。 |
| `quantity` | 購物車中的產品件數 |
| `priceTotal` | 產品明細專案的總價 |
| `discountAmount` | 表示套用至料號的折扣金額 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR` |
| `productImageUrl` | 產品的主要影像URL |
| `selectedOptions` | 用於可設定產品的欄位。 |
| `attribute` | 識別可設定產品的屬性，例如 `size` 或 `color` |
| `value` | 識別屬性值，例如 `small` 或 `black`. |
| `commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |
| `order` | 包含訂單的相關資訊 |
| `purchaseID` | 賣家為此購買或合約所指派的唯一識別碼。 不保證ID為唯一 |
| `priceTotal` | 此訂單套用所有折扣和稅金後的總價 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR` |
| `purchaseOrderNumber` | 購買者為此購買或合約所指派的唯一識別碼 |
| `payments` | 此訂單的付款清單 |
| `paymentType` | 此訂單的付款方式。 列舉，允許自訂值。 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR` |
| `paymentAmount` | 付款的值 |
| `taxAmount` | 買方作為最終付款的一部分所支付的稅捐金額 |
| `discountAmount` | 表示套用至整張訂單的折扣金額 |
| `createdDate` | 在商務系統中建立新訂單的時間和日期。 例如， `2022-10-15T20:20:39+00:00` |
| `shipping` | 一或多個產品的運送詳細資料 |
| `shippingMethod` | 客戶選擇的配送方式，例如標準配送、加速配送、到店取貨等 |
| `shippingAmount` | 客戶必須為運費支付的金額。 |
| `currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR` |
| `address` | 實際送貨地址 |
| `street1` | 主要街道層級資訊、公寓號碼、街道號碼和街道名稱 |
| `street2` | 街道層級資訊的其他欄位 |
| `city` | 城市名稱 |
| `state` | 狀態的名稱。 此為自由格式的欄位。 |
| `postalCode` | 地點的郵遞區號。 郵遞區號並非適用於所有國家/地區。 在某些國家/地區，這僅包含郵遞區號的一部分。 |
| `country` | 政府管理的領土的名稱。 除了 `xdm:countryCode`，此為自由格式的欄位，可能有任何語言的國家/地區名稱。 |
| `billingAddress` | 帳單郵寄地址 |
| `street1` | 主要街道層級資訊、公寓號碼、街道號碼和街道名稱 |
| `street2` | 街道層級資訊的其他欄位 |
| `city` | 城市名稱 |
| `state` | 狀態的名稱。 此為自由格式的欄位。 |
| `postalCode` | 地點的郵遞區號。 郵遞區號並非適用於所有國家/地區。 在某些國家/地區，這僅包含郵遞區號的一部分。 |
| `country` | 政府管理的領土的名稱。 除了 `xdm:countryCode`，此為自由格式的欄位，可能有任何語言的國家/地區名稱。 |
| `personalEmail` | 個人電子郵件地址 |
| `address` | 技術地址，例如，RFC2822和後續標準中通常定義的「name@domain.com」 |

### orderItemsShipped

| 說明 | XDM事件名稱 |
|---|---|
| 在訂單出貨時觸發。 | `commerce.backofficeOrderItemsShipped` |

#### 從orderItemsShipped收集的資料

下表說明為此事件收集的資料。
|欄位|說明| |—|—| |`address`|技術地址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義| |`productListItems`|訂單中的一系列產品| |`id`|此產品專案的條列專案識別碼。 產品本身可透過 `product` 欄位。| |`name`|產品的顯示名稱或人類看得懂的名稱| |`SKU`|庫存單位。 產品的唯一識別碼。| |`quantity`|購物車中的產品件數| |`priceTotal`|產品條列專案的總價| |`discountAmount`|表示套用的折扣金額| |`currencyCode`|此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR`| |`productImageUrl`|產品的主要影像URL| |`selectedOptions`|用於可設定產品的欄位。| |`attribute`|識別可設定產品的屬性，例如 `size` 或 `color`| |`value`|識別屬性值，例如 `small` 或 `black`.| |`commerceScope`|指出發生事件的位置（商店檢視、商店、網站等）。| |`environmentID`|環境ID。 32位數的英數字元ID，以連字型大小分隔。| |`storeCode`|唯一的商店代碼。 每個網站可以有許多商店。| |`storeViewCode`|唯一的商店檢視代碼。 每個商店可以有多個商店檢視。| |`websiteCode`|唯一的網站代碼。 一個環境中可以有許多網站。| |`order`|包含訂單的相關資訊| |`purchaseID`|賣家為此購買或合約所指派的唯一識別碼。 不保證此ID為唯一| |`priceTotal`|此訂單套用所有折扣和稅金後的總價| |`currencyCode`|此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR`| |`purchaseOrderNumber`|購買者為此購買或合約所指派的唯一識別碼| |`payments`|此訂單的付款清單| |`paymentType`|此訂單的付款方式。 列舉，允許自訂值。| |`currencyCode`|此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR`| |`paymentAmount`|付款金額| |`lastUpdatedDate`|在商務系統中上次更新特定訂單記錄的時間| |`shipping`|一或多個產品的運送詳細資料| |`shippingMethod`|客戶選擇的配送方式，例如標準配送、加速配送、到店取貨等| |`currencyCode`|此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR`| |`trackingNumber`|出貨承運商針對訂單料號出貨提供的追蹤編號| |`trackingURL`|追蹤訂單專案出貨狀態的URL| |`shipDate`|訂單中一或多個料號出貨的日期| |`address`|實際送貨地址| |`street1`|主要街道層級資訊、公寓號碼、街道號碼和街道名稱| |`street2`|街道層級資訊的其他欄位| |`city`|城市名稱| |`state`|狀態名稱。 此為自由格式的欄位。| |`postalCode`|地點的郵遞區號。 郵遞區號並非適用於所有國家/地區。 在某些國家/地區，這僅包含郵遞區號的一部分。| |`country`|政府管理的領土名稱。 除了 `xdm:countryCode`，此為自由格式的欄位，可能有任何語言的國家/地區名稱。| |`shippingAmount`|客戶必須支付的運費。| |`currencyCode`|此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR`| |`billingAddress`|帳單郵寄地址| |`street1`|主要街道層級資訊、公寓號碼、街道號碼和街道名稱| |`street2`|街道層級資訊的其他欄位| |`city`|城市名稱| |`state`|狀態名稱。 此為自由格式的欄位。| |`postalCode`|地點的郵遞區號。 郵遞區號並非適用於所有國家/地區。 在某些國家/地區，這僅包含郵遞區號的一部分。| |`country`|政府管理的領土名稱。 除了 `xdm:countryCode`，此為自由格式的欄位，可能有任何語言的國家/地區名稱。| |`personalEmail`|個人電子郵件地址| |`address`|技術位址，例如，「name@domain.com」，通常定義於RFC2822和後續標準|

### orderCanceled

| 說明 | XDM事件名稱 |
|---|---|
| 購物者取消訂單時觸發。 | `commerce.backofficeOrderCancelled` |

#### 從orderCanceled收集的資料

下表說明為此事件收集的資料。
|欄位|說明| |—|—| |`address`|技術地址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義| |`productListItems`|訂單中的一系列產品| |`id`|此產品專案的條列專案識別碼。 產品本身可透過 `product` 欄位。| |`name`|產品的顯示名稱或人類看得懂的名稱| |`SKU`|庫存單位。 產品的唯一識別碼。| |`quantity`|購物車中的產品件數| |`priceTotal`|產品條列專案的總價| |`discountAmount`|表示套用的折扣金額| |`currencyCode`|此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR`| |`productImageUrl`|產品的主要影像URL| |`selectedOptions`|用於可設定產品的欄位。| |`attribute`|識別可設定產品的屬性，例如 `size` 或 `color`| |`value`|識別屬性值，例如 `small` 或 `black`.| |`commerceScope`|指出發生事件的位置（商店檢視、商店、網站等）。| |`environmentID`|環境ID。 32位數的英數字元ID，以連字型大小分隔。| |`storeCode`|唯一的商店代碼。 每個網站可以有許多商店。| |`storeViewCode`|唯一的商店檢視代碼。 每個商店可以有多個商店檢視。| |`websiteCode`|唯一的網站代碼。 一個環境中可以有許多網站。| |`order`|包含訂單的相關資訊| |`purchaseID`|賣家為此購買或合約所指派的唯一識別碼。 不保證此ID為唯一| |`purchaseOrderNumber`|購買者為此購買或合約所指派的唯一識別碼| |`cancelDate`|購物者取消訂單的日期和時間| |`lastUpdatedDate`|在商務系統中上次更新特定訂單記錄的時間| |`personalEmail`|個人電子郵件地址| |`address`|技術位址，例如，「name@domain.com」，通常定義於RFC2822和後續標準|

### creditMemoIssued

| 說明 | XDM事件名稱 |
|---|---|
| 當購物者傳回訂單中的專案時觸發。 | `commerce.backofficeCreditMemoIssued` |

#### 從已核發銷退折讓單收集的資料

下表說明為此事件收集的資料。
|欄位|說明| |—|—| |`address`|技術地址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義| |`productListItems`|訂單中的一系列產品| |`id`|此產品專案的條列專案識別碼。 產品本身可透過 `product` 欄位。| |`name`|產品的顯示名稱或人類看得懂的名稱| |`SKU`|庫存單位。 產品的唯一識別碼。| |`quantity`|購物車中的產品件數| |`priceTotal`|產品條列專案的總價| |`discountAmount`|表示套用的折扣金額| |`currencyCode`|此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR`| |`productImageUrl`|產品的主要影像URL| |`selectedOptions`|用於可設定產品的欄位。| |`attribute`|識別可設定產品的屬性，例如 `size` 或 `color`| |`value`|識別屬性值，例如 `small` 或 `black`.| |`order`|包含訂單的相關資訊| |`purchaseID`|賣家為此購買或合約所指派的唯一識別碼。 不保證此ID為唯一| |`purchaseOrderNumber`|購買者為此購買或合約所指派的唯一識別碼| |`lastUpdatedDate`|在商務系統中上次更新特定訂單記錄的時間| |`priceTotal`|產品條列專案的總價| |`discountAmount`|表示套用的折扣金額| |`currencyCode`|此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR`| |`taxAmount`|購買者支付作為最終付款一部分的稅捐金額。| |`refunds`|此訂單的退款清單| |`refundPaymentType`|此訂單的付款方式。 列舉，允許自訂值。| |`refundAmount`|退款金額。| |`currencyCode`|此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR`| |`personalEmail`|個人電子郵件地址| |`address`|技術地址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義|

### orderShipmentCompleted

| 說明 | XDM事件名稱 |
|---|---|
| 當購物者傳回訂單中的專案時觸發。 | `commerce.backofficeOrderShipmentCompleted` |

#### 從orderShipmentCompleted收集的資料

下表說明為此事件收集的資料。
|欄位|說明| |—|—| |`address`|技術地址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義| |`productListItems`|訂單中的一系列產品| |`id`|此產品專案的條列專案識別碼。 產品本身可透過 `product` 欄位。| |`name`|產品的顯示名稱或人類看得懂的名稱| |`SKU`|庫存單位。 產品的唯一識別碼。| |`quantity`|購物車中的產品件數| |`priceTotal`|產品條列專案的總價| |`discountAmount`|表示套用的折扣金額| |`currencyCode`|此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR`| |`productImageUrl`|產品的主要影像URL| |`selectedOptions`|用於可設定產品的欄位。| |`attribute`|識別可設定產品的屬性，例如 `size` 或 `color`| |`value`|識別屬性值，例如 `small` 或 `black`.| |`order`|包含訂單的相關資訊| |`purchaseID`|賣家為此購買或合約所指派的唯一識別碼。 不保證此ID為唯一| |`priceTotal`|此訂單套用所有折扣和稅金後的總價| |`currencyCode`|此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR`| |`purchaseOrderNumber`|購買者為此購買或合約所指派的唯一識別碼| |`taxAmount`|購買者支付作為最終付款一部分的稅捐金額。| |`createdDate`|在商務系統中建立新訂單的時間和日期。 例如， `2022-10-15T20:20:39+00:00`| |`payments`|此訂單的付款清單| |`paymentType`|此訂單的付款方式。 列舉，允許自訂值。| |`currencyCode`|此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR`| |`paymentAmount`|付款金額| |`shipping`|一或多個產品的運送詳細資料| |`shippingMethod`|客戶選擇的配送方式，例如標準配送、加速配送、到店取貨等| |`address`|實際送貨地址| |`street1`|主要街道層級資訊、公寓號碼、街道號碼和街道名稱| |`street2`|街道層級資訊的其他欄位| |`city`|城市名稱| |`state`|狀態名稱。 此為自由格式的欄位。| |`postalCode`|地點的郵遞區號。 郵遞區號並非適用於所有國家/地區。 在某些國家/地區，這僅包含郵遞區號的一部分。| |`country`|政府管理的領土名稱。 除了 `xdm:countryCode`，此為自由格式的欄位，可能有任何語言的國家/地區名稱。| |`shippingAmount`|客戶必須支付的運費。| |`currencyCode`|此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR`| |`address`|技術地址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義| |`billingAddress`|帳單郵寄地址| |`street1`|主要街道層級資訊、公寓號碼、街道號碼和街道名稱| |`street2`|街道層級資訊的其他欄位| |`city`|城市名稱| |`state`|狀態名稱。 此為自由格式的欄位。| |`postalCode`|地點的郵遞區號。 郵遞區號並非適用於所有國家/地區。 在某些國家/地區，此資料僅包含郵遞區號的一部分。| |`country`|政府管理的領土名稱。 除了 `xdm:countryCode`，此為自由格式的欄位，可能有任何語言的國家/地區名稱。| |`personalEmail`|個人電子郵件地址| |`address`|技術位址，例如，「name@domain.com」，通常定義於RFC2822和後續標準|
