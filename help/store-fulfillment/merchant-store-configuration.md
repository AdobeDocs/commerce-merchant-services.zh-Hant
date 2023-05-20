---
title: 商家商店配置
description: 設定增強的Inventory management來源作為商店。
role: User, Admin
level: Intermediate
exl-id: 7c3444d0-5ecb-4ac1-aa81-e48eea290f5d
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '1206'
ht-degree: 0%

---

# 商家商店（來源）配置

此解決方案通過擴展面向業務的股票來源為商戶提供功能，增強了Inventory management的本地能力。

- 添加商店位置的地理坐標
- 將源指定為 [!DNL Store Pickup Location] 並指定可用的發運功能（收貨地點、發貨地點）
- 指定可用的拾取選項（店內或庫邊）、自定義的拾取說明和其他資訊，以便向客戶傳達拾取詳細資訊和說明

術語 _源_ 和 _商店位置_ 可互換使用。 所有記錄都是庫存來源，但來源也可以是商家商店位置，具體取決於配置設定。

從管理員管理商家商店配置： **[!UICONTROL Stores > Inventory > Sources >  Edit Source]**。

>[!NOTE]
>
>在設定過程中，可能需要在建立源或更新現有源後刷新快取。

## **常規**

<table>
<tbody>
<tr>
<th>欄位</th>
<th>說明</th>
<th>範圍</th>
<th>必需</th>
</tr>
<tr>
<td><strong>[!UICONTROL Latitude]</strong></br><code>Base Attribute: latitude</code></td>
<td>商家商店位置的緯度坐標。 在店面體驗的位置搜索和地圖放置中使用此所需資訊。 該值必須與儲存的準確地址匹配才能通過驗證。</td>
<td>全球</td>
<td>是</td>
</tr>
<tr>
<td><strong>[!UICONTROL Longitude]</strong></br><code>Base Attribute: Longitude</code></td>
<td>商家商店位置的縱向坐標。 在店面體驗的位置搜索和地圖放置中使用此所需資訊。 該值必須與儲存的準確地址匹配才能通過驗證。</td>
<td>全球</td>
<td>是</td>
</tr>
<tr>
<td><strong>[!UICONTROL Use as Pickup Location]</br></strong><code>Base Attribute: is_pickup_location_active</code></td>
<td>將源指定為可用的「儲存裝貨」位置。 此設定確定源是否已同步並顯示給訪問者。</td>
<td>全球</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship to Store]</strong><br><code>Extension Attribute: allow_ship_to_store</code></td>
<td>在源級別配置送貨到儲存功能。 有關詳細資訊，請參閱[常規配置](enable-general.md)選項， <strong>[!UICONTROL Enable Ship To Store]
</tr>
<tr>
<td><strong>[!UICONTROL Latitude]</strong></br><code>Base Attribute: latitude</code></td>
<td>商家商店位置的緯度坐標。 在店面體驗的位置搜索和地圖放置中使用此所需資訊。 該值必須與儲存的準確地址匹配才能通過驗證。</td>
<td>全球</td>
<td>是</td>
</tr>
<tr>
<td><strong>[!UICONTROL Longitude]</strong></br><code>Base Attribute: Longitude</code></td>
<td>商家商店位置的縱向坐標。 在店面體驗的位置搜索和地圖放置中使用此所需資訊。 該值必須與儲存的準確地址匹配才能通過驗證。</td>
<td>全球</td>
<td>是</td>
</tr>
<tr>
<td><strong>[!UICONTROL Use as Pickup Location]</br></strong><code>Base Attribute: is_pickup_location_active</code></td>
<td>將源指定為可用的「儲存裝貨」位置。 此設定確定源是否已同步並顯示給訪問者。</td>
<td>全球</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship to Store]</strong></br> <code>Extension Attribute: [!DNL allow_ship_to_store]</code></td>
<td>在源級別配置送貨到儲存功能。 有關詳細資訊，請參閱[常規配置](enable-general.md)選項， <strong>[!UICONTROL Enable Ship To Store]</strong>。</td>
<td>全球</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong></br><code>Extension Attribute: [!DNL use_as_shipping_source]</code></td>
 <td>在源級別配置從儲存區發貨功能。 有關詳細資訊，請參閱[常規配置](enable-general.md)選項， [!UICONTROL Enable Ship From Store]。</td>
<td>全球</td>
<td>否</td>
</tr>
<tr>
<td>全球</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong><code>Extension Attribute: [!DNL use_as_shipping_source]</code></td><td></td><td></td><td></td></tr></tbody></table>



| **欄位** | **說明** | **範圍** | **必需** |
|--------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Latitude]**</br>`Base Attribute: latitude` | 商家商店位置的緯度坐標。 在店面體驗的位置搜索和地圖放置中使用此所需資訊。 該值必須與儲存的準確地址匹配才能通過驗證。 | 全球 | 是 |
| **[!UICONTROL Longitude]**</br>`Base Attribute: Longitude` | 商家商店位置的縱向坐標。 在店面體驗的位置搜索和地圖放置中使用此所需資訊。 該值必須與儲存的準確地址匹配才能通過驗證。 | 全球 | 是 |
| **[!UICONTROL Use as Pickup Location]**</br>`Base Attribute:[!DNL is_pickup_location_active]` | 將源指定為可用的「儲存裝貨」位置。 此設定確定源是否已同步並顯示給訪問者。 | 全球 | 否 |
| **[!UICONTROL Enable Ship to Store]**</br>`Extension Attribute: [!DNL allow_ship_to_store]` | 在源級別配置送貨到儲存功能。 有關詳細資訊，請參見 [常規配置](enable-general.md) 選項， **[!UICONTROL Enable Ship To Store]**。 | 全球 | 否 |
| **[!UICONTROL Enable Ship From Store]**</br>`Extension Attribute: [!DNL use_as_shipping_source]` | 在源級別配置從儲存區發貨功能。 有關詳細資訊，請參見 [常規配置](enable-general.md) 選項， [!UICONTROL Enable Ship From Store] | 全球 | 否 |

{style="table-layout:auto"}

## 拾取位置配置

| **欄位** | **說明** | **範圍** | **必需** |
|-----------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Allow In-Store Pickup]**</br>`Extension Attribute: [!DNL store_pickup_enabled]` | 兩個取貨選項之一。 [!DNL In-Store Pickup] 指允許客戶輸入商店位置以檢索其訂單的能力。 </br></br>啟用後，在結帳期間可能會向客戶顯示此選項。 </br></br>此選項還將全局配置覆蓋到 [!UICONTROL Enable In-store Pickup] 在 [!UICONTROL Delivery Method] 為 [!UICONTROL In-store Pickup] | 全球 | 否 |
| **儲存中拾取說明**</br>`Extension Attribute: store_pickup_instructions` | 可自定義的郵件已在 **已準備好在商店中裝貨** 電子郵件通知。 | 全球 | 否 |
| **允許Curbside**</br>`Extension Attribute: curbside_enabled` | 兩個取貨選項之一。 Curbside交付允許客戶將車輛停放在商店位置的指定地點。 在此情況下，訂單由商店關聯方交付給客戶。 </br></br>啟用後，在結帳期間，此選項可以呈現給客戶。 此外，在簽入過程中，可能會要求客戶描述其車輛和停車位。 </br></br>此選項還將全局配置覆蓋到 **啟用曲邊拾取** 在 **交貨方法** 為 **店內裝貨** | 全球 | 否 |
| **[!UICONTROL Curbside Instructions]**</br>`Extension Attribute: curbside_instructions` | 可自定義的郵件已在 [!UICONTROL Order Ready For Pickup in Store] 電子郵件通知。 | 全球 | 否 |
| **[!UICONTROL Estimated Pickup Lead Time]**</br>`Extension Attribute: pickup_lead_time` | 接收、領料和準備領料訂單前所需的分鐘數。 </br></br>此資訊用於顯示網站上客戶的訂單提貨估計時間。</br></br> 設定此選項將覆蓋全局配置 **估計提貨提前期** 為 **交貨方法** 的 **店內裝貨** 配置。 | 全球 | 否 |
| **[!UICONTROL Estimated Pickup Time Label]**</br>`Extension Attribute: pickup_time_label` | 標籤，顯示在訂單準備就緒之前的分鐘數。</br></br> 自定義此標籤時，您可以使用代碼%1插入 **估計提貨提前期**。</br></br> 設定此選項將覆蓋全局配置 [!UICONTROL Estimated Pickup Time Label] 為 [!UICONTROL Delivery Method] 的 [!UICONTROL In-store Pickup]。 | 全球 | 否 |

### **開始時間**

| **欄位** | **說明** | **範圍** | **必需** |
|------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Location Timezone]**</br>`Extension Attribute: timezone` | 商家商店位置的時區。 為每天設定開始和結束時間。</br></br>這些設定用於優化估計的拾取時間，並用於完成服務報告。 | 全球 | 是 |
| **[!UICONTROL Opening Hours]**</br>`Internal Attribute: inventory_source_opening_hours_dynamic_rows` | 商家商店位置的工作時數。 </br></br>此資訊可用於優化估計的拾取時間，以及用於完成服務報告。 | 全球 | 是 |

### 配置簽入體驗介面選項



| **欄位** | **說明** | **範圍** | **必需** |
|---------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Use Parking Spots]**</br>`Extension Attribute: parking_spots_enabled` | 指定商家商店位置是否具有用於路邊提貨的指定停車位。 </br></br>啟用後，您可以配置可用的停車位。 | 全球 | 否 |
| **[!UICONTROL Is Parking Spot a Mandatory Field?]**</br>`Extension Attribute: parking_spot_mandatory` | 指定在購物體驗期間是否需要為客戶提供停車位標識。</br></br>如果啟用，系統會提示客戶在到達時指定其停車地點。 如果禁用，客戶可以跳過此輸入。 | 全球 | 否 |
| **[!UICONTROL Parking Spots List]**</br> `Internal Attribute: inventory_source_parking_spot_dynamic_rows` | 這家商店的停車位提供，方便客人提貨。 使用提供的介面為每個點命名。</br></br> 你不需要給每個停車點都打上名字，只要指定給路邊的停車點。 例如，您可能有可用的停車行A-G，但只有前8個行A點指定用於路邊取貨。 在此情形中，可以定義8個點；例如：A1、A2、A3等。 | 全球 | 否 |
| **[!UICONTROL Allow "Other" Parking Spot Field]**</br>`Extension Attribute: custom_parking_spot_enabled` | 啟用後，此設定允許客戶在簽入期間描述其停車地點。 | 全球 | 否 |
| **[!UICONTROL Use Car Color]**</br>`Extension Attribute: use_car_color` | 指定是否支援在簽入期間從客戶收集車輛顏色。 </br></br> 可用的選擇 [!UICONTROL Car Color] 在Admin中配置 [簽入體驗的系統設定](check-in-experience-setup.md)。 | 全球 | 否 |
| **[!UICONTROL Is Car Color a Mandatory Field?]**</br>`Extension Attribute: car_color_mandatory` | 指定在簽入期間是否需要客戶車輛顏色標識。</br></br>如果啟用，系統將提示客戶在到達時指定車輛的顏色。 如果禁用，客戶可以跳過此輸入。 | 全球 | 否 |
| **[!UICONTROL Use Car Make]** </br>`Extension Attribute: use_car_make` | 指定是否支援在簽入期間從客戶收集車輛製造。</br></br> 可用的選擇 [!UICONTROL Car Make] 在Admin中配置 [簽入體驗的系統設定](check-in-experience-setup.md)。 | 全球 | 否 |
| **[!UICONTROL Is Car Make a Mandatory Field?]**</br>`Extension Attribute: car_make_mandatory` | 指定在簽入期間是否需要客戶使用車輛進行標識。</br></br>如果啟用，系統將提示客戶指定到達時的車輛的製造。 如果禁用，客戶可以跳過此輸入。 | 全球 | 否 |
| **[!UICONTROL Use Additional Information]**</br> `Extension Attribute: use_additional_information` | 指定是否支援在簽入期間從客戶收集附加資訊。 | 全球 | 否 |
| **[!UICONTROL Is Additional Information a Mandatory Field?]**</br>`Extension Attribute: additional_information_mandatory` | 指定在簽入期間是否需要客戶的附加資訊。 </br></br>如果啟用，系統會提示客戶在到達時輸入附加資訊。 如果禁用，客戶可以跳過此輸入。 | 全球 | 否 |
