---
title: '"規則技術說明"'
description: 「有關使用的技術說明 [!DNL Live Search] 規則。」
exl-id: 24ff6a19-f7cd-42f7-b466-fc18f9091504
source-git-commit: bffbede99865e9085f60392e474065a454446370
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 規則技術說明

[!DNL Live Search] 規則根據各種查詢條件觸發操作，使商家能夠針對各種情況來塑造搜索體驗。

當前版本 [!DNL Live Search] 規則基於購物者輸入的查詢字串，而不是返回的結果集。 查詢字串可以包含字母數字字元，並忽略大寫。 與小平面和同義詞一樣，規則儲存在 `protobuf dynamo`。 在查詢時，搜索服務檢索規則 `grpc` 呼叫 `search-admin-service`。
