---
title: 建立新建議
description: 瞭解如何建立產品推薦單位。
exl-id: d393ab78-0523-463f-9b03-ad3f523dce0f
source-git-commit: 51ff52eba117fe438d592ca886dbca25304a0d15
workflow-type: tm+mt
source-wordcount: '1022'
ht-degree: 0%

---

# 建立新建議

當您建立建議時，您會建立包含建議產品&#x200B;_專案_&#x200B;的&#x200B;_建議單位_。

![建議單位](assets/unit.png)
_建議單位_

當您啟用建議單位時，Adobe Commerce會開始[收集資料](workspace.md)以測量曝光數、檢視數、點按數等。 [!DNL Product Recommendations]表格會顯示每個建議單位的量度，以協助您做出明智的業務決策。

1. 在&#x200B;_管理員_&#x200B;側邊欄上，前往&#x200B;**行銷** > _促銷活動_ > **產品Recommendations**&#x200B;以顯示&#x200B;_產品Recommendations_&#x200B;工作區。

1. 指定要顯示建議的[存放區檢視](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings)。

   >[!NOTE]
   >
   > 頁面產生器建議單位必須在預設商店檢視中建立，然後才可以在任何地方使用。 若要進一步瞭解如何使用Page Builder建立產品建議，請參閱[新增內容 — 產品Recommendations](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html)。

1. 按一下&#x200B;**建立建議**。

1. 在&#x200B;_為您的建議命名_&#x200B;區段中，輸入描述性名稱以供內部參考，例如`Home page most popular`。

1. 在&#x200B;_選取頁面型別_&#x200B;區段中，從下列選項中選取您要顯示建議的頁面：

   >[!NOTE]
   >
   > 當您的商店設定為將產品加入購物車後立即[顯示購物車頁面時，「購物車」頁面上不支援產品Recommendations](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/cart/cart-configuration.html#redirect-to-cart)。

   * 首頁
   * 類別
   * 產品詳細資料
   * 購物車
   * 確認
   * [頁面產生器](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html)

   您最多可以為每種頁面型別建立5個使用中的建議單位，並為頁面產生器建立25個使用中的建議單位。 當達到限制時，頁面型別會變灰。

   ![建議名稱和頁面](assets/create-recommendation.png)
   _建議名稱和頁面位置_

1. 在&#x200B;_選取建議型別_&#x200B;區段中，指定您要顯示在所選頁面上的[建議型別](type.md)。 對於某些頁面，建議的[位置](placement.md)僅限於某些型別。

1. 在&#x200B;_店面顯示標籤_&#x200B;區段中，輸入購物者可見的[標籤](placement.md#recommendation-labels)，例如「最暢銷商品」。

1. 在&#x200B;_選擇產品數目_&#x200B;區段中，使用滑桿來指定您要顯示在建議單位中的產品數目。

   預設值為`5`，最大值為`20`。

1. 在&#x200B;_選取位置_&#x200B;區段中，指定建議單位在頁面上出現的位置。

   * 在主要內容底部
   * 在主要內容的頂端

1. （選擇性）若要變更建議的順序，請選取並移動&#x200B;_選擇位置_&#x200B;表格中的列。

   _選擇位置_&#x200B;區段會顯示針對您選取的頁面型別建立的所有建議（如果有的話）。

   ![建議順序](assets/create-recommendation-select-placement.png)
   _頁面_&#x200B;上的建議順序

1. （選擇性）在&#x200B;_篩選器_&#x200B;區段中，[套用篩選器](filters.md)以控制哪些產品出現在建議單位中。

   ![建議篩選器](assets/create-recommendation-filter-products.png)
   _推薦產品篩選器_

1. 完成後，按一下下列其中一項：

   * **儲存為草稿**&#x200B;以便稍後編輯建議單位。 您無法修改處於草稿狀態的建議單位的頁面型別或建議型別。

   * **啟動**&#x200B;以啟用店面上的推薦單位。

## 整備程度指標

有些建議型別會使用購物者的行為資料來[訓練機器學習模型](behavioral-data.md)，以建置個人化建議。

只需要目錄資料。 這些不需要行為資料：

* _最喜歡這個_
* _最近檢視的專案_
* _視覺相似度_

根據過去六個月店面行為資料：

* _已檢視此專案，已檢視該專案_
* _已檢視此專案，已購買該專案_
* _已購買此專案，已購買該專案_
* _為您推薦_

基於人氣的建議型別使用最近七天的店面行為資料：

* 檢視次數最多
* 購買最多
* 已新增至購物車
* 趨勢

整備指標值可能會因為某些因素而波動，例如目錄的整體大小、產品互動事件的數量（檢視、加入購物車、購買），以及在特定時間範圍內註冊這些事件的SKU百分比（如上所列）。 例如，在假期旺季的流量中，整備程度指標顯示的值可能會高於正常流量時的值。

為了協助您視覺化每個建議型別的訓練進度，_選取建議型別_&#x200B;區段會顯示每個型別的整備程度。 這些整備程度指標是根據兩個因素計算：

* 足夠的結果集大小：大多數案例中傳回的結果是否足夠避免使用[備份建議](behavioral-data.md#backuprecs)？

* 足夠的結果集變化：傳回的產品是否代表目錄中的各種產品？ 此因素的目標是避免少數產品成為整個網站唯一建議的專案。

系統會根據上述因素計算並顯示整備程度值。 當建議型別的整備程度值為75%或以上時，即視為已準備好部署。 當建議型別的整備程度至少為50%時，即視為部分整備。 當建議型別的整備值小於50%時，即視為未準備好部署。 這些是一般准則，但每個個別案例可能會因上述收集資料的性質而有所不同。

![建議型別](assets/create-recommendation-select-type.png)
_建議型別_

>[!NOTE]
>
>指標可能永遠不會達到100%。

## 預覽Recommendations {#preview}

_建議產品預覽_&#x200B;面板總是隨建議單位部署至店面時可能顯示的產品範例選項一起提供。

若要在非生產環境中工作時測試建議，您可以從[不同的來源](settings.md)擷取建議資料。 這可讓商家在部署至生產環境之前，先體驗規則並預覽建議。

| 欄位 | 說明 |
|---|---|
| 名稱 | 產品的名稱。 |
| SKU | 指派給產品的庫存單位 |
| 價格 | 產品的價格。 |
| 結果型別 | 主要 — 表示收集到的訓練資料足夠顯示建議。<br />備份 — 表示未收集足夠的訓練資料，所以使用備份建議來填滿位置。 移至[行為資料](behavioral-data.md)以進一步瞭解機器學習模型和備份建議。 |

當您建立建議單位時，請嘗試使用頁面型別、建議型別和篩選器，以取得即將包含之產品的即時即時回饋。 當您開始瞭解顯示的產品時，可以設定建議單位以符合您的業務需求。

Adobe Commerce [篩選器](filters.md)建議，以避免在單一頁面上部署多個建議單位時顯示重複的產品。 因此，預覽面板中顯示的產品可能與店面中顯示的產品不同。

>[!NOTE]
>
> 您無法預覽`Recently viewed`建議型別，因為管理中無法取得資料。
