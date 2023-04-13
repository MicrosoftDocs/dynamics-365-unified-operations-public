---
title: Scope of the Brazilian localization
description: This article describes the strategy and scope for tax, finance, and accounting laws and regulations in Brazil.
author: AdamTrukawka
ms.date: 11/22/2021
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Brazil
ms.author: atrukawk
ms.search.validFrom: 2018-04-30
ms.dyn365.ops.version: 8
---

# Scope of the Brazilian localization

[!include [banner](../includes/banner.md)]

This article describes the strategy and scope for Brazilian tax, finance, and accounting laws and regulations that Microsoft has included in Microsoft Dynamics 365 Finance for Brazil. 

In general, Microsoft invests significant resources on extending the business process functionality of Dynamics 365 Finance by developing features and functionality to address specific tax, accounting, or financial regulatory requirements in countries or regions where Microsoft makes Microsoft Dynamics generally available.

The software helps organizations run their business operations while complying with country/region-specific laws, regulations, and common business practices for handling their daily activities. This software includes features and functionality that are designed to address specific federal tax, accounting, financial, or statutory reporting laws or regulations that commonly affect businesses in Brazil.

However, Microsoft Dynamics doesn't address all laws, regulations, or commercial requirements in Brazil, because laws and regulations vary in the way that they affect organizations. Additional details are available in the [Localization Availability Guide](https://aka.ms/dynamics_365_international_availability_deck).

Channel partners are an important part of our global strategy for delivering Microsoft Dynamics to help customers meet local laws and regulatory requirements for Brazil. By taking advantage of the extensible nature of the development architecture of Microsoft Dynamics, channel partners can address a customer's specific business needs during implementation, either through configuration of the software (when configuration options are available), or through partner-created customizations or localizations (if customization or localization is required). Although channel partners might provide solutions that meet specific regulatory requirements that are unique to municipalities, cities, states, or other regions in Brazil, Microsoft doesn't provide any guarantees or warranties (expressed, implied, statutory, or otherwise) that partner-created solutions comply with local business, tax and regulatory, legal, or other applicable requirements.

Channel partners or customers are solely responsible for any configurations, customizations, localizations, or translations that they create or implement on behalf of customers. This responsibility also covers any updates for these solutions, and any support or other service that is provided to customers for such solutions. You must contact your channel partner for information about the solutions that the channel partner creates for licensed versions of Microsoft Dynamics.

## Definitions

**Customization** refers to either of the following:

- Any configuration, modifications, or changes that partners or customers make either to the Microsoft Dynamics software or, when applicable, to the software documentation to fit a customer's specific business needs. Examples include adding or renaming fields or tables, creating custom reports, or integrating with third-party solutions.
- Any software that partners or customers develop for the Microsoft Dynamics software.

**Localization** refers to any modification to, addition to, or adaptation of the Microsoft Dynamics software to enable or include specific features or functionality in the software so that it complies with applicable regulatory requirements (including, without limitation, versions and updates of the Microsoft Dynamics software, user assistance tools, and end-user documentation). Examples of laws or regulatory requirements that might require localization of the software include local tax reporting (such as for sales tax, value-added tax [VAT], and goods and services tax [GST]), invoice tracking by a government authority, government-required tax calculations, local accounting rules, and local regulatory and statutory reporting. 

**National Standards** refer to feature requirements in software that are primarily related to banking practices (such as payment methods, payment formats, and bank statements). Less often, the requirements are related to commercial documents (such as electronic fiscal documents). National Standards are local requirements that aren't required by law or regulation, but that are widely adopted within a geographic region and critical to the sale of licenses for business management software in that geographic region.

## <a name="brazilian-localization-strategy"></a>Brazilian localization strategy

In general, the Microsoft strategy for addressing the tax, financial, accounting, or statutory reporting requirements for Brazil consists of providing localizations for Microsoft Dynamics that do the following:

- They implement the federal tax requirements that are detailed in the [Brazilian localization scope](#brazilian-localization-scope) section of this article.
- They implement, for the following states, the state/region requirements that are detailed in the [Brazilian localization scope](#brazilian-localization-scope) section: São Paulo (SP), Rio de Janeiro (RJ), Paraná (PR), Santa Catarina (SC), and Rio Grande do Sul (RS).
- They deliver specific new regulatory features through configurations or development of new functionality that implements the federal and state/region requirements that are detailed in the [Brazilian localization scope](#brazilian-localization-scope) section, in accordance with the business rules that are specified in this article and the Microsoft Dynamics roadmap on the [Microsoft Dynamics Localization Portal](/dynamics/s-e/).
- They deliver specific new regulatory features in the most recent service pack that is available, or in a new service pack, for supported versions of Microsoft Dynamics.
- They apply National Standards and competitive features that Microsoft, at its sole discretion, determines to be necessary or appropriate, based on business needs in the region.
- They don't focus on the requirements of specific businesses, segments, verticals, regions, or large enterprises, even when these requirements are required by laws, statutes, or regulations at the federal, state, or city level.
- They don't include municipal requirements, except the municipal requirements that are detailed in the [Brazilian localization scope](#brazilian-localization-scope) section.

There are specific laws and requirements that are out of scope for Microsoft Dynamics. For a list, see the [Out of scope](#out-of-scope) section of this article.

The Brazilian localization that Microsoft developed for Microsoft Dynamics is limited to the features and functionality that are described in this article. Therefore, Microsoft Dynamics must be analyzed by prospective customers or a tax professional, such as an accounting and tax auditor, tax law firm, or tax consulting firms, who can assess whether the functionality is appropriate to meet the customer's business needs, or whether custom solutions are required.

## Brazilian localization scope

The user interface (UI) and online Help for Microsoft Dynamics are translated into Brazilian Portuguese. Additional documentation, such as white papers and training materials, might be available only in English and might not be available when the software is first made generally available in Brazil.

The localization scope for Microsoft Dynamics available in Brazil is limited to tax calculation, accounting transactions, issuing/receiving fiscal documents, and issuing fiscal receipts in the following four scenarios: procure to pay, quote to cash, commerce, and regulatory/statutory reporting.

The features that Microsoft delivers and supports as part of the Brazilian localization for Microsoft Dynamics are listed in the [Brazilian localization features](#brazilian-localization-features) section of this article. Details about each of the features can be found in Help in Microsoft Dynamics, and in white papers that are published on the [Microsoft Dynamics Localization Portal](/dynamics/s-e/).

## Market availability

The Microsoft goal is to deliver regulatory features in enough time for installation. To implement the tax, accounting, financial, or regulatory/statutory reporting requirements that typically affect a majority of businesses in Brazil, Microsoft aims to release tax and regulatory updates that contain required changes before the effective date or other date that is mandated by the applicable government authority at either the federal or state level (but only for the states that are identified in the [Brazilian localization strategy](#brazilian-localization-strategy) section of this article), so that our channel partners have enough time to update their customer solutions. Internally, we call this date the *market required date* (MRD).

Microsoft strives to meet its established MRDs and dates that are mandated by the applicable government authority. However, various factors can affect the timely delivery of tax and regulatory updates. Here are some examples:

- Legislative or regulatory changes that the government makes, but that it doesn't give enough notice about before the date when the law takes effect
- Feature, functionality, infrastructure, or architectural limitations of the affected software versions that are generally available in the marketplace
- The complexity and coverage of the coding, redesign, or enhancement that is required in the software to implement the legislation or regulatory requirements, or schedule conflicts

If it isn't feasible to meet these dates, we use commercially reasonable efforts to develop and release tax and regulatory updates as soon as possible.

Any dates that Microsoft publishes are for planning purposes only and are subject to change at any time without notice.

Microsoft makes no representations, warranties, or guarantees about the timeliness or completeness of any tax or regulatory update that it provides, and, to the maximum extent that is permitted under applicable law, disclaims all implied warranties and conditions, such as implied warranties or conditions of merchantability and fitness for a particular purpose.

## Brazilian localization features

The following sections list the features that are specific to Brazil. The sections are divided by area and provide information about the functionality and the availability in Dynamics AX 2012 R3 and Finance. 

### Master data

| Item | AX 2012 R3 |  Finance | 
| ---- | ---------- | -------- |
| Tax identifiers for legal entities and fiscal establishments:<br>- CNPJ/CPF<br>- IE<br>- CCM<br>- IE for tax substitution for multiple states <br>- CNAE | Yes | Yes |
| Tax identifiers for customers and vendors:<br>- CNPJ/CPF<br>- IE<br>- CCM<br>- NIT,br>- INSS-CEI<br>- CNAE | Yes | Yes |
| Item tax characteristics:<br>- Fiscal classification code and exception<br>- Taxation origin<br>- Product type | Yes | Yes |
|CFOP table | Yes | Yes |


### Taxes

| Item | AX 2012 R3 |  Finance | 
| ---- | ---------- | -------- |
| Tax types: IPI, ICMS, ICMS tax substitution, ICMS difference, DIFAL, Importation tax, PIS, COFINS, CSLL, IRRF, INSS, Retained INSS, and ISS | Yes | Yes |
| Taxation mode per tax type:<br>- 1-Taxable<br>- 2-Exempt or non-taxable<br>- 3-Others | Yes | Yes |
| Tax credit based on taxation mode | Yes | Yes |
| ICMS base reduction  | Yes | Yes |
| ICMS tax substitution with calculation based only on markup for outbound fiscal documents | Yes | Yes |
| Simplified ICMS tax substitution | Yes | Yes |
| Independent configuration for ICMS base reduction and tax substitution | Yes | Yes |
| IPI tax on teh final user | Yes | Yes |
| ICMS for use and consumption | Yes | Yes |
| ICMS, POS, and COFINS tax discounts for sales to SUFRAMA | Yes | Yes |
| ICMS difference over sales in final consumer (DIFAL) only for simplified base | Yes | Yes |
| ICMS difference over purchase | Yes | Yes |
| Configurable default taxes based on operations defined/specified per CFOP group | Yes | Yes |
| Calculation of PIS and COFINS reference to law 1.401/2013 during import | Yes | Yes |

### Procure

| Item | AX 2012 R3 |  Finance | 
| ---- | ---------- | -------- |
| Purchase requisitions, requests for quotation, and purchase orders localized to support the Brazilian taxes per the Brazilian localization scope | Yes | Yes |
| Fiscal document texts in purchase orders | Yes | Yes |
| Cancel inbound issues fiscal documents | Yes | Yes |
| Reverse received fiscal documents | Yes | Yes |

### Receive

| Item | AX 2012 R3 |  Finance | 
| ---- | ---------- | -------- |
| Posting fiscal documents for receiving:<br>- Inventory items<br>- Services<br>- Fixed assets with bookkeeping of deferred ICMS tax amounts<br>- Goods for use and consumption<br>- From vendors that aren't ICMS payers/contributors (using models 1, 1-A, and 55)<br>- Direct import (using models 1, 1-A, and 55)<br>- (IPI, ICMS) Tax and price complementary fiscal documents<br>- Vendor invoices (not dependent on purchase orders) | Yes | Yes |
| Referenced fiscal documents | Yes | Yes |
| Fiscal documents with referenced processes | Yes | Yes |
| Multiple processes referenced by fiscal document texts | Yes | Yes |
| Tax adjustments during receipt of inbound fiscal documents | Yes | Yes |
| Electronic fiscal document XML adn DANFE received from a POP3 (Post Office Protocol version 3) email account | No | Yes |
| Validation of electronic fiscal document access key in SEFAZ | No | Yes |
| Archiving of electronic fiscal document XML together with the posted received fiscal document | No | Yes |
| Matching the quantity and price unit from the received electronic fiscal document XML with the vendor invoice from the purchase order | No | Yes |

### Purchase return

| Item | AX 2012 R3 |  Finance | 
| ---- | ---------- | -------- |
| Issuing fiscal document for vendor returns | Yes | Yes |


### Sell

| Item | AX 2012 R3 |  Finance | 
| ---- | ---------- | -------- |
| Sales quotations, sales orders, free text invoices, and project invoices localized to support Brazilian taxes per the Brazilian localization scope | Yes | Yes |
| Input of transport information for fiscal documents | Yes | Yes |
| Fiscal document texts in sales orders and free text invoices | Yes | Yes |
| Cancel issued fiscal documents | Yes | Yes |

### Invoicing

| Item | AX 2012 R3 |  Finance | 
| ---- | ---------- | -------- |
| Issuing fiscal documents for invoicing:<br>- Inventory items<br>- Services<br>- Fixed assets<br>- Third-party sales<br>- Project invoices <br>- For end users<br>- For customers in SUFRAMA<br>- (IPI, ICMS) Tax and price complementary fiscal documents | Yes | Yes |
| Referenced fiscal documents | Yes | Yes |
| Fiscal document with referenced processes | Yes | Yes |
| Multiple processes referenced by fiscal document texts | Yes | Yes |
| Withholding tax for IRRF, INSS, and ISS | Yes | Yes |
| Outbound fiscal document viewer | Yes | Yes |
| Display approximated taxes | Yes | Yes |
| Manual maintenance of Ficha Conteúdo de Importação (FCI) by product, fiscal establishment, and period | Yes | Yes |
| The localization supports issuing fiscal document models 1, 1-A, and 55, and the Services fiscal document for São Paulo city. Partners must customize the requirements or behavior for unsupported fiscal document models. **Note**: The localization doesn't support generation of FCI files, subsequent operation, automatic sending of FCI files, and automatic calculation of importation composition. | Yes | Yes |

### Sales return

| Item | AX 2012 R3 |  Finance | 
| ---- | ---------- | -------- |
| Customer returns with your organization's fiscal document | Yes | Yes |
|	Customer returns with a fiscal document issued by the customer | Yes | Yes |
| Electronic fiscal document access key | Yes | Yes |

### Inventory

| Item | AX 2012 R3 |  Finance | 
| ---- | ---------- | -------- |
| Issue and receive fiscal documents for transfers/returns of inventory items between fiscal establishments | Yes | Yes |
| Issue and receive fiscal documents for remittance/returns of inventory items from a third party | Yes | Yes |

### Production

| Item | AX 2012 R3 |  Finance | 
| ---- | ---------- | -------- |
| Indirect and direct cost absorption only over production orders from discrete manufacturing | Yes | Yes |

### NF-e (Federal)

| Item | AX 2012 R3 |  Finance | 
| ---- | ---------- | -------- |
| Support for NF-e layout 4.0 | Yes | Yes |
| NF-e messages/events:<br>- Issue<br>- Cancel<br>- Discard<br>- Electronic correction letter (CC-e) | Yes | Yes |
| Contingency mode: security form (FS or FS-DA) | Yes | Yes |
| Contingency mode: SCAN | Yes | No |
| Contingency mode: SVC | Yes | Yes |
| XML viewer for issued and received electronic fiscal documents | Yes | Yes |
| Automatic sending of electronic fiscal document through email for customers, vendors, and transportation companies | Yes | Yes |
| **Out of scope**: Overall purpose services in the NF-e | Yes | Yes |

### NFS-e Services (São Paulo city) 

| Item | AX 2012 R3 |  Finance | 
| ---- | ---------- | -------- |
| Service electronic fiscal document using .txt files | Yes | Yes | 
| Recibo Provisório de Serviços (RPS) for São Paulo city | Yes | Yes |

### Financial and treasury

| Item | AX 2012 R3 |  Finance | 
| ---- | ---------- | -------- |
| Withholding IRRF, PIS, COFINS, CSLL, ISS, and INSS taxes on payments and receiving | Yes | Yes |
| Withholding IRRF, PIS, and COFINS tax threshold by legal entity | Yes | Yes |
| Payment with check per bank | Yes | Yes |
| Payment with Brazilian Borderô | Yes | Yes |
| Interest and fines on payments and receiving, applying federal, state, and city holiday calendars | Yes | Yes |
| Interest, fines, and withholding tax on centralized payments | Yes | Yes |
| Electronic payment based on configurable files for the FCC-400 layout | Yes | Yes |
| Electronic receiving based on configurable files for the CNAB-240 layout | Yes | Yes |

### General ledger

| Item | AX 2012 R3 |  Finance | 
| ---- | ---------- | -------- |
| Accounting consolidation with transaction detailed transfers | Yes | Yes |
| Fiscal document for ICMS tax credit transfer between fiscal establishments | Yes | Yes |
| Fiscal document for 1/48 ICMS tax credits | Yes | Yes |
| Legal reports:<br>- Day book<br>- Analytical ledger<br>- Trial balance | Yes | No |

### Commerce

| Item | AX 2012 R3 EPOS |  D365 CPOS / MPOS | 
| ---- | :---------------: | :-----------------: |
| Customer CPF/CNPJ on fiscal receipts | Yes | Yes |
| File generation for Nota Fiscal Paulista | Yes | No |
| Tax calculation according to Commerce headquarters configuration | Yes | Yes |
| Fiscal printer integration for Daruma printers, models FS600, FS700 (H, L and M), FS800i, Mach 1, Mach 2, and Mach 3 | Yes | No |
| Fiscal printer integration for Bematech printers, models MP2100 FI TH FI and MP4200 TH FI II | Yes | No |
| POS legal requirements according to PAF-ECF law "ATO COTEPE/ICMS N°9" of 2013, except for any businesses identified as out of scope in the [Out of scope](#out-of-scope) section of this article | Yes | No |
| POS legal requirements according to PAF-ECF law "ATO COTEPE/ICMS N°46" of 2014, except for any businesses identified as out of scope in the [Out of scope](#out-of-scope) section | Yes | No |
| Display approximated taxes in fiscal receipts | Yes | No |
| Display approximated taxes in DANFE / CF-e-SAT | Yes | Yes |
| Void last fiscal receipt | Yes | No |
| Payments with multiple credit cards | Yes | Yes |
| EFT integration with third-party software D-TEF Dedicado, version 8.1.37.2, commercialized by Direção Processamento de Dados Ltda | Yes | No |
| EFT integration with third-party software SiTef, version 4.0.111.6, commercialized by Software Express Informática Ltda <br>Presales according to PAF-ECF law "ATO COTEPE/ICMS N°46" of 2014 | Yes | No |
| EFT integration with third-party software Adyen, basic capabilities | No | Yes |
| Issuing return NF-e in POS for sales return | Yes | Yes |
| Issuing NF-e linked to fiscal receipt in POS | Yes | No |
| Configurable AOS for NF-e/NFC-e messaging with SEFAZ | Yes | No |
| The EFT service must be contracted directly from the third-party provider and isn't included in any Microsoft software license.<br><br>**Note**: Because of conflicts with the PAF-ECF legislation, not all Enterprise POS operations are permitted in Brazil. For more details, see the [Retail and Enterprise POS Localization for Brazil white paper](https://www.microsoft.com/download/details.aspx?id=42938). | Yes | Yes |           
| Support for layout NFC-e (Nota Fiscal ao Consumidor Eletrônica) 4.0 | Yes | Yes |
| Contingency mode: off-line | Yes | Yes |
| Contingency mode for SP: SAT (model 59) | Yes | Yes |
| Sales presence type: in-person | Yes | Yes |
| Commerce item management:<br>- Released products by category<br>- Mass update worksheet<br>- Product hierarchy | Yes | Yes |
| SAT (model 59) for São Paulo state layout 0.07 | Yes | Yes |
| Support for only one SAT hardware per POS | Yes | Yes |
| Support for SAT DLL selection, for multiple-brand compatibility | Yes | Yes |
| Fiscal receipt reference | Yes | No |
| Fiscal printer auto-configuration | Yes | No |

### Project accounting 

| Item | AX 2012 R3 |  Finance | 
| ---- | ---------- | -------- |
| Credit notes | Yes | Yes |

### TMS

| Item | AX 2012 R3 |  Finance | 
| ---- | ---------- | -------- |
| Issue outbound fiscal documents and electronic fiscal documents from loads for sales order invoices | YEs | Yes |
| Issue outbound fiscal documents and electronic fiscal documents from loads from transfer orders and fiscal document slips | Yes | Yes |

### Call center

| Item | AX 2012 R3 |  Finance | 
| ---- | ---------- | -------- |
| Support for Brazilian tax registration ID (CNPJ/CPF) in customer data management | Yes | Yes |

### Fiscal books

| Item | AX 2012 R3 |  Finance | 
| ---- | ---------- | -------- |
| Fiscal books reports:<br>- IP tax assessment<br>- ICMS tax assessment<br>- ICMS-ST tax assessment for states with IE registration<br>- Incoming and Incoming model 1A<br>- Outgoing and Outgoing Model 2A<br>- Inventory models 3 and 7<br>- CIAP control report<br>- ISS Report model 51 (delivering services)<br>- ISS Report model 56 (acquiring services)<br>- ECF daily operations report (Mapa Resumo) | Yes | Yes |
| Tax assessments | Yes | Yes |
| Generate the tax assessment and payment of the following taxes:<br>- IPI<br>- ICMS and ICMS-ST<br>- ICMS DIFAL<br>- ISS | Yes | Yes | 
| Generate the tax assessment and payment of the following taxes:<br>- INSS CPRB | Yes | Yes |
| Generate the tax assessment and payment of the following taxes:<br>- PIS and COFINS regime Cumulative<br>- PIS and COFINS regime Npn-Cumulative<br>- Both | Yes | Yes |
| CIAP control and manual registration of ICMS installments | Yes | Yes |

### SPED Fiscal (ICMS, IPI)

| Item | AX 2012 R3 |  Finance | 
| ---- | ---------- | -------- |
| Generate a text file and support for companies defined as Profile A <br> Available layout versions include Layout Code 15 and earlier | Yes | Yes |
| Support for the following records for companies defined as Profile A:<br>- Block 0: 0000-0001-0002-0005-0015-0100-0150-0190-0200-0210-0220-0300-0305-0400-0450-0460-0500-0600-0990 <br>- Block C: C001-C100-C101-C110-C111-C113-C114-C120-C130-C140-C141-C160-C170-C172-C180-C185-C190-C191-C195-C400-C405-C410-C420-C460-C470-C490-C500(incoming)-C590 (incoming)-C990 <br>- Block D (only for incoming fiscal documents): D001-D100-D190-D195-D500-D590-D990 <br>- Block E: E001-E100-E110-E111-E116-E200-E210-E220-E250-E300-E310-E311-E312-E313-E316-E500-E510-E520-E530-E990 <br>- Block G: G001-G110-G125-G126-G130-G140-G990 <br>- Block H: H001-H005-H010-H020-H030-H990. Note: H005 and related records are only supported for reason code = 01, 05 for RS state and 06. <br>- Block K: K001-K100-K200-K220-K230-K235-K260-K265-K270-K275-K280-K290-K291-K292-K990 <br>- Block 1: 1001-1010-1250-12251990 <br>- Block 1900-1910-1920-1921-1923-1926-1990 only for Rio Grande do Sul state | Yes | Yes |
| Resolution 13/2019 and Portaria SUCIEF 55/2019- RJ | Yes | Yes |
| **Out of scope**: SPED Fiscal with specific requirements from the state/region, as described in the [Brazilian localization strategy](#brazilian-localization-strategy) section of this article, and companies that are categorized as Profile B and Profile C. | Yes | Yes |

### Portaria CAT 42/2018 - SP

| Item | AX 2012 R3 |  Finance | 
| ---- | ---------- | -------- |
| Layout 1.1 B | Yes | Yes |

### DRCST for Santa Catarina state

| Item | AX 2012 R3 |  Finance | 
| ---- | ---------- | -------- |
| - SEF Portaria No. 396/2018<br>- SEF Portaria No. 208/2019<br>- SEF Portaria No.254/2019 <br>- SEF Portaria No.343/2019 <br>- SEF Portaria No.416/2019 | Yes | Yes |
| Records:<br>- Block 0: 0000-0001-0005-0100-0190-0200-0220<br>- Block 2: 2100-2110-2113-2114-2115-2120-2121-2130-2131-2132-2133-2134 <br>- Block H: H001-H005-H010-H990<br>- Block 9: 9001-9900-9990-9999 | Yes | Yes |  

### SPED Contributions (PIS and COFINS)

| Item | AX 2012 R3 |  Finance | 
| ---- | ---------- | -------- |
| Generate a text file in accordance with layout 006 and earlier | Yes | Yes |
| Support for company type Sociedade empresaria em geral | Yes | Yes |
| Support for booking criteria Regime de Competência – Escrituracao detalhada only | Yes | Yes |
| Support for the following records: <br>- Block 0: 0000-0001-0100-0110-0111-0140-0150-0190-0200-0400-0450-0900-0990<br>- Block A: A001-A010-A100-A110-A111-A120-A170-A990<br>- Block C: C001-C010-C100-C110-C111-C120-C170-C175-C180-C181-C185-C188-C190-C191-C195-C198-C199-C380-C381-C385-C400-C405-C481-C485-C490-C491-C495-C500-C501-C505-C509<br>- Block D (only for incoming fiscal documents): D001-D010-D100-D101-D105-D111-D500-D501-D505-D509<br>- Block F: F010-F100-F111-F120-F129-F130-F600-F700-F800-F990<br>- Block M: M001-M100-M105-M110-M115-M200-M205-M210-M220-M225-M400-M410-M500-M505-M510-M515-M600-M606-M610-M620-M625-M800-M810-M990<br>- Block 1: 1100-1300-1500-1700 | Yes | Yes |  

### SPED ECF

| Item | AX 2012 R3 |  Finance | 
| ---- | ---------- | -------- |
| Generating a text file by using Management Reporter<br><br>Layouts 007 and previous<br><br>Support for the following blocks and records:<br>- Block 0: 0000-0001-0010-0020-0030-0035-0930-0990<br>- Block J: J001-J050-J051-J100<br>- Block K: K001-K030-K155-K156-K355-K356-K990<br>- Block V (DEREX): V001-V010-V020-V030-V100-V990 | Yes | Yes|

### SPED Reinf

| Item | AX 2012 R3 |  Finance | 
| ---- | ---------- | -------- |
| Generating events: <br>- R-1000, R-1070, R-2010, R-2020, R-2055, R-2060, R-2098, R-2099, R-5011<br>- Layout version 1.5.1 | Yes | Yes | 

### SINTEGRA

| Item | AX 2012 R3 |  Finance | 
| ---- | ---------- | -------- |
| Generating text files in accordance with [version 3 - ICMS-76/03](http://www.sintegra.gov.br). | Yes | No |

### GIA-SP

| Item | AX 2012 R3 |  Finance | 
| ---- | ---------- | -------- |
| Generating GIA São Paulo state text files in accordance with [version 08.00 (01/02/2013)](http://www.fazenda.sp.gov.br/download/download_gia.shtm). | Yes | Yes |


### GIA-ST Nacional

| Item | AX 2012 R3 |  Finance | 
| ---- | ---------- | -------- |
| Generating GIA-ST text files in accordance with [version 3.1](http://www.fazenda.sp.gov.br/download/downloadgiast.shtm). | Yes | Yes |


### SPED Accounting

| Item | AX 2012 R3 |  Finance | 
| ---- | ---------- | -------- |
| Generation of SPED Contábil text files <br>Layout version supported: 9.0 and earlier | Yes | Yes | 
| Support for bookkeeping type G (Day Book - Livro Diario) and the generation of the following blocks and records:<br>- Block 0: 0000-0001-0007-0035-0990<br>- Block I: I001-I010-I030-I050-I051-I052-I100-I150-I155-I200-I250-I350-I355-I990<br>- Block J: J001-J005-J100-J150-J800-J801-J900-J930-J932-J935-J999<br>- Block 9: 9001-9900-9990-9999<br>- All available posting layers are included in the generation of SPED ECD file. | Yes | Yes |




## <a name="out-of-scope"></a>Out of scope

Some capabilities of Microsoft Dynamics that are generally available in other countries or regions might not be available in the Brazilian localization. The following items are out of scope or are otherwise not permitted for Brazil.

### Tax calculation requirements

The following tax calculation requirements are out of scope for the Brazilian localization:

- *Simples Nacional* or *Super Simples* taxation mode
- *Regime especial* taxation mode (see the [Notes](#notes) section of this article)
- Requirements from states/regions other than the states/regions that are described in the [Brazilian localization strategy](#brazilian-localization-strategy) section of this article
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
- SPED Fiscal that has specific requirements from the states/regions that are described in the [Brazilian localization strategy](#brazilian-localization-strategy) section of this article
- *Simples Nacional* or *Super Simples* taxation mode
- *Regime especial* taxation mode (see the [Notes](#notes) section of this article)
- Requirements from states/regions other than the states/regions that are described in the [Brazilian localization strategy](#brazilian-localization-strategy) section
- Requirements from regulatory agencies or autarchies, such as SUFRAMA, ANVISA, and ANATEL
- IN86
- GIA for states other than São Paulo
- Data upgrade for fiscal books from AX 2009 to AX 2012 R3 and finance and operations
- Data upgrade of fiscal documents from AX 2009 to AX 2012 R3 and finance and operations

## References

The [Microsoft Dynamics Localization Portal](/dynamics/s-e/) provides information about localization features and documents that have been released by Microsoft, and also localization features and documents that are planned for release.

## <a name="notes"></a>Notes

**Regime especial (special regime)** – Any differential treatment, with respect to general tax rule requirements (whether federal, state, or municipal) and ancillary obligations, that the tax authority authorizes, in peculiar cases, to simplify tax compliance by the taxpayer. This differential treatment doesn't include relief from taxation.

## Brazilian tax terms and abbreviations

| Term or abbreviation | Description |
|----------------------|-------------|
| ANATEL               | Telecommunication regulatory agency |
| ANVISA               | Health and medical regulatory agency |
| CNPJ                 | Federal tax registration number for companies |
| CIAP                 | Control over installments of ICMS tax credit for acquired fixed assets |
| COFINS               | Contribution based on gross revenues from business sales |
| CFOP                 | Fiscal code operation |
| CSLL                 | Social contribution tax on net profit |
| DARF                 | Payment voucher that must be fulfilled for federal tax payment |
| DCTF                 | Debit and credit assessment for federal taxes |
| DIRF                 | Assessment of federal withholding taxes |
| GNRE                 | Payment voucher that must be fulfilled for state tax payment |
| GIA                  | ICMS tax assessment and payment declaration |
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
| Nota fiscal          | Fiscal document |
| PIS                  | Contribution for the social integration program |
| SPED                 | Public digital bookkeeping system |
| SINTEGRA             | Information system for interstate goods and service transactions |
| SEFAZ                | State tax authority |
| SUFRAMA              | Autarchy for economic development of the Amazon region |


[!INCLUDE[footer-include](../../includes/footer-banner.md)]

