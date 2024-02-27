---
title: Automatic rewaving of nonallocated shipment lines
description: This article provides information about automatic rewaving of nonallocated shipment lines. This feature automatically creates work orders for failed shipments. Therefore, those work orders don't have to be manually monitored and created.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 02/27/2024
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Automatic rewaving of nonallocated shipment lines

[!include [banner](../includes/banner.md)]

Automatic rewaving of nonallocated shipment lines automatically creates work orders for failed shipments. Therefore, those work orders don't have to be manually monitored and created.

Use of this feature requires only that warehouse administrators schedule the *Auto add shipments to wave* job to run as often as it's required. Each time that the job runs, it checks for uncompleted work that can be automatically rewaved. This feature boosts operational efficiency by reducing downtime and initiating work that could not previously be completed.

This feature is particularly beneficial for high-volume businesses, where it can significantly enhance operational speed and efficiency. Here are some examples:

- A retailer can support continuous packing and shipping operations, even during inventory shortages.
- In high-velocity sales and production environments, goods can be sold before they reach the storage facility from the production line.

## Standard wave workflow

The wave management process involves three key steps:

1. **Create a wave.** Group work orders, based on criteria such as the shipment date, priority, or item type, and add the group to a wave.
1. **Process the wave.** Pick items from inventory, pack them, and prepare them for shipment.
1. **Release the wave.** Ship the packed items to customers.

## Rewaving workflow

The rewaving workflow ensures continuous, uninterrupted warehouse operations, even when a shipment fails. It ends the need for manual monitoring of failed shipments and enables work to be automatically created and added to each wave. It proceeds in the following way:

1. **A shipment fails while a wave is being processed.** In this situation, the system removes the failed shipment from the wave and continues to process the rest of the wave. A failed shipment can occur if, for example, you don't have enough inventory at a particular picking location.
1. **Create a work placeholder for the failed shipment.** The system creates a placeholder for the work that's required to process the failed shipment. It stores this placeholder in the *WHS Wave Processing Removed Shipment* table. (If this feature isn't used, a user must manually identify failed shipments and then create new work for them.)
1. **Replenish inventory.** Inventory at the picking location is replenished according to standard warehouse operations. That inventory then becomes available for shipment in the next wave.
1. **Automatically rewave.** At the next scheduled run of the *Auto add shipments to wave* batch job, the system checks for previously failed shipments and creates work for them.
1. **Add work to the next wave.** The *Auto add shipments to wave* batch job adds the newly created work to the next wave for processing.
1. **Control and remove placeholders for completed shipments.** The *Auto add shipments to wave* batch job ends by checking the *Wave Processing Removed Shipment* table for records that were successfully processed (that is, their status is no longer *Open*) and that the *Shipment* table includes a shipment for. These records indicate shipments that were successfully rewaved. The system cleans up these placeholders by removing them from the table.

## Enable wave processing in batches to allow for rewaving

Before you can use rewaving, your system must be set up to process waves in batch.

1. In the system settings, go to **Warehouse management** \> **Setup** \> **Warehouse management parameters**.
1. On the **General** tab, on the **Wave Processing** FastTab, set the **Process waves in batch** option to *Yes*.
1. On the Action Pane, select **Save** to apply the new configuration.

## Schedule the Auto add shipments to wave batch job

The rewaving process runs as a batch job that you must schedule to run as often as is required for your system. Follow these steps to set up the batch job.

1. Go to **Warehouse Management** \> **Outbound Waves** \> **Auto add shipments to wave**.
1. On the **Run in the background** FastTab, set the following fields:

    - Set the **Batch processing** option to *Yes*.
    - Make a note of the **Task description** value. The default value is *Auto add shipments to wave*, but you can change it. You can use this value to monitor and edit the job on the **Batch jobs** page.

1. Select the **Recurrence** link.
1. Use the fields that are provided to set up a schedule that defines how often the rewaving job runs, and how long it runs for.
1. Select **OK** to save your schedule for the job.
1. Select **OK** to create the job.

## Monitor the rewave process

To monitor the status of all batch jobs, adjust their schedules, and fix any issues that arise, follow these steps.

1. Go to **System administration** \> **Inquiries** \> **Batch jobs**.
1. Use the **Filter** field to find the relevant jobs, based on the value that you entered in the **Task description** field when you set up the job. (On this page, the field is named **Job description**.) The default description for this type of job is *Auto add shipments to wave*.
1. View basic status information about the job in the grid.
1. Select the **Job ID** value to view more details about the job. From the details, you can edit the job's status, change its recurrence schedule, set alerts, and more.

## Unsupported processes

The rewaving feature doesn't support the following processes:

- Automatic work creation for inventory that's stored in locations that aren't configured for wave processing
- Continuous checks on inventory levels
