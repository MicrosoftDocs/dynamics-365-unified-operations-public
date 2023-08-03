---
# required metadata

title: Clean up source data for upgrade from Microsoft Dynamics AX 2012 to Dynamics 365 Finance + Operations
description: This article describes how to clean up source data as part of an upgrade from Microsoft Dynamics AX 2012 to Dynamics 365 Finance + Operations (on-premises).
author: ttreen 
ms.date: 07/10/2022
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: ttreen
ms.search.validFrom: 
ms.search.form: 2022-04-08

---

# Clean up source data for upgrade from Microsoft Dynamics AX 2012 to Dynamics 365 Finance + Operations

[!include [banner](../includes/banner.md)]

This article describes how to clean up source data as part of an upgrade from Microsoft Dynamics AX 2012 to Dynamics 365 Finance + Operations (on-premises).

> [!IMPORTANT]
> Any cleanup routine should be run only after the business has done detailed analysis and confirmed that the data is no longer required.
>
> Always test each cleanup routine in a test environment before you run it in a production environment.

## Background

Over time, the Dynamics AX 2012 database can grow to a large size. Before the upgrade, you can reduce the size of the database by purging or archiving data. In this way, you can help reduce the time that is required to complete the data upgrade.

There are several tools and processes that you can use to clean up data:

- [Dynamics AX Intelligent Data Management Framework tool](#dynamics-ax-intelligent-data-management-framework-tool)
- [Cleanup routines in Microsoft Dynamics AX 2012](#cleanup-routines-in-microsoft-dynamics-ax-2012)
- [Manual cleanup](#manual-cleanup)

## Dynamics AX Intelligent Data Management Framework tool

Although the Dynamics AX Intelligent Data Management Framework (IDMF) tool is no longer being updated, you can use it to archive or purge data in the Dynamics AX 2012 database. For more information, see [Dynamics AX Intelligent Data Management Framework](/dynamicsax-2012/appuser-itpro/microsoft-dynamics-ax-intelligent-data-management-framework-idmf).

## Cleanup routines in Microsoft Dynamics AX 2012

In Dynamics AX 2012, cleanup routines are available in various modules. The following information provides an overview of the routines that are currently available, to help you clean up data before the upgrade. The information is organized by module.

### System administration

| Path | Description |
|------|-------------|
| System administration \> Periodic tasks \> Notification clean up | <p>This cleanup routine is used to periodically delete records from the EventInbox and EventInboxData tables.</p><p>**Recommendation:** If you don't use alert functionality, turn off the alert from the batch job.</p> |
| <ol><li>Go to **System administration** \> **Inquiries** \> **Users**.</li><li>Select **Clean up**.</li></ol> | <p>Delete user logs that are older than a specific date. This cleanup routine checks for logs that are more than three months old. User logs record user sign-in and sign-out.</p><ol><li>In the **History limit (days)** field, enter a value to define a limit for the deletion. Only log information that is older than the specified number of days is deleted.</li><li>Select **Select** to open the **Select log cleanup criteria** page, which is a version of the **Inquiry** page.</li><li>Select cleanup criteria. Select a user or a range of users, and optionally select additional user information, such as a date and time.</li><li>Select **OK** to return to the **User log cleanup** page.</li><li>Select **OK** to perform the cleanup once, or select the **Batch** tab to define parameters for regular cleanup of the user log.</li></ol> |
| System administration \> Inquiries \> Database \> Database Log \> Clean up log | <p>This cleanup routine lets you delete database logs as you require. You can delete logs for specific tables, delete specific types of database logs, or delete logs based on the date and time when they were created.</p><p>**Note:** Records that have been electronically signed can't be deleted from logs.</p> |
| <ol><li>Go to **System administration** \> **Inquiries** \> **Database** \> **SQL statement trace log**.</li><li>Select **Functions** \> **Clear log**.</li></ol> | Delete the SQL statement trace log to recover database space. This cleanup routine is an "all or nothing" option. You can export the log before you delete it, for later reference. The SQL statement trace log is a record of queries over a specific time threshold or SQL errors that are used for troubleshooting purposes. |
| System administration \> Periodic \> Services and application integration framework \> History | <ol><li>In the **Display by** field, select **Document**.</li><li>Select a document, and then select **Clear document XML**.</li><li>To clear all versions of the XML document that exist in the system, select **Clear all versions**.</li><li>To clear all intermediate versions of the XML document, select **Clear interim versions**. For outbound documents, this action clears all versions except the version that has the highest version number. For inbound documents, it clears all versions except the first version.</li></ol><p>**Recommendation:** Clean up all history that is more than one year old.</p> |

### Data Import Export Framework

| Path | Description |
|------|-------------|
| Data Import Export Framework \> Periodic \> Staging Cleanup | This cleanup routine cleans up staging data, based on the entity, processing group, or job ID. |

### Organization administration

| Path | Description |
|------|-------------|
| Organization administration \> Periodic \> Calendar cleanup | Use the page to specify the end date for deleting old working times. All old working hours up to, but not including, the specified date are deleted.|

### General ledger

| Path | Description |
|------|-------------|
| General ledger \> Periodic tasks \> Clean up ledger journals | <p>This cleanup routine deletes General ledger, Accounts receivable, and Accounts payable journals that have been posted. When you delete a posted ledger journal, all information that is related to the original transaction is removed.</p><p>**Note:** You should delete this information only if you're sure that you won't have to reverse the ledger journal transactions.</p><p>Main article: [Delete posted ledger journals](/dynamicsax-2012/appuser-itpro/delete-posted-ledger-journals)</p> |

### Sales and marketing

| Path | Description |
|------|-------------|
| Sales and marketing \> Periodic tasks \> Clean up \> Delete orders | This cleanup routine deletes selected sales orders. |
| Sales and marketing \> Periodic tasks \> Clean up \> Delete quotations | This cleanup routine deletes selected quotations. |
| Sales and marketing \> Periodic tasks \> Clean up \> Delete return orders | This cleanup routine deletes selected return orders. |
| Sales and marketing \> Periodic tasks \> Clean up \> Sales update history cleanup | <p>This cleanup routine deletes old update history transactions. All updates of confirmations, picking lists, packing slips, and invoices generate update history transactions. You can view these transactions on the **History on update** page.</p><p>Main article: [Delete the update history of purchase or sales orders](/dynamicsax-2012/appuser-itpro/delete-the-update-history-of-purchase-or-sales-orders)</p>|

### Procurement and sourcing

| Path | Description |
|------|-------------|
| Procurement and sourcing \> Periodic tasks \> Clean up \> Purchase update history cleanup | <p>This cleanup routine is used to delete all updates of confirmations, picking lists, product receipts, and invoices that generate update history transactions. </p><p>Main article: [Delete the update history of purchase or sales orders](/dynamicsax-2012/appuser-itpro/delete-the-update-history-of-purchase-or-sales-orders)</p> |
| Procurement and sourcing \> Periodic tasks \> Clean up \> Delete requests for quotations | This cleanup routine is used to delete requests for quotation (RFQs) and RFQ replies. The corresponding RFQ journals aren't deleted but remain in the system. |

### Warehouse management

| Path | Description |
|------|-------------|
| Warehouse management \> Periodic tasks \> Cleanup \> Work creation history purge | This cleanup routine is used to delete work creation history records from the WHSWorkCreateHistorytable table. In the dialog box, you specify the number of days to keep the history. |
| Warehouse management \> Periodic tasks \> Cleanup \> Containerization history purge | This cleanup routine is used to delete containerization history from the WHSContainerizationHistory table. In the dialog box, you specify the number of days to keep the history. |
| Warehouse management \> Periodic tasks \> Cleanup \> Wave batch cleanup | This cleanup routine is used to clean up batch job history records that are related to the wave processing batch group. |
| Warehouse management \> Periodic tasks \> Cleanup \> Cycle count plan cleanup | This cleanup routine is used to clean up batch job history records that are related to cycle count plan configurations. |
| Warehouse management \> Periodic tasks \> Cleanup \> Mobile device activity log cleanup | This cleanup routine is used to delete mobile device activity log records from the WHSMobileDeviceActivityLog table. In the dialog box, you specify the number of days to keep the history. |
| Warehouse management \> Periodic tasks \> Clean up \> Work user session log cleanup | This cleanup routine is used to delete work user session records from the WHSWorkUserSessionLog table. In the dialog box, you specify the number of hours to keep records. |

### Inventory management

| Path | Description |
|------|-------------|
| Inventory management \> Periodic tasks \> Clean up \> Summation of load adjustments | The WMSLocationLoad table is used to track the weight and volume of items and pallets. The **Summation of load adjustments** job can be run to reduce the number of records in the WMSLocationLoad table and help improve performance. |
| Inventory management \> Periodic tasks \> Clean up \> Inventory journals cleanup | <p>This cleanup routine is used to delete posted inventory journals.</p><p>Main article: [Delete posted inventory journals](/dynamicsax-2012/appuser-itpro/delete-posted-inventory-journals)</p> |
| Inventory management \> Periodic tasks \> Clean up \> Inventory settlements cleanup | <p>This cleanup routine is used to group closed inventory transactions or delete canceled inventory settlements. By cleaning up closed or deleted inventory settlements, you can help free up system resources.</p><p>Don't group or delete inventory settlements that are too close to the current date or fiscal year, because part of the transaction information for the settlements will be lost.</p><p>Closed inventory transactions can't be changed after they have been grouped, because the transaction information for the settlements will be lost.</p><p>If canceled inventory settlements are deleted, they can't be reconciled with finance transactions.</p> |
| Inventory management \> Periodic tasks \> Clean up \> Inventory dimensions cleanup | <p>This cleanup routine is used to maintain the InventDim table. The batch process deletes all existing inventory dimensions that are defined but not used in the current company. All unused inventory dimensions are permanently deleted. No alert or database log is created during this process.</p><p>This cleanup routine verifies whether each InventDim record is being used not only on purchase order lines or sales order lines, but also in inventory transactions or on-hand inventory records. If a reference exists to InventDim, it's checked. If it isn't used, it will be deleted. If the same combination of dimensions is used later, Dynamics 365 Finance and Dynamics 365 Supply Chain Management will create a new InventDim record that has a new **InventDimId** value, and will use that record instead.</p> |
| Inventory management \> Periodic tasks \> Clean up \> Dimension inconsistency cleanup | <p>This cleanup routine is used to resolve dimension inconsistencies on inventory transactions that have been financially updated and closed. Inconsistencies might be introduced if the multisite functionality was activated during or before the upgrade process.</p><p>Use this routine only to clean up the transactions that were closed before the multisite functionality was activated.</p><p>**Note:** Don't use this routine periodically.</p> |
| Inventory management \> Periodic tasks \> Clean up \> On-hand entries cleanup | <p>This cleanup routine is used to delete closed and unused entries for on-hand inventory that is assigned to one or more tracking dimensions. Closed transactions contain a value of **0** (zero) for all quantities and cost values, and they are marked as closed. By deleting these transactions, you can help improve the performance of queries for on-hand inventory. Transactions won't be deleted for on-hand inventory that isn't assigned to tracking dimensions.</p><p>Main article: [Clean up closed and unused on-hand inventory transactions](/dynamicsax-2012/appuser-itpro/clean-up-closed-and-unused-on-hand-inventory-transactions)</p> |
| Inventory management \> Periodic tasks \> Clean up \> Warehouse management on-hand entries cleanup | This cleanup routine deletes records in the InventSum and WHSInventReserve tables. These tables are used to store on-hand information for items that are enabled for warehouse management processing (that is, WHS items). By cleaning up these records, you can significantly improve the on-hand calculations. |
| Inventory management \> Periodic tasks \> Clean up \> On-hand entries aggregation by financial dimensions | <p>Use this cleanup routine as a tool to aggregate InventSum rows that have 0 (zero) quantities. This routine extends the previously mentioned routine by also cleaning up records where the **Closed** field is set to **True**.</p><p>This routine is needed for scenarios where there are no more quantities in the InventSum table for a combination of inventory dimensions, but there is still a value. Although these values will disappear in some cases, the current design occasionally allows values to remain.</p><p>For example, if you use batch numbers, each batch number (and the combined site, warehouse, and so on) creates a new record in the InventSum table. When the batch number is sold, quantity fields are set to **0** (zero). In most cases, the **Financial cost amount** and **Physical cost amount** fields are also set to **0** (zero). However, in standard cost revaluation and other scenarios, the field might still show some amount. This behavior is valid and reflects the way that Finance and Supply Chain Management handle the costs at the financial inventory level (for example, the site level).</p><p>In Finance and Supply Chain Management, inventory value is determined by records in the InventSum table. In some cases, when inventory values in the past are reported, inventory value is determined by inventory transactions (the InventTrans table). Therefore, in the previously described scenario, when you run inventory value reports, Finance and Supply Chain Management initially look at the InventSum table, aggregate all records to the site level, and report the value for the item per site.</p><p>The data from the individual records at the batch number level is never used. Therefore, this routine goes through all InventSum records and finds the records where there is no more quantity (that is, the **No open quantities** field is set to **True**). Because there is no reason to keep these records, Finance and Supply Chain Management find the InventSum record for the same item that has the same site, copy the values from the batch number level to the site level, and delete the record. Then, when you run inventory value reports, Finance and Supply Chain Management still find the same correct values. Therefore, this routine reduces, significantly in some cases, the number of InventSum records and can have a positive impact on the performance of any function that queries that table.</p> |
| Inventory management \> Periodic tasks \> Clean up \> Cost calculation details | This cleanup routine is used to clean up cost calculation details. |

### Production control

| Path | Description |
|------|-------------|
| Production control \> Periodic tasks \> Clean up \> Clean up registrations | <p>We recommend that you periodically clean up registrations. This cleanup routine deletes only data that has been processed.</p><p>**Note:** Make sure that you don't delete registrations that might be required later for documentation purposes.</p> |
| Production control \> Periodic tasks \> Clean up \> Archive future registrations | This cleanup routine is used to remove future registrations from the raw registrations table. |
| Production control \> Periodic tasks \> Clean up \> Production journals cleanup | This cleanup routine is used to delete unused journals. |
| Production control \> Periodic tasks \> Clean up \> Production orders cleanup | This cleanup routine is used to delete production orders that are ended. |
| Production control \> Inquiries \> Registrations \> Raw registrations archive | <p>Previously archived time registrations can be cleaned up. You can remove archived registrations by deleting them or exporting them to a file.</p><ol><li>Select **Clean up registrations**.</li><li>In the **Cleanup mode** field, select one of the following values to specify how old registrations should be handled:<ul><li>**To file** – Move the registrations to an external file.</li><li>**Delete** – Permanently delete the registrations.</li></ul></li><li>In the **Maximum age** field, enter the maximum age, in days, of registrations that are kept in the raw registrations table. For example, if you enter **20**, all registrations that are more than 20 days old are archived according to your selection in the **Cleanup mode** field.</li><li>If you selected **To file** in the **Cleanup mode** field, enter a file name or select an existing file in the **File name** field.</li></ol> |

### Master planning

| Path | Description |
|------|-------------|
| Master planning \> Periodic \> Plans \> Delete plan | Use the **Delete plan** process to delete the current scheduling results in the selected plan. Only the data (requirements and planned orders) are deleted, not the plan itself or the configuration of the plan. |

### Project management and accounting

| Path | Description |
|------|-------------|
| <ol><li>Go to **Project management and accounting** \> **Periodic** \> **Journals** \> **Delete project journals**.</li><li>On the **Delete project journals** page, select **Select**.</li><li>In the **Criteria** field, select the journals to delete.</li><li>Select **OK**.</li></ol> | You can delete project journals that transactions have been posted from. In this way, you can make more system resources available. |
| <ol><li>Go to **Project management and accounting** \> **Periodic** \> **Quotations** \> **Delete quotations**.</li><li>On the **Delete quotations** page, select **Select**.</li><li>Select **OK** to transfer the quotations to the **Delete quotations** page.</li><li>If there are any query transfers quotations that you don't want to delete, select them on the **Delete quotations** page, and then select **Alt**+**F9**. The quotations are removed from the list of quotations that will be deleted.</li><li>Select **OK** to delete the quotations that are listed on the **Delete quotations** page.</li></ol> | By deleting unsent project quotations, you can recover database space. You can create a filter to delete only selected quotations. Note that you can't delete quotations that have been sent unless you first update the status to **Lost** or **Cancelled**. |

### Human resources

| Path | Description |
|------|-------------|
| <ol><li>Go to **Human resources** \> **Periodic** \> **Absence** \> **Delete absence journals**.</li><li>Follow one of these steps:<ul><li>Select **OK** to delete all absence journals.</li><li>Select **Select** to select the employees to delete absence journals for.</li></ul></li></ol> | Use the **Delete absence journals** process to delete all empty journals that haven't been transferred for approval. Exceptions to this rule are empty journals that contain a period that is before a journal that contains planned, or future, absences. If planned absences exist in a future period, but you still want to delete the journal, cancel the approval, and repeat the journal deletion procedure. |

## Manual cleanup

Data can be cleaned directly in the database via a SQL script or through custom X++ code. These scripts must be developed and tested per customer.

### Clean up batch job history tables (Manual cleanup)

You can fully or partially clean the following tables. There are no out-of-box clean-up scripts for these tables.

- BatchJobHistory
- BatchHistory
- BatchConstraintsHistory
