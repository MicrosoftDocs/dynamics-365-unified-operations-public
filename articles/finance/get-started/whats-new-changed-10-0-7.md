---
# required metadata

title: Preview features in Dynamics 365 Finance 10.0.7 (December 2019)
description: This topic describes features that are either new or changed in Dynamics 365 Finance 10.0.7.
author: roschlom
manager: AnnBe
ms.date: 10/21/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope:  Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: roschlom
ms.search.validFrom: 2019-10-31 
ms.dyn365.ops.version: 10.0.7

---
# Preview features in Dynamics 365 Finance 10.0.7 (December 2019)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic describes features that are either new or changed in Microsoft Dynamics 365 Finance 10.0.7. This version has a build number of XX.X.XXX. While the general availability date is in November, the new features are available for early release in October. For more information about version 10.0.7, see [Additional resources](../../fin-and-ops/get-started/whats-new-changed-10-0-7.md#additional-resources).

## Budget register entry enhancements

The **Budget register entries for quantity only** feature enables the ability to post a budget register entry with quantity-only amounts. For example, you could post a budget entry of 32 quantity with a price of zero, resulting in an amount of zero. You may then use this quantity within the context of a financial reporting report to display a calculation of an amount devided by this quantity. See [budgeting overview](.../https://docs.microsoft.com/en-us/dynamics365/finance/budgeting/basic-budgeting-overview-configuration.md) for details. 

The **Budget register entries defaulting of amount type** feature enables the defaulting of amount type to revenue or expense based on the main account of the budget line. See [budgeting overview](.../https://docs.microsoft.com/en-us/dynamics365/finance/budgeting/basic-budgeting-overview-configuration.md) for details. 


## Ability to export records from the Accounts payable invoice pool form
This feature lets you export records from the **Accounts payable invoice pool** form to Excel. This capability provides a productive environment to review and analyze the grid data in Excel. 

## Ledger settlement by user

Ledger settlement will now settle marked transactions by user.  When opening the page, only transactions marked by the user for settlement or transactions not marked by anyone will display. Also, a new button has been introduced to unmark transaction by user ID.  This will allow an accounting manager to unmark transactions for a user that left on vacation before finishing the settlement or for a user who has left the organization.  The action will free up those transactions for another user to mark them for settlement. 


## Forecast position reports (Public Sector)

You can use the **Forecast position summary** report to generate forecast position information for during a budget plan and scenario that you specify.  The **Forecast position summary** report shows forecast position costs by account distributions. The forecast position costs are shown, grouped by their assigned account distributions. The cost amounts are factored by the percentage assigned to the account distribution. 

## Purchasing cards (Public Sector)

Agencies use purchasing cards so that employees can procure goods and services without using the standard purchase requisition process. The pages and fields that are related to purchasing cards provide a mechanism for tracking purchases. Each purchase that an employee makes by using a purchasing card is recorded on a vendor invoice. However, the invoice isn't paid by using a check or electronic payment to the vendor that provided the goods or services. Instead, each invoice of this type is associated with another vendor invoice that is created to pay the vendor that provides the purchasing card services (that is, the financial institution). The card purchases are paid off when the balance that is owed to the purchasing card services provider is paid each month.

## Delayed tax calculation on journal

This feature improves the performance of tax calculations on journals when the they contain a significant number of transactions. Tax amounts will only be calculated when you click the **Sales Tax** command or when you post the journal when this feature is enabled. For more information, see [Enable delayed tax calculation on journal](../general-ledger/enable-delayed-tax-calculation.md) for details.

## Reverse journal posting

This feature lets you reverse an entire posted journal or reverse one or more vouchers from the voucher transaction list regardless of their origin. Please refer to [Reverse journal posting](../general-ledger/reverse-journal-posting.md) for details.

## Prohibit submission to workflow when there are unallocated charges on a vendor invoice
This feature lets you prevent a vendor invoice from being submitted to the workflow process when it contains unallocated charges. Instead, the person who submitted the invoice receives an alert that it has unallocated charges and lets them correct it before submitting it to workflow.

