---
# required metadata

title: On-hand entry cleanup
description: This topic describes the on-hand entries cleanup job, which helps improve system performance by identifying and deleting related, but unneeded, records.
author: perlynne
manager: tfehr
ms.date: 04/23/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: perlynne
ms.search.validFrom: 2020-04-03
ms.dyn365.ops.version: Release 10.0.12
---

# On-hand entry cleanup

The performance of queries used to calculate the on-hand inventory is affected by the number of records in the tables involved. One way to improve the performance of such operations is to reduce the number of records that the database has to consider.

This topic describes the on-hand entries cleanup job, which deletes records in the `InventSum` and `WHSInventReserve` tables. These tables store on-hand information for items enabled for warehouse management processing (WHS items). Cleaning up these records can significantly improve the performance of on-hand calculations.

## Run the on-hand entry cleanup

The cleanup job is available under **Inventory Management > Periodic tasks > Clean up > Warehouse management on-hand entries cleanup**. Use the standard job settings here to control the scope and schedule for running the job. In addition, the following settings are provided:

- **Delete if not updated for this many days** - Use this field to reduce the risk of deleting on-hand entries that are still in use. Enter a value of "0" (or leave blank) to allow cleaning up as much as possible.
- **Maximum execution time (hours)** - Enter a maximum execution time (in hours) for the cleanup job. If the job doesn't complete before the time is up, it will save the work completed so far and then exit. This capability is especially relevant for implementations that have high inventory usage, in which case you should schedule the job to run at times when the system is as lightly loaded as possible. Enter a value of "0" (or leave blank) to allow the batch job to continue running until it has finished. This setting is only available if it has been [enabled on your system](#max-execution-time).

You can run the job during normal business hours, but we recommend running it outside of working hours to avoid conflicts where a user is working with a record that is also being cleaned up.

If the job tries to delete a record for an item while it is being used by another user, a deadlock error will occur for either the cleanup job or the user.

The job runs with a commit size of 100, which means that it will try to commit for every 100 deletes. However, since some deletes are set-based, there might be scenarios where more than 100 records can be deleted in the same transaction, so  lock escalations can still sometimes occur.

## What the clean up job does

The cleanup job deletes records in the `WHSInventReserve` and `InventSum` tables where all the field values are 0, because these don't contribute to the on-hand. The job only deletes records below the Location level.

If negative physical inventory is allowed, then the job might not be able to delete all the relevant entries. This is because the job must allow for a special scenario where a license plate has multiple serial numbers and one serial number has gone negative. For example, the system will have zero on-hand at the license plate level when a license plate has +1 pcs of serial number #1 and -1 pcs with serial number #2. For this special case, the job does a breadth-first delete, trying to delete from lower levels first.

## Possible user impact

Users may be impacted if the cleanup job has deleted all records for a given level (such as the license plate level), in which case the functionality for seeing that inventory was once available on-hand at a license plate may not work as expected because the relevant on-hand entries are no longer available. This is the functionality where the condition **Quantity <> 0** is checked in the **Dimension display** settings when viewing on-hand. However, the performance improvement provided by the cleanup job should make up for this small loss in functionality.

<a name="max-execution-time"></a>

## Enable the maximum execution time setting

The **Maximum execution time** setting isn't enabled by default. Use [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) to enable it on your system if you'd like to use it. The feature is listed as:

- **Module** - *Warehouse management*
- **Feature name** - *Maximum execution time for the warehouse management on-hand entries cleanup job*
