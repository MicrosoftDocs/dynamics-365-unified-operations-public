---
# required metadata

title: Cleanup routines in Dynamics 365 Finance and Supply Chain Management
description: The topic provides an overview of cleanup routines in Dynamics 365 Finance and Supply Chain Management
author: dvliegen
manager:
ms.date: 10/06/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form:  
audience: IT Pro
# ms.devlang: 
ms.reviewer: 
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dvliegen
ms.search.validFrom: 2020-10-06
ms.dyn365.ops.version: October 2020 update
---

# Cleanup routines in Dynamics 365 Finance and Supply Chain Management

In Dynamics 365 Finance and Supply Chain Management cleanup routines are available across various modules within the product.
It is important to note that these cleanup routines should be only executed after detailed analysis and confirmation from the business this data is no longer needed.
Also always test each routine first in test environment prior executing it in production. This article provides an overview on what is available today.

## System administration

| **Module**             | **Path**                | **Description** |
|---------------------|-----------------------------|-------------------------------|
| System administration        |   Periodic tasks > Notification clean up               | This is used to periodically delete records from tables EventInbox and EventInboxData. **Recommendation: If you don’t use Alert functionality, disable Alert from Batch job.**
| System administration        |   Periodic tasks > Batch job history clean-up          | The regular version of batch job history clean-up allows you to quickly clean all history entries older than a specified timeframe (in days). Any entry that was created prior to – will be deleted from the BatchJobHistory table, as well as from linked tables with related records (BatchHistory and BatchConstraintsHistory). This form has improved performance optimization because it doesn’t have to execute any filtering. |
| System administration        |   Periodic tasks > Batch job history clean-up (custom) | The custom batch job clean-up form should be used only when specific entries need to be deleted. This form allows you to clean up selected types of batch job history records, based on criteria such as status, job description, company, or user. Other criteria can be added using the Filter button. |
| System administration        |   Inquiries > Database > Database Log > Clean up log   | You can delete database logs as required. You can delete logs for specific tables, delete specific types of database logs, or delete logs based on the date and time when they were created. **Note: Records that have been electronically signed can't be deleted from logs.** |

 
## Data management

| **Module**             | **Path**                | **Description** |
|---------------------|-----------------------------|-------------------------------|
| Data management | Data management workspace > Job history cleanup | Available in Platform update 29 and later, functionality must be enabled in Feature management and Feature name is “Execution history cleanup”. The job history clean-up functionality in data management must be used to schedule a periodic cleanup of the execution history. <br> This functionality replaces the previous staging table clean-up functionality, which is now deprecated. The following tables will be cleaned up by the clean-up process: <br> - All staging tables <br> - DMFSTAGINGVALIDATIONLOG <br> - DMFSTAGINGEXECUTIONERRORS <br> - DMFSTAGINGLOGDETAIL <br> - DMFSTAGINGLOG <br> - DMFDEFINITIONGROUPEXECUTIONHISTORY <br> - DMFEXECUTION <br> - DMFDEFINITIONGROUPEXECUTION |
| Data management | Data management workspace > “Staging cleanup” tile | **The Staging cleanup functionality should no longer be used, it is depreciated. Instead use Job history cleanup** |


 ## General ledger

| **Module**             | **Path**                | **Description** |
|---------------------|-----------------------------|-------------------------------|
| General ledger | Periodic tasks > Clean up ledger journals | It deletes general ledger, accounts receivable, and accounts payable journals that have been posted. When you delete a posted ledger journal, all information that’s related to the original transaction is removed. **You should delete this information only if you’re sure that you won’t have to reverse the ledger journal transactions.** |


## Sales and marketing

| **Module**             | **Path**                | **Description** |
|---------------------|-----------------------------|-------------------------------|
| Sales and marketing | Periodic tasks > Clean up > Delete sales orders | It deletes selected sales orders. |
| Sales and marketing | Periodic tasks > Clean up > Delete quotations | It deletes selected quotations. |
| Sales and marketing | Periodic tasks > Clean up > Delete return orders | It deletes selected return orders. |
| Sales and marketing | Periodic tasks > Clean up > Sales update history cleanup | It deletes old update history transactions. All updates of confirmations, picking lists, packing slips, and invoices generate update history transactions. These transactions ca be viewed in the History on update form. |
| Sales and marketing | Periodic tasks > Clean up > Order events cleanup | Cleanup job for order events. Next step is to remove the not needed order events check-boxes from Order event setup form. |

 
## Procurement and sourcing

| **Module**             | **Path**                | **Description** |
|---------------------|-----------------------------|-------------------------------|
| Procurement and sourcing | Periodic tasks > Clean up > Purchase update history cleanup | This is used to delete all updates of confirmations, picking lists, product receipts, and invoices generate update history transactions. |
| Procurement and sourcing | Periodic tasks > Clean up > Delete requests for quotations | It is used to delete requests for quotation (RFQs) and RFQ replies. The corresponding RFQ journals are not deleted, but remain in the system. |
| Procurement and sourcing | Periodic tasks > Clean up > Draft consignment replenishment order journal cleanup | It is used to cleanup draft consignment replenishment order journals. |


## Warehouse management

| **Module**             | **Path**                | **Description** |
|---------------------|-----------------------------|-------------------------------|
| Warehouse management | Periodic tasks > Clean up > Work creation history purge | This is used to delete work creation history records from WHSWorkCreateHistorytable based on number of days to keep the history provided on dialog. |
| Warehouse management | Periodic tasks > Clean up > Containerization history purge | This is used to delete containerization history from WHSContainerizationHistory table based on number of days to keep the history provided on dialog. |
| Warehouse management | Periodic tasks > Clean up > Wave batch cleanup | This is used to clean up batch job history records related to Wave processing batch group. |
| Warehouse management | Periodic tasks > Clean up > Cycle count plan cleanup | This is used to clean up batch job history records related to Cycle count plan configurations. |
| Warehouse management | Periodic tasks > Clean up > Mobile device activity log cleanup | This is used to delete mobile device activity log records from WHSMobileDeviceActivityLog table based on number of days to keep the history provided on dialog. |
| Warehouse management | Periodic tasks > Clean up > Work user session log cleanup | This is used to delete work user session records from WHSWorkUserSessionLog table based on number of hours to keep provided on dialog. |

 
## Inventory management

| **Module**             | **Path**                | **Description** |
|---------------------|-----------------------------|-------------------------------|
| Inventory management | Periodic tasks > Clean up > Calculation of location load | WMSLocationLoad table is used in tracking weight and volume of items and pallets. Summation of load adjustments job can be run to reduce the number of records in the WMSLocationLoad table and improve performance. |
| Inventory management | Periodic tasks > Clean up > Inventory journals cleanup | It is used to delete posted inventory journals. |
| Inventory management | Periodic tasks > Clean up > Inventory settlements cleanup | It is used to group closed inventory transactions or delete canceled inventory settlements. Cleaning up closed or deleted inventory settlements can help free system resources. <br> Do not group or delete inventory settlements too close to the current date or fiscal year, because part of the transaction information for the settlements is lost. <br> Closed inventory transactions cannot be changed after they have been grouped, because the transaction information for the settlements is lost. <br>Canceled inventory settlements cannot be reconciled with finance transactions if canceled inventory settlements are deleted. |
| Inventory management | Periodic tasks > Clean up > Inventory dimensions cleanup | This is used to maintain the InventDim table. To maintain the table, delete unused inventory dimension combination records that are not referenced by any transaction or master data. The records are deleted regardless of whether the transaction is open or closed. <br> Inventory dimension combination record that is still referenced cannot be deleted because when an InventDim record is deleted, related transactions cannot be reopened. |
| Inventory management | Periodic tasks > Clean up > Dimension inconsistency cleanup | This is used to resolve dimension inconsistencies on inventory transactions that have been financially updated and closed. Inconsistencies might be introduced when the multisite functionality was activated during or before the upgrade process. <br> Use this batch job only to clean up the transactions that were closed before the multisite functionality was activated. **Do not use this batch job periodically.** |
| Inventory management | Periodic tasks > Clean up > On-hand entries cleanup | This is used to delete closed and unused entries for on-hand inventory that is assigned to one or more tracking dimensions. Closed transactions contain the value of zero for all quantities and cost values, and are marked as closed. Deleting these transactions can improve the performance of queries for on-hand inventory. Transactions will not be deleted for on-hand inventory that is not assigned to tracking dimensions. |
| Inventory management | Periodic tasks > Clean up > Warehouse management on-hand entries cleanup | Deletes records in the InventSum and WHSInventReserve tables. These tables are used to store on-hand information for items enabled for warehouse management processing (WHS items). Cleaning up these records can lead to significant improvements of the on-hand calculations. |
| Inventory management | Periodic tasks > Clean up > On-hand entries aggregation by financial dimensions | Tool to aggregate InventSum rows with zero quantities. This is basically extending the previously mentioned cleanup tool by also cleaning up records which have field Closed set to True! <br> The reason why this is needed is basically because in certain scenarios, you might have no more quantities in InventSum for a certain combination of inventory dimensions, but there is still a value. In some cases, these values will disappear, but current design does allow values to remain from time to time. <br> If you for example use Batch numbers, each batch number (and the combined site, warehouse, etc.) creates a new record in InventSum. When the batch number is sold, you will see quantity fields are set to 0. In most cases, the Financial/Physical value field is also set to 0, but in Standard cost revaluation or other scenarios, the value field may show some amount still. This is valid, and is the way Dynamics 365 Finance and Supply Chain Management handles the costs on Financial inventory level, e.g. site level. <br> Inventory value is determined in Dynamics 365 Finance and Supply Chain Managements by records in InventSum, and in some cases Inventory transactions (InventTrans) when reporting inventory values in the past. In the above scenario, this means that when you run inventory value reports, Dynamics 365 Finance and Supply Chain Management looks (initially) at InventSum and aggregates all records to Site level, and reports the value for the item per site. <br> The data from the individual records on Batch number level are never used. The tool therefore goes through all InventSum records, finds the ones where there is no more quantity (No open quantities field is True). There is no reason to keep these records, so Dynamics 365 Finance and Supply Chain Management finds the record in InventSum for the same item which has the same Site, copies the values from the Batch number level to the Site level, and deletes the record. When you now run inventory value reports, Dynamics 365 Finance and Supply Chain Management still finds the same correct values. This reduced number of InventSum records significantly in some cases, and can have a positive impact on performance of any function which queries this table. |
| Inventory management | Periodic tasks > Clean up > Cost calculation details | Used to clean up cost calculation details. |


## Production control

| **Module**             | **Path**                | **Description** |
|---------------------|-----------------------------|-------------------------------|
| Production control | Periodic tasks > Clean up > Production journals cleanup | It is used to delete unused journals. |
| Production control | Periodic tasks > Clean up > Production orders cleanup | It is used to delete production orders that are ended. |
| Production control | Periodic tasks > Clean up > Clean up registrations | It is recommended to clean up registrations periodically. The clean-up function does not delete data that is not processed. **Make sure that you do not delete registrations that may be required later for documentation purposes.** |
| Production control | Periodic tasks > Clean up > Archive future registrations | It is used to remove future registrations from the raw registrations table. |


## Master planning

| **Module**             | **Path**                | **Description** |
|---------------------|-----------------------------|-------------------------------|
| Master planning | Master planning > Maintain plans > Plan version cleanup | Normally this cleanup is taken care of automatically. However, sometimes automatic cleanup malfunctions and orphan data remains in the system, slowing down queries and resulting in growth of the database size. A preventive run once a month, when MRP is not running, is recommended. |
