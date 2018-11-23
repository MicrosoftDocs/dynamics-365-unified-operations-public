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


