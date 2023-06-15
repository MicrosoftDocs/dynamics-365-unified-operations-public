---
title: Default reporting experiences in IaaS environments
description: This article provides information about paginated reporting in finance and operations apps.
author: RichdiMSFT
ms.date: 05/13/2020
ms.topic: article
ms.prod: 
ms.technology: 
audience: IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: richdi
ms.search.validFrom: 
ms.dyn365.ops.version: 
ms.assetid: 
ms.search.form: 
---

# Document Reporting Service in Dynamics 365 applications

[!include [banner](../includes/banner.md)]

## Reporting scenarios in ERP

The Document Reporting Service bundled with finance and operations apps provide user tooling to facilitate two basic user functions, or generic scenarios, in enterprise resource planning (ERP): **document generation** and **business intelligence (BI) and analytics**. These generic scenarios represent the two most frequently used methods for accessing business data.

- **Document generation** – The production of structured documents, where the primary purpose are often printing and bulk email distribution.
- **BI and analytics** – Interactive visualizations that are based on aggregations, and that contain embedded links to referenced data. Users rely on these visualizations to identify patterns and trends in large amounts of data.

Although the Document Reporting Service continues to be the ideal tool for bulk production of business documents, they lack the extensibility options that power users require so that they can adapt analytical views and account for frequent changes in the business environment. At the same time, the [Microsoft Power BI service](/power-bi/fundamentals/power-bi-overview) is recognized as an industry leader in the delivery of powerful analytics for businesses of all sizes. Integration options for finance and operations apps and the Power BI service are available to accommodate seamless exploration of customer business data.

> [!NOTE]
> When the platform updates for version 10.0.12 are released, the Dynamics 365 service will discontinue support for the Report Viewer control that is used to facilitate BI and analytics interactions with paginated reports. Instead, reports that the Document Reporting service renders on the screen will use the embedded PDF viewer. For more information about the embedded PDF viewer, see [Preview PDF documents with an embedded viewer](preview-pdf-documents.md).

### Comparison of report scenarios

In document generation scenarios, a simple business activity, either automated or manual, can trigger the production of between one and hundreds of documents. These documents are often decorated with graphics that include commercial branding. The documents are distributed to both internal and external recipients by using predefined delivery routing instructions.

The following table compares the fundamentals of the two reporting experiences.

| Item                     | Document generation | BI and analytics |
|--------------------------|---------|------------------|
| **Display format**       | PDF and Office documents | HTML |
| **Data volume**          | One to hundreds of rows | Tens of thousands of rows or more |
| **Interactive features** | Printing, text search, and sharing | [Drill-through, drill-down, and nested regions](/sql/reporting-services/report-design/drillthrough-drilldown-subreports-and-nested-data-regions) |
| **Data source**          | Transactional database | Data warehouse |
| **Report author**        | Developer | Power user |
| **Layout**               | Structured, predefined layout | Adaptive, flexible layout |
| **Recommended tooling**  | [Document Reporting Service](document-reporting-services.md)/[configurable Office documents](general-electronic-reporting.md) | [Power BI.com](power-bi-integration.md)/[analytical workspaces](embed-power-bi-workspaces.md) |

## Enhancements in paginated reporting

There are several advantages to using PDFs to interact with documents that are rendered by the Document Reporting Service that is bundled with finance and operations apps:

- **Reports are shown on the screen more quickly.** Users benefit from improved performance when reports are shown on the screen. This performance improvement includes a reduction in the number of progress bars, so that reports are faster.
- **Service reliability is enhanced.** The latest Document Reporting Service architecture delivers the power of the cloud scale to customer environments. The service includes automatic scaling to help maximize resource utilization.
- **Printed output has higher fidelity.** Documents are shown in PDF formats to provide consistency with printer output.
- **Documents can be printed by using local devices.** You can maintain user identity when you send documents directly from your browser to a printer. You can use the built-in user options on the control toolbar to help secure print jobs when you print documents.

For more information about how to preview the embedded PDF viewer in environments, see [Preview PDF documents with an embedded viewer](preview-pdf-documents.md).

### Turn off BI and analytics in one-box environments

In the platform updates for version 10.0.11, developers can preview existing solutions by forcing the local Document Reporting Service to render RDL while the BI and analytics features are turned off. This viewing mode is referred to as **RDL sandboxing**. It can be turned on or off by using Windows PowerShell commands.

Follow these steps to turn on RDL sandboxing in your local one-box environment.

1. Sign in to your one-box environment that uses version 10.0.11 or later.
2. Open Windows PowerShell, and go to C:\AOSService\PackagesLocalDirectory\Plugins\AxReportVmRoleStartupTask\.
3. Run the **UpdateRDLSandboxRule.ps1** command. Here is a list of the parameters:

    - **ConfigPath** – If SQL Server Reporting Services (SSRS) isn't deployed in the default location, specify the configuration location.
    - **RemoveRules** – Set this parameter to remove the rules.
    - **ForceUpdate** – Set this parameter to force the rules to be re-created.
    - **LogDir** – Specify a location to write the log to. The default location is the location of the **UpdateRDLSandboxRule.ps1** command.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
