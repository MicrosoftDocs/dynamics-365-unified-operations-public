--- 
# required metadata 
 
title: Semansys XBRL integration
description: This procedure walks you through using Dutch functionality to export financial data in the XML format. 
author: mrolecki
manager: AnnBe 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: Dialog   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Netherlands
# ms.search.industry: 
ms.author: mrolecki
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---

# Delivering XBRL to Dutch Regulatory bodies via Semansys XBRLOne

[!include [banner](../../includes/banner.md)]

This document walks you through the steps to map, export and ultimaly deliver XBRL (eXtensible Business Reporting Language) to the Dutch regulatory body.  

The high level process is a System to Human to System process.  The first system involved is Microsoft Dynamics 365 Finance.  This system is responsible for creating all the necessary entries, chart of accounts and mappings necessary.  Once this is done, then a user will export the data into the Semansys DataBridge format.  This exported data can then be uploaded into the XBRLOne portal to convert to XBRL, validate and deliver to the correct Dutch regulatory body. 

There are a few prerequisties for this process:
* The report data is available for mapping via the General Ledger in Microsoft Dynamics 365 Finance
* Knowledge of the correct taxonomy for which you're reporting and confirmation that you're delivering to a Dutch regulatory body
* Import "**Dutch XBRL integration model**" and "**Semansys XBRL (NL)**" electronic reporting configurations

For more information about how to download ER configurations from Microsoft Dynamics Lifecycle Services (LCS), see [Download Electronic reporting configurations from Lifecycle Services](https://docs.microsoft.com/en-us/dynamics365/dev-itpro/analytics/download-electronic-reporting-configuration-lcs).

Below are the example steps for a user to export the data necessary for reporting a 2019 annual report. 
1. Go to **General ledger** > **Periodic tasks** > **Export financial data to XBRL**.
2. In the From date field, enter a date; e.g. *2019-01-01*  
3. In the To date field, enter a date; e.g *2019-12-31*  
4. In the Format mapping field, enter the correct formats
5. Click **OK**.

You can now take this Semansys DataBridge format package to the XBRLOne portal for next steps.
