---
title: 將Adobe Experience Platform Mobile SDK與Commerce整合
description: 瞭解如何搭配無周邊或自訂Commerce店面使用Adobe Experience Platform Mobile SDK。
role: Admin, Developer
feature: Personalization, Integration, Eventing
exl-id: d1340b15-e7de-42b5-ad64-d4c31f0db029
source-git-commit: 4a5877d6e1a5c7d840e36f4913306b0c440bbac5
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 0%

---

# 將Adobe Experience Platform Mobile SDK與Commerce整合

>[!IMPORTANT]
>
>適用於iOS的Adobe Experience Platform Mobile SDK支援iOS 11或更新版本。

整合 [Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/home/) 搭配Commerce行動應用程式，商戶可傳送Commerce  [事件資料](events.md) 到Experience Platform邊緣。

當Commerce事件資料可在邊緣取得時，其他Adobe Experience Cloud應用程式即可存取這些資料。 例如，您可以使用資料在Real-Time CDP中建立受眾，然後 [使用這些對象](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html) 個人化您的Commerce行動應用程式。

## 設定

若要開始搭配Commerce使用Adobe Experience Platform Mobile SDK，請在Experience Platform中安裝並設定SDK。 然後，在Commerce中完成設定。

### Experience Platform

1. 檢閱以下內容以瞭解行動應用程式功能 [行動應用程式中的Adobe Experience Cloud教學課程](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/overview.html).

1. [安裝與設定](https://developer.adobe.com/client-sdks/documentation/getting-started/) Experience Platform中的SDK。

   >[!NOTE]
   >
   >您在Experience Platform中建立和設定的結構描述，與您在Commerce行動應用程式中的應用程式程式碼中使用的結構描述相同。

### 商務

完成Experience平台的SDK設定後，請將SDK設定新增至Commerce。

1. 若要透過SDK傳送Commerce事件資料給Experience Platform，您必須在應用程式程式碼中提供XDM結構描述。 此結構描述必須符合結構描述 [已設定](https://developer.adobe.com/client-sdks/home/getting-started/set-up-schemas-and-datasets/) Experience Platform中的SDK專用。

   下列範例說明如何追蹤 `web.webpagedetails.pageViews` 事件並設定 `identityMap` 使用電子郵件欄位。

   ```swift
   let stateName = "luma: content: ios: us: en: home"
   var xdmData: [String: Any] = [
       "eventType": "web.webpagedetails.pageViews",
       "web": [
           "webPageDetails": [
               "pageViews": [
                   "value": 1
               ],
               "name": "Home page"
           ]
       ]
   ]
   
   let experienceEvent = ExperienceEvent(xdm: xdmData)
   Edge.sendEvent(experienceEvent: experienceEvent)
   
   // Adobe Experience Platform - Update Identity
   
   let emailLabel = "mobileuser@example.com"
   
   let identityMap: IdentityMap = IdentityMap()
   identityMap.add(item: IdentityItem(id: emailLabel), withNamespace: "Email")
   Identity.updateIdentities(with: identityMap)
   ```

1. 連線至Commerce Cloud環境。

   在您的專案組建設定中，新增URL至Commerce GraphQL端點。 例如：

   - 偵錯： http://_偵錯_.commercesite.cloud/graphql/
   - 發行版本： http://_版本_.commercesite.cloud/graphql/

1. 若要從Commerce GraphQL端點擷取資料，請先使用在您的專案中產生必要的檔案和目錄 [Apollo程式碼產生器](https://www.apollographql.com/docs/ios/).

   1. 從您的專案目錄， [安裝](https://www.apollographql.com/docs/ios/get-started#1-install-the-apollo-frameworks) 阿波羅·iOS。

   1. [初始化](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#initialize) Apollo Codegen CLI。

      這會建立 `apollo-codegen-configuration.json` 檔案。

   1. 取代專案中必要的GraphQL檔案和目錄 `apollo-codegen-configuration.json` 檔案包含下列專案：

      ```json
      {
      "schemaName" : "MagentoAPI",
      "input" : {
          "operationSearchPaths" : [
          "**/*.graphql"
          ],
          "schemaSearchPaths" : [
          "**/*.graphqls"
          ]
      },
      "output" : {
          "testMocks" : {
          "none" : {
          }
          },
          "schemaTypes" : {
          "path" : "../MagentoAPI",
          "moduleType" : {
              "swiftPackageManager" : {
              }
          }
          },
          "operations" : {
          "inSchemaModule" : {
          }
          }
      },
      "schemaDownloadConfiguration": {
          "downloadMethod": {
              "introspection": {
                  "endpointURL": "http://magento24.com/graphql/",
                  "httpMethod": {
                      "POST": {}
                  },
                  "includeDeprecatedInputValues": false,
                  "outputFormat": "SDL"
              }
          },
          "downloadTimeout": 60,
          "headers": [],
          "outputPath": "magento.graphqls"
      }
      }
      ```

   1. [擷取](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#fetch-schema) Commerce GraphQL結構描述。

      確保路徑指向 `./apollo-codegen-config.json` 檔案，其中包含對Commerce GraphQL架構的參照。

   1. [產生](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#generate) 原始碼。

      確保路徑指向 `./apollo-codegen-config.json` 檔案，其中包含用來產生必要檔案和目錄的組態資訊。

   1. 在新建立的內部 **GraphQLGerated** 資料夾，新增或編輯GraphQL型別。 例如，您可以新增 `DynamicBlocks.graphql` 輸入以下內容：

      ```graphql
      query dynamicBlocks($input: DynamicBlocksFilterInput){
          dynamicBlocks(input: $input)
          {
              items {
                  content {
                      html
                  }
              }
          }
      }
      ```

   您現在已將Adobe Experience Platform Mobile SDK與Commerce行動應用程式整合。 事件資料會從您的應用程式傳輸至Experience Platform邊緣。

若要瞭解如何從您的行動Commerce應用程式擷取Real-Time CDP對象，以告知購物車價格規則和動態區塊，請參閱 [Audience Activation](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html).
