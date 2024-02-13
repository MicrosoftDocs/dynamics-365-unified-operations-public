---
title: Set up and manage archive data in Dynamics 365 Finance (preview) 
description: This article describes how to set up and manage archive data in Dynamics 365 Finance.
author: pnghub
ms.author: gned
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 2/06/2024
ms.custom:

---
# Set up and manage archive data in Dynamics 365 Finance (preview) 

[!INCLUDE [preview-banner](../../../supply-chain/includes/preview-banner.md)]

This article describes how to set up and manage archive data in Dynamics 365 Finance.

## Prepare the environment 

To prepare your environment to archive data, follow these steps:
1. Refresh your PROD data on your sandbox instance to align it with your production instance.
2. Ensure your sandbox instance is on the latest Dynamics 365 Finance version 10.0.39. Make sure to apply the latest quality updates for Finance version 10.0.39.
3. Enable License configuration for **SQL row version change tracking**. Follow these steps: 
 - In Lifecycle services, select environment. Select **Maintain** > enable **Maintenance mode**.
 - Login to Dynamics 365 Finance. Go to **System administrator** > **Setup** > **License configuration**. Select the **SQL row version change tracking** checkbox. Click **Save**.
 - In Lifecycle services, select environment. Select **Maintain** > exit **Maintenance mode**.  

>[!Note]
>If the Power Platform environment isn't set up for the sandbox instance, complete the setup using LCS. 

### Set up Dynamics 365 Finance to archive data with Dataverse long term retention 

To set up a Dynamics 365 Finance to archive data, follow these steps:
1. Confirm that the Finance archive add-in can be installed. 
 - Go to **Power Platform admin center** > **Environments** > **Selected environment** > **Dynamics 365 apps**.
        - Update the **Finance and operations virtual entity** apps if **Update available**.
 - If the **Dynamics 365 finance and operations platform tools** app isn't installed in Power Platform admin center for the selected environment, install the app.  

### Install archive service package 

To install the archive service package, follow these steps:
1. Install package using this link: [Archive service package](https://appsource.microsoft.com/en-us/product/dynamics-365/mscrm.d365-archiveservice-preview?flightCodes=0538131b166e4600b7ea7a53cc34f6b8).
2. Click **Get it now**. This redirects you to the Power Platform admin center portal. Confirm you are logged in as an administrator.
3. Select the environment and click **Install**. 
 
### Enable Synapse link profile creation in Power apps maker portal  

 - Create a URL using Notepad. Open it in a new browser window: =>  https://make.preview.powerapps.com/environments/@@DATAVERSER_ENV_ID@@/exporttodatalake?athena.mdl=true 
Value of @@DATAVERSER_ENV_ID@@ = the GUID in LCS Environment details page -> POWER PLATFORM ENVIRONMENT INFORMATION-> ENVIRONMENT ID  

 - Search **Bientity** and select entities that appear in the list and **Save**. Refer to the table list and select the right entities under the **Dataverse managed data lake** column for each functional scenario that you plan to archive.  

Don't select all tables to avoid synching data from all the live application tables to Dataverse managed data lake tables. 

### Enable Archival service and update entities feature 

To enable the archive feature, follow these steps:
1. In Dynamics 365 Finance, go to **Feature management**.
2. Select the **Archive with Dataverse long term retention** feature for overall archival service integration. This enables Dynamics 365 Finance functional scenarios available for archiving with Dataverse long term retention. 

### Archive with Dataverse long term retention workspace  
The **Archive with Dataverse long term retention** workspace should be visible under in the **Workspaces** list in Dynamics 365 Finance. 

### View archive job progress  
The dashboard in Dynamics 365 Finance archival workspace provides the below details on the archival process:  

The job status column visible for each archive scenario captures the overall status of the archive job as mentioned below 

|Job Status|Description |
|---------|-------------|
|Scheduled |A job has been scheduled but it's not processing. Details on scheduled date and time are available in the dashboard. |
|In progress |The end-to-end archival process is in progress. Some of the interim stages in the archival process might be complete. |
|Complete |All stages of the archival process are complete. |
|Failed |The archive process failed. |

The dashboard in the Dynamics 365 Finance archival workspace provides details on the archival process as it progresses though its various stages. You can view the detailed progress log for each individual archive job by clicking **View progress** > **View detailed logs**. 

>[!Note]
> The **In-progress** prefix indicates the end-to-end archival process is ongoing even if individual stages are complete.  

### Archive with Dataverse long term retention workspace  
The **Archive with Dataverse long term retention** workspace should be visible under in the **Workspaces** list in Dynamics 365 Finance. 


|Information |Description |
|-------|--------|
|Initiating long term retention |Long term retention job has been activated |
|Initial sync for <tablename> in progress [x of y records synced] |Initial sync to Dataverse managed data lake is in progress |
|Initial sync for <tablename> completed |Initial sync to Dataverse managed data lake is completed |
|Retention in progress [x of y records of <tablename> marked |The process is marking records in the Finance and Operations live application table for archival, and the equivalent records in Dataverse managed data lake are being updated as long term retained.   |
|Reconciliation in progress |Reconciliation in progress to verify that the records marked as retained in Dataverse long term retention match the records marked for archival in the Finance and Operations live application tables.    Note: The reconciliation process runs for all FNO entities and not just the entities related to the archive scenario.  |
|Reconciliation completed |Reconciliation for all FnO entities has been completed |
|Pending move to history |Awaiting move to history process to begin |
|Initiating move to history |Move to history process has been activated |
|Staging data for move to history in progress |Data is in the staging/queueing process for moving to history. |
|Staging data for move to history completed |Staging/queueing has been completed |
|Move to history in progress [x of y records of <tablename> moved |Data is being moved from live to history tables |
|Completed archival of table <tablename> |The move to history process is complete for the mentioned table |
|The archive job is complete |The end-to-end archival process for ALL tables is completed |



 

 
