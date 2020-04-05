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
Historically, the Document Reporting Services bundled with Dynamics 365 applications have been used to facilitate two basic user functions in Enterprise Resource Planning:  **Document generation (Doc Gen)**; and **BI & Analytics**.  These two functions facilitate the most common methods of accessing business data.

- **Document generation** - the production and distribution of structured documents with the primary purpose of printing and bulk email distributions
- **BI & Analytics** - interactive visualizations often based on aggregations with embedded links to referenced data.  Users rely on these tools to identify patterns and trends in large amounts of data

Although, Document Reporting Services (RDL) continue to be the ideal tool for bulk production of business documents, these solutions lack extensibility options necessary for Power Users to adapt analytical views to account for frequent changes in the business environment.  At the same time, the [Power BI service](https://docs.microsoft.com/en-us/power-bi/fundamentals/power-bi-overview) is recognized as an industry leader in delivering powerful analytics for businesses of all sizes.  With the latest release of Dynamics 365 Finance & Operations, Power BI service integration options are available to accommodate seamless data exploration of customer business data.

**Note:**  With the Platform Update 36 Release, the Dynamics 365 service will discontinue support for the Report Viewer control used to facilitate BI & Analytics interactions with paginated reports.  Reports rendered to 'Screen' by the Document Reporting service will take advantage of the Embedded PDF viewer.

### Comparing report scenarios
With Doc Gen scenarios in Dynamics 365 applications, the business activity triggers the production of anywhere between one and hundreds of documents, often decorated with graphics including commercial branding, distributed to both external and internal recipients using pre-defined delivery routing instructions.

Let's compare the fundamentals of the two reporting experiences

|                           |         **Doc Gen**        |    **BI & Analytics**    |
|---------------------------|----------------------------|--------------------------|
| **Display format**        |      PDF & Office Docs     |            HTML          |
| **Data volume**           |        1 - 100s rows       |        >10Ks rows        |
| **Interactive features**      |        Printing, Text Search, Sharing       |        [Drill-thru, Drill-down, Sub-reports, Nested regions](https://docs.microsoft.com/en-us/sql/reporting-services/report-design/drillthrough-drilldown-subreports-and-nested-data-regions?view=sql-server-ver15)         |
| **Data source**        |      Transactional DB     |            Data warehouse          |
| **Report author**           |        Developer       |        Power User        |
| **Layout**      |        Structured, pre-defined layout       |        Adaptive, flexible         |
| **Recommended tooling**           |        [Document Reporting (RDL)](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/document-reporting-services?toc=/dynamics365/commerce/toc.json) / [Configurable Office Documents](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/general-electronic-reporting?toc=/dynamics365/commerce/toc.json)       |      [Power BI.com](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/power-bi-integration?toc=/dynamics365/commerce/toc.json) / [Analytical Workspaces](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/embed-power-bi-workspaces?toc=/dynamics365/commerce/toc.json)     |


## Enhancements in Paginated reporting
There are several advantages in using the PDF to interact with document rendered by the Document Reporting service bundled with Dynamics 365 Finance & Operations.  

- **Reports display to 'Screen' faster** - end users will benefit from improved performance when displaying reports on 'Screen'.  Users will appreciate the reduction in the number of progress bars leading to faster reports.
- **Enhanced service reliability** - the latest BI & Reporting service architecture delivers the power of Cloud scale to customers environments.  Service includes automatic scaling to maximize resource utilization
- **Higher fidelity with printed output** - documents are displayed in PDF formats offering consistency with printer output.  
- **Print documents using local devices** - maintain user identity when sending documents to printers directly from your browser.  Use Secure print jobs by printing documents using built-in user options displayed in the control toolbar.

[Click here](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/preview-pdf-documents) for more details on the previewing the embedded PDF viewer in environments using PU32 or later.  

### Disabling BI & Analytics on 1Box environments
In Platform Update 35 or later, developers will have the ability to preview existing solutions by forcing the local Reporting Service to render RDL with BI & Analytics features disabled.  This viewing mode is referred to as **RDL Sandboxing**.  This mode can be enable or disabled using PowerShell commands.

Use the following steps to enable RDL Sandboxing in your local 1 box environment
***Steps:***
1) Log into 1Box environment using **PU35 or later**
2) Start the Control Panel
3) Navigate to **C:\AOSService\PackagesLocalDirectory\Plugins\AxReportVmRoleStartupTask***\
4) Run the command:  **UpdateRDLSandboxRule.ps1**
5) Restart the local SSRS service using the command using Reporting Services Configuration tool

