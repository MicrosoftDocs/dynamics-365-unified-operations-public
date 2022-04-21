---
# required metadata

title: Czech Republic overview
description: This topic provides an overview of Dynamics 365 Finance functionality that is specific to the Czech Republic.
author: kfend
ms.date: 01/18/2022
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.search.region: Czech Republic
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1

---

# Czech Republic overview

[!include [banner](../includes/banner.md)]

This topic includes information and links to resources that can help you set up legal entities with a primary address in the Czech Republic.

## Fixed assets
The following topics cover information that pertains to fixed assets in the Czech Republic:

-   [Depreciation rounding](emea-cze-depreciation-rounding.md)
-   [Half year depreciation on fixed asset disposal for the Czech Republic](emea-cze-half-depreciation-fixed-asset-disposal.md)
-   [Depreciation suspension (holidays)](emea-cze-depreciation-suspension-holidays.md)
-   [Fixed assets depreciation methods for the Czech Republic](emea-cze-fixed-assets-depreciation.md)
-   [Post the pre-acquisition of a fixed asset](emea-pre-acquisition-acquisition-fixed-asset.md)

## VAT reporting
For information about setting up and generating the VAT statement for legal entities located in the Czech Republic, see [VAT statement for the Czech Republic](emea-cze-vat-statement-details.md). For information about the VAT declaration, see [VAT declaration (Czech Republic)](emea-cze-vat-declaration-tax-declaration-model.md)

### Intra-community VAT
This section provides information about how intra-community value-added tax (VAT) is calculated and posted for the Czech Republic. 

When legal entities that have a primary address in the Czech Republic purchase from European Union (EU) member states, they should do a self-assessment of VAT to ensure that the following conditions are met:

-   The output VAT is paid in the VAT period when the invoice was issued (document date).
-   The input VAT wasn't deducted before the document receipt (VAT register date).

Information about intra-community VAT can be calculated and posted automatically. When you post an EU vendor invoice, two VAT transactions for the same amount are created. One VAT transaction is created for payable sales tax, and the other transaction is created for receivable sales tax. To reflect this requirement, you should complete the following setup:

-   Select the **Intra-community VAT** check box on the **Accounts payables parameters** page (**Accounts payable** > **Setup** > **Accounts payables parameters**).
-   Select the **Document date for intra-community VAT** check box on the **Accounts payables parameters** page.
-   Create two sales tax codes: one that has a positive sales tax percentage and another that has a negative sales tax percentage.
-   Create a sales tax group that contains both the positive and negative sales tax codes. Select the **Intra-community VAT** parameter for the negative sales tax code.
-   In journals, select the **Document date for intra-community VAT** parameter.

When a purchase invoice is posted, the receivable VAT and payable VAT are posted at the same time. For the positive sales tax transaction, the VAT register date is set to the VAT register date from the invoice posting page, and the sales tax direction is **Sales tax receivable**. For the negative sales tax transaction, the VAT register date is set to the document date, and the sales tax direction is **Sales tax payable**.

## Intrastat declaration
For information about the Czech Intrastat report, see [Czech Intrastat](emea-cze-intrastat.md).

## Credit note on cash discount
For information about creating, posting, and printing credit notes for cash discounts that are given to customers, see [Credit note on cash discount](emea-cze-credit-note-cash-discount.md).

## Split periods in periodic journals
For legal entities in Estonia, Latvia, Lithuania, Poland, Hungary, Russia, and the Czech Republic, the **Periodic journals** page is extended by the split for periods functionality. For more information, refer to one of the following topics:
- [Split periods in periodic journals](emea-create-post-periodic-journals.md)
- [Post periodic journals](../general-ledger/tasks/post-periodic-journals.md)

## Signers for print forms
For legal entities in Estonia, Latvia, Lithuania, Poland, Hungary, Russia, and the Czech Republic, you can set up signers and titles for customers and vendors that print documents such as invoices and cash orders. For more information, see [Set up signers for print forms](emea-set-up-signers-for-printing-forms.md).

## Customize currency units and subunits
You can update how amounts are displayed on reports and other documents for Estonia, Latvia, Lithuania, Poland, Czech Republic, Hungary, and Russia. You can set up full names and short names for currency units and subunits. For more information, refer to [Update how amounts are displayed on reports and documents](emea-amount-printing-forms.md).

> [!NOTE]
> You can view the sales tax in local currency in the **Customer invoice journal** report and **Vendor invoice journal** report.

## Specify bank symbols for bank accounts 
Constant symbols are set up for bank accounts and then used on sales orders, purchase orders, customer invoices, and free text invoices. 
Use the **Bank constant symbols** page to set up a list of constant symbols. By default, when you set up a constant symbol for a specific company bank account, the symbol is copied to sales orders and free text. From the sales order or free text invoice, the constant symbol is transferred to the customer invoice. 
> [!NOTE]
> By default, when you set up a specific symbol for a bank account, it is copied to the vendor invoice printout form. The constant symbol is also displayed on invoice printouts. 

You can set up bank symbols on the **Bank constant symbols** page (**Cash and bank management** > **Setup** > **Constant symbols**). 

## Year-end close
There are unique considerations for the year-end closing process and opening transactions for the Czech Republic. You can set up the year-end closing process in the following ways: 
- Posting to different accounts for closing and opening of balance accounts. 
- Transfer of profit or loss year-end result into the newly opened year to a different account.
For more information, see [Year-end close for Czech Republic and Hungary](emea-cze-hun-year-end.md).

## Additional resources
- [Electronic reporting overview](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md)
- [Download Electronic reporting configurations from Lifecycle Services](../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
