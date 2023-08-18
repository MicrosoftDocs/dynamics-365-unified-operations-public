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

Qualified Invoice System (QIS) represents updated requirements for issuing and reporting invoices with Japan Consumption Tax (JCT) information. It starts from October 2023 and aims to improve the accuracy and transparency of the tax regime. 
To claim input tax credits, taxpayers must receive and report qualified invoices from their suppliers, unless there are some exceptions. Issued and received qualified invoices must contain certain information, 
such as "Qualified invoice issuer" (QII) registration numbers, the tax rate, and the tax amount by rate. 

Dynamics 365 Finance localization for Japan has extended its invoicing functionality in Accounts receivable and Accounts payable to cover the new system requirements. 
This article explains how to configure it in Finance. The invoicing functionality in Finance helps you support the new requirements in Japan. You can use Finance to:
- Maintain the qualified invoice issuer registration numbers of your company and your vendors and customers.
- Print your company’s registration number on customer invoices, including sales invoices and free text invoices.
- Calculate and round consumption taxes per sales tax code on the invoice level. You can round the total tax amount for all invoice lines using the Rounding by field in the sales tax code.
- Print the total invoice amount and tax amounts by tax code on customer invoices.
- Calculate nondeductible tax to apply transitional measures for input tax credit for purchases from non-qualified vendors.
- Calculate abd round consolidated tax per tax code on the consolidated invoice sales.
- Print the company’s registration number and sales tax section by tax rate on consolidated invoices. For more information, see [Consolidated invoice](/dynamics365/finance/localizations/apac-jpn-consolidate-invoices).

## Assumptions and limitations
The main assumptions for this system in Finance are:
- To calculate, round and and print taxes on invoices and consolidated invoices, you must use only one sales tax code for every tax rate in one invoice. For example, you can’t have two sales tax codes with 10% rate in one invoice.
- Transitional measures for purchase tax credit for non-qualified vendors can be done by splitting the tax amount into deductible and non-deductible parts when you register a purchase invoice, and by posting the non-deductible part to an expense / capitalizing expense account. You can use the non-deductible percentage in sales tax code values for this.
- Printing the vendor’s registration number on a vendor invoice is not supported.

## Setting up a Qualified invoice issuer
To be able to setup and use QII registration numbers, you need to:
- Configure a registration type for qualified invoice issuers for Japan.
- Link the registration type to the “Qualified invoice issuer” registration category.
- Add your company’s registration number to its primary address in Japan.

> [!NOTE]
> For more information, see [Registration IDs](/dynamics365/finance/localizations/emea-registration-ids). This framework is extended to provide the possibility to maintain the qualified invoice issuer registration numbers of the company and its counterparties, that is, vendors and customers. The qualified invoice issuer number of the company can be printed on Japan-specific customer invoice layouts, including sales invoices, free text invoices, and consolidated invoices.

## Setting up Sales tax for JCT
For general information, see [Sales tax overview](../general-ledger/indirect-taxes-overview.md). To work with consumption taxes, consider the following when setting up JCT:
- Create different sales tax codes for the standard rate and the reduced rate.
- Create different sales tax codes for purchases from qualified and non-qualified vendors. You can use the same sales tax codes for purchases from qualified vendors and for sales.
- Turn on "Round deductible tax amount first" in the sales tax codes to ensure correct rounding in purchase invoices from non-qualified suppliers.
- Set up all sales tax codes with these settings: Tax type (Standard, Reducer, or Other), Origin = Percentage of net amount, Marginal base = Net amount of invoice balance, Calculation method = Whole amount. Configure rounding as required.
- Set up transitional periods for purchase tax credit using non-deductible percentage in sales tax code values as follows:
    - add a separate row for every period and enter From / To dates accordingly,
	- fill in the tax rate for the periods,
	- specify the non deductible % for the periods.
- Set up sales tax groups for JCT: different groups for qualified vendors and for non-qualified vendors.
- Set up item sales tax groups for the standard rate and the reduced rate.
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
