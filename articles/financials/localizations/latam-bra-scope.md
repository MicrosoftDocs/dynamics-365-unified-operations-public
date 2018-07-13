---
# required metadata

title: Scope of the Brazilian localization
description: This topic describes the strategy and scope for tax, finance, and accounting laws and regulations in Brazil that have been implemented as part of Microsoft Dynamics AX 2012 R2, R3 and Dynamics 365 for Operations. 
author: sndray
manager: AnnBe
ms.date: 07/13/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
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


Scope of the Brazilian localization 
====================================

This document describes the strategy and scope for tax, finance, and accounting
laws and regulations in Brazil that have been implemented as part of Microsoft
Dynamics AX 2012 R2, R3 and Dynamics 365 for Operations. It is intended for
channel partners and end users of AX 2012 R2, R3 and Dynamics 365 for Operations
. Channel partners or end users who use this information when implementing other
versions of Microsoft Dynamics AX do so at their own risk.

Scope of the Brazilian localization
===================================

In general, Microsoft invests significant resources on extending the business
process functionality of Microsoft Dynamics applications, by developing features
and functionality to address specific tax, accounting, or financial regulatory
requirements in countries/regions where Microsoft makes Microsoft Dynamics
generally available.

Microsoft Dynamics AX helps organizations run their business operations while
managing their obligations to comply with country/region-specific laws,
regulations, and common business practices for handling their daily activities.
This software includes features and functionality that are designed to address
specific federal tax, accounting, financial, or statutory reporting laws or
regulations that commonly affect businesses in Brazil.

However, Microsoft Dynamics AX does not address all laws, regulations, or
commercial requirements in Brazil, because laws and regulations vary in the way
they affect organizations. For example, regulatory features that Microsoft
creates and makes generally available “out of the box” for Microsoft Dynamics AX
in Brazil typically do not include functionality that supports National
Standards, industry-specific regulations (such as for agriculture), vertical
regulations (such as for oil and gas or chemicals), or state, city, or municipal
requirements, except as specifically noted in this document.

Channel partners are an important part of our global strategy for delivering
Microsoft Dynamics AX to help customers meet local laws and regulatory
requirements for Brazil. By utilizing the extensible nature of the development
architecture of Microsoft Dynamics AX, channel partners can address a customer’s
specific business needs during implementation either through configuration of
the software (when available), or through partner-created customizations or
localizations (when needed). Although channel partners might provide solutions
that meet specific regulatory requirements that are unique to municipalities,
cities, states, or other regions in Brazil, Microsoft does not provide any
guarantees or warranties (expressed, implied, statutory, or otherwise) that
partner-created solutions comply with local business, tax and regulatory, legal,
or other applicable requirements.

Channel partners or customers are solely responsible for any configurations,
customizations, localizations, or translations (and also any update for each of
these) that they create or implement on behalf of customers, including any
support or other service provided to customers for such solutions. You must
contact your channel partner for information about the solutions that the
channel partner creates for licensed versions of Microsoft Dynamics AX.

This document describes the strategy and scope of certain requirements that
Microsoft has implemented as part of the Microsoft Dynamics AX software that it
made generally commercially available in Brazil.

Definitions
===========

**Customization** refers to (a) any configuration, modifications, or changes
that partners or customers make either to the Microsoft Dynamics software or,
when applicable, to the software documentation to fit a customer’s specific
business needs (such as adding or renaming fields or tables, creating custom
reports, or integrating with third-party solutions); or (b) any software
developed for the Microsoft Dynamics software.

**Localization** refers to any modification to, addition to, or adaptation of
the Microsoft Dynamics software to enable or include certain features or
functionality in the software to conform to applicable regulatory requirements
(including, without limitation, versions and updates of the Microsoft Dynamics
software, user assistance tools, and end-user documentation). Examples of laws
or regulatory requirements that might require localization of the software
include local tax reporting (such as for sales tax, value-added tax [VAT], and
goods and services tax [GST]), invoice tracking by a government authority,
government-required tax calculations, local accounting rules, and local
regulatory and statutory reporting.

**National Standards** refer to feature requirements in software that are
related primarily to banking practices (such as payment methods, payment
formats, and bank statements) and less frequently to commercial documents (such
as electronic fiscal documents). National Standards are local requirements that
are not required by law or regulation, but that are widely adopted within a
geographic region and critical to the sale of licenses for business management
software in that geographic region.

Brazilian localization strategy
-------------------------------

In general, the Microsoft strategy for addressing the tax, financial,
accounting, or statutory reporting requirements for Brazil consists of providing
localizations for Microsoft Dynamics AX that do the following:

-   Implement the federal tax requirements detailed in the [Brazilian
    localization scope](#brazilian-localization-scope) section.

-   Implement, for the following states, the state/region requirements detailed
    in the [Brazilian localization scope](#brazilian-localization-scope)
    section: São Paulo (SP), Rio de Janeiro (RJ), Paraná (PR), Santa Catarina
    (SC), and Rio Grande do Sul (RS).

-   Deliver certain new regulatory features through configurations or
    development of new functionality that implements the federal and
    state/region requirements detailed in the [Brazilian localization
    scope](#brazilian-localization-scope) section, in accordance with the
    business rules specified in this document and the Microsoft Dynamics AX
    roadmap.

-   Deliver certain new regulatory features in the most recent service pack
    available, or in a new service pack, for supported versions of Microsoft
    Dynamics AX.

-   Apply National Standards and competitive features in the localization that
    Microsoft, at its sole discretion, determines to be necessary or
    appropriate, based on business needs in the region.

-   Do not focus on the requirements of specific businesses, segments,
    verticals, regions, or large enterprises, even when required by laws,
    statutes, or regulations at the federal, state, or city levels.

-   Do not include municipal requirements, except for the ones detailed in the
    [Brazilian localization scope](#brazilian-localization-scope) section.

There are specific laws and requirements that are out of scope for Microsoft
Dynamics AX. These are listed in the [Out of scope](#out-of-scope) section later
in this document.

The Brazilian localization for Microsoft Dynamics AX developed by Microsoft is
limited to the features and functionality described in this document. As a
result, Microsoft Dynamics AX must be analyzed by prospective customers or a tax
professional, such as an accounting and tax auditor, tax law firm, or tax
consulting firms, who can perform an assessment to determine whether the
functionality is appropriate to meet the customer’s business needs, or whether
custom solutions are required.

Brazilian localization scope
----------------------------

The user interface and online Help for Microsoft Dynamics AX are translated into
Brazilian Portuguese. Additional documentation, such as white papers and
training materials, might be available in English only and might not be
available when the software is first made generally available in Brazil.

The localization scope for Microsoft Dynamics AX available in Brazil is limited
to tax calculation, accounting transactions, issuing/receiving fiscal documents,
and issuing fiscal receipts in the following four scenarios: procure to pay,
quote to cash, retail, and regulatory/statutory reporting.

The features that Microsoft delivers and supports as part of the Brazilian
localization for Microsoft Dynamics AX are listed in
[Table 1](#table-1-brazilian-localization-features). Details about each of the
features can be found in Help within Microsoft Dynamics AX, and in white papers
that are published on the [Microsoft Dynamics Localization
Portal](https://mbs.microsoft.com/partnersource/deployment/resources/productreleases/gfmlocalizationportalmc.htm?printpage=false&sid=xdtafwuk1xh2l5jdjhhv0joy&stext=gfm%20localization%20portal).

Market availability
-------------------

Microsoft aims to deliver regulatory features with enough time for installation.
Our goal is to release tax and regulatory updates that contain required changes
in advance of the effective date or other date mandated by the applicable
government authority, whether at the federal or state level (but only for the
states identified in the [Brazilian localization
strategy](#brazilian-localization-strategy) section), to implement the tax,
accounting, financial, or regulatory/statutory reporting requirements that
commonly affect a majority of businesses in Brazil, so that our channel partners
have sufficient time to update their customer solutions. Internally, we call
this the *market required date* (MRD).

We strive to meet our established MRDs and dates mandated by the applicable
government authority. However, various factors can adversely affect the timely
delivery of tax and regulatory updates. These factors include the following:

-   Legislative or regulatory changes made by the government with insufficient
    notice prior to the date that the law takes effect

-   Feature, functionality, infrastructure, or architectural limitations of the
    affected software versions generally available in the marketplace

-   The complexity and coverage of the coding, redesign, or enhancement of the
    software required to implement the legislation or regulatory requirements;
    or schedule conflicts

If it is not feasible to meet these dates, we use commercially reasonable
efforts to develop and release tax and regulatory updates as soon as possible.

Any dates that Microsoft publishes are for planning purposes only and are
subject to change at any time without notice.

Microsoft makes no representations, warranties, or guarantees about the
timeliness or completeness of any tax or regulatory update that it provides and,
to the maximum extent permitted under applicable law, disclaims all implied
warranties and conditions, such as implied warranties or conditions of
merchantability and fitness for a particular purpose.

Table 1 – Brazilian localization features
-----------------------------------------

<table>
<thead>
<tr>
<th>Area</th>
<th>Item</th>
<th>AX 2012 RTM-R2</th>
<th>AX 2012 R3</th>
<th>Finance and Operations</th>
</tr>
</thead>
<tbody>
<tr>
<td>Master data</td>
<td>Legal entity and fiscal establishment tax identifiers:
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
<td>Yes</td>
</tr>
<tr>
<td></td>
<td>Customer and vendor tax identifiers:
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
<td>Yes</td>
</tr>
<tr>
<td></td>
<td>Item tax characteristics:
<ul>
<li>Fiscal classification code an exception</li>
<li>Taxation origin</li>
<li>Product type</li>
</ul>
</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td></td>
<td>CFOP table
</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>Taxes</td>
<td>Tax types: IPI, ICMS, ICMS tax substitution, ICMS difference, DIFAL, Importation tax, PIS, COFINS, CSLL, IRRF, INSS, Retained INSS, and ISS
</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td></td>
<td>Taxation mode per tax type:
<ul>
<li>1 – Taxable</li>
<li>2 – Exempt or non-taxable</li>
<li>3 – Others</li>
</ul>
</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td></td>
<td>Tax credit based on taxation mode</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td></td>
<td>ICMS base reduction</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td></td>
<td>ICMS tax substitution with calculation based on markup</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td></td>
<td>Simplified ICMS tax substitution
</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td></td>
<td>Independent configuration for ICMS base reduction and tax substitution
</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td></td>
<td>IPI tax on the final user
</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td></td>
<td>ICMS for user and consumption</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td></td>
<td>ICMS, PIS, and COFINS tax discounts for sales to SUFRAMA</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td></td>
<td>ICMS difference over sales in final consumer (DIFAL)
</td>
<td>No</td>
<td>Yes</td>
<td>Yes</td>
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
<td>Support for Global CFDI layout 3.3 in customer receipts (Retail)</td>
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

-   CNPJ/CPF

-   IE

-   CCM

-   IE for tax substitution for multiples states

-   CNAE

-   CNPJ/CPF

-   IE

-   CCM

-   NIT

-   INSS-CEI

-   CNAE

-   Fiscal classification code and exception

-   Taxation origin

-   Product type

-   1 – Taxable

-   2 – Exempt or non-taxable

-   3 – Others

-   Inventory items

-   Services

-   Fixed assets with bookkeeping of deferred ICMS tax amounts

-   Goods for use and consumption

-   From vendors that are not ICMS payers/contributors (using models 1, 1-A, and
    55)

-   Direct import (using models 1, 1-A, and 55)

-   (IPI, ICMS) Tax and price complementary fiscal documents

-   Vendor invoices (not dependent on purchase orders)

-   Inventory items

-   Services

-   Fixed assets

-   Third-party sales

-   Project invoices

-   For end users

-   For customers in SUFRAMA

-   (IPI, ICMS) Tax and price complementary fiscal documents

-   Issue

-   Cancel

-   Discard

-   Electronic correction letter (CC-e)

-   Day book

-   Analytical ledger

-   Trial balance

-   Released products by category

-   Mass update worksheet

-   Retail product hierarchy

-   IPI tax assessment

-   ICMS tax assessment

-   ICMS-ST tax assessment for states with IE registration

-   Incoming and Incoming model 1A

-   Outgoing and Outgoing model 2A

-   Inventory models 3 and 7

-   CIAP control report

-   ISS Report model 51 (delivering services)

-   ISS Report model 56 (acquiring services)

-   ECF daily operations report (Mapa Resumo)

-   IPI

-   ICMS and ICMS-ST

-   ICMS DIFAL

-   ISS

-   INSS CPRB

-   Registration and posting of adjustment transactions for ICMS, ICMS\_ST, and
    IPI taxes

-   Registration and posting of non-fiscal operations with calculation of PIS
    and COFINS taxes

-   Tax payment integration with the Accounts payable module

-   Layout Code 08 – Version 1.07 From 01.01.2014 to 12.31.2014

-   Layout Code 09 – Version 1.08 From 01.01.2015 to 12.31.2015

-   Layout Code 10 – Version 1.09 From 01.01.2016 to 12.31.2016

-   Layout Code 10 – Version 1.09 From 01.01.2016 to 12.31.2016

-   Block 0  
    0000-0001-0005-0015-0100-0150-0190-0200-0220-0300-0305-0400-0450-0460-0500-0600-0990

-   Block C  
    C001-C100-C101-C110-C111-C113-C120-C130-C140-C141-C160-C170-C172-C190-C195-C400-C405-C410-C420-C460-C470-C490-C500(incoming)-C590
    (incoming)-C990

-   Block D (only for incoming fiscal documents)  
    D001-D100-D190-D195-D500-D590-D990

-   Block E  
    E001-E100-E110-E111-E116-E200-E210-E220-E250-E300-E310-E311-E312-E313-E316-E500-E510-E520-E530-E990

-   Block G  
    G001-G110-G125-G126-G130-G140-G990

-   Block H  
    H001-H005-H010-H990

-   Block 1  
    1001-1010-1990

-   Block 0  
    0000-0001-0100-0110-0140-0150-0190-0200-0400-0450-0990

-   Block A  
    A001-A010-A100-A110-A111-A120-A170-A990

-   Block C  
    C001-C010-C100-C110-C111-C120-C170-C180-C181-C185-C188-C190-C191-C195-C198-C199-C380-C381-C385-C400-C405-C481-C485-C490-C491-C495-C500-C501-C505-C509

-   Block D (only for incoming fiscal documents)  
    D001-D010-D100-D101-D105-D111-D500-D501-D505-D509

-   Block F  
    F010-F100-F111-F600-F990

-   Block C

C175

-   Block F  
    F120-F129-F130-F139-F700-F800

-   Block M

M001-M100-M105-M110-M115-M200-M205-M210-M220-M225-M400-M410-M500-M505-M510-M515-M600-M606-M610-M620-M625-M800-M810-M990

-   Block 1

1100-1300-1500-1700

-   Block 0  
    0000-0001-0010-0020-0030-0035-0930-0990

-   Block J  
    J001-J050-J051-J100

-   Block K  
    K001-K030-K155-K156-K355-K356-K990

-   Bloco V (DEREX)

V001-V010-V020-V030-V100-V990

-   Block 0  
    0000-0001-0007-0220-0990

-   Block I  
    I001-I010-I020-I050-I052-I100-I150-I155-I200-I250-I350-I355-I990

-   Block J  
    J001-J005-J100-J150-J900-J930-J999

-   Block 9  
    9900-9999

**Out os scope**: Referenced chart of account (mapping between local CoA and
government CoA).

-   Sped Fiscal

-   EFD Contributions

-   Sped ECD and ECF

-   GIA-SP

-   GIA-ST

-   Sintegra

Out of scope 
-------------

Certain capabilities of Microsoft Dynamics AX that are generally available in
other countries/regions might not be available in the Microsoft Dynamics AX
Brazilian localization. The following items are out of scope or otherwise not
permitted for Brazil.

### Tax calculation requirements

The following tax calculation requirements are out of scope for the Microsoft
Dynamics AX Brazilian localization:

-   *Simples Nacional* or *Super Simples* taxation mode

-   *Regime especial* taxation mode (see the [Notes](#notes) section later in
    this document)

-   Requirements from states/regions other than those described in the
    [Brazilian localization strategy](#brazilian-localization-strategy) section

-   Requirements from regulatory agencies or autarchies, such as SUFRAMA,
    ANVISA, or ANATEL

### Modules

The following modules are out of scope for the Microsoft Dynamics AX Brazilian
localization:

-   Budgeting

-   Cost accounting

-   Travel and expenses

-   Compliance and internal controls

-   Human resources

-   Payroll

-   Trade allowance management

-   Service management

-   Enterprise Portal for Microsoft Dynamics AX

### Features and functionality

The following features and functionality are out of scope for the Microsoft
Dynamics AX Brazilian localization:

-   Cash flow

-   Collection management

-   Posting definitions

-   General journal service enhancements

-   Accounts receivable invoice correction

-   Prepayment associated with purchase order

-   E-invoicing web portal

-   Recurring invoices

-   Archiving

-   Quality management system

-   Catalogs and categorization

-   Auto-connecting invoice lines to packing slip lines

-   Adding encryption for credit card processing on Online Services for
    Microsoft Dynamics

-   Purchase order and packing slip correction

-   Vendor self-service portal

### Industries

-   **In general:** The following industry is out of scope for the Microsoft
    Dynamics AX Brazilian localization:

    -   Public Sector

-   **Retail industry**:

    -   **Retail services:** The following online services are out of scope for
        the retail industry for the Microsoft Dynamics AX Brazilian
        localization:

        -   Sites Services for Microsoft Dynamics ERP

        -   Commerce Services for Microsoft Dynamics ERP

        -   Modern POS and Retail server

    -   **Retailers:** Retail POS cannot be used in the following retail
        businesses in states where compliance with the PAF-ECF law “ATO
        COTEPE/ICMS N° 46” of 2014, is mandatory:

        -   Gas station

        -   Restaurant

        -   Hotel

        -   Passenger transportation

        -   Pharmacy/medicine preparation

        -   Garage/repair shop

        -   Toll road

        -   Parking lot

    -   **Fiscal printer features:** The following features and functionality
        for fiscal printers for retail businesses in Brazil are out of scope for
        the Microsoft Dynamics AX for Brazilian localization

        -   Fiscal printers with a different setup of tender types

        -   Fiscal printers with more than one registry for the same tax rate

        -   Rounding of values, quantities, and amounts at the point of sale by
            using a different rule than the fiscal printer

Out of scope for fiscal books 
------------------------------

The following tax reporting requirements are out of scope for fiscal books for
the Brazilian localization:

-   A printable version of fiscal books, in accordance with *AJUSTE SINIEF 2*,
    from April 3, 2009, which deprecated the requirement for printed books

-   SPED Fiscal with specific requirements from the states/regions described in
    the [Brazilian localization strategy](#brazilian-localization-strategy)
    section

-   *Simples Nacional* or *Super Simples* taxation mode

-   *Regime especial* taxation mode (see the [Notes](#notes) section)

-   Requirements from states/regions other than those described in the
    [Brazilian localization strategy](#brazilian-localization-strategy) section

-   Requirements from regulatory agencies or autarchies, such as SUFRAMA,
    ANVISA, and ANATEL

-   IN86

-   GIA for states other than São Paulo

-   Data upgrade for fiscal books from AX 2009 to AX 2012 R3 and Dynamics 365

-   Data upgrade of fiscal documents from AX 2009 to AX 2012 R3 and Dynamics 365

References
==========

The [Microsoft Dynamics Localization
Portal](https://mbs.microsoft.com/partnersource/deployment/resources/productreleases/gfmlocalizationportalmc.htm?printpage=false&sid=xdtafwuk1xh2l5jdjhhv0joy&stext=gfm%20localization%20portal)
provides information about localization features and documents that have been
released by Microsoft, and also those that are planned for release.

Notes
=====

**Regime especial (special regime)** – Any differential treatment, in peculiar
cases, in respect to general tax rule requirements (whether federal, state, or
municipal) and ancillary obligations authorized by the tax authority, to
simplify tax compliance by the taxpayer, but without relief from taxation.

Brazilian tax terms and abbreviations
=====================================

| **Term or abbreviation** | **Description**                                                                                                                                                      |
|--------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **A**                    |                                                                                                                                                                      |
| ANATEL                   | Telecommunication regulatory agency                                                                                                                                  |
| ANVISA                   | Health and medical regulatory agency                                                                                                                                 |
| **C**                    |                                                                                                                                                                      |
| CNPJ                     | Federal tax registration number for companies                                                                                                                        |
| CIAP                     | Control over installments of ICMS tax credit for acquired fixed assets                                                                                               |
| COFINS                   | Contribution based on gross revenues from business sales                                                                                                             |
| CFOP                     | Fiscal code operation                                                                                                                                                |
| CSLL                     | Social contribution tax on net profit                                                                                                                                |
| **D**                    |                                                                                                                                                                      |
| DARF                     | Payment voucher that needs to be fulfilled for federal tax payment                                                                                                   |
| DCTF                     | Debit and credit assessment for federal taxes                                                                                                                        |
| DIRF                     | Assessment of federal withholding taxes                                                                                                                              |
| **G**                    |                                                                                                                                                                      |
| GNRE                     | Payment voucher that needs to be fulfilled for state tax payment                                                                                                     |
| GIA                      | ICMS tax assessment and payment declaration                                                                                                                          |
| **I**                    |                                                                                                                                                                      |
| IPI                      | Tax on manufactured goods                                                                                                                                            |
| ICMS                     | Tax on transit of goods and services                                                                                                                                 |
| ICMS ST                  | ICMS tax substitution                                                                                                                                                |
| ISS                      | Tax on services                                                                                                                                                      |
| IRRF                     | Tax on profit                                                                                                                                                        |
| IE                       | State tax registration number for companies                                                                                                                          |
| IM                       | City tax registration number for companies                                                                                                                           |
| INSS                     | Contribution for social security                                                                                                                                     |
| IN-86                    | Instruction \#86 from the federal tax authority, describing the rules about how and how long companies must hold fiscal and accounting digital data for tax auditing |
| II                       | Importation tax                                                                                                                                                      |
| **N**                    |                                                                                                                                                                      |
| Nota fiscal              | Fiscal document                                                                                                                                                      |
| **P**                    |                                                                                                                                                                      |
| PIS                      | Contribution for the social integration program                                                                                                                      |
| **S**                    |                                                                                                                                                                      |
| SPED                     | Public digital bookkeeping system                                                                                                                                    |
| SINTEGRA                 | Information system for interstate goods and service transactions                                                                                                     |
| SEFAZ                    | State tax authority                                                                                                                                                  |
| SUFRAMA                  | Autarchy for economic development of the Amazon region                                                                                                               |

