---
# required metadata

title: Scope of Mexican localization
description: This topic describes the strategy and scope for tax, finance, and accounting laws and regulations in Mexico that have been implemented as part of Microsoft Dynamics AX or Microsoft Dynamics 365 for Finance and Operations. 
author: sndray
manager: AnnBe
ms.date: 04/11/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Mexico
# ms.search.industry: 
ms.author: sndray
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Scope of the Mexican localization

[!include[banner](../includes/banner.md)]

In general, Microsoft invests significant resources on extending the business process functionality of Microsoft Dynamics applications, by developing features and functionality to address specific tax, accounting, or financial regulatory requirements in countries/regions where Microsoft makes Microsoft Dynamics generally available. 

Microsoft Dynamics AX helps organizations run their business operations while managing their obligations to comply with country/region-specific laws, regulations, and common business practices for handling their daily activities. This software includes features and functionality that are designed to address specific federal tax, accounting, financial, or statutory reporting laws or regulations that commonly affect businesses in Mexico.

However, Microsoft Dynamics AX does not address all laws, regulations, or commercial requirements in Mexico, because laws and regulations vary in the way they affect organizations. For example, regulatory features that Microsoft creates and makes generally available “out of the box” for Microsoft Dynamics AX in Mexico typically do not include functionality that supports National Standards, Payroll, industry-specific regulations (such as for agriculture), vertical regulations (such as for oil and gas or chemicals), or state, city, or municipal requirements, except as specifically noted in this document.

Channel partners are an important part of our global strategy for delivering Microsoft Dynamics AX to help customers meet requirements for Mexico. By utilizing the extensible nature of the development architecture of Microsoft Dynamics AX, channel partners can address a customer’s specific business needs during implementation either through configuration of the software (when available), or through partner-created customizations or localizations (when needed). Although channel partners might provide solutions that meet specific regulatory requirements that are unique to municipalities, cities, states, or other regions in Mexico, Microsoft does not provide any guarantees or warranties (expressed, implied, statutory, or otherwise) that partner-created solutions comply with local business, tax and regulatory, legal, or other applicable requirements.

Channel partners or customers are solely responsible for any configurations, customizations, localizations, or translations (and also any update for each of these) that they create or implement on behalf of customers, including any support or other service provided to customers for such solutions. You must contact your channel partner for information about the solutions that the channel partner creates for licensed versions of Microsoft Dynamics AX.

This document describes the strategy and scope of certain requirements that Microsoft has implemented as part of the Microsoft Dynamics AX software that it made generally commercially available in Mexico.

## Definitions and terminology
**Customization** refers to (a) any configuration, modifications, or changes that partners or customers make either to the Microsoft Dynamics software or, when applicable, to the software documentation to fit a customer’s specific business needs (such as adding or renaming fields or tables, creating custom reports, or integrating with third-party solutions); or (b) any software developed for the Microsoft Dynamics software.

**Localization** refers to any modification to, addition to, or adaptation of the Microsoft Dynamics software to enable or include certain features or functionality in the software to conform to applicable regulatory requirements (including, without limitation, versions and updates of the Microsoft Dynamics software, user assistance tools, and end-user documentation). Examples of laws or regulatory requirements that might require localization of the software include local tax reporting (such as for sales tax, value-added tax [VAT], and goods and services tax [GST]), invoice tracking by a government authority, government-required tax calculations, local accounting rules, and local regulatory and statutory reporting.

**National Standards** refer to feature requirements in software that are related primarily to banking practices (such as payment methods, payment formats, and bank statements) and less frequently to commercial documents (such as electronic fiscal documents). National Standards are local requirements that are not required by law or regulation, but that are widely adopted within a geographic region and critical to the sale of licenses for business management software in that geographic region.

|Term or abbreviation	|Description|
|---------------------|-----------------------|
|CFD	|Electronic invoices by own means. Self-submission – Comprobantes fiscales digitales|
|CFDI|	Electronic invoices by internet - Comprobantes fiscales digitales por internet|
|DIOT|	Declaration of operations with third party|
|IEPS|	Special tax over manufacturing and services|
|ISR|	Income tax|
|IVA|	VAT Sales tax|
|PAC|	Authorized digital signature service provider – Proveedores autorizados de Certificación|
|SAT|	Tax administration Service (Servicio de Administración Tributaria)|
|UUID|	Universal Unique identificator (Identificador Universalmente Único)|

## Mexican localization strategy

In general, the Microsoft strategy for addressing the tax, financial, accounting, or statutory reporting requirements for Mexico consists of providing localizations for AX or Finance and Operations that do the following: 
-	Implement the federal tax requirements detailed in the Mexican localization scope section.
-	Deliver certain new regulatory features through configurations or development of new functionality that implements the federal requirements detailed in the Mexican localization scope section, in accordance with the business rules specified in this document.
-	Deliver certain new regulatory features in the most recent service pack available, or in a new service pack, for supported versions of AX or Finance and Operations.
-	Apply National Standards and competitive features in the localization that Microsoft, at its sole discretion, determines to be necessary or appropriate, based on business needs in the region.
-	Do not focus on the requirements of specific businesses, segments, verticals, regions, or large enterprises, even when required by laws, statutes, or regulations at the federal, state, or city levels.
-	Do not include municipal requirements, except for the ones detailed in the Mexican localization scope section.

There are specific laws and requirements that are out of scope for AX or Finance and Operations. These are listed in the Out of scope section later in this document.

The Mexican localizations for AX and Finance and Operations developed by Microsoft is limited to the features and functionality described in this document. As a result, AX and Finance and Operations must be analyzed by prospective customers or a tax professional, such as an accounting and tax auditor, tax law firm, or tax consulting firms, who can perform an assessment to determine whether the functionality is appropriate to meet the customer’s business needs, or whether custom solutions are required.

## Mexican localization scope
The user interface and online Help for AX and Finance and Operations are translated into Mexican Spanish. Additional documentation, such as white papers and training materials, might be available in English only and might not be available when the software is first made generally available in Mexico.

The localization scope for Microsoft Dynamics AX available in Mexico is limited to tax calculation, accounting transactions, and issuing/receiving invoices in the following four scenarios: procure to pay, quote to cash and regulatory/statutory reporting.

The features that Microsoft delivers and supports as part of the Mexican localization for Microsoft Dynamics AX are listed in Table 1. Details about each of the features can be found in Help within Microsoft Dynamics AX, and in white papers that are published on the [Microsoft Dynamics Localization Portal](https://mbs.microsoft.com/partnersource/deployment/resources/productreleases/gfmlocalizationportalmc.htm?printpage=false&sid=xdtafwuk1xh2l5jdjhhv0joy&stext=gfm%20localization%20portal).

## Market availability
Microsoft aims to deliver regulatory features with enough time for installation. Our goal is to release tax and regulatory updates that contain required changes in advance of the effective date or other date mandated by the applicable government authority, whether at the federal identified in the Mexican localization strategy section), to implement the tax, accounting, financial, or regulatory/statutory reporting requirements that commonly affect a majority of businesses in Mexico, so that our channel partners have sufficient time to update their customer solutions. Internally, we call this the market required date (MRD).

We strive to meet our established MRDs and dates mandated by the applicable government authority. However, various factors can adversely affect the timely delivery of tax and regulatory updates. These factors include the following:
-	Legislative or regulatory changes made by the government with insufficient notice prior to the date that the law takes effect
-	Feature, functionality, infrastructure, or architectural limitations of the affected software versions generally available in the marketplace
-	The complexity and coverage of the coding, redesign, or enhancement of the software required to implement the legislation or regulatory requirements; or schedule conflicts

If it is not feasible to meet these dates, we use commercially reasonable efforts to develop and release tax and regulatory updates as soon as possible.

Any dates that Microsoft publishes are for planning purposes only and are subject to change at any time without notice.

Microsoft makes no representations, warranties, or guarantees about the timeliness or completeness of any tax or regulatory update that it provides and, to the maximum extent permitted under applicable law, disclaims all implied warranties and conditions, such as implied warranties or conditions of merchantability and fitness for a particular purpose.

## Table 1
<table>
  <tr>
    <th>Area</th>
    <th>Item</th>
    <th>AX 2009</th>
    <th>AX 2012 RTM-R2</th>
    <th>AX 2012 R3</th>
    <th>Finance and Operations</th>
  </tr>
  
  <tr>
    <td>Master data</td>
    <td>Legal entity tax identifiers:
  <ul>
    <li>RFC</li>
    <li>CURP</li>
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
    <td>Only RFC</td>
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
    <td>Only RFC</td>
    <td>Yes</td>
    <td>Yes</td>
    <td>Yes</td>
  </tr>
    <tr>
    <td></td>
    <td>Vendor tax identifiers for DIOT declaration
   <ul>
    <li>Type of vendor</li>
    <li>Type of operation</li>
    <li>Tax registration ID for foreign</li>
    <li>Country/Region code</li>
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
    <td>Taxes</td>
    <td>VAT regular and conditional tax</td>
    <td>Regular</td>
    <td>Yes</td>
    <td>Yes</td>
    <td>Yes</td>
  </tr>
  <tr>
    <td>(Calulation by Core functionality)</td>
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
    <td>Procure <br></br> Receive goods and service invoice</td>
    <td>Input UUID of CFDI document
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
    <td>Input Series and invoice number
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
    <td>Input of related information for DIOT declaration
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
    <td>Support to CFD layout 2.0</td>
    <td>P</td>
    <td>P</td>
    <td>P</td>
    <td>O</td>
  </tr>
  <tr>
    <td></td>
    <td>Support to CFD layout 2.2</td>
    <td>P</td>
    <td>P</td>
    <td>P</td>
    <td>O</td>
  </tr>
  <tr>
    <td></td>
    <td>CFD messages/events: Issue</td>
    <td>P</td>
    <td>P</td>
    <td>P</td>
    <td>O</td>
  </tr>
  <tr>
    <td></td>
    <td>Printatble CFD version in PDF format</td>
    <td>P</td>
    <td>P</td>
    <td>P</td>
    <td>O</td>
  </tr>
  <tr>
    <td></td>
    <td>XML viewer for issued CFD invoice</td>
    <td>P</td>
    <td>P</td>
    <td>P</td>
    <td>O</td>
  </tr>
  <tr>
    <td></td>
    <td>Automatic sending of CFD document through email to customers during posting process.</td>
    <td>P</td>
    <td>P</td>
    <td>P</td>
    <td>O</td>
  </tr>
  <tr>
    <td></td>
    <td>Generation of Montlhy report</td>
    <td>P</td>
    <td>P</td>
    <td>P</td>
    <td>O</td>
  </tr>
  <tr>
    <td>CFDI</td>
    <td>Support to CFDI layout 3.0 in customer invoices</td>
    <td>P</td>
    <td>P</td>
    <td>P</td>
    <td>P</td>
  </tr>
  <tr>
    <td></td>
    <td>Support to CFDI layout 3.2 in customer invoices</td>
    <td>P</td>
    <td>P</td>
    <td>P</td>
    <td>P</td>
  </tr>
  <tr>
    <td></td>
    <td>Support to CFDI Layout 3.3 in customer invoices</td>
    <td>P</td>
    <td>P</td>
    <td>P</td>
    <td>P</td>
  </tr>
  <tr>
    <td></td>
    <td>Support to CFDI Layout 3.3 in customer payments with payment complement 1.0</td>
    <td>P</td>
    <td>P</td>
    <td>P</td>
    <td>P</td>
  </tr>
  <tr>
    <td></td>
    <td>Support to CFDI Layout 3.3 in customer advance payments</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>·        CFDI advance payment</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>·        CFDI invoice and settlement</td>
    <td>P</td>
    <td>P</td>
    <td>P</td>
    <td>P</td>
  </tr>
  <tr>
    <td></td>
    <td>·        CFDI advance payment reverse</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Support to CFDI Layout 3.3 in packing slip and transfer orders between different sites (TRASLADOS)</td>
    <td>O</td>
    <td>O</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td>P</td>
    <td>P</td>
  </tr>
  <tr>
    <td></td>
    <td>Support to CFDI Layout 3.3 in foreign customer invoices and foreign complement 1.1</td>
    <td>O</td>
    <td>O</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td>P</td>
    <td>P</td>
  </tr>
  <tr>
    <td></td>
    <td>Support to Global CFDI Layout 3.3 in customer receipts (Retail)</td>
    <td>O</td>
    <td>O</td>
    <td>P</td>
    <td>P</td>
  </tr>
  <tr>
    <td></td>
    <td>Support to CFDI withholding Layout 1.0</td>
    <td>P</td>
    <td>P</td>
    <td>P</td>
    <td>P</td>
  </tr>
  <tr>
    <td></td>
    <td>CFDI messages/events:</td>
    <td>P</td>
    <td>P</td>
    <td>P</td>
    <td>P</td>
  </tr>
  <tr>
    <td></td>
    <td>•      Issue</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>•      Cancel</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>•      Manual Cancel</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Printatble CFDI version in PDF format including Bidimensional bar code</td>
    <td>P</td>
    <td>P</td>
    <td>P</td>
    <td>P</td>
  </tr>
  <tr>
    <td></td>
    <td>XML viewer for issued CFDI invoice</td>
    <td>P</td>
    <td>P</td>
    <td>P</td>
    <td>P</td>
  </tr>
  <tr>
    <td></td>
    <td>Automatic sending of CFD document through email to customers during posting process</td>
    <td>P</td>
    <td>P</td>
    <td>P</td>
    <td>P</td>
  </tr>
  <tr>
    <td>PAC</td>
    <td>Microsoft only provides a code example for PAC integration by using Web server certificate authentication.</td>
    <td>P</td>
    <td>P</td>
    <td>P</td>
    <td>P</td>
  </tr>
  <tr>
    <td>DIOT</td>
    <td>Generation of DIOT declaration as text file</td>
    <td>O</td>
    <td>P</td>
    <td>P</td>
    <td>P</td>
  </tr>
  <tr>
    <td>Adjustment inflation</td>
    <td>Generation and registration of Ajudustment inflation process</td>
    <td>O</td>
    <td>P</td>
    <td>P</td>
    <td>P</td>
  </tr>
  <tr>
    <td>ISR declaration</td>
    <td>Generation of ISR declaration report</td>
    <td>O</td>
    <td>P</td>
    <td>P</td>
    <td>P</td>
  </tr>
  <tr>
    <td>VAT reports</td>
    <td>Generation of VAT reports</td>
    <td>O</td>
    <td>P</td>
    <td>P</td>
    <td>P</td>
  </tr>
  <tr>
    <td></td>
    <td>·        Sales</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>·        Purchase</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Electronic ledger accounting statement</td>
    <td>Generation of electronic ledger accounting XML files:</td>
    <td>P</td>
    <td>P</td>
    <td>P</td>
    <td>P</td>
  </tr>
  <tr>
    <td></td>
    <td>·        Chart of Account</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>·        Trial Balance</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>·        Ledger entries with related documents (folios)</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>·        Auxiliary ledger account</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</table>

## Out of scope 
Certain capabilities of Microsoft Dynamics AX that are generally available in other countries/regions might not be available in the Microsoft Dynamics AX Mexican localization. The following items are out of scope or otherwise not permitted for Mexico.

The following specific requirements are out of scope for the Microsoft Dynamics AX Mexican localization:
-	Foreign trade (incoming)
-	IETU tax declaration
-	PAC integration to certify the CFDI electronic invoce document. 
Microsoft does not support integration with all available and authorized PAC web services, companies must to customize service references for the selected solution and then configure the client authentication (certificate) to generate the CFDI invoice (XML message). Microsoft provides the generation of XML message and a code example of how to integrate with a PAC web services. This code example is included in all supported version of CFDI and it was developed and tested by using Interfactura PAC web services integration
Client authentication with user and password are not currently supported. 
-	Generation of CFDI for Payrroll documents
-	The Electronic ledger accounting XML files don’t include the digital stamp
-	Requirements from states/regions other than those described in the Mexican localization strategy section
-	Requirements from regulatory agencies or autarchies, other than SAT. 

## Modules
The following modules are out of scope for the Microsoft Dynamics AX Mexican localization: 
-	Budgeting
-	Cost accounting
-	Travel and expenses
-	Compliance and internal controls
-	Human resources
-	Payroll
-	RetScoeail
-	Call center
-	Trade allowance management
-	Transportation management
-	Service management
-	Enterprise Portal for Microsoft Dynamics AX

## Features and functionality
The following features and functionality are out of scope for the Microsoft Dynamics AX Mexican localization: 
-	Cash flow
-	Collection management
-	General journal service enhancements
-	Accounts receivable invoice correction
-	Prepayment associated with purchase order
-	E-invoicing web portal
-	Recurring invoices
-	Archiving
-	Quality management system
-	Catalogs and categorization
-	Adding encryption for credit card processing on Online Services for Microsoft Dynamics
-	Vendor self-service portal

## Industries
-	In general: The following industry is out of scope for the Microsoft Dynamics Mexican localization: 
-	Public Sector
-	Retail industry:
-	Retail services: The following online services are out of scope for the retail industry for the Microsoft Dynamics AX Mexican localization: 
-	Sites Services for Microsoft Dynamics ERP
-	Commerce Services for Microsoft Dynamics ERP
-	Modern POS and Retail server
-	Retailers
-	Fiscal printer features

## References
The Microsoft Dynamics Localization Portal provides information about localization features and documents that have been released by Microsoft, and also those that are planned for release.

## Notes
Regime especial (special regime) – Any differential treatment, in peculiar cases, in respect to general tax rule requirements (whether federal, state, or municipal) and ancillary obligations authorized by the tax authority, to simplify tax compliance by the taxpayer, but without relief from taxation
