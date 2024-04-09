---
title: Automatic rewaving of nonallocated shipment lines
description: This article provides information about automatic rewaving of nonallocated shipment lines. This feature automatically creates work orders for failed shipments. Therefore, those work orders don't have to be manually monitored and created.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 04/05/2024
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Automatic rewaving of nonallocated shipment lines

[!include [banner](../includes/banner.md)]

Automatic rewaving of nonallocated shipment lines automatically creates work orders for failed shipment lines. Therefore, those work orders don't have to be manually monitored and created.

Use of this feature requires only that warehouse administrators schedule the *Auto add shipments to wave* job to run as often as it's required. Each time that the job runs, it checks for uncompleted work that can be automatically rewaved. This feature boosts operational efficiency by reducing downtime and initiating work that couldn't previously be completed.

This feature is especially beneficial for high-volume businesses, where it can significantly enhance operational speed and efficiency. Here are some examples:

- A retailer can support continuous packing and shipping operations, even during inventory shortages.
- In high-velocity sales and production environments, goods can be sold before they reach the storage facility from the production line.

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- To run the *Auto add shipments to wave* batch job, you must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.37 or later.
- To monitor the status of failed shipment lines using the **Failed shipment lines** page, you must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.40 or later.

## Wave and rewaving workflows

### The standard wave workflow

The wave management process involves three key steps:

1. **Create a wave** – Group work orders, based on criteria such as the shipment date, priority, or item type, and add the group to a wave.
1. **Process the wave** – Pick items from inventory, pack them, and prepare them for shipment.
1. **Release the wave** – Ship the packed items to customers.

### The rewaving workflow

The rewaving workflow ensures continuous, uninterrupted warehouse operations, even when a shipment line fails. It ends the need for manual monitoring of failed shipment lines and enables work to be automatically created and added to each wave. It proceeds in the following way:

1. **A shipment line fails while a wave is being processed** – In this situation, the system removes the failed shipment line from the wave and continues to process the rest of the wave. A failed shipment line can occur if, for example, you don't have enough inventory at a particular picking location.
1. **Create a work placeholder for the failed shipment line** – The system creates a placeholder for the work that's required to process the failed shipment. It stores this placeholder in the 'WHSWaveProcessingRemovedShipment' form. (If you aren't using this feature on your system, a user must manually identify failed shipments and then create new work for them.)
1. **Replenish inventory** – Inventory at the picking location is replenished according to standard warehouse operations. That inventory then becomes available for shipment in the next wave.
1. **Automatically rewave** – At the next scheduled run of the *Auto add shipments to wave* batch job, the system checks the 'WHSWaveProcessingRemovedShipment' form for previously failed shipments and creates work for them.
1. **Add work to the next wave** – The *Auto add shipments to wave* batch job adds the newly created work to the next wave for processing.
1. **Control and remove placeholders for completed shipment lines** – The *Auto add shipments to wave* batch job ends by checking the 'WHSWaveProcessingRemovedShipment' form for records that were successfully processed (that is, their status is no longer *Open*) and that the *Shipment* form includes a shipment for. These records indicate shipment lines that were successfully rewaved. The system cleans up these placeholders by removing them from the form. The system will try to rewave a shipment line up to five times. If a line fails on the fifth attempt, the system stops trying and marks that line as *failed*.
1. **Cleanup Shipments that failed rewaving** - The *Wave processing removed Shipments Cleanup* job runs, and removes failed shipment lines from the 'WHSWaveProcessingRemovedShipment'form that were not able to be rewaved. These shipment lines will be removed from the *WHSWaveProcessingRemovedShipment* form depending on the configuration on the *Wave processing removed Shipments Cleanup*. It can be configured in a similar way to the *Auto add shipments to wave* page.

If users wish to start the rewaving process from the beginning, you will need to allow the cleanup job to remove the failed shipment line that could not be rewaved, manually add it to a new wave, system will fail the shipment again, and the process will start from the beginning, with the counter on the **Failed shipment lines** page being set to 0. 
If users would like to rewave a particular shipment an extra time, even though it has been rewaved the maximum five times, users can manually add the specific Shipment ID in the **Shipment ID** field on the *Auto add shipments to wave* page. When the batch job runs, the Shipment ID we specified will also be re-waved. If it has been rewaved the maximum 5 times, the counter will still be increased to 6 since we manually re-added it.

## Enable rewaving for your system

To enable rewaving for your system, you must set your system to process waves in batches and schedule the *Auto add shipments to wave* batch job, as described in the following subsections.

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

1. On the **Records to include** FastTab, you can define selection criteria for limiting the set of shipment lines to be processed.
    - Select **Filter** to open a standard query editor dialog where you can add or remove filter criteria.
    - The **Records to include** FastTab lists each field name and value that you've added using the query editor.
    - The **Number of retries** filter is always included here and its value (5) is read-only. This field indicates that the system will attempt to rewave each failed shipment line up to five times. If a line fails on the fifth attempt, the system will stop trying and will mark that line as *failed*.

### Schedule the cleanup job 

The cleanup job runs as a batch job that you must schedule to run as often as is required for your system. Follow these steps to set up the batch job.

1. Go to  **Warehouse Management** \> **Outbound Waves** \> **Wave Proccessing Removed Shipment** \>
1. On the **Run in the background** FastTab, set the following fields:

    - Set the **Batch processing** option to *Yes*.
    - Make a note of the **Task description** value. The default value is *Wave Processing Removed Shipment*, but you can change it. You can use this value to monitor and edit the job on the **Batch jobs** page.
  
1. Select the **Recurrence** link.
1. Use the fields that are provided to set up a schedule that defines how often the cleanup job runs, and how long it runs for.
1. Select **OK** to save your schedule for the job.
1. Select **OK** to create the job.

On the **Parameters** FastTab, you can select the following:
    - In the **Cleanup rewave threshold** field users can select how many times they want their shipment lines to be rewaved before they are removed from the 'WHSWaveProcessingRemovedShipment' form. That means, even as we have the default setting of five attempted re-waves, the cleanup job can remove shipments from the 'WHSWaveProcessingRemovedShipment'form earlier than after 5 attempts, by selecting a number lower than 5. This can be useful if you would only like failed shipment lines to be re-waved a maximum of say, 3 times before they are removed from the 'WHSWaveProcessingRemovedShipment' form.
    - In the **Last update older than given number** field, users can select to remove failed shipment lines based on this critera as well. Setting this to 30 means cleanup job will run and remove all failed shipment lines with last update being older than the given number. This means, if we select 30 as our number, if we have a shipment line that was last updated 31 days ago, when the cleanup job runs, that line will be removed from the 'WHSWaveProcessingRemovedShipment' form. 

## Monitor the rewave process

### Monitor failed shipment lines

To monitor shipment lines that need to be rewaved, go to **Warehouse Management** \> **Shipments** \> **Failed shipment lines**. For each failed shipment line, this page lists the line ID, its current status, the reason for the failure, and how many times the system tried to rewave it.

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
