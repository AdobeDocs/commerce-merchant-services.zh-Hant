---
title: '"[!DNL Live Search] 設定」'
description: 「設定 [!DNL Live Search] 服務。」
exl-id: a0b63116-4b8f-490c-a54e-e21f1b02b634
source-git-commit: eefae3c849545062012cea1a7092c27f7df56b58
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# 設定

使用 *設定* 索引標籤，以設定價格Facet範圍和間隔，以及索引的預設語言。

價格多面向會指定價格範圍群組的數目，以及價格值在群組之間的分配方式。

語言設定告知 [!DNL Live Search] 寫入索引時預期的語言服務。

![設定](assets/settings.png)

## 價格多面向

您可以指定價格範圍群組的數量，以及價格值在群組之間的分配方式。 每個價格範圍會依序與上一個群組重疊。 例如，間隔為20的五個群組會建立下列價格範圍：0-20、20-40、40-60、60-80和>80。 如果目錄中沒有足夠產品可填滿所有已定義的範圍，則會相應地調整可用群組的顯示。 例如：0-20、60-80、>80。

1. 在Admin中，前往 **行銷** > *SEO與搜尋* > **[!DNL Live Search]**.
1. 在 **設定** 標籤下的 *價格多面向*，請執行下列動作：
   * 輸入 **選擇數量**&#x200B;或價格分組以供使用。 最多可定義50個價格群組。
   * 輸入 **間隔值**，或每個群組的價格範圍。 最大值為10,000。
1. 按一下 **儲存**.

   更新後的設定約需15分鐘才能在店面提供。

### 欄位說明

| 欄位 | 說明 |
|--- |--- |
| 選擇數量 | 指定可在店面中作為搜尋篩選器使用的價格範圍群組數目。 預設值：8，最大值：50 |
| 間隔值 | 指定每個群組的價格範圍間隔。 例如，間隔值為20的五個選取專案會建立0-20、20-40、40-60、60-80和>80的五個群組。 預設值：5，最大值：10,000 |

<!-- ## Language

The Language setting tells [!DNL Live Search] which language to expect when reading the catalog and writing the index. 

Languages have different sets of rules for grammar: how words are separated, verb tenses and synonyms, for example.
The Language setting ensures that the correct set of rules are applied to the indexing mechanism.

The Language settings should be set to the primary language of the catalog. -->
