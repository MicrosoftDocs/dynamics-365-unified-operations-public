---
title: View and manage the work exceptions log
description: Learn about the work exceptions log. The system registers work-related errors in the work exceptions log, which lets managers track and diagnose issues related to warehouse workflows.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form: WHSWorkExceptionLog, WHSWorkException, WHSLocationWithWorkException
ms.topic: how-to
ms.date: 1/27/2025
ms.custom: 
  - bap-template
---

# View and manage the work exceptions log

[!include [banner](../includes/banner.md)]

Work exceptions are work-related errors that can occur during warehouse operations (such as discrepancies in inventory or missing goods at a given location). The system registers these exceptions in the work exceptions log, which lets managers track and diagnose issues related to warehouse workflows such as pick or pack procedures.

## Example of how a worker can create a work exception

The Warehouse Management mobile app automatically creates exceptions during some types some workflows in response to certain events. For example, one possible way that a worker can trigger a work exception is by completing the following procedure to perform a short pick (assuming the required work record already exists):

1. Open the Warehouse Management mobile app.
1. Go to **Outbound** \> **Sales Picking**.
1. Enter the **Work ID** and select **OK**.
1. Enter the **Location** and select **OK**.
1. Select **Short Pick**.
1. Specify the following values:
    - The target license plate
    - The quantity picked
    - The reason for the short pick (for example, the item wasn't available at the expected location)
1. Select **OK** and complete the work.

The short pick event generates a work exception for the specified **Location**.

## Configure behaviors for handling each type of work exception

You can configure the way the system should handle each relevant type of work exception. For example, you could set the system to adjust inventory at an affected license plate or allow automatic item reallocation.

To configure these system behaviors, follow these steps.

1. Go to **Warehouse management** \> **Setup** \> **Work** \> **Work exceptions**.
1. Use the buttons on the Action Pane to add, edit, and delete rows as needed. To learn how to use the settings in each column, hover your mouse pointer over the column header to see a tooltip.

    :::image type="content" source="media/work-exceptions-form.png" alt-text="The Work exceptions page." lightbox="media/work-exceptions-form.png":::

## View the work exceptions log

To view the work exceptions log, go to **Warehouse management** \> **Work** \> **Work exceptions log**. You can sort and filter the list using the column headers or by entering a value in the **Filter** field and selecting where to search for it (for example by **Status**).

:::image type="content" source="media/work-exceptions-log-form.png" alt-text="The Work exceptions log page." lightbox="media/work-exceptions-log-form.png":::

Work exceptions can also be shown on other pages, such as the **Outbound work monitoring** workspace (available at **Warehouse management** \> **Workspaces** \> **Outbound work monitoring**), which provides a tile that shows the number of **Locations with open work exceptions**. Select that tile to view and explore full details about the exceptions at each location.

:::image type="content" source="media/outbound-work-monitoring-form.png" alt-text="The Outbound work monitoring page." lightbox="media/outbound-work-monitoring-form.png":::

:::image type="content" source="media/locations-with-open-exceptions-form.png" alt-text="The Locations with open work exceptions page." lightbox="media/locations-with-open-exceptions-form.png":::

## Clean up the work exceptions log

Cleaning out old work exceptions helps make it easier for users to search for locations with open work exceptions and improves the performance of pages that show work exceptions.

The system provides a clean-up batch job to help you delete multiple entries in the work exceptions log once they're resolved or no longer necessary. When you set up the job, you'll set the criteria for selecting which entries should be deleted (for example, according to the status and/or age of each entry). When the job runs, it removes all work exceptions that match the criteria.

> [!NOTE]
> Even after they are resolved, logs are kept in the system until explicitly removed either manually or using a clean-up job.

To clean up the work exceptions log, follow these steps.

1. Go to **Warehouse management** \> **Periodic tasks** \> **Clean up** \> **Clean up work exceptions logs**.
1. In the dialog, expand the **Parameters** FastTab and make the following settings:
    - **The number of days to keep** – Specify the age (in days) of the oldest entries to keep. Entries older than this will be deleted.
    - **Status** – Select the status of the exception logs to delete (*Open* or *Closed*).
    - **Maximum cleanup records count** – Specify the maximum number of records to delete. Setting a limit here can improve system performance by preventing too many records from being deleted in a single operation. (Default is 100,000.)
1. On the **Run in the background** FastTab, set up batch, batch group, scheduling, and alert options as you require, just as you might do for other batch jobs in Supply Chain Management.

When the job finishes execution, the system shows a notification of how many records were removed.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
