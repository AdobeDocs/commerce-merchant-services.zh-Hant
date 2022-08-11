---
title: 使用Adobe Experience Platform標籤收集商業資料
description: 瞭解如何使用Adobe Experience Platform標籤收集Commerce資料。
exl-id: 852fc7d2-5a5f-4b09-8949-e9607a928b44
source-git-commit: 4af50842c883d3aef7bf50d6a68b82321b784591
workflow-type: tm+mt
source-wordcount: '2276'
ht-degree: 0%

---

# 使用Adobe Experience Platform標籤收集商業資料

雖然您可以使用Experience Platform連接器發佈和訂閱店面事件，但某些商家可能已在使用資料收集解決方案，如 [Adobe Experience Platform標籤](https://experienceleague.adobe.com/docs/platform-learn/data-collection/tags/create-a-property.html?lang=en)。 對於這些商家，Adobe Commerce在使用Adobe Commerce事件SDK的Experience Platform連接器中提供了僅發佈選項。

![Experience Platform連接器資料流](assets/tags-data-flow.png)
_Experience Platform連接器帶標籤的資料流_

在本主題中，您將學習如何將Experience Platform連接器提供的店面事件值映射到您已使用的Adobe Experience Platform標籤解決方案。

## 從Adobe Commerce收集事件資料

要收集Commerce事件資料，請執行以下操作：

- 安裝 [Adobe Commerce事件SDK](https://github.com/adobe/commerce-events/tree/main/packages/commerce-events-sdk)。 有關PHP店面，請參見 [安裝](install.md) 主題。 有關PWA Studio店面，請參閱 [PWA Studio指南](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/)。

   >[!NOTE]
   >
   > 做 **不** [配置](connect-data.md) 組織ID和資料流ID。

## 將Commerce儲存前端資料映射到Adobe Experience Platform

要將Commerce儲存前端資料映射到Adobe Experience Platform，請在Adobe Experience Platform標籤內配置和安裝以下內容：

1. [設定標籤屬性](https://experienceleague.adobe.com/docs/platform-learn/implement-in-websites/configure-tags/create-a-property.html?lang=en) 在Adobe Experience Platform資料收集中。

1. 下 **創作**&#x200B;選中 **擴展** 並安裝和配置以下擴展：

   - [Adobe客戶端資料層](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/adobe/client-data-layer/overview.html)

   - [Adobe Experience PlatformWeb SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/installing-the-sdk.html)

1. [發佈標籤](https://experienceleague.adobe.com/docs/experience-platform/tags/publish/overview.html) 發展環境。

1. 關注 **事件映射** 以下步驟為特定事件配置資料元素和規則。

### 事件映射

由於使用標籤的資料收集與使用Adobe Commerce事件SDK的資料收集不同，因此瞭解兩個框架中使用的等效術語非常重要。

| Adobe Experience Platform標籤術語 | Adobe Commerce事件SDK術語 |
|---|---|
| _資料元素_ | 上下文 |
| _規則_ | 事件 |
|  | _規則條件_  — 事件偵聽器（來自ACDL）<br><br>_規則操作_  — 事件處理程式(發送到Adobe Experience Platform) |

當您使用特定於Adobe Commerce的事件資料更新Adobe Experience Platform標籤中的資料元素和規則時，您將採取一些常見步驟。

例如，我們加上Adobe Commerce `signOut` 事件到Adobe Experience Platform標籤。 下面介紹的步驟（除您設定的特定值外）說明如何添加 [資料元素](https://experienceleague.adobe.com/docs/experience-platform/collection/e2e.html#data-element) 和 [規則](https://experienceleague.adobe.com/docs/experience-platform/collection/e2e.html#create-a-rule)，它適用於要添加到標籤的所有Adobe Commerce事件。

1. 建立資料元素：

   ![建立新資料元素](assets/create-new-data-elements.png)
   _建立新資料元素_

1. 設定 **名稱** 至 `sign out`。

1. 設定 **擴展** 至 `Adobe Experience Platform Web SDK`。

1. 設定 **資料元素類型** 至 `XDM object`。

1. 選擇 **沙盒** 和 **架構** 要更新的。

1. 下 **用戶帳戶** > **註銷**&#x200B;的子菜單。 **值** 在 **訪問者註銷** 至 `1`。

   ![更新註銷值](assets/signout-value.png)
   _更新註銷值_

1. 選擇 **保存**。

1. 建立規則：

   ![建立新規則](assets/create-new-rule.png)
   _建立新規則_

1. 選擇 **添加** 在 **事件**。

1. 設定 **擴展** 至 `Adobe Client Data Layer`。

1. 設定 **事件類型** 至 `Data Pushed`。

1. 選擇 **特定事件** 並設定 **要註冊的事件/密鑰** 至 `sign-out`。

1. 選擇 **保留更改** 的子菜單。

1. 添加操作。

1. 設定 **擴展** 至 `Adobe Experience Platform Web SDK`。

1. 設定 **操作類型** 至 `Send Event`。

1. 設定 **實例** 至 `Alloy`。

1. 設定 **類型** 至 `userAccount.logout`。

1. 設定 **XDM資料** 至 `%sign out%`。

1. 按一下 **保存**。

   在架構中為 `signOut` 來自Adobe Commerce。 此外，您還建立了一個規則，該規則具有在從Adobe Commerce店面觸發該事件時應執行的特定操作。

對下面描述的每個Adobe Commerce事件在標籤中重複上述步驟。

### 可用事件

對於以下每個事件，按照上述步驟將Adobe Commerce事件映射到XDM。

- [「註銷」](#signout)
- [「登錄」](#signin)
- [「createAccount」](#createaccount)
- [「編輯帳戶」](#editaccount)
- [「pageView」](#pageview)
- [「productView」](#productview)
- [「searchRequestSent」](#searchrequestsent)
- [「searchResponseReceived」](#searchresponsereceived)
- [「添加到購物車」](#addtocart)
- [「viewCart」](#viewcart)
- [「removeFromCart」](#removefromcart)
- [「initiateCheckout」](#initiatecheckout)
- [「placeOrder」](#placeorder)

### 註銷 {#signout}

#### 資料元素

建立以下資料元素：

1. 註銷：

   - **名稱**: `Sign out`
   - **擴展**: `Adobe Experience Platform Web SDK`
   - **資料元素類型**: `XDM object`
   - **欄位組**: `userAccount` > `logout`
   - **訪問者註銷**: **值** = `1`

#### 規則 

- **名稱**: `Sign out`
- **擴展**: `Adobe Client Data Layer`
- **事件類型**: `Data Pushed`
- **特定事件**: `sign-out`

##### 操作

- **擴展**: `Adobe Experience Platform Web SDK`
- **操作類型**: `Send event`
- **類型**: `userAccount.logout`
- **XDM資料**: `%sign-out%`

### 登錄 {#signin}

#### 資料元素

建立以下資料元素：

1. 帳戶電子郵件：

   - **名稱**: `account email`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑**: `accountContext.emailAddress`

1. 帳戶類型：

   - **名稱**: `account type`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑**: `accountContext.accountType`

1. 帳戶ID:

   - **名稱**: `account id`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑***: `accountContext.accountId`

1. 登錄：

   - **名稱**: `sign in`
   - **擴展**: `Adobe Experience Platform Web SDK`
   - **資料元素類型**: `XDM object`
   - **欄位組**: `person` > `accountID`
   - **帳戶ID**: **值** = `%account id%`
   - **欄位組**: `person` > `accountType`
   - **帳戶類型**: **值** = `%account type%`
   - **欄位組**: `person` > `personalEmailID`
   - **個人電子郵件地址**: **值** = `%account email%`
   - **欄位組**: `personalEmail` > `address`
   - **地址**: **值** = `%account email%`
   - **欄位組**: `userAccount` > `login`
   - **訪問者登錄**: **值** = `1`

#### 規則 

- **名稱**: `sign in`
- **擴展**: `Adobe Client Data Layer`
- **事件類型**: `Data Pushed`
- **特定事件**: `sign-in`

##### 操作

- **擴展**: `Adobe Experience Platform Web SDK`
- **操作類型**: `Send event`
- **類型**: `userAccount.login`
- **XDM資料**: `%sign in%`

### 建立帳戶 {#createaccount}

#### 資料元素

建立以下資料元素：

1. 帳戶電子郵件：

   - **名稱**: `account email`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑**: `accountContext.emailAddress`

1. 帳戶類型：

   - **名稱**: `account type`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑**: `accountContext.accountType`

1. 帳戶ID:

   - **名稱**: `account id`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑**: `accountContext.accountId`

1. 建立帳戶：

   - **名稱**: `Create account`
   - **擴展**: `Adobe Experience Platform Web SDK`
   - **資料元素類型**: `XDM object`
   - **欄位組**: `person` > `accountID`
   - **帳戶ID**: **值** = `%account id%`
   - **欄位組**: `person` > `accountType`
   - **帳戶類型**: **值** = `%account type%`
   - **欄位組**: `person` > `personalEmailID`
   - **個人電子郵件地址**: **值** = `%account email%`
   - **欄位組**: `personalEmail` > `address`
   - **地址**: **值** = `%account email%`
   - **欄位組**: `userAccount` > `createProfile`
   - **建立帳戶配置檔案**: **值** = `1`

#### 規則 

- **名稱**: `Create account`
- **擴展**: `Adobe Client Data Layer`
- **事件類型**: `Data Pushed`
- **特定事件**: `create-account`

##### 操作

- **擴展**: `Adobe Experience Platform Web SDK`
- **操作類型**: `Send event`
- **類型**: `userAccount.createProfile`
- **XDM資料**: `%create account%`

### 編輯帳戶 {#editaccount}

#### 資料元素

建立以下資料元素：

1. 帳戶電子郵件：

   - **名稱**: `account email`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑**: `accountContext.emailAddress`

1. 帳戶類型：

   - **名稱**: `account type`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑**: `accountContext.accountType`

1. 帳戶ID:

   - **名稱**: `account id`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑**: `accountContext.accountId`

1. 編輯帳戶：

   - **名稱**: `Edit account`
   - **擴展**: `Adobe Experience Platform Web SDK`
   - **資料元素類型**: `XDM object`
   - **欄位組**: `person` > `accountID`
   - **帳戶ID**: **值** = `%account id%`
   - **欄位組**: `person` > `accountType`
   - **帳戶類型**: **值** = `%account type%`
   - **欄位組**: `person` > `personalEmailID`
   - **個人電子郵件地址**: **值** = `%account email%`
   - **欄位組**: `personalEmail` > `address`
   - **地址**: **值** = `%account email%`
   - **欄位組**: `userAccount` > `updateProfile`
   - **建立帳戶配置檔案**: **值** = `1`

#### 規則

- **名稱**: `Edit account`
- **擴展**: `Adobe Client Data Layer`
- **事件類型**: `Data Pushed`
- **特定事件**: `edit-account`

##### 操作

- **擴展**: `Adobe Experience Platform Web SDK`
- **操作類型**: `Send event`
- **類型**: `userAccount.updateProfile`
- **XDM資料**: `%edit account%`

### 頁面視圖 {#pageview}

#### 資料元素

建立以下資料元素：

1. 頁名：

   - **名稱**: `page name`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑**: `pageContext.pageName`

#### 規則 

- **名稱**: `page view`
- **擴展**: `Adobe Client Data Layer`
- **事件類型**: `Data Pushed`
- **特定事件**: `page-view`

##### 操作

- **擴展**: `Adobe Experience Platform Web SDK`
- **操作類型**: `Send event`
- **類型**: `web.webPageDetails.pageViews`
- **XDM資料**: `%page view%`

### 產品視圖 {#productview}

#### 資料元素

建立以下資料元素：

1. 產品名稱：

   - **名稱**: `product name`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑**: `productContext.name`

1. 產品SKU:

   - **名稱**: `product sku`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑**: `productContext.sku`

1. 產品幣種：

   - **名稱**: `product currency`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑**: `productContext.pricing.currencyCode`

1. 幣種代碼：

   - **名稱**: `currency code`
   - **擴展**: `Core`
   - **資料元素類型**: `Custom Code`
   - **開啟編輯器**:

   ```bash
   return _satellite.getVar('product currency') || _satellite.getVar('storefront').storeViewCurrencyCode
   ```

1. 特價：

   - **名稱**: `special price`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑**: `productContext.pricing.specialPrice`

1. 常規價格：

   - **名稱**: `regular price`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑**: `productContext.pricing.regularPrice`

1. 產品價格：

   - **名稱**: `product price`
   - **擴展**: `Core`
   - **資料元素類型**: `Custom Code`
   - **開啟編輯器**:

   ```bash
   return _satellite.getVar('product regular price') || _satellite.getVar('product special price')
   ```

1. 產品視圖：

   - **名稱**: `product view`
   - **擴展**: `Adobe Experience Platform Web SDK`
   - **資料元素類型**: `XDM object`
   - **欄位組**: `productListItems`。 選擇 **提供單個項目** 並按一下 **添加項** 按鈕 因為此視圖是用於PDP的，所以可以用單個項填充。
   - **欄位組**: `productListItems` > `name`
   - **名稱**: **值** = `%product name%`
   - **欄位組**: `productListItems` > `SKU`
   - **SKU**: **值** = `%product sku%`
   - **欄位組**: `productListItems` > `priceTotal`
   - **價格合計**: **值** = `%product price%`
   - **欄位組**: `productListItems` > `currencyCode`
   - **幣種代碼**: **值** = `%currency code%`
   - **欄位組**: `commerce` > `productViews` > `value`
   - **值**: **值** = `1`

#### 規則 

- **名稱**: `product view`
- **擴展**: `Adobe Client Data Layer`
- **事件類型**: `Data Pushed`
- **特定事件**: `product-page-view`

##### 操作

- **擴展**: `Adobe Experience Platform Web SDK`
- **操作類型**: `Send event`
- **類型**: `commerce.productViews`
- **XDM資料**: `%product view%`

### searchRequestSent {#searchrequestsent}

#### 資料元素

建立以下資料元素：

1. 搜索輸入

   - **名稱**: `search input`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑**: `searchInputContext.units[0]`

1. 搜索輸入短語

   - **名稱**: `search input phrase`
   - **擴展**: `Core`
   - **資料元素類型**: `Custom Code`
   - **開啟編輯器**:

   ```bash
   return _satellite.getVar('search input').phrase;
   ```

1. 搜索輸入排序

   - **名稱**: `search input sort`
   - **擴展**: `Core`
   - **資料元素類型**: `Custom Code`
   - **開啟編輯器**:

   ```bash
   const searchInput = _satellite.getVar('search input');
   const sortFromInput = searchInput ? searchInput.sort : [];
   const sort = sortFromInput.map((searchSort) => {
       return {
           attribute: searchSort.attribute,
           order: searchSort.direction,
       };
   });
   return sort;
   ```

1. 搜索輸入篩選器

   - **名稱**: `search input filters`
   - **擴展**: `Core`
   - **資料元素類型**: `Custom Code`
   - **開啟編輯器**:

   ```bash
   const searchInput = _satellite.getVar('search input');
   const filtersFromInput = searchInput ? searchInput.filter : [];
   const filters = filtersFromInput.map(
       (searchFilter) => {
           let value = [];
           let isRange = false;
           if (searchFilter.eq) {
               value.push(searchFilter.eq);
           } else if (searchFilter.in) {
               value = searchFilter.in;
           } else if (searchFilter.range) {
               isRange = true;
               value.push(String(searchFilter.range.from));
               value.push(String(searchFilter.range.to));
           }
           return {
               attribute: searchFilter.attribute,
               value,
               isRange,
           };
       }
   );
   
   return filters;
   ```

1. 搜索請求：

   - **名稱**: `search request`
   - **擴展**: `Adobe Experience Platform Web SDK`
   - **資料元素類型**: `XDM object`
   - **欄位組**: `siteSearch` > `phrase`
   - **值**:尚未提供
   - **欄位組**: `siteSearch` > `sort`。 選擇 **提供整個對象**。
   - **欄位組**: `siteSearch` > `filter`。 選擇 **提供整個對象**。
   - **欄位組**: `searchRequest` > `value`
   - **值**: **值** = `1`

#### 規則 

- **名稱**: `search request sent`
- **擴展**: `Adobe Client Data Layer`
- **事件類型**: `Data Pushed`
- **特定事件**: `search-request-sent`

##### 操作

- **擴展**: `Adobe Experience Platform Web SDK`
- **操作類型**: `Send event`
- **類型**: `searchRequest`
- **XDM資料**: `%search request%`

### searchResponseReceived {#searchresponsereceived}

#### 資料元素

建立以下資料元素：

1. 搜索結果：

   - **名稱**: `search results`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑**: `searchResultsContext.units[0]`

1. 產品的搜索結果數：

   - **名稱**: `search result number of products`
   - **擴展**: `Core`
   - **資料元素類型**: `Custom Code`
   - **開啟編輯器**:

   ```bash
   return _satellite.getVar('search result').products.length;
   ```

1. 搜索結果產品：

   - **名稱**: `search result products`
   - **擴展**: `Core`
   - **資料元素類型**: `Custom Code`
   - **開啟編輯器**:

   ```bash
   const searchResult = _satellite.getVar('search result');
   const productsFromResult = searchResult.products ? searchResult.products : [];
   const products = productsFromResult.map(
       (product) => {
           return { SKU: product.sku, name: product.name };
       }
   );
   return products;
   ```

1. 搜索結果建議：

   - **名稱**: `search result products`
   - **擴展**: `Core`
   - **資料元素類型**: `Custom Code`
   - **開啟編輯器**:

   ```bash
   const searchResult = _satellite.getVar('search result');
   const suggestionsFromResult = searchResult.suggestions ? searchResult.suggestions : [];
   const suggestions = suggestionsFromResult.map((suggestion) => suggestion.suggestion);
   return suggestions;
   ```

1. 搜索響應：

   - **名稱**: `search response`
   - **擴展**: `Adobe Experience Platform Web SDK`
   - **資料元素類型**: `XDM object`
   - **欄位組**: `siteSearch` > `suggestions`。 選擇 **提供整個對象**。
   - **資料元素**: `%search result suggestions%`
   - **欄位組**: `siteSearch` > `numberOfResults`
   - **值**: `%search result number of products%`
   - **欄位組**: `productListItems`。 選擇 **提供整個對象**。
   - **資料元素**: `%search result products%`
   - **欄位組**: `searchResponse` > `value`
   - **值**: **值** = `1`

#### 規則 

- **名稱**: `search response received`
- **擴展**: `Adobe Client Data Layer`
- **事件類型**: `Data Pushed`
- **特定事件**: `search-response-received`

##### 操作

- **擴展**: `Adobe Experience Platform Web SDK`
- **操作類型**: `Send event`
- **類型**: `searchResponse`
- **XDM資料**: `%search response%`

### 添加到購物車 {#addtocart}

#### 資料元素

建立以下資料元素：

1. 產品名稱：

   - **名稱**: `product name`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑**: `productContext.name`

1. 產品sku:

   - **名稱**: `product sku`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑**: `productContext.sku`

1. 幣種代碼：

   - **名稱**: `currency code`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑**: `productContext.pricing.currencyCode`

1. 產品特價：

   - **名稱**: `product special price`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑**: `productContext.pricing.specialPrice`

1. 產品定價：

   - **名稱**: `product regular price`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑**: `productContext.pricing.regularPrice`

1. 產品價格：

   - **名稱**: `product price`
   - **擴展**: `Core`
   - **資料元素類型**: `Custom Code`
   - **開啟編輯器**:

   ```bash
   return _satellite.getVar('product regular price') || _satellite.getVar('product special price') 
   ```

1. 購物車：

   - **名稱**: `cart`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑**: `shoppingCartContext`

1. 購物車ID:

   - **名稱**: `cart id`
   - **擴展**: `Core`
   - **資料元素類型**: `Custom Code`
   - **開啟編輯器**:

   ```bash
   return _satellite.getVar('cart').id
   ```

1. 添加到購物車：

   - **名稱**: `add to cart`
   - **擴展**: `Adobe Experience Platform Web SDK`
   - **資料元素類型**: `XDM object`
   - **欄位組**: `productListItems`。 選擇 **提供單個項目** 並按一下 **添加項** 按鈕 因為此視圖是用於PDP的，所以可以用單個項填充。
   - **欄位組**: `productListItems` > `name`
   - **名稱**: **值** = `%product name%`
   - **欄位組**: `productListItems` > `SKU`
   - **SKU**: **值** = `%product sku%`
   - **欄位組**: `productListItems` > `priceTotal`
   - **價格合計**: **值** = `%product price%`
   - **欄位組**: `productListItems` > `currencyCode`
   - **幣種代碼**: **值** = `%currency code%`
   - **欄位組**: `commerce` > `cart` > `cartID`
   - **購物車ID**: **值** = `%cart id%`
   - **欄位組**: `commerce` > `productListAdds` > `value`
   - **值**: **值** = `1`

#### 規則 

- **名稱**: `add to cart`
- **擴展**: `Adobe Client Data Layer`
- **事件類型**: `Data Pushed`
- **特定事件**: `add-to-cart`

##### 操作

- **擴展**: `Adobe Experience Platform Web SDK`
- **操作類型**: `Send event`
- **類型**: `commerce.productListAdds`
- **XDM資料**: `%add to cart%`

### 視圖購物車 {#viewcart}

#### 資料元素

建立以下資料元素：

1. 店面：

   - **名稱**: `storefront`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑**: `storefrontInstanceContext`

1. 購物車：

   - **名稱**: `cart`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑**: `shoppingCartContext`

1. 購物車ID:

   - **名稱**: `cart id`
   - **擴展**: `Core`
   - **資料元素類型**: `Custom Code`
   - **開啟編輯器**:

   ```bash
   return _satellite.getVar('cart').id
   ```

1. 產品清單項：

   - **名稱**: `product list items:`
   - **擴展**: `Core`
   - **資料元素類型**: `Custom Code`
   - **開啟編輯器**:

   ```bash
   const storefrontContext = _satellite.getVar('storefront');
   const cart = _satellite.getVar('cart');
   
   const returnList = [];
   cart.items.forEach(item => {
       const selectedOptions = [];
       item.configurableOptions?.forEach(option => {
           selectedOptions.push({
               attribute: option.optionLabel,
               value: option.valueLabel,
           });
       });
   
       const productListItem = {
           SKU: item.product.sku,
           name: item.product.name,
           quantity: item.quantity,
           priceTotal: item.prices.price.value * item.quantity,
           currencyCode: item.prices.price.currency ? item.prices.price.currency : storefrontContext.storeViewCurrencyCode,
           selectedOptions: selectedOptions,
       };
   
       returnList.push(productListItem);
   });
   return returnList;
   ```

1. 查看購物車：

   - **名稱**: `view cart`
   - **擴展**: `Adobe Experience Platform Web SDK`
   - **資料元素類型**: `XDM object`
   - **欄位組**: `productListItems`。 對於 `productListItems`，可能有多個預計算項。 選擇 **productListItems** > **填充整個陣列**。
   - **資料元素**: `%product list items%`
   - **欄位組**: `commerce` > `cart` > `cartID`
   - **購物車ID**: **值** = `%cart id%`
   - **欄位組**: `commerce` > `productListViews` > `value`
   - **值**: **值** = `1`

#### 規則 

- **名稱**: `view cart`
- **擴展**: `Adobe Client Data Layer`
- **事件類型**: `Data Pushed`
- **特定事件**: `shopping-cart-view`

##### 操作

- **擴展**: `Adobe Experience Platform Web SDK`
- **操作類型**: `Send event`
- **類型**: `commerce.productListViews`
- **XDM資料**: `%view cart%`

### 刪除自購物車 {#removefromcart}

#### 資料元素

建立以下資料元素：

1. 產品名稱：

   - **名稱**: `product name`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑**: `productContext.name`

1. 產品sku:

   - **名稱**: `product sku`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑**: `productContext.sku`

1. 幣種代碼：

   - **名稱**: `currency code`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑**: `productContext.pricing.currencyCode`

1. 產品特價：

   - **名稱**: `product special price`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑**: `productContext.pricing.specialPrice`

1. 產品定價：

   - **名稱**: `product regular price`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑**: `productContext.pricing.regularPrice`

1. 產品價格：

   - **名稱**: `product price`
   - **擴展**: `Core`
   - **資料元素類型**: `Custom Code`
   - **開啟編輯器**:

   ```bash
   return _satellite.getVar('product regular price') || _satellite.getVar('product special price') 
   ```

1. 購物車：

   - **名稱**: `cart`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑**: `shoppingCartContext`

1. 購物車ID:

   - **名稱**: `cart id`
   - **擴展**: `Core`
   - **資料元素類型**: `Custom Code`
   - **開啟編輯器**:

   ```bash
   return _satellite.getVar('cart').id
   ```

1. 從購物車中刪除：

   - **名稱**: `remove from cart`
   - **擴展**: `Adobe Experience Platform Web SDK`
   - **資料元素類型**: `XDM object`
   - **欄位組**: `productListItems`。 選擇 **提供單個項目** 並按一下 **添加項** 按鈕 因為此視圖是用於PDP的，所以可以用單個項填充。
   - **欄位組**: `productListItems` > `name`
   - **名稱**: **值** = `%product name%`
   - **欄位組**: `productListItems` > `SKU`
   - **SKU**: **值** = `%product sku%`
   - **欄位組**: `productListItems` > `priceTotal`
   - **價格合計**: **值** = `%product price%`
   - **欄位組**: `productListItems` > `currencyCode`
   - **幣種代碼**: **值** = `%currency code%`
   - **欄位組**: `commerce` > `cart` > `cartID`
   - **購物車ID**: **值** = `%cart id%`
   - **欄位組**: `commerce` > `productListRemovals` > `value`
   - **值**: **值** = `1`

#### 規則 

- **名稱**: `remove from cart`
- **擴展**: `Adobe Client Data Layer`
- **事件類型**: `Data Pushed`
- **特定事件**: `remove-from-cart`

##### 操作

- **擴展**: `Adobe Experience Platform Web SDK`
- **操作類型**: `Send event`
- **類型**: `commerce.productListRemovals`
- **XDM資料**: `%remove from cart%`

### 啟動簽出 {#initiatecheckout}

#### 資料元素

建立以下資料元素：

1. 店面：

   - **名稱**: `storefront`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑**: `storefrontInstanceContext`

1. 購物車：

   - **名稱**: `cart`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑**: `shoppingCartContext`

1. 購物車ID:

   - **名稱**: `cart id`
   - **擴展**: `Core`
   - **資料元素類型**: `Custom Code`
   - **開啟編輯器**:

   ```bash
   return _satellite.getVar('cart').id
   ```

1. 產品清單項：

   - **名稱**: `product list items`
   - **擴展**: `Core`
   - **資料元素類型**: `Custom Code`
   - **開啟編輯器**:

   ```bash
   const storefrontContext = _satellite.getVar('storefront');
   const cart = _satellite.getVar('cart');
   
   const returnList = [];
   cart.items.forEach(item => {
       const selectedOptions = [];
       item.configurableOptions?.forEach(option => {
           selectedOptions.push({
               attribute: option.optionLabel,
               value: option.valueLabel,
           });
       });
   
       const productListItem = {
           SKU: item.product.sku,
           name: item.product.name,
           quantity: item.quantity,
           priceTotal: item.prices.price.value * item.quantity,
           currencyCode: item.prices.price.currency ? item.prices.price.currency : storefrontContext.storeViewCurrencyCode,
           selectedOptions: selectedOptions,
       };
   
       returnList.push(productListItem);
   });
   return returnList;
   ```

1. 啟動簽出：

   - **名稱**: `initiate checkout`
   - **擴展**: `Adobe Experience Platform Web SDK`
   - **資料元素類型**: `XDM object`
   - **欄位組**: `productListItems`。 對於 `productListItems`，可能有多個預計算項。 選擇 **productListItems** > **填充整個陣列**。
   - **資料元素**: `%product list items%`
   - **欄位組**: `commerce` > `cart` > `cartID`
   - **購物車ID**: **值** = `%cart id%`
   - **欄位組**: `commerce` > `checkouts` > `value`
   - **值**: **值** = `1`

#### 規則 

- **名稱**: `initiate checkout`
- **擴展**: `Adobe Client Data Layer`
- **事件類型**: `Data Pushed`
- **特定事件**: `initiate-checkout`

##### 操作

- **擴展**: `Adobe Experience Platform Web SDK`
- **操作類型**: `Send event`
- **類型**: `commerce.checkouts`
- **XDM資料**: `%initiate checkout%`

### 訂單 {#placeorder}

#### 資料元素

建立以下資料元素：

1. 店面：

   - **名稱**: `storefront`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑**: `storefrontInstanceContext`

1. 購物車：

   - **名稱**: `cart`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑**: `shoppingCartContext`

1. 購物車ID:

   - **名稱**: `cart id`
   - **擴展**: `Core`
   - **資料元素類型**: `Custom Code`
   - **開啟編輯器**:

   ```bash
   return _satellite.getVar('cart').id
   ```

1. 順序：

   - **名稱**: `order`
   - **擴展**: `Adobe Client Data Layer`
   - **資料元素類型**: `Data Layer Computed State`
   - **[可選] 路徑**: `orderContext`

1. 商業訂單：

   - **名稱**: `commerce order`
   - **擴展**: `Core`
   - **資料元素類型**: `Custom Code`
   - **開啟編輯器**:

   ```bash
   const order = _satellite.getVar('order');
   const storefront = _satellite.getVar('storefront');
   
   if (order.payments && order.payments.length) {
       payments = order.payments.map(payment => {
           return {
               paymentAmount: payment.total,
               paymentType: payment.paymentMethodCode,
               transactionID: order.orderId.toString(),
           };
       });
   } else {
       payments = [
           {
               paymentAmount: order.grandTotal,
               paymentType: order.paymentMethodCode,
               transactionID: order.orderId.toString(),
           },
       ];
   }
   
   return {
       purchaseID: order.orderId.toString(),
       currencyCode: storefront.storeViewCurrencyCode,
       payments,
   };
   ```

1. 訂單發運：

   - **名稱**: `order shipping`
   - **擴展**: `Core`
   - **資料元素類型**: `Custom Code`
   - **開啟編輯器**:

   ```bash
   const order = _satellite.getVar('order');
   return {
       shippingMethod: order.shipping.shippingMethod,
       shippingAmount: order.shipping.shippingAmount || 0,
   }
   ```

1. 升級ID:

   - **名稱**: `promotion id`
   - **擴展**: `Core`
   - **資料元素類型**: `Custom Code`
   - **開啟編輯器**:

   ```bash
   return _satellite.getVar('order').appliedCouponCode
   ```

1. 產品清單項：

   - **名稱**: `product list items`
   - **擴展**: `Core`
   - **資料元素類型**: `Custom Code`
   - **開啟編輯器**:

   ```bash
   const storefrontContext = _satellite.getVar('storefront');
   const cart = _satellite.getVar('cart');
   
   const returnList = [];
   cart.items.forEach(item => {
       const selectedOptions = [];
       item.configurableOptions?.forEach(option => {
           selectedOptions.push({
               attribute: option.optionLabel,
               value: option.valueLabel,
           });
       });
   
       const productListItem = {
           SKU: item.product.sku,
           name: item.product.name,
           quantity: item.quantity,
           priceTotal: item.prices.price.value * item.quantity,
           currencyCode: item.prices.price.currency ? item.prices.price.currency : storefrontContext.storeViewCurrencyCode,
           selectedOptions: selectedOptions,
       };
   
       returnList.push(productListItem);
   });
   return returnList;
   ```

1. 下單：

   - **名稱**: `place order`
   - **擴展**: `Adobe Experience Platform Web SDK`
   - **資料元素類型**: `XDM object`
   - **欄位組**: `productListItems`。 對於 `productListItems`，可能有多個預計算項。 選擇 **productListItems** > **填充整個陣列**。
   - **資料元素**: `%product list items%`
   - **欄位組**: `commerce` > `order`
   - **唯一標識符**: **值** = `%commerce order%`
   - **欄位組**: `commerce` > `shipping`
   - **唯一標識符**: **值** = `%order shipping%`
   - **欄位組**: `commerce` > `promotionID`
   - **升級ID**: **值** = `%promotion id%`
   - **欄位組**: `commerce` > `purchases` > `value`
   - **值**: **值** = `1`

#### 規則 

- **名稱**: `place order`
- **擴展**: `Adobe Client Data Layer`
- **事件類型**: `Data Pushed`
- **特定事件**: `place-order`

##### 操作

- **擴展**: `Adobe Experience Platform Web SDK`
- **操作類型**: `Send event`
- **類型**: `commerce.order`
- **XDM資料**: `%place order%`

## 設定標識

Experience Platform連接器簡檔是根據 `personID` 和 `personalEmail` XDM體驗事件中的標識欄位。 

如果您以前有依賴於不同欄位的設定，則可以繼續使用這些欄位。 要設定Experience Platform連接器配置檔案標識欄位，必須設定以下欄位：

- `personalEmail`  — 僅限客戶事件 — 按照上述步驟處理客戶事件
- `personID`  — 所有其他事件：

   - 如果您已捕獲 `ECID` 在標籤中，您可以 `personID` 所有Adobe Experience PlatformWeb SDK規則 `%ECID%`。
   - 捕獲 `ECID` 在標籤中，必須添加 **自定義代碼** 按照以下步驟對發送事件規則執行操作 [標籤文檔](https://experienceleague.adobe.com/docs/experience-platform/edge/extension/accessing-the-ecid.html)。 請參見下面的示例。

### 示例

以下影像顯示了如何配置 `pageView` 事件 `personID` 在Experience Platform連接器中：

1. 為ECID配置自定義代碼的資料元素：

   ![使用自定義代碼配置資料元素](assets/set-custom-code-ecid.png)
   _使用自定義代碼配置資料元素_

1. 添加ECID自定義代碼：

   ![在資料元素中設定ECID的代碼](assets/code-to-set-ecid.png)
   _在資料元素中設定ECID的代碼_

1. 將personID設定為ECID的XDM架構更新：

   ![將personID設定為ECID](assets/set-personid-as-ecid.png)
   _將personID設定為ECID_

1. 定義檢索ECID的規則操作：

   ![檢索ECID](assets/rule-retrieve-ecid.png)
   _檢索ECID_

## 設定同意

Adobe Commerce和Experience Platform連接器資料收集許可預設啟用。 通過 [`mg_dnt` 餅](https://docs.magento.com/user-guide/stores/cookie-reference.html)。 如果您選擇使用 `mg_dnt` 管理同意。 的 [Adobe Experience PlatformWeb SDK文檔](https://experienceleague.adobe.com/docs/experience-platform/edge/consent/supporting-consent.html?lang=en) 還有幾個管理同意的選項。

1. 建立 **核心自定義代碼** 資料元素(`%do not track cookie%`) `mg_dnt` cookie:

   ![建立不跟蹤資料元素](assets/element-dnt-cookie.png)
   _建立不跟蹤資料元素_

1. 建立 **核心自定義代碼** 資料元素(`%consent%`)返回 `out` 如果設定了cookie和 `in` 否則：

   ![建立同意資料元素](assets/element-consent-dnt-cookie.png)
   _建立同意資料元素_

1. 配置Adobe Experience PlatformWeb SDK擴展 `%consent%` 資料元素：

   ![經同意更新SDK](assets/config-sdk-consent.png)
   _經同意更新SDK_

## 警告

- 未執行關閉Experience Platform收集的步驟，導致事件重複計數
- 不設定本主題中所述的映射/事件會影響Adobe Analytics主板
- 如果禁用了資料收集，則無法通過Experience Platform連接器設定目標
