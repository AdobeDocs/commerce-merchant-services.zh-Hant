---
title: 銷售電子郵件模板
description: 配置事務性電子郵件模板，以便在完成儲存代收訂單的過程中與客戶和儲存管理員通信。
role: User, Admin
level: Intermediate
exl-id: 688732e3-06f0-4613-a589-2d465597eb28
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '1202'
ht-degree: 0%

---


# 銷售電子郵件模板

Store Fulfillment提供一組擴展的事務性電子郵件模板，以支援訂單和履行工作流。 它們提供跨渠道的一致、自動通信和消息傳遞 — 通知客戶和儲存管理員有關訂單狀態更改、店內提貨單的說明等。

儲存完成電子郵件模板配置了預設消息和設定。 Adobe Commerce的商戶管理員可以管理和修改配置，並選擇電子郵件模板以在不同情況下與客戶進行通信。 管理員也可以配置和自定義模板。

從管理員配置銷售電子郵件模板： **[!UICONTROL Stores > Configuration > Sales > Sales Emails]**。

## 電子郵件 — 常規設定

<table>
<thead>
<tr>
<th><strong>欄位</strong></th>
<th><strong>說明</strong></th>
<th><strong>範圍</strong></th>
<th><strong>必需</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>非同步發送</strong></td>
<td>禁用此功能。 不支援非同步電子郵件發送。 要獲得儲存拾取的最快通信和響應時間，請立即發送電子郵件，而不是批處理電子郵件。 </td>
<td>儲存視圖</td>
<td>否</td>
</tr>
</tbody></table>

## 已準備好在商店中裝貨

<table>
<thead>
<tr>
<th><strong>欄位</strong></th>
<th><strong>說明</strong></th>
<th><strong>範圍</strong></th>
<th><strong>必需</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>已啟用</strong></td>
<td>此電子郵件在商店關聯完成領料訂單後發送給客戶。 設定為「否」以禁用電子郵件通知。 如果禁用了電子郵件模板，則不會阻止儲存關聯挑選訂單。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<tr>
<td><strong>訂單已準備好接收電子郵件發件人</strong></td>
<td>發送電子郵件通知時使用的發件人標識。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<tr>
<td><strong>訂單準備接收電子郵件模板</strong></td>
<td>用於通知註冊客戶的電子郵件模板。 整合中提供了預設模板。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<td><strong>訂單準備接收來賓的電子郵件模板</strong></td>
<td>用於通知來賓客戶的電子郵件模板。 整合中提供了預設模板。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<tr>
<td><strong>備用代理聯繫人的代理電子郵件模板訂單準備</strong></td>
<td>用於通知按順序命名的其他聯繫人的電子郵件模板。 整合中提供了預設模板。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<tr>
<td><strong>將訂單發送到，以便接收電子郵件副本</strong></td>
<td>用逗號分隔的電子郵件地址清單，用於發送每個通知的副本。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<tr>
<td><strong>發送訂單以便接收電子郵件複製方法</strong></td>
<td>要使用的電子郵件複製方法 — 碳複製。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
</tbody></table>


## 已在商店中提取訂單

<table>
<thead>
<tr>
<th><strong>欄位</strong></th>
<th><strong>說明</strong></th>
<th><strong>範圍</strong></th>
<th><strong>必需</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>已啟用</strong></td>
<td>此電子郵件在確認客戶已從商店領取訂單時發送給客戶。 設定為「否」以禁用電子郵件通知。 如果禁用了電子郵件模板，則不會阻止客戶提取訂單。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<tr>
<td><strong>訂單已接收電子郵件發件人</strong></td>
<td>發送電子郵件通知時使用的發件人標識。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<tr>
<td><strong>訂單已提取電子郵件模板</strong></td>
<td>用於通知註冊客戶的電子郵件模板。 整合提供了預設模板</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<td><strong>已為來賓選擇訂單電子郵件模板</strong></td>
<td>用於通知來賓客戶的電子郵件模板。 整合中提供了預設模板。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<tr>
<td><strong>已將電子郵件副本發送到</strong></td>
<td>用逗號分隔的電子郵件地址清單，用於發送每個通知的副本。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<tr>
<td><strong>已採用發送電子郵件複製方法</strong></td>
<td>要使用的電子郵件複製方法 — 碳複製。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
</tbody></table>

## 訂單延遲

<table>
<thead>
<tr>
<th><strong>欄位</strong></th>
<th><strong>說明</strong></th>
<th><strong>範圍</strong></th>
<th><strong>必需</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>已啟用</strong></td>
<td>此電子郵件將發送給客戶，以通知他們在商家商店處理或領取訂單的延遲。 設定為「否」以禁用電子郵件通知。 如果禁用了電子郵件模板，則功能不會阻止訂單延遲。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<tr>
<td><strong>訂單延遲電子郵件發件人
</strong></td>
<td>發送電子郵件通知時使用的發件人標識。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<tr>
<td><strong>訂單延遲電子郵件模板</strong></td>
<td>用於通知註冊客戶的電子郵件模板。 整合中提供了預設模板。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<td><strong>訂購來賓的延遲電子郵件模板</strong></td>
<td>用於通知來賓客戶的電子郵件模板。 整合中提供了預設模板。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<tr>
<td><strong>將訂單延遲的電子郵件副本發送到</strong></td>
<td>用逗號分隔的電子郵件地址清單，用於發送每個通知的副本。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<tr>
<td><strong>發送訂單延遲複製方法</strong></td>
<td>要使用的電子郵件複製方法 — 碳複製。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
</tbody></table>



## 已取消訂單

<table>
<thead>
<tr>
<th><strong>欄位</strong></th>
<th><strong>說明</strong></th>
<th><strong>範圍</strong></th>
<th><strong>必需</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>已啟用</strong></td>
<td>此電子郵件將發送給客戶，以通知客戶其訂單已在商家商店取消。 設定為 <code>No</code> 來修改標籤元素的屬性。 如果禁用了電子郵件模板，則此功能不會阻止取消訂單。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<tr>
<td><strong>訂單已取消電子郵件發件人
</strong></td>
<td>發送電子郵件通知時使用的發件人標識。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<tr>
<td><strong>已取消訂單的電子郵件模板</strong></td>
<td>用於通知註冊客戶的電子郵件模板。 整合中提供了預設模板。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<td><strong>已取消來賓訂單</strong></td>
<td>用於通知來賓客戶的電子郵件模板。 整合中提供了預設模板。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<tr>
<td><strong>將已取消訂單的電子郵件副本發送到</strong></td>
<td>用逗號分隔的電子郵件地址清單，用於發送每個通知的副本。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<tr>
<td><strong>發送訂單已取消的複製方法</strong></td>
<td>要使用的電子郵件複製方法 — 碳複製。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
</tbody></table>


## 部分取消訂單

<table>
<thead>
<tr>
<th><strong>欄位</strong></th>
<th><strong>說明</strong></th>
<th><strong>範圍</strong></th>
<th><strong>必需</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>已啟用</strong></td>
<td>此電子郵件將發送給客戶，以通知客戶其訂單的一部分已在商店取消。 設定為 <code>No</code> 來修改標籤元素的屬性。 如果禁用了電子郵件模板，則不會阻止訂單部分取消。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<tr>
<td><strong>訂單部分取消電子郵件發件人
</strong></td>
<td>發送電子郵件通知時使用的發件人標識。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<tr>
<td><strong>部分取消的訂單電子郵件模板</strong></td>
<td>用於通知註冊客戶的電子郵件模板。 整合中提供了預設模板。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<td><strong>替代提貨聯繫人的訂單部分取消的電子郵件模板</strong></td>
<td>用於通知按順序命名的其他聯繫人的電子郵件模板。 整合中提供了預設模板。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<tr>
<td><strong>已部分取消來賓訂單</strong></td>
<td>用於通知來賓客戶的電子郵件模板。 整合中提供了預設模板。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<tr>
<td><strong>將訂單部分取消的電子郵件副本發送到</strong></td>
<td>用逗號分隔的電子郵件地址清單，用於發送每個通知的副本。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<tr>
<td><strong>發送訂單部分取消的複製方法</strong></td>
<td>要使用的電子郵件複製方法 — 碳複製。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
</tbody></table>

## 收貨地點

<table>
<thead>
<tr>
<th><strong>欄位</strong></th>
<th><strong>說明</strong></th>
<th><strong>範圍</strong></th>
<th><strong>必需</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>訂單具有收貨地點產品電子郵件發件人</strong></td>
<td>將電子郵件發送給指定的商家人員，作為所有未結訂單的匯總報告，在商家商店的庫存可用之前，這些未結訂單無法在其中領取。 </br></br> 商家可以使用此報表來啟動和管理從商店到商店的庫存轉移或補充。 </br></br>此通知僅在 [!DNL Ship-to-Store] 功能已啟用。
</br></br>此標籤不會影響所選裝運承運人或其可用的裝運方法標籤。</br></br></td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<tr>
<td><strong>收貨方儲存電子郵件收件人</strong></td>
<td>用逗號分隔的電子郵件地址清單，用於發送每個通知的副本。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
<tr>
<td><strong>電子郵件模板</strong></td>
<td>用於通知收件人的電子郵件模板。 整合中提供了預設模板。</td>
<td>儲存視圖</td>
<td>否</td>
</tr>
</tbody></table>

>[!NOTE]
>
>如果允許延交訂單，則必須提供管理員電子郵件地址以接收有關這些訂單的通知。 將地址添加到以下配置設定： **[!UICONTROL Send Order Delayed Email Copy To]** 的 [訂單延遲](#order-delayed) 模板和 [!UICONTROL Ship To Store Email Recipients] 的 [收貨地點](#ship-to-store) 的下界。



