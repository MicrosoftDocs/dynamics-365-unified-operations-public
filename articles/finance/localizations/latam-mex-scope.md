---
title: Scope of Mexican localization
description: This article describes the strategy and scope for tax, finance, and accounting laws and regulations in Mexico.
author: AdamTrukawka
ms.date: 04/11/2018
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Mexico
ms.author: atrukawk
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.search.form: 
---

# Scope of Mexican localization

[!include[banner](../includes/banner.md)]

In general, Microsoft invests significant resources to extend business process functionality by developing features and functionality that address specific tax, accounting, or financial regulatory requirements in countries or regions where Microsoft makes Dynamics 365 Finance generally available.

Dynamics 365 Finance helps organizations run their business operations and also manage their obligations to comply with country/region-specific laws, regulations, and common business practices for handling their daily activities. This software includes features and functionality that are designed to address specific federal tax, accounting, financial, or statutory reporting laws or regulations that commonly affect businesses in Mexico.

However, Finance doesn't address all laws, regulations, or commercial requirements in Mexico, because laws and regulations vary in the way that they affect organizations. For example, regulatory features that Microsoft creates that are made generally available out-of-the-box for Finance in Mexico, don't typically include functionality that supports the following, except as noted in this article:

- National/Regional Standards
- Payroll
- Industry-specific regulations
- Vertical regulations 
- State, city, or municipal requirements

Additional details are available in the [Localization Availability Guide](https://aka.ms/ax-availabilityguide).

Channel partners are an important part of our global strategy for helping customers meet requirements for Mexico. By taking advantage of the extensible nature of the development architecture of Finance, channel partners can address a customer's specific business needs during implementation through either of the following approaches:

- Configuration of the software (when available)
- Partner-created customizations or localizations (when required)

Although channel partners might provide solutions that meet specific regulatory requirements that are unique to municipalities, cities, states, or other regions in Mexico, Microsoft doesn't provide any guarantees or warranties (expressed, implied, statutory, or otherwise) that partner-created solutions comply with local business, tax and regulatory, legal, or other applicable requirements.

Channel partners or customers are solely responsible for any configurations, customizations, localizations, or translations that they create or implement on behalf of customers, and also for any updates to such solutions. They are also solely responsible for any support or other service that is provided to customers for these solutions. Contact your channel partner for information about the solutions that the channel partner creates for licensed versions of Finance.

This article describes the strategy and scope of specific requirements that Microsoft has implemented as part of the finance and operations software that it made generally available in Mexico.

## Terminology and abbreviations
**Customization** refers to:

- Any configuration, modifications, or changes that partners or customers make either to the Microsoft Dynamics software itself or, when applicable, to the software documentation to fit a customer's specific business needs. Examples include adding or renaming fields or tables, creating custom reports, or integrating with third-party solutions.
- Any software that is developed for the Microsoft Dynamics software.

**Localization** refers to any modification to, addition to, or adaptation of the Microsoft Dynamics software to enable or include specific features or functionality in the software so that it conforms to applicable regulatory requirements (including, without limitation, versions and updates of the Microsoft Dynamics software, user assistance tools, and end-user documentation). Here are some examples of laws or regulatory requirements that might require localization of the software:

- Local tax reporting, such as reporting for sales tax, value-added tax (VAT), and goods and services tax (GST)
- Invoice tracking by a government authority
- Government-required tax calculations
- Local accounting rules
- Local regulatory and statutory reporting

**National/Regional Standards** refer to feature requirements in software that are related primarily to banking practices (such as payment methods, payment formats, and bank statements) and less frequently to commercial documents (such as electronic fiscal documents). National/Regional Standards are local requirements that aren't required by law or regulation, but that are widely adopted within a geographic region and critical to the sale of licenses for business management software in that geographic region.

| Abbreviation | Description |
|--------------|-------------|
| CFD          | Electronic invoices by one's own means (self-submission) – Comprobantes fiscales digitales |
| CFDI         | Electronic invoices by internet – Comprobantes fiscales digitales por internet |
| DIOT         | Declaration of operations with a third party – Declaración informativa de operaciones con terceros |
| IEPS         | Special tax over manufacturing and services – Impuesto Especial sobre Producción y Servicios |
| ISR          | Income tax – Impuesto sobre la Renta |
| IVA          | VAT sales tax – Impuesto al Valor Agregado |
| PAC          | Authorized digital signature service provider – Proveedores autorizados de certificación |
| SAT          | Tax administration Service – Servicio de Administración Tributaria |
| UUID         | Universally unique identifier – Identificador universalmente único |

## Mexican localization strategy

In general, the Microsoft strategy for addressing the tax, financial, accounting, or statutory reporting requirements for Mexico consists of providing localizations that:

- Implement the federal tax requirements that are detailed in the [Mexican localization scope](#mexican-localization-scope) section later in this article.
- Deliver specific new regulatory features through configurations or through the development of new functionality that implements the federal requirements that are detailed in the [Mexican localization scope](#mexican-localization-scope) section, in accordance with the information that is specified in this article.
- Deliver specific new regulatory features in the most recent service pack that is available, or in a new service pack, for supported versions of Finance.
- Apply National/Regional Standards and competitive features in the localization, as Microsoft, at its sole discretion, determines them to be necessary or appropriate, based on business needs in the region.
- Don't focus on the requirements of specific businesses, segments, verticals, regions, or large enterprises, even when these requirements are required by laws, statutes, or regulations at the federal, state, or city levels.
- Exclude municipal requirements, except for the municipal requirements that are detailed in the [Mexican localization scope](#mexican-localization-scope) section.

There are specific laws and requirements that are out of scope for Finance. These laws and requirements are listed in the [Out of scope](#out-of-scope) section later in this article.

The Mexican localizations that Microsoft develops are limited to the features and functionality that is described in this article. Therefore, Finance must be analyzed by prospective customers or by a tax professional (such as an accounting and tax auditor, tax law firm, or tax consulting firm) who can perform an assessment to determine whether the functionality is appropriate to meet the customer's business needs, or whether custom solutions are required.

## Mexican localization scope
The user interface and online Help are translated into Mexican Spanish. Additional documentation, such as white papers and training materials, might be available in English only and might not be available when the software is first made generally available in Mexico.

The localization scope for the version of Finance that is available in Mexico is limited to tax calculation, accounting transactions, and issuing and receiving invoices in the following scenarios: 

- Procure to pay
- Quote to cash
- Regulatory/statutory reporting

For a list of the specific features that Microsoft delivers and supports, see the [Supported features](#supported-features) section later in this document. You can find details about each feature in Help within Finance, in online Help, and in white papers that are published on the [Microsoft Dynamics Localization Portal](/dynamics/s-e/).

## Market availability
Microsoft aims to deliver regulatory features in a manner that provides enough time for installation or updates to existing customer solutions. If tax and regulatory updates contain changes required to implement tax, accounting, financial, or regulatory/statutory reporting requirements that commonly affect a majority of businesses in Mexico, our goal is to release the updates before the effective date or by any other mandated date as required at the federal or state level. For more information, see [Mexican localization strategy](#mexican-localization-strategy). 

We strive to meet our established MRDs and dates that are mandated by the applicable government authority. However, various factors can affect the timely delivery of tax and regulatory updates. These factors include:

- Legislative or regulatory changes that the government makes without enough notice before the date that the law takes effect
- Feature, functionality, infrastructure, or architectural limitations of the affected software versions that are generally available in the marketplace
- The complexity and coverage of the coding, redesign, or enhancement of the software that is required to implement the legislation or regulatory requirements, or schedule conflicts

If it isn't feasible to meet these dates, we use commercially reasonable efforts to develop and release tax and regulatory updates as soon as possible.

Any dates that Microsoft publishes are for planning purposes only and are subject to change at any time without notice.

Microsoft makes no representations, warranties, or guarantees about the timeliness or completeness of any tax or regulatory update that it provides, and, to the maximum extent that is permitted under applicable law, disclaims all implied warranties and conditions, such as implied warranties or conditions of merchantability and fitness for a particular purpose.

## Supported features
The following table lists the specific features that Microsoft delivers and supports as part of the Mexican localizations for past and present versions of our product.

<table>
<thead>
<tr>
<th>Area</th>
<th>Item</th>
<th>Dynamics AX 2009</th>
<th>Dynamics AX 2012 RTM-R2</th>
<th>Dynamics AX 2012 R3</th>
<th>Finance</th>
</tr>
</thead>
<tbody>
<tr>
<td>Master data</td>
<td>Legal entity tax identifiers:
<ul>
<li>RFC (Mexican tax ID – Registro Federal de Contribuyentes)</li>
<li>CURP (Unique Population Registry Code – Clave Única de Registro de Población)</li>
<li>Company type</li>
<li>State inscription</li>
<li>Tax regime</li>
</ul>
</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td></td>
<td>Customer tax identifiers:
<ul>
<li>RFC</li>
<li>CURP</li>
<li>Company type</li>
<li>State inscription</li>
</ul>
</td>
<td>RFC only</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td></td>
<td>Vendor tax identifiers:
<ul>
<li>RFC</li>
<li>CURP</li>
<li>Company type</li>
<li>State inscription</li>
</ul>
</td>
<td>RFC only</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td></td>
<td>Vendor tax identifiers for the DIOT declaration:
<ul>
<li>Type of vendor</li>
<li>Type of operation</li>
<li>Tax registration ID for foreign</li>
<li>Country/region code</li>
<li>Nationality</li>
</ul>
</td>
<td>No</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td></td>
<td>Bank tax identifiers:
<ul>
<li>RFC</li>
</ul></td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td></td>
<td>Tax types:
<ul>
<li>VAT (IVA)</li>
<li>ISR</li>
<li>IEPS</li>
</ul>
</td>
<td>No</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>Taxes<br>(Calculation by Core functionality)</td>
<td>VAT regular and conditional tax</td>
<td>Regular</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td></td>
<td>IEPS</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td></td>
<td>ISR regular</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>Procure<br>(Receive goods and service invoice)</td>
<td>Input UUID of the CFDI document:
<ul>
<li>Purchase invoice</li>
<li>Vendor invoice</li>
<li>Invoice register</li>
<li>General journal</li>
</ul>
</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td></td>
<td>Input series and invoice number:
<ul>
<li>Purchase invoice</li>
<li>Vendor invoice</li>
<li>Invoice register</li>
<li>General journal</li>
</ul>
</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td></td>
<td>Input of related information for the DIOT declaration:
<ul>
<li>Purchase invoice</li>
<li>Vendor invoice</li>
<li>Invoice register</li>
<li>General journal</li>
<li>Project – Expense</li>
<li>Project – Journal Fee</li>
</ul>
</td>
<td>No</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>CFD</td>
<td>Support for CFD layout 2.0</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td></td>
<td>Support for CFD layout 2.2</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td></td>
<td>CFD messages/events:
<ul>
<li>Issue</li>
</ul>
</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td></td>
<td>Printable CFD version in PDF format</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td></td>
<td>XML viewer for issued CFD invoices</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td></td>
<td>Automatic sending of the CFD document by email to customers during the posting process</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td></td>
<td>Generation of a monthly report</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td>CFDI</td>
<td>Support for CFDI layout 3.0 in customer invoices</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td></td>
<td>Support for CFDI layout 3.2 in customer invoices</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td></td>
<td>Support for CFDI layout 3.3 in customer invoices</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td></td>
<td>Support for CFDI layout 3.3 in customer payments with payment complement 1.0</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td></td>
<td>Support for CFDI layout 3.3 in customer advance payments:
<ul>
<li>CFDI advance payment</li>
<li>CFDI invoice and settlement</li>
<li>CFDI advance payment reverse</li>
</ul>
</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td></td>
<td>Support for CFDI layout 3.3 in packing slip and transfer orders between sites (TRASLADOS)</td>
<td>No</td>
<td>No</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td></td>
<td>Support for CFDI layout 3.3 in foreign customer invoices and foreign complement 1.1</td>
<td>No</td>
<td>No</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td></td>
<td>Support for Global CFDI layout 3.3 in customer receipts (Commerce)</td>
<td>No</td>
<td>No</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td></td>
<td>Support for CFDI withholding layout 1.0</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td></td>
<td>CFDI messages/events:
<ul>
<li>Issue</li>
<li>Cancel</li>
<li>Manual Cancel</li>
</ul>
</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td></td>
<td>Printable CFDI version in PDF format that includes a bidimensional bar code</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td></td>
<td>XML viewer for issued CFDI invoices</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td></td>
<td>Automatic sending of CFD documents by email to customers during the posting process</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>PAC</td>
<td>Microsoft only provides a code example for PAC integration by using web server certificate authentication.</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>DIOT</td>
<td>Generation of the DIOT declaration as a text file</td>
<td>No</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>Adjustment inflation</td>
<td>Generation and registration of the Adjustment inflation process</td>
<td>No</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>ISR declaration</td>
<td>Generation of the ISR declaration report</td>
<td>No</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>VAT reports</td>
<td>Generation of VAT reports:
<ul>
<li>Sales</li>
<li>Purchase</li>
</ul>
</td>
<td>No</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>Electronic ledger accounting statement</td>
<td>Generation of electronic ledger accounting XML files:
<ul>
<li>Chart of Account</li>
<li>Trial Balance</li>
<li>Ledger entries with related documents (folios)</li>
<li>Auxiliary ledger account</li>
</ul>
</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
</tbody>
</table>

## Out of scope
Some capabilities that are generally available in other countries or regions might not be available in the Mexican localizations of our product. The following items are out of scope or are otherwise not permitted for Mexico.

### Requirements
The following specific requirements are out of scope for Mexican localizations:

- Foreign trade (incoming).
- Impuesto Empressarial a Tasa Única (IETU) tax declaration.
- PAC integration to certify the CFDI electronic invoice document.

    Microsoft doesn't support integration with all available and authorized PAC web services. Companies must customize service references for the selected solution and then configure the client authentication (certificate) to generate the CFDI invoice (XML message). Microsoft provides the generation of the XML message and a code example that shows how to integrate with PAC web services. This code example is included in all supported version of CFDI, and it was developed and tested by using integration with the Interfactura PAC web services.

    Client authentication by using a user name and password isn't currently supported.

- Generation of CFDI for Payroll documents.
- The electronic ledger accounting XML files don't include the digital stamp.
- Requirements from states/regions other than those requirements described in the [Mexican localization strategy](#mexican-localization-strategy) section of this article.
- Requirements from regulatory agencies or autarchies other than SAT.

### Modules
The following modules are out of scope for Mexican localizations:

- Budgeting
- Cost accounting
- Travel and expenses
- Compliance and internal controls
- Human resources
- Payroll
- Commerce
- Call center
- Trade allowance management
- Transportation management
- Service management
- Enterprise Portal for Microsoft Dynamics AX

### Features and functionality
The following features and functionality are out of scope for Mexican localizations:

- Cash flow
- Collection management
- General journal service enhancements
- Accounts receivable invoice correction
- Prepayment associated with purchase order
- E-invoicing web portal
- Recurring invoices
- Archiving
- Quality management system
- Catalogs and categorization
- Adding encryption for credit card processing on Online Services for Microsoft Dynamics
- Vendor self-service portal

### Industries
- **In general** The following industry is out of scope for Mexican localizations:

    - Public Sector

- **Commerce industry**

    - **Services** The following online services are out of scope for the commerce industry for Mexican localizations:

        - Sites Services for Microsoft Dynamics ERP
        - Commerce Services for Microsoft Dynamics ERP
        - Modern POS and RCommerce Scale Unit

    - **Retailers**
    - **Fiscal printer features**

## References
The [Microsoft Dynamics Localization Portal](/dynamics/s-e/) provides information about localization features and documents that have been released by Microsoft, and also those that are planned for release.

## Notes
**Regime especial (special regime)** refers to any differential treatment, except relief from taxation, that the tax authority authorizes with respect to general tax rule requirements (federal, state, or municipal) and ancillary obligations, to simplify tax compliance by the taxpayer in peculiar cases.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
