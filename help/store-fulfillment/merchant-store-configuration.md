---
title: 商家商店設定
description: 將增強的Inventory management來源設定為商家商店。
role: User, Admin
level: Intermediate
exl-id: 7c3444d0-5ecb-4ac1-aa81-e48eea290f5d
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '1206'
ht-degree: 0%

---

# 商家商店（來源）設定

此解決方案藉由擴充庫存來源，為商家提供以作業為導向的功能，進而增強原生Inventory management功能。

- 新增商店位置的地理座標
- 將來源指定為 [!DNL Store Pickup Location] 並指定可用的送貨功能（送貨地點商店、出貨地點商店）
- 指定可用的取車選項（店內或路邊）、自訂取車指示，以及其他資訊，以便向客戶傳達取車詳細資訊和指示

條款 _source_ 和 _商家商店位置_ 可互換使用。 所有記錄都是存貨來源，但來源也可以是商家商店位置，具體取決於組態設定。

從管理員管理商戶商店設定： **[!UICONTROL Stores > Inventory > Sources >  Edit Source]**.

>[!NOTE]
>
>在設定過程中，您可能需要在建立來源或更新現有來源後清除快取。

## **一般**

<table>
<tbody>
<tr>
<th>欄位</th>
<th>說明</th>
<th>範圍</th>
<th>必填</th>
</tr>
<tr>
<td><strong>[!UICONTROL Latitude]</strong></br><code>Base Attribute: latitude</code></td>
<td>商家商店位置的緯度座標。 此必要資訊會用於店面體驗中的位置搜尋和地圖放置。 值必須符合存放區的確切位址，才能通過驗證。</td>
<td>全域</td>
<td>是</td>
</tr>
<tr>
<td><strong>[!UICONTROL Longitude]</strong></br><code>Base Attribute: Longitude</code></td>
<td>商家商店位置的縱向座標。 此必要資訊會用於店面體驗中的位置搜尋和地圖放置。 值必須符合存放區的確切位址，才能通過驗證。</td>
<td>全域</td>
<td>是</td>
</tr>
<tr>
<td><strong>[!UICONTROL Use as Pickup Location]</br></strong><code>Base Attribute: is_pickup_location_active</code></td>
<td>將來源指定為可用的商店取貨地點。 此設定會決定是否同步來源並向訪客顯示。</td>
<td>全域</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship to Store]</strong><br><code>Extension Attribute: allow_ship_to_store</code></td>
<td>在來源層級設定送貨至商店功能。 如需詳細資訊，請參閱[一般組態](enable-general.md)選項， <strong>[!UICONTROL Enable Ship To Store]
</tr>
<tr>
<td><strong>[!UICONTROL Latitude]</strong></br><code>Base Attribute: latitude</code></td>
<td>商家商店位置的緯度座標。 此必要資訊會用於店面體驗中的位置搜尋和地圖放置。 值必須符合存放區的確切位址，才能通過驗證。</td>
<td>全域</td>
<td>是</td>
</tr>
<tr>
<td><strong>[!UICONTROL Longitude]</strong></br><code>Base Attribute: Longitude</code></td>
<td>商家商店位置的縱向座標。 此必要資訊會用於店面體驗中的位置搜尋和地圖放置。 值必須符合存放區的確切位址，才能通過驗證。</td>
<td>全域</td>
<td>是</td>
</tr>
<tr>
<td><strong>[!UICONTROL Use as Pickup Location]</br></strong><code>Base Attribute: is_pickup_location_active</code></td>
<td>將來源指定為可用的商店取貨地點。 此設定會決定是否同步來源並向訪客顯示。</td>
<td>全域</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship to Store]</strong></br> <code>Extension Attribute: [!DNL allow_ship_to_store]</code></td>
<td>在來源層級設定送貨至商店功能。 如需詳細資訊，請參閱[一般組態](enable-general.md)選項， <strong>[!UICONTROL Enable Ship To Store]</strong>.</td>
<td>全域</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong></br><code>Extension Attribute: [!DNL use_as_shipping_source]</code></td>
 <td>在來源層級設定出貨地點儲存功能。 如需詳細資訊，請參閱[一般組態](enable-general.md)選項， [!UICONTROL Enable Ship From Store].</td>
<td>全域</td>
<td>否</td>
</tr>
<tr>
<td>全域</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong><code>Extension Attribute: [!DNL use_as_shipping_source]</code></td><td></td><td></td><td></td></tr></tbody></table>



| **欄位** | **說明** | **範圍** | **必填** |
|--------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Latitude]**</br>`Base Attribute: latitude` | 商家商店位置的緯度座標。 此必要資訊會用於店面體驗中的位置搜尋和地圖放置。 值必須符合存放區的確切位址，才能通過驗證。 | 全域 | 是 |
| **[!UICONTROL Longitude]**</br>`Base Attribute: Longitude` | 商家商店位置的縱向座標。 此必要資訊會用於店面體驗中的位置搜尋和地圖放置。 值必須符合存放區的確切位址，才能通過驗證。 | 全域 | 是 |
| **[!UICONTROL Use as Pickup Location]**</br>`Base Attribute:[!DNL is_pickup_location_active]` | 將來源指定為可用的商店取貨地點。 此設定會決定是否同步來源並向訪客顯示。 | 全域 | 否 |
| **[!UICONTROL Enable Ship to Store]**</br>`Extension Attribute: [!DNL allow_ship_to_store]` | 在來源層級設定送貨至商店功能。 如需詳細資訊，請參閱 [一般設定](enable-general.md) 選項， **[!UICONTROL Enable Ship To Store]**. | 全域 | 否 |
| **[!UICONTROL Enable Ship From Store]**</br>`Extension Attribute: [!DNL use_as_shipping_source]` | 在來源層級設定出貨地點儲存功能。 如需詳細資訊，請參閱 [一般設定](enable-general.md) 選項， [!UICONTROL Enable Ship From Store] | 全域 | 否 |

{style="table-layout:auto"}

## 取車地點設定

| **欄位** | **說明** | **範圍** | **必填** |
|-----------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Allow In-Store Pickup]**</br>`Extension Attribute: [!DNL store_pickup_enabled]` | 兩個取車選項之一。 [!DNL In-Store Pickup] 是指允許客戶進入商家商店位置以擷取其訂單的能力。 </br></br>啟用後，此選項可能會在結帳期間顯示給客戶。 </br></br>此選項也會將全域設定覆寫為 [!UICONTROL Enable In-store Pickup] 已在 [!UICONTROL Delivery Method] 的 [!UICONTROL In-store Pickup] | 全域 | 否 |
| **店內取貨指示**</br>`Extension Attribute: store_pickup_instructions` | 傳送給客戶的可自訂訊息，位於 **已準備好在商店取貨的訂單** 電子郵件通知。 | 全域 | 否 |
| **允許路邊**</br>`Extension Attribute: curbside_enabled` | 兩個取車選項之一。 路邊遞送可讓客戶將其車輛停留在商戶商店地點的指定地點。 在此案例中，訂單是由商店關聯商交付給客戶。 </br></br>啟用後，可在結帳時向客戶顯示此選項。 此外，客戶在辦理登記入住手續時，可能會被要求描述其車輛和停車地點。 </br></br>此選項也會將全域設定覆寫為 **啟用路邊取車** 已在 **傳遞方法** 的 **店內取貨** | 全域 | 否 |
| **[!UICONTROL Curbside Instructions]**</br>`Extension Attribute: curbside_instructions` | 傳送給客戶的可自訂訊息，位於 [!UICONTROL Order Ready For Pickup in Store] 電子郵件通知。 | 全域 | 否 |
| **[!UICONTROL Estimated Pickup Lead Time]**</br>`Extension Attribute: pickup_lead_time` | 接收、撿料及準備撿料訂單之前所需的分鐘數。 </br></br>此資訊用於在網站上向客戶顯示訂單收取的估計時間。</br></br> 設定此選項會覆寫下列專案的全域設定： **預估取貨前置時間** 已為 **傳遞方法** 在 **店內取貨** 設定。 | 全域 | 否 |
| **[!UICONTROL Estimated Pickup Time Label]**</br>`Extension Attribute: pickup_time_label` | 顯示訂單準備好接受前所經過分鐘數的標籤。</br></br> 自訂此標籤時，您可以使用代碼%1插入 **預估取貨前置時間**.</br></br> 設定此選項會覆寫下列專案的全域設定： [!UICONTROL Estimated Pickup Time Label] 已為 [!UICONTROL Delivery Method] 在 [!UICONTROL In-store Pickup]. | 全域 | 否 |

### **營業時間**

| **欄位** | **說明** | **範圍** | **必填** |
|------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Location Timezone]**</br>`Extension Attribute: timezone` | 商家商店位置的時區。 對於每一天，設定開始和結束時間。</br></br>這些設定用於最佳化預估接車時間，以及履行服務報告。 | 全域 | 是 |
| **[!UICONTROL Opening Hours]**</br>`Internal Attribute: inventory_source_opening_hours_dynamic_rows` | 商家商店地點的營業時間。 </br></br>此資訊可用於最佳化預估取貨時間，以及履行服務報告。 | 全域 | 是 |

### 設定簽入Experience介面選項



| **欄位** | **說明** | **範圍** | **必填** |
|---------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Use Parking Spots]**</br>`Extension Attribute: parking_spots_enabled` | 指定商戶商店位置是否有指定停車地點供路邊取車。 </br></br>啟用後，您可以設定可用的停車位。 | 全域 | 否 |
| **[!UICONTROL Is Parking Spot a Mandatory Field?]**</br>`Extension Attribute: parking_spot_mandatory` | 指定客戶在購物體驗期間是否需要泊車地點識別。</br></br>如果啟用，系統會提示客戶在抵達時指定其停車地點。 如果停用，客戶可以略過此輸入。 | 全域 | 否 |
| **[!UICONTROL Parking Spots List]**</br> `Internal Attribute: inventory_source_parking_spot_dynamic_rows` | 此商場位置提供路邊取車的停車位。 使用提供的介面為每個點命名。</br></br> 您不需要為每一個停車點命名，只需要為路邊指定的停車點命名。 例如，您可能有可供停車的A-G列，但只有列A的前8個地點指定用於路邊取車。 在此案例中，您可能會定義8個位置；例如：A1、A2、A3等。 | 全域 | 否 |
| **[!UICONTROL Allow "Other" Parking Spot Field]**</br>`Extension Attribute: custom_parking_spot_enabled` | 啟用時，此設定可讓客戶在簽到期間描述其停車點。 | 全域 | 否 |
| **[!UICONTROL Use Car Color]**</br>`Extension Attribute: use_car_color` | 指定是否支援在簽到期間從客戶收集車輛顏色。 </br></br> 可用的選取專案 [!UICONTROL Car Color] 已在Admin中設定 [簽入體驗的系統設定](check-in-experience-setup.md). | 全域 | 否 |
| **[!UICONTROL Is Car Color a Mandatory Field?]**</br>`Extension Attribute: car_color_mandatory` | 指定客戶在簽到期間是否需要車輛顏色識別。</br></br>如果啟用，系統會提示客戶在抵達時指定其車輛的顏色。 如果停用，客戶可以略過此輸入。 | 全域 | 否 |
| **[!UICONTROL Use Car Make]** </br>`Extension Attribute: use_car_make` | 指定是否支援在簽到期間從客戶收集車輛製造。</br></br> 可用的選取專案 [!UICONTROL Car Make] 已在Admin中設定 [簽入體驗的系統設定](check-in-experience-setup.md). | 全域 | 否 |
| **[!UICONTROL Is Car Make a Mandatory Field?]**</br>`Extension Attribute: car_make_mandatory` | 指定客戶在簽到期間是否需要車輛製造識別。</br></br>如果啟用，系統會提示客戶在抵達時指定其車輛的廠牌。 如果停用，客戶可以略過此輸入。 | 全域 | 否 |
| **[!UICONTROL Use Additional Information]**</br> `Extension Attribute: use_additional_information` | 指定是否支援在簽入期間從客戶收集其他資訊。 | 全域 | 否 |
| **[!UICONTROL Is Additional Information a Mandatory Field?]**</br>`Extension Attribute: additional_information_mandatory` | 指定客戶在簽入期間是否需要其他資訊。 </br></br>如果啟用，則系統會提示客戶在抵達時輸入其他資訊。 如果停用，客戶可以略過此輸入。 | 全域 | 否 |
