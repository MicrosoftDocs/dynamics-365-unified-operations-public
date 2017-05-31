---
# required metadata
title: Invoice processing overview
description: This topic provides information about invoice processing for Eastern Europe.
author: v-kikozl
manager: AnnBe
ms.date: 05/11/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 
# optional metadata
# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
# ms.reviewer: shylaw
# ms.search.scope: [Which Operations client to show this topic as help for, to be set by content strategist, see list here:https://microsoft.sharepoint.com/teams/DynDoc/_layouts/15/WopiFrame.aspx?sourcedoc={23419e1c-eb64-42e9-aa9b-79875b428718}&action=edit&wd=target%28Core%20Dynamics%20AX%20CP%20requirements%2Eone%7C4CC185C0%2DEFAA%2D42CD%2D94B9%2D8F2A45E7F61A%2FVersions%20list%20for%20docs%20topics%7CC14BE630%2D5151%2D49D6%2D8305%2D554B5084593C%2F%29]
# ms.tgt_pltfrm: 
# ms.custom: [used by loc]
ms.assetid: [Go get from guidgenerator.com]
ms.search.region: Eastern Europe
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: v-kikozl
ms.search.validFrom: [month/year of release that feature was introduced in, in format yyyy-mm-dd]
ms.dyn365.ops.version: [name of release that feature was introduced in, see list here:https://microsoft.sharepoint.com/teams/DynDoc/_layouts/15/WopiFrame.aspx?sourcedoc={23419e1c-eb64-42e9-aa9b-79875b428718}&action=edit&wd=target%28Core%20Dynamics%20AX%20CP%20requirements%2Eone%7C4CC185C0%2DEFAA%2D42CD%2D94B9%2D8F2A45E7F61A%2FVersions%20list%20for%20docs%20topics%7CC14BE630%2D5151%2D49D6%2D8305%2D554B5084593C%2F%29]
---

# Invoice processing overview

The information below introduces changes in the Eastern European localization related to the customer and vendor invoice processing. These changes support country-specific legal requirements regarding to the filling and control of the dates that are important for tax reporting in those countries.

 - the sales date in customer invoices and the document receipt date in
   vendor invoices,  
 - the date of VAT register.

Also it provides a short description for some country-specific scenarios, for example, Intra-community VAT or Deferred tax.

|Scenario   |Applicable for countries   |Description of the functionality changes   |
|---|---|---|
|Accounts receivable and Accounts payable dates for VAT   |Czech Republic   | When the goods are purchased from the European Union countries, there is an obligation of self-assessment of VAT: <br>  - the output VAT must be paid in VAT period where the invoice has been issued (Document date),<br>  - the input VAT can’t be deducted before document receipt (VAT register date).<br>The following settings should be done to support this scenario:<br>  - enable ‘Intra-community VAT’ and ‘Document date for intra-community VAT’ in the Accounts payable parameters,<br>  - two sales tax codes: one with positive sales tax percentage and another with negative,<br>  - set up a sales tax group including both positive and negative sales tax codes. Negative sales tax code will have ‘Intra-community VAT’ parameter set to true.<br>In result a purchase will have two posted sales tax transactions:<br>  - a positive transaction with direction ‘sales tax receivable’ and VAT register date equals to the same date from the invoice posting window,<br>  - a negative transaction with direction ‘sales tax payable’ and VAT register date equals to the Document date. |
|   |   |   |
|   |   |   |
