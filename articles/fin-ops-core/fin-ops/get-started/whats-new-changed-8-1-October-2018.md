---
title: What's new or changed in Dynamics 365 Finance and Operations version 8.1 (October 2018)
description: This article describes features that are either new or changed in Dynamics 365 Finance and Operations version 8.1. This version was released in October 2018.
author: sericks007
ms.date: 10/15/2019
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: sericks
ms.search.validFrom: 2018-10-01
ms.dyn365.ops.version: Release 8.1
ms.custom: 
ms.assetid: b264a51c-52d1-45c5-b698-64c5242c592a
ROBOTS: NOINDEX, NOFOLLOW
---
# What's new or changed in Dynamics 365 Finance and Operations version 8.1 (October 2018)

[!include [banner](../includes/banner.md)]

This article describes features that are either new or changed in Microsoft Dynamics 365 Finance and Operations version 8.1 (October 2018). This version was released in October 2018 and has a build number of 8.1.136.

To learn about the new features and changes in the latest releases of Retail, see [What's new or changed in Dynamics 365 for Retail](../../../commerce/get-started/whats-new.md).

### Announcing the Dynamics 365 October '18 release notes

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

[Check out the October '18 release notes](/dynamics365/release-plans/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

## Use shared number sequences to copy customers or vendors

You can use shared number sequences to assign customer IDs or vendor IDs. Shared number sequences also let you copy customers or vendors from one legal entity to another legal entity but use the same IDs in both legal entities.

For additional details, see [Copy customers by using shared number sequences](../../../finance/accounts-receivable/copy-customer.md) and [Copy vendors by using shared number sequences](../../../finance/accounts-payable/vendor-copy.md).

## Customer transactions list page

The **View settlements** button on the Action Pane provides quick access to the settlement history and more information about the whole settlement transaction. You can also show additional transactions that are related to the selected transaction, either because they were part of the same settlement or because they are payments that were created in the same payment journal.

The **Global transactions** button has been added to the customer page. This button lets you view all transactions for a customer across all legal entities. The **Customer transactions** list page shows transactions only for the legal entities that the user has access to, based on their security settings.

The filter for showing open transactions has been replaced with a new filter that lets you view more combinations of transactions.

You can also update due dates and discount dates for open customer transactions, and you can add due dates to the **Customer transactions** list page.

For more information, see [Customer transaction list page](../../../finance/accounts-receivable/customer-transactions-list-page.md).

## Vendor transaction list page

The **View settlements** button on the Action Pane provides quick access to the settlement history and more information about the whole settlement transaction. You can also show additional transactions that are related to the selected transaction, either because they were part of the same settlement or because they are payments that were created in the same payment journal.

The **Global transactions** button has been added to the vendor page. This button lets you view all transactions for a vendor across all legal entities. The **Vendor transaction** list page shows transactions only for the legal entities that the user has access to, based on their security settings.

The filter for showing open transactions has been replaced with a new filter that lets you view more combinations of transactions. A **Hide currency revaluations** filter has also been added that lets you hide currency translation transactions.

You can also update due dates and discount dates for open customer transactions. In release 8.1, the experience has been improved so that you can add due dates to the **Vendor transaction** list page.

For more information, see [Vendor transaction list page](../../../finance/accounts-payable/vendor-transaction-list-page.md).

## Financial dimensions

You can use values from master records, such as customer and vendor, as default values in new dimensions. When the new dimensions are created, the master record ID is entered in the dimension values for those master records. For example, when you create a new customer, the customer ID is entered in the customer dimension. When you create sales orders, invoices, or other documents that require a customer ID, the existing defaulting rules are used, and the customer ID is added to the document.

You can configure a dimension so that information for other dimensions is automatically entered when you enter that dimension in a document. For example, if you enter cost center 10, a value of **20** can be automatically entered in the department dimension.

You can set up the derived dimensions segments and values by using entities.

For more information, see [Financial dimensions](../../../finance/general-ledger/financial-dimensions.md).

## Dual currency

Reporting currency can now be repurposed and used as a second accounting currency. This functionality is referred to as dual currency. The changes for dual currency can't be turned off through a configuration key or parameter. Because the reporting currency is used as a second accounting currency, the way that the reporting currency is calculated in the posting logic has changed.

For more information, see [Dual currency](../../../finance/general-ledger/dual-currency.md).

## Extensibility enhancements

In this release of Finance and Operations, numerous extensibility enhancements have been made to support extensibility through chain of command, delegates, or by providing access to members. In addition, enhancements have been made to enumerations, metadata, and SQL operations. For detailed information, see [Extensibility changes in Dynamics 365 Finance version 8.1](../../dev-itpro/extensibility/extensibility-changes-81.md)

## Phantom items

The Phantom line type can be used for the lines of a bill of materials (BOM) and multilevel BOM structures. Phantom BOMs can also be used for a BOM that has a route network.

For more information, see [Phantom items](../../../supply-chain/production-control/phantom-items.md).

## Russian localization

Dynamics 365 Finance and Operations now supports mandatory regulatory requirements in Russia (for on-premises deployment only). This release of Russian localization covers the following functional areas: accounts payable, accounts receivable, advance holders, bank and cash, export part of Client-Bank interface, fixed assets, general ledger and G/L reporting, electronic reporting for financial reports, inventory, addresses/FIAS, VAT and profit tax registers in areas of cash movement, goods movement, rated expenses, deferred expenses, exchange difference and WIP.

For more information, see [Russia](../../../finance/localizations/russia.md).

## VAT reporting for the United Arab Emirates

Standard sales tax functionality in Finance and Operations now fulfils the majority of legislation requirements of United Arab Emirates VAT law. The following country/region-specific features are specific to the United Arab Emirates:

- Legal entity configuration has been extended with additional fields required in VAT reporting.
- VAT reverse charge functionality has been enabled for UAE (ARE country/region context) to properly record taxable domestic operations within GCC territory.
- Additional sales, invoice, and credit notes print layouts have been added with additional columns and VAT summary information.
- Sales Invoice and Credit notes for UAE now print in two languages, including a new ar-AE Arabic language for user interface.
- VAT Return declaration report is printed to an electronic file format ready for uploading to e-TAX FTA portal.
- Standard audit file functionality has been shared with UAE local functionality. This is required by bht Federal Tax Authorities FTA VAT audit file - (FAF) and can be exported to a comma separated file format.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

