---
# required metadata

title: Financial reporting (Russia)
description: This topic provides information about financial reporting for Russia.
author: AnastasiaYashenina
ms.date: 09/23/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: anasyash
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Financial reports (Russia)

[!include [banner](../includes/banner.md)]



The Financial reports setup allows you to configure list and content of “boxed” reports like
Balance sheet. For each report box or cell, the data collection for ledger
transactions, budget transactions, and calculated profit tax registers can be
configured. 

You should also configure report output in GER (electronic reporting) in a way where ER
configuration takes the data calculated according to user setup of the
financial report and generates the file output according to format
configuration (for example Excel and/or XML).


You should also configure Electronic message processing where one of the steps allows authorized user to
run the ER configuration of the financial report, generate report and store generated
report data.

## Financial reports setup

You should complete the following steps to set up the report:

   •	Setup list of report names
   
   •	Setup cells of the report
   
   •	Setup calculation criteria for report cells


### Setup list of report names
1.	Go to **General ledger > Financial reports setup > Financial reports**.
The **Overview** tab displays a list of all the reports that are set up in the system.
2.	Create new report. Enter a brief, and full names of the report in the **Report code** and **Description** fields.
3.	The **General** tab displays the general parameters for report generation. 
Define the following fields:






