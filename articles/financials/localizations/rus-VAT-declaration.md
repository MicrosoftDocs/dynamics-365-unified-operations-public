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

For example, to generate VAT declaration for reporting period 2018 year, download the latest versions of the following configurations:

   VAT declaration model (RU)
       VAT declaration model mapping (RU)
       VAT declaration format 5.05

Fix downloading instructions are here:
https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/analytics/download-electronic-reporting-configuration-lcs 

2.	Optionally set up **Financial report** for VAT declaration and calculation rules for **Financial report cells**. Set it up if you are going to use Financial reports for generating data for some cells in Chapter 3 of VAT declaration based on financial reports cells setup.
You can find more details about how to set up Financial reports in Financial reporting (Russia) article 

3.	For the first use, optionally Upload Data management package settings to work with Russian VAT declaration


   1)	In the LCS Shared asset library https://lcs.dynamics.com/V2, click on **Shared asset library** tile.
   2)	Select asset type **Data package**. Download package with name “RU VAT Declaration demo setup”. As result, file RU VAT  Declaration.zip will be downloaded.
   3)	In the **Data management** workspace of Dynamics 365 for Finance and operations, click **Import**
   4)	Fill in **Job details** group of fields:
  
      a.	In the field **Name** enter the job name
      b.	In the **Data source format** field, select value “Package”
      
   5)	In the **Upload data file**, click **Upload** and choose the RU VAT Declaration.zip file downloaded on the previous step.
   6)	When upload of Data entities finishes, click on button **Import**.
   7)	Validate the imported Financial report at **General ledger > Financial reports setup > Financial reports**

## Overview

Russian VAT declaration version 5.05 contains the following information:

Section 1 – Total VAT amount to be paid to budget, or to be reclaimed. This chapter contains cumulative amounts from chapters 3,4,5,6,7

Section 2 – VAT amount to be paid to budget by Tax agent. 

Section 3 – Calculation of VAT amounts to be paid to budget or to be reclaimed

Application 1 to Section 3 – VAT amounts previously deducted and which are now subject to restoration and payment to budget for fixed assets used in non-taxable operations

Section 4 – Calculation of VAT amounts for export sales where tax rate 0% is confirmed during the period

Section 5 – Calculation of VAT deduction amounts of the reporting period for export sales where tax rate 0% was confirmed in previous periods.

Section 6 – Calculation of VAT amounts for export sales where tax rate 0% is should have been but was not confirmed during the period

Section 8 – Information from Purchase book

Section 8.1 – Appendix to Chapter 8 – Information from additional sheets to purchase book

Section 9 – Information from Sales book

Section 9.1 – Appendix to Chapter 9 – Information from additional sheets to sales book

Section 10 – Information from Issued factures journal regarding intermediary deals

Section 11 - Information from Received factures journal regarding intermediary deals

You can find more details about how to generate Sales, purchase books and facture accounting journal in https://msdyneng.visualstudio.com/web/wi.aspx?pcguid=a1559462-dfa9-4e8b-8925-9299fe8a88ab&id=148853 article


## Section 2 VAT amount to be paid to budget by Tax agent.

In the Section 2 of VAT declaration, VAT amounts calculated based on Tax agent transactions, are reflected. 
You can find more details about how to set up and register Tax agent transactions in Value-added tax (VAT) for tax agents (Russia) article https://docs.microsoft.com/en-us/dynamics365/unified-operations/financials/localizations/rus-tax-agent.

A separate section for each Tax agent is created which contains the following information:

- name of organization for which legal entity is acting as Tax agent (line 020)
- tax registration Id of type of organization for which legal entity is acting as Tax agent (line 030)
- budget classification code (line 040)
- territory code (line 050)
- VAT amount calculated for tax agent transactions (line 060)
- VAT operation code (line 070)

## Section 3 Calculation of VAT amounts to be paid to budget or to be reclaimed

In the Section 3 of VAT declaration, amounts of the registered factures, incoming VAT and restored VAT amounts from the sales and purchase books are reflected, as shown in the following table. These amounts are generated automatically based on registered documents.

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
You should set up Financial report and financial report cells to calculate required cells values. You can find more details in Financial reporting (Russia) article.

You should define the following names of Financial report cells so that the calculated amounts are automatically exported to VAT declaration format 5.05:

|**Name of cell** |	**Line-Column of Section 3** |
| --- | --- |
| **ax payable** |
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







