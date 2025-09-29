---
title: VAT declaration for Indonesia
description: Learn how to configure and generate the SPT Masa PPN 1111 (Pajak Pertambahan Nilai) form for Indonesia, including prerequisites.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/27/2024
ms.reviewer: johnmichalak
ms.search.region: Indonesia
ms.search.validFrom: 2021-09-01
ms.dyn365.ops.version: 10.0.20
---

# VAT declaration for Indonesia 

This article explains how to set up and generate the value-added tax (VAT) return form for legal entities in Indonesia. 
This form is referred as *SPT Masa PPN (Surat Pemberitahuan Masa Pajak Pertambahan Nilai)*. 
Corporate taxpayers should issue it to report the calculated amount of tax so that they can report VAT (PPN) and Luxury Goods Sales Tax (PPNnBM) that are owed. 

Microsoft Dynamics 365 Finance support generation of the **SPT Masa PPN (Pajak Pertambahan Nilai)** in Exel format that includes the following pages:

- **11. Other Output Tax Documents** – reports VAT collected using documents other than standard tax invoices (e.g., customs or specific government documents).
- **12. Other Input Tax Documents** – records VAT paid that is creditable based on documents other than standard tax invoices.
- **13. Return of Other Output Tax Documents** – declares corrections or returns of previously reported other output VAT documents.
- **14. Return of Other Input Tax Documents** – declares corrections or returns of previously reported other input VAT documents.
- **15. Output Tax Invoice** – lists VAT collected through standard e-Faktur (tax invoices) issued to buyers.
- **16. Return of Input Tax Invoice** – records VAT invoice returns/cancellations that reduce previously credited input tax.

## Prerequisites

The primary address of the legal entity must be in Indonesia.

In the **Feature management** workspace, enable the **Enable credit invoicing for vendor invoices** feature. For more information about how to enable features, see [Feature management overview](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Upload Electronic reporting configurations

Implementation of the VAT return form for Indonesia is based on Electronic reporting (ER) configurations. For more information about the capabilities and concepts of configurable reporting, see [Electronic reporting](../../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md).

In the **Electronic reporting** workspace, import the latest version **VAT Declaration Excel (ID)** ER format from the repository. This format is based on the **Tax declaration model** configuration and uses the **Tax declaration model mapping** configuration. Model and model mapping configurations will be automatically imported. Learn more about how to import ER configurations in [Import Electronic reporting (ER) configurations from Dataverse](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/global/workspace/gsw-import-er-config-dataverse).

## Set up application-specific parameters

Application-specific parameters of the **SPT Masa PPN** format in ER facilitate the mapping of your tax data to the required values that are defined by the report structure.
The application-specific parameters let you establish the criteria that define how the tax transactions are collected and calculated in **SPT Masa PPN** report when it is generated, based on the configuration of the sales tax code. Here are some of the available criteria:

- Sales tax group
- Item sales tax group
- Sales tax code
- Transaction classifier
- Exempt reason

There must be enough transactional data to define values in **SPT Masa PPN** report. Therefore, set up enough sales tax codes, sales tax groups, and item sales tax groups to differentiate tax transactions for the structure of in **SPT Masa PPN**.

To prepare Finance to generate a **SPT Masa PPN** report in compliance with the required schema, follow these steps.

1. In Dynamics 365 Finance, go to the **Electronic reporting** workspace.
2. In the configuration tree, select **Tax declaration model** \> **VAT Declaration Excel (ID)**.
3. On the Action Pane, on the **Configurations** tab, in the **Applications specific parameters** group, select **Setup**.
4. On the left side of **Application specific parameters** page, select the latest version of the format.
5. On the **Lookups** FastTab, select a lookup field in the list. Detailed descriptions of all the lookup fields of the **SPT Masa PPN** format are provided after this procedure.
6. On the **Conditions** FastTab, define the required conditions, and specify the values in the **Lookup result** column.
7. As the last two lines, add lines that have the conditions **Not blank** and **Blank** where applicable.
8. Repeat steps 5 through 7 for each additional lookup field.
9. When all the lookup fields are set up, select **Completed** in the **State** field, and save the configuration.

### TaxTypeLookup

| Lookup result | Label En            |
|---------------|---------------------|
| PPM           | Value Added Tax     |
| PPnBM         | Luxury sales tax    |
| N/A           | Not applicable      |

The following criteria are required to define the **TaxTypeLookup**:

- Tax code

### ReportFieldLookup

This lookup field is used to define the page of **SPT Masa PPN** report where the document to be reported.

| Lookup result                          | Label En                                                                 |
|----------------------------------------|--------------------------------------------------------------------------|
| 11-Other Output Tax Documents          | Output VAT that is not documented through standard tax invoices (Faktur Pajak) |
| 12-Other Input Tax Documents           | Input creditable VAT that is not covered by standard tax invoices (Faktur Pajak) |
| 13-Return of Other Output Tax Documents| Corrections or returns related to previously reported non-standard output tax documents |
| 14-Return of Other Input Tax Documents | Adjustments or reversals of input VAT that was previously claimed using non-standard input tax documents |
| 15-Output Tax Invoice                  | Sales or service transactions where the taxpayer has issued a valid Faktur Pajak |
| 16-Return of Input Tax Invoice         | Reversals or corrections of previously claimed input VAT that was supported by standard Faktur Pajak (Tax Invoices) |
| Other                                  | Documents not included in any reporting category                          |

The documents (transactions) that are classified as **"Other"** are excluded from  **SPT Masa PPN** report. The line containing **Other** lookup result must be added as the last line for the ReportFieldLookup and mapped to **"Not blank"**.  

The following criteria are required to define the **TaxTypeLookup**:

- Sales tax group  
- Item sales tax group  
- Sales tax code  
- Transaction classifier  

### TransactionTypeLookup

**TransactionTypeLookup** is used to classify and define the type of transaction being reported in the pages 11–14 of **SPT Masa PPN** report, ensuring that output and input VAT not covered by standard invoices are properly categorized according to whether they relate to domestic sales, exports, imports, purchases, exemptions, or other non-standard transactions.

| Lookup result | Label En                                              | Description EN                                                             |
|---------------|-------------------------------------------------------|----------------------------------------------------------------------------|
| 01-DELIVERY   | Sales transactions subject to standard VAT rate       | Standard sales transactions subject to VAT                                 |
| 02-EXPORT     | Export sales of goods or services from Indonesia subject to 0% VAT | Sales of goods or services exported out of Indonesia, typically subject to a 0% VAT rate |
| 03-IMPORT     | Imports of goods or services into Indonesia subject to VAT | Purchases of goods or services imported into Indonesia, subject to VAT      |
| 04-PURCHASE   | Purchases of goods or services within Indonesia subject to VAT | Purchases of goods or services within Indonesia, subject to VAT            |
| 05-UNCREDIT   | Sales of goods or services that are exempt from VAT, not subject to VAT | Sales of goods or services that are exempt from VAT                         |
| Other         | Other transactions no type                            | For these transactions the type filed will be empty                         |

The following criteria are required to define the **TransactionTypeLookup**:

- Sales tax code  
- Transaction classifier  
- Sales tax group  
- Item sales tax group  

### TransactionDetailLookup

**TransactionDetailLookup** is used to specify the detailed nature of transactions reported in the pages 11–14 of **SPT Masa PPN** report, distinguishing between types of taxable supplies, exemptions, exports, imports, special tax bases, and other specific cases required by Indonesian VAT regulations.

| Lookup result | Label En                                               | Description EN |
|---------------|--------------------------------------------------------|----------------|
| 01-To other party than VAT Collector | Sales of taxable goods/services where the VAT is collected by the seller (PKP) and does not fall under transaction codes 02 to 09. | This transaction code is used for the submission of BKP and/or JKP whose VAT or VAT and PPnBM are collected by the PKP that submits the BKP and/or JKP. This transaction code is used in the event that it is not a type of submission as referred to in transaction codes 02 to transaction codes 09. |
| 02-To Government Institution as VAT Collector | Sales of taxable goods/services to government agency VAT collectors, where VAT or VAT and luxury tax (PPnBM) are withheld and paid by the government agency as the buyer | This transaction code is used to submit BKP and/or JKP to VAT collectors of government agencies whose VAT or VAT and PPnBM are collected by VAT collectors of government agencies. |
| 03-To VAT Collector other than Government Institution | Sales of taxable goods/services to non-government VAT collectors | This transaction code is used to submit BKP and/or JKP to other VAT collectors (other than government agencies) whose VAT or VAT and PPnBM are collected by other VAT collectors (other than government agencies). |
| 04-Other Tax Base | Different tax base is applied | Taxable goods and services whose tax basis uses other values as stipulated in Article 8A paragraph (1) of the VAT Law where VAT or VAT and PPnBM are collected by the PKP that submits BKP and/or JKP. |
| 05-Certain value Tax Base | VAT is calculated using a specific percentage of the selling price | This transaction code is used for the submission of BKP and/or JKP whose VAT is collected with a certain amount as stipulated in Article 9A paragraph (1) of the VAT Law whose VAT is collected by the PKP who submits the BKP and/or JKP. |
| 06-To Tourist for VAT Refund for Tourist | Sales to tourists eligible for VAT refunds under the VAT refund. | Sales to tourists eligible for VAT refunds. |
| 07-VAT Uncollected | VAT is not collected due to specific exemptions or special treatments | VAT is not collected due to specific exemptions or special treatments when certain transactions are legally excluded from VAT collection, even though they involve taxable goods or services. |
| 08-VAT Exempted | Transactions that are exempt from VAT under the law | This transaction code is used for submissions that receive facilities exempt from the imposition of VAT or VAT and PPnBM based on applicable special regulations. |
| 09-Sale of unrelated to business asset | Sales of assets not used directly in the company's core business activities. | Sales of assets that are not part of the company's core business activities. |
| 10-Other delivery of goods/services | Transactions that don't fall under standard VAT categories. | Miscellaneous taxable deliveries not covered by codes 01–09 |
| 11-01-Exports of Tangible Goods | Export of physical goods | Sale and shipment of physical goods from Indonesia to overseas buyers |
| 12-02-Exports of Intangible Goods | Exports of intangible goods | Export of intangible goods, such as: software licenses, intellectual property rights, etc. |
| 13-03-Exports of Services | Exports of services | Export of services, such as: consulting, engineering, design services, etc. |
| 14-01-Import Taxable Goods | Import taxable goods | Imported goods subject to VAT |
| 15-02-Utilization of Intangible Taxable Goods and Services | Utilization of intangible taxable goods and taxable services | Intangible goods or services from abroad are utilized in Indonesia |
| Other | Other transactions no details | For these transactions the Detail filed will be empty |

The following criteria are required to define the **TransactionDetailLookup**:

- Sales tax code  
- Transaction classifier  
- Sales tax group  
- Item sales tax group 

### TransactionDocLookup

**TransactionDocLookup** is used when a transaction lacks a standard tax invoice but is still recognized for VAT purposes. This category includes receipts, simplified invoices, or other documents that clearly state VAT has been collected and paid, such as commercial invoices, billing documents, or order receipts. These documents serve as proof of VAT collection and are acceptable for VAT reporting and compliance

| Lookup result | Label En                                | Description EN |
|---------------|-----------------------------------------|----------------|
| 01-Documents Equivalent to Tax Invoice | Documents Equivalent to Tax Invoice | Used when a transaction is not accompanied by a standard tax invoice but is still recognized for VAT purposes. For example, receipts or simplified invoices issued by small retailers or under special schemes. |
| 02-Cigarette Excise | Cigarette Excise | Refers to excise documents related to cigarette production and distribution. These documents are used to report VAT on excisable goods like tobacco, where VAT is embedded in the excise mechanism. |
| 03-Bonded Area Document | Bonded Area Document | Used for transactions involving bonded zones (Kawasan Berikat), where goods are imported or moved under customs suspension. These documents support VAT exemption or deferral. |
| 04-Export Notice of Goods | Export Notice of Goods | Customs export declaration (PEB) for tangible goods. This document is used to support zero-rated VAT treatment for exports. |
| 05-Export Notice of Services/Intangible Goods | Export Notice of Services/Intangible Goods | Declaration for the export of services or intangible goods (e.g., software, IP rights). Supports zero-rated VAT treatment. |
| 06-Import Notice and Payment | Import Notice and Payment | Customs import declaration (PIB) and proof of VAT payment at import. Used to claim input VAT on imported goods. |
| 07-Payment | Payment | Refers to direct VAT payments made to the tax authority, often in cases of self-assessment or corrections. |
| 08-Special documents | Special Documents | Covers special cases such as government grants, donations, or barter transactions. These documents are recognized for VAT purposes under specific rules. |
| 09-Notice of Tax Underpayment Assessment | Notice of Tax Underpayment Assessment | Notice of tax underpayment assessment or notice of additional tax underpayment assessment. |
| 10-Import Notice | Import Notice | Refers to specific import declarations under different schemes (e.g., temporary imports, bonded logistics). |
| Other | Other transaction document types | For these transactions the transaction document filed will be empty. |

The following criteria are required to define the TransactionDocLookup:

- Sales tax code  
- Transaction classifier  
- Sales tax group  
- Item sales tax group

### AdditionalInformationLookup

**AdditionalInformationLookup** represents supplemental details required for a transaction’s VAT reporting. It helps classify transactions according to applicable government regulations (PPs) or Ministry of Finance decrees (PMKs) and ensures accurate reporting and compliance in VAT declarations. Each entry corresponds to a specific combination of sales tax code, transaction classifier, exempt reason, sales tax group, and item sales tax group.

| Lookup result | Label En | Description EN |
|---------------|----------|----------------|
| 07-1-VAT not collected - PP 10/2012 | VAT not collected based on PP number 10 of 2012 | VAT not collected based on Government Regulation (PP) Number 10 of 2012 |
| 07-2-VAT or Luxury Tax not collected | VAT or VAT and Sales Tax on Luxury Goods are not collected | VAT or VAT and Luxury Goods Sales Tax are not collected |
| 07-3-VAT and Luxury Tax not collected | VAT and Sales Tax on Luxury Goods are not collected | VAT and Sales Tax on Luxury Goods are not collected |
| 07-4-VAT not collected - PP 71/2012 | VAT not collected according to PP number 71 of 2012 | VAT not collected based on PP Number 71 of 2012 |
| 07-5-No stamp | No Stamp | No regulatory stamp or annotation |
| 07-6-VAT not collected - PMK 194/2012 | VAT and/or PPnBM are not collected based on PMK No. 194/PMK.03/2012 | VAT and/or PPnBM not collected per Finance Ministry Decree No. 194/PMK.03/2012 |
| 07-7-VAT not collected - PP 15/2015 | VAT not collected based on PP number 15 of 2015 | VAT not collected based on PP Number 15 of 2015 |
| 07-8-VAT not collected - PP 69/2015 | VAT not collected based on PP number 69 of 2015 | VAT not collected based on PP Number 69 of 2015 |
| 07-9-VAT not collected - PP 96/2015 | VAT not collected based on PP number 96 of 2015 | VAT not collected based on PP Number 96 of 2015 |
| 07-10-VAT not collected - PP 106/2015 | VAT not collected based on PP number 106 of 2015 | VAT not collected based on PP Number 106 of 2015 |
| 07-11-VAT not collected - PP 50/2019 | VAT not collected based on PP number 50 of 2019 | VAT not collected based on PP Number 50 of 2019 |
| 07-12-VAT/Luxury Tax not collected - PP 27/2017 | VAT or VAT and PPnBM not collected according to PP number 27 of 2017 | VAT or VAT and PPnBM not collected under PP Number 27 of 2017 |
| 07-13-VAT borne by Gov - PMK 21/2021 | VAT borne by the government EX PMK 21/PMK.010/21 | VAT covered by the government per PMK 21/PMK.010/2021 |
| 07-14-VAT borne by Gov - PMK 102/2021 | VAT borne by the government EX PMK 102/PMK.010/2021 | VAT covered by the government per PMK 102/PMK.010/2021 |
| 07-15-VAT borne by Gov - PMK 239/2020 | VAT borne by the government EX PMK 239/PMK.03/2020 | VAT covered by the government per PMK 239/PMK.03/2020 |
| 07-16-VAT incentive - PMK 103/2021 | VAT Incentives borne by the government executing PMK number 103/PMK.010/2021 | Government VAT incentive execution based on PMK 103/PMK.010/2021 |
| 07-17-VAT not collected - PP 40/2021 | VAT is not collected based on PP number 40 OF 2021 | VAT not collected under PP Number 40 of 2021 |
| 07-18-VAT not collected - PP 41/2021 | VAT is not collected based on PP number 41 OF 2021 | VAT not collected under PP Number 41 of 2021 |
| 07-19-VAT borne by Gov - PMK 6/2022 | VAT borne by the government EX PMK 6/PMK.010/2022 | VAT covered by government under PMK 6/PMK.010/2022 |
| 07-20-VAT borne by Gov - PMK 226/2021 | VAT borne by the government EX PMK NUMBER 226/PMK.03/2021 | VAT covered by government under PMK 226/PMK.03/2021 |
| 07-21-VAT/PPnBM not collected - PP 53/2017 | VAT or VAT and PPnBM are not collected in accordance with PP number 53 of 2017 | VAT or VAT and PPnBM not collected in accordance with PP 53/2017 |
| 07-22-VAT not collected - PP 70/2021 | VAT is not collected based on Government Regulation Number 70 of 2021 | VAT not collected based on PP 70 of 2021 |
| 07-23-VAT borne by Gov - PMK 125/2020 | VAT is borne by the Government Ex PMK-125/PMK.01/2020 | VAT covered by the government per PMK-125/PMK.01/2020 |
| 07-24-No stamp | No stamp | No regulatory stamp or annotation |
| 07-25-VAT not collected - PP 49/2022 | VAT is not collected based on Government Regulation Number 49 of 2022 | VAT not collected based on PP Number 49 of 2022 |
| 07-26-VAT not collected - PP 12/2023 | VAT is not collected based on Government Regulation Number 12 of 2023 | VAT not collected based on PP Number 12 of 2023 |
| 07-27-VAT borne by Gov - PMK 38/2023 | VAT is borne by the Government based on PMK Number 38 of 2023 | VAT covered by government based on PMK Number 38 of 2023 |
| 08-1-VAT exempted - PP 146/2000 & 38/2003 | VAT is exempted according to government regulation number 146 of 2000 As Amended by Government Regulation Number 38 of 2003 | VAT exemption under PP 146/2000 as amended by PP 38/2003 |
| 08-2-VAT exempted - PP 12/2001 to PP 31/2007 | VAT is exempted according to government regulation number 12 of 2001 as amended several times last by government regulation number 31 of 2007 | VAT exemption under PP 12/2001, latest amendment PP 31/2007 |
| 08-3-VAT exempted - PP 28/2009 | VAT is exempted according to government regulation number 28 of 2009 | VAT exemption under PP 28 of 2009 |
| 08-4-No stamp | No stamp | No regulatory stamp or annotation |
| 08-5-VAT exempted - PP 81/2015 | VAT is exempted according to government regulation number 81 of 2015 | VAT exemption under PP 81 of 2015 |
| 08-6-VAT exempted - PP 74/2015 | VAT exempted based on PP Number 74 of 2015 | VAT exemption under PP 74 of 2015 |
| 08-7-No stamp | Without stamp | No regulatory stamp or annotation |
| 08-8-VAT exempted - PP 81/2015 amended by PP 48/2020 | VAT is exempted according to PP number 81 of 2015 as amended by PP 48 of 2020 | VAT exemption under PP 81/2015, amended by PP 48/2020 |
| 08-9-VAT exempted - PP 47/2020 | VAT exempted based on PP number 47 OF 2020 | VAT exemption under PP 47 of 2020 |
| 08-10-VAT exempted - PP 49/2022 | VAT exempted based on PP number 49 of 2022 | VAT exemption under PP 49 of 2022 |
| Other | Other transactions no additional information | For these transactions the additional information filed will be empty |

The following criteria are required to define the **AdditionalInformationLookup**:

- Sales tax code
- Transaction classifier
- Exempt reason
- Sales tax group
- Item sales tax group

### FacilityStampLookup

**FacilityStampLookup** represents the specific VAT-related facility or treatment applied to a transaction under Indonesian tax regulations. Each entry reflects a particular regulatory scenario, such as Free Zones, Bonded Warehouses, government-funded programs, strategic goods, or pandemic-related relief, and helps ensure accurate VAT reporting and compliance. The lookup is defined based on sales tax code, transaction classifier, exempt reason, sales tax group, and item sales tax group.

| Lookup result | Label EN | Description EN |
|---------------|----------|----------------|
| Tidak Ada | None | No VAT facility applies; standard VAT rules and collection apply. |
| 07-TD.01101 | 1 - for Free Zones | VAT not collected on goods/services delivered to Free Trade Zones, as per incentive rules. |
| 07-TD.01102 | 2 - for Bonded Warehouses | VAT is not collected for transactions related to Bonded Warehouses under incentive mechanisms. |
| 07-TD.01103 | 3 - for Grants and Foreign Assistance | VAT is not collected for deliveries funded by foreign grants or international aid, borne by government. |
| 07-TD.01104 | 4 - for Avtur | VAT not collected for aviation turbine fuel for international flights. |
| 07-TD.01105 | 5 - for Others | VAT is not collected for other categories of goods/services determined by regulation or government policy. |
| 07-TD.01106 | 6 - for Contractors of Coal Mining Business Work Agreements Generation I | VAT not collected on supplies for Generation I Coal Contract Holders. |
| 07-TD.01107 | 7 - for Delivery of fuel oil for Overseas Sea Transport Vessels | VAT is not collected for oil fuel supplied to international marine vessels. |
| 07-TD.01108 | 8 - for Delivery of taxable services related to certain means of transportation | VAT not collected for specific transportation-related services. |
| 07-TD.01109 | 9 - for Delivery of Certain BKP in KEK | VAT not collected for strategic goods delivered to Special Economic Zones. |
| 07-TD.01110 | 10 - for certain BKP of a strategic nature in the form of anode slime | VAT not collected for strategic goods like anode slime. |
| 07-TD.01111 | 11 - for Delivery of certain means of transportation and/or Taxable Services related to certain means of transportation | VAT not collected for specific transport vehicles/services. |
| 07-TD.01112 | 12 - for Delivery to Oil and Gas Cooperation Contractors that comply with the provisions of Government Regulation Number 27 of 2017 | VAT not collected for upstream oil and gas contractors under GR 27/2017. |
| 07-TD.01113 | 13 - Delivery of Landed Houses and Apartment Units Borne by the Government in the 2021 Fiscal Year | VAT borne by the Government for residential property transactions in 2021. |
| 07-TD.01114 | 14 - Delivery of Room or Building Rental Services to Retail Traders Borne by the Government in the 2021 Fiscal Year | VAT borne by the Government for commercial rental services in 2021. |
| 07-TD.01115 | 15 - Delivery of Goods and Services in COVID-19 Pandemic Handling Framework (PMK 239/PMK. 03/2020) | VAT not collected for pandemic-response goods/services as per PMK 239. |
| 07-TD.01116 | 16 - PMK-103/PMK.010/2021 Incentive in the form of VAT on the Submission of Landed Houses and Apartment Residential Units Borne by the Government in the 2021 Fiscal Year | Government covers VAT for eligible housing transactions in 2021 under PMK 103. |
| 07-TD.01117 | 17 - Special Economic Zone PP number 40 of 2021 | VAT not collected for KEK transactions under GR 40/2021. |
| 07-TD.01118 | 18 - Free Zone PP number 41 of 2021 | VAT not collected for transactions in Free Zones under GR 41/2021. |
| 07-TD.01119 | 19 - Submission of Landed Houses and Apartment Residential Units Borne by the Government in the 2022 Fiscal Year | VAT borne by the Government for housing transactions in 2022. |
| 07-TD.01120 | 20 - VAT Borne by the Government in the context of Handling the Corona Virus Pandemic | VAT on pandemic-related supplies is borne by the Government. |
| 07-TD.01121 | 21 - Submission to Oil and Gas Cooperation Contractors who comply with the provisions of Government Regulation Number 53 of 2017 | VAT not collected for oil and gas contractors under GR 53/2017. |
| 07-TD.01122 | 22 - Certain strategic BKP in the form of anode slime and gold granules | VAT not collected for delivery of strategic materials like anode slime and gold. |
| 07-TD.01123 | 23 - for the submission of newspaper and/or magazines | VAT not collected on printed newspapers or magazines. |
| 07-TD.01124 | 24 - VAT is not collected by other Governments | VAT is not collected due to diplomatic or inter-governmental arrangements. |
| 07-TD.01125 | 25 - BKP and JKP certain | VAT not collected on specifically designated taxable goods and services. |
| 07-TD.01126 | 26 - Delivery of BKP and JKP in the new National Capital | VAT not collected for supplies supporting Indonesia's new capital development. |
| 07-TD.01127 | 27 - Delivery of battery-based electric vehicles | VAT not collected for electric vehicle deliveries to promote sustainability. |
| 08-TD.01101 | 1 - for Certain BKP and JKP | Certain goods and services are exempt from VAT under specific regulations. |
| 08-TD.01102 | 2 - for Certain BKP of a Strategic Nature | Strategic goods are exempt from VAT as designated by policy. |
| 08-TD.01103 | 3 - for Airport Services | VAT exempted for specific airport services to support connectivity and infrastructure. |
| 08-TD.01104 | 4 - for Others | Miscellaneous exemptions outside specific categories as outlined in tax regulations. |
| 08-TD.01105 | 5 - for Certain BKP of a Strategic Nature according to PP Number 81 of 2015 | VAT exempted on strategic goods under GR No. 81/2015. |
| 08-TD.01106 | 6 - for Delivery of Certain Port Services for Foreign Sea Transportation Activities | VAT exempted for port services supporting international shipping. |
| 08-TD.01107 | 7 - for Delivery of Clean Water | VAT exempted for clean water supply, as it is an essential service. |
| 08-TD.01108 | 8 - Delivery of Certain BKP of a Strategic Nature based on PP 48 of 2020 | VAT exempted on goods declared strategic under GR No. 48/2020. |
| 08-TD.01109 | 9 - Delivery to Representatives of Foreign Countries and International Agencies and Their Officials | VAT exempted for diplomatic and international agency transactions. |
| 08-TD.01110 | 10 - Certain BKP and JKP | Specific goods and services are exempt from VAT under applicable rules. |

The following criteria are required to define the **FacilityStampLookup**:

- Sales tax code
- Transaction classifier
- Exempt reason
- Sales tax group
- Item sales tax group

### UnitOfMeasurementLookup

**UnitOfMeasurementLookup** represents the standard units of measurement used in transactions and reporting. This ensures consistency, clarity, and compliance in data entry, reporting, and analysis across various tax and business processes.

| Lookup Result | Label EN | Description EN |
|---------------|----------|----------------|
| UM.0003 Kilogram | Kilogram | Kilogram is a metric unit of mass or weight. |
| UM.0004 Gram | Gram | Gram is a metric unit of mass, smaller than a kilogram. |
| UM.0005 Karat | Carat | Carat is a unit used for measuring the weight of gemstones. |
| UM.0001 Metrik Ton | Metric Ton | Metric Ton is equal to 1,000 kilograms. |
| UM.0002 Wet Ton | Wet Ton | Wet Ton is a unit for weight including moisture, often used in commodities. |
| UM.0006 Kiloliter | Kiloliter | Kiloliter is a metric unit of volume equal to 1,000 liters. |
| UM.0007 Liter | Liter | Liter is a metric unit of volume commonly used for liquids. |
| UM.0008 Barrel | Barrel | Barrel is a unit of volume often used for oil and other liquids. |
| UM.0009 MMBTU | MMBTU | MMBTU (Million British Thermal Units) is a unit of energy. |
| UM.0010 Ampere | Ampere | Ampere is a unit of electric current. |
| UM.0011 Sentimeter Kubik | Cubic Centimeter | Cubic Centimeter is a metric unit of volume. |
| UM.0012 Meter Persegi | Square Meter | Square Meter is a metric unit of area. |
| UM.0013 Meter | Meter | Meter is a metric unit of length. |
| UM.0014 Inches | Inches | Inches are a unit of length used in the imperial system. |
| UM.0015 Sentimeter | Centimeter | Centimeter is a metric unit of length smaller than a meter. |
| UM.0016 Yard | Yard | Yard is a unit of length in the imperial system. |
| UM.0017 Lusin | Dozen | Dozen means 12 items; commonly used in counting grouped goods. |
| UM.0018 Unit | Unit | Unit is a general term for a single item or entity. |
| UM.0019 Set | Set | Set refers to a collection of related items considered as a unit. |
| UM.0020 Lembar | Sheet | Sheet is used to count flat items like paper. |
| UM.0021 Piece | Piece | Piece refers to a single item or part. |
| UM.0022 Boks | Box | Box refers to a container or unit of packaging. |
| UM.0023 Tahun | Year | Year is a unit of time consisting of 12 months. |
| UM.0024 Bulan | Month | Month is a unit of time, part of a calendar year. |
| UM.0025 Minggu | Week | Week is a unit of time equal to seven days. |
| UM.0026 Hari | Day | Day is a basic unit of time, equal to 24 hours. |
| UM.0027 Jam | Hour | Hour is a unit of time equal to 60 minutes. |
| UM.0028 Menit | Minute | Minute is a unit of time equal to 60 seconds. |
| UM.0029 Persen | Percent | Percent expresses parts per hundred. |
| UM.0030 Kegiatan | Activity | Activity refers to a task or event, often quantified in planning or execution. |
| UM.0031 Laporan | Report | Report is a document summarizing information or data. |
| UM.0032 Bahan | Material | Material refers to substances or inputs used in manufacturing or construction. |
| UM.0033 Lainnya | Others | Others is used for unspecified or miscellaneous units. |

The following criteria are required to define the **UnitOfMeasurementLookup**:

- Units (UnitOfMeasure)

## Set up General ledger parameters

To generate the **SPT Masa PPN** report in Excel format, define an ER format on the **General ledger parameters** page.

1. Go to **Tax** \> **Setup** \> **General ledger parameters**.
2. On the **Sales tax** tab, in the **Tax options** section, in the **VAT statement format mapping** field, select **VAT Declaration Excel (ID)**. If you leave the field blank, the standard sales tax report will be generated in SQL Server Reporting Services (SSRS) format.

## Generate an SPT Masa PPN report

The process of preparing and submitting an **SPT Masa PPN** report for a period is based on sales tax payment transactions that were posted during the **Settle and post sales tax** job. For more information about sales tax settlement and reporting, see [Sales tax overview](../../general-ledger/indirect-taxes-overview.md).

Follow these steps to generate the tax declaration report.

1. Go to **Tax** \> **Declarations** \> **Sales tax** \> **Report sales tax for settlement period** or **Settle and post sales tax**.
2. Select the settlement period.
3. Select the from date.
4. Select the sales tax payment version.
5. Select **OK**. 
6. In the next dialog box, enter the following information:

    - The business activity code.
    - The amount of compensation for excess VAT that was caused by correction of the tax period's VAT SPT, if applicable.
    - The amount of VAT excess compensation for the previous tax period, if applicable.
    - The date of compensation for excess VAT, if applicable.
    - The amount of VAT that was paid in advance during the same tax period.
    - The version number. Valid version numbers are from 0 through 7.
    - Output file type. Select one or many options from provided list of pages of **SPT Masa PPN** report and click **Select**.

7. Select **OK** to confirm your settings and generate the report.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
