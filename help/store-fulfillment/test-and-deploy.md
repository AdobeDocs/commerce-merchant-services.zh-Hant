---
title: 測試和部署儲存完成
description: 測試計畫以驗證「儲存完成」功能。 測試內容涵蓋庫存同步API、已取消訂單的端對端履行工作流程、商店履行應用程式使用者管理，以及客戶簽入體驗。
role: User, Admin
level: Intermediate
exl-id: 77285a66-5161-407b-94cd-b3f412d7949d
source-git-commit: 0a1d70465247422db44daee302c67fe1a5a29d32
workflow-type: tm+mt
source-wordcount: '2657'
ht-degree: 0%

---

# 測試並部署Adobe Commerce的商店完成

在您的開發環境中完成上線流程後，您可以啟動此流程，以測試商店完成解決方案並部署至您的生產環境。

**必要條件**

在測試或同步任何資訊、儲存或訂單之前，請驗證您已完成以下任務：

- 已完成 [一般配置](enable-general.md) （用於商店完成服務）。

- [新增及驗證您沙箱和生產環境的帳戶憑證和連線詳細資訊](connect-set-up-service.md#configure-store-fulfillment-account-credentials)

- 確認 [Adobe Commerce整合](connect-set-up-service.md#configure-store-fulfillment-account-credentials) 對於商店完成解決方案，可供使用和授權。

## 準備測試

必須先完成連線設定，您才能建立任何測試訂單或執行整合測試。 在測試之前，還必須驗證儲存資料是否已同步。

1. 同步儲存完成源。

   - 前往 **[!UICONTROL Stores > Sources]**.

   - 選擇 **[!UICONTROL Synchronize Store Fulfillment Sources]**.

1. 在儲存網格中，驗證儲存已標籤為 `Synced` 建立測試訂單之前。

## 示例測試計畫

零售商在部署的設定和測試階段期間驗證商店完成解決方案的基本功能。 此示例測試計畫提供測試的起始點。 根據您的需求新增其他案例。

>[!NOTE]
>
>完成商店完成解決方案的初始入門或更新現有安裝後，請始終在非生產環境中測試應用程式，然後再部署到生產環境。

此示例測試計畫涵蓋以下功能領域：

| 功能區 | 函式 | 角色 |
|-------------------------------------|------------------------------------------|----------------------------------|
| 庫存和訂單同步 | 庫存API同步 | Adobe Commerce管理員 |
| 端對端 | 訂單取消工作流 | 客戶、管理員、商店關聯 |
| 管理 | 商店完成應用程式權限 | 管理 |
| Adobe Commerce弗朗滕 | 產品類型 | 客戶、管理員 |
| 前端結帳</br>簽入表單 | 簽入體驗 | 客戶、管理員 |
| 商店協助應用程式 | 順序</br>挑選</br>階段</br>和切換 | 儲存關聯 |

### 庫存API同步

測試計畫的此部分包括庫存和訂單同步，以驗證在Adobe Commerce和商店完成解決方案之間正確同步了對拾取源和庫存的更新。

**功能區**:庫存和訂單同步</br>
**角色：** 管理</br>
**測試類型：** 全部正

<table>
<thead>
<tr>
<th>函式</th>
<th>測試藍本</th>
<th>預期結果</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>添加裝貨庫存來源</strong></td>
<td>保存新的裝貨庫存來源。</td>
<td>即時同步會在5分鐘內將源詳細資訊發送到沃爾瑪GIF服務。</td>
</tr>
<tr>
<td><strong>更新現有的裝貨庫存來源</strong></td>
<td>保存對現有裝貨庫存來源的更新。</td>
<td>即時同步操作會在5分鐘內將詳細資訊發送給沃爾瑪GIF</td>
</tr>
<tr>
<td><strong>裝貨貨源</br><code>Is Synced</code> 狀態</br><code>Is Synced</code></strong></td>
<td>保存對現有裝貨庫存來源的更新。</td>
<td>成功操作後， <code>Is Synced</code> 「管理源」頁更新的列 <code>No</code> to <code>Yes</code>.</td>
</tr>
<tr>
<td><strong>修改的庫存預留流程</strong></td>
<td>為產品建立和提交新訂單。</td>
<td>產品的可售數量相應減少。</td>
</tr>
<tr>
<td><strong>新訂單推送、API同步 — 客戶訂單</strong></td>
<td>客戶提交商店提貨訂單。</td>
<td><ul><li>在「管理順序」檢視中， <strong>Adobe Commerce管理員使用者</strong> 查看訂單同步狀態已更新為 <code>Sent</code></li><li>訂單詳細資訊記錄包含訊息 <code>Order was sent to BOPIS solution for sync, it's not yet acknowledged yet.</code></li></ul></td>
</tr>
<tr>
<td><strong>新訂單推送、API同步 — 管理員提交訂單</strong></td>
<td>安Adobe Commerce <strong>管理</strong> 提交提貨單。</td>
<td><ul><li>在「管理訂單」檢視中，訂單同步狀態會更新至 <code>Sent</code>.</li><li>訂單詳細資訊記錄包含訊息 <code>Order was sent to BOPIS solution for sync, it's not yet acknowledged yet.</code></li></ul></td>
</tr>
<tr>
<td><strong>新訂單推送，例外佇列<strong></td>
<td>在Adobe Commerce管理員中識別數個可以透過Adobe Commerce履行的虛擬和可下載產品，而不需要與履行服務(FaaS)互動。</td>
<td>這些產品在出口中被適當地移除或標籤以防止與FaaS的下游衝突。</td>
</tr>
</tbody>
</table>

### 訂單取消工作流

測試計畫的此區段包含測試透過Adobe Commerce取消之訂單的端對端工作流程的案例。

**功能區：** Adobe Commerce管理員</br>
**角色：** 端對端（管理員、商店關聯、客戶）</br>
**測試結果類型：** 所有情況均為正數

<table style="table-layout:fixed">
<tr>
<th>函式</th>
<th>藍本</th>
<th>預期結果</th>
</tr>
<tr>
<td><strong>完全取消訂單</strong></td>
<td><ol>
<li>下訂單。</li>
<li>請等候直到同步順序為止。</li>
<li>驗證發票電子郵件的發票建立（如果授權並捕獲）接收。</li>
<li>從「發票」視圖建立包含所有已訂購產品的貸項通知單。</li>
</ol>
</td>
<td>
<ul>
<li>訂單歷史記錄已更新為 <code>We refunded $X online. Transaction ID: transactionID</code> 和 <code>Received Cancel acknowledgment from the BOPIS solution.</code></li>
<li>訂單狀態為 <code>Closed</code>. （我們已設定「付款審核」。）</li>
<li>在Adobe Commerce建立的貸項通知單。 （等到cron運作。）</li>
<li>如果所有項目均已選中，則準備接收電子郵件 <code>DISPLAY COMMENT HISTORY</code> 顯示 <code>Order is ready for pickup</code> (<code>CUSTOMER NOTIFIED</code> 標幟為 <code>true</code>.)</li>
<li>如果未選擇所有項目，則取消電子郵件和「顯示注釋歷史記錄」將顯示 <code>Order has been canceled - all items were not available</code></li>
<li><code>CUSTOMER NOTIFIED</code> 標幟為 <code>true</code>.)</li>
</ul>
</td>
</tr>
<tr><td><strong>部分訂單取消<strong></td>
<td>
<ol>
<li>訂購至少兩種產品。</li>
<li>請等候直到同步順序為止。</li>
<li>檢查是否已建立發票（如果授權並捕獲），並收到發票電子郵件。</li>
<li>等待兩小時進行交易結算。</li>
<li>從「發票」視圖中建立僅包含已訂購產品一部分的貸項通知單。</li>
</td>
<td>
<ul>
<li>訂單歷史記錄更新： <code>We refunded $X online. Transaction ID: transactionID</code></li>
<li>訂單歷史記錄更新： <code>Order notified as partly canceled at: Date and Hour</code></li>
<li>訂單退款電子郵件的接收： <code>$x amount was refunded</code></li>
<li>訂單狀態為 <code>Processing</code>.</li>
<li>在Adobe Commerce中建立的貸項通知單（等到cron運行後）。</li>
<li>如果未挑選某些項目，請確認 [!UICONTROL Ready for Pickup] 會顯示包含nil挑選或退款區段的電子郵件。 <code>DISPLAY COMMENT HISTORY</code> 顯示 <code>Order is ready for pickup, but some items not available.</code>.</li>
<li><code>CUSTOMER NOTIFIED</code> 標幟為 <code>true</code>.</li>
</ul>
</td>
</tr>
<td><strong>準備提貨</br></br>完全取消</br>（所有產品均設定為挑選，數量為0）</br></strong></td>
<td>
<ol>
<li>下訂單。</li>
<li>請等候直到同步順序為止。</li>
<li>檢查是否已建立發票（如果授權並捕獲），並收到發票電子郵件。</li>
<li>前往Postman，執行「準備提貨」請求，所有產品均設為 <code>picked</code> with <code>0 qty</code>.</li>
</ol>
</td>
<td>
<ul>
<li>訂單歷史記錄已更新： <code>We refunded $X offline</code></li>
<li>訂單狀態為 <code>CLOSED</code>.
<li>貸項通知單隨即建立。 （等到cron運作。）</li>
<li>收到退款電子郵件： <code>$x amount was refunded</code></li>
<li>已發送訂單取消電子郵件。</li>
</ul>
</td>
</tr>
<tr>
<td><strong>準備提貨 — 部分取消</strong></br></br><strong>(有些產品被挑選，有些則被挑選 <code>0 qty</code>)</strong>
</td>
<td>
<ol>
<li>下訂單。</li>
<li>請等候直到同步順序為止。</li>
<li>檢查是否已建立發票（如果授權並捕獲），並收到發票電子郵件。</li>
<li>轉到Postman，運行「準備提貨」請求，其中部分產品設定為已挑選，數量為0，其餘部分為已挑選。</li>
</ol>
</td>
<td>
<ul>
<li><code>Your order is ready for pickup</code> with [!UICONTROL Ready for Pickup Items] 和 [!UICONTROL Canceled Items] 表格。 </li>
<li>訂單狀態為「REAY FOR PICK（準備提貨）」。 </li>
<li>訂單歷史記錄已更新： <code>We refunded $X offline.</code>
<li>訂單歷史記錄已更新： <code>Order notified as partly canceled at: Date and hour</code>
<li>收到退款電子郵件： <code>$x amount was refunded</code>
<li>貸項通知單已建立。 （等到cron運作。）</li>
</ul>
</td>
</tr>
<tr>
<td><strong>準備提貨 — 部分取消</br></br>有些產品被挑選，有些則被挑選 <code>0 qty</code>)</strong>
</td>
<td><ol>
<li>下訂單。</li>
<li>請等候直到同步順序為止。</li>
<li>檢查是否已建立發票（如果授權並捕獲），並收到發票電子郵件。</li>
<li>轉到Postman，運行「準備提貨」請求，其中部分產品設定為已挑選，數量為0，其餘部分為已挑選。</li>
</ol>
</td>
<td><ul>
<li><code>Your order is ready for pickup</code> with [!UICONTROL Ready for Pickup Items] 和 [!UICONTROL Canceled Items] 表格。 </li>
<li>訂單狀態為「REAY FOR PICK（準備提貨）」。 </li>
<li>訂單歷史記錄已更新： <code>We refunded $X offline.</code>
<li>訂單歷史記錄已更新： <code>Order notified as partly canceled at: Date and hour</code>
<li>收到退款電子郵件： <code>$x amount was refunded</code>
<li>貸項通知單已建立。 （等到cron運作。）</li>
</ul>
</td>
</tr>
<tr>
<td><strong>分配（分配期間） </br></br>完全取消（所有產品均設為拒絕）</strong>
</td>
<td>
<ol>
<li>下訂單。</li>
<li>請等候直到同步順序為止。</li>
<li>檢查是否已建立發票（如果授權並捕獲），並收到發票電子郵件。</li>
<li>前往Postman，執行「準備提貨」請求，並將所有產品設為已挑選。</li>
<li>開啟郵箱，找到「準備提貨」電子郵件。 然後，按一下**[!UICONTROL Confirm Arrival]**。</li>
<li>簽到。</li>
<li>前往Postman，將所有產品設為已拒絕的項目執行分配請求。</li>
</ol>
<td><ul>
<li>訂單歷史記錄已更新： <code>We refunded $X offline.</code></li>
<li>收到退款電子郵件： <code>$x amount was refunded</code></li>
<li>狀態設定為 <code>CLOSED</code>.</li>
<li>已建立貸項通知單。 （等到cron運作。）</li>
</ul>
</td>
</tr>
<tr>
<td><strong>分配（分配期間）</br></br>部分取消</br>(一些產品被分配；有些被拒絕。)</strong>
</br></td>
<td>
<ol>
<li>下訂單。</li>
<li>請等候直到同步順序為止。</li>
<li>檢查是否已建立發票（如果授權並捕獲），並收到發票電子郵件。</li>
<li>前往Postman，執行「準備提貨」請求，並將所有產品設為已挑選。</li>
<li>開啟您的郵箱。 查找「Ready for Pick（準備提貨）」電子郵件，然後選擇 <code>Confirm Arrival</code>.</li>
<li>簽到。</li>
<li>前往Postman，對要分配的產品和要拒絕的產品執行分配請求</li>
</ol>
</td>
<td>
<li>訂單歷史記錄已更新： <code>We refunded $X offline</code></li>
<li><code>Order notified as partly canceled at: Date and Hour</code>
<li>收到退款電子郵件： <code>$x amount was refunded</code>
<li>訂單狀態設定為 <code>Ready for pickup Dispensed</code>
<li>已建立貸項通知單。 （等到cron運作。）</li>
</td>
</tr>
<tr>
<td> <strong>退貨後新的RMA（完整）</strong>
</td>
<td>
<ol>
<li>下訂單。</li>
<li>請等候直到同步順序為止。</li>
<li>確認已建立發票（如果授權並擷取），且已收到發票電子郵件。</li>
<li>使用Postman挑選所有產品。</li>
<li>簽到。</li>
<li>做分發。</li>
<li>按順序選擇<strong>[!UICONTROL Create returns]=
<li>建立RMA。</li>
</ol>
</td>
<td>
<ul>
<li>RMA已建立，顯示在 <strong>[!UICONTROL Returns]</b> 頁簽。</li>
<li>客戶收到RMA確認電子郵件。</li>
</ul>
</td>
</tr>
<tr>
<td><strong>退貨後新的RMA — 部分</strong>
</td>
<td>
<ol>
<li>下訂單。</li>
<li>請等候直到同步順序為止。</li>
<li>檢查是否已建立發票（如果授權並捕獲），並收到發票電子郵件。</li>
<li>使用Postman挑選所有產品。</li>
<li>簽到。</li>
<li>做分發。</li>
<li>按順序，然後選擇  <strong>[!UICONTROL Create returns]</strong></li>
<li>使用訂購的產品的一部分建立RMA。</li>
</ol>
<td>
<ul>
<li>RMA建立並顯示在 <strong>[!UICONTROL Returns]</strong> 頁簽。</li>
<li>客戶收到RMA確認電子郵件。</li>
<li>建立RMA後，獲取RMA授權：從管理員，前往 <strong>[!UICONTROL Sales > Returns]</strong>. 選擇您建立並授權的RMA。</li>
<li>驗證客戶是否收到RMA授權確認電子郵件。</li>
<li>檢查退款是否已添加到事務處理和訂單歷史記錄中。</li>
</ul>
</td>
</tr>
</table>


### 商店完成應用程式權限

測試計畫的此部分涵蓋商店履行應用程式使用者的帳戶管理。

- 確認商店關聯可以使用從Adobe Commerce管理員建立的新使用者帳戶進行驗證。
- 確認已成功套用現有帳戶的更新。

**功能區：** Adobe Commerce管理員</br>
**角色：** 管理員、商店關聯</br>
**測試類型：** 全部呈正

<table style="table-layout:auto">
<tr>
<th>函式</th>
<th>藍本</th>
<th>預期結果</th>
</tr>
<tr>
<td><strong>用戶帳戶管理 — 建立帳戶</strong></br></br>
</td>
<td>
<ol>
<li><strong>管理</strong>  — 登入Adobe Commerce管理員</li>
<li>前往 <strong>[!UICONTROL System] &gt;商店完成應用程式權限&gt;所有商店完成應用程式用戶</strong></li>
<li><strong>新增使用者。</strong></li>
</ol>
<td>
<ul>
<li>帳戶已成功建立。</li>
<li>新使用者帳戶會顯示在 [!UICONTROL Store Fulfillment Users] 控制面板。</li>
<li><strong>儲存關聯</strong> 使用新的使用者帳戶登入Store Assist應用程式。</li>
</ul>
</td>
</tr>
<tr>
<td><strong>用戶帳戶管理 — 更新現有用戶帳戶</strong>
</td>
<td>
<ol>
<li>使用管理員使用者帳戶登入Adobe Commerce管理員。</li>
<li>前往 <strong>[!UICONTROL System] &gt;商店完成應用程式權限&gt;所有商店完成應用程式用戶</strong>.</li>
<li>在「用戶帳戶」清單中，通過選擇 <strong>[!UICONTROL Edit]</strong>.
<li>透過變更 <strong>[!UICONTROL Is Active]</strong> to <strong>否</strong>.</li>
</ol>
</td>
<td>
<ul>
<li>在 <strong>[!UICONTROL Store Fulfillment App Users]</strong> 控制面板中，已更新帳戶的狀態已變更為 <strong>[!UICONTROL Inactive]</strong>.</li>
<li>儲存關聯無法使用非活動帳戶憑據登錄到儲存輔助應用。</li>
</ul>
</td>
</tr>
</table>

## Adobe Commerce產品類型

Adobe Commerce產品類型的測試案例會驗證客戶是否看到不同產品類型的正確產品、庫存和傳送方法資訊：

- [!UICONTROL Configurable]
- [!UICONTROL Grouped]
- [!UICONTROL Virtual]
- [!UICONTROL Bundle products] 在Adobe Commerce店。

**功能區：** Adobe Commerce弗朗滕</br>
**角色：** Store Assist應用程式使用者（商店關聯）</br>
**測試類型：** 全部呈正

<table style="table-layout:auto">
<tr>
<th>函式</th>
<th>藍本</th>
<th>註解</th>
</tr>
<tr>
<td><strong>可配置產品</strong>
</td>
<td>
<ul>
<li>驗證用戶只能看到那些可配置的選項（已啟用源、已分配庫存以及存在庫存中的某些物料） — 檢查子產品。</li>
<li>確認選取其他商店時，無法使用的選項會顯示為划出。</li>
<li>驗證如果用戶選擇不同的儲存，則可配置選項將取消選中。</li>
<li>確認如果可設定產品已在購物車中，且使用者選取不同的商店，則產品會顯示為無存貨。</li>
</ul>
</td>
<td></td>
</td>
</tr>
<tr>
<td><strong>分組產品</strong>
</td>
<td>
<ul>
<li>驗證傳送方法和 [!UICONTROL Add to cart] 當所有子產品都具有
<code>qty</code> 設為 <code>0</code>.</li>
<li>確認當至少有一個子產品具有 <code>qty</code> 設為 <code>0.</code></li>
<li>確認 [!UICONTROL Store Pickup Delivery] 方法僅對具有 [!UICONTROL Available for Store Pickup] 已啟用。 （檢查子產品。）</li>
</ul>
</td>
<td></td>
</tr>
<tr>
<td><strong>虛擬產品</strong>
</td>
<td>
驗證虛擬產品未提供  [!UICONTROL In-store Pickup] 傳遞方法。
<td></td>
</td>
</tr>
<tr>
<td><strong>捆綁產品</strong>
</td>
<td>
<ul>
<li>如果至少有一個子產品具有 [!UICONTROL Available for Store Pickup] 停用時，客戶無法使用商店取貨傳送選項。</li>
<li>如果至少有一個子產品具有 [!UICONTROL Available for Home Delivery] 停用時，客戶無法使用「首頁傳送」選項。</li>
<li>驗證捆綁包中是否至少有一個子產品無存貨，該捆綁包（父產品）也顯示為 [!UICONTROL Out of stock].</li>
</ul>
</td>
<td></td>
</tr>
<tbody>
</table>

## 簽入體驗

測試計畫的此部分涵蓋以下功能的「商店裝貨訂單的簽入體驗」：

- 替代拾取聯繫人 — 驗證添加的工作流 [!UICONTROL Alternate Pickup Contact] 和選擇 [!UICONTROL Preferred Contact] 儲存裝貨訂單。

- 簽入表單 — 驗證提交存貨提貨單的簽入請求的工作流。

**功能領域：** 購物車結帳，存貨裝貨訂單簽入表</br>
**角色：** 管理員、客戶、商店關聯</br>
**測試類型：** 全部呈正

### 備用提貨聯繫人


**功能區：** 購物車結帳</br>
**角色：** 客戶</br>
**測試類型：** 全部呈正

<table style="table-layout:auto">
<tr>
<th>函式</th>
<th>藍本</th>
<th>預期結果</th>
</tr>
<tr>
<td><strong>備用提貨聯繫人</br>
簽入</br><strong>
</td>
<td>
客戶使用店內裝貨選項提交訂單。</td>
<td>在結帳過程中，客戶會看到 [!UICONTROL Alternate Pickup Contact] 「裝運」步驟上的選項。
</td>
</tr>
<tr>
<td><strong>備用裝貨首選聯繫人，簽入</strong>
<td>
客戶使用店內裝貨選項提交訂單。 結帳期間，客戶新增 [!UICONTROL Alternate Pickup Contact].</td>
<td>在結帳過程中，客戶會看到 [!UICONTROL Preferred Contact] 選項。</td>
</td>
</tr>
<tr>
<td><strong>備用裝貨聯繫人詳細資訊，簽入</strong>
</td>
<td>
客戶使用店內裝貨選項提交訂單。 結帳期間，客戶會選取 [!UICONTROL Alternate Pickup Contact] 上。
</td>
<td>客戶會看到輸入選項以輸入聯繫人詳細資訊： [!UICONTROL First name], [!UICONTROL Last name], [!UICONTROL Phone]，和 [!UICONTROL Email].</td>
</tr>
<tr>
<td><strong>備用裝貨，簽入電子郵件</strong>
</td>
<td>客戶使用店內裝貨選項提交訂單。 結帳期間，客戶會選取 [!UICONTROL Alternate Pickup Contact] 在發運步驟中，添加聯繫人詳細資訊並提交訂單。</td>
<td>客戶和備用聯繫人都會收到訂單的簽入電子郵件。</td>
</tr>
<td><strong>替代裝貨、訂單詳細資訊</strong></td>
<td>客戶使用店內裝貨選項提交訂單。 結帳期間，客戶會選取 [!UICONTROL Alternate Pickup Contact] 在發運步驟中，添加聯繫人詳細資訊並提交訂單。</td>
<td>管理員會查看已儲存訂單的其他聯絡資訊。</td>
</tr>
<tr>
<td><strong>備用裝貨聯繫人，儲存關聯訂單視圖</strong>
</td>
<td>客戶使用店內裝貨選項提交訂單。 結帳期間，客戶會選取 [!UICONTROL Alternate Pickup Contact] 在發運步驟中，添加聯繫人詳細資訊並提交訂單。</td>
<td>Store Associate可以在FaaS/ChaaS中查看訂單的其他聯繫資訊。</td>
</td>
</tr>
</tbody>
</table>

### 簽入表


**功能區：** 簽入表單</br>
**角色：** 客戶</br>
**測試類型：** 全部呈正

<table style="table-layout:auto">
<tr>
<th>函式</th>
<th>藍本</th>
<th>預期結果</th>
</tr>
<tr>
<td><strong>簽入操作 — 提交請求</strong>
</td>
<td>在簽入表中，客戶填寫所有必填欄位並提交請求。</td>
<td>客戶會收到成功回應。</td>
</tr>
<tr>
<td><strong>簽入操作 — 查看請求詳細資訊</strong></td>
<td>客戶成功提交簽入請求。</td>
<td>FaaS系統中的訂單狀態更新，Store Associate可以在FaaS中查看簽入請求的詳細資訊。
</td>
</tr>
<tr>
<td><strong>簽入操作 — 僅提交請求一次</strong></td>
<td>在提交訂單的簽入請求後，客戶將選擇該連結進行第二次簽入。</td>
<td>在「簽入」表單中，客戶看不到編輯或重新提交表單的選項。</td>
</tr>
<tr>
<td><strong>簽入操作 — 確認到達</strong></td>
<td>在FaaS中，店內取貨訂單已經標籤為可取貨。 客戶收到「準備提貨」電子郵件，並選擇 [!UICONTROL Confirm Arrival].</td>
<td>客戶看到訂單的簽入表單。</td>
</tr>
</tbody>
</table>

## 商店協助應用程式

測試計畫的本節涵蓋在商店輔助應用程式中測試訂單、挑選和切換工作流程的情況。

**功能區：** 商店協助應用程式</br>
**角色：** 儲存關聯</br>
**測試類型：** 全部呈正

<table style="table-layout:auto">
<tr>
<th>函式</th>
<th>藍本</th>
<th>預期結果</th>
</tr>
<tr>
<td>
<strong>單張訂單領料 — 快捷路徑，邊線提貨</strong></td>
<td>挑選單數量和多數量物料。 沒有無提貨，也沒有提貨（具有預備）。
</td>
<td>
</td>
</tr>
<tr>
<td><strong>多訂單領料 — 快捷路徑、邊線領料</strong></td>
<td>單數量和多數量物料。 無無提貨，無提貨（具有測試環境）</td>
<td></td>
</tr>
<tr>
<td><strong>單張訂單領料 — 店內快捷路徑提貨</strong></td>
<td>單數量和多數量物料。 無無提貨，在店內提貨（具有暫存）</td>
<td>
</td>
</tr>
<tr>
<td><strong>多訂單領料 — 快捷路徑、店內提貨</strong></td>
<td>挑選單數量和多數量物料。 沒有無提貨，也沒有提貨（具有預備）。</td>
<td></td>
</tr>
<tr>
<td><strong>單張訂單領料 — 不快樂路徑，店內提貨</strong></td>
<td>挑選具有部分和零挑庫和內部挑庫的單件和多件物料（具有分段）</td>
</td>
<td></td>
</tr>
<td><strong>多訂單領料 — 不快樂的路徑 — 邊裝貨</strong></td>
<td>挑選具有部分和零挑庫和內部挑庫的單件和多件物料（具有分段）</td>
<td></td>
</tr>
<td><strong>單張訂單領料 — 不快樂路徑，邊裝貨</strong></td>
<td>挑選具有部分和零挑庫的單件和多件物料（具有分段）</strong></td>
</td>
<td></td>
</tr>
<tr><td><strong>已下訂單 — 領料前已取消</strong></td>
<td></td>
<td></td>
</tr>
<tr>
<td><strong>下訂單 — 在切換前取消</strong></td>
<td></td>
<td></td>
</tr>
<tr>
<td><strong>下訂單 — 按訂單模組搜索</strong></td>
<td></td>
<td></td>
</tr>
<tr><td><strong>下單 — 搜索和手動簽入以進行切換</strong></td>
<td></td>
<td></td>
</tr>
<tr><td><strong>已下訂單 — 所有未挑庫的項目或由選擇器標籤的不可用項目</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>帶捆綁項目的訂單 — 挑庫和切換</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>下單 — 放棄</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>下單 — 將所有物料交出並拒絕</strong></td>
<td></td>
<td></td></tr>
</tbody>
</table>

## 部署

在您驗證解決方案已根據您的規格進行配置和測試後，您就可以從測試部署到生產部署。

部署和測試會因您的基礎架構和功能而異。

>[!TIP]
>
>如需雲端基礎架構專案上Adobe Commerce的部署准則、核取清單和最佳實務，請參閱 [部署您的商店](https://devdocs.magento.com/cloud/live/stage-prod-live.html) 在Adobe Commerce開發人員檔案中。
