---
title: Cleanup routines in Dynamics 365 Finance and Dynamics 365 Supply Chain Management
description: Learn about cleanup routines in Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management, including a table defining various system administration paths.
author: dvliegen
ms.author: dvliegen
ms.topic: article
ms.date: 07/10/2024
ms.custom: 
ms.reviewer: johnmichalak 
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2020-10-31
ms.search.form: 
ms.dyn365.ops.version: 10.0.13
---

# Cleanup routines in Dynamics 365 Finance and Dynamics 365 Supply Chain Management

[!include [banner](../includes/banner.md)]

In Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management, cleanup routines are available in various modules. This article provides an overview of the routines that are currently available. The information is organized by module.

> [!IMPORTANT]
> These cleanup routines should be run only after the business has done detailed analysis and confirmed that the data is no longer required.
>
> Always test each cleanup routine in a test environment before you run it in a production environment.

## System administration

| Path | Description |
|------|-------------|
| System administration \> Periodic tasks \> Notification clean up | <p>This cleanup routine is used to periodically delete records from the EventInbox and EventInboxData tables.</p><p>**Recommendation:** If you don't use alert functionality, turn off the alert from the batch job.</p> |
| System administration \> Periodic tasks \> Batch job history clean-up | This regular version of the [batch job history cleanup](batch-history-cleanup.md) routine lets you quickly clean all history entries that are older than a specified number of days. Any entry that was created earlier is deleted from the BatchJobHistory table, and also from linked tables that have related records (BatchHistory and BatchConstraintsHistory). This version has improved performance optimization, because it doesn't have to run any filtering. |
| System administration \> Periodic tasks \> Batch job history clean-up (custom) | This [custom batch job history cleanup](batch-history-cleanup.md) routine should be used only when specific entries must be deleted. You can clean up selected types of batch job history records, based on criteria such as status, job description, company, or user. You can add other criteria by using the **Filter** button. |
| System administration \> Periodic tasks \> Batch job clean-up | [Clean up the batch job table](batch-job-cleanup.md) should be used regularly to clean up the batch job table. In **Retain jobs (days)** field, specify the number of days to keep the records of batch jobs. This cleanup should be done outside business hours. |
| System administration \> Inquiries \> Database \> Database Log \> Clean up log | <p>This cleanup routine lets you delete database logs as you require. You can delete logs for specific tables, delete specific types of database logs, or delete logs based on the date and time when they were created.</p><p>**Note:** Records that have been electronically signed can't be deleted from logs.</p> |

## Data management

| Path | Description |
|------|-------------|
| In the **Data management** workspace, select **Job history cleanup**. | <p>By default, job history entries and related staging table data that are older than 90 days are automatically deleted (starting September 2023). To configure a job history retention period of less than 90 days, use the Execution history cleanup feature in Data management. It replaces the earlier Staging cleanup routine, which is now obsolete (deprecated).</p><p>The following tables are cleaned up:</p><ul><li>All staging tables</li><li>DMFSTAGINGVALIDATIONLOG</li><li>DMFSTAGINGEXECUTIONERRORS</li><li>DMFSTAGINGLOGDETAIL</li><li>DMFSTAGINGLOG</li><li>DMFDEFINITIONGROUPEXECUTIONHISTORY</li><li>DMFEXECUTION</li><li>DMFDEFINITIONGROUPEXECUTION</li><li>DMFDEFINITIONGROUPEXECUTIONPROGRESS</li></ul> |

## General ledger

| Path | Description |
|------|-------------|
| General ledger \> Periodic tasks \> Clean up ledger journals | <p>This cleanup routine deletes General ledger, Accounts receivable, and Accounts payable journals that have been posted. When you delete a posted ledger journal, all information that is related to the original transaction is removed.</p><p>**Note:** You should delete this information only if you're sure that you won't have to reverse the ledger journal transactions.</p> |

## Retail and Commerce

| Path | Description |
|------|-------------|
| Retail and Commerce \> Retail and Commerce IT \> Email and notifications \> Clean up email notification logs | <p>This cleanup routine sets up a batch job to clean up the email notification logs.</p> |

## Sales and marketing

| Path | Description |
|------|-------------|
| Sales and marketing \> Periodic tasks \> Clean up \> Delete sales orders | This cleanup routine deletes selected sales orders. |
| Sales and marketing \> Periodic tasks \> Clean up \> Delete quotations | This cleanup routine deletes selected quotations. |
| Sales and marketing \> Periodic tasks \> Clean up \> Delete return orders | This cleanup routine deletes selected return orders. |
| Sales and marketing \> Periodic tasks \> Clean up \> Sales update history cleanup | This cleanup routine deletes old update history transactions. All updates of confirmations, picking lists, packing slips, and invoices generate update history transactions. You can view these transactions on the **History on update** page. |
| Sales and marketing \> Periodic tasks \> Clean up \> Order events cleanup | This cleanup routine cleans up order events. The next step is to open the **Order event setup** page and clear the check boxes for any order events that aren't required. |

## Procurement and sourcing

| Path | Description |
|------|-------------|
| Procurement and sourcing \> Periodic tasks \> Clean up \> Purchase update history cleanup | This cleanup routine is used to delete all updates of confirmations, picking lists, product receipts, and invoices that generate update history transactions. |
| Procurement and sourcing \> Periodic tasks \> Clean up \> Delete requests for quotations | This cleanup routine is used to delete requests for quotation (RFQs) and RFQ replies. The corresponding RFQ journals aren't deleted but remain in the system. |
| Procurement and sourcing \> Periodic tasks \> Clean up \> Draft consignment replenishment order journal cleanup | This cleanup routine is used to clean up draft consignment replenishment order journals. |

## Warehouse management

| Path | Description |
|------|-------------|
| Warehouse management \> Periodic tasks \> Clean up \> Work creation history cleanup | This cleanup routine is used to delete work creation history records from the WHSWorkCreateHistorytable table. In the dialog box, you specify the number of days to keep the history. |
| Warehouse management \> Periodic tasks \> Clean up \> Containerization history cleanup | This cleanup routine is used to delete containerization history from the WHSContainerizationHistory table. In the dialog box, you specify the number of days to keep the history. |
| Warehouse management \> Periodic tasks \> Clean up \> Wave processing history log cleanup | This cleanup routine is used to delete the wave processing history log records from the WHSWaveExecutionHistory table. In the dialog box, you specify the number of days to keep the history. |
| Warehouse management \> Periodic tasks \> Clean up \> Wave batch cleanup | This cleanup routine is used to clean up batch job history records that are related to the wave processing batch group. |
| Warehouse management \> Periodic tasks \> Clean up \> Cycle count plan cleanup | This cleanup routine is used to clean up batch job history records that are related to cycle count plan configurations. |
| Warehouse management \> Periodic tasks \> Clean up \> Mobile device activity log cleanup | This cleanup routine is used to delete mobile device activity log records from the WHSMobileDeviceActivityLog table. In the dialog box, you specify the number of days to keep the history. |
| Warehouse management \> Periodic tasks \> Clean up \> Work user session log cleanup | This cleanup routine is used to delete work user session records from the WHSWorkUserSessionLog table. In the dialog box, you specify the number of hours to keep records. |
| Warehouse management \> Periodic tasks \> Clean up \> Wave labels cleanup | This cleanup routine is used to clean up the wave label records from the WHSWaveLabel table. |
| Warehouse management \> Periodic tasks \> Clean up \> Work line history log cleanup | This cleanup routine is used to delete the temporary work history records from the WHSTmpWorkLineHistory table. In the dialog box, you specify the number of days to keep the history. |
| Warehouse management \> Periodic tasks \> Clean up \> Clean up License plate registration history | This cleanup routine is used to delete the license plate receiving history records from the WHSLicensePlateReceivingHistory. In the dialog box, you specify the number of days to keep the history. |
| Warehouse management \> Periodic tasks \> Clean up \> Clean up work exception logs | This cleanup routine is used to delete work exception log records from WHSWorkExceptionLog. In the dialog box, you specify the number of days to keep the history, the status of work exception logs to be deleted (i.e. Open or Closed) and the maximum amount of records that can be deleted by this operation. |

## Inventory management

The following table describes the cleanup jobs that are available for the Inventory management module. Each of them is listed under the **Inventory management** \> **Periodic tasks** \> **Clean up** path in the navigation pane at the left side of the page. You can also find any of them by entering the job name directly into the **Search for a page** field in the navigation bar at the top of the page.

| Job name | Description |
|------|-------------|
| Calculation of location load | The `WMSLocationLoad` table tracks the weight and volume of items and pallets. The *Calculation of location load* job reduces the number of records in the `WMSLocationLoad` table and helps improve performance. |
| Inventory journals cleanup | This cleanup routine deletes posted inventory journals. Cleaning up posted inventory journals can help free system resources. |
| Inventory settlements cleanup | <p>This cleanup routine groups closed inventory transactions or deletes canceled inventory settlements. By cleaning up closed or deleted inventory settlements, you can help free up system resources.</p><p>Don't group or delete inventory settlements that are too close to the current date or fiscal year, because part of the transaction information for the settlements are lost.</p><p>Closed inventory transactions can't be changed after they're grouped, because the transaction information for the settlements is lost.</p><p>If canceled inventory settlements are deleted, they can't be reconciled with finance transactions.</p><p>The dialog for setting up this job provides the following optional settings:</p><ul><li>**Group settlements posted before** – Enter the date before which the closed inventory transactions settlements will be grouped.</li><li>**Delete canceled settlements posted before** – Enter the date before which the settlements were canceled and will be deleted.</li></ul> |
| Inventory dimensions cleanup | <p>This cleanup routine maintains the `InventDim` table. It deletes all existing inventory dimensions that are defined but not used in the current company. All unused inventory dimensions are permanently deleted regardless of whether the transaction is open or closed.</p><p>This cleanup routine verifies whether each `InventDim` record is being used in any purchase order lines, sales order lines, inventory transactions, and/or on-hand inventory records. If a reference exists to `InventDim`, it's checked. If it's not used, it's deleted. If the same combination of dimensions is used later, the system creates a new `InventDim` record with a new `InventDimId` value and uses this instead.</p><p>Inventory dimension combination records that are still referenced can't be deleted because when an `InventDim` record is deleted, related transactions can't be reopened.</p><p>**Warning:** This job deletes all inventory dimensions that were created during the targeted date range and which are defined but not used in the current company. Unused inventory dimensions are deleted permanently. No alert or database log is created during the process. Don't run this job without a good reason. Be sure to schedule this process to run outside of business hours. |
| On-hand entries cleanup | <p>This cleanup routine deletes closed and unused entries for on-hand inventory that is assigned to one or more tracking dimensions. Closed transactions are marked as closed and contain a value of *0* (zero) for all quantities and cost values. By deleting these transactions, you can help improve the performance of queries for on-hand inventory. Transactions won't be deleted for on-hand inventory that isn't assigned to tracking dimensions.</p><p>The dialog for setting up this job provides the following setting:</p><ul><li>**Delete if not updated for this many days** – Closed on-hand entries that haven't been updated for this number of days will be deleted (default is *7*). Entries that have been changed during this period aren't deleted</li></ul> |
| Warehouse management on-hand cleanup | This cleanup routine deletes records in the `InventSum` and `WHSInventReserve` tables. These tables are used to store on-hand information for items that are enabled for warehouse management processes (that is, WHS items). By cleaning up these records, you can significantly improve the performance of on-hand calculations. |
| On-hand entries aggregation by financial dimensions | <p>This cleanup routine aggregates `InventSum` rows that have a quantity of 0 (zero) and cleans up records where **Closed** is set to *True*.</p><p>This routine handles scenarios where there are no more quantities in the `InventSum` table for a combination of inventory dimensions, but there's still a value. Although these values disappear in some cases, the current design occasionally allows values to remain.</p><p>For example, if you use batch numbers, each batch number (and the combined site, warehouse, and so on) creates a new record in the `InventSum` table. When the batch number is sold, quantity fields are set to *0* (zero). In most cases, the **Financial cost amount** and **Physical cost amount** fields are also set to *0* (zero). However, in standard cost revaluation and other scenarios, the field might still show some amount. This behavior is valid, and reflects the way that the system handles costs at the financial inventory level (for example, the site level).</p><p>Inventory value is determined by records in the `InventSum` table. In some cases, when inventory values in the past are reported, value is determined by inventory transactions (the `InventTrans` table). Therefore, when you run inventory value reports, the system initially looks at the `InventSum` table, aggregates all records to the site level, and reports the value for the item per site.</p><p>The data from the individual records at the batch-number level are never used. Therefore, this routine goes through all `InventSum` records, finds the records where there's no more quantity (that is, where **No open quantities** is set to *True*). Because there's no reason to keep these records, the system finds the `InventSum` record for the same item that has the same site, copies the values from the batch-number level to the site level, and deletes the record. Then, when you run inventory value reports, the system still finds the same correct values. Therefore, this routine reduces number of `InventSum` records, significantly in some cases, and can have a positive impact on the performance of any function that queries that table.</p> |
| Cost calculation details | This cleanup routine cleans up cost calculation details. |
| Transfer order update history cleanup  | This cleanup routine deletes records from the `InventTransferParmTable`, `InventTransferParmUpdate` and `InventTransferParmLine` tables. These tables are used when posting transfer orders. This cleanup can help improve the performance of any function that queries these tables. |
| Inventory transaction consolidation | This cleanup routine consolidates data about inventory transactions to help improve system performance. For more information about this functionality, see [Consolidate inventory transactions](../../../supply-chain/inventory/archive-inventory-transactions.md). |
| Inventory on-hand report data clean up | <p>This cleanup routine deletes on-hand storage data for reports that were executed before a specific date.</p><p>The dialog for setting up this job provides the following setting:</p><ul><li>**Delete inventory on-hand report executed before** – Enter the newest date for which to keep report data. Data for reports that are older than this will be deleted.</li></ul>  |
| Correct inventory transfer order lines manually | <p>This cleanup routine fixes inconsistent data and corrects unexpected quantities that are related to transfer orders.</p><p>The dialog for setting up this job provides the following settings:</p><ul><li>**Recalculate transfer-related quantities** – Set to *Yes* to recalculate and correct shipped quantity, ship remaining quantity, and receive remaining quantity values.</li><li>**Recalculate inventory transactions** – Set to *Yes* to fix corrupted inventory transactions, such as received transfer orders that still have ordered transactions and transfer orders that are linked to completed output orders.</li><li>**Recalculate header status** – Set to *Yes* to correct transfer orders' header status values based on their line status values.</li><li>**Recover header** – Set to *Yes* to recover transfer orders that were unexpectedly removed even though they weren't fully received, related order lines still exist, or related inventory transactions still exist.</li></ul> |
| Inventory journal data correction | <p>This cleanup routine deletes all on-order or ordered inventory transactions that link to posted or nonexistent inventory journals in the current company. You can choose whether or not to clean up orphan unposted inventory transactions without journal lines.</p><p>**Warning:** The inventory transactions are deleted permanently. No alert or database log is created during the process. Don't run this process without a good reason, and be sure test carefully before running it in production environment.</p> |
| Correct item that is not visible in released products form manually | This cleanup routine solves display problems such as released products not displaying and e-commerce catalogs not working after you deploy a proactive quality update (PQU) for your system. It works by making sure the `InventDim` table includes a record where the `InventDimId` field has a value of *AllBlank*, and that records in the `InventItemLocation` table correctly relate to this record through the `InventItemLocation.InventDimId` field as needed. |

## Production control

| Path | Description |
|------|-------------|
| Production control \> Periodic tasks \> Clean up \> Production journals cleanup | This cleanup routine is used to delete unused journals. |
| Production control \> Periodic tasks \> Clean up \> Production orders cleanup | This cleanup routine is used to delete production orders that are ended. |
| Production control \> Periodic tasks \> Clean up \> Clean up registrations | <p>We recommend that you periodically clean up registrations. This cleanup routine deletes only data that has been processed.</p><p>**Note:** Make sure that you don't delete registrations that might be required later for documentation purposes.</p> |
| Production control \> Periodic tasks \> Clean up \> Archive future registrations | This cleanup routine is used to remove future registrations from the raw registrations table. |

## Cost management

| Path | Description |
|------|-------------|
| Cost management \> Manufacturing accounting \> Clean up \> Production orders cleanup | <p>Same as **Production control \> Periodic tasks \> Clean up \> Production orders cleanup**.<br><br>This cleanup routine is used to delete production orders that have ended.</p> |
| Cost management \> Manufacturing accounting \> Clean up \> Production recalculation | Bundles production orders where the estimated costs for material and time consumption should be recalculated and schedules recalculation tasks. |
| Cost management \> Manufacturing accounting \> Clean up \> Clean up the costing sheet cache | The CostSheetCache table is used as a temp location for cost sheets to help generate prices. This job cleans up the costing sheet cache. Records in the cache that have an age of the specified days or older are deleted. |

## Master planning

| Path | Description |
|------|-------------|
| Master planning \> Master planning \> Maintain plans \> Plan version cleanup | Usually, this cleanup is done automatically. However, automatic cleanup sometimes malfunctions, and orphan data remains in the system. This orphan data slows down queries and causes the database size to grow. We recommend that you do a preventive run one time per month, when master resource planning (MRP) isn't running. |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
