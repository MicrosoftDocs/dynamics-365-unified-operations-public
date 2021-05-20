---
# required metadata

title: What's new or changed in Dynamics 365 Finance version 10.0.7 (January 2020)
description: This topic describes features that are either new or changed in Dynamics 365 Finance version 10.0.7.
author: roschlom
ms.date: 12/05/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: roschlom
ms.search.validFrom: 2019-10-31 
ms.dyn365.ops.version: 10.0.7

---
# What's new or changed in Dynamics 365 Finance version 10.0.7 (January 2020)

[!include [banner](../includes/banner.md)]

This topic describes features that are new or changed for Microsoft Dynamics 365 Finance, version 10.0.7. This version has a build number of 10.0.283 and is available as follows:

- Preview release is in October 2019.
- General availability (self-update) is in November 2019.
- Auto-update is in January 2020.

For more information about Platform update 31, see [Additional resources](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-update-31.md#additional-resources).

## Budget register entry enhancements

The **Budget register entries for quantity only** feature enables the ability to post a budget register entry with quantity-only amounts. For example, you could post a budget entry of quantity 32 with a price of zero, resulting in an amount of zero. You can then use this quantity within the context of a financial reporting report to display a calculation of an amount divided by this quantity. For more information, see [Budgeting overview](../budgeting/basic-budgeting-overview-configuration.md). 

The **Budget register entries defaulting of amount type** feature enables the defaulting of amount type to revenue or expense based on the main account of the budget line. For details, see [Budgeting overview](../budgeting/basic-budgeting-overview-configuration.md) for details. 


## Ability to export records from the Accounts payable invoice pool form
This feature lets you export records from the **Accounts payable invoice pool** form to Excel. This capability makes it easier to review and analyze the grid data in Excel. 

## Ledger settlement by user

Ledger settlement will now settle marked transactions by user.  When opening the page, only transactions marked by the user for settlement or transactions not marked by anyone will display. Also, a new button has been introduced to clear transactions by user ID.  This will allow an accounting manager to clear transactions for a user who might have left on vacation before finishing the settlement or for a user who has left the organization. The action will free up those transactions for another user to mark them for settlement. 

## Forecast position reports (Public Sector)

You can use the **Forecast position summary** report to generate forecast position information for a budget plan and scenario that you specify. The **Forecast position summary** report shows forecast position costs by account distributions. The forecast position costs are shown, grouped by their assigned account distributions. The cost amounts are factored by the percentage assigned to the account distribution. 

## Purchasing cards (Public Sector)

Agencies use purchasing cards so that employees can procure goods and services without using the standard purchase requisition process. The pages and fields that are related to purchasing cards provide a mechanism for tracking purchases. Each purchase that an employee makes by using a purchasing card is recorded on a vendor invoice. However, the invoice isn't paid by using a check or electronic payment to the vendor that provided the goods or services. Instead, each invoice of this type is associated with another vendor invoice that is created to pay the vendor that provides the purchasing card services (that is, the financial institution). The card purchases are paid off when the balance that is owed to the purchasing card services provider is paid each month.

## Mark a purchase agreement as "Closed"

Users can now mark a purchase agreement as "Closed" to signal that the agreement is no longer actively used, making it so users will not be able to create release orders from the purchase agreement.

## Delayed tax calculation on journal

This feature improves the performance of tax calculations on journals when that contain a significant number of transactions. Tax amounts will only be calculated when you click the **Sales Tax** command or when you post the journal when this feature is enabled. For more information, see [Enable delayed tax calculation on journal](../general-ledger/enable-delayed-tax-calculation.md).

## Reverse journal posting

This feature lets you reverse an entire posted journal or reverse one or more vouchers from the voucher transaction list regardless of their origin. For more information, see [Reverse journal posting](../general-ledger/reverse-journal-posting.md).

## Prohibit submission to workflow when there are unallocated charges on a vendor invoice
This feature lets you prevent a vendor invoice from being submitted to the workflow process when it contains unallocated charges. Instead, the person who submitted the invoice receives an alert that there are unallocated charges and lets the user make corrections before submitting it to workflow.

## Account groups selection for Chinese voucher types

This feature allows you to select accounts groups when setting up voucher types for China. 

### Enable the feature
1. Enable the feature in the **Workspaces > Feature management**.
2. This introduces a new table where voucher type setup is stored. To copy existing Chinese voucher type setup information to a new table, go to **System administration > Periodic tasks > Database > Consistency check**. Expand **Program > General ledger** and select **Restriction type for voucher**. 
3. Select **Check** in the **Check/Fix** field to check whether there are settings in existing setup to copy to a new table.
4. Select **Fix** in the **Check/Fix** field to copy settings from an existing table to a new table.

### Set up voucher type
1. Go to **General ledger > Journal setup > Chinese voucher type > Voucher type**.
2. Under the **Rules** FastTab, select the line with specific restriction.
3. Under the **Impacted accounts** FastTab, click **Add** and set up the accounts for the selected rule:
- In the **Account type** field, select **Ledger**, **Customer**, **Vendor**, **Project**, **Fixed assets**, **Bank**
- In the **Account code**, select **Account**, **Group**, or **All**. Note that the value **Group** is not available for **Ledger** account code.
- In the **Group number** field, select **Customer group**, **Vendor group**, **Project group**, **Fixed asset group**, or **Bank group** to match the value in the **Account type** field, if you selected **Group** in the **Account code** field.
- In the **Account number** field, select **Ledger account**, **Customer account**, **Vendor account**, **Project ID**, **Fixed asset number**, or **Bank account value** in the **Account type** field, if you selected **Table** in the **Account code** field.


For details about how to set up Chinese voucher types, see [Set up Chinese vouchers](../localizations/tasks/set-up-chinese-vouchers.md).

## Sort by resource in the project invoice proposal

The **Enable sorting by resource during project invoice proposal creation** feature allows the project accountant to sort the project transactions available for billing by the resource when creating a new project invoice proposal. The grid displaying the available project transactions will have a separate field for Resource ID and Resource, allowing the user to filter and sort on the resource name. This feature is disabled by default and can be enabled in **Workspaces > Feature management**.

## Run Settle and post sales tax in batch mode 

Users can now run **Settle and post sales tax** in batch mode in Italy, Belgium, and Australia. Refer to [Set up sales tax settlement periods](../general-ledger/tasks/set-up-sales-tax-settlement-periods.md) for setup information. 

## Tax engine 

The tax engine (GTE) is currently only available for India. 

### Create tax component with pre-defined rules

Instead of creating a new tax component, users can now create it with predefined tax rules that support the most commonly used taxation rules like reverse charge and non-deductible. For more information, see [Create tax component](../localizations/tax-engine-create-tax-component.md).


## Additional resources

### Platform update 31

Microsoft Dynamics 365 Finance 10.0.7 includes Platform update 31. To learn more, see [What's new and changed in Platform update 31](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-update-31.md).


### Bug fixes 
For information about the bug fixes included in each of the updates that are part of 10.0.7, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=386529&dbType=3&qc=e03ced97fa18dc4439f36de17b00da7257dc15869a72e5b2435fec0acec0c493).


### Dynamics 365: 2019 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2019 release wave 2 plan](/dynamics365-release-plan/2019wave2/index). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features](../../fin-ops-core/dev-itpro/migration-upgrade/deprecated-features.md) topic describes features that have been removed or deprecated for Dynamics 365 for Finance and Operations.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features](../../fin-ops-core/dev-itpro/migration-upgrade/deprecated-features.md) topic 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]