---
title: Use Traceability data in Power BI (preview)
description: Learn how to connect Power BI to Traceability add-in for Dynamics 365 Supply Chain Management.
author: banluo-ms
ms.author: banluo
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 07/29/2024
ms.custom: 
  - bap-template
---

# Use Traceability data in Power BI (preview)

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

In Power BI, you can use the public API of the Traceability add-in for Dynamics 365 Supply Chain Management to retrieve data and use it to build your own business reports.

This article describes how to connect Power BI to Traceability add-in for Dynamics 365 Supply Chain Management.

Follow these steps to connect your Power BI report to Traceability:

1. Open Power BI Desktop and open a report or create a new one.
1. On the **Home** tab of the ribbon, select **Get Data** \> **Blank query**.
1. The **Power Query Editor** opens. On the **Properties** pane, rename the new query
1. On the **Queries** pane, right-click on the new query and and choose **Advanced Editor**.
1. In the Advanced editor, enter the following code and edit it to match your environment details:

    ```Power Query M
    let
        accessUrl = "<OAuthEndpoint>",
        accessBody = "client_id=<clientId>&client_secret=<clientSecret>&grant_type=client_credentials&scope=0cdb527f-a8d1-4bf8-9436-b352c68682b2/.default",
        AccessTokenResponse = Json.Document(Web.Contents(accessUrl, [Headers=[#"Content-Type"="application/x-www-form-urlencoded"], Content=Text.ToBinary(accessBody)])),
        AccessToken = AccessTokenResponse[access_token],
    
        bearerUrl = "https://securityservice.operations365.dynamics.com/token",
        bearerBody  = "{ ""grant_type"": ""client_credentials"", ""client_assertion_type"": ""aad_app"", ""client_assertion"": """& AccessToken &""", ""scope"":""https://traceabilityservice.operations365.dynamics.com/.default"", ""context"": ""<environmentId>"", ""context_type"": ""finops-env""}",
        BearerTokenResponse = Json.Document(Web.Contents(bearerUrl,[Headers = [#"Content-Type"="application/json"], Content = Text.ToBinary(bearerBody) ] )),
        BearerToken = BearerTokenResponse[access_token],
        BearerTokenHeader = "Bearer " & BearerToken,
    
        dataUrl = "<queryAPI>",
        dataBody = "{"<query>"}",
        DataResponse = Json.Document(Web.Contents(dataUrl,[Headers = [#"Content-Type"="application/json", #"Authorization"=BearerTokenHeader], Content = Text.ToBinary(dataBody)] )),
        root = DataResponse[root],
        events = root[events],
        #"Converted to Table" = Table.FromList(events, Splitter.SplitByNothing(), null, null, ExtraValues.Error),
        #"Expanded Column1" = Table.ExpandRecordColumn(#"Converted to Table", "Column1", {"eventId", "companyCode", "operator", "activityType", "activityCode", "datetime", "details", "consumptionTransactions", "productTransactions", "recordId"}, {"Column1.eventId", "Column1.companyCode", "Column1.operator", "Column1.activityType", "Column1.activityCode", "Column1.datetime", "Column1.details", "Column1.consumptionTransactions", "Column1.productTransactions", "Column1.recordId"}),
        #"Expanded Column1.details" = Table.ExpandRecordColumn(#"Expanded Column1", "Column1.details", {"operator", "production order", "received warehouse", "received location"}, {"Column1.details.operator", "Column1.details.production order", "Column1.details.received warehouse", "Column1.details.received location"})
    in
        #"Expanded Column1.details"
    ```

    Where you must substitute the following values:

    - *\<OAuthEndpoint\>* – Enter the OAuth 2.0 token endpoint (v2) URL for your Microsoft Entra ID app registration. See also [Authentication](traceability-api.md#authentication).
    - *\<clientId\>* – Enter the Application (client) ID of your Microsoft Entra ID app registration. See also [Authentication](traceability-api.md#authentication).
    - *\<environmentId\>* – Enter the environment ID of your Supply Chain Management environment in lifecycle services.
    - *\<queryAPI\>* – Enter the URL of the Traceability API. See also [API endpoint](traceability-app-configure.md#api-endpoint).
    - *\<query\>* – Enter the query you want to execute. For example: `"tracingDirection"": ""Backward"", ""trackingId"": ""bike-demo~USMF~~bike-s0001~~"",""shouldIncludeEvents"": ""true"`. <!--KFM: We probably need to provide more information about how to formulate this query. -->

1. Select **Done** to save your query. Your query results are now shown in the **Power Query Editor**.

    :::image type="content" source="media/powerbi-query-editor-example.png" alt-text="Example of query results in the Power Query Editor" lightbox="media/backward-search-example.png":::

1. On the **Home** tab of the ribbon, select **Close & Apply**.

1. The data is now available in Power BI, where you can explore it, design visualizations and export the report as needed.

    :::image type="content" source="media/powerbi-report-example.png" alt-text="Example of query results in the Power Query Editor" lightbox="media/powerbi-report-example.png":::
