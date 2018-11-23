---
# required metadata
title: VAT declaration (Russia)
description: This topic provides information about VAT declaration for Russia
author: anasyash
manager: AnnBe
ms.date: 11/23/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata
ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: anasyash
ms.search.validFrom: 2018-11-23
ms.dyn365.ops.version: 8.1.1

---

# VAT declaration (Russia)

## Set up

To start working with VAT declaration, you should do the following:

1.	Download ER configurations from LCS Shared asset library
You need to download the latest version of ER configuration VAT declaration format.

For example, to generate VAT declaration for reporting period 2018 year, download the latest versions of the following configurations  

  - VAT declaration model (RU)
     - VAT declaration model mapping (RU)
     - VAT declaration format 5.05

Fix downloading instructions are here:
https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/analytics/download-electronic-reporting-configuration-lcs 

2.	Optionally set up **Financial report** for VAT declaration and calculation rules for **Financial report cells**. Set it up if you are going to use Financial reports for generating data for some cells in Section 3 of VAT declaration based on financial reports cells setup.
You can find more details about how to set up Financial reports in (Financial reporting (Russia) article https://docs.microsoft.com/ru-ru/dynamics365/unified-operations/financials/localizations/rus-financial-reports


3.	For the first use, optionally Upload Data management package settings to work with Russian VAT declaration
  1. 	In the LCS Shared asset library https://lcs.dynamics.com/V2, click on **Shared asset library** tile.
  2. Select asset type **Data package**. Download package with name “RU VAT Declaration demo setup”. As result, file RU VAT  Declaration.zip will be downloaded.
  3. In the **Data management** workspace of Dynamics 365 for Finance and operations, click **Import**
  4. Fill in **Job details** group of fields
     1. In the field **Name** enter the job name
     2. In the **Data source format** field, select value “Package”
      
  5. In the **Upload data file**, click **Upload** and choose the RU VAT Declaration.zip file downloaded on the previous step.
  6. When upload of Data entities finishes, click on button **Import**.
  7. Validate the imported Financial report at **General ledger > Financial reports setup > Financial reports**

## Overview

Russian VAT declaration version 5.05 in XML format is configured in **Electronic reporting** module and contains the following information:

- *Section 1* – Total VAT amount to be paid to budget, or to be reclaimed. This section contains cumulative amounts from sections 3,4,5,6,7

- *Section 2* – VAT amount to be paid to budget by Tax agent. 

- *Section 3* – Calculation of VAT amounts to be paid to budget or to be reclaimed

  - *Application 1 to Section 3* – VAT amounts previously deducted and which are now subject to restoration and payment to budget for fixed assets used in non-taxable operations

- *Section 4* – Calculation of VAT amounts for export sales where tax rate 0% is confirmed during the period

- *Section 5* – Calculation of VAT deduction amounts of the reporting period for export sales where tax rate 0% was confirmed in previous periods.

- *Section 6* – Calculation of VAT amounts for export sales where tax rate 0% is should have been but was not confirmed during the period

- *Section 8* – Information from Purchase book

  - *Section 8.1* – Appendix to Chapter 8 – Information from additional sheets to purchase book

- *Section 9* – Information from Sales book

  - *Section 9.1* – Appendix to Chapter 9 – Information from additional sheets to sales book

- *Section 10* – Information from Issued factures journal regarding intermediary deals

- *Section 11* - Information from Received factures journal regarding intermediary deals

You can find more details about how to generate Sales, purchase books and facture accounting journal in https://msdyneng.visualstudio.com/web/wi.aspx?pcguid=a1559462-dfa9-4e8b-8925-9299fe8a88ab&id=148853 article


## Section 2 VAT amount to be paid to budget by Tax agent.

Section 2 of VAT declaration contains VAT amounts which are calculated based on Tax agent transactions. 

You can find more details about how to set up and register Tax agent transactions in Value-added tax (VAT) for tax agents (Russia) article https://docs.microsoft.com/en-us/dynamics365/unified-operations/financials/localizations/rus-tax-agent.

A separate section for each Tax agent is created which contains the following information:

- name of organization for which legal entity is acting as Tax agent (line 020)
- tax registration Id of type of organization for which legal entity is acting as Tax agent (line 030)
- budget classification code (line 040)
- territory code (line 050)
- VAT amount calculated for tax agent transactions (line 060)
- VAT operation code (line 070)

## Section 3 Calculation of VAT amounts to be paid to budget or to be reclaimed

Section 3 of VAT declaration, contains amounts of the registered factures, incoming VAT and restored VAT amounts from the sales and purchase books, as shown in the following table. These amounts are generated automatically based on registered documents.

| Line number	| Column number	| Name	| XML attribute, element name	| Description |
|---|---|---|---|---|
|**VAT payable** |
|010	| 3	| Transfer of goods, services and property rights	| РеалТов18\ НалБаза	| Tax base of outgoing customer invoices with VAT at 18 percent. |
| 010	| 4	| Transfer of goods, services and property rights	| РеалТов18\ СумНал	| VAT amount of outgoing customer invoices with VAT at 18 percent.|
| 020	| 3	| Transfer of goods, services and property rights	| РеалТов10\ НалБаза	| Tax base of outgoing customer invoices with VAT at 10 percent.|
| 020	| 4	| Transfer of goods, services and property rights	| РеалТов10\ СумНал	| VAT amount of outgoing customer invoices with VAT at 10 percent.|
| 070	| 3	| Prepayments or partial payments received from customers for future shipments	| ОплПредПост\ НалБаза	| Tax base of factures for prepayments received from customers for future shipments.|
| 070	| 4	| Prepayments or partial payments received from customers for future shipments	| ОплПредПост\ СумНал	| VAT amount of factures for prepayments received from customers for future shipments| 
| 080	| 4	| Tax amounts that were accepted for deduction, which are subject to restoration, total	| СумНалВосст\ СумНалВс	| The amount of restored VAT based on the following outgoing VAT processing data: -- Incoming factures related to nontaxable shipments for the current reporting period. - Outgoing factures on prepayments made to vendors. - Fixed assets used in nontaxable operations. |
| 090	| 4	| Tax amounts that were accepted for deduction and which are subject to restoration, for prepayments to vendors	| СумНалВосст\ СумНал170.3.3	| The amount of restored VAT based on outgoing factures on prepayments made to vendors. The VAT restoration occurs in the current reporting period| 
| 100	| 4	| Tax amounts that were accepted for deduction and which are subject to restoration for operations subject to 0% VAT rate |  СумНалВосст\ СумНалОперСт0 | 	The amount of restored VAT for all export factures during the current reporting period|
| **VAT receivable / deductible** |
| 120	| 3	| Tax amount accepted during acquisition of goods, services, and property rights that are subject to tax deduction |  НалПредНППриоб	| The amount of incoming VAT subject to reimbursement of factures on purchase invoices. The purchases include goods, services, and property rights that are subject to tax deduction. |
| 130	| 3	| Tax amounts accepted when prepayments are made to vendors for future acquisitions that are subject to tax deduction |	НалПредНППок	| The amount of incoming VAT subject to reimbursement of factures on prepayments made to vendors.|
| 150	| 3	| Tax amount that was accepted for deduction when goods were imported for internal consumption |	НалУплТамож	| The VAT amount of factures of GTD and KTS types when goods are imported from territories other than Belarus.|
| 160	| 3	| Tax amount that was accepted for deduction when goods were imported from Belarus	| НалУплНОТовТС	| The VAT amount of factures with types GTD (Custom declaration), and KTS (Customs values correction) when goods are imported from Belarus.|
| 170	| 3	| Tax amount that was accepted for deduction after delivery of goods to customers	НалИсчПрод	The amount of incoming VAT of factures on prepayments received from customers for future shipments. The amount is subject to refund after goods are delivered or services are rendered|
| 180	| 3	| Tax amount that was accepted for deduction for a buyer-tax agent	| НалУплПокНА	| The VAT amount of factures on tax agent transactions with the Facture source = Tax correction|

In Section 3 you can also get amounts of Financial report which is set up for VAT declaration. 
You should set up Financial report and financial report cells to calculate required cells values. You can find more details in Financial reporting (Russia) article https://docs.microsoft.com/en-us/dynamics365/unified-operations/financials/localizations/rus-financial-reports

You should define the following names of Financial report cells so that the calculated amounts are automatically exported to Section 3 of VAT declaration format 5.05:

|**Name of cell** |	**Line-Column of Section 3** |
| --- | --- |
| **Tax payable** |
| РеалТов18НалБаза	| 010-3 *** |
| РеалТов18СумНал	| 010-4 *** |
| РеалТов10НалБаза	| 020-3 *** |
| РеалТов10СумНал	| 020-4 *** |
| РеалСрок151.1_118НалБаза	| 041-3|
| РеалСрок151.1_118СумНал	| 041-4|
| РеалСрок151.1_110НалБаза	| 042-3|
| РеалСрок151.1_110СумНал	| 042-4|
| РеалПредИКНалБаза	| 050-3 |
| РеалПредИКСумНал	| 050-4 |
| ВыпСМРСобНалБаза	| 060-3 |
| ВыпСМРСобСумНал	| 060-4 |
| ОплПредПостНалБаза	| 070-3 *** |
| ОплПредПостСумНал	| 070-4 *** |
| СумНалВосстСумНалВс	| 080-4 *** |
| СумНалВосстСумНал170.3.3	| 090-4 *** |
| СумНалВосстСумНалОперСт0	| 100-4 *** |
| КорРеалТов18НалБаза	| 105-3 |
| КорРеалТов18СумНал	| 105-4 |
| КорРеалТов10НалБаза	| 106-3 |
| КорРеалТов10СумНал	| 106-4 |
| КорРеалТов118НалБаза	| 107-3 |
| КорРеалТов118СумНал	| 107-4 |
| КорРеалТов110НалБаза	| 108-3 |
| КорРеалТов110СумНал	| 108-4 |
| КорРеалПредИКНалБаза	| 109-3 |
| КорРеалПредИКСумНал	| 109-4 |
| УплДеклар151.1НалБаза	| 110-3 |
| УплДеклар151.1СумНал	| 110-4 |
| УплДеклар173.6НалБаза	| 115-3 |
| УплДеклар173.6СумНал	| 115-4 |
| **Tax receivable and deductible** |
| НалПредНППриоб |	120-3 *** |
| НалПредНПКапСтр	| 125-3 |
| НалПредНППок	| 130-3 *** |
| НалИсчСМР	| 140-3 |
| НалУплТамож	| 150-3 *** |
| НалУплНОТовТС | 160-3 *** |
| НалИсчПрод	| 170-3 *** |
| НалУплПокНА	| 180-3 *** |
| НалВыч171.14	| 185-3 |

Note. Requisites marked with *** are calculated automatically based on registered documents as described above. 
  If you set up Financial report cells calculation rules for them, the calculated amounts of Financial report will be added to automatically calculated amounts. 
  
  If you want to replace automatic calculation by Financial report cell calculation, review **How to customize Section 3 of VAT declaration** section of this article.

Tip. You can download demo setup of Financial report for VAT declaration from Data package **RU VAT declaration demo setup** of LCS Shared asset library.


### How to customize Section 3 of VAT declaration

Section 3 is represented in VAT declaration model (RU) by model element **Declaration items**. 
In ER configuration **VAT declaration model mapping (RU)** this element is bound to the data source **$RRG.$Section3.$data** that is configured as **$RRG.$Section3.$data = LISTJOIN(@.'$dataStd', @.'$dataCustom')**. It refers to two data sources: 

   - **$RRG.$Section3.$data.$dataStd**: This data source is configured to access the application class **VAT Declaration helper (RU)** by calling the method **getSection3data** which is producing the list with amounts of several Section 3 boxes 

   - **$RRG.$Section3.$data.$dataCustom**: This data source is configured to access the application class **LedgerRRGCustomReportHelper_RU** by calling the method **getCustomReportData** which is producing the record list with calculated amounts for some Financial report cells configured by user

To customize the declaration, you can do either of the following:

   - set up Financial report to calculate cells which are not calculated automatically by **VAT Declaration helper (RU)** class
In this case you should to set up Financial report calculation rules for report cells not marked with *** above

   - set up Financial report to calculate cells fully based on user setup instead of automatic calculation. 
   In this case you should do the following: 
      1.	Set up Financial report calculation rules for all required cells, including those marked with ***
      2.	Create customized Model mapping ER configuration as derived from the one provided by Microsoft configuration provider 
      3.	In customized Model mapping ER configuration (created on the previous step), redefine model mapping data source **$RRG.$Section3.$data = '$dataCustom'** instead of  **$RRG.$Section3.$data = LISTJOIN(@.'$dataStd', @.'$dataCustom')**

   - extend the **VAT Declaration helper (RU) class** (use methods starting from "getSection3data" like getSection3dataDomesticVAT) or create alternative helper methods in a similar manner which calculate required cells values. 
   In this case you should do the following:
      1.	Create customized Model mapping ER configuration as derived from the one provided by Microsoft configuration provider 
      2.	Redefine the model mapping data source element $RRG.$Section3.$data.$dataStd

Learn how to create a derived version of ER configurations to do customization by using the (ER Upgrade your format by adopting a new, base version of that format topic) https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/analytics/tasks/er-upgrade-format.

Learn how to define model mappings in the (Define ER model mappings and select data sources for them article) https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/analytics/tasks/er-define-model-mapping-select-data-sources-2016-11?toc=/fin-and-ops/toc.json


## Application 1 to Section 3 

Application 1 contains information about fixed assets that are used in nontaxable activities. 
Application 1 is generated in the last reporting period of the calendar year and contains the restored VAT amount for the fixed asset calculated for the entire calendar year. Data for the section are generated based on VAT restoration journal entries.

This section contains:
- name of fixed asset (line 010)
- putting into operation date (line 030)
- depreciation start date (line 040)
- initial cost of fixed asset (line 050)
- incoming VAT amount related to fixed asset which was deducted (line 060)
- the year that the VAT restoration begins until the tenth year of depreciation for fixed asset (line 070, column 1)
- the date when the fixed asset was first used in non-taxable operations (line 070, column 2)
- the percentage of revenue for nontaxable goods and export operations (line 070, column 3)
- VAT amount restored for fixed asset in a year (line 070, column 4)


## Sections for export taxed at 0% rate.

Before generating these sections of VAT declaration, you should do the following settings:
1.	Create VAT operation codes for export trade at Tax > Setup > Sales tax > VAT operation codes
2.	Assign VAT operation codes to Sales tax codes at Tax > Indirect taxes > Sales tax > Sales tax codes

### Overview and example

Sections for export are generated based on Export factures registration and VAT restoration journal entries.
You can find more details about how to process export transactions in the Processing invoice-factures for Export trade article when it’s available.

**Example**:

*January 2018* – Products are purchased:

   Invoice V1/Facture1 – 10 pcs., at amount 118 000 RUB, incl. VAT 18% 18 000 RUB

*January 2018* – Incoming VAT deduction for Facture1: Amount incl. VAT 82 600 RUB, incl. VAT 18% 12 600 RUB
  Notice that incoming Facture contains only part of goods purchased with Invoice V1.

*April 2018* – Products are sold for export (at exchange rate 45 RUB / USD):

   Invoice C1 – 2 pcs., amount 600 USD = 27 000 RUB (respective incoming VAT amount is 3 600 RUB)
   Invoice C2 – 8 pcs., amount 2 400USD = 108 000 RUB (respective incoming VAT amount is 14 400 RUB)

In this example, the deadline for collecting all document for export 0% rate confirmation is September 2018

*August 2018* - Export for Invoice C1 confirmed in time.

*September 2018* - Export for Invoice C2 wasn’t confirmed by deadline. As result, VAT at domestic VAT rate 18% was calculated for this invoice.  108 000 * 18% = 19 440 RUB. 
    Respective incoming VAT deduction amount for not confirmed export is 9 000 RUB.

*November 2018* - Facture2 for left part of purchase by Invoice V1 is received. So, incoming VAT deduction for left part of Invoice V1 purchase is posted:
    Amount incl. VAT 35 400 RUB, incl. VAT 18% 5 400 RUB (this is for goods purchased by Invoice C2)


VAT declaration for III Quarter 2018 will contain Chapter 4 and Chapter 6

VAT declaration for IV Quarter 2018 will contain Chapter 5 

Find more details for this example below.


### Section 4 Calculation of VAT amounts for export sales where tax rate 0% is confirmed during the period

This section represents amounts for export factures if 0% rate was confirmed during the reporting period. Data are grouped by VAT operation code. The following data is exported:
- VAT operation code (line 010)
- Tax base (line 020)
- VAT amount deductible from the purchase of items used in export confirmed at 0% rate (line 030)
- Adjustment: VAT amount deductible which was paid in previous periods when 0% rate wasn’t confirmed yet (line 040).
- Adjustment: VAT amount restoration which was deducted in previous periods for not confirmed export (line 050).
Corrections of amounts for goods return:
- VAT operation code (line 060)
- Tax base (line 070)

**Example**

In example above, the following data will be present in Section 4 of VAT declaration for III quarter 2018:

| Requisite | Line | Value |
|----|----|-----|
| VAT operation code | 010 | 1011410 (as per the user setup for respective Sales tax code) |
| Tax base | 020| 27 000 |
| VAT amount deductible from the purchase of items used in export confirmed at 0% rate | 030 | 3 600 |


### Section 5 – Calculation of VAT deduction amounts of the reporting period for export sales where tax rate 0% was confirmed or not confirmed in previous periods.

This section represents VAT amounts deductible in the reporting period for export sales where 0% rate was confirmed or not confirmed in previous periods (“later” deductions of VAT amounts).  
Data are grouped by the period when respective export was declared, and VAT operation code. The following data is exported:

- Year when respective export was declared (line 010)
- Reporting period code when respective export was declared (line 020)
- VAT operation code (line 030)
- Tax base from the purchase of items used in confirmed export (line 040)
- VAT amount deductible from the purchase of items used in confirmed export (line 050)
- Tax base from the purchase of items used in not confirmed export (line 060)
- VAT amount deductible from the purchase of items used in not confirmed export (line 070)

**Example**

In example above, the following data will be present in Section 5 of VAT declaration for IV quarter 2018:

| Requisite | Line | Value |
|----|----|-----|
| Year when respective export was declared | 010 | 2018 |
| Reporting period code when respective export was declared | 020 | 23 – period code for III quarter |
| VAT operation code | 030 | 1011410 |
| Tax base from the purchase of items used in not confirmed export | 060 | 108 000 |
| VAT amount deductible from the purchase of items used in not confirmed export | 070 | 5 400 |


### Section 6 – Calculation of VAT amounts for export sales where tax rate 0% is should have been but was not confirmed during the period

This section represents amounts for export factures if 0% rate was not confirmed and deadline expired during the reporting period. Data are grouped by VAT operation code. The following data is exported:

- VAT operation code (line 010)
- Tax base (line 020)
- VAT amount payable calculated from the tax base for not confirmed export (line 030)
- VAT amount deductible from the purchase of items used in not confirmed export (line 040)
Corrections of amounts for goods return:
- VAT operation code (line 070)
- Tax base of goods return (line 080)
- VAT amount of goods return which is decreasing VAT amount payable (line 090)
- Adjustment: VAT amount from the purchase of items used in export, previously deducted and to be restored for goods return (line 100)

In example above, the following data will be present in Section 6 of VAT declaration for III quarter 2018:

| Requisite | Line | Value |
|----|----|-----|
| VAT operation code | 010 | 1011410 (as per the user setup for respective Sales tax code) |
| Tax base | 020 | 108 000 |
| VAT amount payable calculated from the tax base for not confirmed export | 030 | 19 440 |
| VAT amount deductible from the purchase of items used in not confirmed export | 040 | 9 000 |



How to start working with VAT declaration https://support.microsoft.com/en-us/help/4477332/rus-russia-vat-declaration-in-electronic-format?preview
