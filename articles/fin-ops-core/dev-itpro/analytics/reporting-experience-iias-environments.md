---
# required metadata

title: Default reporting experiences in Iaas environments
description:  This topic provides information about paginated reporting in Dynamics 365 Finance and Operations apps.
author: TJVass
manager: AnnBe
ms.date: 04/06/2020
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

# Default reporting experiences in Iaas environments
[!include [banner](../includes/banner.md)]

## Reporting scenarios in ERP
The Document Reporting Services bundled with Dynamics 365 Finance and Operations apps provide end user tooling to facilitate two basic user functions in Enterprise Resource Planning: **Document generation (Doc Gen)** and **BI and Analytics**. These generic scenarios represent the two most common methods of accessing business data.

- **Document generation** - The production of structured documents often with the primary purpose of printing and bulk email distribution.
- **BI and Analytics** - Interactive visualizations based on aggregations that contain embedded links to referenced data. Users rely on these tools to identify patterns and trends in large amounts of data.

Though Document Reporting Services (RDL) continue to be the ideal tool for bulk production of business documents, these solutions lack the extensibility options that a Power User requires to adapt analytical views and account for frequent changes in the business environment.  At the same time, the [Power BI service](https://docs.microsoft.com/en-us/power-bi/fundamentals/power-bi-overview) is recognized as an industry leader in delivering powerful analytics for businesses of all sizes. Finance and Operations apps, Power BI service integration options are available to accommodate the seamless data exploration of customer business data.

> [!NOTE]
> With the release of the platform updates for verion 10.0.12, the Dynamics 365 service will discontinue support for the Report Viewer control that is used to facilitate BI and Analytics interactions with paginated reports. Reports rendered to 'Screen' by the Document Reporting service will now use the Embedded PDF viewer. For more information about the embedded PDF viewer, see [Preview PDF documents with an embedded viewer](preview-pdf-documents.md).

### Compare report scenarios
With Doc Gen scenarios, a simple business activity, either automated or manual, may trigger the production of anywhere between one and hundreds of documents, often decorated with graphics that include commercial branding. These documents are distributed to both internal and external recipients using pre-defined delivery routing instructions.

The following table compares the fundamentals of the two reporting experiences.

|                           |         **Doc Gen**        |    **BI and Analytics**    |
|---------------------------|----------------------------|--------------------------|
| **Display format**        |      PDF & Office Docs     |            HTML          |
| **Data volume**           |        1 - 100s rows       |        >10,000s rows     |
| **Interactive features**      |        Printing, Text Search, Sharing       |        [Drill-thru, Drill-down, Sub-reports, Nested regions](https://docs.microsoft.com/en-us/sql/reporting-services/report-design/drillthrough-drilldown-subreports-and-nested-data-regions?view=sql-server-ver15)         |
| **Data source**        |      Transactional DB     |            Data warehouse          |
| **Report author**           |        Developer       |        Power User        |
| **Layout**      |        Structured, pre-defined layout       |        Adaptive, flexible         |
| **Recommended tooling**           |        [Document Reporting (RDL)](document-reporting-services.md)/[Configurable Office Documents](general-electronic-reporting.md)       |      [Power BI.com](power-bi-integration.md)/[Analytical Workspaces](embed-power-bi-workspaces.md)     |


## Enhancements in paginated reporting
There are several advantages in using the PDF to interact with the document that is rendered by the Document Reporting service bundled with Finance & Operations apps.  

- **Reports display to 'Screen' faster** - End users benefit from improved performance when displaying reports on the 'Screen', including a reduction in the number of progress bars leading to faster reports.
- **Enhanced service reliability** - The latest BI and Reporting service architecture delivers the power of the Cloud scale to customer environments. Service includes automatic scaling to maximize resource utilization.
- **Higher fidelity with printed output** - Documents are displayed in PDF formats offering consistency with printer output.  
- **Print documents using local devices** - <aintain user identity when sending documents to printers directly from your browser. Use built-in user options displayed in the control toolbar to secure print jobs when printing documents .

For more details on previewing the embedded PDF viewer in environments, see [Preview PDF documents with an embedded viewer](preview-pdf-documents.md).  

### Disabling BI and Analytics on One-Box environments
With the platform updates for 10.0.11 release, developers will have the ability to preview existing solutions by forcing the local Reporting Service to render RDL while the BI and Analytics features are disabled. This viewing mode is referred to as **RDL Sandboxing**. This mode can be enabled or disabled using PowerShell commands.

Use the following steps to enable RDL Sandboxing in your local One-Box environment.

1. Log into your One-Box environment using release 10.0.11 or later.
2. Start the **PowerShell** application and navigate to **C:\AOSService\PackagesLocalDirectory\Plugins\AxReportVmRoleStartupTask***\.
3. Run the command, **UpdateRDLSandboxRule.ps1**.

**Parameters**

-	**ConfigPath:** If SSRS is not deployed in the default location, provide the configuration location.
-	**RemoveRules:** Set this parameter to remove the rules.
-	**ForceUpdate:** Set this parameter to force recreate rules. 
-	**LogDir:** Provide a location to the write log. The default is the location of the UpdateRDLSandboxRule.ps1 command.
