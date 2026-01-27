---
title: Set up and manage archive data in finance and operations apps
description: Learn about how to set up and manage archive data in finance and operations apps, including an overview on preparing environments.
author: pnghub
ms.author: johnmichalak
ms.topic: how-to
ms.date: 01/21/2026
ms.custom:
ms.reviewer: johnmichalak
---
# Set up and manage archive data in finance and operations apps

This article describes how to set up and manage archive data in Microsoft Dynamics 365 Finance and operations apps.

## Required privileges

You need the following privileges:

- In Power Platform: 
  - The **System Administrator** and **System Customizer** roles in the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).

    To confirm that you have these privileges, follow these steps:
    
    1. In the Power Platform Admin Center, go to **Environments**.
    1. Select the relevant environment.
    1. In the **Access** section, select users.
    1. Select **Installing user** > **Roles**. Confirm the necessary privileges.

- In Microsoft Dynamics 365 Finance and operations apps:
   - The **System administrator** role in Microsoft Dynamics 365 Finance and operations apps.
    
     To confirm that you have these privileges, follow these steps:
  
     1. In Dynamics 365 Finance and operations apps, go to **System administration**.
     1. Select **Users** > **Users**.
     1. Select **Installing user** > **Roles**. Confirm the necessary permissions.

- In Microsoft Dynamics Lifecycle Services:

  - The **Organization Admin** role to create environments. Additionally, assign the **Project owner** or **Environment manager** role to the user in the **Project security** role field in Lifecycle Services.

## Prepare the environment

To prepare your environment to archive data, follow these steps:

1. Refresh your sandbox instance with PROD data to align it with your production instance.
1. Ensure that your sandbox instance is on the latest version of Dynamics 365 Finance and operations apps version 10.0.39 or later. Apply the latest quality updates for the version.
1. Under license configuration, ensure that **SQL row version change tracking** is enabled. If it's not enabled, follow these steps:

    1. In Microsoft Dynamics Lifecycle Services, select the environment, and go to **Maintain** \> **Enable Maintenance Mode**.
    1. Sign in to Finance and operations apps, and go to **System administrator** \> **Setup** \> **License configuration**. Select the **SQL row version change tracking** checkbox, and then select **Save**.
    1. In Lifecycle Services, select the environment, and then select **Maintain** \> **Disable Maintenance Mode**.

> [!NOTE]
> If the Microsoft Power Platform environment isn't set up for the sandbox instance, complete the setup in Lifecycle Services.

## Set up Finance and operations apps to archive data with Dataverse long-term retention

To archive data, follow these steps to confirm that the Dataverse archive add-in can be installed.

1. In [Power Platform admin center](https://admin.powerplatform.microsoft.com/resources/applications), go to **Environments**, select the environment, and then select **Dynamics 365 apps**. Ensure that the Power Platform environment is a [Managed Environment](/power-platform/admin/managed-environment-overview).
1. Update the **Finance and operations virtual entity** app if the status is **Update available**.
1. If the **Dynamics 365 finance and operations platform tools** app isn't installed in Power Platform admin center for the selected environment, install it.
1. Install **Dynamics 365 Archive with Dataverse long term retention** from the Power Platform admin center.
1. If you already have the app installed, install the latest update.

### Enable finance and operations data archival by using Dataverse long-term retention

1. In Finance and operations apps, go to **Feature management**.
1. Select the **Archive with Dataverse long term retention** feature for overall archival service integration. This feature enables all supported Finance functional scenarios for archiving by using Dataverse long-term retention.

The **Archive with Dataverse long term retention** workspace is now available in the **Workspaces** list in Finance and operations apps.

### Schedule an archive job

> [!NOTE]
> Before you schedule an archive job, check for custom fields in archive tables by running the [validate archive table schema script](https://github.com/MicrosoftDocs/D365FnOArchiveWithDataverseLongTermRetention/tree/main/Finance%20and%20Operations/SQL%20Scripts). If custom fields are found, follow the instructions in [Archive customization](archive-custom.md) to include those fields in the data archive.

- You can schedule Finance and operations apps archive jobs from the archive workspace for supported functional scenarios by using the new long-term retention job wizard. 
- While you can schedule a time during which you want the job to run to minimize impact on other database operations, only the move to history process runs during the scheduled window. The other asynchronous archive processes for Dataverse long term retention occur continuously even outside of the scheduled duration.
- Only one archive job across all scenarios runs at any given time. The scheduled job starts to run only after the previous archive job is completed.

> [!IMPORTANT]
> **Known issue:** When you submit a new archive job for the first time, you might receive this error message: "An error occurred while accessing the archive service. Check your archive service installation."
>
> **Workaround:** Wait 15 minutes, and then resubmit the archive job.

## View archive job progress

The Finance and operations apps archive workspace provides the following details about the archival process as it progresses through its various stages.

The **Job status** column that's visible for each archive scenario captures the overall status of the archive job.

| Job status | Description |
|---|---|
| **Scheduled** | A job is scheduled, but the process hasn't started yet. The dashboard shows the scheduled date and time. |
| **In progress** | The archive job is in progress. Some of the interim stages in the archive job might be completed. |
| **Complete** | All stages of the archive job are complete. |
| **Failed** | The archive job failed. |

You can view the detailed progress log for each archive job by selecting **View progress** \> **View detailed logs**.

> [!NOTE]
> The **In progress** status indicates that the end-to-end archival process is ongoing, even if individual stages are completed.

### View information in the Finance and operations apps archive workspace

| Information | Description |
|---|---|
| Initiating long term retention | The process activates the long-term retention job. |
| Initial sync for \<*tablename*\> in progress \[x of y records synced\] |The process starts the initial synchronization to the Dataverse long term retention. |
| Initial sync for \<*tablename*\> completed | The process finishes the initial synchronization to the Dataverse long term retention. |
| Retention in progress \[x of y records of \<*tablename*\> marked\] | The process marks records in the finance and operations live application table for archiving, and updates the equivalent records in the Dataverse long term retention as retained. |
| Reconciliation in progress | <p>Reconciliation is in progress to verify that the records that are marked as retained in Dataverse long term retention match the records that are marked for archiving in the finance and operations live application tables.|
| Reconciliation completed | Reconciliation for all finance entities is completed. |
| Pending move to history | The move to history process is waiting to begin. |
| Initiating move to history | The process activates the move to history. |
| Staging data for move to history in progress \[x of y records of \<*tablename*\> staged\]| Data is in the staging or queueing process for the move to history. |
| Staging data for move to history completed for \<*tablename*\> | Staging or queueing completed for the specified table. |
| Staging data for move to history completed for all tables | Staging or queueing completed. |
| Move to history in progress \[x of y records of \<*tablename*\> moved\] | Data is being moved from live tables to history tables. |
| Completed archival of table \<*tablename*\> | The move to history process completed for the specified table. |
| The archive job is complete | The end-to-end archival process completed for all tables in the functional scenario. |
