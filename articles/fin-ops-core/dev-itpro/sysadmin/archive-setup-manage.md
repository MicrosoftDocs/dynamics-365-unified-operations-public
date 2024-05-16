---
title: Set up and manage archive data in Dynamics 365 Finance (preview)
description: Learn about how to set up and manage archive data in Microsoft Dynamics 365 Finance, including an overview on preparing environments.
author: pnghub
ms.author: gned
ms.topic: conceptual
ms.date: 04/29/2024
ms.custom:
ms.reviewer: johnmichalak
---
# Set up and manage archive data in Dynamics 365 Finance (preview)

[!INCLUDE [preview-banner](../../../supply-chain/includes/preview-banner.md)]

This article describes how to set up and manage archive data in Microsoft Dynamics 365 Finance.

## Prepare the environment

To prepare your environment to archive data, follow these steps.

1. To align it with your production instance, refresh your PROD data in your sandbox instance.
2. Ensure that your sandbox instance is on the latest version of Dynamics 365 Finance version 10.0.39 or later. Be sure to apply the latest quality updates for the version.
3. Under license configuration, ensure that **SQL row version change tracking** is enabled. If it isn't enabled, follow these steps:

    1. In Microsoft Dynamics Lifecycle Services, select the environment, and go to **Maintain** \> **Enable Maintenance Mode**.
    2. Sign in to Finance, and go to **System administrator** \> **Setup** \> **License configuration**. Select the **SQL row version change tracking** checkbox, and then select **Save**.
    3. In Lifecycle Services, select the environment, and then select **Maintain** \> **Disable Maintenance Mode**.

> [!NOTE]
> If the Microsoft Power Platform environment isn't set up for the sandbox instance, complete the setup in Lifecyle Services.

## Set up Finance to archive data with Dataverse long-term retention

To archive data, follow these steps to confirm that the Dataverse archive add-in can be installed.

1. In [Power Platform admin center](https://admin.powerplatform.microsoft.com/resources/applications), go to **Environments**, select the environment, and then select **Dynamics 365 apps**. Ensure that the Power Platform environment is a [Managed Environment](/power-platform/admin/managed-environment-overview).
2. Update the **Finance and operations virtual entity** app if the status is **Update available**.
3. If the **Dynamics 365 finance and operations platform tools** app isn't installed in Power Platform admin center for the selected environment, install it.
4. Install **Dynamics 365 Archive with Dataverse long term retention** from the Power Platform admin center.
5. Select **Install App**.
6. Search for and select **Dynamics 365 Archive with Dataverse long term retention (Preview)**.
7. Select **Install**. If you already have the app installed, you should install the latest update.

### Enable finance and operations data archival with Dataverse long-term retention

1. In Finance, go to **Feature management**.
2. Select the **Archive with Dataverse long term retention** feature for overall archival service integration. This feature enables all supported Finance functional scenarios for archiving with Dataverse long-term retention.

The **Archive with Dataverse long term retention** workspace should now be available in the **Workspaces** list in Finance.

### Schedule an archive job

> [!NOTE]
> Before you schedule an archive job, check for custom fields in archive tables by running the [validate archive table schema script](https://github.com/MicrosoftDocs/D365FnOArchiveWithDataverseLongTermRetention/tree/main/Finance%20and%20Operations/SQL%20Scripts). If custom fields are found, follow the instructions in [Archive customization](archive-custom.md) to include those fields in the data archive.

- You can schedule Finance archive jobs from the archive workspace for supported functional scenarios by using the new long-term retention job wizard. 
- While you can schedule a time during which you would like the job to run in order to minimize impact on other database operations, only the move to history process runs during the scheduled window. The other asynchronous archive processes for Dataverse long term retention occur continuously even outside of the scheduled duration.
- Only one archive job across all scenarios runs at any given time. The scheduled job starts to run only after the previous archive job is completed.

> [!IMPORTANT]
> **Known issue:** When you submit a new archive job for the first time, you might receive this error message: "An error occurred while accessing the archive service. Please check your archive service installation."
>
> **Workaround:** Wait 15 minutes, and then resubmit the archive job.

## View archive job progress

The Finance archive workspace provides the following details about the archival process as it progresses through its various stages.

The **Job status** column that's visible for each archive scenario captures the overall status of the archive job.

| Job status | Description |
|---|---|
| **Scheduled** | A job is scheduled, but it isn't being processed yet. Details about the scheduled date and time are available on the dashboard. |
| **In progress** | The archive job is in progress. Some of the interim stages in the archive job might be completed. |
| **Complete** | All stages of the archive job are complete. |
| **Failed** | The archive job failed. |

You can view the detailed progress log for each archive job by selecting **View progress** \> **View detailed logs**.

> [!NOTE]
> The **In progress** status indicates that the end-to-end archival process is ongoing, even if individual stages are completed.

### View information in the Finance archive workspace

| Information | Description |
|---|---|
| Initiating long term retention | The long-term retention job is activated. |
| Initial sync for \<*tablename*\> in progress \[x of y records synced\] |Initial synchronization to the Dataverse long term retention is in progress. |
| Initial sync for \<*tablename*\> completed | Initial synchronization to the Dataverse long term retention is completed. |
| Marking in progress \[x of y records of \<*tablename*\> marked\] | The process is marking records in the finance and operations live application table for archiving, and the equivalent records in the Dataverse long term retention are being updated as retained. |
| Reconciliation in progress | <p>Reconciliation is in progress to verify that the records that are marked as retained in Dataverse long term retention match the records that are marked for archiving in the finance and operations live application tables.|
| Reconciliation completed | Reconciliation for all finance entities is completed. |
| Pending move to history | The move to history process is waiting to begin. |
| Initiating move to history | The move to history process is activated. |
| Staging data for move to history in progress \[x of y records of \<*tablename*\> staged\]| Data is in the staging/queueing process for the move to history. |
| Staging data for move to history completed for \<*tablename*\> | Staging/queueing completed. |
| Staging data for move to history completed for all tables | Staging/queueing completed. |
| Move to history in progress \[x of y records of \<*tablename*\> moved\] | Data is being moved from live tables to history tables. |
| Completed archival of table \<*tablename*\> | The move to history process completed for the specified table. |
| The archive job is complete | The end-to-end archival process completed for all tables in the functional scenario. |
