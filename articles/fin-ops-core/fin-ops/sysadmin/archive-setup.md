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

### Dashboard  

The dashboard in Dynamics 365 Finance archival workspace provides details on the archival process as it progresses though its various stages.  

>[!Note]
> The **In-progress** prefix indicates the end-to-end archival process is ongoing even if individual stages are complete.  

| Job status  | View details  |   Description |
|---|---|---|  
|Scheduled |Scheduled |Job scheduled to begin at scheduled date and time |
|In progress | In progress – Initial synch  |Initial sync to Dataverse managed data lake in progress x of y records of tablename synced. |
|            |In progress – Initial synch complete| Initial sync to Dataverse managed data lake completed x records of tablename synced. |
|            |In progress – Retention [x of y] |The process is marking records in the Dynamics 365 Finance live application table for archival, and the equivalent records in Dataverse managed data lake are being updated as long term retained. |
|             |In progress – reconciliation |Reconciliation in progress to verify that the records marked as retained in Dataverse long term retention match the records marked for archival in the Dynamics 365 Finance.  |
|            | In progress – Move to history [x of y records] |Archived records from the Dynamics 365 Finance application table are being moved to the Dynamics 365 Finance history tables. |
|Complete |Archival complete – Move to history [x of x records] |The move to the Dynamics 365 Finance history table is complete. |
|Failed |Failed – Move to history failed |The move to history failed. |

### Restore from history table to live table  

The archival workspace dashboard also provides progress details on the restore from the history table to the live table. 

| Job status  | View details  |   Description |
|---|---|---|  
|Scheduled |Scheduled |Job scheduled to begin at scheduled date and time |
|In Progress |In progress – Restored [x of y records] |Restore to live application table in progress |
|Restored |Complete – Restored [x of x records] |Restore to live application table process completed |

>[!Note]
>When data from the history table is restored to the live table, duplicate records are created in the Dataverse long term retention. 

 
