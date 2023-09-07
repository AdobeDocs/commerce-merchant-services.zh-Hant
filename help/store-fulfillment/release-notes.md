---
title: '[!DNL Store Fulfillment by Walmart Commerce Technologies] 發行說明'
description: 「檢閱發行說明，瞭解所有資訊 [!DNL Store Fulfillment by Walmart Commerce Technologies] 發行版本。」
role: Admin, User, Leader
feature: Shipping/Delivery, Release Notes
exl-id: 04dcec10-fff8-483d-a2c1-4b58e063e0f0
source-git-commit: db1d5523f48f5686c2a28c7dfb7b1175238b37cf
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 1%

---

# 發行說明

以下版本說明說明的初始版本 [!DNL Store Fulfillment Services by Walmart Commerce Technologies] 並包含：

![新增](../assets/new.svg) 新功能
![已修正的問題](../assets/fix.svg) 修正和改良
![已知問題](../assets/bug.svg) 已知問題

另請參閱 [即將發行的版本](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) 以瞭解發行排程和支援。

另請參閱 [產品可用性](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html) 以瞭解哪些Adobe Commerce版本支援此擴充功能。

## v1.5.0

*2023年8月3日*

[!BADGE 支援]{type=Informative tooltip="支援"}[Adobe Commerce 2.4.4至2.4.6](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html)，包括2.4.6-p1、2.4.5-p3和2.4.4-p4安全性修補程式發行版本

此版本包含下列更新：

![新增](../assets/fix.svg) 更新擴充功能以支援 [Adobe Commerce安全性修補程式發行版本](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/security-patches/overview.html) 2.4.6-p1、2.4.5-p3和2.4.4-p4。

![新增](../assets/new.svg)<!-- WMTP-918 --> 新增對 [非同步傳送](sales-emails.md) 銷售電子郵件的設定選項。 升級至1.5.0版的商家可選擇立即傳送電子郵件（預設）或以非同步方式傳送。

![新增](../assets/new.svg)<!-- WMTP-916--> 已更新 [來源組態](merchant-store-configuration.md) 以支援國際電話號碼格式。

![新增](../assets/new.svg) 新增邏輯，以防止退款金額超過剩餘金額或開立商業發票的金額。

![新增](../assets/new.svg)<!-- WMTP-882 --> 已取代 `google.map.LatLng` 物件，具有JSON常值，可支援與舊版的相容性 [!DNL Google Maps].

![已修正的問題](../assets/fix.svg)<!-- WMTP- --> 更新建立 `[!DNL Available for Store Pickup]` 和 `[!DNL Available for Home Delivery]` 產品屬性，以防止屬性類別衝突。

![已修正的問題](../assets/fix.svg)<!-- WMTP-915 --> 修正載入和儲存某些實體時，造成無休止回圈的相容性問題。

![已修正的問題](../assets/fix.svg)<!-- WMTP-921 --> 已修正導致無法 [!DNL Ship to Store] 當從產品詳細資料頁面(PDP)將專案新增到購物車時，觸發的報價驗證。

![已修正的問題](../assets/fix.svg)<!-- WMTP- 932 --> 已修正允許客戶為不符合首頁傳送條件的專案選擇首頁傳送方法的結帳問題。

![已修正的問題](../assets/fix.svg) 安裝更新：

- <!-- WMTP-880--> 修正安裝時傳回錯誤網站程式碼的問題 [!DNL Store Fulfillment] 副檔名。

- <!-- WMTP-878--> 修正SKU整數在安裝期間必須轉型為字串型別的問題。

![已修正的問題](../assets/fix.svg)<!-- WMTP-915--> 修正遺失「簽入」錯誤碼所造成的失敗。

![已修正的問題](../assets/fix.svg)<!-- WMTP-932 --> 修正與分配作業期間部分拒絕相關的錯誤。

![新增](../assets/new.svg)<!-- WMTP-953 --> 更新Cancel API端點，將status引數作為選用物件使用。

![新增](../assets/new.svg)<!-- WMTP-960 --> 改善Dispense API端點的記錄詳細資料。

## v1.4.0

*2023年4月13日*

[!BADGE 支援]{type=Informative tooltip="支援"}

![新增](../assets/fix.svg) [!DNL Store Fulfillment] 為現在 [相容於 [!DNL Adobe Commerce] 2.4.4至2.4.6](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).


## v1.3.0

*2023年2月27日*

[!BADGE 支援]{type=Informative tooltip="支援"}

此版本包含下列更新：

![新增](../assets/fix.svg)<!-- WMTP-795 --> 新增將系統組態設定的預設範圍從網站變更為全域的功能，以停用特定網站的「商店履行」解決方案。

## v1.2.0

*2022年9月27日*

[!BADGE 支援]{type=Informative tooltip="支援"}

此版本包含下列更新：

![新增](../assets/fix.svg) [!DNL Store Fulfillment] 為現在 [相容於 [!DNL Adobe Commerce] 2.4.4至2.4.5](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).


## v1.1.0

*2022年7月15日*

[!BADGE 支援]{type=Informative tooltip="支援"}

穩定性：一般可用性

![新增](../assets/fix.svg)<!-- WMTP-731 --> 簡化 [簽入體驗設定](check-in-experience-setup.md) 針對「商店協助」應用程式，新增預設汽車造型和模型選項。 在舊版中，商家必須手動設定汽車廠牌和模型選項。

## v1.0.0

*2022年3月4日*

[!BADGE 支援]{type=Informative tooltip="支援"}

穩定性：一般可用性

## 商店協助應用程式

如需Store Assist應用程式最新版本的相關資訊，請參閱 [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id1609281539){target="_blank"} or [Google Play store](https://play.google.com/store/apps/details?id=com.walmart.faas.storeassist){target="_blank"}.
