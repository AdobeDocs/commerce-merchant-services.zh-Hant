---
title: 指南概述
description: Adobe Experience Platform連接器連接Adobe Commerce [!DNL Commerce] 例如其他Adobe Experience Cloud產品。
source-git-commit: 9b5f2da08167e22bbba504009bccc87d0ab02c48
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# Experience Platform連接器概述

Experience Platform連接器擴展使Adobe Commerce商家能夠將資料發送到Adobe Experience Platform邊緣，以便Adobe Analytics和Adobe Target等其他Adobe Experience Cloud產品可以使用 [!DNL Commerce] 資料。 通過連接 [!DNL Commerce] 資料到Adobe Experience Cloud的其他產品，您可以執行任務，如分析站點上的用戶行為、執行AB測試和建立個性化市場活動。

店面事件捕獲購物者交互，如 `View Page`。 `View Product`。 `Add to Cart`等等。 捕獲的資料不包括個人身份資訊(PII)。 所有用戶標識符，如cookie ID和IP地址，都是嚴格匿名的。 [瞭解更多資訊](https://www.adobe.com/privacy/experience-cloud.html)。 請參閱此頁末尾的店面事件完整清單。

## 使用Experience Platform連接器的先決條件 {#prereqs}

要使用Experience Platform連接器，必須首先：

- 填寫以下內容 [表格](https://forms.office.com/pages/responsepage.aspx?id=Wht7-jR7h0OUrtLBeN7O4VH_dtG9hJVAk_TqGkZC2DxUM1FSWkdJOE41UVpUWUw0M1JWV0RKS1VXQi4u) 而Adobe將為您提供對資料流和Adobe Experience Platform（如果需要）的訪問權限。

授予訪問權限時：

1. [登錄](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) 你的Adobe。
1. 看你 [組織](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=en#concept_EA8AEE5B02CF46ACBDAD6A8508646255)。 組織ID是與您預配的Experience Cloud公司關聯的ID。 此ID是24個字元的字母數字字串，後跟（必須包括）@AdobeOrg。
1. 訪問資料流工作區和 [建立資料流](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en)。

將Adobe Commerce實例連接到Adobe Experience Platform時，將使用組織ID和資料流。

## 後續步驟

- 安裝 [Experience Platform連接器延伸部](install.md)。

   Experience Platform連接器擴展從伺服器的命令行安裝，並作為 [服務](../landing/saas.md)。 完成該過程後，Experience Platform連接器出現在 **系統** 菜單 **服務** 的 [!DNL Commerce] _管理_。

## 觀眾

本指南針對必須將其Adobe Commerce店面資料連接到其他AdobeDX產品的Adobe Commerce商家而設計。

## 已知問題

當前，Experience Platform連接器存在以下已知問題：

- 安裝了B2B模組的Adobe Commerce企業版不支援搜索事件。
- Storefront資料連接到Adobe Experience Platform邊緣後，需要幾個小時才能從Commerce到達各個目的地。

## 支援

如果您需要資訊或有本指南未包括的問題，請發佈到以下Slack渠道：

- `#beacon-ama`
