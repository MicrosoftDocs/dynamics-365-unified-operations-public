---
title: Financial reporting
description: Financial reporting allows financial and business professionals to create, maintain, deploy, and view financial statements.
author: aprilolson
ms.date: 12/01/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: twheeloc
ms.search.region: Global
ms.author: aolson
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611
ms.collection: get-started
ms.assetid: fe8b27e7-a40a-4689-ac6a-7f7401c387f5
ms.search.form: FinanicalReportingSetup
---

# Financial reporting

[!include [banner](../includes/banner.md)]

Financial reporting for the application allows financial and business professionals to create, maintain, deploy, and view financial statements. It moves beyond traditional reporting constraints to help you efficiently design various types of reports.

Financial reporting includes dimension support. Therefore, account segments or dimensions are immediately available. No additional tools or configuration steps are required.

## Financial reporting setup
The **Financial reporting setup** page has a list of all financial dimensions in the system. **General ledger** \> **Ledger setup** \> **Financial reporting setup**.

The **Financial reporting setup** page has two sections that determine the data you report on in Financial reporting:

- **Dimensions tab** - Because different companies use different dimensions and account structures, there is no way to determine the order in which users want to view all financial dimensions on reports. This page allows you set the order in which you want financial dimensions to appear when you build and view a report in Financial reporting.
- **Attributes tab** is where you can select whether you want the ability to use **Vendors** and **Customers** as attributes for filtering and report design. Reporting on Vendor and Customer will only be valuable if you do not enter multiple vendors or customers in a single voucher when posting transactions. Choosing Vendor and/or Customer will add additional time to the integration.

## Financial reporting components
The following components of financial reporting make it easy to create, view, and schedule reports.

| Component        | Functions | Additional information |
|------------------|-----------|------------------------|
| Report Designer  | Create report building blocks that can be combined to define and generate a report. The report wizard guides less experienced users through the design process. Advanced users can create new report building blocks or modify existing building blocks to meet their requirements. | |
| Report schedules | Schedule a single report or a group of reports so that it is generated on a regular basis. | [Generate financial reports](generate-financial-report.md) |

## Features
<table>
<thead>
<tr>
<th>Feature</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Report design flexibility</td>
<td>Report Designer provides the following reporting options when you design a report:
<ul>
<li>Save dimension combinations, and reuse the dimensions for multiple reports.</li>
<li>Control how dimension descriptions are formatted and displayed.</li>
<li>Identify accounts or dimensions that have been omitted from report building blocks.</li>
<li>Format headers for rolling forecasts.</li>
</ul>
</td>
</tr>
<tr>
<td>Financial report collaboration</td>
<td>The following features help you manage the generation and distribution of reports:
<ul>
<li>Schedule reports so that they are automatically generated on a daily, weekly, monthly, or annual basis.</li>
<li>Export to the read-only XPS format, which provides better document security through digital signatures.</li>
<li>Export to a Microsoft Excel worksheet.</li>
<li>To share reports, you can create email messages that contain links to the reports.</li>
</ul>
</td>
</tr>
<tr>
<td>Interactive report viewing</td>
<td>Interactive features let you perform the following tasks:
<ul>
<li>Change the report date for the report that you're viewing.</li>
<li>Change the currency of the report that you're viewing.</li>
<li>View the report in either a summary view or a detailed view.</li>
<li>Add dimension filters to limit the report content to a specific dimension or combination of dimensions.</li>
<li>Add attribute filters to limit the report content to a specific attribute or combination of attributes.</li>
</ul>
</td>
</tr>
</tbody>
</table>

## Additional resources
[Generate financial reports](generate-financial-report.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
