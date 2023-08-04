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
ms.author: wangchen
ms.search.validFrom: 2023-08-11
ms.dyn365.ops.version: AX 7.0.0

---

# Qualified Invoice System in Japan

[!include [banner](../includes/banner.md)]

The Qualified Invoice System is a new invoicing system that takes effect in Japan from October 2023 to improve the accuracy and transparency of the consumption tax regime. The system will require taxpayers to issue and receive qualified invoices that contain certain information, such as the registration number, the applicable tax rate, and the consumption tax amount categorized by tax rate12. The system will also require taxpayers to report the qualified invoices they issue and receive to the tax authorities through an electronic platform.

The system will affect the eligibility of taxpayers to claim input tax credits, as they will only be able to do so if they receive qualified invoices from their suppliers and report them to the tax authorities. However, there are some exceptions where taxpayers do not need qualified invoices to take input credits, such as for small transactions, imports, or purchases from non-qualified vendors.

The system is similar to the invoicing systems used by countries that impose value added tax (VAT) or goods and services tax (GST), such as the European Union or Australia. The system is also supported by e-invoicing as an option, which adopts the European and global Peppol standard.

Accounts payable and Accounts receivable invoicing functionality for Japan is extended to cover the new Qualified Invoice System requirements. This article provides information about this Qualified Invoice System, and explains how it is designed in Dynamics 365 Finance localization for Japan.

The extended invoicing functionality in Accounts payable and Accounts receivable provides capabilities that can help you stay compliant with the new Qualified Invoice System requirements in Japan. In addition, this feature addresses the opportunities coming from the introduction of Electronic Invoicing in Japan. Using the Electronic Invoicing service, you can comply with the local standards, raise the level of automation of your invoicing processes, and follow global tax digitalization trends.

Japan is enforcing Qualified Invoice System requirements starting October 1, 2023. As part of the Qualified Invoice System, the wide use of electronic invoices is being promoted.

Microsoft Dynamics 365 Finance includes capabilities that are aimed at supporting certain requirements of the Qualified Invoice System.

The [Registration IDs](/dynamics365/finance/localizations/emea-registration-ids) framework is extended to provide the possibility to maintain the qualified invoice issuer registration numbers of the company and its counterparties, that is, vendors and customers. The qualified invoice issuer number of the company can be printed on Japan-specific customer invoice layouts, including sales invoices, free text invoices, and project invoices. 

You can use Finance to configure sales tax so that the tax calculation and rounding per sales tax code can happen on the invoice level. Total tax breakdown per sales tax code can also be printed on customer invoice layouts. 

In Japan, it's common for businesses to issue monthly invoices to their customers and not per individual shipment. In Finance for Japan, the [consolidated invoice](/dynamics365/finance/localizations/apac-jpn-consolidate-invoices) functionality supports this business practice. The functionality is extended to comply with the Qualified Invoice System requirements. This includes:

- Recalculating and rounding consumption taxes per sales tax code on the consolidated invoice level.
- Posting corresponding tax adjustments.
- Printing the qualified invoice issuer number of the company and the total tax breakdown per sales tax code on the consolidated invoice layout.

The following capabilities are available in relation to the Qualified Invoice System in Japan:
	1. Maintain the company's and its counterparties' "Qualified invoice issuer" (QII) registration numbers.
	1. Include the company's QII registration number in the printed form of a Sales invoice and Free Text Invoice issued by the company.
	1. Ensure Japan Consumption Tax (JCT) amounts are rounded off once per invoice and tax rate.
	1. Include the total invoice amount and tax amounts' break down per tax rate in the printed form of a sales invoice issued by the company.
	1. Support transitional measures for input (purchase) tax credit for purchases from non-qualified vendors.
	1. The qualified invoice requirements apply to both invoices and consolidated invoices.

## Assumptions
The following are main assumptions that are applicable to QIS implementation in Dynamics 365 Finance:
	1. The QII registration number of a company is different from and is not related to the JCT registration number or the corporate number of the company. Hence, a new registration category can be created to be used for QII registration numbers independently of other registration categories.
	1. It is possible for a company to configure sales tax codes so that two or more sales tax codes with the same tax rate are never used in one and the same vendor or customer invoice. For example, two sales tax codes with the same standard JCT rate 10% can never appear simultaneously in one sales invoice. Hence, the requirements on JCT calculation, rounding, and printing per tax rate can be fulfilled by the existing capabilities of sales tax calculation, rounding, and printing per sales tax code.
	1. A JCT rate consists of National JCT and Local JCT parts. For example, the JCT rate 10% consists of the National JCT rate 7.8% and the Local JCT rate 2.2%. However, it is not needed to calculate National JCT and Local JCT separately when posting an invoice and calculating JCT. The tax split must only be done on the tax declaration level. Hence, only total JCT rates need to be configured and used to calculate and post sales tax.
	1. Transitional measures for purchase tax credit for purchases from non-QII can be implemented by splitting the purchase tax amount into deductible and non-deductible parts upon registering a purchase invoice, and by capitalizing the non-deductible part to inventory. Hence, existing standard capabilities of non-deductible percentage in a sales tax code value can be used to fulfill the requirements.

## Limitations
The following are out of scope of QIS implementation in Dynamics 365 Finance:
	1. Validation of QII registration via external service.
	1. Printing QII number of the vendor in a vendor invoice.

## Configuring a Qualified invoice issuer
In order to work with the company's and its counterparties' "Qualified invoice issuer" (QII) registration numbers, the following steps should be performed:

-   **Configure a registration type for QII registration for Japan**
-   **Link the registration type to the "Qualified invoice issuer" registration category**
-   **Add a QII registration number to the primary address of the Japaneese legal entity**

## Setup of the Sales tax for JCT
In order to work with the company's and its counterparties' "Qualified invoice issuer" (QII) registration numbers, the following steps should be performed:

-   Create separate sales tax codes for the standard rate and reduced rate.
- 	Create separate sales tax codes for purchases from qualified invoice issuers and non-qualified invoice issuers. The sales tax codes for purchases from qualified invoice issuers can also be used for sales.
-	All sales tax codes should have corresponding Tax type, Origin = Percentage of net amount, Marginal base = Net amount of invoice balance, Calculation method = Whole amount, Rounding precision = 1.00, Rounding method = Normal, Print = Print code, Print code = <JCT rate>%
-	Configure transitional periods for purchase tax credit for purchases from non-qualified invoice issuers using non-deductible percentage in sales tax code values.
-	Set up sales tax groups for JCT, one for qualified invoice issuers and another one for non-qualified invoice issuers.
-	Set up item sales tax groups for the standard rate and reduced rate.
-	Specify sales tax groups on vendor maser records: one vendor as QII and another one as non-QII.
-	Specify the sales tax group for qualified invoice issuers on customer maser record.
-	Specify item sales tax groups for purchases and for sales on items: two for standard JCT rate and another two for reduced one.
-	Accounts receivable -> Form setup:
			i. General -> Sales tax specification = Registration currency
			ii. Invoice -> Print tax exempt number on invoice = Yes
			iii. Invoice -> Print qualified invoice issuer number on invoice = Yes
			iv. Free text invoice -> Print tax exempt number on invoice = Yes
			v. Free text invoice -> Print qualified invoice issuer number on invoice = Yes
			vi. Print management:
				1) Customer invoice -> Original: Report format = SalesInvoice.Report_JP
				2) Free text invoice -> Original: Report format = FreeTextInvoice.Report_JP


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
