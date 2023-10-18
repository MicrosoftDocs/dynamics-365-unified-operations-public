---
title: Log and view successful API posts
description: The inventory log history feature for Inventory Visibility creates a log of successfully updated inventory API posts, which include a timestamp and specify the API type. This article describes how to set up and use the feature.
author: yufeihuang
ms.author: yufeihuang
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/18/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Log and view successful API posts

The *inventory log history* feature for Inventory Visibility creates a log of successfully updated inventory API posts, which include a timestamp and specify the API type. This article describes how to set up and use the feature.

## Set up inventory log history

To start keeping the log of successfully updated inventory API posts, you must enable the feature in Power Apps. Follow these steps to enable the feature:

1. Make sure your Dataverse solutions are in version 1.2.2.1 or higher. <!-- KFM: Version of which Dataverse solutions? How do I make sure of this? -->
1. Sign into Power Apps and go to **Inventory Visibility \> Settings \> Feature Management**.
1. Enable the *Inventory log history* feature.
1. Go to **Admin settings** and select **Update configuration**.

## View inventory log history

Once you have enabled the log, you can view the log entries either by using the Inventory Visibility app in Power Apps or by calling the API.

### View log entries using the Inventory Visibility app in Power Apps

Follow these steps to view the log using the Inventory Visibility app in Power Apps:

1. Sign in to Power Apps and go to **Inventory Visibility \> Operational visibility \> Inventory log history**.
1. Enter a product ID, org ID, site ID, warehouse ID and date range to retrieve and view the log details.

### Retrieve log entries by calling the API

Follow these steps to retrieve log entries by calling the [Inventory Visibility API](inventory-visibility-api.md):

1. Run a tool that lets you call APIs (such as [Postman](https://www.postman.com/)) and use it to access the `{inventoryVisibilityEndpoint}/api/environment/{yourEnvironmentId}/logTransactionDetails` API using the `Post` method.
1. Set up and submit a request body to retrieve the log data you are interested in <!-- KFM:What does this message do? Just start a job and return a job ID? What does that job do?  -->. Here's an example:

    ```txt
    
    Path:
    
        /api/environment/{environmentId}/logTransactionDetails
    
    Method:
    
        Post
    
    Headers:
    
        Api-Version="1.0"

        Authorization="Bearer $access_token"
    
    ContentType:
    
        application/json
    
    Body:
    
        {
        "id": "id-postman-{{datetime}}",
        "organizationId": "usmf",
        "UtcFromDate": "2023/8/23",
        "UtcToDate": "2023/8/23",
        "productId": "D0001",
        "dimensions": {
            "SiteId": "1",
            "LocationId": "13"
        }
    }
    
    ```

1. Use the `{inventoryVisibilityEndpoint}/api/environment/{yourEnvironmentId}/getJobProgress?jobId={jobIdGotInLastStep}` API to track the status of inventory log history job. <!-- KFM: What "job" is this? What is going on here? This should be mentioned in the intro. -->
1. Once the job is completed successfully, you can check all the logs in Dataverse table: Transaction Logging Report (`is_transactionloggingreport`). <!-- KFM: Does this API call create or update this table instead of returning the log entries? What is going on here? How do I do this step?  -->
