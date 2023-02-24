---
title: 商家商店配置
description: 設定會增強Inventory management來源作為商家商店。
role: User, Admin
level: Intermediate
exl-id: 7c3444d0-5ecb-4ac1-aa81-e48eea290f5d
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '1209'
ht-degree: 0%

---

# 商家商店（源）配置

此解決方案通過擴展庫存來源，為商戶提供面向操作的功能，增強了本地的Inventory management功能。

- 為商店位置新增地理座標
- 將源指定為 [!DNL Store Pickup Location] 並指定可用的發運能力（收貨方商店、發貨方商店）
- 指定可用的提貨選項（店內或店內）、自定義提貨指令和其他資訊，以便向客戶傳達提貨詳細資訊和指示

詞語 _來源_ 和 _商店位置_ 可互換使用。 所有記錄都是庫存來源，但來源也可以是商家存放區位置，具體取決於組態設定。

從管理員管理商家商店配置： **[!UICONTROL Stores > Inventory > Sources >  Edit Source]**.

>[!NOTE]
>
>在設定過程中，可能需要在建立源或更新現有源後刷新快取。

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
<td>商家商店位置的緯度坐標。 此必要資訊會用於店面體驗的位置搜尋和地圖放置。 值必須與存放區的確切位址相符，才能通過驗證。</td>
<td>全球</td>
<td>是</td>
</tr>
<tr>
<td><strong>[!UICONTROL Longitude]</strong></br><code>Base Attribute: Longitude</code></td>
<td>商家商店位置的縱向坐標。 此必要資訊會用於店面體驗的位置搜尋和地圖放置。 值必須與存放區的確切位址相符，才能通過驗證。</td>
<td>全球</td>
<td>是</td>
</tr>
<tr>
<td><strong>[!UICONTROL Use as Pickup Location]</br></strong><code>Base Attribute: is_pickup_location_active</code></td>
<td>將源指定為可用的儲存拾取位置。 此設定會判斷來源是否已同步並顯示給訪客。</td>
<td>全球</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship to Store]</strong><br><code>Extension Attribute: allow_ship_to_store</code></td>
<td>在源層配置收貨儲存功能。 如需詳細資訊，請參閱[一般設定](enable-general.md)選項， <strong>[!UICONTROL Enable Ship To Store]
</tr>
<tr>
<td><strong>[!UICONTROL Latitude]</strong></br><code>Base Attribute: latitude</code></td>
<td>商家商店位置的緯度坐標。 此必要資訊會用於店面體驗的位置搜尋和地圖放置。 值必須與存放區的確切位址相符，才能通過驗證。</td>
<td>全球</td>
<td>是</td>
</tr>
<tr>
<td><strong>[!UICONTROL Longitude]</strong></br><code>Base Attribute: Longitude</code></td>
<td>商家商店位置的縱向坐標。 此必要資訊會用於店面體驗的位置搜尋和地圖放置。 值必須與存放區的確切位址相符，才能通過驗證。</td>
<td>全球</td>
<td>是</td>
</tr>
<tr>
<td><strong>[!UICONTROL Use as Pickup Location]</br></strong><code>Base Attribute: is_pickup_location_active</code></td>
<td>將源指定為可用的儲存拾取位置。 此設定會判斷來源是否已同步並顯示給訪客。</td>
<td>全球</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship to Store]</strong></br> <code>Extension Attribute: [!DNL allow_ship_to_store]</code></td>
<td>在源層配置收貨儲存功能。 如需詳細資訊，請參閱[一般設定](enable-general.md)選項， <strong>[!UICONTROL Enable Ship To Store]</strong>.</td>
<td>全球</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong></br><code>Extension Attribute: [!DNL use_as_shipping_source]</code></td>
 <td>在源層配置從商店發貨功能。 如需詳細資訊，請參閱[一般設定](enable-general.md)選項， [!UICONTROL Enable Ship From Store].</td>
<td>全球</td>
<td>否</td>
</tr>
<tr>
<td>全球</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong><code>Extension Attribute: [!DNL use_as_shipping_source]</code></td><td></td><td></td><td></td></tr></tbody></table>



| **欄位** | **說明** | **範圍** | **必填** |
|--------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Latitude]**</br>`Base Attribute: latitude` | 商家商店位置的緯度坐標。 此必要資訊會用於店面體驗的位置搜尋和地圖放置。 值必須與存放區的確切位址相符，才能通過驗證。 | 全球 | 是 |
| **[!UICONTROL Longitude]**</br>`Base Attribute: Longitude` | 商家商店位置的縱向坐標。 此必要資訊會用於店面體驗的位置搜尋和地圖放置。 值必須與存放區的確切位址相符，才能通過驗證。 | 全球 | 是 |
| **[!UICONTROL Use as Pickup Location]**</br>`Base Attribute:[!DNL is_pickup_location_active]` | 將源指定為可用的儲存拾取位置。 此設定會判斷來源是否已同步並顯示給訪客。 | 全球 | 否 |
| **[!UICONTROL Enable Ship to Store]**</br>`Extension Attribute: [!DNL allow_ship_to_store]` | 在源層配置收貨儲存功能。 如需詳細資訊，請參閱 [一般配置](enable-general.md) 選項， **[!UICONTROL Enable Ship To Store]**. | 全球 | 否 |
| **[!UICONTROL Enable Ship From Store]**</br>`Extension Attribute: [!DNL use_as_shipping_source]` | 在源層配置從商店發貨功能。 如需詳細資訊，請參閱 [一般配置](enable-general.md) 選項， [!UICONTROL Enable Ship From Store] | 全球 | 否 |

{style=&quot;table-layout:auto&quot;}

## 拾取位置配置

| **欄位** | **說明** | **範圍** | **必填** |
|-----------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Allow In-Store Pickup]**</br>`Extension Attribute: [!DNL store_pickup_enabled]` | 兩個取貨選項之一。 [!DNL In-Store Pickup] 是指允許客戶進入商家商店位置以檢索其訂單的能力。 </br></br>啟用後，結帳期間可能會向客戶顯示此選項。 </br></br>此選項也會將全域設定覆寫為 [!UICONTROL Enable In-store Pickup] 在 [!UICONTROL Delivery Method] for [!UICONTROL In-store Pickup] | 全球 | 否 |
| **店內取貨指示**</br>`Extension Attribute: store_pickup_instructions` | 在 **已準備好在商店取貨** 電子郵件通知。 | 全球 | 否 |
| **允許彎曲**</br>`Extension Attribute: curbside_enabled` | 兩個取貨選項之一。 貨運允許客戶將車輛停放在商家商店位置的指定地點。 在此案例中，訂單是由商店關聯人員傳送給客戶。 </br></br>啟用後，結帳期間可向客戶顯示此選項。 此外，在簽入過程中，可能會要求客戶描述其車輛和停車位。 </br></br>此選項也會將全域設定覆寫為 **啟用組織裝貨** 在 **傳送方法** for **店內取貨** | 全球 | 否 |
| **[!UICONTROL Curbside Instructions]**</br>`Extension Attribute: curbside_instructions` | 在 [!UICONTROL Order Ready For Pickup in Store] 電子郵件通知。 | 全球 | 否 |
| **[!UICONTROL Estimated Pickup Lead Time]**</br>`Extension Attribute: pickup_lead_time` | 接收、挑選和準備挑選訂單之前所需的分鐘數。 </br></br>此資訊用於顯示網站上向客戶提貨的估計時間。</br></br> 設定此選項會覆寫 **預計提貨提前期** 為 **傳送方法** 在 **店內取貨** 設定。 | 全球 | 否 |
| **[!UICONTROL Estimated Pickup Time Label]**</br>`Extension Attribute: pickup_time_label` | 在訂單準備就緒前顯示分鐘數的標籤。</br></br> 自定義此標籤時，可以使用代碼%1插入 **預計提貨提前期**.</br></br> 設定此選項會覆寫 [!UICONTROL Estimated Pickup Time Label] 為 [!UICONTROL Delivery Method] 在 [!UICONTROL In-store Pickup]. | 全球 | 否 |

### **營業時間**

| **欄位** | **說明** | **範圍** | **必填** |
|------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Location Timezone]**</br>`Extension Attribute: timezone` | 商家商店位置的時區。 每天設定開始和結束時間。</br></br>這些設定用於優化估計的提貨時間以及完成服務報告。 | 全球 | 是 |
| **[!UICONTROL Opening Hours]**</br>`Internal Attribute: inventory_source_opening_hours_dynamic_rows` | 商家商店位置的營業時間。 </br></br>此資訊可用於優化估計的提貨時間，並用於履行服務報告。 | 全球 | 是 |

### 設定簽入體驗介面選項



| **欄位** | **說明** | **範圍** | **必填** |
|---------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Use Parking Spots]**</br>`Extension Attribute: parking_spots_enabled` | 指定商家商店位置是否具有用於貨物運送的指定停車位。 </br></br>啟用後，您可以配置可用的停車位。 | 全球 | 否 |
| **[!UICONTROL Is Parking Spot a Mandatory Field?]**</br>`Extension Attribute: parking_spot_mandatory` | 指定在購物體驗期間是否需要客戶的停車位識別。</br></br>如果已啟用，系統會提示客戶在到達時指定其停車地點。 如果已停用，客戶可略過此輸入。 | 全球 | 否 |
| **[!UICONTROL Parking Spots List]**</br> `Internal Attribute: inventory_source_parking_spot_dynamic_rows` | 這家商家商店提供的停車位，供客人提貨。 使用提供的介面為每個地點命名。</br></br> 您不需要為每個停車點命名，只需為庫邊指定的點。 例如，您可能有A-G行停車，但只有前8個行A點被指定用於輪邊裝貨。 在此案例中，您可以定義8個位置；例如：A1、A2、A3等。 | 全球 | 否 |
| **[!UICONTROL Allow "Other" Parking Spot Field]**</br>`Extension Attribute: custom_parking_spot_enabled` | 啟用後，此設定允許客戶在簽入期間描述其停車地點。 | 全球 | 否 |
| **[!UICONTROL Use Car Color]**</br>`Extension Attribute: use_car_color` | 指定是否支援在簽入期間從客戶收集車輛顏色。 </br></br> 可用的選項 [!UICONTROL Car Color] 在管理員中設定 [簽入體驗的系統設定](check-in-experience-setup.md). | 全球 | 否 |
| **[!UICONTROL Is Car Color a Mandatory Field?]**</br>`Extension Attribute: car_color_mandatory` | 指定客戶在簽入期間是否需要車輛顏色標識。</br></br>如果已啟用，系統會提示客戶在到達時指定其車輛的顏色。 如果已停用，客戶可略過此輸入。 | 全球 | 否 |
| **[!UICONTROL Use Car Make]** </br>`Extension Attribute: use_car_make` | 指定是否支援在簽入期間從客戶收集車輛製造。</br></br> 可用的選項 [!UICONTROL Car Make] 在管理員中設定 [簽入體驗的系統設定](check-in-experience-setup.md). | 全球 | 否 |
| **[!UICONTROL Is Car Make a Mandatory Field?]**</br>`Extension Attribute: car_make_mandatory` | 指定在簽入期間是否需要客戶進行車輛識別。</br></br>如果已啟用，系統會提示客戶在到達時指定其車輛的型號。 如果已停用，客戶可略過此輸入。 | 全球 | 否 |
| **[!UICONTROL Use Additional Information]**</br> `Extension Attribute: use_additional_information` | 指定是否支援在簽入期間從客戶收集其他資訊。 | 全球 | 否 |
| **[!UICONTROL Is Additional Information a Mandatory Field?]**</br>`Extension Attribute: additional_information_mandatory` | 指定客戶在簽入期間是否需要其他資訊。 </br></br>如果已啟用，系統會提示客戶在到達時輸入其他資訊。 如果已停用，客戶可略過此輸入。 | 全球 | 否 |
