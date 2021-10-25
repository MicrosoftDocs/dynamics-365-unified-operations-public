---
# required metadata

title: Customer aging data storage
description: This topic describes the process of using external storage for customer aging data. You can run Customer aging data storage to make the output available to export to an external system.
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
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
ms.custom: 14151
ms.assetid: 3d43ba40-780c-459a-a66f-9a01d556e674
ms.search.region: Global
# ms.search.industry: 
ms.author: jchrist
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Customer aging data storage 

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic describes the process of using external storage for customer aging data. In Microsoft Dynamics 365 Finance, you can run Customer aging data storage to make the output available to export to an external system. When running the process, the same aging report options are available. The details are always included in the exported data.

Making customer aging data available to an external system for storage is helpful in cases where the output contains many customers and/or many transactions. When the existing Customer aging report times out because it has too much data to print, this provides an alternative method to get the same data. 

## Enable the Customer aging data storage feature

Before you can use this feature, you must enable it in your system. Administrators can use the feature management settings to check the feature status and enable it if needed. Here, the feature is listed as:

- Module - Credit and collections
- Feature name - Customer aging data storage

## Run a Customer aging data storage
1. Go to **Credit and collections > Inquires and reports > Customer > Customer aging data storage**.
2. Select **New**.
3. In the **Name** field, enter a name for the process.
4. Select the rest of the parameters as you require. 

   Transaction details are always included. 

   Processing is always doen in a batch job. 

5. Select **OK**. 
6. Refresh the **Customer aging data storage** page to see the **Batch name** and **Batch run time** that are shown along with the **Processing status**. When the batch job is complete the **Processing status** is set to **Ended** and the **Number of aging lines** is populated. If the batch job is recurring the Processing status is set to **Waiting**.
7. Click the **Filter** icon next to **Number of aging lines** field to review the fileters added for this batch job.
8. The **Customer aging data storage** page doesn't include the results; however, the **Customer aging data storage** data entitiy lets you export the output to any format that Data management supports. 

> [!NOTE]
> Before exporting, add a filter to limit the exported results to only the most recent aging. For example, add the following criteria to return the most recent batch run:<br> (CustAgingDataStorageSysQueryRangeUtil::getLatestBatchName())<br>
Alternatviely, use the below criteria to return the most recent batch run for the current user:<br>
(CustAgingDataStorageSysQueryRangeUtil::getLatestBatchNameForCurrentUser())
