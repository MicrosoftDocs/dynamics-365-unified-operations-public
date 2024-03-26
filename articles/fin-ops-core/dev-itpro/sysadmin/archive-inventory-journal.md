---
title: Archive inventory journal data in Dynamics 365 Supply Chain Management (preview)
description: This article explains how to archive data for inventory journal with Dataverse long term retention. 
author: epodkolz
ms.author: epodkolzina
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 3/20/2024
ms.custom:

---
# Archive inventory journal data in Dynamics 365 Supply Chain Management (preview)

[!INCLUDE [preview-banner](../../../supply-chain/includes/preview-banner.md)]

This article explains how to archive data for inventory journal with Dataverse long term retention. 

## Prerequisites 

The following prerequisites must be met before you archive inventory journal data:
 - The ledger period of inventory journal which need be archived must be closed.
 - The period must be at least one year before the from-period date of the archive. 

## Turn on the features in Supply Chain Management  

If your system doesn't already enable the features, follow these steps:
1. Go to **Feature management**.
2. Enable **Archive with Dataverse long term retention** feature. This feature moves inventory journal to Dataverse long term retention and replicates the data to the history table. 


### Schedule the long term retention job 

To move inventory journal records to the Dataverse long term retention, follow these steps.
1. Go to **Workspaces > Archive with Dataverse long term retention**.
2. Select **Inventory journal**.
3. Select **New long term retention job** to open a wizard to schedule a new Inventory Journal archival job with Dataverse long-term retention.
4. Enter a name for the job, and then select **Next**.
5. Select the period of inventory journal which needs to be purged, and then select **Next**.
6. Enter the start date and time of the job, and then select **Next**.
7. Select **Finish** to schedule the archive job. 

You receive a message that the long term retention job has been created.   

### View the status of the long term retention job 

To view the results of the long term retention job, follow these steps. 
1. Go to **Workspaces > Archive with Dataverse long term retention > Inventory journal**.
2. A list of long term retention jobs is displayed. Select the job with a **Job status** is **Completed**.
3. Under **Results**, select the link.
4. View the Inventory journal archive progress information.
5. Select **View detailed logs** to view the Archive job message log. This log describes the steps of the long term retention job in detail. 

### View historical data from the history table

When the Inventory journal data is archived with Dataverse long term retention, the archived data is replicated to a history table in the Dynamics 365 Supply Chain database. 
This allows users to view the archived data using an inquiry page. 

To view the historical data, follow these steps. 
1. Go to **Workspaces > Archive with Dataverse long term retention > Inventory journal**.
2. A list of long term retention jobs is shown. Select the job where **Job status** is **Completed**.
3. Select **View historical data** to view the data in the history table. 

###C apacity reports 

The capacity consumed by Inventory journal tables that are archived with Dataverse long term retention appear in the Power Platform admin center, under the database storage capacity reports. The capacity consumed by the live and history tables in the Dynamics 365 Finance and Operations tables are available in the Finance section of the Power Platform admin center capacity reports. 
