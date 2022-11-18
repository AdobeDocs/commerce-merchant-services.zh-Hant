---
title: 安全性和合規性
description: 檢查您網站的安全性和合規性要求。
exl-id: 083c5a12-1d78-48b5-b9e3-612b104ce7e0
source-git-commit: c993a2afe5b4da478ab57cbb391bb524d83c3d1a
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# 安全性和合規性

安全是最令人關切的 [!DNL Payment Services] 而且，貴機構中不會傳遞私人或支付卡行業(PCI)監管資訊 [!DNL Payment Services].

## 商務安全

[!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 包括對多個安全功能的支援。

請參閱 [安全性](https://docs.magento.com/user-guide/stores/security.html)核心使用手冊中的{target=&quot;_blank&quot;}，以檢閱安全性最佳實務，並了解如何管理管理員工作階段和憑證、實作CAPTCHA及管理網站限制。

## PCI合規性

支付卡行業(PCI)為接受通過網際網路通過信用卡付款的企業制定了一套要求。 除了維護安全環境外，處理客戶信用卡資訊的商家還負責滿足一些標準准則。

請參閱 [PCI合規性指南](https://docs.magento.com/user-guide/stores/compliance-pci.html){target=&quot;_blank&quot;}以取得詳細資訊。

商戶可以 [自我評估問卷](https://www.pcisecuritystandards.org/pci_security/completing_self_assessment){target=&quot;_blank&quot;}，這是評估持卡人資料安全性的自我驗證工具。

### 信用卡欄位

使用信用卡欄位時，在您的服務中不會傳遞任何PCI規範的資料。 您不必儲存或維護該資料，這大大減少了對PCI合規性的擔憂。

### 卡儲存

購物者 [保管庫（或「保存」） — 其信用卡資訊](vaulting.md) 對於您未來在商店中的購買，最低的信用卡資訊會與購物者共用（最後四位數、卡的到期日和卡的品牌）。 信用卡資訊與支付提供者一起儲存。 當資訊卡過期，或不再需要儲存的資訊時，他們可以刪除該代號，讓支付提供者不再儲存該資訊。

### PayPal智慧按鈕

使用PayPal智慧按鈕時，不會在服務中傳遞PCI規範的資料。 您不必儲存或維護該資料，這大大減少了對PCI合規性的擔憂。

出於安全原因，PayPal在結帳期間不會傳遞帳單地址 — 國家/地區、電子郵件和名稱是唯一使用的帳單資訊。 您可以聯絡PayPal並完成審查程式，選擇性地啟用網站的PayPal結帳，以傳回完整的帳單地址。

PayPal還整合了欺詐保護功能，利用機器學習來幫助您打擊欺詐。 請參閱PayPal [賣方保護檔案](https://www.paypal.com/us/webapps/mpp/security/seller-protection) 以取得更多資訊。
