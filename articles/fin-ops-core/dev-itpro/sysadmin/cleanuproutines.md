---
# required metadata

title: Cleanup routines in Dynamics 365 Finance and Dynamics 365 Supply Chain Management
description: The article provides an overview of cleanup routines in Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management.
author: dvliegen
ms.date: 08/01/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dvliegen
ms.search.validFrom: 2020-10-31
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
| System administration \> Periodic tasks \> Batch job history clean-up | This regular version of the [batch job history cleanup](batch-history-cleanup.md) routine lets you quickly clean all history entries that are older than a specified number of days. Any entry that was created earlier will be deleted from the BatchJobHistory table, and also from linked tables that have related records (BatchHistory and BatchConstraintsHistory). This version has improved performance optimization, because it doesn't have to run any filtering. |
| System administration \> Periodic tasks \> Batch job history clean-up (custom) | This [custom batch job history cleanup](batch-history-cleanup.md) routine should be used only when specific entries must be deleted. You can clean up selected types of batch job history records, based on criteria such as status, job description, company, or user. You can add other criteria by using the **Filter** button. |
| System administration \> Inquiries \> Database \> Database Log \> Clean up log | <p>This cleanup routine lets you delete database logs as you require. You can delete logs for specific tables, delete specific types of database logs, or delete logs based on the date and time when they were created.</p><p>**Note:** Records that have been electronically signed can't be deleted from logs.</p> |

## Data management

| Path | Description |
|------|-------------|
| In the **Data management** workspace, select **Job history cleanup**. | <p>By default, job history entries and related staging table data that are older than 90 days are automatically deleted (starting September 2023). To configure a job history retention period of less than 90 days, use the Execution history cleanup feature in Data management. It replaces the earlier Staging cleanup routine, which is now obsolete (deprecated).</p><p>The following tables will be cleaned up:</p><ul><li>All staging tables</li><li>DMFSTAGINGVALIDATIONLOG</li><li>DMFSTAGINGEXECUTIONERRORS</li><li>DMFSTAGINGLOGDETAIL</li><li>DMFSTAGINGLOG</li><li>DMFDEFINITIONGROUPEXECUTIONHISTORY</li><li>DMFEXECUTION</li><li>DMFDEFINITIONGROUPEXECUTION</li></ul> |
| In the **Data management** workspace, select the **Staging cleanup** tile. | This cleanup routine should no longer be used, because it's obsolete. Instead, use the Job history cleanup routine. |

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
| Warehouse management \> Periodic tasks \> Clean up \> Work creation history purge | This cleanup routine is used to delete work creation history records from the WHSWorkCreateHistorytable table. In the dialog box, you specify the number of days to keep the history. |
| Warehouse management \> Periodic tasks \> Clean up \> Containerization history purge | This cleanup routine is used to delete containerization history from the WHSContainerizationHistory table. In the dialog box, you specify the number of days to keep the history. |
| Warehouse management \> Periodic tasks \> Clean up \> Wave batch cleanup | This cleanup routine is used to clean up batch job history records that are related to the wave processing batch group. |
| Warehouse management \> Periodic tasks \> Clean up \> Cycle count plan cleanup | This cleanup routine is used to clean up batch job history records that are related to cycle count plan configurations. |
| Warehouse management \> Periodic tasks \> Clean up \> Mobile device activity log cleanup | This cleanup routine is used to delete mobile device activity log records from the WHSMobileDeviceActivityLog table. In the dialog box, you specify the number of days to keep the history. |
| Warehouse management \> Periodic tasks \> Clean up \> Work user session log cleanup | This cleanup routine is used to delete work user session records from the WHSWorkUserSessionLog table. In the dialog box, you specify the number of hours to keep records. |

## Inventory management

| Path | Description |
|------|-------------|
| Inventory management \> Periodic tasks \> Clean up \> Calculation of location load | The WMSLocationLoad table is used to track the weight and volume of items and pallets. The Summation of load adjustments job can be run to reduce the number of records in the WMSLocationLoad table and help improve performance. |
| Inventory management \> Periodic tasks \> Clean up \> Inventory journals cleanup | This cleanup routine is used to delete posted inventory journals. |
| Inventory management \> Periodic tasks \> Clean up \> Inventory settlements cleanup | <p>This cleanup routine is used to group closed inventory transactions or delete canceled inventory settlements. By cleaning up closed or deleted inventory settlements, you can help free up system resources.</p><p>Don't group or delete inventory settlements that are too close to the current date or fiscal year, because part of the transaction information for the settlements will be lost.</p><p>Closed inventory transactions can't be changed after they have been grouped, because the transaction information for the settlements will be lost.</p><p>If canceled inventory settlements are deleted, they can't be reconciled with finance transactions.</p> |
| Inventory management \> Periodic tasks \> Clean up \> Inventory dimensions cleanup | <p>This cleanup routine is used to maintain the InventDim table. This batch process deletes all existing inventory dimensions that are defined but not used in the current company. All unused inventory dimensions are permanently deleted. No alert or database log is created during this process.</p><p>This cleanup routine verifies if each InventDim record is being used in not only purchase order lines or sales order lines, but also inventory transactions or on-hand inventory records. If a reference exists to InventDim, it's checked. If it's not used, it will be deleted. If the same combination of dimensions is used later, Dynamics 365 Finance and Dynamics 365 Supply Chain Management will create a new InventDim record with a new InventDimId and use this instead.</p> |
| Inventory management \> Periodic tasks \> Clean up \> Dimension inconsistency cleanup | <p>This cleanup routine is used to resolve dimension inconsistencies on inventory transactions that have been financially updated and closed. Inconsistencies might be introduced if the multisite functionality was activated during or before the upgrade process.</p><p>Use this routine only to clean up the transactions that were closed before the multisite functionality was activated.</p><p>**Note:** Don't use this routine periodically.</p> |
| Inventory management \> Periodic tasks \> Clean up \> On-hand entries cleanup | This cleanup routine is used to delete closed and unused entries for on-hand inventory that is assigned to one or more tracking dimensions. Closed transactions contain a value of **0** (zero) for all quantities and cost values, and they're marked as closed. By deleting these transactions, you can help improve the performance of queries for on-hand inventory. Transactions won't be deleted for on-hand inventory that isn't assigned to tracking dimensions. |
| Inventory management \> Periodic tasks \> Clean up \> Warehouse management on-hand entries cleanup | This cleanup routine deletes records in the InventSum and WHSInventReserve tables. These tables are used to store on-hand information for items that are enabled for warehouse management processing (that is, WHS items). By cleaning up these records, you can significantly improve of the on-hand calculations. |
| Inventory management \> Periodic tasks \> Clean up \> On-hand entries aggregation by financial dimensions | <p>Use this cleanup routine as a tool to aggregate InventSum rows that have 0 (zero) quantities. This routine basically extends the previously mentioned routine by also cleaning up records where the **Closed** field is set to **True**.</p><p>Basically, this routine is needed to handle scenarios where there are no more quantities in the InventSum table for a combination of inventory dimensions, but there's still a value. Although these values will disappear in some cases, the current design occasionally allows values to remain.</p><p>For example, if you use batch numbers, each batch number (and the combined site, warehouse, and so on) creates a new record in the InventSum table. When the batch number is sold, you'll see that quantity fields are set to **0** (zero). In most cases, the **Financial cost amount** and **Physical cost amount** fields are also set to **0** (zero). However, in standard cost revaluation and other scenarios, the field might still show some amount. This behavior is valid, and it reflects the way that Finance and Supply Chain Management handle the costs at the financial inventory level (for example, the site level).</p><p>In Finance and Supply Chain Management, inventory value is determined by records in the InventSum table. In some cases, when inventory values in the past are reported, it's determined by inventory transactions (the InventTrans table). Therefore, in the previously described scenario, when you run inventory value reports, Finance and Supply Chain Management initially look at the InventSum table, aggregate all records to the site level, and report the value for the item per site.</p><p>The data from the individual records at batch number level are never used. Therefore, this routine goes through all InventSum records, finds the records where there's no more quantity (that is, **No open quantities** field is set to **True**). Because there's no reason to keep these records, Finance and Supply Chain Management find the InventSum record for the same item that has the same site, they copy the values from the batch number level to the site level, and they delete the record. Then, when you run inventory value reports, Finance and Supply Chain Management still find the same correct values. Therefore, this routine reduces number of InventSum records, significantly in some cases, and can have a positive impact on the performance of any function that queries that table.</p> |
| Inventory management \> Periodic tasks \> Clean up \> Cost calculation details | This cleanup routine is used to clean up cost calculation details. |

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
