---
title: What's new or changed in Dynamics 365 Finance version 10.0.7 (January 2020)
description: Learn about features that are either new or changed in Dynamics 365 Finance version 10.0.7, including an outline on budget register entry enhancements.
author: kfend
ms.author: johnmichalak
ms.topic: whats-new
ms.custom:
  - bap-template
  - evergreen
ms.date: 12/02/2025
ms.update-cycle: 1095-days
ms.reviewer: kfend
ms.search.region: Global
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 10.0.7
---
# What's new or changed in Dynamics 365 Finance version 10.0.7 (January 2020)

[!include [banner](../includes/banner.md)]

This article describes features that are new or changed for Microsoft Dynamics 365 Finance, version 10.0.7. This version has a build number of 10.0.283 and is available as follows:

- Preview release is in October 2019.
- General availability (self-update) is in November 2019.
- Autoupdate is in January 2020.

For more information about Platform update 31, see [Additional resources](../../fin-ops-core/fin-ops/get-started/whats-new-platform-update-31.md#additional-resources).

## Budget register entry enhancements

The **Budget register entries for quantity only** feature enables you to post a budget register entry with quantity-only amounts. For example, you could post a budget entry of quantity 32 with a price of zero, resulting in an amount of zero. You can then use this quantity within the context of a financial reporting report to display a calculation of an amount divided by this quantity. For more information, see [Budgeting overview](../budgeting/basic-budgeting-overview-configuration.md). 

The **Budget register entries defaulting of amount type** feature enables the defaulting of amount type to revenue or expense based on the main account of the budget line. For details, see [Budgeting overview](../budgeting/basic-budgeting-overview-configuration.md) for details. 


## Ability to export records from the Accounts payable invoice pool form
This feature lets you export records from the **Accounts payable invoice pool** form to Excel. This capability makes it easier to review and analyze the grid data in Excel. 

## Ledger settlement by user

Ledger settlement now settles marked transactions by user. When you open the page, it displays only transactions that you marked for settlement or transactions that no one marked. Also, a new button clears transactions by user ID. This feature allows an accounting manager to clear transactions for a user who left on vacation before finishing the settlement or for a user who left the organization. The action frees up those transactions for another user to mark them for settlement. 

## Forecast position reports (Public Sector)

You can use the **Forecast position summary** report to generate forecast position information for a budget plan and scenario that you specify. The **Forecast position summary** report shows forecast position costs by account distributions. The forecast position costs are shown, grouped by their assigned account distributions. The cost amounts are factored by the percentage assigned to the account distribution. 

## Purchasing cards (Public Sector)

Agencies use purchasing cards so that employees can procure goods and services without using the standard purchase requisition process. The pages and fields related to purchasing cards provide a mechanism for tracking purchases. Each purchase that an employee makes by using a purchasing card is recorded on a vendor invoice. However, the invoice isn't paid by using a check or electronic payment to the vendor that provided the goods or services. Instead, each invoice of this type is associated with another vendor invoice that is created to pay the vendor that provides the purchasing card services (that is, the financial institution). The card purchases are paid off when the balance that is owed to the purchasing card services provider is paid each month.

## Mark a purchase agreement as "Closed"

You can now mark a purchase agreement as "Closed" to signal that the agreement is no longer actively used. When you close a purchase agreement, users can't create release orders from the purchase agreement.

## Delayed tax calculation on journal

This feature improves the performance of tax calculations on journals that contain a significant number of transactions. Tax amounts are calculated only when you select the **Sales Tax** command or when you post the journal. For more information, see [Enable delayed tax calculation on journal](../general-ledger/enable-delayed-tax-calculation.md).

## Reverse journal posting

This feature lets you reverse an entire posted journal or reverse one or more vouchers from the voucher transaction list regardless of their origin. For more information, see [Reverse journal posting](../general-ledger/reverse-journal-posting.md).

## Prohibit submission to workflow when there are unallocated charges on a vendor invoice
This feature lets you prevent a vendor invoice from being submitted to the workflow process when it contains unallocated charges. Instead, the person who submitted the invoice receives an alert that there are unallocated charges and lets the user make corrections before submitting it to workflow.

## Account groups selection for Chinese voucher types

This feature allows you to select accounts groups when setting up voucher types for China. 

### Enable the feature
1. Enable the feature in the **Workspaces > Feature management**.
1. This feature introduces a new table where voucher type setup is stored. To copy existing Chinese voucher type setup information to the new table, go to **System administration > Periodic tasks > Database > Consistency check**. Expand **Program > General ledger** and select **Restriction type for voucher**. 
1. Select **Check** in the **Check/Fix** field to check whether there are settings in existing setup to copy to the new table.
1. Select **Fix** in the **Check/Fix** field to copy settings from an existing table to the new table.

### Set up voucher type
1. Go to **General ledger > Journal setup > Chinese voucher type > Voucher type**.
1. Under the **Rules** FastTab, select the line with specific restriction.
1. Under the **Impacted accounts** FastTab, select **Add** and set up the accounts for the selected rule:
- In the **Account type** field, select **Ledger**, **Customer**, **Vendor**, **Project**, **Fixed assets**, or **Bank**.
- In the **Account code** field, select **Account**, **Group**, or **All**. The value **Group** isn't available for **Ledger** account code.
- In the **Group number** field, select **Customer group**, **Vendor group**, **Project group**, **Fixed asset group**, or **Bank group** to match the value in the **Account type** field, if you selected **Group** in the **Account code** field.
- In the **Account number** field, select **Ledger account**, **Customer account**, **Vendor account**, **Project ID**, **Fixed asset number**, or **Bank account value** in the **Account type** field, if you selected **Table** in the **Account code** field.


For details about how to set up Chinese voucher types, see [Set up Chinese vouchers](../localizations/china/set-up-chinese-vouchers.md).

## Sort by resource in the project invoice proposal

The **Enable sorting by resource during project invoice proposal creation** feature allows the project accountant to sort the project transactions available for billing by the resource when creating a new project invoice proposal. The grid displaying the available project transactions has a separate field for Resource ID and Resource, allowing the user to filter and sort on the resource name. This feature is disabled by default and can be enabled in **Workspaces > Feature management**.

## Run Settle and post sales tax in batch mode 

Users can now run **Settle and post sales tax** in batch mode in Italy, Belgium, and Australia. For setup information, see [Set up sales tax settlement periods](../general-ledger/tasks/set-up-sales-tax-settlement-periods.md). 

## Tax engine 

The tax engine (GTE) is currently only available for India. 

### Create tax component with predefined rules

Instead of creating a new tax component, users can now create it with predefined tax rules that support the most commonly used taxation rules like reverse charge and nondeductible. For more information, see [Create tax component](../localizations/india/tax-engine-create-tax-component.md).


## Additional resources

### Platform update 31

Microsoft Dynamics 365 Finance 10.0.7 includes Platform update 31. For more information, see [What's new and changed in Platform update 31](../../fin-ops-core/fin-ops/get-started/whats-new-platform-update-31.md).


### Bug fixes 
For information about the bug fixes included in each of the updates that are part of 10.0.7, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=386529&dbType=3&qc=e03ced97fa18dc4439f36de17b00da7257dc15869a72e5b2435fec0acec0c493).


### Dynamics 365: 2019 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2019 release wave 2 plan](/dynamics365-release-plan/2019wave2/index). We captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features](../../fin-ops-core/dev-itpro/migration-upgrade/deprecated-features.md) article describes features that are removed or deprecated for Dynamics 365 Finance.

- A *removed* feature isn't available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

Before removing any feature from the product, the deprecation notice is announced in the [Removed or deprecated features in Dynamics 365 Finance](../get-started/removed-deprecated-features-finance.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time but are binary compatible with sandbox and production environments, the deprecation time is less than 12 months. Typically, these changes are functional updates that you need to make to the compiler.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]

