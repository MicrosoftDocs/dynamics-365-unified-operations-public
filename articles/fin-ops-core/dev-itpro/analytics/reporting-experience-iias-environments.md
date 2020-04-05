---
# required metadata

title: Default reporting experiences in Iaas environments
description:  
author: 
manager: AnnBe
ms.date: 03/17/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 27661
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: milindav
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Paginated Reporting in Dynamics 365 applications

[!include [banner](../includes/banner.md)]

## Reporting scenarios in ERP
Historically, the Reporting Services bundled with Dynamics 365 applications have been used to facilitate two basic user functions in Enterprise Resource Planning:  Document generation (Doc Gen); and BI & Analytics.  These two functions represent the most common methods of accessing data produced as a result of business activities.

- Document generation - the production and distribution of structured documents with the primary purpose of printing and bulk email distributions
- BI & Analytics - interactive visualizations based on aggregations with embedded links to referenced data that make it possible for users to identify patterns and trends in large amounts of data

Although, Reporting Services continue to be the ideal tool for bulk production of business documents, these solutions lack extensibility options allowing Power Users to evolve analytical views to align with frequent changes in business.  At the same time, the Power BI service is recognized as an industry leader in delivering powerful analytics for businesses of all sizes.  With the latest release of Dynamics 365 Finance & Operations, Power BI service integration options are available to accommodate seamless data exploration of customer business data.

***Note:***  By default, documents rendered to 'Screen' by the Document Reporting service will take advantage of the Embedded PDF viewer .  With the Platform Update 36 Release, the Dynamics 365 service will discontinue support for the Report Viewer control used to facilitate BI & Analytics interactions with paginated reports. 

### Comparing report scenarios
With Doc Gen scenarios in Dynamics 365 applications, a user interaction triggers the production of anywhere between one and hundreds of documents, often decorated with graphics relaying commercial branding, distributed to both external and internal recipients used actions based on pre-defined routing instructions.

Let's compare the fundamentals of the two reporting experiences

## Enhancements in Paginated reporting
There are several advantages in using the PDF to interact with document rendered by the Document Reporting service bundled with Dynamics 365 Finance & Operations.  

- ***Reports display to 'Screen' faster*** - end users will benefit from improved performance when displaying reports on 'Screen'.  Users will notice a reduction in the number of progress bars leading to faster reports.
- ***Enhanced service reliability*** - the latest BI & Reporting service architecture delivers the power of Cloud scale to customers environments.  Service includes automatic scaling to maximize resource utilization
- ***Higher fidelity with printed output*** - documents are displayed in PDF formats offering consistency with printer output.  
- ***Print documents using local devices*** - maintain user identity when sending documents to printers directly from your browser.  Use Secure print jobs by printing documents using built-in user options displayed in the control toolbar.

Click here for more details on the previewing the embedded PDF viewer in environments using PU32 or later.  

### Disabling BI & Analytics on 1Box environments
In Platform Update 35 or later, developers will have the ability to preview existing solutions by forcing the local Reporting Service to render RDL with BI & Analytics features disabled.  This viewing mode is referred to as RDL Sandboxing and can be enable/disabled using PowerShell commands.

Use the following steps to enable RDL Sandboxing in your local 1 box environment
***Steps:***
        1) Log into 1Box environment using ***PU35 or later***
        2) Start the Control Panel
        3) Navigate to ***C:\AOSService\PackagesLocalDirectory\Plugins\AxReportVmRoleStartupTask***
        4) Run the command:  ***UpdateRDLSandboxRule.ps1***
        5) Restart the local SSRS service using the command using Reporting Services Configuration tool

