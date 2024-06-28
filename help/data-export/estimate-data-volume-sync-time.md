---
title: 預估資料量和傳輸時間
description: 「瞭解如何估計所需的資料量和傳輸時間， [!DNL data export] 工具，可在Adobe Commerce和連線的服務之間同步摘要資料。」
role: Admin, Developer
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 0%

---

# 預估資料同步處理的資料量和傳輸時間

Adobe建議您在開始任何資料摘要同步處理前，先預估資料量和同步處理時間，以確保順暢的排程並避免網站作業中斷。 在計畫初始同步或大規模目錄更新（例如大量價格變更）時，此預估很重要。

依預設，資料匯出工具會以單一執行緒模式，以預設批次大小處理資料。 使用預設設定時，摘要提交程式不會平行化。 此外，預設的節流原則可讓Adobe Commerce接受每秒兩個要求(RPS)，其轉譯如下：

- 每分鐘最多10,000個產品，其中產品是具有特定店面屬性的SKU
- 最高每分鐘50,000個價格

根據預設設定，下列因素會影響同步期間的資料傳輸時間。

- 執行緒計數設定為1 （預設）
- 批次大小已設定為 _100_ 適用於所有摘要，但 `prices` 摘要，其設定為 _500_.
- 摘要接受率為2個要求/秒。
- 所有產品都會指派至所有現有網站
- 對於價格計算案例，所有產品都會指定特殊與群組價格

>[!NOTE]
>
>如有需要，可根據效能影響分析增加節流原則限制。 如需協助，請聯絡您的技術客戶經理(TAM)或提交支援票證。

## 計算每個摘要的資料傳輸

使用下表中的值和公式來計算每個資料摘要的資料量和同步處理時間。

>[!NOTE]
>
>這些計算是以每秒2個要求的傳輸速率為基礎。 速度取決於資料收集和資料提交所需的時間。 實際傳輸速度視要求裝載大小和Commerce應用程式伺服器上的目前負載而定。

| 摘要 | 資料範例 | 計算記錄的公式 | 預測的要求計數 | 預測的重新同步時間 |
| --- | --- | --- | --- | --- |
| 產品 | 產品(P)：10000，商店檢視(SV)：4 | P * SV = 40000 | 40000/批次大小(100) = 400個請求 | （400個請求*每個請求0.5秒） / 60 = 3.3分鐘 |
| 類別 | 類別(C)：500，商店檢視(SV)：4 | C * SV = 2000 | 2000 /批次大小(100) = 20個請求 | （20個請求*每個請求0.5秒） / 60 = 0.1分鐘（4秒） |
| 價格 | 產品(P)：10000，客戶群組(CG)：6 （例如共用目錄中的不重複價格），網站(WS)：2 | P \* WS * CG = 120000 | 120000/批次大小(500) = 240個請求 | （240個請求*每個請求0.5秒） / 60 = 2分鐘 |
| 產品覆寫 | 具有許可權或在共用目錄(P)中的產品：10000、受影響的客戶群組(CG)：5、指派的網站WS：2 | P \* WS * CG = 100000 | 100000/批次大小(100) = 1000個請求 | （1000個請求*每個請求0.5秒） / 60 = 8.3分鐘 |
| 產品系列品種 | 指派給可設定產品(PV)的變體（子產品）： 100000 | PV = 100000 | 100000/批次大小(100) = 1000個請求 | （1000個請求*每個請求0.5秒） / 60 = 8.3分鐘 |
| 類別許可權 | 所有類別許可權計數+ 4個遞補記錄(CP)： 10000 | CP = 10000 | 10000/批次大小(100) = 100個請求 | （100個請求*每個請求0.5秒） / 60 = 0.8分鐘（50秒） |
| 存貨存量狀態 | 產品(P)：10000，庫存指派給(S)的產品：5 （假設每個產品都指派給每個庫存） | P * S = 50000 | 50000/批次大小(100) = 500個請求 | （500個請求*每個請求0.5秒） / 60 = 4.2分鐘 |
| 銷售訂單 | 所有訂單記錄（包括商業發票、出貨等） (SO)：10000 | SO = 10000 | 10000/批次大小(100) = 100個請求 | （100個請求*每個請求0.5秒） / 60 = 0.8分鐘（50秒） |
