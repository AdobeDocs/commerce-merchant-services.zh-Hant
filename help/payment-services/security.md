---
title: 安全性和合規性
description: 查看您的站點的安全性和合規性要求。
exl-id: 083c5a12-1d78-48b5-b9e3-612b104ce7e0
source-git-commit: bcb817775fe9cd9ac7096931dd40d5ec0c4a5cfc
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# 安全性和合規性

安全是 [!DNL Payment Services] 並且您的PCI中沒有傳遞私有或支付卡行業(PCI)規範的資訊 [!DNL Payment Services]。

## 商業安全

Adobe Commerce和Magento Open Source包括對幾種安全功能的支援。

請參閱 [安全](https://docs.magento.com/user-guide/stores/security.html)核心使用手冊中的{target=&quot;_blank&quot;}，用於查看安全最佳實踐，並瞭解如何管理管理員會話和憑據、實施驗證碼驗證和管理網站限制。

## PCI合規性

支付卡行業(PCI)為接受通過Internet通過信用卡付款的企業制定了一套要求。 除了維護安全環境外，處理客戶信用卡資訊的商家還負責滿足一些標準准則。

請參閱 [PCI合規性指南](https://docs.magento.com/user-guide/stores/compliance-pci.html){target=&quot;_blank&quot;}獲取詳細資訊。

商家可以 [自評調查表](https://www.pcisecuritystandards.org/pci_security/completing_self_assessment){target=&quot;_blank&quot;}，它是評估持卡人資料安全性的自驗證工具。

### 信用卡欄位

使用「信用卡欄位」，您的服務中不會傳遞PCI管制的資料。 您不必儲存或維護該資料，這會大大降低PCI合規性問題。

### PayPal智慧按鈕

使用PayPal Smart Buttons，您的服務中不會傳遞PCI調節的資料。 您不必儲存或維護該資料，這會大大降低PCI合規性問題。

出於安全原因，PayPal在結帳期間不會傳遞帳單地址 — 國家/地區、電子郵件和名稱是使用的唯一帳單資訊。 您可以選擇啟用站點的PayPal結帳，以通過聯繫PayPal並完成審查流程來返回完整的開單地址。

PayPal還整合了欺詐保護，利用機器學習幫助你打擊欺詐行為。 請參閱PayPal`s [賣家保護文檔](https://www.paypal.com/us/webapps/mpp/security/seller-protection) 的子菜單。
