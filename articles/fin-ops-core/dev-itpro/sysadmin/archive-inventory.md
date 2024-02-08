---
title: Archive inventory transaction data in Dynamics 365 Supply chain (preview)
description: This article explains how to archive inventory transaction data in Dynamics 365 Supply chain.
author: pnghub
ms.author: gned
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 2/06/2024
ms.custom:

---
# Archive inventory transaction data in Dynamics 365 Supply chain (preview)

[!INCLUDE [preview-banner](../../../supply-chain/includes/preview-banner.md)]

This article explains how archive data with Dataverse long term retention for inventory transactions.  

Currently, users can consolidate and compress inventory transactions table (InventTrans) and archives the original records into InventTransArchive table. For more information, see [Archive inventory transactions](../../supply-chain/inventory/archive-inventory-transactions). This feature addresses the data volume issue of table InventTrans and improves system performance. 

The new feature **Archive with Dataverse long term retention** moves the InventTransArchive records to a data lake and replicate corresponding records to InventTransArchiveHistory in Dynamics 365 Supply 
Chain Management for performance optimization. 

## Prerequisites 
 - The **Inventory transactions archive** feature is enabled.
 - Inventory transactions are archived from InventTrans table to InventTransArchive table. 

### Turn on the features in Dynamics 365 Supply Chain Management 

If your system doesn't already include the features, follow these steps: 
1. Go to **Feature management**.
2. Enable the **Inventory transactions archive** and **Archive with Dataverse long term retention** features.  
 - **Inventory transactions archive** feature archives inventory transactions from InventTrans to InventTransArchive. 
 - **Archive with Dataverse long term retention** feature moves archived inventory transaction from InventTransArchive table to Dataverse managed data lake and replicates the data to InventTransArchiveHistory table.

### Considerations before purging inventory transactions  
 - The **Reverse** function of the **Inventory transactions archive** feature isn't available for the purged inventory transaction records.
 - Unpurge activity isn't available from Dataverse managed data lake to Dynamics 365 Supply Chain Management. 

### Archive inventory transactions before purge 

For more information about archiving inventory transactions, see [Archive inventory transactions](supply-chain/inventory/archive-inventory-transactions). 

### Schedule long term retention job 

To move InventTransArchive records to Dataverse managed data lake, follow these steps: 
1. Go to **Workspaces** > **Archive with Dataverse long term retention** > **Inventory transactions**.
2. Click **New long term retention job**. The wizard of long term retention job creation is available.
3. Enter a job name and click **Next**.
5. Select the period that has been processed by Inventory transactions archive and click **Next**.
6. Enter the start date and time of long term retention job and click **Next**.
7. Review the job details and create long term retention job. 

You receive a message that the long term retention job is created. The archived records are purged on the scheduled date. 

### View long term retention job status 

To view long term retention job results, follow these steps: 
1. Go to **Workspaces** > **Archive** > **Inventory transactions**.
2. A list of long term retention jobs is displayed.
3. Select the job with **Job status** of **Completed**.
4. Under **Results**, click the link.
5. View the **Inventory transactions archive progress**”.
6. Click **View detailed logs** to view the **Archive job message log** which describes the detail steps of long term retention job. 

### View historical data 

When the long term retention job moves archived inventory transaction from InventTransArchive table to Dataverse managed data lake, the same data is replicated to InventTransArchiveHistory table. 
To view the historical data in table InventTransArchiveHistory, follow these steps: 
1. Go to **Workspaces** > **Archive** > **Inventory transactions**.
2. A list of long term retention jobs will be displayed.
3. Select the job with **Job status** of **Completed**.
4. Click **View historical data** to view the data in table InventTransArchiveHistory. 


 

 

 

 

 
