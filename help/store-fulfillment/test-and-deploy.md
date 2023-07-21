---
title: 測試並部署商店履行
description: 測試計畫，以驗證「商店履行」功能。 測試包含「存貨同步API」、已取消訂單的端對端履行工作流程、「商店履行」應用程式使用者管理，以及「客戶簽到」體驗。
role: User, Admin
level: Intermediate
feature: Shipping/Delivery, User Account, Roles/Permissions
exl-id: 77285a66-5161-407b-94cd-b3f412d7949d
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '2660'
ht-degree: 0%

---

# 測試並部署Adobe Commerce的商店履行

在開發環境中完成入門流程後，您可以開始該流程，以測試並將Store Fulfillment解決方案部署到生產環境。

**必要條件**

在測試或同步任何資訊、商店或訂單之前，請確認您已完成下列工作：

- 已完成 [一般設定](enable-general.md) 用於「商店履行」服務。

- [新增並驗證您的沙箱和生產環境的帳戶憑證和連線詳細資料](connect-set-up-service.md#configure-store-fulfillment-account-credentials)

- 確認 [Adobe Commerce整合](connect-set-up-service.md#configure-store-fulfillment-account-credentials) 適用於Store Fulfillment解決方案，現可提供並獲授權。

## 準備測試

必須先完成連線設定，然後才能建立任何測試訂單或執行整合測試。 在測試之前，您也必須確認您的存放區資料已同步。

1. 同步化商店履行來源。

   - 前往 **[!UICONTROL Stores > Sources]**.

   - 選取 **[!UICONTROL Synchronize Store Fulfillment Sources]**.

1. 從商店格線，確認商店已標示為 `Synced` 建立測試訂單之前。

## 範例測試計畫

零售商會在部署的設定和測試階段驗證Store Fulfillment解決方案的基本功能。 此範例測試計畫提供測試的起點。 根據您的需求新增其他案例。

>[!NOTE]
>
>完成Store Fulfillment解決方案的初始入門或更新現有安裝後，在部署到生產環境之前，請務必在非生產環境中測試應用程式。

此範例測試計畫涵蓋下列功能區域：

| 功能區域 | 函式 | 角色 |
|-------------------------------------|------------------------------------------|----------------------------------|
| 存貨與訂單同步化 | 詳細目錄API同步 | Adobe Commerce管理員 |
| 端對端 | 訂單取消工作流程 | 客戶、管理員、商店關聯 |
| 管理員 | Store Fulfillment應用程式許可權 | 管理員 |
| Adobe Commerce前端 | 產品型別 | 客戶、管理員 |
| 前端結帳</br>簽入表單 | 簽入體驗 | 客戶、管理員 |
| 商店協助應用程式 | 訂購</br>選取</br>階段</br>和移交 | 存放區關聯 |

### 詳細目錄API同步

測試計畫的這個區段涵蓋存貨與訂單同步化，以確認取貨來源與存貨的更新在Adobe Commerce與「商店履行」解決方案之間已正確同步。

**功能區域**：存貨與訂單同步化</br>
**角色：** 管理員</br>
**測試型別：** 全部正面

<table>
<thead>
<tr>
<th>函式</th>
<th>測試案例</th>
<th>預期結果</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>新增取貨庫存來源</strong></td>
<td>儲存新的撿料庫存來源。</td>
<td>即時同步會在5分鐘內將來源詳細資料傳送至WalmartGIF服務。</td>
</tr>
<tr>
<td><strong>更新現有的取貨存量來源</strong></td>
<td>將更新儲存至現有的取貨庫存來源。</td>
<td>即時同步作業會在5分鐘內將詳細資料傳送至WalmartGIF</td>
</tr>
<tr>
<td><strong>取貨庫存來源</br><code>Is Synced</code> 狀態</strong></td>
<td>將更新儲存至現有的取貨庫存來源。</td>
<td>成功操作後， <code>Is Synced</code> 「管理來源」頁面更新的資料欄 <code>No</code> 至 <code>Yes</code>.</td>
</tr>
<tr>
<td><strong>已修改的庫存預留程式</strong></td>
<td>建立並提交產品的新訂單。</td>
<td>產品的可銷售數量會相應減少。</td>
</tr>
<tr>
<td><strong>新訂單推送、API同步 — 客戶訂單</strong></td>
<td>客戶提交商店取貨訂單。</td>
<td><ul><li>在「管理訂單」檢視中， <strong>Adobe Commerce管理員使用者</strong> 訂單同步狀態已更新至 <code>Sent</code></li><li>訂單詳細資訊記錄包含訊息 <code>Order was sent to BOPIS solution for sync, it's not yet acknowledged yet.</code></li></ul></td>
</tr>
<tr>
<td><strong>新訂單推送、API同步 — 管理員提交訂單</strong></td>
<td>Adobe Commerce <strong>管理員</strong> 提交取貨單。</td>
<td><ul><li>在「管理訂單」檢視中，「訂單同步」狀態會更新為 <code>Sent</code>.</li><li>訂單詳細資訊記錄包含訊息 <code>Order was sent to BOPIS solution for sync, it's not yet acknowledged yet.</code></li></ul></td>
</tr>
<tr>
<td><strong>新訂單推送，例外狀況佇列<strong></td>
<td>識別Adobe Commerce Admin中可透過Adobe Commerce完成的多項虛擬及可下載產品，不需與Fulfillment服務(FaaS)互動。</td>
<td>這些產品在匯出時會適當地移除或標幟，以防止下游與FaaS衝突。</td>
</tr>
</tbody>
</table>

### 訂單取消工作流程

測試計畫的這個部分包含測試透過Adobe Commerce取消的訂單的端對端工作流程的情況。

**功能區域：** Adobe Commerce管理員</br>
**角色：** 端對端（管理員、商店夥伴、客戶）</br>
**測試結果型別：** 所有情境皆為正數

<table style="table-layout:fixed">
<tr>
<th>函式</th>
<th>情境</th>
<th>預期結果</th>
</tr>
<tr>
<td><strong>完整訂單取消</strong></td>
<td><ol>
<li>下訂單。</li>
<li>等候順序同步完成。</li>
<li>驗證商業發票電子郵件的收據建立（若已授權並擷取）。</li>
<li>從「商業發票」檢視建立包含所有已訂購產品的「銷退折讓單」。</li>
</ol>
</td>
<td>
<ul>
<li>訂單歷史記錄已更新 <code>We refunded $X online. Transaction ID: transactionID</code> 和 <code>Received Cancel acknowledgment from the BOPIS solution.</code></li>
<li>訂單狀態為 <code>Closed</code>. （我們已設定「立即付款稽核」。）</li>
<li>在Adobe Commerce中建立的銷退折讓單。 （等到cron運作為止。）</li>
<li>若已撿料所有料號，則準備好接收電子郵件 <code>DISPLAY COMMENT HISTORY</code> 顯示 <code>Order is ready for pickup</code> (<code>CUSTOMER NOTIFIED</code> 標幟為 <code>true</code>.)</li>
<li>如果所有料號均未撿料，則會顯示取消電子郵件與顯示註解歷史記錄 <code>Order has been canceled - all items were not available</code></li>
<li><code>CUSTOMER NOTIFIED</code> 標幟為 <code>true</code>.)</li>
</ul>
</td>
</tr>
<tr><td><strong>部分訂單取消<strong></td>
<td>
<ol>
<li>訂購至少兩種產品。</li>
<li>等候順序同步完成。</li>
<li>檢查是否已建立發票（如果授權並擷取）以及是否收到發票電子郵件。</li>
<li>等候兩小時進行交易結算。</li>
<li>從「商業發票」檢視建立僅含部分訂購產品的「銷退折讓單」。</li>
</td>
<td>
<ul>
<li>訂單歷史記錄更新： <code>We refunded $X online. Transaction ID: transactionID</code></li>
<li>訂單歷史記錄更新： <code>Order notified as partly canceled at: Date and Hour</code></li>
<li>收到訂單退款電子郵件： <code>$x amount was refunded</code></li>
<li>訂單狀態為 <code>Processing</code>.</li>
<li>在Adobe Commerce中建立的銷退折讓單（等到cron運作為止）。</li>
<li>如果未撿料某些料號，請確認 [!UICONTROL Ready for Pickup] 顯示nil pick or refust區段的電子郵件。 <code>DISPLAY COMMENT HISTORY</code> 顯示 <code>Order is ready for pickup, but some items not available.</code>.</li>
<li><code>CUSTOMER NOTIFIED</code> 標幟為 <code>true</code>.</li>
</ul>
</td>
</tr>
<td><strong>準備取車</br></br>完全取消</br>（所有產品都設定為0數量挑庫）</strong></td>
<td>
<ol>
<li>下訂單。</li>
<li>等候順序同步完成。</li>
<li>檢查是否已建立發票（如果授權並擷取）以及是否收到發票電子郵件。</li>
<li>前往Postman並執行「準備好取貨」請求，將所有產品設定為 <code>picked</code> 替換為 <code>0 qty</code>.</li>
</ol>
</td>
<td>
<ul>
<li>已更新訂單歷史記錄： <code>We refunded $X offline</code></li>
<li>訂單狀態為 <code>CLOSED</code>.
<li>已建立銷退折讓單。 （等到cron運作為止。）</li>
<li>已收到退款電子郵件： <code>$x amount was refunded</code></li>
<li>訂單取消電子郵件已傳送。</li>
</ul>
</td>
</tr>
<tr>
<td><strong>準備取貨 — 部分取消</strong></br></br><strong>(部分產品已撿料，部分產品則使用下列方式撿料 <code>0 qty</code>)</strong>
</td>
<td>
<ol>
<li>下訂單。</li>
<li>等候順序同步完成。</li>
<li>檢查是否已建立發票（如果授權並擷取）以及是否收到發票電子郵件。</li>
<li>移至Postman，執行「準備取貨」請求，將部份產品設定為「已撿料」且數量為0，其餘則已撿料。</li>
</ol>
</td>
<td>
<ul>
<li><code>Your order is ready for pickup</code> 替換為 [!UICONTROL Ready for Pickup Items] 和 [!UICONTROL Canceled Items] 表格。 </li>
<li>訂單狀態為準備取貨。 </li>
<li>已更新訂單歷史記錄： <code>We refunded $X offline.</code>
<li>已更新訂單歷史記錄： <code>Order notified as partly canceled at: Date and hour</code>
<li>已收到退款電子郵件： <code>$x amount was refunded</code>
<li>已建立銷退折讓單。 （等到cron運作為止。）</li>
</ul>
</td>
</tr>
<tr>
<td><strong>準備取貨 — 部分取消</br></br>部分產品已撿料，部分產品則使用下列方式撿料 <code>0 qty</code>)</strong>
</td>
<td><ol>
<li>下訂單。</li>
<li>等候順序同步完成。</li>
<li>檢查是否已建立發票（如果授權並擷取）以及是否收到發票電子郵件。</li>
<li>移至Postman，執行「準備取貨」請求，將部份產品設定為「已撿料」且數量為0，其餘則已撿料。</li>
</ol>
</td>
<td><ul>
<li><code>Your order is ready for pickup</code> 替換為 [!UICONTROL Ready for Pickup Items] 和 [!UICONTROL Canceled Items] 表格。 </li>
<li>訂單狀態為準備取貨。 </li>
<li>已更新訂單歷史記錄： <code>We refunded $X offline.</code>
<li>已更新訂單歷史記錄： <code>Order notified as partly canceled at: Date and hour</code>
<li>已收到退款電子郵件： <code>$x amount was refunded</code>
<li>已建立銷退折讓單。 （等到cron運作為止。）</li>
</ul>
</td>
</tr>
<tr>
<td><strong>分配（分配期間） </br></br>完全取消（將所有產品設定為已拒絕）</strong>
</td>
<td>
<ol>
<li>下訂單。</li>
<li>等候順序同步完成。</li>
<li>檢查是否已建立發票（如果授權並擷取）以及是否收到發票電子郵件。</li>
<li>前往Postman並執行「準備好取貨」請求，將所有產品設定為「已取貨」。</li>
<li>開啟您的信箱，找到「準備好取貨」電子郵件。 然後，按一下**[!UICONTROL Confirm Arrival]**。</li>
<li>簽入。</li>
<li>前往Postman並執行Dispensed要求，將所有產品設定為已拒絕。</li>
</ol>
<td><ul>
<li>已更新訂單歷史記錄： <code>We refunded $X offline.</code></li>
<li>已收到退款電子郵件： <code>$x amount was refunded</code></li>
<li>狀態已設定為 <code>CLOSED</code>.</li>
<li>已建立銷退折讓單。 （等到cron運作為止。）</li>
</ul>
</td>
</tr>
<tr>
<td><strong>分配（分配期間）</br></br>部分取消</br>（部分產品已分發，部分已拒絕。）</strong>
</td>
<td>
<ol>
<li>下訂單。</li>
<li>等候順序同步完成。</li>
<li>檢查是否已建立發票（如果授權並擷取）以及是否收到發票電子郵件。</li>
<li>前往Postman，執行「準備好取貨」請求，並將所有產品設定為「已取貨」。</li>
<li>開啟您的信箱。 找到「準備好取車」電子郵件，然後選取 <code>Confirm Arrival</code>.</li>
<li>簽入。</li>
<li>前往Postman，執行Dispensed請求，並將部分產品設定為dispensed，並將部分產品設定為rejected</li>
</ol>
</td>
<td>
<li>已更新訂單歷史記錄： <code>We refunded $X offline</code></li>
<li><code>Order notified as partly canceled at: Date and Hour</code>
<li>已收到退款電子郵件： <code>$x amount was refunded</code>
<li>訂單狀態設定為 <code>Ready for pickup Dispensed</code>
<li>已建立銷退折讓單。 （等到cron運作為止。）</li>
</td>
</tr>
<tr>
<td> <strong>回訪後新增RMA （完整）</strong>
</td>
<td>
<ol>
<li>下訂單。</li>
<li>等候順序同步完成。</li>
<li>如果已設定授權與擷取選項，請確認已建立商業發票，且客戶已收到商業發票電子郵件。</li>
<li>選擇所有具有Postman的產品。</li>
<li>簽入。</li>
<li>進行分配。</li>
<li>前往訂單，然後選取<strong>[!UICONTROL Create returns]=
<li>建立RMA。</li>
</ol>
</td>
<td>
<ul>
<li>已建立RMA，並顯示在 <strong>[!UICONTROL Returns]</b> 索引標籤上的「訂單」檢視。</li>
<li>客戶已收到RMA確認電子郵件。</li>
</ul>
</td>
</tr>
<tr>
<td><strong>返回後新增RMA — 部分</strong>
</td>
<td>
<ol>
<li>下訂單。</li>
<li>等候順序同步完成。</li>
<li>檢查是否已建立發票（如果授權並擷取）以及是否收到發票電子郵件。</li>
<li>選擇所有具有Postman的產品。</li>
<li>簽入。</li>
<li>進行分配。</li>
<li>移至順序，然後選取  <strong>[!UICONTROL Create returns]</strong></li>
<li>使用部分訂購產品建立RMA。</li>
</ol>
<td>
<ul>
<li>RMA已建立並顯示在下列 <strong>[!UICONTROL Returns]</strong> 索引標籤上的「訂單」檢視。</li>
<li>客戶已收到RMA確認電子郵件。</li>
<li>建立RMA之後，取得RMA授權：從管理員，前往 <strong>[!UICONTROL Sales > Returns]</strong>. 選取您建立並授權的RMA。</li>
<li>確認客戶已收到RMA授權確認電子郵件。</li>
<li>檢查退款是否已新增至交易與訂單歷史記錄。</li>
</ul>
</td>
</tr>
</table>


### Store Fulfillment應用程式許可權

測試計畫的這個區段涵蓋「商店履行」應用程式使用者的帳戶管理。

- 確認商店關聯可使用從Adobe Commerce管理員建立的新使用者帳戶進行驗證。
- 確認已成功套用現有帳戶的更新。

**功能區域：** Adobe Commerce管理員</br>
**角色：** 管理員、商店關聯</br>
**測試型別：** 全部正面

<table style="table-layout:auto">
<tr>
<th>函式</th>
<th>情境</th>
<th>預期結果</th>
</tr>
<tr>
<td><strong>使用者帳戶管理 — 建立帳戶</strong></br></br>
</td>
<td>
<ol>
<li><strong>管理員</strong>  — 登入Adobe Commerce Admin</li>
<li>前往 <strong>[!UICONTROL System] &gt;商店履行應用程式許可權&gt;所有商店履行應用程式使用者</strong></li>
<li><strong>新增使用者。</strong></li>
</ol>
<td>
<ul>
<li>已成功建立帳戶。</li>
<li>新使用者帳戶會顯示在 [!UICONTROL Store Fulfillment Users] 儀表板。</li>
<li><strong>存放區關聯</strong> 使用新的使用者帳戶登入「商店協助」應用程式。</li>
</ul>
</td>
</tr>
<tr>
<td><strong>使用者帳戶管理 — 更新現有的使用者帳戶</strong>
</td>
<td>
<ol>
<li>使用管理員使用者帳戶登入Adobe Commerce管理員。</li>
<li>前往 <strong>[!UICONTROL System] &gt;商店履行應用程式許可權&gt;所有商店履行應用程式使用者</strong>.</li>
<li>在「使用者帳戶」清單中，選取以開啟現有的作用中使用者帳戶 <strong>[!UICONTROL Edit]</strong>.
<li>透過變更停用帳戶 <strong>[!UICONTROL Is Active]</strong> 至 <strong>否</strong>.</li>
</ol>
</td>
<td>
<ul>
<li>於 <strong>[!UICONTROL Store Fulfillment App Users]</strong> 儀表板，已更新帳戶的狀態已變更為 <strong>[!UICONTROL Inactive]</strong>.</li>
<li>Store Associate無法使用非作用中帳戶認證登入Store Assist應用程式。</li>
</ul>
</td>
</tr>
</table>

## Adobe Commerce產品型別

Adobe Commerce產品型別的測試案例會驗證客戶是否看到不同產品型別的正確產品、庫存和傳遞方法資訊：

- [!UICONTROL Configurable]
- [!UICONTROL Grouped]
- [!UICONTROL Virtual]
- [!UICONTROL Bundle products] 在Adobe Commerce店面。

**功能區域：** Adobe Commerce前端</br>
**角色：** 商店協助應用程式使用者（商店關聯）</br>
**測試型別：** 全部正面

<table style="table-layout:auto">
<tr>
<th>函式</th>
<th>情境</th>
<th>註解</th>
</tr>
<tr>
<td><strong>可設定的產品</strong>
</td>
<td>
<ul>
<li>確認使用者只能看到這些可設定的選項，包括已啟用的來源、已指定庫存以及庫存中有某些專案 — 檢查子產品。</li>
<li>確認選取其他存放區時，不可用的選項會顯示為已劃出。</li>
<li>確認如果使用者選取不同的商店，可設定的選項會取消選取。</li>
<li>確認如果可設定的產品已經在購物車中，且使用者選擇不同的商店，則產品顯示為無庫存。</li>
</ul>
</td>
<td></td>
</td>
</tr>
<tr>
<td><strong>群組的產品</strong>
</td>
<td>
<ul>
<li>確認傳遞方法和 [!UICONTROL Add to cart] 當所有子產品都具備以下條件時，按鈕將針對客戶停用
<code>qty</code> 設定為 <code>0</code>.</li>
<li>確認至少有一個子產品具備下列條件時，客戶已啟用傳遞方法 <code>qty</code> 設定為 <code>0.</code></li>
<li>確認 [!UICONTROL Store Pickup Delivery] 方法僅對具有「 」的產品可見及作用 [!UICONTROL Available for Store Pickup] 已啟用。 （檢查子產品。）</li>
</ul>
</td>
<td></td>
</tr>
<tr>
<td><strong>虛擬產品</strong>
</td>
<td>
確認虛擬產品不提供  [!UICONTROL In-store Pickup] 傳遞方法。
<td></td>
</td>
</tr>
<tr>
<td><strong>套裝產品</strong>
</td>
<td>
<ul>
<li>確認至少有一個子產品具有 [!UICONTROL Available for Store Pickup] 停用，客戶無法使用「商店取貨」交貨選項。</li>
<li>確認至少有一個子產品具有 [!UICONTROL Available for Home Delivery] 停用，「首頁傳送」選項不適用於客戶。</li>
<li>驗證套件組合中是否有至少一個子產品無庫存，套件組合（父產品）亦顯示為 [!UICONTROL Out of stock].</li>
</ul>
</td>
<td></td>
</tr>
<tbody>
</table>

## 簽入體驗

測試計畫的這個區段涵蓋下列功能的「商店取貨單的簽到體驗」：

- 替代取車聯絡人 — 確認新增 [!UICONTROL Alternate Pickup Contact] 並選取 [!UICONTROL Preferred Contact] 在商店取貨單上。

- 簽入表單 — 驗證提交「商店取貨」訂單的簽入請求的工作流程。

**功能區域：** 購物車結帳、商店取貨訂單的簽到表單</br>
**角色：** 管理員、客戶、商店關聯</br>
**測試型別：** 全部正面

### 替代取車連絡人


**功能區域：** 購物車結帳</br>
**角色：** 客戶</br>
**測試型別：** 全部正面

<table style="table-layout:auto">
<tr>
<th>函式</th>
<th>情境</th>
<th>預期結果</th>
</tr>
<tr>
<td><strong>替代取車連絡人</br>
簽入<strong>
</td>
<td>
客戶提交具有「店內取貨」選項的訂單。</td>
<td>在結帳過程中，客戶會看到 [!UICONTROL Alternate Pickup Contact] 「送貨」步驟上的選項。
</td>
</tr>
<tr>
<td><strong>備用取車偏好連絡人，簽到</strong>
<td>
客戶提交具有「店內取貨」選項的訂單。 結帳期間，客戶新增 [!UICONTROL Alternate Pickup Contact].</td>
<td>在結帳過程中，客戶會看到 [!UICONTROL Preferred Contact] 運送步驟上的選項。</td>
</td>
</tr>
<tr>
<td><strong>備用取貨聯絡人詳細資料，入庫</strong>
</td>
<td>
客戶提交具有「店內取貨」選項的訂單。 結帳時，客戶選取 [!UICONTROL Alternate Pickup Contact] 在送貨步驟中。
</td>
<td>客戶會看到輸入選項來輸入聯絡人詳細資訊： [!UICONTROL First name]， [!UICONTROL Last name]， [!UICONTROL Phone]、和 [!UICONTROL Email].</td>
</tr>
<tr>
<td><strong>備用接送、簽到電子郵件</strong>
</td>
<td>客戶提交具有「店內取貨」選項的訂單。 結帳時，客戶選取 [!UICONTROL Alternate Pickup Contact] 在送貨步驟中，新增聯絡人詳細資料並提交訂單。</td>
<td>客戶與替代連絡人都會收到訂單的「簽到電子郵件」。</td>
</tr>
<td><strong>替代取貨、訂單明細</strong></td>
<td>客戶提交具有「店內取貨」選項的訂單。 結帳時，客戶選取 [!UICONTROL Alternate Pickup Contact] 在送貨步驟中，新增聯絡人詳細資料並提交訂單。</td>
<td>管理員會看到已儲存訂單上的其他連絡資訊。</td>
</tr>
<tr>
<td><strong>替代取貨連絡人、商店相關訂單檢視表</strong>
</td>
<td>客戶提交具有「店內取貨」選項的訂單。 結帳時，客戶選取 [!UICONTROL Alternate Pickup Contact] 在送貨步驟中，新增聯絡人詳細資料並提交訂單。</td>
<td>Store Associate可在FaaS/ChaaS中檢視訂單的其他聯絡資訊。</td>
</td>
</tr>
</tbody>
</table>

### 簽入表單


**功能區域：** 簽入表單</br>
**角色：** 客戶</br>
**測試型別：** 全部正面

<table style="table-layout:auto">
<tr>
<th>函式</th>
<th>情境</th>
<th>預期結果</th>
</tr>
<tr>
<td><strong>簽入動作 — 提交請求</strong>
</td>
<td>在簽入表單上，客戶完成所有必填欄位，並提交請求。</td>
<td>客戶會收到成功回應。</td>
</tr>
<tr>
<td><strong>簽入動作 — 檢視請求詳細資訊</strong></td>
<td>客戶成功提交簽到要求。</td>
<td>訂單狀態會在FaaS系統中更新，而「商店關聯」可在FaaS中檢視簽入請求詳細資訊。
</td>
</tr>
<tr>
<td><strong>簽入動作 — 僅提交請求一次</strong></td>
<td>在提交訂單的簽入請求後，客戶會選取要第二次簽入的連結。</td>
<td>在「入庫」表單中，客戶看不到編輯或重新提交表單的選項。</td>
</tr>
<tr>
<td><strong>簽入動作 — 確認到達</strong></td>
<td>店內取貨訂單已標示為可在FaaS中取貨。 客戶會收到「準備好取貨」電子郵件，並選擇 [!UICONTROL Confirm Arrival].</td>
<td>客戶看到訂單的「簽到」表單。</td>
</tr>
</tbody>
</table>

## 商店協助應用程式

測試計畫的這個區段涵蓋Store Assist應用程式中測試訂單、挑選和移交工作流程的情況。

**功能區域：** 商店協助應用程式</br>
**角色：** 存放區關聯</br>
**測試型別：** 全部正面

<table style="table-layout:auto">
<tr>
<th>函式</th>
<th>情境</th>
<th>預期結果</th>
</tr>
<tr>
<td>
<strong>單一訂單撿料 — 快樂路徑、路邊撿料</strong></td>
<td>挑選單一和多數量料號。 無nil pick和路邊取貨（含分段）。
</td>
<td>
</td>
</tr>
<tr>
<td><strong>多訂單撿料 — 快樂路徑、路邊撿料</strong></td>
<td>單一和多數量料號。 無nil pick和路邊取貨（含預備）</td>
<td></td>
</tr>
<tr>
<td><strong>單次取貨 — 店內取貨的快樂路徑</strong></td>
<td>單一和多數量料號。 無nil pick，和店內取貨（含分段）</td>
<td>
</td>
</tr>
<tr>
<td><strong>多訂單撿料 — 快樂路徑、店內撿料</strong></td>
<td>挑選單一和多數量料號。 無nil pick和路邊取貨（含分段）。</td>
<td></td>
</tr>
<tr>
<td><strong>單一訂單撿料 — 路徑不愉快，店內撿料</strong></td>
<td>撿料單一與多重數量料號，具有部份與零撿料與店內撿料（含暫存）</td>
</td>
<td></td>
</tr>
<td><strong>多訂單撿料 — 不滿意的路邊撿料</strong></td>
<td>撿料單一與多重數量料號，具有部份與零撿料與店內撿料（含暫存）</td>
<td></td>
</tr>
<td><strong>單一訂單撿料 — 路徑不愉快，路邊撿料</strong></td>
<td>撿料單一與多重數量料號，具有部份與撿料與路邊撿料（含暫存）</strong></td>
</td>
<td></td>
</tr>
<tr><td><strong>已下訂單 — 撿料前已取消</strong></td>
<td></td>
<td></td>
</tr>
<tr>
<td><strong>下訂單 — 移交前已取消</strong></td>
<td></td>
<td></td>
</tr>
<tr>
<td><strong>已下訂單 — 依訂單模組搜尋</strong></td>
<td></td>
<td></td>
</tr>
<tr><td><strong>下訂單 — 搜尋和手動簽入以進行移交</strong></td>
<td></td>
<td></td>
</tr>
<tr><td><strong>已下訂單 — 所有料號未撿料或撿料器未標示為可用</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>使用套件組合專案下訂單 — 撿料和移交</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>已下訂單 — 已拒絕的交出</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>已下訂單 — 交出並拒絕所有料號</strong></td>
<td></td>
<td></td></tr>
</tbody>
</table>

## 部署

在您確認解決方案已設定完畢，並依照您的規格完成測試後，您就可以準備從測試版部署至生產版。

部署和測試會依您的基礎結構和功能而異。

>[!TIP]
>
>如需雲端基礎結構專案的部署准則、檢查清單和Adobe Commerce最佳實務，請參閱 [部署您的存放區](https://devdocs.magento.com/cloud/live/stage-prod-live.html) (位於Adobe Commerce開發人員檔案中)。
