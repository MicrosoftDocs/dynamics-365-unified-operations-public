---
title: Error management and alert notifications
description: Learn error logs and alert notifications that can help you troubleshoot issues, including an overview of consolidated error management.
author: nhelgren
ms.author: nhelgren
ms.topic: article
ms.custom: 
  - bap-template
ms.date: 04/03/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2020-03-20
ms.dyn365.ops.version: AX 7.0.0
ms.custom: sfi-image-nochange
---

# Error management and alert notifications

[!include [banner](../../includes/banner.md)]

Microsoft invested significant time and effort into making dual-write resilient to errors. However, if you encounter an issue while or after you enable table maps for dual-write, select specific table maps to get a consolidated view of all the activities and errors for them. This consolidated view includes error logs. The goal is to help you during troubleshooting by providing a single view of the activities for a table map.

## Consolidated error management

The activity log provides a chronological list of events that a specific table map goes through from the **Not Running** status to the **Running** status. For example, the list can include mappings that are created, updates of column mappings, and mappings that are run. Additionally, if errors occur, you can download the logs to get the next level of details.

:::image type="content" source="media/activity-log.png" alt-text="Screenshot of the activity log.":::

## Re-running execution for initial sync

If you encounter issues while you copy pre-existing data between finance and operations apps and Dataverse, the **Initial sync details** tab provides a count of the errors. 

:::image type="content" source="media/Initial-sync-rerun-1.png" alt-text="Screenshot of the initial sync error.":::

Selecting the individual project shows you the direction in which the sync failed (finance and operations app to Dataverse or vice versa) and details of why it failed. You can choose to fix the underlying issues and then select **Re-run execution** which retries the entire execution, along with the records that failed or errored out in the last sync. When this operation finishes, initial sync is completed and the table returns to the **Running** state. There might be cases where you want to ignore the errors and add new incremental data. In these cases, select **Rerun execution without errors**, which lets you add new data and not retry the errored records. 

:::image type="content" source="media/Initial-sync-rerun-3.png" alt-text="Screenshot of the initial sync retry with errors.":::

When the operation finishes, the status is marked **Completed** and then you can change the table to the **Running** state. 

:::image type="content" source="media/Initial-sync-rerun-4.png" alt-text="Screenshot of the initial sync retry without errors.":::

## Catch-up errors from pausing a table map

When you [resume a table map after pausing](pause-for-maintenance.md), some records might error out and fail to write due to various reasons, including business validations on the destination app. In these cases, the records stay in the queue and you can view them under the **Catch-up errors** tab.

:::image type="content" source="media/Queued-Insights-retry-selected3.png" alt-text="Screenshot of queued records retry selected.":::

The detailed error message helps you fix the underlying issue. After you fix the issue, you can **Retry selected** records or **Retry All** records. When the retry is successful, **Retry status** is marked as **Completed**.

:::image type="content" source="media/Queued-Insights-retry-selected4.png" alt-text="Screenshot of queued records completed.":::

> [!NOTE]
> The queue holds errored records for one day. After that time, the system purges them. In some cases, you might no longer need these records and you can delete them from the queue.

## Alert notifications

As an admin, you can create one or more alert settings to handle cases of planned or unplanned maintenance. For example, you can set up the dual-write system to notify you by email if a specific error threshold is reached because of, for example, network errors. The dual-write system can also take action on your behalf. For example, it can pause or stop dual-write.

The following illustration shows an example where dual-write pauses if 10 errors of the **Application error** type occur within 15 minutes.

:::image type="content" source="media/create-alert-settings.png" alt-text="Screenshot of creating one or more alert settings.":::

By selecting **Create alert settings**, you can create more alerts. You can also select whether notifications should be sent to an individual or a group, and whether the dual-write system should take any action on your behalf. To send alerts to a group, enter the values separated by commas, for example, "id1@contoso.com, id2@contoso.com".

:::image type="content" source="media/create-alert-notification.png" alt-text="Screenshot of creating alerts and sending notifications.":::

> [!NOTE]
> To make your alerts take effect, you need to restart your table maps.

This feature is especially useful if there's unplanned maintenance. For example, one of the apps becomes unavailable and, based on your defined thresholds, dual-write goes into a paused state where all new requests are queued (that is, they aren't lost). After you fix the underlying issue, and both apps are running smoothly, you can resume from the paused state. The updates are then read back from the queue and written to the recovered app.

## Next steps

[Application lifecycle management](app-lifecycle-management.md)


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
