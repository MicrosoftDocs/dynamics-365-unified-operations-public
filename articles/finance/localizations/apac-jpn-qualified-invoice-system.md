---
# required metadata

title: Qualified Invoice System in Japan
description: The updated Qualified Invoice System is coming into force in Japan from October 1, 2023. This article provides information about this Qualified Invoice System, and explains how it works.
author: ankviklis
ms.date: 08/04/2023
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
ms.dyn365.ops.version: AX 7.0.0

---

# Qualified Invoice System in Japan

[!include [banner](../includes/banner.md)]

**Qualified Invoice System (QIS)** represents updated requirements for issuing and reporting invoices with **Japan Consumption Tax (JCT)** information. It starts from October 2023 and aims to improve the accuracy and transparency of the tax regime. 
To claim input tax credits, taxpayers must receive and report qualified invoices from their suppliers. Issued and received qualified invoices must contain certain information, 
such as **Qualified invoice issuer (QII)** registration numbers, the tax rates, and the tax amounts by rate. 

Dynamics 365 Finance localization for Japan has extended its invoicing functionality in Accounts receivable and Accounts payable to cover the new requirements. 
This article explains how to configure and use it in Finance. The invoicing functionality in Finance helps you support the new requirements in Japan in the following way:
- Maintain the qualified invoice issuer registration numbers of your company and your vendors and customers.
- Print your company’s registration number on customer invoices, including sales invoices and free text invoices.
- Calculate and round consumption taxes per sales tax code on the invoice level. You can round the total tax amount for all invoice lines using the "Rounding precision" and "Rounding method" fields in the "Sales tax rounding rule" group in the sales tax code.
- Print the total invoice amount and tax amounts by tax code on customer invoices.
- Calculate non-deductible tax to apply transitional measures for input tax credit for purchases from non-qualified vendors.
- Calculate and round consolidated tax per tax code on the consolidated invoice level.
- Print the company’s registration number and sales tax amounts by tax code on customer consolidated invoices. For more information, see [Consolidated invoice](/dynamics365/finance/localizations/apac-jpn-consolidate-invoices).

## Assumptions and limitations
The main considerations for this functionality in Finance are as follows:
- To accurately calculate, round, and print taxes on invoices and consolidated invoices, it is recommended to use only one sales tax code for each tax rate. For example, instead of having two sales tax codes with a 10% rate on one invoice, you should use just one. This will ensure consistency and accuracy in your tax calculations and output.
- Transitional measures for input tax credit for non-qualified vendors can be supported by splitting the tax amount into deductible and non-deductible parts when you register a purchase invoice, and by posting the non-deductible part to an expense / capitalizing account. You can use the non-deductible percentage in sales tax code values for this.
- Printing the vendor’s QII registration number on a vendor invoice is not supported.

## Setting up a Qualified invoice issuer registration number
To be able to use QII registration numbers, you need to:
- Configure a registration type for qualified invoice issuers for Japan.
- Link the registration type to the “Qualified invoice issuer” registration category.
- Add your company’s registration number to its primary address in Japan.

> [!NOTE]
> For more information, see [Registration IDs](/dynamics365/finance/localizations/emea-registration-ids). This framework is extended to provide the possibility to maintain the qualified invoice issuer registration numbers of the company and its counterparties, that is, vendors and customers. The qualified invoice issuer number of the company can be printed on Japan-specific customer invoice layouts, including sales invoices, free text invoices, and consolidated invoices.

## Setting up Sales tax for JCT
For general information, see [Sales tax overview](../general-ledger/indirect-taxes-overview.md). To support Japan consumption taxes, consider the following when setting up JCT:
- Create different **sales tax codes** for the **standard rate** and the **reduced rate**.
- Create different **sales tax codes** for purchases from **qualified and non-qualified vendors**. You can use the same sales tax codes for purchases from qualified vendors and for sales.
- Turn on **Round deductible tax amount first** in the sales tax codes to ensure correct rounding in purchase invoices from non-qualified vendors.
- Set up all sales tax codes with these settings: **Tax type** (*Standard and/or Reduced*), **Origin = Percentage of net amount**, **Marginal base = Net amount of invoice balance**, **Calculation method = Whole amount**. Also configure **Sales tax rounding rule** as required.
- Set up transitional periods for purchase tax credit using non-deductible percentage in **sales tax code values** as follows:
    - add a separate row for every transition period and enter **From / To date** accordingly,
	- fill in the **tax rate** in **Value** field,
	- specify **Non deductible %** for the periods.
- Set up **Sales tax groups for JCT** for vendors: different groups for **qualified vendors** and for **non-qualified vendors**.
- Set up **Sales tax groups for JCT** for customers.
- Set up **Item sales tax groups** for the **standard rate** and the **reduced rate**.
- Specify sales tax groups on vendor and customer records: different groups for qualified vendors and for non-qualified vendors.
- Specify item sales tax groups on items: for the standard rate and for the reduced rate.

## Setting up Invoices layouts in Account Receivable
Go to **Accounts receivable -> Setup -> Forms -> Form setup** and make configuration as follows:
1. **General** tab -> **Sales tax specification = Registration currency**
1. **General** tab -> **Print management** button:
    * **Customer invoice** -> Original: **Report format = SalesInvoice.Report_JP**
    * **Free text invoice** -> Original: **Report format = FreeTextInvoice.Report_JP**
1. **Invoice** tab -> **Print qualified invoice issuer number on invoice = Yes**
1. **Free text invoice** tab -> **Print qualified invoice issuer number on invoice = Yes**



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
