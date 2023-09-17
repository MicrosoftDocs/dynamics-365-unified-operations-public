---
title: Report definitions in financial report designer
description: This article provides information about report definitions.
author: aprilolson
ms.date: 11/22/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: twheeloc
ms.search.region: Global
ms.author: aolson
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611
ms.assetid: 966a3f1d-c59c-4a84-acd4-5bb7e65144c8
ms.search.form: FinancialReports
---

# Report definitions in financial report designer

[!include [banner](../includes/banner.md)]

This article provides information about report definitions. A report definition is a report component (or building block) that uses a row definition, a column definition, and an optional reporting tree definition to create a report. A report definition also provides options and settings that for customizing a report. 

A report definition is a report component (or building block) that uses a row definition, a column definition, and an optional reporting tree definition to create a report. A report definition also provides options and settings that you can use to customize a report. After you define row definitions and column definitions, you must combine them in a report definition. At this point, you also define other aspects of the definitions, such as the detail level and report date. You can then save and generate a report. Financial reporting offers the following levels of detail:

- Financial
- Financial and Account
- Financial, Account, and Transaction

However, depending on how data is stored in the Microsoft Dynamics ERP system, transaction details might not be available in reports.

## Create a report definition
1. In Report designer, on the **File** menu, click **New**, and then select **Report definition**.
2. Specify the appropriate information on the **Report**, **Output and distribution**, **Headers and footers**, and **Settings** tabs.

## Contents of a report definition
The following table describes the tabs in a report definition and how the information is used.

<table>
<thead>
<tr>
<th>Tab</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Report</td>
<td>Create a report, configure a report, or modify an existing report.</td>
</tr>
<tr>
<td>Output and distribution</td>
<td>Change the output type and destination of the report.</td>
</tr>
<tr>
<td>Headers and footers</td>
<td>Define and format the headers and footers for the report. For example, you can add text or images to the header or footer. Financial reporting supports .bmp, .jpg, and .png files for images. You can also add autotext codes to insert other information, such as a company name, report name, or page number.</td>
</tr>
<tr>
<td>Settings</td>
<td>Specify report definition settings, such as the following settings:
<ul>
<li>Formatting and rounding amounts</li>
<li>Format detail reports</li>
<li>Format reporting trees</li>
<li>Generate an exception report</li>
<li>Specify currency conversion</li>
<li>Subtotal and filter account details</li>
</ul>
</td>
</tr>
</tbody>
</table>

## Additional resources

[Financial reporting](financial-reporting-intro.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
