---
title: 行為資料
description: 瞭解行為資料，以及何時可以開始使用它。
exl-id: d68a97b9-1497-4603-a72c-4aaaf6e048cb
source-git-commit: 840b091638aedd3f6ac097a010d035eff997ffe2
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 0%

---

# 行為資料

有些建議型別會使用購物者的行為資料來訓練機器學習模型，以建立個人化建議。 其他建議型別僅使用目錄資料，不使用任何行為資料。 如果您想要快速開始，可以使用以下僅限目錄的建議型別：

- `More like this`
- `Visual similarity`

那麼，何時可以開始使用使用行為資料的建議型別？ 視情況而定。 這稱為 _冷啟動_ 問題。

此 _冷啟動_ 問題是指模型需要訓練多久才能被視為高品質的測量。 在產品建議中，這表示等候Adobe Sensei訓練其機器學習模型，然後再將建議單位部署在您的網站上。 這些模型擁有的資料越多，建議就越準確和有用。 收集此資料需要時間，而且會因流量而異。 由於此資料只能在生產網站上收集，因此請儘早在那裡部署資料收集符合您的最大利益。 您可以透過以下方式執行此操作 [安裝和設定](install-configure.md) 此 `magento/production-recommendations` 模組。

下表提供收集每種建議型別的足夠資料所需時間的一般指引：

| 建議型別 | 訓練時間 | 附註 |
|---|---|---|
| 人氣型(`Most viewed`， `Most purchased`， `Most added to cart`) | 視情況而定 | 視事件數量而定 — 檢視是最常見的，因此學習速度更快；然後新增購物車，然後購買 |
| `Viewed this, viewed that` | 需要更多訓練 | 產品檢視量相當大 |
| `Viewed this, bought that`, `Bought this, bought that` | 需要最多訓練 | 購買事件是商業網站上最罕見的事件，尤其是與產品檢視次數相比 |
| `Trending` | 需要三天的資料來建立人氣基線 | 趨勢是衡量產品受歡迎程度與其本身受歡迎程度基線相比的最新動向。 產品的趨勢分數是使用前景集（最近24小時內的熱門程度）和背景集（72小時內的熱門程度基線）計算。 如果某個專案在過去24小時內比其基準熱門度受歡迎許多，則會獲得高趨勢分數。 每個產品都有這個分數，而最高的分數則包含所有熱門產品。 |

其他可能影響訓練所需時間的變數：

- 更高的流量有助於更快的學習
- 有些建議型別的訓練速度比其他建議型別快
- Adobe Commerce每四小時重新計算一次行為資料。 在您的網站上使用期限越久，Recommendations就越準確。

為了協助您以視覺效果呈現每個建議型別的培訓進度， [建立建議](create.md) 頁面會顯示整備程度指標。

在生產環境中收集資料並訓練機器學習模型時，您可以實作 [剩餘任務](implementation-workflow.md) 將建議部署至您的店面所需。 當您完成測試和設定建議時，機器學習模型已收集並運算足夠的資料來建置相關建議，因此可讓您將建議部署至店面。

如果大部分SKU的流量（瀏覽數、購買的產品、趨勢）不足，可能沒有足夠的資料來完成學習程式。 這可能會造成管理員中的整備程度指標看起來像是卡住了。
整備程度指標旨在為商家提供另一個資料點，以便選擇哪種推薦型別更適合他們的商店。 這些數字可作為指引，可能永遠無法達到100%。

## 備份建議 {#backuprecs}

如果輸入資料不足，無法在一個單位中提供所有要求的建議專案，Adobe Commerce會提供備份建議來填入建議單位。 例如，如果您部署 `Recommended for you` 建議型別到您的首頁，您網站上的首次購物者未產生足夠的行為資料，因此無法準確建議個人化產品。 在此情況下，Adobe Commerce會根據 `Most viewed` 給此購物者的建議型別。

下列建議型別後援至 `Most viewed` 建議型別（如果收集的輸入資料不足）：

- `Recommended for you`
- `Viewed this, viewed that`
- `Viewed this, bought that`
- `Bought this, bought that`
- `Trending`
- `Conversion (view to purchase)`
- `Conversion (view to cart)`
