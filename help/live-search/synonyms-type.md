---
title: 「同義字型別」
description: 「單向與雙向 [!DNL Live Search] 同義字會擴展關鍵字的定義。」
exl-id: 708d7b0d-7361-44f4-ae9e-b92f574ac975
source-git-commit: 9bacdb5fd232a3603bcb7abe2e93da9ead794d38
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 0%

---

# 同義字的型別

單向和雙向同義字會擴展關鍵字的定義。 有些可與關鍵字互換，有些則代表關鍵字的子集。

## 雙向

雙向同義字具有相同的意義，並傳回相同的搜尋結果。 在下列範例中，以粗體顯示的第一個字詞是目錄中所使用的關鍵字，後面跟有與原始關鍵字相同含義的字詞。 您可以為同一個關鍵字建立一對簡單的雙向同義字，或是多個雙向同義字的鏈結。

**夾克** ![雙向選擇器](assets/btn-two-way.png) 外套
**褲子** ![雙向選擇器](assets/btn-two-way.png) 鬆弛 ![雙向選擇器](assets/btn-two-way.png) 褲子

## 單向

單向同義字是關鍵字的子集，但具有更具體的含義。 例如，卡普里和短褲是短褲，但並非所有短褲都是卡普里或短褲。 搜尋褲子包括卡布瑞和短褲。 不過，搜尋短褲不會傳回Capris。

**運動衫** ![單向選擇器](assets/btn-one-way.png) 連帽衫
**褲子** ![單向選擇器](assets/btn-one-way.png) 卡普里斯 ![多個單向選擇器](assets/btn-multiple-one-way.png) 小腿長褲 ![多個單向選擇器](assets/btn-multiple-one-way.png) 兜售推銷

## 最佳實務

請牢記以下最佳實務，以充分發揮 [!DNL Live Search] 同義字。

### 避免「停用詞」

[!DNL Live Search] 從同義字中篩選出常見英文「停用詞」，例如：

a、an、and、are、as、at、be、but、by、for、if、in、into、is、it、no、not、of、on、or、such、that、the、their、then、there、these、they、this、to、was、will、with

停用字詞不會使同義字更有意義，但會增加必須處理的資料量。

### 使用單字

如果同義字詞包含多個字詞，則字詞之間的空白字元會將它們視為個別的同義字。 例如，如果您將「time piece」定義為「watch」的同義字，則「time」和「piece」會被視為個別的同義字。

### 使用單數與複數

不需要將單字的單數與複數形式都定義為同義字。 如果您的目錄中混合了單數與複數詞語，則搜尋會尋找正確的產品集。 例如，如果您在產品名稱中使用「pant」一詞，而購物者搜尋「pants」，則會傳回正確的產品集，而提供單字「pant」作為建議。 「褲子」這個單數詞匯通常用於時尚業，有時也用於零售業，儘管複數形式的「褲子」更常用於某些領域。 （技術上來說，「褲子」一詞是指服裝中遮蓋一條腿的部分，因此您需要一雙「褲子」來遮蓋兩條腿。）

### 一致性

與目錄中術語的使用方式一致。 請記住，使用方式上可能存在地區差異，有時候，產業內部也可能存在差異。

### 關鍵字對應

此技巧使用可搜尋的產品屬性（而非同義字）來建立產品之間的關鍵字型關聯。 因此，對應的產品可能會出現在其他產品的搜尋結果中。 若要深入瞭解，請參閱 [搜尋結果](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-results.html).
