---
# required metadata

title: Warehouse management on-hand entries cleanup job
description: This article describes the on-hand entries cleanup job, which helps improve system performance by identifying and deleting related but unneeded records.
author: perlynne
ms.date: 04/23/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  SysOperationTemplateForm
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for articles migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: perlynne
ms.search.validFrom: 2020-04-03
ms.dyn365.ops.version: 10.0.12
---

# Warehouse management on-hand entries cleanup job

[!include [banner](../includes/banner.md)]

The performance of queries that are used to calculate on-hand inventory is affected by the number of records in the tables that are involved. One way to help improve the performance is to reduce the number of records that the database must consider.

This article describes the on-hand entries cleanup job, which deletes unneeded records in the `InventSum` and `WHSInventReserve` tables. These tables store on-hand information for items that are enabled for warehouse management processing. (These items are referred to as WMS items.) Deletion of these records can significantly improve the performance of on-hand calculations.

## What the cleanup job does

The on-hand entries cleanup job deletes any records in the `WHSInventReserve` and `InventSum` tables where all the field values are *0* (zero). These records can be deleted because they don't contribute to the on-hand information. The job deletes only records that are below the **Location** level.

If negative physical inventory is allowed, the cleanup job might not be able to delete all the relevant entries. The reason for this limitation is that the job must allow for a special scenario where a license plate has multiple serial numbers, and one of those serial numbers has become negative. For example, the system will have zero on hand at the license plate level when a license plate has +1 pcs of serial number 1 and –1 pcs of serial number 2. For this special scenario, the job does a breadth-first deletion, where it tries to delete from lower levels first.

## Schedule and configure the cleanup job

The on-hand entries cleanup job is available at **Inventory management \> Periodic tasks \> Clean up \> Warehouse management on-hand entries cleanup**. Use the standard job settings to control the scope and schedule for running the job. In addition, the following settings are provided:

- **Delete if not updated for this many days** – Enter the minimum number of days that the job should wait before it deletes an on-hand entry that has dropped to zero quantity. Use this setting to help reduce the risk of deleting on-hand entries that are still being used. If you want cleanup to occur as soon as possible, either enter *0* (zero) or leave the field blank.
- **Maximum execution time (hours)** – Enter the maximum execution time of the cleanup job, in hours. If the job isn't completed before this time passes, it will save the work that it has completed so far and then close itself. This capability is especially relevant for implementations that have high inventory use. In these cases, you should schedule the job to run at times when the system load is as light as possible. If you want the batch job to continue to run until it's completed, either enter *0* (zero) or leave the field blank. This setting is available only if the related feature has been [turned on for your system](#max-execution-time).

Although you can run the job during regular business hours, we recommend that you run it outside working hours. In this way, you help prevent conflicts that can occur if a user is working with a record that is also being cleaned up.

If the job tries to delete a record for an item while that record is being used by another user, a deadlock error occurs for either the cleanup job or the user.

When the job runs, it has a commit size of 100. In other words, it will try to commit one time for every 100 deletions. However, because some deletions are set-based, there might be scenarios where more than 100 records can be deleted in the same transaction. Therefore, lock escalations can still sometimes occur.

## Possible user impact

Users might be affected if the on-hand entries cleanup job deletes all the records for a given level (such as the license plate level). In this case, the functionality for seeing that inventory was previously available on-hand at a license plate might not work as expected because the relevant on-hand entries are no longer available. This can, for example, be experienced in the following situations:

- On the **On-hand list**, when the user deselects the condition **Quantity \<\> 0** or selects the condition **Closed transactions** in the **Dimensions display** settings.
- In a **Physical inventory by inventory dimension** report for past periods, when the user sets the **As of date** parameter.

However, the performance improvement that the cleanup job provides should make up for these small losses in functionality.

## <a name="max-execution-time"></a>Make the Maximum execution time setting available

The **Maximum execution time** setting is only available when the *Maximum execution time for the warehouse management on-hand entries cleanup job* feature is turned on. As of Supply Chain Management version 10.0.25, this feature is turned on by default. As of Supply Chain Management version 10.0.32, this feature is mandatory and can't be turned off. If you are running a version older than 10.0.32, then admins can turn this functionality on or off by searching for the *Maximum execution time for the warehouse management on-hand entries cleanup job* feature in the [**Feature management** workspace](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]