---
# required metadata

title: Qualified Invoice System in Japan
description: This article provides information about the Qualified Invoice System, which will be required in Japan as of October 1, 2023.
author: ankviklis
ms.date: 08/28/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: CustConsInvoice_JP, VendConsInvoice_JP
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: bd7255d9-0b0e-4372-8563-eaa559adbf24
ms.search.region: Japan
# ms.search.industry: 
ms.author: ankviklis 
ms.search.validFrom: 2023-08-11
ms.dyn365.ops.version: 10.0.34

---

# Qualified Invoice System in Japan

[!include [banner](../includes/banner.md)]

The Qualified Invoice System (QIS) represents updated requirements for issuing and reporting invoices that include Japan Consumption Tax (JCT) information. The requirements begin on October 1, 2023, and their purpose is to improve the accuracy and transparency of the tax regime. 

To claim input tax credits, taxpayers must receive and report qualified invoices from their suppliers. Issued and received qualified invoices must contain specific information, including the Qualified Invoice Issuer (QII) registration numbers, the tax rates, and the tax amounts by rate. 

The localization of Microsoft Dynamics 365 Finance for Japan has extended the invoicing functionality in Accounts receivable and Accounts payable to cover the new requirements. This article explains how to configure and use the functionality so that you comply with the new requirements in Japan. Here are some of the configuration and use guidelines:

- Maintain the QII registration numbers of your company, your vendors, and your customers.
- Print your company's registration number on customer invoices, including sales invoices and free text invoices.
- Calculate and round consumption taxes per sales tax code at the invoice level. You can round the total tax amount for all invoice lines by using the **Rounding precision** and **Rounding method** fields in the **Sales tax rounding rule** section in the sales tax code.
- Print the total invoice amount and tax amounts by tax code on customer invoices.
- Calculate non-deductible tax to apply transitional measures for input tax credits for purchases from non-qualified vendors.
- Calculate and round consolidated tax per tax code at the consolidated invoice level.
- Print the company's registration number and sales tax amounts by tax code on customer consolidated invoices. For more information, see [Consolidated invoices for Japan](/dynamics365/finance/localizations/apac-jpn-consolidate-invoices.md).

## Considerations

Here are the main considerations for this functionality:

- To accurately calculate, round, and print taxes on invoices and consolidated invoices, we recommend that you use only one sales tax code for each tax rate. For example, instead of using two sales tax codes that have a 10 percent rate on one invoice, you should use just one. In this way, you ensure consistency and accuracy in your tax calculations and output.
- To support transitional measures for input tax credits for non-qualified vendors, you can split the tax amount into deductible and non-deductible parts when you perform these actions:

    - Register a purchase invoice.
    - Post the non-deductible part to an expense/capitalizing account. You can use the non-deductible percentage in sales tax code values for this purpose.

- Printing the vendor's QII registration number on a vendor invoice isn't supported.

## Set up a QII registration number

To use QII registration numbers, you must complete these tasks.

1. Configure a registration type for QIIs for Japan.
2. Link the registration type to the **Qualified invoice issuer** registration category.
3. Add your company's registration number to its primary address in Japan.

> [!NOTE]
> For more information, see [Registration IDs](/dynamics365/finance/localizations/emea-registration-ids.md). The framework is extended so that you can maintain the QII registration numbers of your company and its counterparties (that is, vendors and customers). The QII number of the company can be printed on Japan-specific customer invoice layouts, including sales invoices, free text invoices, and consolidated invoices.

## Set up sales tax for JCT

For general information about sales tax, see [Sales tax overview](../general-ledger/indirect-taxes-overview.md).

Consider the following guidelines when you set up JCT:

- Create different sales tax codes for the *standard rate* and the *reduced rate*.
- Create different sales tax codes for purchases from *qualified* vendors and *non-qualified* vendors. Use the same sales tax codes for purchases from qualified vendors and for sales.
- Turn on the **Round deductible tax amount first** option in the sales tax codes to ensure correct rounding in purchase invoices from non-qualified vendors.
- Configure these settings in all sales tax codes:

    - Set an appropriate value for the **Tax type** field (**Standard** and/or **Reduced**).
    - Set the **Origin** field to **Percentage of net amount**.
    - Set the **Marginal base** field to **Net amount of invoice balance**.
    - Set the **Calculation method** field to **Whole amount**.
    - Configure **Sales tax rounding rule** as required.

- In **Sales tax code values**, set up transitional periods for purchase tax credits that use a non-deductible percentage:

    - Add a separate row for every transition period, and enter from and to dates as appropriate.
    - In the **Value** field, enter a tax rate.
    - For the periods, specify **Non deductible %**.

- Set up sales tax groups for JCT for vendors. Create different groups for qualified vendors and non-qualified vendors.
- Set up sales tax groups for JCT for customers.
- Set up item sales tax groups for the standard rate and the reduced rate.
- Specify sales tax groups on vendor and customer records by using different groups for qualified vendors and non-qualified vendors.
- Specify item sales tax groups on items for the standard rate and the reduced rate.

## Set up invoice layouts in Account receivable

1. Go to **Accounts receivable** \> **Setup** \> **Forms** \> **Form setup**.
1. On the **General** tab, in the **Sales tax specification** field, select **Registration currency**.
1. Select **Print management**.
1. Follow these steps:

    - For **Customer invoice**, set the **Report format** field to **SalesInvoice.Report\_JP**.
    - For **Free text invoice**, set the **Report format** field to **FreeTextInvoice.Report\_JP**.

1. On the **Invoice** tab, set the **Print qualified invoice issuer number on invoice** option to **Yes**.
1. On the **Free text invoice** tab, set the **Print qualified invoice issuer number on invoice** option to **Yes**.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
