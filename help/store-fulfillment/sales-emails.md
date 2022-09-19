---
title: 銷售電子郵件
description: 配置交易式電子郵件模板，以便在「儲存裝貨訂單」的完成流程期間與客戶和儲存管理員進行通信。
role: User, Admin
level: Intermediate
exl-id: 688732e3-06f0-4613-a589-2d465597eb28
source-git-commit: 31ad67d3f3d11c68341de0306eea37f231b2d9b9
workflow-type: tm+mt
source-wordcount: '1200'
ht-degree: 0%

---


# 銷售電子郵件

商店履行提供一組擴展的交易式電子郵件模板，以支援訂單和履行工作流。 它們提供跨通道的一致、自動通信和消息傳送 — 通知客戶和儲存管理員訂單狀態更改、店內提貨訂單的說明等。

儲存履行電子郵件模板配置了預設郵件和設定。 Adobe Commerce中的商家管理員可以管理和修改設定，並選取電子郵件範本以在不同情境下與客戶通訊。 管理員也可以設定和自訂範本。

從管理員配置銷售電子郵件模板： **[!UICONTROL Stores > Configuration > Sales > Sales Emails]**.

## 電子郵件 — 一般設定

<table>
<thead>
<tr>
<th><strong>欄位</strong></th>
<th><strong>說明</strong></th>
<th><strong>範圍</strong></th>
<th><strong>必填</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>非同步傳送</strong></td>
<td>停用此功能。 不支援非同步電子郵件傳送。 為達到商店取貨的最快通訊和回應時間，請立即傳送電子郵件，而非批次處理。 </td>
<td>商店檢視</td>
<td>否</td>
</tr>
</tbody></table>

## 已準備好在商店提貨

<table>
<thead>
<tr>
<th><strong>欄位</strong></th>
<th><strong>說明</strong></th>
<th><strong>範圍</strong></th>
<th><strong>必填</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>已啟用</strong></td>
<td>當商店關聯人完成領料時，此電子郵件會傳送給客戶。 設為「否」以停用電子郵件通知。 如果停用電子郵件範本，並不會防止商店關聯人員挑選訂單。</td>
<td>商店檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>訂單已就緒，可接收電子郵件發件人</strong></td>
<td>傳送電子郵件通知時使用的寄件者身分識別。</td>
<td>商店檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>訂單已就緒，可接收電子郵件模板</strong></td>
<td>用於通知註冊客戶的電子郵件消息模板。 整合會提供預設範本。</td>
<td>商店檢視</td>
<td>否</td>
</tr>
<td><strong>訂單已就緒，可接收來賓的電子郵件模板</strong></td>
<td>用於通知來賓客戶的電子郵件消息模板。 整合會提供預設範本。</td>
<td>商店檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>備用代理聯繫人的「訂單就緒」代理電子郵件模板</strong></td>
<td>用於通知訂單中命名的其他聯繫人的電子郵件消息模板。 整合會提供預設範本。</td>
<td>商店檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>將訂單就緒，以便提貨電子郵件副本發送至</strong></td>
<td>以逗號分隔的電子郵件地址清單，用於傳送每個通知的副本。</td>
<td>商店檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>發送訂單以備取貨電子郵件複製方法</strong></td>
<td>要使用的電子郵件複製方法 — 碳複製。</td>
<td>商店檢視</td>
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
<th><strong>必填</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>已啟用</strong></td>
<td>此電子郵件會在確認客戶已從商店取得訂單時傳送給客戶。 設為「否」以停用電子郵件通知。 如果停用電子郵件範本，並不會防止客戶擷取訂單。</td>
<td>商店檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>訂單已獲取電子郵件發件人</strong></td>
<td>傳送電子郵件通知時使用的寄件者身分識別。</td>
<td>商店檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>已拾取訂單電子郵件模板</strong></td>
<td>用於通知註冊客戶的電子郵件消息模板。 整合會提供預設範本</td>
<td>商店檢視</td>
<td>否</td>
</tr>
<td><strong>已為來賓選擇電子郵件模板</strong></td>
<td>用於通知來賓客戶的電子郵件消息模板。 整合會提供預設範本。</td>
<td>商店檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>已將電子郵件副本收到</strong></td>
<td>以逗號分隔的電子郵件地址清單，用於傳送每個通知的副本。</td>
<td>商店檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>已擷取「傳送」電子郵件複製方法</strong></td>
<td>要使用的電子郵件複製方法 — 碳複製。</td>
<td>商店檢視</td>
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
<th><strong>必填</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>已啟用</strong></td>
<td>此電子郵件會傳送給客戶，通知他們處理或在商家商店挑選訂單的延遲。 設為「否」以停用電子郵件通知。 如果停用電子郵件範本，功能不會防止訂單延遲。</td>
<td>商店檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>訂單延遲電子郵件發件人
</strong></td>
<td>傳送電子郵件通知時使用的寄件者身分識別。</td>
<td>商店檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>訂單延遲電子郵件範本</strong></td>
<td>用於通知註冊客戶的電子郵件消息模板。 整合會提供預設範本。</td>
<td>商店檢視</td>
<td>否</td>
</tr>
<td><strong>來賓的訂單延遲電子郵件模板</strong></td>
<td>用於通知來賓客戶的電子郵件消息模板。 整合會提供預設範本。</td>
<td>商店檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>將訂單延遲的電子郵件副本發送到</strong></td>
<td>以逗號分隔的電子郵件地址清單，用於傳送每個通知的副本。</td>
<td>商店檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>發送訂單延遲複製方法</strong></td>
<td>要使用的電子郵件複製方法 — 碳複製。</td>
<td>商店檢視</td>
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
<th><strong>必填</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>已啟用</strong></td>
<td>此電子郵件會傳送給客戶，通知他們其訂單已在商家商店取消。 設為 <code>No</code> 來停用電子郵件通知。 如果停用電子郵件範本，此功能不會阻止訂單取消。</td>
<td>商店檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>訂單已取消電子郵件發件人
</strong></td>
<td>傳送電子郵件通知時使用的寄件者身分識別。</td>
<td>商店檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>已取消訂單的電子郵件模板</strong></td>
<td>用於通知註冊客戶的電子郵件消息模板。 整合會提供預設範本。</td>
<td>商店檢視</td>
<td>否</td>
</tr>
<td><strong>已取消來賓訂單</strong></td>
<td>用於通知來賓客戶的電子郵件消息模板。 整合會提供預設範本。</td>
<td>商店檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>將已取消的訂單電子郵件副本發送到</strong></td>
<td>以逗號分隔的電子郵件地址清單，用於傳送每個通知的副本。</td>
<td>商店檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>發送訂單已取消的複製方法</strong></td>
<td>要使用的電子郵件複製方法 — 碳複製。</td>
<td>商店檢視</td>
<td>否</td>
</tr>
</tbody></table>


## 訂單部分取消

<table>
<thead>
<tr>
<th><strong>欄位</strong></th>
<th><strong>說明</strong></th>
<th><strong>範圍</strong></th>
<th><strong>必填</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>已啟用</strong></td>
<td>此電子郵件會傳送給客戶，通知他們其部分訂單已在商家商店取消。 設為 <code>No</code> 來停用電子郵件通知。 如果停用電子郵件範本，並不會防止訂單被部分取消。</td>
<td>商店檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>訂單部分取消電子郵件發件人
</strong></td>
<td>傳送電子郵件通知時使用的寄件者身分識別。</td>
<td>商店檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>訂單部分取消的電子郵件模板</strong></td>
<td>用於通知註冊客戶的電子郵件消息模板。 整合會提供預設範本。</td>
<td>商店檢視</td>
<td>否</td>
</tr>
<td><strong>替代裝貨聯繫人的訂單部分取消電子郵件模板</strong></td>
<td>用於通知訂單中命名的其他聯繫人的電子郵件消息模板。 整合會提供預設範本。</td>
<td>商店檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>部分取消來賓訂單</strong></td>
<td>用於通知來賓客戶的電子郵件消息模板。 整合會提供預設範本。</td>
<td>商店檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>將訂單部分取消的電子郵件副本發送到</strong></td>
<td>以逗號分隔的電子郵件地址清單，用於傳送每個通知的副本。</td>
<td>商店檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>發送訂單部分取消的複製方法</strong></td>
<td>要使用的電子郵件複製方法 — 碳複製。</td>
<td>商店檢視</td>
<td>否</td>
</tr>
</tbody></table>

## 收貨方商店

<table>
<thead>
<tr>
<th><strong>欄位</strong></th>
<th><strong>說明</strong></th>
<th><strong>範圍</strong></th>
<th><strong>必填</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>訂單已發貨到儲存產品電子郵件發件人</strong></td>
<td>發送給指定商家人員的電子郵件，作為所有未結訂單的匯總報告，在其庫存可用之前，這些未結訂單在商家商店中不能被挑選。 </br></br> 商戶可以使用此報表來起始和管理商店到商店的庫存轉移或補充。 </br></br>此通知僅適用於 [!DNL Ship-to-Store] 功能。
</br></br>此標籤不會影響所選發運承運人或其可用的發運方法標籤。</br></br></td>
<td>商店檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>收貨方儲存電子郵件收件人</strong></td>
<td>以逗號分隔的電子郵件地址清單，用於傳送每個通知的副本。</td>
<td>商店檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>電子郵件範本</strong></td>
<td>用於通知收件者的電子郵件訊息範本。 整合會提供預設範本。</td>
<td>商店檢視</td>
<td>否</td>
</tr>
</tbody></table>

>[!NOTE]
>
>如果允許延交訂單，則必須提供管理員電子郵件地址來接收這些訂單的通知。 將地址添加到以下配置設定中： **[!UICONTROL Send Order Delayed Email Copy To]** 在 [訂單延遲](#order-delayed) 範本和 [!UICONTROL Ship To Store Email Recipients] 在 [收貨方商店](#ship-to-store) 範本。



