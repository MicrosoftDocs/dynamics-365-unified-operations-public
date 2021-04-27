---
# required metadata

title: What's new or changed in Dynamics 365 for Finance and Operations version 8.1.1 (November 2018)
description: This topic describes features that are either new or changed in Dynamics 365 for Finance and Operations version 8.1.1. This version was released in November 2018.
author: tonyafehr
ms.date: 10/15/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
ROBOTS: NOINDEX, NOFOLLOW 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: b364a31c-52d3-45c5-b698-64c5242c592a
ms.search.region: Global
# ms.search.industry: 
ms.author: tfehr
ms.search.validFrom: 2018-10-01 
ms.dyn365.ops.version: Release 8.1.1

---
# What's new or changed in Dynamics 365 for Finance and Operations version 8.1.1 (November 2018)

[!include [banner](../includes/banner.md)]

This topic describes features that are either new or changed in Microsoft Dynamics 365 for Finance and Operations version 8.1.1 (November 2018). This version was released in November 2018 and has a build number of 8.1.170.

To learn about the new features and changes in the latest releases of Retail, see [What's new or changed in Dynamics 365 for Retail](../../../commerce/get-started/whats-new.md).

### Announcing the Dynamics 365 October '18 release notes

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

[Check out the October '18 release notes](/dynamics365/release-plans/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

## Bug fixes

For information about the bug fixes included in each of the updates that are part of Finance and Operations version 8.1.1, sign in to Lifecycle Services (LCS) and view the [KB article](https://go.microsoft.com/fwlink/?linkid=2038101).

## Platform update 21

Microsoft Dynamics 365 for Finance and Operations version 8.1.1 includes Platform update 21. To learn more about Platform update 21, see [What's new or changed in Dynamics 365 for Finance and Operations platform update 21 (November 2018)](whats-new-platform-update-21.md).

## Ledger settlements

Ledger settlements let you match debit and credit transactions in the general ledger, and mark them as settled. In this way, you can make sure that related transactions have been cleared. You can also reverse settlements if they were made by mistake. For detailed information, see [Ledger settlements](../../../finance/general-ledger/ledger-settlements.md).

## Prevent generating offset tax transactions during tax settlement

During the tax settlement process, the system will generate offset tax transactions which can cause performance issues if there are a large number of tax transactions within a specific time period. The **Prevent generating offset tax transactions** check box has been added to the **Sales tax settlement periods** page to prevent this from happening. For more information, see [Set up sales tax settlement periods](../../../finance/general-ledger/tasks/set-up-sales-tax-settlement-periods.md).

## Extensibility enhancements

In this release of Finance and Operations, numerous extensibility enhancements have been made to support extensibility including enhancements to enumerations, metadata, and methods. For detailed information, see [Extensibility changes in Dynamics 365 for Finance and Operations version 8.1.1](../../dev-itpro/extensibility/extensibility-changes-811.md)

## VAT declaration for Russia

In this release, you can review the ER configurations for generating VAT declaration for Russia in electronic format. For detailed information, see [RUS/Russia VAT Declaration in electronic format](https://support.microsoft.com/help/4477332/rusrussiavatdeclarationinelectronicformat).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
