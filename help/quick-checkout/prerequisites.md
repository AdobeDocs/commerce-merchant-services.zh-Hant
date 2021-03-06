---
title: '"[!DNL Quick Checkout] 先決條件'
description: 「驗證您的系統是否滿足使用 [!DNL Quick Checkout] Adobe Commerce分機"
exl-id: fa61aa73-a2b6-4c69-ab42-cede74c15caa
source-git-commit: 9841db7616c8aa6d5bc5af3e6e92c0abe9a4a1e2
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 1%

---

# [!DNL Quick Checkout] 先決條件

的 [!DNL Quick Checkout] 與Magento Open Source和Adobe Commerce版本相容 `>= 2.4.1-p1`。

請參閱 [登機](../quick-checkout/onboarding.md) 的子菜單。

## 相容性限制

的 [!DNL Quick Checkout] 存在早期訪問程式(EAP)的現有相容性問題：

| **問題** | **約束** |
|----------------|-----------------|
| 僅美國 | 此功能僅適用於美國客戶 |
| 僅美元 | USD是唯一相容的貨幣 |
| [!DNL Amazon Pay] | [!DNL Quick Checkout] 與不相容 [!DNL Amazon Pay] |
| PWA | 僅支援Luma店面 |
| [!DNL 3D Secure] | [!DNL 3D Secure] 不支援 |
| B2B | 不支援B2B |
| ISPU | [!DNL In-Store Pickup] (ISPU)功能不受支援 |
| 多發運 | 不支援多發運 |

請參閱 [[!DNL Bolt] 限制](https://help.bolt.com/integrations/adobe-quick-checkout/set-up/#limitations) 有關相容性限制的詳細資訊主題 [!DNL Bolt] 和 [!DNL Quick Checkout] 擴展。
