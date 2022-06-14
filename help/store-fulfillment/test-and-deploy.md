---
title: Test和部署儲存履行
description: Test計畫驗證「商店履行」功能。 Test包括庫存同步API、已取消訂單的端到端履行工作流、Store Fullment應用程式用戶管理和客戶簽入體驗。
role: User, Admin
level: Intermediate
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '2652'
ht-degree: 0%

---


# Test和部署Adobe Commerce的儲存履行

在開發環境中完成登入過程後，您可以啟動該過程，將儲存完成解決方案test並部署到您的生產環境。

**先決條件**

在測試或同步任何資訊、儲存或訂單之前，請驗證您已完成以下任務：

- 已完成 [常規配置](enable-general.md) 用於儲存履行服務。

- [添加並驗證沙盒和生產環境的帳戶憑據和連接詳細資訊](connect-set-up-service.md#configure-store-fulfillment-account-credentials)

- 確認 [Adobe Commerce整合](connect-set-up-service.md#configure-store-fulfillment-account-credentials) 可獲得並授權。

## 準備測試

必須先完成連接配置，然後才能建立任何test訂單或執行整合測試。 在測試之前，還必須驗證儲存資料是否已同步。

1. 同步儲存完成源。

   - 轉到 **[!UICONTROL Stores > Sources]**。

   - 選擇 **[!UICONTROL Synchronize Store Fulfillment Sources]**。

1. 在儲存網格中，驗證儲存是否標籤為 `Synced` 建立test訂單之前。

## 示例Test計畫

零售商在部署的配置和test階段驗證商店履行解決方案的基本功能。 此示例test計畫為測試提供了起點。 根據您的要求添加其他方案。

>[!NOTE]
>
>在完成Store Fullimment解決方案的初始啟動或更新現有安裝後，在部署到生產環境之前，始終在非生產環境中test應用程式。

此示例test計畫涵蓋以下功能區：

| 功能區 | 函式 | 角色 |
|-------------------------------------|------------------------------------------|----------------------------------|
| 庫存和訂單同步 | 清單API同步 | Adobe Commerce |
| 端到端 | 訂單取消工作流 | 客戶、管理員、商店關聯 |
| 管理 | 儲存履行應用權限 | 管理 |
| Adobe Commerce額 | 產品類型 | 客戶，管理員 |
| 前端結帳</br>簽入表單 | 簽入體驗 | 客戶，管理員 |
| 應用商店協助 | 訂單</br>選擇</br>舞台</br>切換 | 儲存關聯 |




### 清單API同步

test計畫的這一部分包括庫存和訂單同步，以驗證Adobe Commerce和商店完成解決方案之間對拾取來源和庫存的更新是否正確同步。

**功能區**:庫存和訂單同步</br>
**角色：** 管理</br>
**Test類型：** 全部正

<table>
<thead>
<tr>
<th>函式</th>
<th>Test方案</th>
<th>預期結果</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>添加裝貨庫源</strong></td>
<td>保存新的裝貨庫存來源。</td>
<td>即時同步在5分鐘內將源詳細資訊發送到沃爾瑪GIF服務。</td>
</tr>
<tr>
<td><strong>更新現有裝貨庫源</strong></td>
<td>將更新保存到現有裝貨庫存來源。</td>
<td>即時同步操作在5分鐘內將詳細資訊發送到沃爾瑪GIF</td>
</tr>
<tr>
<td><strong>裝貨庫源</br><code>Is Synced</code> 狀態</br><code>Is Synced</code></strong></td>
<td>將更新保存到現有裝貨庫存來源。</td>
<td>成功操作後， <code>Is Synced</code> 「管理源」頁更新的列 <code>No</code> 至 <code>Yes</code>。</td>
</tr>
<tr>
<td><strong>修改的庫存預留流程</strong></td>
<td>為產品建立和提交新訂單。</td>
<td>產品的可銷售數量相應減少。</td>
</tr>
<tr>
<td><strong>新訂單推送、API同步 — 客戶訂單</strong></td>
<td>客戶提交商店提貨訂單。</td>
<td><ul><li>在「管理訂單」視圖中， <strong>Adobe Commerce管理員用戶</strong> 查看訂單同步狀態已更新為 <code>Sent</code></li><li>訂單詳細資訊日誌包括消息 <code>Order was sent to BOPIS solution for sync, it’s not yet acknowledged yet.</code></li></ul></td>
</tr>
<tr>
<td><strong>新訂單推送，API同步 — 管理員提交訂單</strong></td>
<td>安Adobe Commerce <strong>管理</strong> 提交提貨單。</td>
<td><ul><li>在「管理訂單」視圖中，訂單同步狀態將更新至 <code>Sent</code>。</li><li>訂單詳細資訊日誌包括消息 <code>Order was sent to BOPIS solution for sync, it’s not yet acknowledged yet.</code></li></ul></td>
</tr>
<tr>
<td><strong>新訂單推送，異常隊列<strong></td>
<td>確定Adobe Commerce管理部內可通過Adobe Commerce完成的幾種虛擬和可下載產品，而無需與履行服務(FaaS)進行交互。</td>
<td>這些產品在出口中被適當地移除或標籤，以防止與FaaS發生下游衝突。</td>
</tr>
</tbody>
</table>

### 訂單取消工作流

test計畫的此部分包括test通過Adobe Commerce取消的訂單的端到端工作流的方案。

**功能區：** Adobe Commerce</br>
**角色：** 端對端（管理員、儲存關聯、客戶）</br>
**Test結果類型：** 所有方案均為正數

<table style="table-layout:fixed">
<tr>
<th>函式</th>
<th>方案</th>
<th>預期結果</th>
</tr>
<tr>
<td><strong>完全取消訂單</strong></td>
<td><ol>
<li>下訂單。</li>
<li>請等待訂單同步。</li>
<li>驗證發票電子郵件的建立（如果授權並捕獲）。</li>
<li>使用「發票」視圖中的所有訂購產品建立貸項通知單。</li>
</ol>
</td>
<td>
<ul>
<td>
<li>訂單歷史記錄更新為 <code>We refunded $X online. Transaction ID: transactionID</code> 和 <code>Received Cancel acknowledgment from the BOPIS solution.</code></li>
<li>訂單狀態為 <code>Closed</code>。 （我們已設定「付款審核」。）</li>
<li>在Adobe Commerce建立的貸項通知單。 （等到cron工作。）</li>
<li>如果已領取所有項目，則準備接收電子郵件 <code>DISPLAY COMMENT HISTORY</code> 顯示 <code>Order is ready for pickup</code> (<code>CUSTOMER NOTIFIED</code> 標誌 <code>true</code>。)</li>
<li>如果未選取所有項目，則取消電子郵件和顯示注釋歷史記錄 <code>Order has been canceled - all items were not available</code></li>
<li><code>CUSTOMER NOTIFIED</code> 標誌 <code>true</code>。)</li>
</ul>
</td>
</tr>
<tr><td><strong>偏序取消<strong></td>
<td>
<ol>
<li>至少訂購兩種產品。</li>
<li>請等待訂單同步。</li>
<li>檢查是否已建立發票（如果授權並捕獲）和收到發票電子郵件。</li>
<li>等待兩小時進行交易結算。</li>
<li>從「發票」視圖中僅建立部分訂購產品的貸項通知單。</li>
</td>
<td>
<ul>
<li>訂單歷史記錄更新： <code>We refunded $X online. Transaction ID: transactionID</code></li>
<li>訂單歷史記錄更新： <code>Order notified as partly canceled at: Date and Hour</code></li>
<li>訂單退款電子郵件的接收： <code>$x amount was refunded</code></li>
<li>訂單狀態為 <code>Processing</code>。</li>
<li>在Adobe Commerce建立的貸項通知單（等到cron工作為止）。</li>
<li>如果未選取某些項目，請確認 [!UICONTROL Ready for Pickup] 將顯示包含「nilpick」或「退款」部分的電子郵件。 <code>DISPLAY COMMENT HISTORY</code> 顯示 <code>Order is ready for pickup, but some items not available.</code>。</li>
<li><code>CUSTOMER NOTIFIED</code> 標誌 <code>true</code>。</li>
</ul>
</td>
</tr>
<td><strong>準備裝貨</br></br>完全取消</br>（所有產品均設定為已挑庫，數量為0）</br></strong></td>
<td>
<ol>
<li>下訂單。</li>
<li>請等待訂單同步。</li>
<li>檢查是否已建立發票（如果授權並捕獲）和收到發票電子郵件。</li>
<li>轉到Postman並運行「準備裝貨」請求，所有產品均設定為 <code>picked</code> 與 <code>0 qty</code>。</li>
</ol>
</td>
<td>
<ul>
<li>訂單歷史記錄已更新： <code>We refunded $X offline</code></li>
<li>訂單狀態為 <code>CLOSED</code>。
<li>建立貸項通知單。 （等到cron工作。）</li>
<li>已收到退款電子郵件： <code>$x amount was refunded</code></li>
<li>已發送訂單取消電子郵件。</li>
</ul>
</td>
</tr>
<tr>
<td><strong>準備裝貨 — 部分取消</strong></br></br><strong>(有些產品被挑選，有些則被挑選 <code>0 qty</code>)</strong>
</td>
<td>
<ol>
<li>下訂單。</li>
<li>請等待訂單同步。</li>
<li>檢查是否已建立發票（如果授權並捕獲）和收到發票電子郵件。</li>
<li>轉至Postman，運行「準備裝貨」請求，其中部分產品設定為已挑庫，數量為0，其餘產品已挑庫。</li>
</ol>
</td>
<td>
<ul>
<li><code>Your order is ready for pickup</code> 與 [!UICONTROL Ready for Pickup Items] 和 [!UICONTROL Canceled Items] 的下界。 </li>
<li>訂單狀態為「準備裝貨」。 </li>
<li>訂單歷史記錄已更新： <code>We refunded $X offline.</code>
<li>訂單歷史記錄已更新： <code>Order notified as partly canceled at: Date and hour</code>
<li>已收到退款電子郵件： <code>$x amount was refunded</code>
<li>建立貸項通知單。 （等到cron工作。）</li>
</ul>
</td>
</tr>
<tr>
<td><strong>準備裝貨 — 部分取消</br></br>有些產品被挑選，有些產品被挑選 <code>0 qty</code>)</strong>
</td>
<td><ol>
<li>下訂單。</li>
<li>請等待訂單同步。</li>
<li>檢查是否已建立發票（如果授權並捕獲）和收到發票電子郵件。</li>
<li>轉至Postman，運行「準備裝貨」請求，其中部分產品設定為已挑庫，數量為0，其餘產品已挑庫。</li>
</ol>
</td>
<td><ul>
<li><code>Your order is ready for pickup</code> 與 [!UICONTROL Ready for Pickup Items] 和 [!UICONTROL Canceled Items] 的下界。 </li>
<li>訂單狀態為「準備裝貨」。 </li>
<li>訂單歷史記錄已更新： <code>We refunded $X offline.</code>
<li>訂單歷史記錄已更新： <code>Order notified as partly canceled at: Date and hour</code>
<li>已收到退款電子郵件： <code>$x amount was refunded</code>
<li>建立貸項通知單。 （等到cron工作。）</li>
</ul>
</td>
</tr>
<tr>
<td><strong>分配（在分配期間） </br></br>完全取消（所有產品均設定為拒絕）</strong>
</td>
<td>
<ol>
<li>下訂單。</li>
<li>請等待訂單同步。</li>
<li>檢查是否已建立發票（如果授權並捕獲）和收到發票電子郵件。</li>
<li>轉到Postman並運行「準備裝貨」請求，所有產品均設定為已挑庫。</li>
<li>開啟郵箱，找到「準備接收」電子郵件。 然後，按一下**[!UICONTROL Confirm Arrival]**。</li>
<li>登記。</li>
<li>轉到Postman，運行「分配」請求，並將所有產品設定為拒絕。</li>
</ol>
<td><ul>
<li>訂單歷史記錄已更新： <code>We refunded $X offline.</code></li>
<li>已收到退款電子郵件： <code>$x amount was refunded</code></li>
<li>狀態設定為 <code>CLOSED</code>。</li>
<li>已建立貸項通知單。 （等到cron工作。）</li>
</ul>
</td>
</tr>
<tr>
<td><strong>分配（在分配期間）</br></br>部分取消</br>（一）有的產品配發；有的被拒絕。)</strong>
</br></td>
<td>
<ol>
<li>下訂單。</li>
<li>請等待訂單同步。</li>
<li>檢查是否已建立發票（如果授權並捕獲）和收到發票電子郵件。</li>
<li>轉到Postman，並運行「準備裝貨」請求，所有產品均設定為已挑庫。</li>
<li>開啟郵箱。 查找「準備接收」電子郵件，然後選擇 <code>Confirm Arrival</code>。</li>
<li>登記。</li>
<li>轉到Postman，運行「分配」請求，其中某些產品設定為分配，而某些產品設定為拒絕</li>
</ol>
</td>
<td>
<li>訂單歷史記錄已更新： <code>We refunded $X offline</code></li>
<li><code>Order notified as partly canceled at: Date and Hour</code>
<li>已收到退款電子郵件： <code>$x amount was refunded</code>
<li>訂單狀態設定為 <code>Ready for pickup Dispensed</code>
<li>已建立貸項通知單。 （等到cron工作。）</li>
</td>
</tr>
<tr>
<td> <strong>退貨後新RMA（完全）</strong>
</td>
<td>
<ol>
<li>下訂單。</li>
<li>請等待訂單同步。</li>
<li>驗證發票是否已建立（如果授權並捕獲）並且已收到發票電子郵件。</li>
<li>和Postman一起挑選所有產品。</li>
<li>登記。</li>
<li>做點藥。</li>
<li>轉到訂單，然後選擇<strong>[!UICONTROL Create returns]=
<li>建立RMA。</li>
</ol>
</td>
<td>
<ul>
<li>RMA已建立，並顯示在 <strong>[!UICONTROL Returns]</b> 按鈕。</li>
<li>客戶收到RMA確認電子郵件。</li>
</ul>
</td>
</tr>
<tr>
<td><strong>退貨後新RMA — 部分</strong>
</td>
<td>
<ol>
<li>下訂單。</li>
<li>請等待訂單同步。</li>
<li>檢查是否已建立發票（如果授權並捕獲）和收到發票電子郵件。</li>
<li>和Postman一起挑選所有產品。</li>
<li>登記。</li>
<li>做點藥。</li>
<li>按順序，然後選擇  <strong>[!UICONTROL Create returns]</strong></li>
<li>使用訂購產品的一部分建立RMA。</li>
</ol>
<td>
<ul>
<li>建立並顯示在 <strong>[!UICONTROL Returns]</strong> 按鈕。</li>
<li>客戶收到RMA確認電子郵件。</li>
<li>建立RMA後，獲取RMA授權：從管理員，轉到 <strong>[!UICONTROL Sales > Returns]</strong>。 選擇您建立並授權的RMA。</li>
<li>驗證客戶是否收到RMA授權確認電子郵件。</li>
<li>檢查退款是否已添加到交易記錄和訂單歷史記錄中。</li>
</ul>
</td>
</tr>
</table>


### 儲存履行應用權限

test計畫的此部分涵蓋Store Fulfilment App用戶的帳戶管理。

- 確認儲存關聯可以使用從Adobe Commerce管理員建立的新用戶帳戶進行身份驗證。
- 確認已成功應用對現有帳戶的更新。

**功能區：** Adobe Commerce</br>
**角色：** 管理員，儲存關聯</br>
**Test類型：** 全部為正

<table style="table-layout:auto">
<tr>
<th>函式</th>
<th>方案</th>
<th>預期結果</th>
</tr>
<tr>
<td><strong>用戶帳戶管理 — 建立帳戶</strong></br></br>
</td>
<td>
<ol>
<li><strong>管理</strong>  — 登錄Adobe Commerce管理員</li>
<li>轉到 <strong>[!UICONTROL System] &gt;儲存完成應用程式權限&gt;所有儲存完成應用程式用戶</strong></li>
<li><strong>添加新用戶。</strong></li>
</ol>
<td>
<ul>
<li>帳戶已成功建立。</li>
<li>「New User account（新用戶帳戶）」顯示在 [!UICONTROL Store Fulfillment Users] 控制項欄。</li>
<li><strong>儲存關聯</strong> 使用新用戶帳戶登錄到Store Assist應用。</li>
</ul>
</td>
</tr>
<tr>
<td><strong>用戶帳戶管理 — 更新現有用戶帳戶</strong>
</td>
<td>
<ol>
<li>使用管理員用戶帳戶登錄Adobe Commerce管理員。</li>
<li>轉到 <strong>[!UICONTROL System] &gt;儲存完成應用程式權限&gt;所有儲存完成應用程式用戶</strong>。</li>
<li>在「用戶帳戶」清單中，通過選擇 <strong>[!UICONTROL Edit]</strong>。
<li>通過更改禁用帳戶 <strong>[!UICONTROL Is Active]</strong> 至 <strong>否</strong>。</li>
</ol>
</td>
<td>
<ul>
<li>在 <strong>[!UICONTROL Store Fulfillment App Users]</strong> 儀表板，更新帳戶的狀態更改為 <strong>[!UICONTROL Inactive]</strong>。</li>
<li>儲存關聯無法使用非活動帳戶憑據登錄到Store Assist應用。</li>
</ul>
</td>
</tr>
</table>

## Adobe Commerce產品類型

「Adobe Commerce產品類型」的test方案驗證客戶是否看到不同產品類型的正確產品、庫存和交貨方法資訊：

- [!UICONTROL Configurable]
- [!UICONTROL Grouped]
- [!UICONTROL Virtual]
- [!UICONTROL Bundle products] 在Adobe Commerce店面。

**功能區：** Adobe Commerce額</br>
**角色：** Store Assist應用程式用戶(Store Associate)</br>
**Test類型：** 全部為正

<table style="table-layout:auto">
<tr>
<th>函式</th>
<th>方案</th>
<th>注釋</th>
</tr>
<tr>
<td><strong>可配置產品</strong>
</td>
<td>
<ul>
<li>驗證用戶是否只能查看那些可配置的選項（已啟用哪個來源、分配了庫存以及存貨中的某些物料） — 檢查子產品。</li>
<li>驗證選擇其他儲存時，不可用的選項顯示為划出。</li>
<li>驗證如果用戶選擇了不同的儲存區，則可配置選項將取消選中。</li>
<li>驗證可配置產品是否已在購物車中，並且用戶選擇了不同的商店，則產品將顯示為庫存不足。</li>
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
<li>驗證交付方法和 [!UICONTROL Add to cart] 按鈕在所有子產品都具有
<code>qty</code> 設定為 <code>0</code>。</li>
<li>驗證當至少有一個子產品具有 <code>qty</code> 設定為 <code>0.</code></li>
<li>驗證 [!UICONTROL Store Pickup Delivery] 方法僅對具有 [!UICONTROL Available for Store Pickup] 啟用。 （檢查子產品。）</li>
</ul>
</td>
<td></td>
</tr>
<tr>
<td><strong>虛擬產品</strong>
</td>
<td>
驗證虛擬產品是否不提供  [!UICONTROL In-store Pickup] 傳遞方法。
<td></td>
</td>
</tr>
<tr>
<td><strong>捆綁產品</strong>
</td>
<td>
<ul>
<li>驗證是否至少有一個子產品 [!UICONTROL Available for Store Pickup] 禁用後，「商店提貨交貨」選項對客戶不可用。</li>
<li>驗證是否至少有一個子產品 [!UICONTROL Available for Home Delivery] 禁用後，「首頁交付」選項對客戶不可用。</li>
<li>驗證捆綁包中的至少一個子產品是否庫存不足，該捆綁包（父產品）還顯示為 [!UICONTROL Out of stock]。</li>
</ul>
</td>
<td></td>
</tr>
<tbody>
</table>

## 簽入體驗

test計畫的此部分包括以下功能的「儲存代貨單的簽入體驗」：

- 替代裝貨聯繫人 — 驗證用於添加 [!UICONTROL Alternate Pickup Contact] 選擇 [!UICONTROL Preferred Contact] 商店代貨訂單。

- 簽入表單 — 驗證提交儲存裝貨單簽入請求的工作流。

**功能區：** 購物車結帳，簽入儲存裝貨單的表單</br>
**角色：** 管理員、客戶、儲存關聯</br>
**Test類型：** 全部為正

### 替代裝貨聯繫人


**功能區：** 購物車結帳</br>
**角色：** 客戶</br>
**Test類型：** 全部為正

<table style="table-layout:auto">
<tr>
<th>函式</th>
<th>方案</th>
<th>預期結果</th>
</tr>
<tr>
<td><strong>替代裝貨聯繫人</br>
簽入</br><strong>
</td>
<td>
客戶使用「店內裝貨」選項提交訂單。</td>
<td>在結帳過程中，客戶看到 [!UICONTROL Alternate Pickup Contact] 選項。
</td>
</tr>
<tr>
<td><strong>替代提貨首選聯繫人，簽入</strong>
<td>
客戶使用「店內裝貨」選項提交訂單。 在結帳期間，客戶添加 [!UICONTROL Alternate Pickup Contact]。</td>
<td>在結帳過程中，客戶看到 [!UICONTROL Preferred Contact] 的上界。</td>
</td>
</tr>
<tr>
<td><strong>替代裝貨聯繫人詳細資訊，簽入</strong>
</td>
<td>
客戶使用「店內裝貨」選項提交訂單。 結帳期間，客戶選擇 [!UICONTROL Alternate Pickup Contact] 裝船步驟。
</td>
<td>客戶將看到輸入選項以輸入聯繫人詳細資訊： [!UICONTROL First name]。 [!UICONTROL Last name]。 [!UICONTROL Phone], [!UICONTROL Email]。</td>
</tr>
<tr>
<td><strong>備用代收、簽入電子郵件</strong>
</td>
<td>客戶使用「店內裝貨」選項提交訂單。 結帳期間，客戶選擇 [!UICONTROL Alternate Pickup Contact] 在發運步驟中，添加聯繫人詳細資訊並提交訂單。</td>
<td>客戶和備用聯繫人均收到訂單的「簽入電子郵件」。</td>
</tr>
<td><strong>替代裝貨，訂單詳細資訊</strong></td>
<td>客戶使用「店內裝貨」選項提交訂單。 結帳期間，客戶選擇 [!UICONTROL Alternate Pickup Contact] 在發運步驟中，添加聯繫人詳細資訊並提交訂單。</td>
<td>管理員看到有關已保存訂單的其他聯繫資訊。</td>
</tr>
<tr>
<td><strong>替代代料接收聯繫人，儲存關聯訂單視圖</strong>
</td>
<td>客戶使用「店內裝貨」選項提交訂單。 結帳期間，客戶選擇 [!UICONTROL Alternate Pickup Contact] 在發運步驟中，添加聯繫人詳細資訊並提交訂單。</td>
<td>Store Associate可以在FaaS/ChaaS中查看有關訂單的其他聯繫資訊。</td>
</td>
</tr>
</tbody>
</table>

### 簽入表單


**功能區：** 簽入表單</br>
**角色：** 客戶</br>
**Test類型：** 全部為正

<table style="table-layout:auto">
<tr>
<th>函式</th>
<th>方案</th>
<th>預期結果</th>
</tr>
<tr>
<td><strong>簽入操作 — 提交請求</strong>
</td>
<td>在簽入表單上，客戶完成所有必填欄位，然後提交請求。</td>
<td>客戶收到成功響應。</td>
</tr>
<tr>
<td><strong>簽入操作 — 查看請求詳細資訊</strong></td>
<td>客戶成功提交簽入請求。</td>
<td>FaaS系統中的訂單狀態更新，Store Associate可以在FaaS中查看簽入請求詳細資訊。
</td>
</tr>
<tr>
<td><strong>簽入操作 — 僅提交一次請求</strong></td>
<td>在提交訂單的簽入請求後，客戶選擇連結以再次簽入。</td>
<td>在「簽入」表單上，客戶看不到編輯或重新提交表單的選項。</td>
</tr>
<tr>
<td><strong>簽入操作 — 確認到貨</strong></td>
<td>在FaaS中，店內提貨訂單已標籤為可提貨。 客戶收到「準備接收」電子郵件，並選擇 [!UICONTROL Confirm Arrival]。</td>
<td>客戶看到訂單的「簽入」表單。</td>
</tr>
</tbody>
</table>

## 應用商店協助

test計畫的這一部分介紹了在Store Assist應用中測試訂單、選擇和切換工作流的方案。

**功能區：** 應用商店協助</br>
**角色：** 儲存關聯</br>
**Test類型：** 全部為正

<table style="table-layout:auto">
<tr>
<th>函式</th>
<th>方案</th>
<th>預期結果</th>
</tr>
<tr>
<td>
<strong>單次領料快樂路徑，彎邊領料</strong></td>
<td>挑選單個和多數量物料。 不提貨，也不提貨（有分段）。
</td>
<td>
</td>
</tr>
<tr>
<td><strong>多訂單領料 — 快樂路徑、彎邊領料</strong></td>
<td>單個和多數量物料。 無Nilpicks和Curbside拾取（帶分段）</td>
<td></td>
</tr>
<tr>
<td><strong>單個訂單領料 — 店內快捷路徑提貨</strong></td>
<td>單個和多數量物料。 無Nilpicks ，並在儲存中提貨（帶暫存）</td>
<td>
</td>
</tr>
<tr>
<td><strong>多訂單領料 — 快樂路徑，店內領料</strong></td>
<td>挑選單個和多數量物料。 不提貨，也不提貨（有分段）。</td>
<td></td>
</tr>
<tr>
<td><strong>單訂單領料 — 不快樂路徑，店內提貨</strong></td>
<td>帶有部分和零件的單件和多件物料的挑庫和儲存內挑庫（帶分段）</td>
</td>
<td></td>
</tr>
<td><strong>多訂單領料 — 不快樂的路徑邊撿料</strong></td>
<td>帶有部分和零件的單件和多件物料的挑庫和儲存內挑庫（帶分段）</td>
<td></td>
</tr>
<td><strong>單訂單領料 — 不快樂路徑，彎邊領料</strong></td>
<td>挑選單件和多件物料，包括部分和零件挑庫和庫邊提庫（帶分段）</strong></td>
</td>
<td></td>
</tr>
<tr><td><strong>已下訂單 — 領料前已取消</strong></td>
<td></td>
<td></td>
</tr>
<tr>
<td><strong>已下訂單 — 切換前取消</strong></td>
<td></td>
<td></td>
</tr>
<tr>
<td><strong>訂單 — 按訂單搜索模組</strong></td>
<td></td>
<td></td>
</tr>
<tr><td><strong>訂單 — 搜索和手動簽入以進行切換</strong></td>
<td></td>
<td></td>
</tr>
<tr><td><strong>已下訂單 — 所有物料都未領料或由選取器標籤為不可用</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>與捆綁項目一起下單 — 領料和切換</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>已下訂單 — 與拒絕交手</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>已下訂單 — 放棄所有物料</strong></td>
<td></td>
<td></td></tr>
</tbody>
</table>



## 部署

在驗證解決方案已按您的規格配置和測試後，您已準備好從試運行部署到生產。

部署和測試因基礎架構和功能而異。

>[!TIP]
>
>有關Adobe Commerce雲基礎架構項目的部署指南、核對清單和最佳實踐，請參閱 [部署儲存](https://devdocs.magento.com/cloud/live/stage-prod-live.html) 在Adobe Commerce開發人員文檔中。




















