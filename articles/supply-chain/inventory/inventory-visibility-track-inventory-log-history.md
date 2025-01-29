---
title: Log and view successful API posts
description: Learn how to set up and use the inventory log history feature for Inventory Visibility. This feature creates a log of successfully updated inventory API posts.
author: yufei-huang
ms.author: yufeihuang
ms.topic: how-to
ms.date: 11/20/2023
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Log and view successful API posts

[!include [banner](../includes/banner.md)]

This article describes how to set up and use the *inventory log history* feature for Inventory Visibility. This feature creates a log of successfully updated inventory API posts. The posts include a timestamp and specify the API type.

## Set up inventory log history

To start to keep a log of successfully updated inventory API posts, you must enable the feature in Microsoft Power Apps.

1. Sign in to Power Apps, and go to **Inventory Visibility** \> **Settings** \> **Feature Management**.
1. Enable the *Inventory log history* feature.
1. Go to **Admin settings**, and select **Update configuration**.

## View inventory log history

After the feature is enabled, you can view the log entries either by using the Inventory Visibility app in Power Apps or by calling the API.

### View log entries by using the Inventory Visibility app in Power Apps

Follow these steps to view the log by using the Inventory Visibility app in Power Apps.

1. Sign in to Power Apps, and go to **Inventory Visibility** \> **Operational visibility** \> **Inventory log history**.
1. Enter a product ID, organization ID, site ID, warehouse ID, and date range to retrieve and view the log details.

### Retrieve log entries by calling the API

Follow these steps to retrieve log entries by calling the [Inventory Visibility API](inventory-visibility-api.md).

1. Run a tool that lets you call APIs. Use the tool to access the `{inventoryVisibilityEndpoint}/api/environment/{yourEnvironmentId}/logTransactionDetails` API by using the `Post` method.
1. Set up and submit a request body to retrieve the log data that you're interested in. The following example shows a request body that asks the system to prepare and retrieve the log. This step is necessary because the log is stored in Azure Data Lake and is transferred to Dataverse only on request. The API returns a log history job ID that you can use to check the job completion status.

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
        "id": "id-contoso-{{datetime}}",
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

1. Use the `{inventoryVisibilityEndpoint}/api/environment/{yourEnvironmentId}/getJobProgress?jobId={jobIdFromPreviousStep}` API to track the status of the inventory log history job.
1. When the API reports that the job is successfully completed, you can review the logs in Dataverse by opening the transaction logging report table (`is_transactionloggingreport`).
