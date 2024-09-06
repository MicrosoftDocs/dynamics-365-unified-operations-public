---
title: Archive Dynamics 365 Supply Chain Management Inventory related documents 
description: Learn about how to archive Microsoft Dynamics 365 Supply Chain Management Inventory related documents 
author: pnghub
ms.author: gned
ms.topic: conceptual
ms.date: 9/06/2024
ms.custom:
ms.reviewer: twheeloc
---
# Archive Dynamics 365 Supply Chain Management Inventory related documents 

This article explains how to archive Microsoft Dynamics 365 Supply Chain Management Inventory related documents. 

 - Inventory transactions originator 
For the removed inventory transactions, corresponding inventory transactions originator are removed from `InventTransOrigin` to `InventTransOriginHistory` by a scheduled job. 

## Prerequisites 

Before you can use this feature, you must enable it for your system.

### Turn on the feature in Dynamics 365 Supply Chain Management 

To enable the archive feature in feature management, follow these steps:
1. In Dynamics 365 finance and operations apps, go to **Feature management**.
2. Select the **Archive with Dataverse long term retention** for overall archival service integration. This feature enables all supported finance and operations functional scenarios for archiving through 
Dataverse long term retention. 

The **Archive with Dataverse long term retention** workspace should now be available in the **Workspaces** list in finance and operations apps. 

### Set up an archival job 

To move inventory journal records to Dataverse long term retention, follow these steps. 

1. Go to **Workspaces** > **Archive with Dataverse long term retention**.
2. Select **Inventory transactions originator**.
3. Select **New long term retention job** to open a wizard to schedule a new Inventory transactions originator archival job with Dataverse long term retention.
4. Enter a name for the job, and select **Next**.
5. Select the legal entity of the inventory transactions originate that need be purged, and select **Next**.
6. Enter the start date and time of the job, and select **Next**.
7. Select **Finish** to schedule the archive job.
8. You receive a message that the long term retention job has been created. 

### View the status of the long term retention job 

To view the results of the long term retention job, follow these steps. 

1. Go to **Workspaces** > **Archive with Dataverse long term retention** > **Inventory transactions originator**.
2. A list of long term retention jobs is displayed.
3. Select the job where **Job status** is **Completed**.
4. Under **Results**, select the link. 

### View historical data from the history table 

When inventory transactions originator is archived by using Dataverse long term retention, the archived data is replicated to a history table in the Dynamics 365 Supply Chain Management database. Users can view 
the archived data by using an inquiry page. 

To view the historical data, follow these steps. 
1. Go to **Workspaces** > **Archive with Dataverse long term retention** > **Inventory transactions originator**.
2. A list of long term retention jobs is displayed. Select the job where **Job status** is **Completed**.
3. Select **View historical data** to view the data in the history table. 

### Capacity reports 

The capacity that's consumed by Inventory transactions originator tables that are archived by using Dataverse long term retention appear under the database storage capacity reports in Platform admin center. The
capacity that's consumed by the live and history tables in the finance and operations tables are available in the Finance section of the Power Platform admin center capacity reports. 

 
