---
# required metadata

title: Customer aging data storage
description: This article describes the process of using external storage for customer aging data. You can run the Customer aging data storage process to make the output available for export to an external system.
author: JodiChristiansen
ms.date: 10/27/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.assetid: 3d43ba40-780c-459a-a66f-9a01d556e674
ms.search.region: Global
# ms.search.industry: 
ms.author: jchrist
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Customer aging data storage

[!include [banner](../includes/banner.md)]

This article describes the process of using external storage for customer aging data. In Microsoft Dynamics 365 Finance, you can run the **Customer aging data storage** process to make the output available for export to an external system. When you run the process, the same aging report options that are available in the system are available to external systems. The details are always included in the exported data.

It can be helpful to make customer aging data available to an external system for storage in cases where the output contains many customers and/or many transactions. If the existing **Customer aging** report times out because it has too much data to print, this feature provides an alternative way to get the same data.

## Enable the Customer aging data storage feature

Before you can use this feature, you must enable it in your system. Administrators can use the feature management settings to check the status of the feature and enable it if it's required. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** Credit and collections
- **Feature name:** Customer aging data storage

## Run the Customer aging data storage process

1. Go to **Credit and collections \> Inquiries and reports \> Customer \> Customer aging data storage**.
2. Select **New**.
3. In the **Name** field, enter a name for the process.
4. Set the remaining parameters as you require.

    > [!NOTE]
    > Transaction details are always included, and the processing is always done in a batch job.

5. Select **OK**.
6. Refresh the **Customer aging data storage** page to see the **Batch name** and **Batch run time** values that are shown together with the **Processing status** value. When the batch job is completed, the **Processing status** field is set to **Ended** and the **Number of aging lines** field is set. If the batch job is recurring, the **Processing status** field is set to **Waiting**.
7. Select the **Filter** button next to the **Number of aging lines** field to review the filters that have been added for the batch job.

The **Customer aging data storage** page doesn't include the results. However, the **Customer aging data storage** data entity lets you export the output to any format that Data management supports.

> [!NOTE]
> Before you do an export, add a filter to limit the exported results to the most recent aging. For example, add the following criteria to return the most recent batch run:
>
> (CustAgingDataStorageSysQueryRangeUtil::getLatestBatchName())
>
> Alternatively, add the following criteria to return the most recent batch run for the current user:
>
> (CustAgingDataStorageSysQueryRangeUtil::getLatestBatchNameForCurrentUser())
