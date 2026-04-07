---
title: Modifying and deleting financial dimensions
description: Learn about renaming, suspending, and deleting financial dimensions and dimension values, including restrictions and best practices.
author: anaborges02
ms.author: aolson
ms.topic: article
ms.date: 03/26/2026
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

This article covers renaming, suspending, and deleting financial dimensions and their values.

## Renaming financial dimensions

When working with financial dimensions, you might need to rename dimension values or the dimensions themselves. However, several requirements and considerations affect your ability to rename financial dimensions and their values.

- Change entity-backed dimensions through their source entity - You can't rename entity-backed dimension values through the **Financial dimension values** page. Rename them on the corresponding entity page. For example, rename Department dimension values in the **Operating units** page where the department is defined.
- Ensure dimension value names are unique - Dimension value names must be unique across the system. To check for duplicates, go to **General ledger > Chart of accounts > Dimensions > Financial dimensions**, select the dimension, then select **Dimension values**. If a duplicate exists, choose a different name.
- Verify you have sufficient privileges - Your user account must have the necessary roles and privileges to modify dimension values. If you're unable to make changes, contact your system administrator to verify permissions.

In some cases, if a dimension value was renamed outside the standard user interface, the financial dimension value may display inconsistent naming or casing across the application. This can happen if an incorrectly cased value was imported through an Excel-based data import or if a customization changed the value name without using the supported dimension update methods, such as through a direct database modification. To address the issue, rename the dimension value using the standard rename process on the source entity page.

### Rename by primary key

Some entities—such as customers and vendors—don't support direct renaming of their identifier and instead require the **Rename primary key** option. This is because they use their account number as their primary key rather than their name.

1. Find the record to change.
2. Select **Options** > **Record info**.
3. Select **Rename Primary Key**.
4. Enter the new name and select **OK**. Acknowledge any dialogs indicating the value will be renamed.

## Deleting financial dimensions and dimension values

To protect data integrity, the system restricts deletion of both financial dimensions and their values. In most cases, neither can be deleted once they've been referenced. Instead of deleting, consider renaming or suspending:

- **Rename** the dimension or value to indicate it shouldn't be used (for example, **\_\_\_DONOTUSE\_DimensionName**). Later, when a new value is needed, you can rename and reuse the old one rather than creating a new one. Reusing existing dimension values can improve application performance.
- **Suspend** a dimension value to prevent it from being used on new transactions. Go to **General ledger** > **Chart of accounts** > **Dimensions** > **Financial dimensions**. Select the dimension, select **Dimension values**, select the value, select **Edit**, and mark it as suspended. Suspended values are hidden from lookups but can be renamed and reused later.

### When a financial dimension can't be deleted

A financial dimension can't be deleted if any of the following are true:

- It's used in any active account structure, advanced rule structure, or financial dimension set.
- It's part of a default financial dimension integration format, or is set up as a default dimension.
- It's still selected in the Financial Reporting setup.
- Any dimension value has been created for the dimension — even if the value was never used on a transaction.

> [!NOTE]
> Starting in Finance version 10.0.27, the system doesn't automatically select financial dimensions for financial reporting setup as they're created.

### When a dimension value can't be deleted

A dimension value can't be deleted if it has been used on any posted or unposted transaction, or in any dimension value combination such as a ledger account or default dimension. If deletion is still required, a thorough assessment of all data references to the value is needed before any data can be removed.

### Deleting entity-backed records used as dimension values

When you delete a record from a source entity (such as a customer, vendor, project, or bank account) that is used as a financial dimension value, the system's response depends on how the dimension value was referenced:

- **Used in a ledger account** — If the dimension value is part of any ledger account combination, deletion is blocked immediately. Deletion of this dimension value is not possible and is not supported by Microsoft.
- **Used in a default dimension, posting profile, or other non-ledger-account context** — The system runs a reference scan before allowing the deletion. Allow the scan to run to completion. If no references are found, both the entity record and its dimension value are removed. If references are found, the deletion is blocked and the system displays the transaction types that reference the record. You can remove the references found by the scan and then rerun it to delete the dimension value.

If deletion is blocked, consider renaming or suspending the value instead, as described earlier in this article.

## Financial dimension value sync

The [data maintenance portal](/dynamics365/fin-ops-core/dev-itpro/sysadmin/datamaintenanceportal) includes the **Dimension value rename and modify chart of accounts delimiter process** job under the **Misc** tab. This job keeps financial dimension values in sync with their source entity records.

If a dimension value appears to be out of sync with its source record, try manually renaming the value at the source (for example, renaming a customer or vendor record). This triggers the sync job automatically and propagates the change through the dimension framework. If the value is still out of sync after the rename, check the job status in the data maintenance portal for errors.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
