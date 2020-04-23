---
# required metadata

title: Metrics setup for IoT Intelligence core insights
description: This topic describes how to setup metrics for IoT Intelligence core insights.
author: robinarh
manager: AnnBe
ms.date: 04/25/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom:
ms.search.region: Global
# ms.search.industry: 
ms.author: rhaertle
ms.search.validFrom: 2020-04-25
ms.dyn365.ops.version: AX 7.0.0
---

# Metrics setup for IoT Intelligence core insights

[!include [banner](../../includes/banner.md)]

If you want to view graphs of your messages in Supply Chain Management, you must setup the metrics using this steps:

1. Copy the Redis cache connection string:
    1. In Azure, go to the Redis cache.
    2. Navigate to **Settings** \> **Access keys**.
    3. Copy the **Primary connection string** field.
2. In Supply Chain Management, navigate to **Production control \> Setup \> IoT Intelligence \> Scenario parameters**.  
    1. On the **Scenario parameters** page, in the **Time series** tab, copy the connection string into the textbox for **Redis metric store connection string**. This allows the metrics from IoT Hub to be visualized in Supply Chain Management.
3. Navigate to **Production control \> Inquiries and reports \> IoT Intelligence \> Metric keys**.
    1. On the **Metric keys** page, click **Update**.
    2. In the **Update metric keys** dialog that appears, the value in the dropdown is **Run in the background**. Click **OK**.
    3. All the metric keys in the Redis cache are retrieved, and added to the **Metric keys** list.
4. Navigate to **Production control \> Manufacturing execution \> Resource Status**. On the **Resource status** page, enter the values in the **Configure** pane.
    1. Select an item to monitor from the **Resource** list.
    2. Select the edit button for **Time series 1**.
    3. Select a metric from the table on the **Select time series** dialog. (You can also use the **Update metric keys** link to update the metric keys from this dialog.)
    4. Click **OK** to return to the **Configure** dialog.
    5. Enter a display name.
    6. Select a time frame for **Show data from**.
    7. Click OK.
5. The graph is displayed.

## How to delete a metric key

To delete a metric key.
