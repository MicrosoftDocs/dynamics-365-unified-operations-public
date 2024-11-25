---
title: Automatic rewaving of nonallocated shipment lines
description: Learn about automatic rewaving of nonallocated shipment lines. This feature automatically creates work orders for failed shipments.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 04/11/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form: WHSParameters, WHSWaveProcessingRemovedShipment
---

# Automatic rewaving of nonallocated shipment lines

[!include [banner](../includes/banner.md)]

Automatic rewaving of nonallocated shipment lines automatically creates work orders for failed shipment lines. Therefore, those work orders don't have to be manually monitored and created.

Use of this feature requires only that warehouse administrators schedule the *Auto add shipments to wave* job to run as often as it's required. Each time that the job runs, it checks for uncompleted work that can be automatically rewaved. This feature boosts operational efficiency by reducing downtime and initiating work that couldn't previously be completed.

This feature is especially beneficial for high-volume businesses, where it can significantly enhance operational speed and efficiency. Here are some examples:

- A retailer can support continuous packing and shipping operations, even during inventory shortages.
- In high-velocity sales and production environments, goods can be sold before they reach the storage facility from the production line.

The rewaving feature collects shipments lines for inventory that couldn't be allocated during initial wave processing. It adds a **Failed shipment lines** page, where you can review the lines that are ready to be rewaved. A scheduled batch job regularly processes these lines, tries again to allocate inventory for them, and adds the lines to a new wave if inventory is available.

## Prerequisites

Before you can use the features that are described in this article, your system must meet the following requirements:

- To run the *Auto add shipments to wave* batch job, you must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.37 or later.
- To monitor the status of failed shipment lines by using the **Failed shipment lines** page, you must be running Supply Chain Management version 10.0.40 or later.

## Wave and rewaving workflows

### The standard wave workflow

The wave management process involves three key steps:

1. **Create a wave** – Group work orders, based on criteria such as the shipment date, priority, or item type, and add the group to a wave.
1. **Process the wave** – Pick items from inventory, pack them, and prepare them for shipment.
1. **Release the wave** – Ship the packed items to customers.

### The rewaving workflow

The rewaving workflow ensures continuous, uninterrupted warehouse operations, even when a shipment line fails. It ends the need for manual monitoring of failed shipment lines and enables work to be automatically created and added to each wave. It proceeds in the following way:

1. **A shipment line fails while a wave is being processed** – The system removes the failed shipment line from the wave and continues to process the rest of the wave. A failed shipment line can occur if, for example, you don't have enough inventory at a particular picking location.
1. **Create a work placeholder for the failed shipment line** – The system creates a placeholder for the work that's required to process the failed shipment. It stores this placeholder in the *Failed shipment lines* table. (If you aren't using this feature on your system, a user must manually identify failed shipments and then create new work for them.)
1. **Replenish inventory** – Inventory at the picking location is replenished according to standard warehouse operations. That inventory then becomes available for shipment in the next wave.
1. **Automatically rewave** – At the next scheduled run of the *Auto add shipments to wave* batch job, the system checks the *Failed shipment lines* table for previously failed shipments and creates work for them.
1. **Add work to the next wave** – The *Auto add shipments to wave* batch job adds the newly created work to the next wave for processing.
1. **Control and remove placeholders for completed shipment lines** – The *Auto add shipments to wave* batch job ends by checking the *Failed shipment lines* table for records that were successfully processed (that is, their status is no longer *Open*) and that the *Shipment* table includes a shipment for. These records indicate shipment lines that were successfully rewaved. The system cleans up these placeholders by removing them from the table. The system tries to rewave a shipment line up to five times. If a line fails on the fifth attempt, the system stops trying and marks that line as *Failed*.
1. **Cleanup shipment lines that failed rewaving** - The *Wave processing removed shipments cleanup* job runs and removes *Failed* shipment lines from the *Failed shipment lines* table. These shipment lines are removed from the *Failed shipment lines* table according to the configuration of the *Wave processing removed shipments cleanup* job.

To restart the rewaving process from the beginning, you must allow the cleanup job to remove the failed shipment lines that couldn't be rewaved and then manually add them to a new wave. Then, if a shipment line fails again, the rewave process starts over with the retry count reset to zero.

## Enable rewaving for your system

To enable rewaving for your system, you must set up your system to process waves in batches. You must also schedule the *Auto add shipments to wave* batch job.

### Enable wave processing in batches to allow for rewaving

Before you can use rewaving, your system must be set up to process waves in batch.

1. In the system settings, go to **Warehouse management** \> **Setup** \> **Warehouse management parameters**.
1. On the **General** tab, on the **Wave Processing** FastTab, set the **Process waves in batch** option to *Yes*.
1. On the Action Pane, select **Save** to apply the new configuration.

### Schedule the Auto add shipments to wave batch job

The rewaving process runs as a batch job that you must schedule to run as often as is required for your system. Follow these steps to set up the batch job.

1. Go to **Warehouse Management** \> **Outbound Waves** \> **Auto add shipments to wave**.
1. On the **Run in the background** FastTab, set the following fields:

    - Set the **Batch processing** option to *Yes*.
    - Make a note of the **Task description** value. The default value is *Auto add shipments to wave*, but you can change it. You can use this value to monitor and edit the job on the **Batch jobs** page.

1. Select the **Recurrence** link.
1. Use the fields that are provided to set up a schedule that defines how often the rewaving job runs, and how long it runs for.
1. Select **OK** to save your schedule for the job.
1. Select **OK** to create the job.
1. On the **Records to include** FastTab, you can define selection criteria to limit the set of shipment lines that's processed.

    - Select the **Filter** link to open a standard query editor dialog box, where you can add or remove filter criteria.
    - The **Records to include** FastTab lists each field name and value that you added by using the query editor.
    - The **Number of retries** filter is always included, and its value (*5*) is read-only. This setting indicates that the system will try to rewave each failed shipment line up to five times. If a line fails on the fifth attempt, the system stops trying and marks that line as *failed*.

### Schedule the cleanup job

The cleanup job removes failed and old shipment lines from the *Failed shipment lines* table. You must schedule it to run as often as is required for your system. To set it up, follow these steps.

1. Go to **Warehouse Management** \> **Outbound Waves** \> **Wave processing removed shipment cleanup**.
1. On the **Parameters** FastTab, set the following fields:

    - **Cleanup rewave threshold** – Enter the maximum number of retries that the cleanup job allows for a shipping line before it removes that line from the *Failed shipment lines* table. The *Auto add shipments to wave* batch job allows for maximum of five retries, but you can remove shipping lines sooner by entering a lower value here. Values that are more than *5* have no effect.
    - **Last update older than given number** – Enter the maximum number of days that the cleanup job should allow a shipping line to remain in the *Failed shipment lines* table. It removes all shipping lines that are older than this value.

1. On the **Run in the background** FastTab, set the following fields:

    - **Batch processing** – Set this option to *Yes*.
    - **Task description** – The default value is *Wave Processing Removed Shipment*, but you can change it. Make a note of the value. You can use it to monitor and edit the job on the **Batch jobs** page.

1. Select the **Recurrence** link, and use the fields that are provided to set up a schedule that defines how often the cleanup job runs, and how long it runs for.
1. Select **OK** to save your schedule for the job.
1. Select **OK** to create the job.

## Monitor the rewave process

### Monitor failed shipment lines

To monitor shipment lines that must be rewaved, go to **Warehouse Management** \> **Shipments** \> **Failed shipment lines**. For each failed shipment line, the page shows the line ID, the line's current status, the reason for the failure, and the number of times that the system tried to rewave the line.

### Monitor batch job status

To monitor the status of all batch jobs, adjust their schedules, and fix any issues that arise, follow these steps.

1. Go to **System administration** \> **Inquiries** \> **Batch jobs**.
1. Use the **Filter** field to find the relevant jobs, based on the value that you entered in the **Task description** field when you set up the job. (On this page, the field is named **Job description**.) The default description for this type of job is *Auto add shipments to wave*.
1. View basic status information about the job in the grid.
1. Select the **Job ID** value to view more details about the job. From the details, you can edit the job's status, change its recurrence schedule, set alerts, and more.

## Unsupported processes

The rewaving feature doesn't support the following processes:

- Automatic work creation for inventory that's stored in locations that aren't configured for wave processing
- Continuous checks on inventory levels
