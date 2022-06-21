---
title: 行為資料
description: 瞭解行為資料以及何時開始使用它。
exl-id: d68a97b9-1497-4603-a72c-4aaaf6e048cb
source-git-commit: 371ae21c97021912279381b5e32f953fe3b4f0dd
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 0%

---

# 行為資料

某些推薦類型使用購物者的行為資料來訓練機器學習模型以構建個性化推薦。 其他建議類型僅使用目錄資料，不使用任何行為資料。 如果要快速啟動，可以使用以下僅目錄的建議類型：

- `More like this`
- `Visual similarity`

那麼，你什麼時候才能開始使用使用行為資料的推薦類型呢？ 看情況。 這稱為 _冷啟動_ 問題。

的 _冷啟動_ 問題是模型需要訓練多長時間才能被視為高質量。 在產品建議中，它轉換為等待Adobe Sensei在您的站點上部署建議單元之前培訓其機器學習模型。 這些模型擁有的資料越多，建議就越準確和有用。 收集此資料需要時間，並且會因通信量而異。 由於此資料只能在生產站點上收集，因此盡早在生產站點部署資料收集符合您的最大利益。 您可以通過 [安裝和配置](install-configure.md) 這樣 `magento/production-recommendations` 中。

下表提供了一些一般指導，說明為每種建議類型收集足夠資料所花的時間：

| 建議類型 | 培訓時間 | 注釋 |
|---|---|---|
| 基於受歡迎度(`Most viewed`。 `Most purchased`。 `Most added to cart`) | 變化 | 取決於事件數量 — 視圖最常見，因此學習速度更快；然後添加購物車，然後購買 |
| `Viewed this, viewed that` | 需要更多培訓 | 產品視圖的數量非常高 |
| `Viewed this, bought that`。 `Bought this, bought that` | 需要最多的培訓 | 購買事件是商務站點上最少見的事件，特別是與產品視圖相比 |
| `Trending` | 需要三天的資料來確定受歡迎程度基準 | Trending是衡量產品最近受歡迎程度的指標，與其流行程度基線相比。 產品的趨勢分數是使用前景集（最近24小時的流行度）和背景集（72小時的流行度基線）計算的。 如果某個項目在過去24小時內比其基準受歡迎程度高得多，則它會獲得高趨勢分數。 每個產品都有這一分，而任何時候最高的分數都構成了一組熱門趨勢產品。 |

其他可影響訓練所需時間的變數：

- 更高的流量有助於加快學習
- 某些建議類型的訓練速度比其他類型快
- Adobe Commerce每四小時重新計算行為資料。 雖然您當時在技術上可以部署建議單元，但要知道建議在您的站點上使用的時間越長，建議就越準確。

要幫助您直觀地查看每種建議類型的培訓進度， [建立建議](create.md) 頁顯示就緒指示器。

在收集生產資料並訓練機器學習模型時，您可以實施 [剩餘任務](implementation-workflow.md) 將建議部署到店面。 在您完成測試和配置建議之後，機器學習模型已收集和計算了足夠的資料來構建相關建議，從而允許您將建議部署到您的店面。

## 備份建議 {#backuprecs}

如果沒有足夠的輸入資料來提供一個單位內所有請求的建議項目，Adobe Commerce將提供備份建議來填充建議單位。 例如，如果部署 `Recommended for you` 首次在您的網站上購物的推薦類型沒有生成足夠的行為資料，無法準確推薦個性化產品。 在本例中，Adobe Commerce基於 `Most viewed` 推薦類型。

以下建議類型回退到 `Most viewed` 如果收集的輸入資料不足，則建議類型：

- `Recommended for you`
- `Viewed this, viewed that`
- `Viewed this, bought that`
- `Bought this, bought that`
- `Trending`
- `Conversion (view to purchase)`
- `Conversion (view to cart)`
