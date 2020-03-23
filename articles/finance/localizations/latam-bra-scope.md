---
# required metadata

title: Scope of the Brazilian localization
description: This topic describes the strategy and scope for tax, finance, and accounting laws and regulations in Brazil. 
author: sndray
manager: AnnBe
ms.date: 12/12/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Brazil
# ms.search.industry: 
ms.author: sndray
ms.search.validFrom: 2018-4-30
ms.dyn365.ops.version: 8.0

---

# Scope of the Brazilian localization

[!include [banner](../includes/banner.md)]

This topic describes the strategy and scope for Brazilian tax, finance, and accounting laws and regulations that Microsoft has included in Microsoft Dynamics 365 Finance for Brazil. 

In general, Microsoft invests significant resources on extending the business process functionality of Dynamics 365 Finance by developing features and functionality to address specific tax, accounting, or financial regulatory requirements in countries or regions where Microsoft makes Microsoft Dynamics generally available.

The software helps organizations run their business operations while complying with country/region-specific laws, regulations, and common business practices for handling their daily activities. This software includes features and functionality that are designed to address specific federal tax, accounting, financial, or statutory reporting laws or regulations that commonly affect businesses in Brazil.

However, Microsoft Dynamics doesn't address all laws, regulations, or commercial requirements in Brazil, because laws and regulations vary in the way that they affect organizations. Additional details are available in the [Localization Availability Guide](https://aka.ms/ax-availabilityguide).

Channel partners are an important part of our global strategy for delivering Microsoft Dynamics to help customers meet local laws and regulatory requirements for Brazil. By taking advantage of the extensible nature of the development architecture of Microsoft Dynamics, channel partners can address a customer's specific business needs during implementation, either through configuration of the software (when configuration options are available), or through partner-created customizations or localizations (if customization or localization is required). Although channel partners might provide solutions that meet specific regulatory requirements that are unique to municipalities, cities, states, or other regions in Brazil, Microsoft doesn't provide any guarantees or warranties (expressed, implied, statutory, or otherwise) that partner-created solutions comply with local business, tax and regulatory, legal, or other applicable requirements.

Channel partners or customers are solely responsible for any configurations, customizations, localizations, or translations that they create or implement on behalf of customers. This responsibility also covers any updates for these solutions, and any support or other service that is provided to customers for such solutions. You must contact your channel partner for information about the solutions that the channel partner creates for licensed versions of Microsoft Dynamics.

## Definitions

**Customization** refers to either of the following:

- Any configuration, modifications, or changes that partners or customers make either to the Microsoft Dynamics software or, when applicable, to the software documentation to fit a customer's specific business needs. Examples include adding or renaming fields or tables, creating custom reports, or integrating with third-party solutions.
- Any software that partners or customers develop for the Microsoft Dynamics software.

**Localization** refers to any modification to, addition to, or adaptation of the Microsoft Dynamics software to enable or include specific features or functionality in the software so that it complies with applicable regulatory requirements (including, without limitation, versions and updates of the Microsoft Dynamics software, user assistance tools, and end-user documentation). Examples of laws or regulatory requirements that might require localization of the software include local tax reporting (such as for sales tax, value-added tax [VAT], and goods and services tax [GST]), invoice tracking by a government authority, government-required tax calculations, local accounting rules, and local regulatory and statutory reporting.

**National Standards** refer to feature requirements in software that are primarily related to banking practices (such as payment methods, payment formats, and bank statements). Less often, the requirements are related to commercial documents (such as electronic fiscal documents). National Standards are local requirements that aren't required by law or regulation, but that are widely adopted within a geographic region and critical to the sale of licenses for business management software in that geographic region.

## Brazilian localization strategy

In general, the Microsoft strategy for addressing the tax, financial, accounting, or statutory reporting requirements for Brazil consists of providing localizations for Microsoft Dynamics that do the following:

- They implement the federal tax requirements that are detailed in the [Brazilian localization scope](#brazilian-localization-scope) section of this topic.
- They implement, for the following states, the state/region requirements that are detailed in the [Brazilian localization scope](#brazilian-localization-scope) section: São Paulo (SP), Rio de Janeiro (RJ), Paraná (PR), Santa Catarina (SC), and Rio Grande do Sul (RS).
- They deliver specific new regulatory features through configurations or development of new functionality that implements the federal and state/region requirements that are detailed in the [Brazilian localization scope](#brazilian-localization-scope) section, in accordance with the business rules that are specified in this topic and the Microsoft Dynamics roadmap on the [Microsoft Dynamics Localization Portal](https://mbs.microsoft.com/partnersource/deployment/resources/productreleases/gfmlocalizationportalmc.htm?printpage=false&sid=xdtafwuk1xh2l5jdjhhv0joy&stext=gfm%20localization%20portal).
- They deliver specific new regulatory features in the most recent service pack that is available, or in a new service pack, for supported versions of Microsoft Dynamics.
- They apply National Standards and competitive features that Microsoft, at its sole discretion, determines to be necessary or appropriate, based on business needs in the region.
- They don't focus on the requirements of specific businesses, segments, verticals, regions, or large enterprises, even when these requirements are required by laws, statutes, or regulations at the federal, state, or city level.
- They don't include municipal requirements, except the municipal requirements that are detailed in the [Brazilian localization scope](#brazilian-localization-scope) section.

There are specific laws and requirements that are out of scope for Microsoft Dynamics. For a list, see the [Out of scope](#out-of-scope) section of this topic.

The Brazilian localization that Microsoft developed for Microsoft Dynamics is limited to the features and functionality that are described in this topic. Therefore, Microsoft Dynamics must be analyzed by prospective customers or a tax professional, such as an accounting and tax auditor, tax law firm, or tax consulting firms, who can assess whether the functionality is appropriate to meet the customer's business needs, or whether custom solutions are required.

## Brazilian localization scope

The user interface (UI) and online Help for Microsoft Dynamics are translated into Brazilian Portuguese. Additional documentation, such as white papers and training materials, might be available only in English and might not be available when the software is first made generally available in Brazil.

The localization scope for Microsoft Dynamics available in Brazil is limited to tax calculation, accounting transactions, issuing/receiving fiscal documents, and issuing fiscal receipts in the following four scenarios: procure to pay, quote to cash, commerce, and regulatory/statutory reporting.

The features that Microsoft delivers and supports as part of the Brazilian localization for Microsoft Dynamics are listed in the [Brazilian localization features](#brazilian-localization-features) section of this topic. Details about each of the features can be found in Help in Microsoft Dynamics, and in white papers that are published on the [Microsoft Dynamics Localization Portal](https://mbs.microsoft.com/partnersource/deployment/resources/productreleases/gfmlocalizationportalmc.htm?printpage=false&sid=xdtafwuk1xh2l5jdjhhv0joy&stext=gfm%20localization%20portal).

## Market availability

The Microsoft goal is to deliver regulatory features in enough time for installation. To implement the tax, accounting, financial, or regulatory/statutory reporting requirements that typically affect a majority of businesses in Brazil, Microsoft aims to release tax and regulatory updates that contain required changes before the effective date or other date that is mandated by the applicable government authority at either the federal or state level (but only for the states that are identified in the [Brazilian localization strategy](#brazilian-localization-strategy) section of this topic), so that our channel partners have enough time to update their customer solutions. Internally, we call this date the *market required date* (MRD).

Microsoft strives to meet its established MRDs and dates that are mandated by the applicable government authority. However, various factors can affect the timely delivery of tax and regulatory updates. Here are some examples:

- Legislative or regulatory changes that the government makes, but that it doesn't give enough notice about before the date when the law takes effect
- Feature, functionality, infrastructure, or architectural limitations of the affected software versions that are generally available in the marketplace
- The complexity and coverage of the coding, redesign, or enhancement that is required in the software to implement the legislation or regulatory requirements, or schedule conflicts

If it isn't feasible to meet these dates, we use commercially reasonable efforts to develop and release tax and regulatory updates as soon as possible.

Any dates that Microsoft publishes are for planning purposes only and are subject to change at any time without notice.

Microsoft makes no representations, warranties, or guarantees about the timeliness or completeness of any tax or regulatory update that it provides, and, to the maximum extent that is permitted under applicable law, disclaims all implied warranties and conditions, such as implied warranties or conditions of merchantability and fitness for a particular purpose.

## Brazilian localization features

<table>
<thead>
<tr>
<th>Area</th>
<th>Item</th>
<th>AX 2012 R3</th>
<th>Finance</th>
</tr>
</thead>
<tbody>
<tr>
<td>Master data</td>
<td>Tax identifiers for legal entities and fiscal establishments:
<ul>
<li>CNPJ/CPF</li>
<li>IE</li>
<li>CCM</li>
<li>IE for tax substitution for multiples states</li>
<li>CNAE</li>
</ul>
</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Tax identifiers for customers and vendors:
<ul>
<li>CNPJ/CPF</li>
<li>IE</li>
<li>CCM</li>
<li>NIT</li>
<li>INSS-CEI</li>
<li>CNAE</li>
</ul>
</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Item tax characteristics:
<ul>
<li>Fiscal classification code and exception</li>
<li>Taxation origin</li>
<li>Product type</li>
</ul>
</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>CFOP table</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>Taxes</td>
<td>Tax types: IPI, ICMS, ICMS tax substitution, ICMS difference, DIFAL, Importation tax, PIS, COFINS, CSLL, IRRF, INSS, Retained INSS, and ISS</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Taxation mode per tax type:
<ul>
<li>1 &ndash; Taxable</li>
<li>2 &ndash; Exempt or non-taxable</li>
<li>3 &ndash; Others</li>
</ul>
</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Tax credit based on taxation mode</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>ICMS base reduction</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>ICMS tax substitution with calculation based only on markup for outbound fiscal documents</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Simplified ICMS tax substitution</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Independent configuration for ICMS base reduction and tax substitution</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>IPI tax on the final user</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>ICMS for use and consumption</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>ICMS, PIS, and COFINS tax discounts for sales to SUFRAMA</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>ICMS difference over sales in final consumer (DIFAL) only for simplified base</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>ICMS difference over purchase</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Configurable default taxes based on operations defined/specified per CFOP group</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Calculation of PIS and COFINS reference to law 1.401/2013 during importation</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>Procure</td>
<td>Purchase requisitions, requests for quotation, and purchase orders localized to support the Brazilian taxes per the Brazilian localization scope</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Fiscal document texts in purchase orders</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Cancel inbound issued fiscal documents</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Reverse received fiscal documents</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>Receive</td>
<td>Posting fiscal documents for receiving:
<ul>
<li>Inventory items</li>
<li>Services</li>
<li>Fixed assets with bookkeeping of deferred ICMS tax amounts</li>
<li>Goods for use and consumption</li>
<li>From vendors that aren't ICMS payers/contributors (using models 1, 1-A, and 55)</li>
<li>Direct import (using models 1, 1-A, and 55)</li>
<li>(IPI, ICMS) Tax and price complementary fiscal documents</li>
<li>Vendor invoices (not dependent on purchase orders)</li>
</ul>
</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Referenced fiscal documents</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Fiscal documents with referenced processes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Multiple processes referenced by fiscal document texts</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Tax adjustments during receipt of inbound fiscal documents</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Electronic fiscal document XML and DANFE received from a POP3 (Post Office Protocol version 3) email account</td>
<td>No</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Validation of electronic fiscal document access key in SEFAZ</td>
<td>No</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Archiving of electronic fiscal document XML together with the posted received fiscal document</td>
<td>No</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Matching the quantity and price unit from the received electronic fiscal document XML with the vendor invoice from the purchase order</td>
<td>No</td>
<td>Yes</td>
</tr>
<tr>
<td>Purchase return</td>
<td>Issuing fiscal document for vendor returns</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>Sell</td>
<td>Sales quotations, sales orders, free text invoices, and project invoices localized to support Brazilian taxes per the Brazilian localization scope</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Input of transport information for fiscal documents</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Fiscal document texts in sales orders and free text invoices</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Cancel issued fiscal documents</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>Invoicing</td>
<td>Issuing fiscal documents for invoicing:
<ul>
<li>Inventory items</li>
<li>Services</li>
<li>Fixed assets</li>
<li>Third-party sales</li>
<li>Project invoices</li>
<li>For end users</li>
<li>For customers in SUFRAMA</li>
<li>(IPI, ICMS) Tax and price complementary fiscal documents</li>
</ul>
</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Referenced fiscal documents</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Fiscal document with referenced processes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Multiple processes referenced by fiscal document texts</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Withholding tax for IRRF, INSS, and ISS</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Outbound fiscal document viewer</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Display approximated taxes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Manual maintenance of Ficha Conte&uacute;do de Importa&ccedil;&atilde;o (FCI) by product, fiscal establishment, and period</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>The localization supports issuing fiscal document models 1, 1-A, and 55, and the Services fiscal document for S&atilde;o Paulo city. Partners must customize the requirements or behavior for unsupported fiscal document models.
<p><strong>Note:</strong> The localization doesn't support generation of FCI files, subsequent operation, automatic sending of FCI files, and automatic calculation of importation composition.</p>
</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>Sales return</td>
<td>Customer returns with your organization's fiscal document</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Customer returns with a fiscal document issued by the customer</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Electronic fiscal document access key</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>Inventory</td>
<td>Issue and receive fiscal documents for transfers/returns of inventory items between fiscal establishments</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Issue and receive fiscal documents for remittance/returns of inventory items from a third party</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>Production</td>
<td>Indirect and direct cost absorption only over production orders from discrete manufacturing</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>NF-e (Federal)</td>
<td><span style="display: inline !important; float: none; background-color: #ffffff; color: #000000; cursor: text; font-family: Verdana,Arial,Helvetica,sans-serif; font-size: 14px; font-style: normal; font-variant: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: left; text-decoration: none; text-indent: 0px; text-transform: none; -webkit-text-stroke-width: 0px; white-space: normal; word-spacing: 0px;">Support for NF-e layout 4.0</span></td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>NF-e messages/events:
<ul>
<li>Issue</li>
<li>Cancel</li>
<li>Discard</li>
<li>Electronic correction letter (CC-e)</li>
</ul>
</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Contingency mode: security form (FS or FS-DA)</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Contingency mode: SCAN</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Contingency mode: SVC</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>XML viewer for issued and received electronic fiscal documents</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Automatic sending of electronic fiscal document through email for customers, vendors, and transportation companies</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td><strong>Out of scope:</strong> Overall purpose services in the NF-e</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>NFS-e Services (S&atilde;o Paulo city)</td>
<td>Service electronic fiscal document using .txt files</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Recibo Provis&oacute;rio de Servi&ccedil;os (RPS) for S&atilde;o Paulo city</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>Financial and treasury</td>
<td>Withholding IRRF, PIS, COFINS, CSLL, ISS, and INSS taxes on payments and receiving</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Withholding IRRF, PIS, and COFINS tax threshold by legal entity</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Payment with check per bank</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Payment with Brazilian Border&ocirc;</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Interest and fines on payments and receiving, applying federal, state, and city holiday calendars</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Interest, fines, and withholding tax on centralized payments</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Electronic payment based on configurable files for the FCC-400 layout</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Electronic receiving based on configurable files for the CNAB-240 layout</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>General ledger</td>
<td>Accounting consolidation with transaction detailed transfers</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Fiscal document for ICMS tax credit transfer between fiscal establishments</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Fiscal document for 1/48 ICMS tax credits</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Legal reports:
<ul>
<li>Day book</li>
<li>Analytical ledger</li>
<li>Trial balance</li>
</ul>
</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td>Enterprise POS</td>
<td>Customer CPF/CNPJ on fiscal receipts</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>File generation for Nota Fiscal Paulista</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Tax calculation according to Microsoft Dynamics AX 2012 configuration</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Fiscal printer integration for Daruma printers, models FS600, FS700 (H, L and M), FS800i, Mach 1, Mach 2, and Mach 3</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Fiscal printer integration for Bematech printers, models MP2100 FI TH FI and MP4200 TH FI II</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>POS legal requirements according to PAF-ECF law "ATO COTEPE/ICMS N&deg;9" of 2013, except for any businesses identified as out of scope in the <a href="#out-of-scope">Out of scope</a> section of this topic</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>POS legal requirements according to PAF-ECF law "ATO COTEPE/ICMS N&deg;46" of 2014, except for any businesses identified as out of scope in the <a href="#out-of-scope">Out of scope</a> section</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Display approximated taxes in fiscal receipts</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Void last fiscal receipt</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Payments with multiple credit cards</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>EFT integration with third-party software D-TEF Dedicado, version 8.1.37.2, commercialized by Dire&ccedil;&atilde;o Processamento de Dados Ltda</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>EFT integration with third-party software SiTef, version 4.0.111.6, commercialized by Software Express Inform&aacute;tica Ltda
<p>Presales according to PAF-ECF law "ATO COTEPE/ICMS N&deg;46" of 2014</p>
</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Issuing return NF-e in EPOS for sales return</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Issuing NF-e linked to fiscal receipt in EPOS</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Configurable AOS for NF-e/NFC-e messaging with SEFAZ</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>The EFT service must be contracted directly from the third-party provider and isn't included in any Microsoft software license.
<p><strong>Note:</strong> Because of conflicts with the PAF-ECF legislation, not all Enterprise POS operations are permitted in Brazil. For more details, see the <a href="https://www.microsoft.com/download/details.aspx?id=42938">Retail and Enterprise POS Localization for Brazil white paper.</a></p>
</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td>NFC-e (Nota Fiscal ao Consumidor Eletr&ocirc;nica) in Enterprise POS</td>
<td><span style="display: inline !important; float: none; background-color: #ffffff; color: #000000; cursor: text; font-family: Verdana,Arial,Helvetica,sans-serif; font-size: 14px; font-style: normal; font-variant: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: left; text-decoration: none; text-indent: 0px; text-transform: none; -webkit-text-stroke-width: 0px; white-space: normal; word-spacing: 0px;">Support for layout NFC-e 4.0</span></td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Contingency mode: off-line</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Contingency mode for SP: SAT (model 59)</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Sales presence type: in-person</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td>Commerce</td>
<td>Commerce item management:
<ul>
<li>Released products by category</li>
<li>Mass update worksheet</li>
<li>Product hierarchy</li>
</ul>
</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>SAT (model 59) for S&atilde;o Paulo state layout 0.07</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Support for only one SAT hardware per EPOS</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Support for SAT DLL selection, for multiple-brand compatibility</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Fiscal receipt reference</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Fiscal printer auto-configuration</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td>Project accounting (PSA)</td>
<td>Credit notes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>TMS</td>
<td>Issuing outbound fiscal documents and electronic fiscal documents from loads for sales order invoices</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Issuing outbound fiscal documents and electronic fiscal documents from loads from transfer orders and fiscal document slips</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>Call center</td>
<td>Support for Brazilian tax registration ID (CNPJ/CPF) in customer data management</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>Fiscal books</td>
<td>Fiscal books reports:
<ul>
<li>IPI tax assessment</li>
<li>ICMS tax assessment</li>
<li>ICMS-ST tax assessment for states with IE registration</li>
<li>Incoming and Incoming model 1A</li>
<li>Outgoing and Outgoing model 2A</li>
<li>Inventory models 3 and 7</li>
<li>CIAP control report</li>
<li>ISS Report model 51 (delivering services)</li>
<li>ISS Report model 56 (acquiring services)</li>
<li>ECF daily operations report (Mapa Resumo)</li>
</ul>
</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Tax assessments</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Generation of tax assessment and payment of the following taxes:
<ul>
<li>IPI</li>
<li>ICMS and ICMS-ST</li>
<li>ICMS DIFAL</li>
<li>ISS</li>
</ul>
</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Generation of tax assessment and payment of the following taxes:
<ul>
<li>INSS CPRB</li>
</ul>
</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Generation of tax assessment and payment of the following taxes:
<ul>
<li>PIS and COFINS regime Cumulative</li>
<li>PIS and COFINS regime Non-Cumulative</li>
<li>Both</li>
</ul>
</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td><span style="display: inline !important; float: none; background-color: #ffffff; color: #000000; cursor: text; font-family: Verdana,Arial,Helvetica,sans-serif; font-size: 14px; font-style: normal; font-variant: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: left; text-decoration: none; text-indent: 0px; text-transform: none; -webkit-text-stroke-width: 0px; white-space: normal; word-spacing: 0px;">CIAP control and manual registration of ICMS installments</span></td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>
<div>&nbsp;SPED Fiscal</div>
<div>(ICMS, IPI)</div>
</td>
<td>Generation of a text file and support for companies defined as Profile A
<p>Available layout versions:</p>
<ul>
<li>Layout Code 14 and earlier</li>
</ul>
</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Support for the following records for companies defined as Profile A:
<ul>
<li>Block 0: 0000-0001-0002-0005-0015-0100-0150-0190-0200-0210-0220-0300-0305-0400-0450-0460-0500-0600-0990</li>
<li>Block C: C001-C100-C101-C110-C111-C113-C114-C120-C130-C140-C141-C160-C170-C172-C180-C185-C190-C191-C195-C400-C405-C410-C420-C460-C470-C490-C500(incoming)-C590 (incoming)-C990</li>
<li>Block D (only for incoming fiscal documents): D001-D100-D190-D195-D500-D590-D990</li>
<li>Block E: E001-E100-E110-E111-E116-E200-E210-E220-E250-E300-E310-E311-E312-E313-E316-E500-E510-E520-E530-E990</li>
<li>Block G: G001-G110-G125-G126-G130-G140-G990</li>
<li>Block H: H001-H005-H010-H020-H030-H990. Note: H005 and related records are only supported for reason code = 01, 05 for RS state and 06.</li>
<li>Block K: K001-K100-K200-K220-K230-K235</span></li>
<li>Block 1: 1001-1010-1250-12251990
<ul>
<li>Block 1900-1910-1920-1921-1923-1926-1990 only for Rio Grande do Sul state</li>
</ul>
</li>
</ul>
</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Resolution 13/2019 and Portaria SUCIEF 55/2019- RJ</td>
<td>&nbsp;Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td><strong>Out of scope:</strong> SPED Fiscal with specific requirements from the state/region, as described in the <a href="#brazilian-localization-strategy">Brazilian localization strategy</a> section of this topic, and companies that are categorized as Profile B and Profile C.</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>Portaria CAT 42/2018 - SP</td>
<td>
<ul style="color: #000000; font-family: Verdana,Arial,Helvetica,sans-serif; font-size: 14px; font-style: normal; font-variant: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: left; text-decoration: none; text-indent: 0px; text-transform: none; -webkit-text-stroke-width: 0px; white-space: normal; word-spacing: 0px;">
<li>Layout 1.1 B</li>
</ul>
</td>
<td>&nbsp;Yes</td>
<td>Yes</td>
</tr>
<tr>
<td><span style="display: inline !important; float: none; background-color: #ffffff; color: #000000; cursor: text; font-family: Verdana,Arial,Helvetica,sans-serif; font-size: 14px; font-style: normal; font-variant: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: left; text-decoration: none; text-indent: 0px; text-transform: none; -webkit-text-stroke-width: 0px; white-space: normal; word-spacing: 0px;">DRCST for Santa Catarina state</span></td>
<td>
<ul>
<li>SEF Portaria No. 396/2018</li>
<li>SEF Portaria No. 208/2019</li>
<li>SEF Portaria No. 254/2019</li>
<li>SEF Portaria No. 343/2019</li>
<li>SEF Portaria No. 416/2019</li>
<li>Records:
<ul>
<li>Block 0: 0000-0001-0005-0100-0190-0200-0220</li>
<li>Block 2: 2100-2110-2113-2114-2115-2120-2121-2130-2131-2132-2133-2134</li>
<li>Block H: H001-H005-H010-H990</li>
<li>Block 9: 9001-9900-9990-9999</li>
</ul>
</li>
</ul>
</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>

<td>SPED Contributions (PIS and COFINS)</td>
<td>Generation of a text file in accordance with layout 006 and earlier</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Support for company type Sociedade empresaria em geral</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Support for booking criteria Regime de Compet&ecirc;ncia &ndash; Escrituracao detalhada only</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Support for the following records:
<ul>
<li>Block 0: 0000-0001-0100-0110-0111-0140-0150-0190-0200-0400-0450-0900-0990</li>
<li>Block A: A001-A010-A100-A110-A111-A120-A170-A990</li>
<li>Block C: C001-C010-C100-C110-C111-C120-C170-C175-C180-C181-C185-C188-C190-C191-C195-C198-C199-C380-C381-C385-C400-C405-C481-C485-C490-C491-C495-C500-C501-C505-C509</li>
<li>Block D (only for incoming fiscal documents): D001-D010-D100-D101-D105-D111-D500-D501-D505-D509</li>
<li>Block F: F010-F100-F111-F120-F129-F130-F600-F700-F800-F990</li>
<li>Block M: M001-M100-M105-M110-M115-M200-M205-M210-M220-M225-M400-M410-M500-M505-M510-M515-M600-M606-M610-M620-M625-M800-M810-M990</li>
<li>Block 1: 1100-1010-1011-1300-1500-1700</li>
</ul>
</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>SPED ECF</td>
<td>Generation of a text file by using Management Reporter
<p>Layouts 005 and previous</p>
<p>Support for the following blocks and records:</p>
<ul>
<li>Block 0: 0000-0001-0010-0020-0030-0035-0930-0990</li>
<li>Block J: J001-J050-J051-J100</li>
<li>Block K: K001-K030-K155-K156-K355-K356-K990</li>
<li>Block V (DEREX): V001-V010-V020-V030-V100-V990</li>
</ul>
</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>SPED Reinf</td>
<td>
<div>Generation of events:</div>
<ul>
<li>R-1000, R-1070, R-2010, R-2020, R-2060, R-2098, R-2099, R-5011</li>
<li>Layout version 1.4</li>
</ul>
</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>SINTEGRA</td>
<td>Generation of text files in accordance with Version 3 - ICMS-76/03, which is available from <a href="http://www.sintegra.gov.br/">http://www.sintegra.gov.br</a></td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td>GIA-SP</td>
<td>Generation of GIA S&atilde;o Paulo state text files in accordance with version 08.00 (01/02/2013), which is available from <a href="http://www.fazenda.sp.gov.br/download/download_gia.shtm">http://www.fazenda.sp.gov.br/download/download_gia.shtm</a></td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>GIA-ST Nacional</td>
<td>Generation of GIA-ST text files in accordance with version 3.1, which is available from <a href="http://www.fazenda.sp.gov.br/download/downloadgiast.shtm">http://www.fazenda.sp.gov.br/download/downloadgiast.shtm</a></td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>SPED Accounting</td>
<td>Generation of SPED Cont&aacute;bil text files
<p>Layout version supported: 8.0 and earlier</p>
</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Support for bookkeeping type G (Day Book - Livro Diario) and the generation of the following blocks and records:
<ul>
<li>Block 0: 0000-0001-0007-0020-0035-0150-0180-0990</li>
<li>Block I: I001-I010-I030-I050-I051-I052-I100-I150-I155-I200-I250-I350-I355-I990</li>
<li>Block J: J001-J005-J100-J150-J800-J801-J900-J930-J932-J935-J999</li>
<li>Block 9: 9001-9900-9990-9999</li>
</ul>
</td>
<td>Yes</td>
<td>Yes</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>


## Out of scope

Some capabilities of Microsoft Dynamics that are generally available in other countries or regions might not be available in the Brazilian localization. The following items are out of scope or are otherwise not permitted for Brazil.

### Tax calculation requirements

The following tax calculation requirements are out of scope for the Brazilian localization:

- *Simples Nacional* or *Super Simples* taxation mode
- *Regime especial* taxation mode (see the [Notes](#notes) section of this topic)
- Requirements from states/regions other than the states/regions that are described in the [Brazilian localization strategy](#brazilian-localization-strategy) section of this topic
- Requirements from regulatory agencies or autarchies, such as SUFRAMA, ANVISA, or ANATEL

### Modules

The following modules are out of scope for the Brazilian localization:

- Budgeting
- Cost accounting
- Travel and expenses
- Compliance and internal controls
- Human resources
- Payroll
- Trade allowance management
- Service management
- Enterprise Portal for Microsoft Dynamics AX

### Features and functionality

The following features and functionality are out of scope for the Brazilian localization:

- Cash flow
- Collection management
- Posting definitions
- General journal service enhancements
- Accounts receivable invoice correction
- Prepayment associated with purchase order
- E-invoicing web portal
- Recurring invoices
- Archiving
- Quality management system
- Catalogs and categorization
- Auto-connecting invoice lines to packing slip lines
- Adding encryption for credit card processing on Online Services for Microsoft Dynamics
- Purchase order and packing slip correction
- Vendor self-service portal

### Industries

- **In general:** The following industry is out of scope for the Brazilian localization:

    - Public Sector

- **Commerce industry:**

    - **Services:** The following online services are out of scope for the commerce industry for the Brazilian localization:

        - Sites Services for Microsoft Dynamics ERP
        - Commerce Services for Microsoft Dynamics ERP
        - Modern POS and Commerce Scale Unit

    - **Retailers:** POS can't be used in the following businesses in states where compliance with the PAF-ECF law "ATO COTEPE/ICMS N° 46" of 2014 is mandatory:

        - Gas station
        - Restaurant
        - Hotel
        - Passenger transportation
        - Pharmacy/medicine preparation
        - Garage/repair shop
        - Toll road
        - Parking lot

    - **Fiscal printer features:** The following features and functionality for fiscal printers for businesses in Brazil are out of scope for the Brazilian localization:

        - Fiscal printers that have a different setup of tender types
        - Fiscal printers that have more than one registry for the same tax rate
        - Rounding of values, quantities, and amounts at the point of sale (POS) by using a different rule than the fiscal printer

    - **Tax calculation requirements:** The following tax calculation requirements for businesses in Brazil are out of scope for the Brazilian localization:

        - Tax discounts for sales through Enterprise POS in SUFRAMA or other Free Trade Zone

### Out of scope for fiscal books

The following tax reporting requirements are out of scope for fiscal books for the Brazilian localization:

- A printable version of fiscal books, in accordance with *AJUSTE SINIEF 2* from April 3, 2009, which the requirement for printed books obsolete
- SPED Fiscal that has specific requirements from the states/regions that are described in the [Brazilian localization strategy](#brazilian-localization-strategy) section of this topic
- *Simples Nacional* or *Super Simples* taxation mode
- *Regime especial* taxation mode (see the [Notes](#notes) section of this topic)
- Requirements from states/regions other than the states/regions that are described in the [Brazilian localization strategy](#brazilian-localization-strategy) section
- Requirements from regulatory agencies or autarchies, such as SUFRAMA, ANVISA, and ANATEL
- IN86
- GIA for states other than São Paulo
- Data upgrade for fiscal books from AX 2009 to AX 2012 R3 and Finance and Operations
- Data upgrade of fiscal documents from AX 2009 to AX 2012 R3 and Finance and Operations

## References

The [Microsoft Dynamics Localization Portal](https://mbs.microsoft.com/partnersource/deployment/resources/productreleases/gfmlocalizationportalmc.htm?printpage=false&sid=xdtafwuk1xh2l5jdjhhv0joy&stext=gfm%20localization%20portal) provides information about localization features and documents that have been released by Microsoft, and also localization features and documents that are planned for release.

## Notes

**Regime especial (special regime)** – Any differential treatment, with respect to general tax rule requirements (whether federal, state, or municipal) and ancillary obligations, that the tax authority authorizes, in peculiar cases, to simplify tax compliance by the taxpayer. This differential treatment doesn't include relief from taxation.

## Brazilian tax terms and abbreviations

| Term or abbreviation | Description |
|----------------------|-------------|
| **A**                | |
| ANATEL               | Telecommunication regulatory agency |
| ANVISA               | Health and medical regulatory agency |
| **C**                | |
| CNPJ                 | Federal tax registration number for companies |
| CIAP                 | Control over installments of ICMS tax credit for acquired fixed assets |
| COFINS               | Contribution based on gross revenues from business sales |
| CFOP                 | Fiscal code operation |
| CSLL                 | Social contribution tax on net profit |
| **D**                | |
| DARF                 | Payment voucher that must be fulfilled for federal tax payment |
| DCTF                 | Debit and credit assessment for federal taxes |
| DIRF                 | Assessment of federal withholding taxes |
| **G**                | |
| GNRE                 | Payment voucher that must be fulfilled for state tax payment |
| GIA                  | ICMS tax assessment and payment declaration |
| **I**                | |
| IPI                  | Tax on manufactured goods |
| ICMS                 | Tax on transit of goods and services |
| ICMS ST              | ICMS tax substitution |
| ISS                  | Tax on services |
| IRRF                 | Tax on profit |
| IE                   | State tax registration number for companies |
| IM                   | City tax registration number for companies |
| INSS                 | Contribution for social security |
| IN-86                | Instruction \#86 from the federal tax authority, which describes the rules about how and how long companies must hold fiscal and accounting digital data for tax auditing |
| II                   | Importation tax |
| **N**                | |
| Nota fiscal          | Fiscal document |
| **P**                | |
| PIS                  | Contribution for the social integration program |
| **S**                | |
| SPED                 | Public digital bookkeeping system |
| SINTEGRA             | Information system for interstate goods and service transactions |
| SEFAZ                | State tax authority |
| SUFRAMA              | Autarchy for economic development of the Amazon region |
