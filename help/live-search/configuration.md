---
title: 「Commerce組態設定和 [!DNL Live Search] 『
description: 說明Adobe Commerce組態設定， [!DNL Live Search] 可以閱讀。
exl-id: a4e9e2dd-e912-4ced-a44a-091ac5334e50
features: Services, Search, Configuration
source-git-commit: 888b81683a4e139a35b771d9c573f1f5f0c3b902
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# [!DNL Live Search] 和Adobe Commerce組態設定

有一些Commerce組態設定 [!DNL Live Search] 支援。 本主題列出這些組態值。

## 支援的設定值

| Commerce組態設定 | 由Popover支援 | 由介面卡支援 |
|---|---|---|
| 商店>設定>目錄>目錄>目錄搜尋>允許每個頁面的所有產品長度 | 是。 最多500種產品 | 是。 最多500種產品 |
| 儲存>設定>目錄>目錄>目錄搜尋>最小查詢長度 | 是 | 是 |
| 儲存>設定>目錄>目錄>目錄搜尋>每頁產品網格允許值 | 是 | 是 |
| 商店>設定>目錄>目錄>目錄搜尋>產品每頁格點預設值 | 是。 最多500種產品 | 是。 最多500種產品 |
| 儲存>設定>目錄>庫存>顯示無庫存產品 | 是，含v2.0.4+ | 是，含v2.0.4+ |
| 儲存>組態>幣別>預設顯示幣別 | 是，含3.1.0+ | 是，含3.1.0+ |
| 儲存>組態>一般>貨幣設定>貨幣選項>基本貨幣 | 是 | 是 |

「Widget產品清單」頁面與「彈出視窗」中的價格現在會使用設定的匯率轉換為預設顯示貨幣。

## 搜尋詞

[!DNL Live Search] 支援 [搜尋字詞重新導向](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html) 在Adobe Commerce處理路由的實施中：Luma和其他基於php的主題。

## 不支援的設定值

[!DNL Live Search] 無法讀取所有設定值。 此表格列出了開發人員可能更感興趣的值。

| Commerce組態設定 | 附註 |
|---|---|
| 商店>設定>目錄>店面>清單模式 | 正確轉譯，但部分頁面互動不會傳送事件 |
| 儲存>組態>目錄>目錄>目錄搜尋>查詢長度上限 | 未實作；搜尋服務接受最多255個字元 |
| 組態>銷售>稅捐>價格顯示設定>在目錄中顯示產品價格 |  |
