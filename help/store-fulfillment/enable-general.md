---
title: 常規配置
description: 配置常規設定以啟用 [!DNL Store Fulfillment] 給你的店。 配置全局擴展設定、記錄、資料同步和安全性的系統設定。 提供關鍵資料，以實現Adobe Commerce和儲存履行服務之間的整合。
role: User, Admin
level: Intermediate
exl-id: 51dcfc95-3dd6-40d9-bd26-d8409a25f3c8
source-git-commit: e7493618e00e28e2de5043ae2d7e05a81110d8f1
workflow-type: tm+mt
source-wordcount: '2440'
ht-degree: 0%

---

# 儲存服務和銷售配置

配置 [!DNL Store Fulfillment] 從 [!DNL Commerce] 管理員：啟用擴展、指定擴展設定、配置Store Assist應用用戶的安全設定，以及設定傳遞方法的選項。

>[!IMPORTANT]
>
>僅在您連接Adobe Commerce實例和 [!DNL Store Fulfillment] 的子菜單。 請參閱 [連接儲存履行](connect-set-up-service.md)。

## 管理儲存履行服務設定

從管理 [!DNL Commerce Admin Store Configuration] 的子菜單。

- 通過選擇以啟用擴展、配置全局設定，以及為Store Assist應用程式用戶連接和帳戶指定安全選項 **[!UICONTROL Stores > Configuration > Services > Store Fulfillment by Walmart Commerce Technologies]**。

   ![儲存履行的管理儲存服務配置](assets/store-services-admin-sf-config.png)

- 通過選擇 **[!UICONTROL Store > Configuration > Sales > Delivery Methods > In-Store Pickup]**。

   ![Admin Store銷售配置用於Store Fullment](assets/store-sales-admin-sf-deliver-config.png)

## 基本設定

<table>
<thead>
<tr>
<td><strong>欄位</strong></td>
<td><strong>說明</strong></td>
<td><strong>範圍</strong></td>
<td><strong>必需</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Price]</strong></td>
<td>您向客戶收取的店內裝貨價格。 預設為零。</td>
<td>網站</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Search Radius]</strong></td>
<td>購物者在店前結賬處搜索商店取貨位置時使用的半徑（以公里為單位）。 搜索結果僅返回位於指定搜索半徑內的儲存。</td>
<td>網站</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Displayed error message]</strong></td>
<td>當客戶為不可用於店內裝貨的物料選擇店內裝貨時顯示的消息。 如果需要，可以自定義預設文本。
</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>的 [!UICONTROL Search Radius] 僅當配置了 [儲存位置和映射設定](store-location-map-provider-setup.md) Adobe Commerce。

## 啟用「儲存履行」解決方案

啟用 [!DNL Store Fulfillment] 解決方案，將店內和路邊的提貨功能添加到您的Adobe Commerce店面的購物和結賬體驗中。

<table>
<thead>
<tr>
<td><strong>欄位</strong></td>
<td><strong>說明</strong></td>
<td><strong>範圍</strong></td>
<td><strong>必需</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL Enabled]</strong></td>
<td>啟用或禁用解決方案。 啟用後，配置和使用「儲存履行」功能，並建立您的Adobe Commerce儲存與 [!DNL Store Fulfillment] 服務。 禁用後，所有商店履行功能都將被禁用，而且Adobe Commerce和商店履行服務之間沒有通信。 無法處理或接收訂單資訊。</td>
<td>網站</td>
<td>是</td>
</tr>
</tbody>
</table>

## 添加帳戶憑據

<table>
<tr>
<td><strong>欄位</strong></td>
<td><strong>說明</strong></td>
<td><strong>範圍</strong></td>
<td><strong>必需</strong></td>
</tr>
<tr>
<td><strong>[!UICONTROL Environment]</strong></td>
<td>選擇 <i>[!UICONTROL Sandbox]</i> 或 <i>[!UICONTROL Production]</i><br></br>選擇 [!UICONTROL Sandbox] 允許在test環境中與履行服務進行通信。<br></br>選擇 [!UICONTROL Production] 在即時環境中實現與履行服務的通信。<br></br>您為每個環境提供了一組憑據，並可以在同一安裝中管理這兩組憑據。 <br></br>在驗證連接之前保存憑據。</td>
<td>全球</td>
<td>是</td>
</tr>
<tr>
<td><strong>[!UICONTROL API Server URL]</strong></td>
<td>Walmart Store Fulfilment API終結點的URL。 這必須是在登機過程中提供的完全限定的URL。 儲存履行客戶同時收到沙盒和生產URL。 添加值時，請確保複製並貼上完整URL，包括尾斜槓「/」。</td>
<td>全球</td>
<td>是</td>
</tr>
<tr>
<td><strong>[!UICONTROL Token Auth Server URL]</strong></td>
<td>Walmart Store Fulfilment Authentication終結點的URL。 值必須是在登機過程中提供的完全限定的URL。 您同時收到沙盒和生產URL。 添加值時，請確保複製並貼上完整URL，包括尾斜槓「/」。</td>
<td>全球</td>
<td>是</td>
</tr>
<tr>
<td><strong>[!UICONTROL Merchant Id]</strong></td>
<td>在登機過程中提供的唯一商戶（租戶）ID。 此ID用於傳遞訂單以確保您的商戶商店接收訂單。</td>
<td>全球</td>
<td>是</td>
</tr>
<tr>
<td><strong>[!UICONTROL Consumer Id]</strong></td>
<td>在登機過程中提供的唯一整合ID。 此ID用於驗證Adobe Commerce和儲存履行服務之間的所有通信</td>
<td>全球</td>
<td>是</td>
</tr>
<tr>
<td><strong>[!UICONTROL Consumer Secret]</strong></td>
<td>在登機過程中提供的唯一整合密鑰。 此密鑰用於驗證Adobe Commerce和儲存履行服務之間的所有通信。</td>
<td>全球</td>
<td>是</td>
</tr>
</table>

配置 [!UICONTROL Account Credentials]選中 <strong>[!UICONTROL Validate Credentials]</strong> 驗證並首次建立到儲存履行服務的連接。

## 配置日誌記錄

日誌檔案中提供了用於儲存履行服務的日誌 `var/log/walmart-bopis.log`。

請系統管理員配置您的環境以允許異常處理，以便通過防火牆或快取捕獲與API相關的異常。

因為應用程式日誌檔案可以快速增長，所以僅在需要時為應用程式啟用記錄 — 例如，在對儲存完成問題進行故障排除時 [!DNL Commerce] 命令。 此配置可防止由於大型日誌檔案而導致的生產環境中的響應時間問題。

>[!TIP]
>
>對於Adobe Commerce本地安裝，請讓系統管理員為 `var/log/walmart-bopis.log` 檔案來最小化大小。 有關Adobe Commerce內部安裝，請參見 [日誌旋轉](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html#server-settings) 的 _Adobe Commerce安裝指南_。 有關Adobe Commerce雲基礎架構項目，請參閱 [查看和管理日誌](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html)。

<table>
<thead>
<tr>
<td><strong>欄位</strong></td>
<td><strong>說明</strong></td>
<td><strong>範圍</strong></td>
<td><strong>必需</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Debug Mode]</strong></td>
<td>調試模式用於增加整合中記錄的活動。 禁用時，不記錄調試資訊。 啟用後，將記錄所有調試資訊 <br></br>在檔案中可找到所有記錄的資料： <pre>var/log/walmart-bopis.log</pre>
<td>全球</td>
<td>否</td>
</tr>
</tbody>
</table>

## 管理訂單同步

配置設定以管理訂單同步的錯誤處理、用於在訂單領料期間進行條形碼掃描的目錄屬性，以及為儲存履行隊列配置訂單批大小。

您可以從管理員(
<strong>[!UICONTROL System > Tools > Store Fulfillment Queue]</strong>)。

### 同步錯誤管理

<table>
<tr>
<td><strong>欄位</strong></td>
<td><strong>說明</strong></td>
<td><strong>範圍</strong></td>
<td><strong>必需</strong></td>
</tr>
<tr>
<td><strong>[!UICONTROL Retry Critical Error]</strong></td>
<td>指定發生嚴重錯誤後記錄同步操作的重試嘗試。<br></br>當整合未能從履行服務中獲得正面響應時，就會出現嚴重錯誤。 當服務關閉或發送的訂單資料出錯時，可能會發生這種情況。<br></br>達到重試閾值後，該項將保留在隊列中，但不會再次處理。 查看所有出錯的項 <strong>[!UICONTROL System > Tools > Store Fulfillment Queue]</strong> 管理中的管理。 要對持續出現故障的項目進行故障排除，請與客戶經理聯繫。</td>
<td>全球</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Error Notification Email]</strong></td>
<td>啟用錯誤通知以在 [!UICONTROL Retry Critical Error Threshold] 的子菜單。 通知包括有關錯誤的任何可用詳細資訊。</td>
<td>全球</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Send Error Notification Email To]</strong></td>
<td>錯誤通知的收件人電子郵件地址的逗號分隔清單。</td>
<td>全球</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Order Sync Exception Email Template]</strong></td>
<td>指定用於通知收件人訂單同步錯誤的電子郵件模板。 提供了預設模板。 它不支援定制。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
</table>

### 訂單同步

<table>
<thead>
<tr>
<td><strong>欄位</strong></td>
<td><strong>說明</strong></td>
<td><strong>範圍</strong></td>
<td><strong>必需</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Barcode Source]</strong></td>
<td>儲存商戶位置中相應物料的可掃描代碼的目錄屬性。<br></br>如果您只有一個現有商戶地點，則很可能使用UPC代碼，而您的電子商務渠道則按SKU標識產品。 如果這是您的方案，請選擇包含UPC代碼的目錄屬性。<br></br>此設定可確保發送到您的商店的訂單清單項目具有正確的標識符，以便商店關聯在領料過程中能夠準確掃描項目。<br></br>如果您不確定，請與發運和領料部門的履單聯繫人聯繫，以確定應發送哪個屬性。 如果該屬性當前未包括在資料庫中，則可能需要將相應的屬性添加到Adobe Commerce產品屬性集。</td>
<td>網站</td>
<td>是</td>
</tr>
<tr>
<td><strong>[!UICONTROL Barcode Type]</strong></td>
<td>在您的商家位置中儲存相應物料的條形碼源的目錄屬性。<br></br>此設定可確保發送給您的商店的訂單清單項目具有正確的標識符，以便商店關聯在領料過程中能夠準確掃描項目。 這些選項包括 — SKU、UPC、GTIN、UPCA、EAN13、UPCE0、DISA、UAB、CODABAR、Price Embedded UPC。<br></br>如果不確定，請選擇與包含的值最相似的選項 [!UICONTROL Barcode Source] 屬性。 儲存關聯仍然可以從其挑庫清單中手動匹配項目。</td>
<td>網站</td>
<td>是</td>
</tr>
<tr>
<td><strong>[!UICONTROL Max Number of Items]</strong></td>
<td>一次要從儲存履行隊列發送的最大項目數。<br></br>BOPIS訂單按定期分批發送給履行服務。 此設定允許您控制批的大小。<br></br>預設值為100個項目。 根據訂單數量和容量，您可能需要向上或向下調整此值。</td>
<td>全球</td>
<td>否</td>
</tr>
</tbody>
</table>

## 啟用商店完成發運選項

配置商店履行發運選項，以確定您的Adobe Commerce商店的店內提貨和送貨上門選項的可用性。

### 收貨方商店

<table>
<thead>
<tr>
<td><strong>欄位</strong></td>
<td><strong>說明</strong></td>
<td><strong>範圍</strong></td>
<td><strong>必需</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Enable Ship To Store]</strong></td>
<td>送貨上門設定基於您現有的送貨上門功能。 如果您使用Inventory management，或者您可以通過商店到商店的庫存轉移在沒有庫存的商家地點接受和履行訂單，請將此選項設定為「是」。<br></br>如果您不支援「送貨到商店」選項或不想提供它，請設定為「否」。 禁用時，目錄中商店庫存為零的物料，或該位置以下的物料 [!DNL Out of Stock Threshold]，不提供店內裝貨選項。<br></br>這是一個全局設定，可以按商家位置調整。</td>
<td>全球</td>
<td>否</td>
</tr>
</tbody>
</table>

### 發貨商店

<table>
<thead>
<tr>
<td><strong>欄位</strong></td>
<td><strong>說明</strong></td>
<td><strong>範圍</strong></td>
<td><strong>必需</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong></td>
<td>在商店中啟用或禁用「送貨上門」選項。 啟用後，您的商家商店地點將與與網站關聯的庫存中的其他分配來源一起考慮。<br></br>在標準的Inventory management服務中， [!DNL Ship from Store] is選項是固有的，無法禁用。 使用Store Fulliment解決方案，您可以開啟或關閉它。<br></br>這是一個全局設定。 您還可以根據商家位置和產品調整此設定。</td>
<td>全球</td>
<td>否</td>
</tr>
</tbody>
</table>


## 管理應用商店履行應用使用帳戶和權限

配置Store Fulfillment App用戶帳戶和密碼安全性的設定以及二元身份驗證。

### 應用安全

<table>
<thead>
<tr>
<td><strong>欄位</strong></td>
<td><strong>說明</strong></td>
<td><strong>範圍</strong></td>
<td><strong>必需</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL User Session Lifetime]</strong></td>
<td>儲存關聯用戶會話在自動註銷之前保持活動的時間段（秒）。 有效值範圍從60到31536000。</td>
<td>全球</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Maximum Login Failures to Lockout Account]</strong></td>
<td>指定在將儲存關聯鎖定到其帳戶之外之前允許的失敗登錄嘗試次數。<br></br>要禁用帳戶鎖定，請將值設定為0。</td>
<td>全球</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Lockout Time (minutes)]</strong></td>
<td>登錄失敗後鎖定帳戶的分鐘數。</td>
<td>全球</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Force Password Change]</strong></td>
<td><em>[!UICONTROL Yes]</em>:要求用戶在設定帳戶後更改其密碼。<br></br><em>[!UICONTROL No]</em>:建議用戶在設定帳戶後更改密碼。</td>
<td>全球</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Password Lifetime]</strong></td>
<td>在更改所需密碼之前密碼保持有效的天數。 留空以禁用此選項。</td>
<td>全球</td>
<td>否</td>
</tr>
</tbody>
</table>

## 傳遞方法

通過擴展本地Adobe Commerce [!DNL In-Store Delivery] 功能。 安裝擴展後，可以使用添加到管理員的以下擴展設定來配置店內傳遞方法。

- **店內提貨** — 在結帳過程中提供店內交貨選項這是BOPIS訂單最常見的交貨方案。

- **[!UICONTROL Curbside pick up]** — 為客戶提供選擇，讓其停放在商店地點，並由商店聯營商將訂單交付給客戶。

通過選擇 <strong>[!UICONTROL Stores > Configuration > Sales > Delivery Methods > In-Store Pickup]</strong>。

>[!NOTE]
>
>有關配置店內交貨選項的其他資訊，請參見 [店內交貨](https://docs.magento.com/user-guide/shipping/shipping-in-store-delivery.html) 的 _Adobe Commerce使用手冊_。


### 傳遞方法配置

使用店內交貨方法，客戶可以選擇在結帳期間用作提貨地點的來源。

<table>
<thead>
<tr>
<td><strong>欄位</strong></td>
<td><strong>說明</strong></td>
<td><strong>範圍</strong></td>
<td><strong>必需</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL Enable In-Store Pickup]</strong></td>
<td>啟用或禁用在結帳期間為選擇商店提貨的客戶提供的商店內提貨選項。 禁用店內拾取時，不顯示該選項。<br></br>此全局設定適用於所有零售商店位置。 啟用後，可以在零售商店位置有選擇地禁用它。</td>
<td>網站</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Curbside Pickup]</strong></td>
<td>在為選擇儲存提貨的客戶進行結帳過程中，啟用或禁用庫邊提貨選項。<br></br>此全局設定適用於所有零售商店位置。 啟用後，可以在零售商店位置有選擇地禁用它。</td>
<td>網站</td>
<td>否</td>
</tr>
</tbody>
</table>

### 傳遞方法標題配置

<table>
<thead>
<tr>
<th><strong>欄位</strong></th>
<th><strong>說明</strong></th>
<th><strong>範圍</strong></th>
<th><strong>必需</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>首頁交付標題</strong></td>
<td>指定要在產品、購物車和結帳區域中顯示「送貨上門」選項的標題。 送貨上門是指Adobe Commerce的標準送貨功能 — 從倉庫、承運人或直接到客戶提供的送貨地址。 </br></br>此標籤不會影響所選裝運承運人的裝運方法標籤。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<tr>
<td><strong>首頁交付說明</strong></td>
<td>一個可選說明，在客戶顯示「主交貨標題」時顯示。 通常，描述是傳遞您的傳遞承諾的靜態消息。 一些示例：</br><code>Same-day shipping on orders by 4</code></br></br><code>Ships within 2 business days</code></td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<tr>
<td><strong>儲存裝貨標題</strong></td>
<td>當向客戶提供交貨選項並提供店內提貨時，將顯示此標籤。 </br></br>您可以自定義此標籤，該標籤顯示在產品、購物車和結帳區域中。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<td><strong>儲存裝貨說明</strong></td>
<td>無論「商店提貨標題」顯示在何處，您都可以根據需要包括說明。 此靜態消息有助於改善與商店取貨體驗相關的客戶通信。 一些示例：</br></br><code>Get it today for free!</code></br></br><code>Ready for pickup in an hour!</code></td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<tr>
<td><strong>店內取貨標題</strong></td>
<td>啟用「店內提貨」後，此標題將作為「商店提貨交貨」選項顯示給客戶。 可以自定義其標籤。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<tr>
<tr>
<td><strong>曲邊拾取標題</strong></td>
<td>啟用「庫邊裝貨」後，該選項將作為「商店裝貨交貨」選項的類型顯示給客戶。 您可以在此處自定義其標籤。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<tr>
<td><strong>儲存中拾取說明</strong></td>
<td>當訂單準備在您的零售店取貨時，會通過電子郵件通知客戶。 如果客戶已選擇 [!DNL In-Store Pickup] 在簽出期間，您可以在此處自定義裝貨說明。 </br></br>這是一個適用於所有零售商店位置的全局設定。 您還可以在零售商店位置級別自定義說明。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<tr>
<td><strong>曲邊拾取說明</strong></td>
<td>指定要包含在客戶電子郵件通知中的庫邊裝貨訂單的自定義訂單裝貨說明。 </br></br>這是一個適用於所有零售商店位置的全局設定。 您還可以在零售商店位置級別自定義說明。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<tr>
<td><strong>估計提貨提前期</strong></td>
<td>接收、履行和準備接收訂單前所需的分鐘數。 在為「商店提貨交貨」選項選擇零售商店位置時，此資訊將顯示給客戶。 這是全局設定，適用於所有零售商店位置。 您還可以在零售商店位置層自定義提前期。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<tr>
<td><strong>估計裝貨時間標籤</strong></td>
<td>顯示在訂單可用於客戶裝貨之前的估計時間。 當客戶為 [!DNL In-Store Pickup] 「交貨」選項。 </br></br>自定義此標籤時，可以使用 <code>%1</code> 插入 <strong>估計提貨提前期</strong>。 例如：</br></br><code>Ready for Pickup in %1 minutes.</code></br></br>這是一個適用於所有零售商店位置的全局設定。 您還可以在零售商店位置層自定義提前期。</br></br><code>Ready for Pickup in %1 minutes.</code></br></br></td>
<td>儲存視圖</td>
<td>否</td>
<tr>
<td><strong>裝貨時間免責聲明</strong></td>
<td>在產品頁面上顯示的內容在工具提示中列出儲存時間、節假日、意外關閉等</td>
<td>儲存視圖
</td>
<td>否
</td>
</tr>
</tbody></table>

### 庫存可用性標題配置

<table>
<thead>
<tr>
<th><strong>欄位</strong></th>
<th><strong>說明</strong></th>
<th><strong>範圍</strong></th>
<th><strong>必需</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>庫存</strong></td>
<td>當客戶使用零售商店貨位時，每個地點都顯示當前物料的庫存可用性。 </br></br>您可以自定義 <em>[!UICONTROL in-stock]</em> 狀態標籤。</br></br></td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<tr>
<td><strong>缺貨</strong></td>
<td>當客戶使用零售商店貨位時，每個地點都會顯示任何當前物料的庫存可用性。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<tr>
<td><strong>部分庫存</strong></td>
<td>當客戶使用零售商店貨位時，每個地點都顯示任何當前物料的庫存可用性。 </br></br>您可以自定義 <em>[!UICONTROL partially in-stock]</em> 狀態標籤。</br></br></td>
<td>儲存視圖</td>
<td>否</td>
</tr>
</tbody></table>

