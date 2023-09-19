---
title: 摘要擷取服務
description: 瞭解Adobe Commerce的摘要擷取服務
source-git-commit: b57fc43d23dbbcbcae31743fd0ab9c1b3d1c1084
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---


# 摘要擷取服務

>[!NOTE]
>
>摘要擷取服務目前處於私人測試階段。 尚未開放一般使用。

摘要擷取服務可讓擁有大型和/或複雜目錄的客戶直接將資料傳送至Adobe Commerce服務。

摘要擷取服務會略過Adobe Commerce執行個體，並將目錄資料從協力廠商企業資源規劃(ERP)直接移動至Adobe Commerce服務，減少處理產品變更（價格更新、新增屬性）所需的時間。

此服務適用於在核心Adobe Commerce應用程式外部系統中儲存和管理其產品目錄的客戶。 它作為API提供，因此客戶可以將其整合到其現有系統中，為其部署提供更大的靈活性。

如果客戶有大型複雜目錄，或擁有頻繁更新的目錄，他們可能會擔心新資料在即時商店中顯示所花的時間可能超過預期。 由於目錄服務知道處理這些更新所需的資料，因此不需要透過核心Commerce產品傳送資料，只需轉送至目錄服務。 移除此中間步驟可提升效率。

## 摘要擷取流程

根據Adobe Commerce的設定，資料儲存和資料流程可能會採取不同的路徑。

* 在標準Adobe Commerce執行個體中，產品目錄會儲存在核心資料庫中。
* 使用Adobe Commerce服務時，目錄資料會從核心資料庫複製到服務，並從那裡進行處理和傳送。
* 將目錄資料儲存在協力廠商系統(ERP、MDM、PIM)時，資料會流經核心Commerce應用程式，然後流向Commerce服務。
* 透過摘要擷取服務，產品資料會直接從協力廠商系統傳入Commerce服務基礎架構。

![摘要擷取服務](assets/feed-ingestion.png)

略過核心Commerce應用程式並直接將資料移至Commerce服務，產品更新就會更快反映在商店中。 核心目錄資料（例如SKU）會傳送至核心商務應用程式，以供個別處理。

## 加入Beta

摘要擷取服務是專為下列用途而設計：

* 擁有Headless實作的中型企業客戶
* 擁有大型複雜目錄的客戶
* 客戶未使用Adobe Commerce管理員管理目錄資料，而是使用ERP或協力廠商系統管理目錄資料

如果您有興趣加入Beta版計畫，請透過sagonzal@adobe.com聯絡團隊。
