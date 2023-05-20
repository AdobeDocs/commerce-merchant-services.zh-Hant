---
title: 事件
description: 瞭解每個事件捕獲的資料。
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
source-git-commit: ddacfc053f83be750c63ba376519169b38f7f478
workflow-type: tm+mt
source-wordcount: '4596'
ht-degree: 0%

---

# Experience Platform連接器事件

下面列出了安裝Experience Platform連接器擴展時可用的Commerce事件。 這些事件收集的資料被發送到Adobe Experience Platform邊緣。 您還可以建立 [自定義事件](custom-events.md) 收集未在機箱中提供的其他資料。

除了以下事件收集的資料外，您還可以 [其他資料](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) 由Adobe Experience PlatformWeb SDK提供。

## 店面事件

店面事件在顧客瀏覽你的網站時收集匿名行為資料。 這些事件收集的資料可用於建立針對特定一組購物者的促銷和活動。

>[!NOTE]
>
>所有店面事件包括 [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) 欄位，其中包括購物者的電子郵件地址（如果可用）和ECID。 通過在每個事件中都包括此配置檔案資料，您不需要從Adobe Commerce單獨導入用戶帳戶。

### 添加到購物車

| 說明 | XDM事件名稱 |
|---|---|
| 當產品添加到購物車或購物車中產品的數量增加時觸發。 | `commerce.productListAdds` |

#### 從addToCart收集的資料

下表介紹了為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `productListAdds` | 指示是否將產品添加到購物車。 值 `1` 表示已添加產品。 |
| `productListItems` | 添加到購物車中的一系列產品 |
| `SKU` | 庫存單位。 產品的唯一標識符。 |
| `name` | 產品的顯示名稱或人可讀名稱 |
| `priceTotal` | 產品行項目的總價 |
| `quantity` | 添加到購物車的產品單位數 |
| `discountAmount` | 指示應用的折扣金額 |
| `currencyCode` | 的 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 產品的幣種 |
| `productImageUrl` | 產品的主影像URL |
| `selectedOptions` | 用於可配置產品的欄位。 `attribute` 標識可配置產品的屬性，如 `size` 或 `color` 和 `value` 標識屬性的值，如 `small` 或 `black`。 |
| `cartID` | 標識客戶購物車的唯一ID |

### openCart

| 說明 | XDM事件名稱 |
|---|---|
| 建立新購物車時觸發，即將產品添加到空購物車時觸發。 | `commerce.productListOpens` |

#### 從openCart收集的資料

下表介紹了為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `productListOpens` | 指示是否已建立購物車。 值 `1` 表示已建立購物車。 |
| `productListItems` | 添加到購物車中的一系列產品 |
| `SKU` | 庫存單位。 產品的唯一標識符。 |
| `name` | 產品的顯示名稱或人可讀名稱 |
| `priceTotal` | 產品行項目的總價 |
| `quantity` | 添加到購物車的產品單位數 |
| `discountAmount` | 指示應用的折扣金額 |
| `currencyCode` | 的 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 產品的幣種 |
| `productImageUrl` | 產品的主影像URL |
| `selectedOptions` | 用於可配置產品的欄位。 `attribute` 標識可配置產品的屬性，如 `size` 或 `color` 和 `value` 標識屬性的值，如 `small` 或 `black`。 |
| `cartID` | 標識客戶購物車的唯一ID |

### 刪除自購物車

| 說明 | XDM事件名稱 |
|---|---|
| 每次刪除產品或每次減少購物車中產品的數量時觸發。 | `commerce.productListRemovals` |

#### 從removeFromCart收集的資料

下表介紹了為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `productListRemovals` | 指示是否從購物車中刪除了產品。 值 `1` 指示已從購物車中刪除產品。 |
| `productListItems` | 從購物車中刪除的一系列產品 |
| `SKU` | 庫存單位。 產品的唯一標識符。 |
| `name` | 產品的顯示名稱或人可讀名稱 |
| `priceTotal` | 產品行項目的總價 |
| `quantity` | 從購物車中刪除的產品單位數 |
| `discountAmount` | 指示應用的折扣金額 |
| `currencyCode` | 的 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 產品的幣種 |
| `productImageUrl` | 產品的主影像URL |
| `selectedOptions` | 用於可配置產品的欄位。 `attribute` 標識可配置產品的屬性，如 `size` 或 `color` 和 `value` 標識屬性的值，如 `small` 或 `black`。 |
| `cartID` | 標識客戶購物車的唯一ID |

### 購物車視圖

| 說明 | XDM事件名稱 |
|---|---|
| 載入任何購物車頁面時觸發。 | `commerce.productListViews` |

#### 從shoppingCartView收集的資料

下表介紹了為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `productListViews` | 指示是否查看了產品清單 |
| `productListItems` | 購物車中的一系列產品 |
| `SKU` | 庫存單位。 產品的唯一標識符。 |
| `name` | 產品的顯示名稱或人可讀名稱 |
| `priceTotal` | 產品行項目的總價 |
| `quantity` | 購物車中的產品單位數 |
| `discountAmount` | 指示應用的折扣金額 |
| `currencyCode` | 的 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 產品的幣種 |
| `productImageUrl` | 產品的主影像URL |
| `selectedOptions` | 用於可配置產品的欄位。 `attribute` 標識可配置產品的屬性，如 `size` 或 `color` 和 `value` 標識屬性的值，如 `small` 或 `black`。 |
| `cartID` | 標識客戶購物車的唯一ID |

### 頁面視圖

| 說明 | XDM事件名稱 |
|---|---|
| 載入任何頁面時觸發。 | `web.webpagedetails.pageViews` |

#### 從pageView收集的資料

下表介紹了為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `pageViews` | 指示是否載入了頁面。 A `value` 共 `1` 指示已載入該頁。 |

### productPageView

| 說明 | XDM事件名稱 |
|---|---|
| 載入任何產品頁時觸發。 | `commerce.productViews` |

#### 從productPageView收集的資料

下表介紹了為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `productViews` | 指示是否查看了產品 |
| `productListItems` | 購物車中的一系列產品 |
| `SKU` | 庫存單位。 產品的唯一標識符。 |
| `name` | 產品的顯示名稱或人可讀名稱 |
| `priceTotal` | 產品行項目的總價 |
| `discountAmount` | 指示應用的折扣金額 |
| `currencyCode` | 的 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 產品的幣種 |
| `productImageUrl` | 產品的主影像URL |
| `selectedOptions` | 用於可配置產品的欄位。 `attribute` 標識可配置產品的屬性，如 `size` 或 `color` 和 `value` 標識屬性的值，如 `small` 或 `black`。 |

### 開始簽出

| 說明 | XDM事件名稱 |
|---|---|
| 當購物者按一下結帳按鈕時觸發。 | `commerce.checkouts` |

#### 從startCheckout收集的資料

下表介紹了為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `checkouts` | 指示在簽出過程中是否發生了操作 |
| `productListItems` | 購物車中的一系列產品 |
| `SKU` | 庫存單位。 產品的唯一標識符。 |
| `name` | 產品的顯示名稱或人可讀名稱 |
| `priceTotal` | 產品行項目的總價 |
| `quantity` | 購物車中的產品單位數 |
| `discountAmount` | 指示應用的折扣金額 |
| `currencyCode` | 的 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 產品的幣種 |
| `productImageUrl` | 產品的主影像URL |
| `selectedOptions` | 用於可配置產品的欄位。 `attribute` 標識可配置產品的屬性，如 `size` 或 `color` 和 `value` 標識屬性的值，如 `small` 或 `black`。 |
| `cartID` | 標識客戶購物車的唯一ID |

### 完成簽出

| 說明 | XDM事件名稱 |
|---|---|
| 購物者下訂單時觸發。 | `commerce.order` |

#### 從completeCheckout收集的資料

下表介紹了為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `purchases` | 指示是否已接受訂單 |
| `order` | 包含有關一個或多個產品的已下訂單的資訊 |
| `purchaseID` | 賣方為此採購或合同分配的唯一標識符。 無法保證ID是唯一的。 |
| `orderType` | 指示已下達的訂單類型，如「結帳」或「即時採購」 |
| `payments` | 此訂單的付款清單 |
| `currencyCode` | 的 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 用於此付款項的幣種代碼。 比如說， `USD` 或 `EUR`。 |
| `paymentAmount` | 付款的值 |
| `paymentType` | 此訂單的付款方式。 選項包括： `cash`。 `credit_card`。 `debit_card`。 `gift_card`。 `check`。 `paypal`。 `wire_transfer`。 `credit_card_reference`。 `other` |
| `transactionID` | 此付款項的唯一交易記錄標識符 |
| `shipping` | 一個或多個產品的發運詳細資訊。 |
| `shippingMethod` | 由客戶選擇的運輸方法，如標準交貨、快速交貨、在商店中提貨等 |
| `shippingAmount` | 購物車中物料的總發運成本 |
| `promotionID` | 升級的唯一標識符（如果有） |
| `personalEmail` | 指定個人電子郵件地址 |
| `address` | 例如， `name@domain.com` RFC2822和後續標準中通常定義的 |
| `productListItems` | 購物車中的一系列產品 |
| `SKU` | 庫存單位。 產品的唯一標識符。 |
| `name` | 產品的顯示名稱或人可讀名稱 |
| `priceTotal` | 產品行項目的總價 |
| `quantity` | 購物車中的產品單位數 |
| `discountAmount` | 指示應用的折扣金額 |
| `currencyCode` | 的 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 用於訂單合計的幣種代碼。 |
| `productImageUrl` | 產品的主影像URL |
| `selectedOptions` | 用於可配置產品的欄位。 `attribute` 標識可配置產品的屬性，如 `size` 或 `color` 和 `value` 標識屬性的值，如 `small` 或 `black`。 |

## 配置檔案事件

配置檔案事件包括帳戶資訊，如 `signIn`。 `signOut`。 `createAccount`, `editAccount`。 此資料用於幫助填充關鍵客戶詳細資訊，這些詳細資訊是更好地定義細分市場或執行市場營銷活動所必需的，例如，您希望瞄準住在紐約的購物者。

### 登錄

| 說明 | XDM事件名稱 |
|---|---|
| 當購物者嘗試登錄時觸發。 | `userAccount.login` |

>[!NOTE]
>
> 當嘗試特定操作時觸發此事件。 它不表示操作成功。

#### 從signIn收集的資料

下表介紹了為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `person` | 個人演員、聯繫人或所有者 |
| `accountID` | 捕獲用戶帳戶ID |
| `accountType` | 捕獲用戶帳戶類型，如 `Personal` 或 `Company`（如果適用） |
| `personalEmailID` | 例如， `name@domain.com` RFC2822和後續標準中通常定義的 |
| `personalEmail` | 捕獲聯繫人詳細資訊 — 電子郵件和相關資訊 |
| `address` | 例如， `name@domain.com` RFC2822和後續標準中通常定義的 |
| `userAccount` | 指示任何會員詳細資訊、首選項、登錄流程和其他帳戶首選項 |
| `login` | 指示訪問者是否嘗試登錄 |

### 註銷

| 說明 | XDM事件名稱 |
|---|---|
| 當購物者嘗試註銷時觸發。 | `userAccount.logout` |

>[!NOTE]
>
> 當嘗試特定操作時觸發此事件。 它不表示操作成功。

#### 從signOut收集的資料

下表介紹了為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `userAccount` | 指示任何會員詳細資訊、首選項、登錄流程和其他帳戶首選項 |
| `logout` | 指示訪問者是否嘗試註銷 |

### 建立帳戶

| 說明 | XDM事件名稱 |
|---|---|
| 當購物者嘗試建立帳戶時觸發。 | `userAccount.createProfile` |

>[!NOTE]
>
> 當嘗試特定操作時觸發此事件。 它不表示操作成功。

#### 從createAccount收集的資料

下表介紹了為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `person` | 個人演員、聯繫人或所有者 |
| `accountID` | 捕獲用戶帳戶ID |
| `accountType` | 捕獲用戶帳戶類型，如 `Personal` 或 `Company`（如果適用） |
| `personalEmailID` | 例如， `name@domain.com` RFC2822和後續標準中通常定義的 |
| `personalEmail` | 捕獲聯繫人詳細資訊 — 電子郵件和相關資訊 |
| `address` | 例如， `name@domain.com` RFC2822和後續標準中通常定義的 |
| `userAccount` | 指示任何會員詳細資訊、首選項、登錄流程和其他帳戶首選項 |
| `createProfile` | 指示用戶是否已建立帳戶配置檔案 |

### 編輯帳戶

| 說明 | XDM事件名稱 |
|---|---|
| 當購物者嘗試編輯帳戶時觸發。 | `userAccount.updateProfile` |

>[!NOTE]
>
> 當嘗試特定操作時觸發此事件。 它不表示操作成功。

#### 從editAccount收集的資料

下表介紹了為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `person` | 個人演員、聯繫人或所有者 |
| `accountID` | 捕獲用戶帳戶ID |
| `accountType` | 捕獲用戶帳戶類型，如 `Personal` 或 `Company`（如果適用） |
| `personalEmailID` | 例如， `name@domain.com` RFC2822和後續標準中通常定義的 |
| `personalEmail` | 捕獲聯繫人詳細資訊 — 電子郵件和相關資訊 |
| `address` | 例如， `name@domain.com` RFC2822和後續標準中通常定義的 |
| `userAccount` | 指示任何會員詳細資訊、首選項、登錄流程和其他帳戶首選項 |
| `updateProfile` | 指示用戶是否已更新其帳戶配置檔案 |

## 搜索事件

搜索事件提供與購物者意圖相關的資料。 對購物者意圖的洞察有助於商家瞭解購物者如何搜索商品、點擊什麼商品，並最終購買或放棄。 您可以如何使用此資料的一個示例是，如果您希望瞄準那些搜索您的頂級產品但從不購買該產品的現有購物者。

使用 `uniqueIdentifier` 在 `searchRequestSent` 和 `searchResponseReceived` 將搜索請求交叉引用到相應的搜索響應的事件。

### searchRequestSent

| 說明 | XDM事件名稱 |
|---|---|
| 由「鍵入時搜索」跨距中的以下事件觸發：<br><br>按Enter鍵，按一下 _全部查看_<br><br>&#x200B;由搜索結果頁上的以下事件觸發：<br><br>選擇篩選器，更改排序順序(_排序依據_)，更改排序方向（升序或降序），更改每頁的結果數(_每頁顯示#_)，導航到下一頁，導航到上一頁，導航到其他頁 | `searchRequest` |

>[!NOTE]
>
>安裝了B2B模組的Adobe Commerce企業版不支援搜索事件。

#### 從searchRequestSent收集的資料

下表介紹了為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `searchRequest` | 指示是否發送了搜索請求 |
| `id` | 此特定搜索請求的唯一ID |
| `filter` | 指示是否應用了任何篩選器以限制搜索結果 |
| `attribute` （篩選器） | 用於確定是否將項目包括在搜索結果中的項目的方面 |
| `value` | 用於確定搜索結果中包括哪些項的屬性值 |
| `isRange` | 如果為true，則值指示可接受值範圍的端點 |
| `sort` | 指示應如何對搜索結果進行排序 |
| `attribute` （排序） | 用於對搜索結果中的項排序的屬性 |
| `order` | 返回搜索結果的順序 |
| `query` | 搜索的詞 |

### searchResponseReceived

| 說明 | XDM事件名稱 |
|---|---|
| 當Live Search返回「鍵入時搜索」跨距或搜索結果頁的結果時觸發。 | `searchResponse` |

>[!NOTE]
>
>安裝了B2B模組的Adobe Commerce企業版不支援搜索事件。

#### 從searchResponseReceived收集的資料

下表介紹了為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `searchResponse` | 指示是否已收到搜索響應 |
| `id` | 此特定搜索響應的唯一ID |
| `suggestions` | 包含目錄中與搜索查詢類似的產品和類別名稱的字串陣列 |
| `numberOfResults` | 返回的產品數 |
| `productListItems` | 購物車中的一系列產品。 |
| `SKU` | 庫存單位。 產品的唯一標識符。 |
| `name` | 產品的顯示名稱或人可讀名稱 |
| `productImageUrl` | 產品的主影像URL |

## B2B事件

![Adobe CommerceB2B](../assets/b2b.svg) 對於B2B商戶，必須 [安裝](install.md#install-the-b2b-extension) 這樣 `experience-platform-connector-b2b` 擴展，以啟用這些事件。

B2B事件包含 [申請表](https://experienceleague.adobe.com/docs/commerce-admin/b2b/requisition-lists/requisition-lists.html) 資訊，如建立、添加或刪除申請清單。 通過跟蹤特定於申請清單的事件，您可以查看您的客戶經常購買哪些產品，並根據這些資料建立市場活動。

### createRequisitionList

| 說明 | XDM事件名稱 |
|---|---|
| 當購物者建立新申請清單時觸發。 | `commerce.requisitionListOpens` |

#### 從createRequisitionList收集的資料

下表介紹了為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `requisitionList` | 客戶建立的申請清單的屬性 |
| `ID` | 申請清單的唯一標識符 |
| `name` | 客戶指定的申請清單的名稱 |
| `description` | 客戶指定的申請清單說明 |

### addToRequisitionList

| 說明 | XDM事件名稱 |
|---|---|
| 當購物者將產品添加到現有請求清單或建立新清單時觸發。 | `commerce.requisitionListAdds` |

>[!NOTE]
>
>`addToRequisitionList` 在類別視圖頁面或可配置產品上不受支援。 產品視圖頁面和簡單產品都支援此功能。

#### 從addToRequistionList收集的資料

下表介紹了為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `requisitionList` | 客戶建立的申請清單的屬性 |
| `ID` | 申請清單的唯一標識符 |
| `name` | 客戶指定的申請清單的名稱 |
| `description` | 客戶指定的申請清單說明 |
| `productListItems` | 已添加到申請清單的產品陣列 |
| `name` | 產品的顯示名稱或人可讀名稱 |
| `SKU` | 庫存單位。 產品的唯一標識符。 |
| `quantity` | 添加的產品單位數 |
| `priceTotal` | 產品行項目的總價 |
| `discountAmount` | 指示應用的折扣金額 |
| `currencyCode` | 的 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 用於此付款項的幣種代碼 |
| `selectedOptions` | 用於可配置產品的欄位。 `attribute` 標識可配置產品的屬性，如 `size` 或 `color` 和 `value` 標識屬性的值，如 `small` 或 `black`。 |

### removeFromRequistionList

| 說明 | XDM事件名稱 |
|---|---|
| 當購物者從申請清單中刪除產品時觸發。 | `commerce.requisitionListRemovals` |

#### 從removeFromRequisitionList收集的資料

下表介紹了為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `requisitionList` | 客戶建立的申請清單的屬性 |
| `ID` | 申請清單的唯一標識符 |
| `name` | 客戶指定的申請清單的名稱 |
| `description` | 客戶指定的申請清單說明 |
| `productListItems` | 已添加到申請清單的產品陣列 |
| `name` | 產品的顯示名稱或人可讀名稱 |
| `SKU` | 庫存單位。 產品的唯一標識符。 |
| `quantity` | 添加的產品單位數 |
| `priceTotal` | 產品行項目的總價 |
| `discountAmount` | 指示應用的折扣金額 |
| `currencyCode` | 的 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 用於此付款項的幣種代碼 |
| `selectedOptions` | 用於可配置產品的欄位。 `attribute` 標識可配置產品的屬性，如 `size` 或 `color` 和 `value` 標識屬性的值，如 `small` 或 `black`。 |

## 後台辦公室事件

後台辦公室事件包含有關訂單狀態的資訊，例如訂單是否已下達、取消、退還、發運或完成。 這些伺服器端事件收集的資料顯示購物者訂單的360視圖。 此視圖可幫助商家在制定市場營銷活動時更好地確定或分析整個訂單狀態。 例如，您可以發現某些產品類別中的趨勢，這些趨勢在一年中的不同時間表現良好。 例如，冬季服裝在寒冷的月份賣得更好，或者消費者對某些產品顏色多年來感興趣。 此外，訂單狀態資料還可以通過瞭解購物者基於先前訂單的轉換傾向來幫助您計算客戶的生命週期價值。

>[!NOTE]
>
>所有後台辦公室事件包括 [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) 欄位，提供購物者的電子郵件地址。 通過在每個事件中都包括此配置檔案資料，您不需要從Adobe Commerce單獨導入用戶帳戶。

### 訂單已放置

| 說明 | XDM事件名稱 |
|---|---|
| 購物者下訂單時觸發。 | `commerce.backofficeOrderPlaced` |

#### 從orderPlaced收集的資料

下表介紹了為此事件收集的資料。

| 欄位 | 說明 |
|---|---|
| `address` | 例如， `name@domain.com` RFC2822和後續標準中通常定義的 |
| `productListItems` | 按順序排列的一系列產品 |
| `id` | 此產品條目的行項目標識符。 產品本身通過 `product` 的子菜單。 |
| `name` | 產品的顯示名稱或人可讀名稱 |
| `SKU` | 庫存單位。 產品的唯一標識符。 |
| `quantity` | 購物車中的產品單位數 |
| `priceTotal` | 產品行項目的總價 |
| `discountAmount` | 指示應用的折扣金額 |
| `order` | 包含有關訂單的資訊 |
| `purchaseID` | 賣方為此採購或合同分配的唯一標識符。 無法保證ID是唯一的 |
| `priceTotal` | 已應用所有折扣和稅後此訂單的總價格 |
| `currencyCode` | 用於訂單合計的ISO 4217幣種代碼 |
| `purchaseOrderNumber` | 購買者為此採購或合同分配的唯一標識符 |
| `payments` | 此訂單的付款清單 |
| `paymentType` | 此訂單的付款方式。 枚舉，允許自定義值。 |
| `currencyCode` | 的 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 用於此付款項的幣種代碼 |
| `paymentAmount` | 付款的值 |
| `taxAmount` | 作為最終付款一部分由買方支付的稅額 |
| `createdDate` | 在商務系統中建立新訂單的時間和日期。 比如說， `2022-10-15T20:20:39+00:00` |
| `shipping` | 一個或多個產品的發運詳細資訊 |
| `shippingMethod` | 由客戶選擇的運輸方法，如標準交貨、快速交貨、在商店中提貨等 |
| `shippingAmount` | 客戶為發運而必須支付的金額。 |
| `address` | 實際發運地址 |
| `street1` | 主要街道層資訊、公寓編號、街道編號和街道名稱 |
| `street2` | 街道級別資訊的附加欄位 |
| `city` | 城市名稱 |
| `state` | 州名。 這是自由格式欄位。 |
| `postalCode` | 地點的郵遞區號。 並非所有國家都有郵遞區號。 在一些國家，這隻包含部分郵遞區號。 |
| `country` | 政府管理領土的名稱。 除 `xdm:countryCode`，這是一個自由格式欄位，可以使用任何語言使用國家/地區名稱。 |
| `billingAddress` | 開單郵政地址 |
| `street1` | 主要街道層資訊、公寓編號、街道編號和街道名稱 |
| `street2` | 街道級別資訊的附加欄位 |
| `city` | 城市名稱 |
| `state` | 州名。 這是自由格式欄位。 |
| `postalCode` | 地點的郵遞區號。 並非所有國家都有郵遞區號。 在一些國家，這隻包含部分郵遞區號。 |
| `country` | 政府管理領土的名稱。 除 `xdm:countryCode`，這是一個自由格式欄位，可以使用任何語言使用國家/地區名稱。 |
| `personalEmail` | 個人電子郵件地址 |
| `address` | 例如，RFC2822和後續標準中通常定義的「name@domain.com」技術地址 |

### 訂單物料已發運

| 說明 | XDM事件名稱 |
|---|---|
| 發運訂單時觸發。 | `commerce.backofficeOrderItemsShipped` |

#### 從orderItemsShipped收集的資料

下表介紹了為此事件收集的資料。
|欄位|說明| |—| |`address`|技術地址，例如 `name@domain.com` 如RFC2822和後續標準中通常定義的| |`productListItems`|按順序排列的產品陣列| |`id`|此產品條目的行項目標識符。 產品本身通過 `product` 的子菜單。| |`name`|產品的顯示名稱或人可讀名稱| |`SKU`|庫存單位。 產品的唯一標識符。| |`quantity`|購物車中的產品數量| |`priceTotal`|產品行項目的總價格| |`discountAmount`|指示應用的折扣金額| |`order`|包含有關訂單|的資訊 |`purchaseID`|賣方為此採購或合同分配的唯一標識符。 無法保證ID是唯一| |`priceTotal`|已應用所有折扣和稅後此訂單的總價格| |`currencyCode`|用於訂單合計的ISO 4217幣種代碼| |`purchaseOrderNumber`|採購人為此採購或合同分配的唯一標識符| |`payments`|此訂單的付款清單| |`paymentType`|此訂單的付款方式。 枚舉，允許自定義值。| |`currencyCode`| [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 此付款項使用的幣種代碼| |`paymentAmount`|付款值| |`lastUpdatedDate`|特定訂單記錄上次在商業系統中更新的時間| |`shipping`|一個或多個產品的發運詳細資訊| |`shippingMethod`|客戶選擇的發運方法，如標準交貨、快速交貨、在商店提貨等| |`trackingNumber`|發運承運人為訂單物料發運提供的跟蹤編號| |`trackingURL`|跟蹤訂單物料發運狀態的URL| |`shipDate`|訂單中一個或多個項的發貨日期| |`address`|實際發運地址| |`street1`|主要街道級別資訊、公寓編號、街道編號和街道名稱| |`street2`街道級別資訊的|其他欄位| |`city`|城市名稱| |`state`|狀態名稱。 這是自由格式欄位。| |`postalCode`|位置的郵遞區號。 並非所有國家都有郵遞區號。 在一些國家，這隻包含部分郵遞區號。| |`country`|政府管理的地區的名稱。 除 `xdm:countryCode`，這是一個自由格式欄位，可以使用任何語言使用國家/地區名稱。| |`shippingAmount`|客戶必須支付的發運金額。| |`billingAddress`|開單郵政地址| |`street1`|主要街道級別資訊、公寓編號、街道編號和街道名稱| |`street2`街道級別資訊的|其他欄位| |`city`|城市名稱| |`state`|狀態名稱。 這是自由格式欄位。| |`postalCode`|位置的郵遞區號。 並非所有國家都有郵遞區號。 在一些國家，這隻包含部分郵遞區號。| |`country`|政府管理的地區的名稱。 除 `xdm:countryCode`，這是一個自由格式欄位，可以使用任何語言使用國家/地區名稱。| |`personalEmail`|個人電子郵件地址| |`address`|RFC2822和後續標準中通常定義的技術地址，例如「name@domain.com」|

### 訂單已取消

| 說明 | XDM事件名稱 |
|---|---|
| 購物者取消訂單時觸發。 | `commerce.backofficeOrderCancelled` |

#### 從orderCanceled收集的資料

下表介紹了為此事件收集的資料。
|欄位|說明| |—| |`address`|技術地址，例如 `name@domain.com` 如RFC2822和後續標準中通常定義的| |`productListItems`|按順序排列的產品陣列| |`id`|此產品條目的行項目標識符。 產品本身通過 `product` 的子菜單。| |`name`|產品的顯示名稱或人可讀名稱| |`SKU`|庫存單位。 產品的唯一標識符。| |`quantity`|購物車中的產品數量| |`priceTotal`|產品行項目的總價格| |`discountAmount`|指示應用的折扣金額| |`order`|包含有關訂單|的資訊 |`purchaseID`|賣方為此採購或合同分配的唯一標識符。 無法保證ID是唯一| |`purchaseOrderNumber`|採購人為此採購或合同分配的唯一標識符| |`cancelDate`|購物者取消訂單的日期和時間| |`lastUpdatedDate`|特定訂單記錄上次在商業系統中更新的時間| |`personalEmail`|個人電子郵件地址| |`address`|RFC2822和後續標準中通常定義的技術地址，例如「name@domain.com」|

### creditMemoIssuted

| 說明 | XDM事件名稱 |
|---|---|
| 購物者在訂單中返回物料時觸發。 | `commerce.backofficeCreditMemoIssued` |

#### 從creditMemoIssuted收集的資料

下表介紹了為此事件收集的資料。
|欄位|說明| |—| |`address`|技術地址，例如 `name@domain.com` 如RFC2822和後續標準中通常定義的| |`productListItems`|按順序排列的產品陣列| |`id`|此產品條目的行項目標識符。 產品本身通過 `product` 的子菜單。| |`name`|產品的顯示名稱或人可讀名稱| |`SKU`|庫存單位。 產品的唯一標識符。| |`quantity`|購物車中的產品數量| |`priceTotal`|產品行項目的總價格| |`discountAmount`|指示應用的折扣金額| |`order`|包含有關訂單|的資訊 |`purchaseID`|賣方為此採購或合同分配的唯一標識符。 無法保證ID是唯一| |`purchaseOrderNumber`|採購人為此採購或合同分配的唯一標識符| |`lastUpdatedDate`|特定訂單記錄上次在商業系統中更新的時間| |`personalEmail`|個人電子郵件地址| |`address`|RFC2822和後續標準中通常定義的技術地址，例如「name@domain.com」|

### orderShipmentCompleted

| 說明 | XDM事件名稱 |
|---|---|
| 購物者在訂單中返回物料時觸發。 | `commerce.backofficeOrderShipmentCompleted` |

#### 從orderShipmentCompleted收集的資料

下表介紹了為此事件收集的資料。
|欄位|說明| |—| |`address`|技術地址，例如 `name@domain.com` 如RFC2822和後續標準中通常定義的| |`productListItems`|按順序排列的產品陣列| |`id`|此產品條目的行項目標識符。 產品本身通過 `product` 的子菜單。| |`name`|產品的顯示名稱或人可讀名稱| |`SKU`|庫存單位。 產品的唯一標識符。| |`quantity`|購物車中的產品數量| |`priceTotal`|產品行項目的總價格| |`discountAmount`|指示應用的折扣金額| |`order`|包含有關訂單|的資訊 |`purchaseID`|賣方為此採購或合同分配的唯一標識符。 無法保證ID是唯一| |`priceTotal`|已應用所有折扣和稅後此訂單的總價格| |`currencyCode`|用於訂單合計的ISO 4217幣種代碼| |`purchaseOrderNumber`|採購人為此採購或合同分配的唯一標識符| |`taxAmount`|採購員作為最終付款的一部分支付的稅額。| |`createdDate`|在商業系統中建立新訂單的時間和日期。 比如說， `2022-10-15T20:20:39+00:00`| |`payments`|此訂單的付款清單| |`paymentType`|此訂單的付款方式。 枚舉，允許自定義值。| |`currencyCode`| [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 此付款項使用的幣種代碼| |`paymentAmount`|付款值| |`shipping`|一個或多個產品的發運詳細資訊| |`shippingMethod`|客戶選擇的發運方法，如標準交貨、快速交貨、在商店提貨等| |`address`|實際發運地址| |`street1`|主要街道級別資訊、公寓編號、街道編號和街道名稱| |`street2`街道級別資訊的|其他欄位| |`city`|城市名稱| |`state`|狀態名稱。 這是自由格式欄位。| |`postalCode`|位置的郵遞區號。 並非所有國家都有郵遞區號。 在一些國家，這隻包含部分郵遞區號。| |`country`|政府管理的地區的名稱。 除 `xdm:countryCode`，這是一個自由格式欄位，可以使用任何語言使用國家/地區名稱。| |`shippingAmount`|客戶必須支付的發運金額。| |`address`|技術地址，例如 `name@domain.com` 如RFC2822和後續標準中通常定義的| |`billingAddress`|開單郵政地址| |`street1`|主要街道級別資訊、公寓編號、街道編號和街道名稱| |`street2`街道級別資訊的|其他欄位| |`city`|城市名稱| |`state`|狀態名稱。 這是自由格式欄位。| |`postalCode`|位置的郵遞區號。 並非所有國家都有郵遞區號。 在一些國家，這些資料只包含郵遞區號的一部分。| |`country`|政府管理的地區的名稱。 除 `xdm:countryCode`，這是一個自由格式欄位，可以使用任何語言使用國家/地區名稱。| |`personalEmail`|個人電子郵件地址| |`address`|RFC2822和後續標準中通常定義的技術地址，例如「name@domain.com」|
