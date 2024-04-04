---
title: 『[!DNL Page Builder] 整合
description: 瞭解如何使用 [!DNL Product Recommendations] 頁面產生器中的單位。
exl-id: dd972642-1fb4-426a-ac68-f56bb5fa2ecf
feature: Services, Recommendations, Page Builder
source-git-commit: 6bc8eb5ffbefc46c8666ead8c8ec8b274a0040e7
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---

# [!DNL Page Builder] 整合

產品Recommendations可以整合在您網站上部署的任何頁面產生器內容中。

>[!NOTE]
>
> 原生頁面產生器頁面最多可有25個建議單位。 非原生頁面產生器頁面最多可包含5個建議單位。 另請參閱 [建立新建議](create.md) 以取得詳細資訊。

## 搭配使用產品Recommendations與頁面產生器內容

1. 在網站的預設商店檢視中建立建議單位。 即使您打算在不同的存放區檢視中使用它們，也必須在預設存放區檢視中建立它們。

   >[!NOTE]
   >
   >Page Builder建議單位的量度只會出現在預設的存放區檢視中 [!DNL Product Recommendations] 工作區。 即使您將頁面產生器建議單位放在非預設商店檢視的商店檢視上，與這些頁面產生器建議單位相關的量度仍只顯示在預設商店檢視上 [!DNL Product Recommendations] 工作區。 若要在非預設商店中檢視頁面產生器量度 [!DNL Product Recommendations] 工作區，開啟和 [編輯](edit.md) 非預設存放區中的頁面產生器建議單位，然後按一下 [!UICONTROL **儲存**]. 頁面產生器量度現在會出現在 [!DNL Product Recommendations] 工作區位於非預設的storeview下。

1. 在頁面產生器中，選取Recommendations產品內容Widget並放置於您的網站上。

![插入建議單位](assets/pb-insert.png)

1. 按一下 **編輯產品推薦**
1. 按一下 **選取**
1. 選取您先前建立的建議單位，然後按一下 **新增選取專案**

![插入建議單位](assets/pb-select.png)

1. 對頁面產生器內容進行任何其他編輯並儲存您的變更。

在轉譯時，Recommendation單位會考量頁面產生器內容的內容和範圍。
