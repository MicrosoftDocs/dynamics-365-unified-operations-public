---
title: Automatic rewaving of nonallocated shipment lines
description: Automatic rewaving of nonallocated shipment lines automatically creates work orders for failed shipments, which removes the need to manually monitor and create such work orders.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 02/06/2024
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Automatic rewaving of nonallocated shipment lines

[!include [banner](../includes/banner.md)]

Automatic rewaving of nonallocated shipment lines automatically creates work orders for failed shipments, which removes the need to manually monitor and create such work orders. To use it, warehouse administrators just need to schedule the *Auto add shipments to wave* job to run as often as required. Each time the job runs, it checks for uncompleted work to be rewaved automatically. This feature boosts operational efficiency by reducing downtime and initiating work that wasn't able to be completed previously.

This feature is particularly beneficial for high-volume businesses, where it can significantly enhance operational speed and efficiency. For example:

- A retailer can support continuous packing and shipping operations, even during inventory shortages.
- In high-velocity sales and production environments, this feature allows goods to be sold before they reach the storage facility from the production line.

## The standard wave workflow

The wave management process involves three key steps:

1. **Create a wave**: Group work orders based on criteria such as shipment date, priority, or item type and add the group to a wave.
1. **Process the wave**: Pick items from inventory, pack them, and prepare them for shipment.
1. **Release the wave**: Ship the packed items to customers.

## The rewaving workflow

The rewaving workflow ensures continuous warehouse operations without interruption, even when a shipment fails. It ends the need for manual monitoring of failed shipments and allows work to be created and added to each wave automatically. It proceeds as follows:

1. **Shipment fails while processing a wave:** If this happens, the system removes that shipment from the wave and continues processing the rest of the wave. This could occur, for example, if you don't have enough inventory at a particular picking location.
1. **Create a work placeholder for the failed shipment**: The system creates a placeholder for the work required to process the failed shipment and stores it in the *WHS Wave Processing Removed Shipment* table. (Without this feature, a user would need to manually identify failed shipments and then create new work for them.)
1. **Replenish inventory**: Inventory at the picking location is replenished according to standard warehouse operations, making that inventory available for shipping with the next wave.
1. **Automatically rewave**: On the next scheduled run of the *Auto add shipments to wave* batch job, the system checks for previously failed shipments and creates work for them.
1. **Add work to the next wave**: The *Auto add shipments to wave* batch job adds the newly created work to the next wave for processing.
1. **Control and remove placeholders for completed shipments:** The *Auto add shipments to wave* batch job finishes by checking each record in the *Wave Processing Removed Shipment* table. Each record that has now been processed successfully (whose status is no longer *Open*), and for which a shipment exists in the *Shipment* table, indicates a shipment that has now been rewaved successfully. The system cleans up these placeholders by removing them from the table.

## Enable processing waves in batches to allow rewaving

To use rewaving, your system must be set to process waves in batch. Follow these steps:

1. Go to **Warehouse management** \> **Setup** \> **Warehouse management parameters** in the system settings.
1. Open the **General** tab.
1. On the **Wave Processing** FastTab, set **Process waves in batch** to *Yes*.
1. On the Action Pane, select **Save** to apply the new configuration.

## Schedule Auto add shipments to wave batch job

The rewaving process runs as a batch job that you must schedule to run as often as needed for your system. Follow these steps to set it up:

1. Go to **Warehouse Management** \> **Outbound Waves** \> **Auto add shipments to wave**.
1. On the **Run in the background** FastTab, make the following settings:
    - Set **Batch processing** to *Yes*.
    - Note the **Task description**. The default value is *Auto add shipments to wave*, but you can change it if you like. This value lets you monitor and edit this job on the **Batch jobs** page.

1. On the **Run in the background** FastTab, select the **Recurrence** link.
1. Use the settings provided to set up the schedule for how often to run the rewaving job and for how long.
1. Select **OK** to save your schedule for the job.
1. Select **OK** to create the job.

## Monitor the rewave process

To monitor the status of all batch jobs, adjust their schedules, and solve any issues that may arise, follow these steps:

1. Go to **System administration** \> **Inquiries** \> **Batch jobs**.
1. Use the **Filter** field to find the relevant jobs based on the value you entered for the **Task description** when you set up the job (on this page, it's called the **Job description**). The default description for this type of job is *Auto add shipments to wave*.
1. View basic status information about the job in the grid.
1. Select the **Job ID** value to view more details about the job. From here, you can also edit its status, change its recurrence schedule, set alerts, and more.

## Unsupported processes

The rewaving feature doesn't support the following processes:

- Automatic work creation for inventory stored in locations that aren't configured for wave processing.
- Continuous checks on inventory levels
