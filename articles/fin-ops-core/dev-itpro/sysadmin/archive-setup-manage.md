---
title: Set up and manage archive data in Dynamics 365 Finance (preview)
description: This article describes how to set up and manage archive data in Microsoft Dynamics 365 Finance. 
author: pnghub
ms.author: gned
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 2/06/2024
ms.custom:

---
# Set up and manage archive data in Dynamics 365 Finance (preview)

[!INCLUDE [preview-banner](../../../supply-chain/includes/preview-banner.md)]

This article describes how to set up and manage archive data in Microsoft Dynamics 365 Finance.

## Prepare the environment

To prepare your environment to archive data, follow these steps.

1. Refresh your PROD data in your sandbox instance to align it with your production instance.
1. Ensure that your sandbox instance is on the latest version of Finance version 10.0.39. Be sure to apply the latest quality updates for Finance version 10.0.39.
1. Enable license configuration for SQL row version change tracking:

    1. In Microsoft Dynamics Lifecycle Services, select the environment, and then select **Maintain** \> **Enable Maintenance Mode**.
    1. Sign in to Finance, and go to **System administrator** \> **Setup** \> **License configuration**. Select the **SQL row version change tracking** checkbox, and then select **Save**.
    1. In Lifecycle Services, select the environment, and then select **Maintain** \> **Disable Maintenance Mode**.  

> [!NOTE]
> If the Microsoft Power Platform environment isn't set up for the sandbox instance, complete the setup in Lifecyle Services.

## Set up Dynamics 365 Finance and Operations to archive data with Dataverse long-term retention

To archive data, follow these steps to confirm that the Dataverse archive add-in can be installed.

1. In [Power Platform admin center](https://admin.powerplatform.microsoft.com/resources/applications), go to **Environments**, select the environment, and then select **Dynamics 365 apps**.
1. Update the **Finance and operations virtual entity** app if the status is **Update available**.
> [!Note]
> Known issue - If msft_DataArchivalBaseComponents version is below 1.0.0.178 then download the corresponding component as per Dynamics 365 CE version below. This is required because Dynamics 365 CE is native to Dataverse and Dynamics 365 Finance and Operations data archival feature leverages Dataverse.

| Dynamics 365 CE Version | msft_DataArchivalBaseComponent |
|---|---|
| 9.2.23121.00190 | . |
| 9.2.23122.00186 | . |
| 9.2.23123.00210 | . |
  
1. If the **Dynamics 365 finance and operations platform tools** app isn't installed in Power Platform admin center for the selected environment, install it.
2. Install Dynamics 365 Archive with Dataverse Long Term Retention - From the Power Platform admin center, Click on Install App and search for Dynamics 365 Archive with Dataverse Long Term Retention (Preview). Select and click install. If you already have the app installed, you should install the latest update.



## Enable Synapse link profile creation in the Power Apps maker portal

1. In Notepad, create a URL that has the following format: `https://make.preview.powerapps.com/environments/@@DATAVERSER_ENV_ID@@/exporttodatalake?athena.mdl=true`. Replace `@@DATAVERSER_ENV_ID@@` with the globally unique identifier (GUID) of the environment. You can find this value in the **Environment ID** field under **Power platform environment information** on the **Environment details** page in Lifecycle Services.
1. Open the URL in a new browser window.
1. Search for **Bientity**, select the entities that appear in the list, and then select **Save**. Refer to the table list, and select the correct entities in the **Dataverse managed data lake** column for each functional scenario that you plan to archive.

> [!NOTE]
> Don't select all tables. Otherwise, data from all the live application tables is synced to tables in the Dataverse-managed Azure data lake.

## Enable the archival service and update entities feature

1. In Dynamics 365 Finance and Operations, go to **Feature management**.
1. Select the **Archive with Dataverse long term retention** feature for overall archival service integration. This will enable all supported Dynamics 365 Finance and Operations functional scenarios for archiving with Dataverse long-term retention.

## Archive with Dataverse long term retention workspace

The **Archive with Dataverse long term retention** workspace (archival workspace) should be available in the **Workspaces** list in Finance.

### View archive job progress

The dashboard in the Dynamicsw 365 Finance and Operations archival workspace provides the following details about the archival process as it progresses through its various stages.

The **Job status** column that's visible for each archive scenario captures the overall status of the archive job, as mentioned later.

| Job status | Description |
|---|---|
| Scheduled | A job has been scheduled, but it isn't being processed yet. Details about the scheduled date and time are available on the dashboard. |
| In progress | The end-to-end archival process is in progress. Some of the interim stages in the archival process might be completed. |
| Complete | All stages of the archival process have been completed. |
| Failed | The archive process failed. |

You can view the detailed progress log for each archive job by selecting **View progress** \> **View detailed logs**.

> [!NOTE]
> The "In progress" prefix indicates that the end-to-end archival process is ongoing, even if individual stages are completed.

### View information in the archival workspace

| Information | Description |
|---|---|
| Initiating long term retention | The long-term retention job has been activated. |
| Initial sync for \<*tablename*\> in progress \[x of y records synced\] |Initial synchronization to the Dataverse-managed data lake is in progress. |
| Initial sync for \<*tablename*\> completed | Initial synchronization to the Dataverse-managed data lake has been completed. |
| Retention in progress \[x of y records of \<*tablename*\> marked\] | The process is marking records in the finance and operations live application table for archiving, and the equivalent records in the Dataverse-managed data lake are being updated as long-term-retained. |
| Reconciliation in progress | <p>Reconciliation is in progress to verify that the records that are marked as retained in Dataverse long-term retention match the records that are marked for archiving in the finance and operations live application tables.</p><p><strong>Note:</strong> The reconciliation process runs for all finance and operations entities, not just the entities that are related to the archival scenario.</p> |
| Reconciliation completed | Reconciliation for all finance and operations entities has been completed. |
| Pending move to history | The move to history process is waiting to begin. |
| Initiating move to history | The move to history process has been activated. |
| Staging data for move to history in progress | Data is in the staging/queueing process for the move to history. |
| Staging data for move to history completed | Staging/queueing has been completed. |
| Move to history in progress \[x of y records of \<*tablename*\> moved\] | Data is being moved from live tables to history tables. |
| Completed archival of table \<*tablename*\> | The move to history process has been completed for the specified table. |
| The archive job is complete | The end-to-end archival process has been completed for **all** tables. |
