---
title: 簽出流
description: 概述 [!DNL Express Checkout] 在Adobe Commerce。
exl-id: 82761627-a0d4-4cb0-aad1-9865fcb550d4
source-git-commit: 163dd5260908b4ea3a8bfbcfdb834531d1603734
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 0%

---

# [!DNL Express Checkout] 流

>[!IMPORTANT]
>
> 此功能僅適用於早期採用者計畫(EAP)用戶，尚不適用於所有客戶。 目前僅限於美國客戶。 請聯繫Adobe Commerce支援部門以獲取幫助和問題。

本節概述了使用 [!DNL Express Checkout] Adobe Commerce分機。

成功 [!DNL Express Checkout] 流包含以下步驟：

1. 開啟店面，在購物車中添加物品。
1. 繼續簽出。

![簽出](../assets/proceed-checkout.png)

1. 當出現提示時，輸入與Bolt帳戶關聯的電子郵件地址。
1. 輸入發送到該Bolt帳戶的電子郵件地址或電話號碼的一次性密碼(OTP)。
1. 使用Bolt帳戶登錄後，簽出詳細資訊將自動填寫：

   - 裝運資訊
   - 付款方式

   >[!NOTE]
   >
   > 即使您的結帳詳細資訊自動填寫，您也可以使用現有的錢夾資訊（地址或信用卡資訊）。

1. 下訂單。

的 [!DNL Express Checkout] 與標準的附加Adobe Commerce結帳選項相容，如 [禮品卡](https://docs.magento.com/user-guide/catalog/product-gift-card.html) 或 [折扣代碼](https://docs.magento.com/user-guide/marketing/price-rules-cart-coupon.html)。

## [!DNL Express Checkout] 使用案例

的 [!DNL Express Checkout] 允許在簽出流程中使用多個用例：

- 具有註冊的Bolt帳戶的來賓用戶。
- 具有新Bolt帳戶的來賓用戶。
- 具有/不具有註冊的Bolt帳戶的現有Adobe Commerce用戶。

## 來賓用戶簽出：它的工作原理

來賓簽出體驗與登錄體驗不同。 當購物者將電子郵件地址輸入結帳時， [!DNL Express Checkout] 驗證它以查找現有的Bolt帳戶。

### 已註冊的螺栓帳戶

如果找到Bolt帳戶，購物者將繼續使用 [!DNL Express Checkout] 無縫的結賬體驗：

1. 根據Bolt帳戶中用戶的首選項，輸入發送到該Bolt帳戶的電子郵件地址或移動地址的一次性密碼(OTP)。
1. 使用Bolt帳戶登錄後，它將自動填寫簽出詳細資訊：

   - 裝運資訊
   - 付款方式

1. 下訂單。

>[!TIP]
>
> 來賓用戶下訂單，可在Adobe Commerce註冊。

### 新建Bolt帳戶

如果找不到Bolt帳戶，購物者將繼續使用預設的現成Adobe Commerce結帳，購物者將提供所有必要的詳細資訊來訂購：

- 發運和開單資訊
- 裝運方法
- 複核付款方法
- 出現一個複選框，用於在下訂單前在Bolt中註冊以加快簽出速度。 他們可以同意建立其Bolt帳戶的條款和條件。

   ![記住博爾特](../assets/checked-bolt.png)

- 來賓用戶下訂單，可在Adobe Commerce註冊。

## 現有Adobe Commerce用戶：它的工作原理

現有用戶可以在用戶將訂單與 [!DNL Express Checkout] 更快的結帳體驗。

當購物者將電子郵件地址輸入結帳時， [!DNL Express Checkout] 驗證它以查找現有的Bolt帳戶。

### 已註冊的Bolt帳戶，Adobe Commerce用戶

如果找到Bolt帳戶，購物者將繼續使用預設的現成Adobe Commerce結帳，購物者將提供所有必要的詳細資訊，然後下單：

- 發運和開單資訊
- 裝運方法
- 複核付款方法

請參閱 [故障排除](../express-checkout/troubleshooting.md) 主題，以獲取現有的Adobe Commerce用戶身份下訂單時遇到的問題。

>[!NOTE]
>
> 如果用戶具有Bolt帳戶，並且電子郵件未在Adobe Commerce註冊，則會觸發一次性密碼(OTP)登錄。 查看 [已註冊的螺栓帳戶](#registered-bolt-account) 。

### 新建Bolt帳戶

如果找不到Bolt帳戶，購物者將繼續其預設的Adobe Commerce結帳，購物者從保存的資訊中選擇所有必要的詳細資訊來下訂單：

- 發運和開單資訊
- 裝運方法
- 複核付款方法
- 出現一個複選框，用於在下訂單前在Bolt中註冊以加快簽出速度。 他們可以同意建立其Bolt帳戶的條款和條件。

   ![記住博爾特](../assets/checked-bolt.png)

## 獲取幫助

請聯繫Adobe Commerce支援部門以獲取幫助和問題。
