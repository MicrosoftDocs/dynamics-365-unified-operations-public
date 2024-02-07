---
title: Archive inventory transaction data in Dynamics 365 Supply chain (preview)
description: This article explains how to archiveinventory transaction data in Dynamics 365 Supply chain.
author: pnghub
ms.author: gned
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 2/06/2024
ms.custom:

---
# Archive inventory transaction data in Dynamics 365 Supply chain (preview)

[!INCLUDE [preview-banner](../../../supply-chain/includes/preview-banner.md)]

This article explains how archive data with Dataverse long term retention for Inventory Transactions.  


Archive inventory transactions - Supply Chain Management | Dynamics 365 | Microsoft Learn consolidates and compress the inventory transactions table (InventTrans) and archives the original records into
InventTransArchive table. This feature remissions the data volume issue of table InventTrans and improve the system performance. 

New feature Archive with Dataverse long term retention is released to move the records of InventTransArchive to data lake and replicate corresponding records to InventTransArchiveHistory in Dynamics 365 Supply 
Chain Management for performance optimization. 

## Prerequisites 
 - Inventory transactions archive feature has been turned on.
 - Inventory transactions have been archived from InventTrans table to InventTransArchive table. 

### Install solution in your Power platform 
Refer to Setup and Management  
Hold -> D365 Finance and Operations - Archival with DV LTR.docx (sharepoint.com) 

### Turn on the features in your Dynamics 365 Supply Chain Management 

If your system doesn't already include the features that is described in this article, go to Feature management, and turn on the Inventory transactions archive and Archive with Dataverse long term rentention 
feature.  
 - Inventory transactions archive: Archive inventory transaction from InventTrans to InventTransArchive. (https://learn.microsoft.com/en-us/dynamics365/supply-chain/inventory/archive-inventory-transactions)
 - Archive with Dataverse long term retention: Move the archived inventory transaction from InventTransArchive table to dataverse managed data lake and replicate data to InventTransArchiveHistory table.

Things to consider before you purge inventory transactions 

The “Reverse” function of Inventory transactions archive feature is not available to those purged inventory transaction records. 

Un-purge activity is not available from Dataverse managed data lake to Dynamics 365 Supply Chain Management. 

## Archive inventory transactions before purge 

Archive inventory transactions - Supply Chain Management | Dynamics 365 | Microsoft Learn 

### Schedule long term retention job 

To move InventTransArchive records to data verse managed data lake, follow these steps: 
1. Go to Workspaces > Archive with Dataverse long term retention > Inventory transactions.
2. A page appears and shows a list of long term retention jobs.
3. Click “New long term retention job” and jump to the wizard of long term retention job creation.
4. Input job name and click “Next”.
5. Select the period which has been processed by Inventory transactions archive and click “Next”.
6. Determine the start date and time of long term retention job and click “Next”
7. Review the job details and create long term retention job. 

You receive a message that states that your long term retention job has been created. The archived records will be purged on the scheduled date. 

### View long term retention job status 

To view long term retention job results, follow these steps: 
1. Go to Workspaces > Archive > Inventory transactions.
2. A page appears and shows a list of long term retention jobs.
3. Select the job with “Job status” is “Completed”.
4. Click the link under “Results”.
5. You can view the “Inventory transactions archive progress”.
6. Click “View detailed logs”. 
You can view the detail of “Archive job message log” which describes the detail steps of long term retention job. 

### View historical data 

When long term retention job move archived inventory transaction from InventTransArchive table to dataverse managed data lake, the same data is replicated to InventTransArchiveHistory table. To view the 
historical data in table InventTransArchiveHistory, follow these steps: 
1. Go to Workspaces > Archive > Inventory transactions.
2. A page appears and shows a list of long term retention jobs.
3. Select the job with “Job status” is “Completed”.
4. Click “View historical data”.
5. You can view the data in table InventTransArchiveHistory. 


 

 

 

 

 
