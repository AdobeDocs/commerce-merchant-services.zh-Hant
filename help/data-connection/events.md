---
title: 活動
description: 瞭解每個事件擷取哪些資料。
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: f90ef4d2732a0b0676e0899712f94b41a1c2d85a
workflow-type: tm+mt
source-wordcount: '6894'
ht-degree: 0%

---

# [!DNL Data Connection] 活動

下表列出您在安裝時可用的Commerce事件 [!DNL Data Connection] 副檔名。 這些事件收集的資料會傳送至Adobe Experience Platform Edge。 您也可以建立 [自訂事件](custom-events.md) 以立即收集未提供的其他資料。

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
| `commerce.productListAdds` | 表示是否已將產品新增至購物車。 值 `1` 表示已新增產品。 |
| `commerce.cart.cartID` | 識別客戶購物車的唯一ID。 |
| `commerce.commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `commerce.commerceScope.environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `commerce.commerceScope.websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |
| `productListItems` | 加入購物車的一系列產品。 |
| `productListItems.SKU` | 庫存單位。 產品的唯一識別碼。 |
| `productListItems.name` | 產品的顯示名稱或人類看得懂的名稱。 |
| `productListItems.priceTotal` | 產品明細專案的總價。 |
| `productListItems.quantity` | 購物車中的產品件數。 |
| `productListItems.discountAmount` | 表示套用的折扣金額。 |
| `productListItems.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR`. |
| `productListItems.productImageUrl` | 產品的主要影像URL。 |
| `productListItems.selectedOptions` | 用於可設定產品的欄位。 |
| `productListItems.selectedOptions.attribute` | 識別可設定產品的屬性，例如 `size` 或 `color`. |
| `productListItems.selectedOptions.value` | 識別屬性值，例如 `small` 或 `black`. |

### openCart

| 說明 | XDM事件名稱 |
|---|---|
| 建立新購物車時觸發，亦即將產品新增至空白購物車時。 | `commerce.productListOpens` |

#### 從openCart收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `commerce.productListOpens` | 指出是否已建立購物車。 值 `1` 表示已建立購物車。 |
| `commerce.cart.cartID` | 識別客戶購物車的唯一ID。 |
| `commerce.commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `commerce.commerceScope.environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `commerce.commerceScope.websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |
| `productListItems` | 加入購物車的一系列產品。 |
| `productListItems.SKU` | 庫存單位。 產品的唯一識別碼。 |
| `productListItems.name` | 產品的顯示名稱或人類看得懂的名稱。 |
| `productListItems.priceTotal` | 產品明細專案的總價。 |
| `productListItems.quantity` | 購物車中的產品件數。 |
| `productListItems.discountAmount` | 表示套用的折扣金額。 |
| `productListItems.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR`. |
| `productListItems.productImageUrl` | 產品的主要影像URL。 |
| `productListItems.selectedOptions` | 用於可設定產品的欄位。 |
| `productListItems.selectedOptions.attribute` | 識別可設定產品的屬性，例如 `size` 或 `color`. |
| `productListItems.selectedOptions.value` | 識別屬性值，例如 `small` 或 `black`. |

### removeFromCart

| 說明 | XDM事件名稱 |
|---|---|
| 每次移除產品或每次購物車中的產品數量減少時觸發。 | `commerce.productListRemovals` |

#### 從removeFromCart收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `commerce.productListRemovals` | 表示產品是否已從購物車移除。 值 `1` 表示產品已從購物車移除。 |
| `commerce.cart.cartID` | 識別客戶購物車的唯一ID。 |
| `commerce.commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `commerce.commerceScope.environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `commerce.commerceScope.websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |
| `productListItems` | 加入購物車的一系列產品。 |
| `productListItems.SKU` | 庫存單位。 產品的唯一識別碼。 |
| `productListItems.name` | 產品的顯示名稱或人類看得懂的名稱。 |
| `productListItems.priceTotal` | 產品明細專案的總價。 |
| `productListItems.quantity` | 購物車中的產品件數。 |
| `productListItems.discountAmount` | 表示套用的折扣金額。 |
| `productListItems.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR`. |
| `productListItems.productImageUrl` | 產品的主要影像URL。 |
| `productListItems.selectedOptions` | 用於可設定產品的欄位。 |
| `productListItems.selectedOptions.attribute` | 識別可設定產品的屬性，例如 `size` 或 `color`. |
| `productListItems.selectedOptions.value` | 識別屬性值，例如 `small` 或 `black`. |

### shoppingCartView

| 說明 | XDM事件名稱 |
|---|---|
| 任何購物車頁面載入時觸發。 | `commerce.productListViews` |

#### 從shoppingCartView收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `commerce.productListViews` | 表示是否已檢視產品清單。 |
| `commerce.cart.cartID` | 識別客戶購物車的唯一ID。 |
| `commerce.commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `commerce.commerceScope.environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `commerce.commerceScope.websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |
| `productListItems` | 加入購物車的一系列產品。 |
| `productListItems.SKU` | 庫存單位。 產品的唯一識別碼。 |
| `productListItems.name` | 產品的顯示名稱或人類看得懂的名稱。 |
| `productListItems.priceTotal` | 產品明細專案的總價。 |
| `productListItems.quantity` | 購物車中的產品件數。 |
| `productListItems.discountAmount` | 表示套用的折扣金額。 |
| `productListItems.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR`. |
| `productListItems.productImageUrl` | 產品的主要影像URL。 |
| `productListItems.selectedOptions` | 用於可設定產品的欄位。 |
| `productListItems.selectedOptions.attribute` | 識別可設定產品的屬性，例如 `size` 或 `color`. |
| `productListItems.selectedOptions.value` | 識別屬性值，例如 `small` 或 `black`. |

### pageView

| 說明 | XDM事件名稱 |
|---|---|
| 任何頁面載入時觸發。 | `web.webpagedetails.pageViews` |

#### 從pageView收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `web.webPageDetails.pageViews` | 指出是否已載入頁面。 A `value` 之 `1` 表示頁面已載入。 |
| `web.webPageDetails.URL` | 網頁的規範或一般URL。 這可以是用來存取頁面的實際URL，將使用進行記錄 `Web Link`. |
| `web.webPageDetails.name` | 網頁的規範名稱。 此名稱不一定是頁面標題或直接與頁面內容相關聯，但用於整理網站頁面以進行分類。 |
| `web.webReferrer.URL` | 購物者在點按您網站的連結前所造訪的網頁的URL。 |
| `commerce.commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `commerce.commerceScope.environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `commerce.commerceScope.websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |

### productPageView

| 說明 | XDM事件名稱 |
|---|---|
| 任何產品頁面載入時觸發。 | `commerce.productViews` |

#### 從productPageView收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `commerce.productViews` | 表示是否已檢視產品。 |
| `commerce.commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `commerce.commerceScope.environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `commerce.commerceScope.websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |
| `productListItems` | 加入購物車的一系列產品。 |
| `productListItems.SKU` | 庫存單位。 產品的唯一識別碼。 |
| `productListItems.name` | 產品的顯示名稱或人類看得懂的名稱。 |
| `productListItems.priceTotal` | 產品明細專案的總價。 |
| `productListItems.quantity` | 購物車中的產品件數。 |
| `productListItems.discountAmount` | 表示套用的折扣金額。 |
| `productListItems.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR`. |
| `productListItems.productImageUrl` | 產品的主要影像URL。 |
| `productListItems.selectedOptions` | 用於可設定產品的欄位。 |
| `productListItems.selectedOptions.attribute` | 識別可設定產品的屬性，例如 `size` 或 `color`. |
| `productListItems.selectedOptions.value` | 識別屬性值，例如 `small` 或 `black`. |

### startCheckout

| 說明 | XDM事件名稱 |
|---|---|
| 購物者按一下結帳按鈕時觸發。 | `commerce.checkouts` |

#### 從startCheckout收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `commerce.checkouts` | 表示在結帳過程中是否發生動作。 |
| `commerce.cart.cartID` | 識別客戶購物車的唯一ID。 |
| `commerce.commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `commerce.commerceScope.environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `commerce.commerceScope.websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |
| `productListItems` | 加入購物車的一系列產品。 |
| `productListItems.SKU` | 庫存單位。 產品的唯一識別碼。 |
| `productListItems.name` | 產品的顯示名稱或人類看得懂的名稱。 |
| `productListItems.priceTotal` | 產品明細專案的總價。 |
| `productListItems.quantity` | 購物車中的產品件數。 |
| `productListItems.discountAmount` | 表示套用的折扣金額。 |
| `productListItems.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR`. |
| `productListItems.productImageUrl` | 產品的主要影像URL。 |
| `productListItems.selectedOptions` | 用於可設定產品的欄位。 |
| `productListItems.selectedOptions.attribute` | 識別可設定產品的屬性，例如 `size` 或 `color`. |
| `productListItems.selectedOptions.value` | 識別屬性值，例如 `small` 或 `black`. |

### completeCheckout

| 說明 | XDM事件名稱 |
|---|---|
| 購物者下訂單時觸發。 | `commerce.order` |

#### 從completeCheckout收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `commerce.purchases` | 表示是否已接受訂單。 |
| `commerce.order` | 包含一或多個產品已下訂單的相關資訊。 |
| `commerce.order.purchaseID` | 賣家為此購買或合約所指派的唯一識別碼。 無法保證ID是唯一的。 |
| `commerce.order.payments` | 此訂單的付款清單。 |
| `commerce.order.payments.paymentTransactionID` | 此付款交易的唯一識別碼。 |
| `commerce.order.payments.paymentAmount` | 付款的值。 |
| `commerce.order.payments.paymentType` | 此訂單的付款方式。 選項包括： `cash`， `credit_card`， `debit_card`， `gift_card`， `check`， `paypal`， `wire_transfer`， `credit_card_reference`， `other`. |
| `commerce.order.payments.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR`. |
| `commerce.order.taxAmount` | 買方支付作為最終付款一部分的稅捐金額。 |
| `commerce.order.discountAmount` | 表示套用至整張訂單的折扣金額。 |
| `commerce.order.createdDate` | 在商務系統中建立新訂單的時間和日期。 例如， `2022-10-15T20:20:39+00:00`. |
| `commerce.shipping` | 一或多個產品的運送詳細資料。 |
| `commerce.shipping.shippingMethod` | 客戶選擇的配送方式，例如標準配送、加速配送、到店取貨等。 |
| `commerce.shipping.shippingAmount` | 客戶必須為運費支付的金額。 |  | `shipping` | 一或多個產品的運送詳細資料。 |
| `commerce.shipping.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR`. |
| `commerce.commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `commerce.commerceScope.environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `commerce.commerceScope.websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |
| `personalEmail` | 個人電子郵件地址。 |
| `personalEmail.address` | 技術地址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義。 |
| `productListItems` | 加入購物車的一系列產品。 |
| `productListItems.SKU` | 庫存單位。 產品的唯一識別碼。 |
| `productListItems.name` | 產品的顯示名稱或人類看得懂的名稱。 |
| `productListItems.priceTotal` | 產品明細專案的總價。 |
| `productListItems.quantity` | 購物車中的產品件數。 |
| `productListItems.discountAmount` | 表示套用的折扣金額。 |
| `productListItems.productImageUrl` | 產品的主要影像URL。 |
| `productListItems.selectedOptions` | 用於可設定產品的欄位。 |
| `productListItems.selectedOptions.attribute` | 識別可設定產品的屬性，例如 `size` 或 `color`. |
| `productListItems.selectedOptions.value` | 識別屬性值，例如 `small` 或 `black`. |

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
| `person` | 個別執行者、聯絡人或擁有者。 |
| `person.accountID` | 擷取使用者帳戶ID。 |
| `person.accountType` | 擷取使用者帳戶型別，例如 `Personal` 或 `Company`，如適用。 |
| `person.personalEmailID` | 技術地址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義。 |
| `personalEmail` | 擷取聯絡詳細資料 — 電子郵件和相關資訊。 |
| `personalEmail.address` | 技術地址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義。 |
| `userAccount` | 表示任何熟客方案細節、偏好設定、登入流程和其他帳戶偏好設定。 |
| `userAccount.login` | 表示訪客是否嘗試登入。 |
| `commerce.commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `commerce.commerceScope.environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `commerce.commerceScope.websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |

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
| `userAccount` | 表示任何熟客方案細節、偏好設定、登入流程和其他帳戶偏好設定。 |
| `userAccount.logout` | 表示訪客是否嘗試登出。 |
| `commerce.commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `commerce.commerceScope.environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `commerce.commerceScope.websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |

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
| `person` | 個別執行者、聯絡人或擁有者。 |
| `person.accountID` | 擷取使用者帳戶ID。 |
| `person.accountType` | 擷取使用者帳戶型別，例如 `Personal` 或 `Company`，如適用。 |
| `person.personalEmailID` | 技術地址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義。 |
| `personalEmail` | 擷取聯絡詳細資料 — 電子郵件和相關資訊。 |
| `personalEmail.address` | 技術地址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義。 |
| `userAccount` | 表示任何熟客方案細節、偏好設定、登入流程和其他帳戶偏好設定。 |
| `userAccount.updateProfile` | 指出使用者是否已更新其帳戶設定檔。 |
| `commerce.commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `commerce.commerceScope.environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `commerce.commerceScope.websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |

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
| `person` | 個別執行者、聯絡人或擁有者。 |
| `person.accountID` | 擷取使用者帳戶ID。 |
| `person.accountType` | 擷取使用者帳戶型別，例如 `Personal` 或 `Company`，如適用。 |
| `person.personalEmailID` | 技術地址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義。 |
| `personalEmail` | 擷取聯絡詳細資料 — 電子郵件和相關資訊。 |
| `personalEmail.address` | 技術地址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義。 |
| `userAccount` | 表示任何熟客方案細節、偏好設定、登入流程和其他帳戶偏好設定。 |
| `userAccount.updateProfile` | 指出使用者是否已更新其帳戶設定檔。 |
| `commerce.commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `commerce.commerceScope.environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `commerce.commerceScope.websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |

## 搜尋事件

搜尋事件會提供與購物者意圖相關的資料。 深入瞭解購物者的意圖，有助於商戶瞭解購物者如何搜尋商品、點選內容，以及最終購買或放棄。 此資料如何使用的範例是，如果您想要鎖定搜尋您最熱門產品但從未購買產品的現有購物者。

使用 `searchRequest.id` 和 `searchResponse.id` 在「 」和「 」 `searchRequestSent` 和 `searchResponseReceived` 將搜尋要求互動參照至對應搜尋回應的事件。

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
| `searchRequest` | 表示是否已傳送搜尋要求。 |
| `searchRequest.id` | 此特定搜尋要求的唯一ID。 |
| `searchRequest.value` | 請求的可量化值。 |
| `siteSearch` | 包含搜尋的相關資訊。 |
| `siteSearch.filter` | 顯示是否套用任何篩選器以限制搜尋結果。 |
| `siteSearch.filter.attribute` （篩選） | 用於確定是否將其納入搜尋結果的專案面向。 |
| `siteSearch.filter.isRange` | 為true時，值表示可接受值範圍的端點。 |
| `siteSearch.filter.value` | 用於確定搜尋結果中包含哪些專案的屬性值。 |
| `siteSearch.sort` | 指出搜尋結果的排序方式。 |
| `siteSearch.sort.attribute` （排序） | 用於對搜尋結果中的專案進行排序的屬性。 |
| `siteSearch.sort.order` | 傳回搜尋結果的順序。 |
| `siteSearch.query` | 搜尋的字詞。 |
| `commerce.commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `commerce.commerceScope.environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `commerce.commerceScope.websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |

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
| `searchResponse` | 表示是否已收到搜尋回應。 |
| `searchResponse.id` | 此特定搜尋回應的唯一ID。 |
| `searchResponse.value` | 回應的可量化值。 |
| `siteSearch.numberOfResults` | 傳回的產品數。 |
| `siteSearch.suggestions` | 字串陣列，其中包含存在於目錄中且與搜尋查詢類似的產品和類別名稱。 |
| `productListItems` | 加入購物車的一系列產品。 |
| `productListItems.SKU` | 庫存單位。 產品的唯一識別碼。 |
| `productListItems.name` | 產品的顯示名稱或人類看得懂的名稱。 |
| `productListItems.productImageUrl` | 產品的主要影像URL。 |
| `commerce.commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `commerce.commerceScope.environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `commerce.commerceScope.websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |

## B2B事件

![適用於Adobe Commerce的B2B](../assets/b2b.svg) 針對B2B商家，您必須 [安裝](install.md#install-the-b2b-extension) 此 `experience-platform-connector-b2b` 擴充功能以啟用這些事件。

B2B事件包含 [請購單清單](https://experienceleague.adobe.com/docs/commerce-admin/b2b/requisition-lists/requisition-lists.html) 資訊，例如，是否已建立、新增或從中刪除請購單清單。 透過追蹤請購單清單的特定事件，您可以檢視客戶經常購買哪些產品，並根據該資料建立行銷活動。

### createRequisitionList

| 說明 | XDM事件名稱 |
|---|---|
| 當購物者建立請購單清單時觸發。 | `commerce.requisitionListOpens` |

#### 從createRequisitionList收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `commerce.requisitionListOpens` | 指示初始化新的請購單清單。 |
| `commerce.requisitionList` | 客戶建立的請購單清單屬性。 |
| `commerce.requisitionList.ID` | 請購單清單的唯一識別碼。 |
| `commerce.requisitionList.name` | 客戶指定的請購單清單名稱。 |
| `commerce.requisitionList.description` | 客戶指定的請購單清單摘要。 |
| `commerce.commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `commerce.commerceScope.environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `commerce.commerceScope.websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |

### addToRequisitionList

| 說明 | XDM事件名稱 |
|---|---|
| 購物者將產品新增至現有請購單清單或建立清單時觸發。 | `commerce.requisitionListAdds` |

#### 從addToRequisitionList收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `commerce.requisitionListAdds` | 指示新增一或多個產品至請購單清單。 |
| `commerce.requisitionList` | 客戶建立的請購單清單屬性。 |
| `commerce.requisitionList.ID` | 請購單清單的唯一識別碼。 |
| `commerce.requisitionList.name` | 客戶指定的請購單清單名稱。 |
| `commerce.requisitionList.description` | 客戶指定的請購單清單摘要。 |
| `commerce.commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `commerce.commerceScope.environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `commerce.commerceScope.websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |
| `productListItems` | 已新增至請購單清單的產品陣列。 |
| `productListItems.SKU` | 庫存單位。 產品的唯一識別碼。 |
| `productListItems.name` | 產品的顯示名稱或人類看得懂的名稱。 |
| `productListItems.priceTotal` | 產品明細專案的總價。 |
| `productListItems.quantity` | 購物車中的產品件數。 |
| `productListItems.discountAmount` | 表示套用的折扣金額。 |
| `productListItems.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR`. |
| `productListItems.selectedOptions` | 用於可設定產品的欄位。 |
| `productListItems.selectedOptions.attribute` | 識別可設定產品的屬性，例如 `size` 或 `color`. |
| `productListItems.selectedOptions.value` | 識別屬性值，例如 `small` 或 `black`. |

### removeFromRequisitionList

| 說明 | XDM事件名稱 |
|---|---|
| 當購物者從請購單清單移除產品時觸發。 | `commerce.requisitionListRemovals` |

#### 從removeFromRequisitionList收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `commerce.requsitionListRemovals` | 表示從請購單清單移除一或多個產品。 |
| `commerce.requisitionList` | 客戶建立的請購單清單屬性。 |
| `commerce.requisitionList.ID` | 請購單清單的唯一識別碼。 |
| `commerce.requisitionList.name` | 客戶指定的請購單清單名稱。 |
| `commerce.requisitionList.description` | 客戶指定的請購單清單摘要。 |
| `commerce.commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `commerce.commerceScope.environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `commerce.commerceScope.websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |
| `productListItems` | 已新增至請購單清單的產品陣列。 |
| `productListItems.SKU` | 庫存單位。 產品的唯一識別碼。 |
| `productListItems.name` | 產品的顯示名稱或人類看得懂的名稱。 |
| `productListItems.priceTotal` | 產品明細專案的總價。 |
| `productListItems.quantity` | 購物車中的產品件數。 |
| `productListItems.discountAmount` | 表示套用的折扣金額。 |
| `productListItems.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR`. |
| `productListItems.selectedOptions` | 用於可設定產品的欄位。 |
| `productListItems.selectedOptions.attribute` | 識別可設定產品的屬性，例如 `size` 或 `color`. |
| `productListItems.selectedOptions.value` | 識別屬性值，例如 `small` 或 `black`. |

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
| `commerce.order` | 包含訂單的相關資訊。 |
| `commerce.order.purchaseID` | 賣家為此購買或合約所指派的唯一識別碼。 無法保證ID是唯一的。 |
| `commerce.order.payments` | 此訂單的付款清單。 |
| `commerce.order.payments.paymentTransactionID` | 此付款交易的唯一識別碼。 |
| `commerce.order.payments.paymentAmount` | 付款的值。 |
| `commerce.order.payments.paymentType` | 此訂單的付款方式。 已計算，允許自訂值。 |
| `commerce.order.payments.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR`. |
| `commerce.order.taxAmount` | 買方支付作為最終付款一部分的稅捐金額。 |
| `commerce.order.discountAmount` | 表示套用至整張訂單的折扣金額。 |
| `commerce.order.createdDate` | 在商務系統中建立新訂單的時間和日期。 例如， `2022-10-15T20:20:39+00:00`. |
| `commerce.order.currencyCode` | 用於訂單總額的ISO 4217貨幣代碼。 |
| `commerce.shipping` | 一或多個產品的運送詳細資料。 |
| `commerce.shipping.shippingMethod` | 客戶選擇的配送方式，例如標準配送、加速配送、到店取貨等。 |
| `commerce.shipping.shippingAmount` | 客戶必須為運費支付的金額。 |
| `commerce.shipping.currencyCode` | 用於配送總額的ISO 4217貨幣代碼。 |
| `commerce.commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `commerce.commerceScope.environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `commerce.commerceScope.websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |
| `commerce.billing.address` | 帳單郵寄地址。 |
| `commerce.billing.address.street1` | 主要街道層級資訊、公寓號碼、街道號碼和街道名稱 |
| `commerce.billing.address.street2` | 街道層級資訊的其他欄位。 |
| `commerce.billing.address.city` | 城市的名稱。 |
| `commerce.billing.address.state` | 狀態的名稱。 此為自由格式的欄位。 |
| `commerce.billing.address.postalCode` | 地點的郵遞區號。 郵遞區號並非適用於所有國家/地區。 在某些國家/地區，這僅包含郵遞區號的一部分。 |
| `commerce.billing.address.country` | 政府管理的領土的名稱。 除了 `xdm:countryCode`，此為自由格式的欄位，可能有任何語言的國家/地區名稱。 |
| `personalEmail` | 個人電子郵件地址。 |
| `personalEmail.address` | 技術地址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義。 |
| `productListItems` | 訂單中的一系列產品。 |
| `productListItems.id` | 此產品條目的明細專案識別碼。 |
| `productListItems.SKU` | 庫存單位。 產品的唯一識別碼。 |
| `productListItems.name` | 產品的顯示名稱或人類看得懂的名稱。 |
| `productListItems.priceTotal` | 產品明細專案的總價。 |
| `productListItems.quantity` | 購物車中的產品件數。 |
| `productListItems.discountAmount` | 表示套用的折扣金額。 |
| `productListItems.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR`. |
| `productListItems.selectedOptions` | 用於可設定產品的欄位。 |
| `productListItems.selectedOptions.attribute` | 識別可設定產品的屬性，例如 `size` 或 `color`. |
| `productListItems.selectedOptions.value` | 識別屬性值，例如 `small` 或 `black`. |
| `productListItems.categories` | 包含有關產品類別的資訊。 |
| `productListItems.categories.id` | 類別的唯一識別碼。 |
| `productListItems.categories.name` | 類別的名稱。 |
| `productListItems.categories.path` | 類別的路徑。 |
| `productListItems.productImageUrl` | 產品的主要影像URL。 |

### orderInvoiced

| 說明 | XDM事件名稱 |
|---|---|
| 當商家提交商業發票以請求付款時觸發。 | `commerce.backofficeOrderInvoiced` |

#### 從orderInvoiced收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `commerce.order` | 包含訂單的相關資訊。 |
| `commerce.order.purchaseID` | 賣家為此購買或合約所指派的唯一識別碼。 無法保證ID是唯一的。 |
| `commerce.order.priceTotal` | 此訂單套用所有折扣和稅金後的總價。 |
| `commerce.order.currencyCode` | 用於訂單總額的ISO 4217貨幣代碼。 |
| `commerce.order.purchaseOrderNumber` | 購買者為此購買或合約所指派的唯一識別碼。 |
| `commerce.order.payments` | 此訂單的付款清單。 |
| `commerce.order.payments.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR`. |
| `commerce.order.payments.paymentType` | 此訂單的付款方式。 已計算，允許自訂值。 |
| `commerce.order.payments.paymentAmount` | 付款的值。 |
| `commerce.shipping` | 一或多個產品的運送詳細資料。 |
| `commerce.shipping.shippingMethod` | 客戶選擇的配送方式，例如標準配送、加速配送、到店取貨等。 |
| `commerce.shipping.shippingAmount` | 客戶必須為運費支付的金額。 |
| `commerce.commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `commerce.commerceScope.environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `commerce.commerceScope.websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |
| `personalEmail` | 個人電子郵件地址。 |
| `personalEmail.address` | 技術地址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義。 |
| `productListItems` | 訂單中的一系列產品。 |
| `productListItems.id` | 此產品條目的明細專案識別碼。 |
| `productListItems.SKU` | 庫存單位。 產品的唯一識別碼。 |
| `productListItems.name` | 產品的顯示名稱或人類看得懂的名稱。 |
| `productListItems.priceTotal` | 產品明細專案的總價。 |
| `productListItems.quantity` | 購物車中的產品件數。 |
| `productListItems.discountAmount` | 表示套用的折扣金額。 |
| `productListItems.categories` | 包含有關產品類別的資訊。 |
| `productListItems.categories.id` | 類別的唯一識別碼。 |
| `productListItems.categories.name` | 類別的名稱。 |
| `productListItems.categories.path` | 類別的路徑。 |

### orderItemsShipped

| 說明 | XDM事件名稱 |
|---|---|
| 在訂單出貨時觸發。 | `commerce.backofficeOrderItemsShipped` |

#### 從orderItemsShipped收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `commerce.order` | 包含訂單的相關資訊。 |
| `commerce.order.purchaseID` | 賣家為此購買或合約所指派的唯一識別碼。 無法保證ID是唯一的。 |
| `commerce.order.payments` | 此訂單的付款清單。 |
| `commerce.order.payments.paymentTransactionID` | 此付款交易的唯一識別碼。 |
| `commerce.order.payments.paymentAmount` | 付款的值。 |
| `commerce.order.payments.paymentType` | 此訂單的付款方式。 已計算，允許自訂值。 |
| `commerce.order.payments.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR`. |
| `commerce.order.priceTotal` | 此訂單套用所有折扣和稅金後的總價。 |
| `commerce.order.purchaseOrderNumber` | 購買者為此購買或合約所指派的唯一識別碼。 |
| `commerce.order.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR`. |
| `commerce.order.lastUpdatedDate` | 商業系統中特定訂單記錄的上次更新時間。 |
| `commerce.shipping` | 一或多個產品的運送詳細資料。 |
| `commerce.shipping.shippingMethod` | 客戶選擇的配送方式，例如標準配送、加速配送、到店取貨等。 |
| `commerce.shipping.shippingAmount` | 客戶必須為運費支付的金額。 |
| `commerce.shipping.address` | 實際送貨地址。 |
| `commerce.shipping.address.street1` | 主要街道層級資訊、公寓號碼、街道號碼和街道名稱。 |
| `commerce.shipping.address.street2` | 選用的街道資訊第二行。 |
| `commerce.shipping.address.city` | 城市的名稱。 |
| `commerce.shipping.address.state` | 州名。 此為自由格式的欄位。 |
| `commerce.shipping.address.postalCode` | 地點的郵遞區號。 郵遞區號並非適用於所有國家/地區。 在某些國家/地區，這僅包含郵遞區號的一部分。 |
| `commerce.shipping.address.country` | 政府管理的領土的名稱。 除了 `xdm:countryCode`，此為自由格式的欄位，可能有任何語言的國家/地區名稱。 |
| `commerce.shipping.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR`. |
| `commerce.shipping.trackingNumber` | 出貨承運商為訂單料號出貨提供的追蹤編號。 |
| `commerce.shipping.trackingURL` | 追蹤訂單專案出貨狀態的URL。 |
| `commerce.shipping.shipDate` | 訂單中一或多個料號出貨的日期。 |
| `commerce.commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `commerce.commerceScope.environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `commerce.commerceScope.websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |
| `commerce.billing.address` | 帳單郵寄地址。 |
| `commerce.billing.address.street1` | 主要街道層級資訊、公寓號碼、街道號碼和街道名稱 |
| `commerce.billing.address.street2` | 街道層級資訊的其他欄位。 |
| `commerce.billing.address.city` | 城市的名稱。 |
| `commerce.billing.address.state` | 狀態的名稱。 此為自由格式的欄位。 |
| `commerce.billing.address.postalCode` | 地點的郵遞區號。 郵遞區號並非適用於所有國家/地區。 在某些國家/地區，這僅包含郵遞區號的一部分。 |
| `commerce.billing.address.country` | 政府管理的領土的名稱。 除了 `xdm:countryCode`，此為自由格式的欄位，可能有任何語言的國家/地區名稱。 |
| `personalEmail` | 個人電子郵件地址。 |
| `personalEmail.address` | 技術地址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義。 |
| `productListItems` | 訂單中的一系列產品。 |
| `productListItems.SKU` | 庫存單位。 產品的唯一識別碼。 |
| `productListItems.name` | 產品的顯示名稱或人類看得懂的名稱。 |
| `productListItems.priceTotal` | 產品明細專案的總價。 |
| `productListItems.quantity` | 購物車中的產品件數。 |
| `productListItems.discountAmount` | 表示套用的折扣金額。 |
| `productListItems.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR`. |
| `productListItems.selectedOptions` | 用於可設定產品的欄位。 |
| `productListItems.selectedOptions.attribute` | 識別可設定產品的屬性，例如 `size` 或 `color`. |
| `productListItems.selectedOptions.value` | 識別屬性值，例如 `small` 或 `black`. |
| `productListItems.categories` | 包含有關產品類別的資訊。 |
| `productListItems.categories.id` | 類別的唯一識別碼。 |
| `productListItems.categories.name` | 類別的名稱。 |
| `productListItems.categories.path` | 類別的路徑。 |

### orderCanceled

| 說明 | XDM事件名稱 |
|---|---|
| 購物者取消訂單時觸發。 | `commerce.backofficeOrderCancelled` |

#### 從orderCanceled收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `commerce.order` | 包含訂單的相關資訊。 |
| `commerce.order.purchaseID` | 賣家為此購買或合約所指派的唯一識別碼。 無法保證ID是唯一的。 |
| `commerce.order.purchaseOrderNumber` | 購買者為此購買或合約所指派的唯一識別碼。 |
| `commerce.order.cancelDate` | 購物者取消訂單的日期和時間。 |
| `commerce.order.lastUpdatedDate` | 商業系統中特定訂單記錄的上次更新時間。 |
| `commerce.commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `commerce.commerceScope.environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `commerce.commerceScope.websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |
| `personalEmail` | 個人電子郵件地址。 |
| `personalEmail.address` | 技術地址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義。 |

### orderLineItemRefreaded

| 說明 | XDM事件名稱 |
|---|---|
| 當購物者針對退回的料號退款時觸發。 | `commerce.backofficeCreditMemoIssued` |

#### 從orderLineItemRefreaded收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `commerce.order` | 包含訂單的相關資訊。 |
| `commerce.order.purchaseID` | 賣家為此購買或合約所指派的唯一識別碼。 無法保證ID是唯一的。 |
| `commerce.order.lastUpdatedDate` | 商業系統中特定訂單記錄的上次更新時間。 |
| `commerce.order.purchaseOrderNumber` | 購買者為此購買或合約所指派的唯一識別碼。 |
| `commerce.refunds` | 此訂單的退款清單。 |
| `commerce.refunds.transactionID` | 此退款的唯一識別碼。 |
| `commerce.refunds.refundAmount` | 退款的值。 |
| `commerce.refunds.refundPaymentType` | 此訂單的付款方式。 已計算，允許自訂值。 |
| `commerce.refunds.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR`. |
| `personalEmail` | 個人電子郵件地址。 |
| `personalEmail.address` | 技術地址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義。 |
| `productListItems` | 訂單中的一系列產品。 |
| `productListItems.SKU` | 庫存單位。 產品的唯一識別碼。 |
| `productListItems.name` | 產品的顯示名稱或人類看得懂的名稱。 |
| `productListItems.priceTotal` | 產品明細專案的總價。 |
| `productListItems.quantity` | 購物車中的產品件數。 |
| `productListItems.discountAmount` | 表示套用的折扣金額。 |
| `productListItems.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR`. |
| `productListItems.selectedOptions` | 用於可設定產品的欄位。 |
| `productListItems.selectedOptions.attribute` | 識別可設定產品的屬性，例如 `size` 或 `color`. |
| `productListItems.selectedOptions.value` | 識別屬性值，例如 `small` 或 `black`. |
| `productListItems.categories` | 包含有關產品類別的資訊。 |
| `productListItems.categories.id` | 類別的唯一識別碼。 |
| `productListItems.categories.name` | 類別的名稱。 |
| `productListItems.categories.path` | 類別的路徑。 |

### orderItemsReturnInitiated

| 說明 | XDM事件名稱 |
|---|---|
| 購物者要求傳回專案時觸發。 | `commerce.backofficeOrderItemsReturnInitiated` |

#### 從orderItemsReturnInitiated收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `commerce.order` | 包含訂單的相關資訊。 |
| `commerce.order.purchaseID` | 賣家為此購買或合約所指派的唯一識別碼。 無法保證ID是唯一的。 |
| `commerce.order.returns` | 此訂單的RMA （退貨授權）資訊。 |
| `commerce.order.returns.returnID` | 此RMA （退貨授權）的唯一識別碼。 |
| `commerce.order.returns.returnStatus` | RMA （退貨授權）的狀態，例如「擱置中」、「已關閉」等。 |
| `commerce.commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `commerce.commerceScope.environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `commerce.commerceScope.websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |
| `personalEmail` | 個人電子郵件地址。 |
| `personalEmail.address` | 技術地址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義。 |
| `productListItems` | 訂單中的一系列產品。 |
| `productListItems.SKU` | 庫存單位。 產品的唯一識別碼。 |
| `productListItems.name` | 產品的顯示名稱或人類看得懂的名稱。 |
| `productListItems.quantity` | 購物車中的產品件數。 |
| `productListItems.selectedOptions` | 用於可設定產品的欄位。 |
| `productListItems.selectedOptions.attribute` | 識別可設定產品的屬性，例如 `size` 或 `color`. |
| `productListItems.selectedOptions.value` | 識別屬性值，例如 `small` 或 `black`. |
| `productListItems.categories` | 包含有關產品類別的資訊。 |
| `productListItems.categories.id` | 類別的唯一識別碼。 |
| `productListItems.categories.name` | 類別的名稱。 |
| `productListItems.categories.path` | 類別的路徑。 |
| `productListItems.returnItem` | 此料號的RMA （退貨授權）資訊。 |
| `productListItems.returnItem.returnStatus` | 傳回專案的狀態，例如「擱置中」、「已核准」等。 |
| `productListItems.returnItem.returnReason` | 要求此專案退貨的原因。 |
| `productListItems.returnItem.returnItemCondition` | 要求傳回的專案的條件。 |
| `productListItems.returnItem.returnResolution` | 要退回之專案的要求解決方式，例如「退款」、「兌換」等。 |
| `productListItems.returnItem.returnQuantityRequested` | 購物者要求傳回的此專案數。 |
| `productListItems.returnItem.returnQuantityAuthorized` | 已授權可傳回的此專案數。 |
| `productListItems.returnItem.eturnQuantityReceived` | 收到的傳回專案數。 |
| `productListItems.returnItem.returnQuantityApproved` | 此專案與傳回完全完成且已核准的編號。 |

### orderItemReturnCompleted

| 說明 | XDM事件名稱 |
|---|---|
| 購物者要求退貨的專案完成時觸發。 | `commerce.backofficeOrderItemsReturnCompleted` |

#### 從orderItemReturnCompleted收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `commerce.order` | 包含訂單的相關資訊。 |
| `commerce.order.purchaseID` | 賣家為此購買或合約所指派的唯一識別碼。 無法保證ID是唯一的。 |
| `commerce.order.returns` | 此訂單的RMA （退貨授權）資訊。 |
| `commerce.order.returns.returnID` | 此RMA （退貨授權）的唯一識別碼。 |
| `commerce.order.returns.returnStatus` | RMA （退貨授權）的狀態，例如「擱置中」、「已關閉」等。 |
| `commerce.commerceScope` | 表示事件發生位置（商店檢視、商店、網站等）。 |
| `commerce.commerceScope.environmentID` | 環境識別碼。 32位數的英數字元ID，以連字型大小分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代碼。 每個網站可以有許多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的存放區檢視代碼。 每個商店可以有多個商店檢視。 |
| `commerce.commerceScope.websiteCode` | 不重複網站代碼。 一個環境中可以有許多網站。 |
| `personalEmail` | 個人電子郵件地址。 |
| `personalEmail.address` | 技術地址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義。 |
| `productListItems` | 訂單中的一系列產品。 |
| `productListItems.SKU` | 庫存單位。 產品的唯一識別碼。 |
| `productListItems.name` | 產品的顯示名稱或人類看得懂的名稱。 |
| `productListItems.selectedOptions` | 用於可設定產品的欄位。 |
| `productListItems.selectedOptions.attribute` | 識別可設定產品的屬性，例如 `size` 或 `color`. |
| `productListItems.selectedOptions.value` | 識別屬性值，例如 `small` 或 `black`. |
| `productListItems.categories` | 包含有關產品類別的資訊。 |
| `productListItems.categories.id` | 類別的唯一識別碼。 |
| `productListItems.categories.name` | 類別的名稱。 |
| `productListItems.categories.path` | 類別的路徑。 |
| `productListItems.returnItem` | 此料號的RMA （退貨授權）資訊。 |
| `productListItems.returnItem.returnStatus` | 傳回專案的狀態，例如「擱置中」、「已核准」等。 |
| `productListItems.returnItem.returnReason` | 要求此專案退貨的原因。 |
| `productListItems.returnItem.returnItemCondition` | 要求傳回的專案的條件。 |
| `productListItems.returnItem.returnResolution` | 要退回之專案的要求解決方式，例如「退款」、「兌換」等。 |
| `productListItems.returnItem.returnQuantityRequested` | 購物者要求傳回的此專案數。 |
| `productListItems.returnItem.returnQuantityAuthorized` | 已授權可傳回的此專案數。 |
| `productListItems.returnItem.eturnQuantityReceived` | 收到的傳回專案數。 |
| `productListItems.returnItem.returnQuantityApproved` | 此專案與傳回完全完成且已核准的編號。 |

### orderShipmentCompleted

| 說明 | XDM事件名稱 |
|---|---|
| 在出貨完成時觸發。 | `commerce.backofficeOrderShipmentCompleted` |

#### 從orderShipmentCompleted收集的資料

下表說明為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `commerce.order` | 包含訂單的相關資訊。 |
| `commerce.order.purchaseID` | 賣家為此購買或合約所指派的唯一識別碼。 無法保證ID是唯一的。 |
| `commerce.order.payments` | 此訂單的付款清單。 |
| `commerce.order.payments.paymentTransactionID` | 此付款交易的唯一識別碼。 |
| `commerce.order.payments.paymentAmount` | 付款的值。 |
| `commerce.order.payments.paymentType` | 此訂單的付款方式。 已計算，允許自訂值。 |
| `commerce.order.payments.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR`. |
| `commerce.order.taxAmount` | 買方支付作為最終付款一部分的稅捐金額。 |
| `commerce.order.createdDate` | 在商務系統中建立新訂單的時間和日期。 例如， `2022-10-15T20:20:39+00:00`. |
| `commerce.shipping` | 一或多個產品的運送詳細資料。 |
| `commerce.shipping.shippingMethod` | 客戶選擇的配送方式，例如標準配送、加速配送、到店取貨等。 |
| `commerce.shipping.shippingAmount` | 客戶必須為運費支付的金額。 |
| `commerce.shipping.shipDate` | 訂單中一或多個料號出貨的日期。 |
| `commerce.shipping.address` | 實際送貨地址。 |
| `commerce.shipping.address.street1` | 主要街道層級資訊、公寓號碼、街道號碼和街道名稱。 |
| `commerce.shipping.address.street2` | 選用的街道資訊第二行。 |
| `commerce.shipping.address.city` | 城市的名稱。 |
| `commerce.shipping.address.state` | 州名。 此為自由格式的欄位。 |
| `commerce.shipping.address.postalCode` | 地點的郵遞區號。 郵遞區號並非適用於所有國家/地區。 在某些國家/地區，這僅包含郵遞區號的一部分。 |
| `commerce.shipping.address.country` | 政府管理的領土的名稱。 除了 `xdm:countryCode`，此為自由格式的欄位，可能有任何語言的國家/地區名稱。 |
| `commerce.billing.address` | 帳單郵寄地址。 |
| `commerce.billing.address.street1` | 主要街道層級資訊、公寓號碼、街道號碼和街道名稱 |
| `commerce.billing.address.street2` | 街道層級資訊的其他欄位。 |
| `commerce.billing.address.city` | 城市的名稱。 |
| `commerce.billing.address.state` | 狀態的名稱。 此為自由格式的欄位。 |
| `commerce.billing.address.postalCode` | 地點的郵遞區號。 郵遞區號並非適用於所有國家/地區。 在某些國家/地區，這僅包含郵遞區號的一部分。 |
| `commerce.billing.address.country` | 政府管理的領土的名稱。 除了 `xdm:countryCode`，此為自由格式的欄位，可能有任何語言的國家/地區名稱。 |
| `personalEmail` | 個人電子郵件地址。 |
| `personalEmail.address` | 技術地址，例如， `name@domain.com` 如RFC2822和後續標準中一般定義。 |
| `productListItems` | 訂單中的一系列產品。 |
| `productListItems.SKU` | 庫存單位。 產品的唯一識別碼。 |
| `productListItems.name` | 產品的顯示名稱或人類看得懂的名稱。 |
| `productListItems.priceTotal` | 產品明細專案的總價。 |
| `productListItems.quantity` | 購物車中的產品件數。 |
| `productListItems.discountAmount` | 表示套用的折扣金額。 |
| `productListItems.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的貨幣代碼，例如 `USD` 或 `EUR`. |
| `productListItems.selectedOptions` | 用於可設定產品的欄位。 |
| `productListItems.selectedOptions.attribute` | 識別可設定產品的屬性，例如 `size` 或 `color`. |
| `productListItems.selectedOptions.value` | 識別屬性值，例如 `small` 或 `black`. |
| `productListItems.categories` | 包含有關產品類別的資訊。 |
| `productListItems.categories.id` | 類別的唯一識別碼。 |
| `productListItems.categories.name` | 類別的名稱。 |
| `productListItems.categories.path` | 類別的路徑。 |
