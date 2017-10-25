---
# required metadata

title: Document Reporting Services overview
description: This article describes the integrated reporting solution that is available in Microsoft Dynamics 365 for Finance and Operations. This solution simplifies service administration, increases developer productivity, and provides an enhanced report viewing experience for users.
author: TJVass
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 69191
ms.assetid: 57aaba22-4068-4c3f-9428-7fcd99632295
ms.search.region: Global
# ms.search.industry: 
ms.author: tjvass
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Document Reporting Services overview

[!include[banner](../includes/banner.md)]


This article describes the integrated reporting solution that is available in Microsoft Dynamics 365 for Finance and Operations. This solution simplifies service administration, increases developer productivity, and provides an enhanced report viewing experience for users.

Document Reporting Services
---------------------------

Document Reporting Services are based on Microsoft SQL Server Reporting Services (SSRS). In the current version of Microsoft Dynamics 365 for Finance and Operations, these services are hosted in the Microsoft Azure compute service. If you're developing in a one-box environment, the services also run locally in the Azure compute emulator.

### Service deployment – Local vs. cloud

In a one-box environment, developers can create, modify, and preview reports, from end to end, by using Microsoft Visual Studio 2015. A separate process isn't required in order to add reports to the application's metadata store. Changes to reports are packaged together with other solution updates and then deployed to the cloud after development is completed in the local environment. 

[![document-reporting-services-topology](./media/document-reporting-services-topology.png)](./media/document-reporting-services-topology.png)

### Viewing reports in Dynamics 365 for Finance and Operations

The enhanced report viewing experience that Finance and Operations provides for end users is the same as the report preview experience in Microsoft Visual Studio. You no longer use a separate design preview in Visual Studio. Instead, just press Ctrl+F5 to build and preview the report in an Internet Explorer window. The report appears exactly as it would appear in the client. Even the user's parameter experience is the same. The following screen shot shows an example of a report preview that is opened from Visual Studio. 

[![Example of a report preview](./media/2_report.png)](./media/2_report.png)

## Service administration prerequisites
The following table compares the service administration prerequisites for Microsoft Dynamics AX 2012 and the current version of Finance and Operations.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>AX 2012</th>
<th>The current version of Dynamics 365 for Finance and Operations</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>A report development environment has the following prerequisites:
<ul>
<li>SSRS must be installed.</li>
<li>SSRS must be configured by using Reporting Services Configuration Manager.</li>
<li>SSRS extensions for Finance and Operations must be installed.</li>
</ul></td>
<td>Reporting services run in the Azure compute emulator, together with the application server. Therefore, there are no SSRS service administration prerequisites. After reports have been deployed to the local reporting services, they can be accessed from the client.</td>
</tr>
</tbody>
</table>

## Developing application reports
The process for developing a report in the current version of Finance and Operations is easier than it is in AX 2012, because you can create and validate a reporting solution entirely in Visual Studio 2015. The following table describes how Finance and Operations simplifies the basic procedure for adding an automatic design report that is based on a query.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>AX 2012</th>
<th>The current version of Dynamics 365 for Finance and Operations</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol>
<li>In the Microsoft Dynamics 365 for Finance and Operations client, create a query in the Application Object Tree (AOT).</li>
<li>In Visual Studio, create a reporting project, and add the query to it.</li>
<li>Edit the report in the Visual Studio model editor.</li>
<li>Preview the report design in Visual Studio by using the model editor toolbar.</li>
<li>Use Visual Studio to add the report to the AOT.</li>
<li>Use the AOT in the client to create a menu item for the report, and add the menu item to a menu.</li>
<li>Use the AOT to deploy the report to the report server.</li>
<li>Verify the report in the client.</li>
</ol></td>
<td><ol>
<li>In Visual Studio, create a reporting project and the query.</li>
<li>Edit the report in Visual Studio.</li>
<li>In Visual Studio, add the report to a menu item, and set the menu item as a startup object.</li>
<li>Use the AOT to deploy the report to the report server.</li>
<li>Press Ctrl+F5 to verify the report in the Finance and Operations client. <strong>Note:</strong> There is no longer a separate preview of the report design from the model editor.</li>
<li>When the whole solution is completed, deploy it to the cloud in one package.</li>
</ol></td>
</tr>
</tbody>
</table>





