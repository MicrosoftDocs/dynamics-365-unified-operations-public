---
title: Warehouse management on-hand entries cleanup job
description: Learn when to use warehouse management on-hand entries cleanup and how to run the separate cleanup for warehouse user locations.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form: SysOperationTemplateForm
ms.topic: how-to
ms.date: 11/24/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Warehouse management on-hand entries cleanup job

[!INCLUDE [banner](../includes/banner.md)]

The performance of queries that calculate on-hand inventory depends on the number of records in the tables. To improve performance, reduce the number of records the database must consider.

Use the *Warehouse management on-hand entries cleanup* batch job to remove unused entries below the location level for items that use warehouse management processes. To remove closed entries specifically at warehouse user locations, use the *[Clean up on-hand records for user locations](#clean-up-on-hand-records-for-user-locations)* batch job instead. The two jobs use different settings.

## What the cleanup job does

The on-hand entries cleanup job deletes any records in the `WHSInventReserve` and `InventSum` tables where all the field values are *0* (zero). These records can be deleted because they don't contribute to the on-hand information. The job deletes only records that are below the **Location** level.

If you allow negative physical inventory, the cleanup job might not be able to delete all the relevant entries. This limitation exists because the job must account for a special scenario where a license plate has multiple serial numbers, and one of those serial numbers becomes negative. For example, the system shows zero on hand at the license plate level when a license plate has +1 pcs of serial number 1 and –1 pcs of serial number 2. For this special scenario, the job performs a breadth-first deletion, where it tries to delete from lower levels first.

## Schedule and configure the cleanup job

You can find the on-hand entries cleanup job at **Inventory management > Periodic tasks > Clean up > Warehouse management on-hand entries cleanup**. Use the standard job settings to control the scope and schedule for running the job. In addition, the following settings are provided:

- **Delete if not updated for this many days** – Enter the minimum number of days that the job should wait before it deletes an on-hand entry that drops to zero quantity. Use this setting to help reduce the risk of deleting on-hand entries that are still in use. If you want cleanup to occur as soon as possible, either enter *0* (zero) or leave the field blank.
- **Maximum execution time (hours)** – Enter the maximum execution time of the cleanup job, in hours. If the job isn't completed before this time passes, it saves the work that it completed so far and then closes itself. This capability is especially relevant for implementations that have high inventory use. In these cases, schedule the job to run at times when the system load is as light as possible. If you want the batch job to continue to run until it's completed, either enter *0* (zero) or leave the field blank.

Although you can run the job during regular business hours, run it outside working hours. In this way, you help prevent conflicts that can occur if a user is working with a record that the job is also cleaning up.

If the job tries to delete a record for an item while another user is using that record, a deadlock error occurs for either the cleanup job or the user.

When the job runs, it has a commit size of 100. In other words, it tries to commit one time for every 100 deletions. However, because some deletions are set-based, there might be scenarios where more than 100 records can be deleted in the same transaction. Therefore, lock escalations can still sometimes occur.

## Possible user impact

Users might be affected if the on-hand entries cleanup job deletes all the records for a given level, such as the license plate level. In this case, the functionality for seeing that inventory was previously available on-hand at a license plate might not work as expected because the relevant on-hand entries are no longer available. Users can experience this issue in the following situations:

- On the **On-hand list**, when the user deselects the condition **Quantity \<\> 0** or selects the condition **Closed transactions** in the **Dimensions display** settings.
- In a **Physical inventory by inventory dimension** report for past periods, when the user sets the **As of date** parameter.

However, the performance improvement that the cleanup job provides should make up for these small losses in functionality.

## Clean up on-hand records for user locations

After a worker finishes warehouse work, closed on-hand entries can remain at the worker's user location. Use the *Cleanup on-hand records for user locations* batch job to remove those entries without changing inventory quantities.

The job selects closed on-hand entries that have no open quantities and zero physical inventory. For items that use a reservation hierarchy, it also removes related empty reservation records, up to and including the location level. It keeps open on-hand entries, reservations with nonzero quantities, and any reservation record that a lower-level record still uses. It doesn't clean up reservations above the location level.

### Prerequisites

To use the *Cleanup on-hand records for user locations* batch job, your system and user account must meet the following requirements:

- You must be running Dynamics 365 Supply Chain Management version 10.0.51 or later.
- Your user account must be assigned a security role that includes the *Clean up closed on-hand entries* privilege.
- The target warehouse must be enabled for warehouse management processes (WMS).
- A **User location profile** must be specified on the **[Warehouse management parameters](tasks/configure-locations-wms-enabled-warehouse.md#set-warehouse-management-parameters)** page, and it must reference an existing profile.

### Run or schedule the cleanup job

To run the *Cleanup on-hand records for user locations* job once or on a schedule, follow these steps:

1. Go to **Inventory management** > **Periodic tasks** > **Clean up** > **Cleanup on-hand records for user locations**.
1. Specify the locations the job should process:
    - To clean up one location, select the **Warehouse** first, and then select the **User location**.
    - To clean up all user locations in one warehouse, select the **Warehouse** and leave **User location** blank.
    - To clean up all eligible warehouses in the current company, leave both fields blank.

1. Set **Maximum execution time (minutes)** to the maximum time you want the job to use each time it runs. Enter a value greater than zero. The default is *60* minutes. When this time limit is reached, the job finishes processing the current location and then stops.
1. Use the **Continue last execution** setting to control what happens the next time the job runs if it reaches the **Maximum execution time (minutes)** limit before processing all locations. This setting only has an effect when you process multiple locations (**User location** is blank). If you select a single location, the job fully processes that location every time.
    - Select *Yes* to resume from the next location on the list the next time it runs.
    - Select *No* to restart from the first location on the list each time it runs.

1. On the **Run in the background** FastTab, set **Batch processing** to *No* to run the job once right away. To schedule the job to run in the background, set **Batch processing** to *Yes* and select **Recurrence** to set up the schedule. The settings work just as they do for other types of [background jobs](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management.
1. Select **OK** to run or schedule the job according to the settings you specified.

The completion message reports how many locations the job processed, not how many records it removed. On each visit, the job processes up to 1,000 candidate on-hand entries at a time, with a default limit of 10 batches per location. A location can therefore still have eligible entries after a completed run. Run the job again for that location, or let a recurring job revisit it. If the job reports that it reached the time limit, use **Continue last execution** on the next multi-location run so that later locations get a turn.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
