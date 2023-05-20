---
title: 安全性和合規性
description: 查看您的站點的安全性和合規性要求。
exl-id: 083c5a12-1d78-48b5-b9e3-612b104ce7e0
source-git-commit: bfce1cb702d634647022a92669d704dd82fe41e6
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---

# 安全性和合規性

安全是 [!DNL Payment Services] 並且您的PCI中沒有傳遞私有或支付卡行業(PCI)規範的資訊 [!DNL Payment Services]。

## 商業安全

[!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 包括對幾種安全功能的支援。

請參閱 [安全](https://docs.magento.com/user-guide/stores/security.html){target="_blank"} 在核心使用手冊中，查看安全最佳實踐，瞭解如何管理管理會話和憑據、實施驗證碼查詢和管理網站限制。

## PCI合規性

支付卡行業(PCI)為接受通過Internet通過信用卡付款的企業制定了一套要求。 除了維護安全環境外，處理客戶信用卡資訊的商家還負責滿足一些標準准則。

請參閱 [PCI合規性指南](https://docs.magento.com/user-guide/stores/compliance-pci.html){target="_blank"} 的子菜單。

商家可以 [自評調查表](https://www.pcisecuritystandards.org/pci_security/completing_self_assessment){target="_blank"}它是評估持卡人資料安全性的自驗證工具。

### 信用卡欄位

使用「信用卡欄位」，您的服務中不會傳遞PCI管制的資料。 您不必儲存或維護該資料，這會大大降低PCI合規性問題。

### 3DS

PCI 3-D Secure(3DS)使購買者在進行線上信用卡購買時能夠與信用卡發行者進行身份驗證。 這一額外的安全層有助於防止線上欺詐，並且是歐盟（歐盟）合規條例的一部分。

[!UICONTROL Payment Services] 提供3DS功能，使商戶能夠遵守歐盟法規，並保護客戶和商戶不在其商店中從事欺詐活動。

如果您是歐盟或英國內需要遵守3DS法規的商家，則必須手動啟用3DS(它是 `Off` 預設) [設定](settings.md#credit-card-fields)。

>[!NOTE]
>
>3DS要求適用於業務和持卡人銀行位於 [歐洲經濟區](https://www.efta.int/eea) (EEA)和英國。 美國商戶不需要3DS，但如果需要，可以啟用3DS進行交易。

商家/商店人員為買方下達的訂單未配置3DS合規性措施。

請參閱 [3DS設定](settings.md#3ds) 的子菜單。

### 卡保險儲存

當購物者 [保管庫 — 或「保存」 — 其信用卡資訊](vaulting.md) 對於將來在你的商店中購買的商品，會與購物者共用最少的信用卡資訊（最後四位數、卡過期日期和卡牌品牌）。 信用卡資訊與付款提供方一起儲存。 當卡過期或不再需要保存資訊時，他們可以刪除該令牌，以便支付提供商不再儲存該資訊。

請參閱 [信用卡保險儲存](vaulting.md) 的子菜單。

### PayPal智慧按鈕

使用PayPal Smart Buttons，您的服務中不會傳遞PCI調節的資料。 您不必儲存或維護該資料，這會大大降低PCI合規性問題。

出於安全原因，PayPal在結帳期間不會傳遞帳單地址 — 國家/地區、電子郵件和名稱是使用的唯一帳單資訊。 您可以選擇啟用站點的PayPal結帳，以通過聯繫PayPal並完成審查流程來返回完整的開單地址。

PayPal還整合了欺詐保護，利用機器學習幫助你打擊欺詐行為。 請參閱PayPal`s [賣家保護文檔](https://www.paypal.com/us/webapps/mpp/security/seller-protection) 的子菜單。
