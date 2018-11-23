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

