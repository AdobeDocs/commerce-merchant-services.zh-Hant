---
title: 安全性與合規性
description: 檢閱您網站的安全與法規遵循需求。
exl-id: 083c5a12-1d78-48b5-b9e3-612b104ce7e0
feature: Payments, Checkout, Compliance
redirect_from: https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/security.html
source-git-commit: 5fe23b5aba9ad0a2a6c995fa6ade78f46fe7e3e1
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 0%

---

# 安全性與合規性

安全性是 [!DNL Payment Services] 而且您的系統不會傳遞任何私人或支付卡產業(PCI)規範資訊。 [!DNL Payment Services].

## 商務安全性

[!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 包含對多項安全性功能的支援。

另請參閱 [安全性](https://docs.magento.com/user-guide/stores/security.html){target="_blank"} 核心使用指南中的安全性最佳實務，並瞭解如何管理管理員工作階段和認證、實作驗證碼及管理網站限制。

## PCI法規遵循

支付卡產業(PCI)針對接受透過網際網路以信用卡付款的企業建立了一套要求。 除了維護安全的環境之外，處理客戶信用卡資訊的商戶也應負責符合某些標準准則。

另請參閱 [PCI法規遵循指南](https://docs.magento.com/user-guide/stores/compliance-pci.html){target="_blank"} 以取得詳細資訊。

商家可以完成 [自我評估問卷(SAQ)](https://www.pcisecuritystandards.org/pci_security/completing_self_assessment){target="_blank"}，這是一套自我驗證工具，用於評估持卡人資料的安全性。

### 信用卡欄位

若使用信用卡欄位，您的服務不會傳遞PCI管制的資料。 您不必儲存或維護這些資料，這大大降低了PCI法規遵循問題。

### 3DS

PCI 3-D Secure (3DS)可讓購買者線上上購買信用卡時，與其信用卡發行者進行驗證。 此額外的安全性層級有助於防止線上詐騙，是歐盟(EU)法規的必要專案。

[!UICONTROL Payment Services] 提供3DS功能，讓商戶遵守歐盟法規，並保護客戶和商戶免受其商店中的詐騙活動。

如果您是歐盟或英國境內需要3DS規範的商家，您必須手動開啟3DS (這是 `Off` 預設的)，在 [設定](settings.md#credit-card-fields).

>[!NOTE]
>
>3DS需求適用於企業和持卡人銀行位於 [歐洲經濟區](https://www.efta.int/eea) (EEA)和英國。 美國商家不需要3DS，但可視需要為其交易啟用。

商家/店舖人員為買家下單的訂單未設定3DS合規性措施。

另請參閱 [設定中的3DS](settings.md#3ds) 以取得詳細資訊。

### 卡片存放

當購物者 [儲存庫（或「儲存」）的信用卡資訊](vaulting.md) 若是未來在您商店購物，購物者會共用最低限度的信用卡資訊（最後四位數、卡片到期日及卡片品牌）。 信用卡資訊會與付款提供者一併儲存。 當卡片過期或不再需要儲存資訊時，可以刪除該Token，讓付款提供者不再儲存資訊。

另請參閱 [信用卡保險存放](vaulting.md) 以取得詳細資訊。

### PayPal付款按鈕

使用PayPal付款按鈕，您的服務不會傳遞PCI管制的資料。 您不必儲存或維護這些資料，這大大降低了PCI法規遵循問題。

基於安全考量，PayPal在結帳時不會傳送帳單地址 — 國家/地區、電子郵件和名稱是唯一使用的帳單資訊。 您可以選擇啟用網站的PayPal結帳，連絡PayPal並完成審查程式，以傳回完整的帳單地址。

PayPal也整合了防欺詐功能，使用機器學習協助您對抗欺詐行為。 請參閱PayPal的 [賣方保護檔案](https://www.paypal.com/us/webapps/mpp/security/seller-protection) 以取得詳細資訊。

## 欺詐保護

您可以使用為支付服務啟用自動詐騙保護 [代表擴充功能](https://commercemarketplace.adobe.com/signifyd-module-connect.html).

另請參閱 [有效保護詐騙](fraud-protection.md) 以取得詳細資訊。

