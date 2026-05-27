---
title: Modifying and deleting financial dimensions
description: Learn about renaming, suspending, and deleting financial dimensions and dimension values, including restrictions and best practices.
author: anaborges02
ms.author: aolson
ms.topic: article
ms.date: 05/11/2026
ms.custom: evergreen
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2018-10-31
ms.search.form: DimensionDetails, DimensionValueDetails
ms.dyn365.ops.version: 8.1
---

# Modifying and deleting financial dimensions

[!include [banner](../includes/banner.md)]

This article explains how to rename, suspend, and delete financial dimensions and their values.

## Renaming financial dimensions

When you work with financial dimensions, you might need to rename dimension values or the dimensions themselves. However, several requirements and considerations affect your ability to rename financial dimensions and their values.

- Change entity-backed dimensions through their source entity - You can't rename entity-backed dimension values through the **Financial dimension values** page. Rename them on the corresponding entity page. For example, rename Department dimension values in the **Operating units** page where the department is defined.
- Ensure dimension value names are unique - Dimension value names must be unique across the system. To check for duplicates, go to **General ledger > Chart of accounts > Dimensions > Financial dimensions**, select the dimension, and then select **Dimension values**. If a duplicate exists, choose a different name.
- Verify you have sufficient privileges - Your user account must have the necessary roles and privileges to modify dimension values. If you can't make changes, contact your system administrator to verify permissions.

In some cases, if you rename a dimension value outside the standard user interface, the financial dimension value might display inconsistent naming or casing across the application. This inconsistency can happen if you import an incorrectly cased value through an Excel-based data import or if a customization changed the value name without using the supported dimension update methods, such as through a direct database modification. To address the issue, rename the dimension value to a temporary value by using the standard rename process on the source entity page, wait for the rename data maintenance to finish, and then rename it back to the original value.

### Rename by primary key

Some entities, such as customers and vendors, don't support direct renaming of their identifier and instead require the **Rename primary key** option. These entities use their account number as their primary key rather than their name.

1. Find the record to change.
1. Select **Options** > **Record info**.
1. Select **Rename Primary Key**.
1. Enter the new name and select **OK**. Acknowledge any dialogs indicating the value is renamed.

## Deleting financial dimensions and dimension values

To protect data integrity, the system restricts deletion of both financial dimensions and their values. In most cases, you can't delete these elements once they're referenced. Instead of deleting, consider renaming or suspending:

- **Rename** the dimension or value to indicate it shouldn't be used (for example, **\_\_\_DONOTUSE\_DimensionName**). When you need a new value, you can rename and reuse the old one rather than creating a new one. Reusing existing dimension values can improve application performance.
- **Suspend** a dimension value to prevent it from being used on new transactions. Go to **General ledger** > **Chart of accounts** > **Dimensions** > **Financial dimensions**. Select the dimension, select **Dimension values**, select the value, select **Edit**, and mark it as suspended. Suspended values are hidden from lookups but can be renamed and reused later.

### When you can't delete a financial dimension

You can't delete a financial dimension once you use it in any of the following, even if you later remove the reference:

- An account structure, advanced rule structure, financial dimension set, or dimension value combination.
- A default financial dimension integration format, or as a default dimension (for example, ledger setup, module parameters, or posting profiles).
- The Financial Reporting setup.
- Any dimension value created for the dimension - even if you never used the value on a transaction.

The system enforces this restriction even when:

- No posted transactions exist.
- Journals were never posted.
- You created and later removed records.
- You later removed the dimension from the account structure.

This behavior is by design and preserves reporting accuracy and audit integrity for the historical periods in which the dimension participated. To retire a dimension you no longer need, rename or suspend it as described earlier in this article.

The system doesn't automatically select financial dimensions for financial reporting setup as you create them.

### When you can't delete a dimension value

You can't delete a dimension value if it's used on any posted or unposted transaction, or in any dimension value combination such as a ledger account or default dimension. If you still need to delete the value, thoroughly assess all data references to the value before removing any data.

### Deleting entity-backed records used as dimension values

When you delete a record from a source entity (such as a customer, vendor, project, or bank account) that is used as a financial dimension value, the system's response depends on how the dimension value was referenced:

- **Used in a ledger account** – If the dimension value is part of any ledger account combination, deletion is blocked immediately. Deletion of this dimension value isn't possible and isn't supported by Microsoft.
- **Used in a default dimension, posting profile, or other non-ledger-account context** – The system runs a reference scan before it allows the deletion. While the scan is in progress, you might see a message such as "The \<EntityType> '\<RecordName>' is currently being checked for references before it can be deleted. It can't be deleted until the process is complete." This message is expected - the scan runs as a background job and the deletion is held until it finishes. To check whether the scan finished, go to **System administration** > **Periodic tasks** > **Data maintenance**. Select the **Misc** tab, and then select **Include system actions**. Find the **Process pending requests for validation for deleting a value** data maintenance action and review its execution logs for errors. The **Last status** column shows **Completed** when the run finished successfully.

    If the scan doesn't find any references, both the entity record and its dimension value are removed. If the scan finds references, the deletion is blocked and the system displays the transaction types that reference the record. You can remove the references found by the scan and then rerun it to delete the dimension value.

If deletion is blocked, consider renaming or suspending the value instead, as described earlier in this article.

Selecting multiple records on a list page (for example, fixed assets, customers, or vendors) and choosing **Delete** still runs the reference scan one record at a time. For high-volume cleanup, use the entity's standard retire, inactivate, or suspend flow instead of bulk delete. If you require a deletion-only outcome at volume, contact support.

## Financial dimension value sync

The [data maintenance portal](/dynamics365/fin-ops-core/dev-itpro/sysadmin/datamaintenanceportal) includes the **Dimension value rename and modify chart of accounts delimiter process** job under the **Misc** tab. This job keeps financial dimension values in sync with their source entity records.

If a dimension value appears to be out of sync with its source record, try manually renaming the value at the source (for example, renaming a customer or vendor record). This action automatically triggers the sync job and propagates the change through the dimension framework. If the value is still out of sync after the rename, check the job status in the data maintenance portal for errors.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
