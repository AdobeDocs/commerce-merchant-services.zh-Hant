---
title: 銷售電子郵件範本
description: 設定異動電子郵件範本，以便在「商店取貨」訂單的履行程式期間與客戶和商店管理員通訊。
role: User, Admin
level: Intermediate
exl-id: 688732e3-06f0-4613-a589-2d465597eb28
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '1202'
ht-degree: 0%

---


# 銷售電子郵件範本

Store Fulfillment提供一組擴充的交易式電子郵件範本，以支援訂單和履行工作流程。 它們提供跨頻道一致、自動化的通訊和傳訊，可通知客戶和商店管理員訂單狀態變更、店內取貨訂單指示等。

「商店履行」電子郵件範本已設定預設訊息與設定。 Adobe Commerce中的商家管理員可以管理和修改設定，並選取電子郵件範本，以在不同情境中與客戶通訊。 管理員也可以設定和自訂範本。

從管理員設定銷售電子郵件範本： **[!UICONTROL Stores > Configuration > Sales > Sales Emails]**.

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
<td>停用此功能。 不支援非同步電子郵件傳送。 為了讓「商店見面交收」的通訊和回應時間最短，請立即傳送電子郵件，而非批次處理。 </td>
<td>存放區檢視</td>
<td>否</td>
</tr>
</tbody></table>

## 已準備好在商店取貨的訂單

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
<td>當店舖相關人員完成揀選訂單後，就會傳送此電子郵件給客戶。 設為「否」可停用電子郵件通知。 如果電子郵件範本已停用，並不會阻止商店關聯人員挑選訂單。</td>
<td>存放區檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>訂單已準備好接收電子郵件寄件者</strong></td>
<td>傳送電子郵件通知時使用的寄件者身分。</td>
<td>存放區檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>訂單準備取貨電子郵件範本</strong></td>
<td>用於通知註冊客戶的電子郵件訊息範本。 預設範本會與整合一併提供。</td>
<td>存放區檢視</td>
<td>否</td>
</tr>
<td><strong>客人的訂單準備取貨電子郵件範本</strong></td>
<td>用於通知來賓客戶的電子郵件訊息範本。 預設範本會與整合一併提供。</td>
<td>存放區檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>替代取貨連絡人的訂單準備取貨電子郵件範本</strong></td>
<td>用於通知訂單中指定之其他連絡人的電子郵件訊息範本。 預設範本會與整合一併提供。</td>
<td>存放區檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>將訂單準備取貨電子郵件副本傳送至</strong></td>
<td>以逗號分隔的電子郵件地址清單，用於傳送每個通知的副本。</td>
<td>存放區檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>傳送訂單準備取貨電子郵件複製方法</strong></td>
<td>要使用的電子郵件複製方法（復本）。</td>
<td>存放區檢視</td>
<td>否</td>
</tr>
</tbody></table>


## 已在市集內取得訂單

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
<td>當客戶確認其已從商店取貨時，系統會傳送此電子郵件給客戶。 設為「否」可停用電子郵件通知。 如果電子郵件範本已停用，它不會阻止客戶提取訂單。</td>
<td>存放區檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>已接取訂單電子郵件寄件者</strong></td>
<td>傳送電子郵件通知時使用的寄件者身分。</td>
<td>存放區檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>已提取訂單的電子郵件範本</strong></td>
<td>用於通知註冊客戶的電子郵件訊息範本。 預設範本會與整合一併提供</td>
<td>存放區檢視</td>
<td>否</td>
</tr>
<td><strong>已提取訪客的訂單電子郵件範本</strong></td>
<td>用於通知來賓客戶的電子郵件訊息範本。 預設範本會與整合一併提供。</td>
<td>存放區檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>傳送已提取電子郵件副本至</strong></td>
<td>以逗號分隔的電子郵件地址清單，用於傳送每個通知的副本。</td>
<td>存放區檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>傳送已選取電子郵件複製方法</strong></td>
<td>要使用的電子郵件複製方法（復本）。</td>
<td>存放區檢視</td>
<td>否</td>
</tr>
</tbody></table>

## 訂單已延遲

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
<td>此電子郵件會傳送給客戶，通知他們商戶商店的處理或取貨延遲。 設為「否」可停用電子郵件通知。 如果電子郵件範本已停用，功能不會防止訂單延遲。</td>
<td>存放區檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>訂單延遲的電子郵件寄件者
</strong></td>
<td>傳送電子郵件通知時使用的寄件者身分。</td>
<td>存放區檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>訂單延遲的電子郵件範本</strong></td>
<td>用於通知註冊客戶的電子郵件訊息範本。 預設範本會與整合一併提供。</td>
<td>存放區檢視</td>
<td>否</td>
</tr>
<td><strong>訪客的訂單延遲電子郵件範本</strong></td>
<td>用於通知來賓客戶的電子郵件訊息範本。 預設範本會與整合一併提供。</td>
<td>存放區檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>將訂單延遲的電子郵件副本傳送至</strong></td>
<td>以逗號分隔的電子郵件地址清單，用於傳送每個通知的副本。</td>
<td>存放區檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>傳送訂單延遲複製方法</strong></td>
<td>要使用的電子郵件複製方法（復本）。</td>
<td>存放區檢視</td>
<td>否</td>
</tr>
</tbody></table>



## 訂單已取消

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
<td>此電子郵件會傳送給客戶，通知他們已在商戶商店取消其訂單。 設定為 <code>No</code> 以停用電子郵件通知。 如果電子郵件範本已停用，其功能不會阻止訂單被取消。</td>
<td>存放區檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>訂單已取消的電子郵件寄件者
</strong></td>
<td>傳送電子郵件通知時使用的寄件者身分。</td>
<td>存放區檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>已取消訂單的電子郵件範本</strong></td>
<td>用於通知註冊客戶的電子郵件訊息範本。 預設範本會與整合一併提供。</td>
<td>存放區檢視</td>
<td>否</td>
</tr>
<td><strong>已取消訪客的訂單</strong></td>
<td>用於通知來賓客戶的電子郵件訊息範本。 預設範本會與整合一併提供。</td>
<td>存放區檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>將訂單取消的電子郵件副本傳送至</strong></td>
<td>以逗號分隔的電子郵件地址清單，用於傳送每個通知的副本。</td>
<td>存放區檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>傳送已取消訂單的複製方法</strong></td>
<td>要使用的電子郵件複製方法（復本）。</td>
<td>存放區檢視</td>
<td>否</td>
</tr>
</tbody></table>


## 訂單已部份取消

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
<td>此電子郵件會傳送給客戶，通知他們已在商戶商店取消部分訂單。 設定為 <code>No</code> 以停用電子郵件通知。 如果電子郵件範本已停用，並不會阻止部分取消訂單。</td>
<td>存放區檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>部分取消的訂單電子郵件寄件者
</strong></td>
<td>傳送電子郵件通知時使用的寄件者身分。</td>
<td>存放區檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>部分取消的訂單電子郵件範本</strong></td>
<td>用於通知註冊客戶的電子郵件訊息範本。 預設範本會與整合一併提供。</td>
<td>存放區檢視</td>
<td>否</td>
</tr>
<td><strong>替代取貨聯絡人的訂單部分取消的電子郵件範本</strong></td>
<td>用於通知訂單中指定之其他連絡人的電子郵件訊息範本。 預設範本會與整合一併提供。</td>
<td>存放區檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>已部分取消客人的訂單</strong></td>
<td>用於通知來賓客戶的電子郵件訊息範本。 預設範本會與整合一併提供。</td>
<td>存放區檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>將部分取消的訂單電子郵件副本傳送至</strong></td>
<td>以逗號分隔的電子郵件地址清單，用於傳送每個通知的副本。</td>
<td>存放區檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>傳送部分取消的訂單複製方式</strong></td>
<td>要使用的電子郵件複製方法（復本）。</td>
<td>存放區檢視</td>
<td>否</td>
</tr>
</tbody></table>

## 送貨至商店

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
<td><strong>Order具有Ship To Store Products電子郵件寄件者</strong></td>
<td>傳送給指定商家人員的電子郵件，作為所有未結訂單的彙總報表，這些訂單在商家商店存貨可用之前無法領料。 </br></br> 商戶可以使用此報表來初始化及管理儲存至儲存庫的存貨移轉或補貨。 </br></br>此通知僅適用於 [!DNL Ship-to-Store] 功能已啟用。
</br></br>此標籤不會影響選取的送貨業者或其可用的送貨方式標籤。</br></br></td>
<td>存放區檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>收貨方儲存電子郵件收件者</strong></td>
<td>以逗號分隔的電子郵件地址清單，用於傳送每個通知的副本。</td>
<td>存放區檢視</td>
<td>否</td>
</tr>
<tr>
<td><strong>電子郵件範本</strong></td>
<td>用於通知收件者的電子郵件訊息範本。 預設範本會與整合一併提供。</td>
<td>存放區檢視</td>
<td>否</td>
</tr>
</tbody></table>

>[!NOTE]
>
>如果您允許延期交貨，則必須提供管理員電子郵件地址，以接收有關這些訂單的通知。 將位址新增至下列組態設定： **[!UICONTROL Send Order Delayed Email Copy To]** 在 [訂單延遲](#order-delayed) 範本，以及 [!UICONTROL Ship To Store Email Recipients] 在 [送貨至商店](#ship-to-store) 範本。



