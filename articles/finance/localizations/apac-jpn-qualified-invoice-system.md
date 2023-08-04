---
# required metadata

title: Qualified Invoice System in Japan
description: The new Qualified Invoice System is coming into force in Japan from October 1, 2023. This article provides information about this Qualified Invoice System, and explains how it works.
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
ms.author: 
ms.search.validFrom: 2023-08-11
ms.dyn365.ops.version: AX 7.0.0

---

# Qualified Invoice System in Japan

[!include [banner](../includes/banner.md)]

Qualified Invoice System in Japan: This is a new system for issuing and reporting invoices with consumption tax information in Japan. It starts from October 2023 and aims to improve the accuracy and transparency of the tax regime. Taxpayers must issue and receive qualified invoices that have certain information, such as the registration number, the tax rate, and the tax amount by rate. They must also report these invoices electronically to the tax authorities. To claim input tax credits, taxpayers must receive and report qualified invoices from their suppliers, unless there are some exceptions. The system is similar to the VAT or GST systems in other countries, such as the EU or Australia. It also supports e-invoicing using the Peppol standard.
Dynamics 365 Finance localization for Japan has extended its invoicing functionality in Accounts payable and Accounts receivable to cover the new system requirements. This article explains how this system works and how to set it up in Finance.
The invoicing functionality in Finance helps you comply with the new system requirements in Japan. It also lets you use e-invoicing to follow the local standards and global trends. You can use Finance to:
- Maintain the qualified invoice issuer registration numbers of your company and your vendors and customers. You can use a different registration number for your company if it is not the primary address, but it is in Japan and it is the primary address for the country.
- Print your company’s registration number on customer invoices, including sales invoices and free text invoices, including consolidated invoices.
- Calculate and round consumption taxes per tax rate on the invoice level. You can round the total tax amount for all invoice lines using the Rounding by field in the sales tax group.
- Print the total invoice amount and tax amounts by tax rate on customer invoices.
- Apply transitional measures for input tax credit for purchases from non-qualified vendors.
- Use consolidated invoices for monthly billing. You can print the sales tax section by tax rate on all invoices, including consolidated invoices. For more information, see [Consolidated invoice](/dynamics365/finance/localizations/apac-jpn-consolidate-invoices).

The following scenarios are supported by this system:
- Sales invoice and credit note.
- Free text invoice and credit note.
- Consolidated invoices.

## Assumptions
The main assumptions for this system in Finance are:
- The qualified invoice issuer registration number of a company is different from its JCT registration number or corporate number. You can create a new registration category for it.
- You can set up sales tax codes so that only one sales tax code with the same tax rate is used in one invoice. For example, you can’t have two sales tax codes with 10% rate in one invoice. This way, you can use sales tax codes to calculate and print taxes by rate.
- A JCT rate has two parts: National JCT and Local JCT. For example, 10% rate has 7.8% National JCT and 2.2% Local JCT. But you don’t need to calculate them separately for invoices. You only need to split them for tax declarations. So you only need to set up total JCT rates for invoices.
- Transitional measures for purchase tax credit for non-qualified vendors can be done by splitting the tax amount into deductible and non-deductible parts when you register a purchase invoice, and by posting the non-deductible part to an expense account. You can use the non-deductible percentage in sales tax code values for this.

## Limitations
The following are not covered by this system in Finance:
- Checking the validity of registration numbers through an external service.
- Printing the vendor’s registration number on a vendor invoice.

## Setting up a Qualified invoice issuer
To work with registration numbers, you need to:
- Configure a registration type for qualified invoice issuers for Japan.
- Link the registration type to the “Qualified invoice issuer” registration category.
- Add your company’s registration number to its primary address in Japan.

For more information, see [Registration IDs](/dynamics365/finance/localizations/emea-registration-ids). This framework is extended to provide the possibility to maintain the qualified invoice issuer registration numbers of the company and its counterparties, that is, vendors and customers. The qualified invoice issuer number of the company can be printed on Japan-specific customer invoice layouts, including sales invoices and free text invoices. 

## Setting up Sales tax for JCT
In order to work with the company's and its counterparties' "Qualified invoice issuer" (QII) registration numbers, the following steps should be performed:
To work with consumption taxes, you need to:
- Create different sales tax codes for standard rate and reduced rate.
- Create different sales tax codes for purchases from qualified and non-qualified vendors. You can use the same sales tax codes for purchases from qualified vendors and for sales.
- Set up all sales tax codes with these settings: Tax type, Origin = Percentage of net amount, Marginal base = Net amount of invoice balance, Calculation method = Whole amount, Rounding precision = 1.00, Rounding method = Normal, Print = Print code, Print code = <JCT rate>%.
- Set up transitional periods for purchase tax credit using non-deductible percentage in sales tax code values.
- Set up sales tax groups for JCT: one for qualified vendors and another one for non-qualified vendors.
- Set up item sales tax groups for standard rate and reduced rate.
- Specify sales tax groups on vendor and customer records: one vendor as qualified and another one as non-qualified.
- Specify item sales tax groups on items: two for standard rate and another two for reduced rate.

## Setting up Invoices in Account Receivable
In Accounts receivable -> Form setup:
1. General -> Sales tax specification = Registration currency
1. Invoice -> Print tax exempt number on invoice = Yes
1. Invoice -> Print qualified invoice issuer number on invoice = Yes
1. Free text invoice -> Print tax exempt number on invoice = Yes
1. Free text invoice -> Print qualified invoice issuer number on invoice = Yes
1. Print management:
	i. Customer invoice -> Original: Report format = SalesInvoice.Report_JP
	ii. Free text invoice -> Original: Report format = FreeTextInvoice.Report_JP


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
