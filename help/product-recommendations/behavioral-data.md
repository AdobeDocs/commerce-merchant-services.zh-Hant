---
title: 行為資料
description: 了解行為資料，以及何時可以開始使用。
exl-id: d68a97b9-1497-4603-a72c-4aaaf6e048cb
source-git-commit: 840b091638aedd3f6ac097a010d035eff997ffe2
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 0%

---

# 行為資料

某些建議類型會使用購物者的行為資料來訓練機器學習模型以建立個人化建議。 其他建議類型僅使用目錄資料，不使用任何行為資料。 如果您想要快速開始，可以使用下列僅目錄的建議類型：

- `More like this`
- `Visual similarity`

那麼，何時可以開始使用使用行為資料的建議類型？ 視情況而定。 這稱為 _冷啟動_ 問題。

此 _冷啟動_ 問題是模型需要多長時間才能被視為高質量。 在產品建議中，這會轉譯為等待Adobe Sensei先訓練其機器學習模型，再在您的網站上部署建議單元。 這些模型擁有的資料越多，建議就越準確和實用。 收集此資料需要時間，而且會依流量而有所不同。 因為這些資料只能在生產網站上收集，因此盡早將資料收集部署在生產網站是符合您最佳利益的做法。 您可以透過 [安裝和配置](install-configure.md) the `magento/production-recommendations` 模組。

下表提供一些一般指引，說明收集每個建議類型的足夠資料所花的時間：

| 建議類型 | 培訓時間 | 附註 |
|---|---|---|
| 人氣(`Most viewed`, `Most purchased`, `Most added to cart`) | 視 | 視事件數量而定 — 檢視最常見，因此學習速度更快；然後新增至購物車，然後購買 |
| `Viewed this, viewed that` | 需要更多培訓 | 產品檢視的數量非常高 |
| `Viewed this, bought that`, `Bought this, bought that` | 需要最多的培訓 | 購買事件是商務網站上最罕見的事件，尤其是與產品檢視相比 |
| `Trending` | 需要三天的資料才能建立人氣基準 | 趨勢分析是衡量產品最近受歡迎程度與自身受歡迎程度基準的指標。 產品的趨勢分數是使用前景集（24小時內最近的人氣）和背景集（72小時內的人氣基線）來計算。 如果項目在過去24小時內比其基準人氣更受歡迎，則會獲得高趨勢分數。 每個產品都有此分數，而任何時候最高的產品都包含一組最熱門的趨勢產品。 |

可影響訓練所需時間的其他變數：

- 流量增加有助於加快學習速度
- 某些建議類型的訓練速度比其他類型快
- Adobe Commerce每四小時重新計算一次行為資料。 Recommendations越準確，網站上就會使用越久。

若要協助您視覺化每種建議類型的訓練進度， [建立建議](create.md) 頁面顯示就緒指標。

在生產環境中收集資料，並訓練機器學習模型時，您可以實作 [剩餘任務](implementation-workflow.md) 將建議部署至店面的必要條件。 當您完成測試和設定建議時，機器學習模型已收集並計算足夠的資料以建立相關建議，讓您將建議部署至店面。

如果大部分SKU的流量（檢視、購買的產品、趨勢）不足，則可能沒有足夠的資料來完成學習程式。 這可能會導致管理員中的準備狀態指標看起來好像卡住了。
準備狀態指標的用途是為商戶提供其他資料點，以選擇最適合其商店的建議類型。 這些數字是指南，可能永遠達不到100%。

## 備份建議 {#backuprecs}

如果沒有足夠的輸入資料來提供單位中所有請求的建議項目，Adobe Commerce會提供備用建議來填入建議單位。 例如，如果您部署 `Recommended for you` 建議類型至您的首頁時，您網站上的首次購物者未產生足夠的行為資料，以便準確建議個人化產品。 在此案例中，Adobe Commerce會根據 `Most viewed` 建議類型給此購物者。

下列建議類型後援至 `Most viewed` 如果收集的輸入資料不足，則建議類型：

- `Recommended for you`
- `Viewed this, viewed that`
- `Viewed this, bought that`
- `Bought this, bought that`
- `Trending`
- `Conversion (view to purchase)`
- `Conversion (view to cart)`
