---
title: Issue search in Lifecycle Services (LCS)
description: This article provides information about the Issue search tool on Microsoft Dynamics Lifecycle Services (LCS).
author: gianugo
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: gianura
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 160b2882-c70c-44b1-9780-68dc47afb2e8
---

# Issue search in Lifecycle Services (LCS)

[!include [banner](../includes/banner.md)]

This article provides information about the Issue search tool on Microsoft Dynamics Lifecycle Services (LCS). It explains how to search for product issues and regulatory features, and describes the information that is provided for each status.

## Prerequisites

None

## Search for product issues and regulatory features
You can use Issue search to search for product issues, and determine whether an issue has been resolved, is open, or has a workaround. You can also search for regulatory features, and determine whether a feature is available or is planned in a future release. Finally, you can find regulatory white papers, certifications, and registrations.

1.  [Go to Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com).
2.  Select a project to work in.
3.  Click the **Issue search** tile.
4.  Enter search terms. You can enter a keyword or group of keywords, or a Microsoft Knowledge Base (KB) number. You can also use a dollar sign ($) to indicate an Application Object Tree (AOT) object path in the format $\\*ObjectType\\Object* or $\\*ObjectType\\Object*\#*Method* (for example, **$\\Classes\\Tax\#Save**). Standard search operators such as **AND** and **OR** are supported.

You can filter the results list for resolved or open issues, workarounds, and issues that won't be fixed or are postponed. You can also filter by the application version. By default, the results are sorted by relevance. However, you can sort by date ascending, date descending, version ascending, or version descending instead. By default, all status and product version filters are selected. **Note:** Results for Microsoft Dynamics AX 2009 are included in Microsoft Dynamics AX 2012 projects only when you search for regulatory features. The following table describes the information that is provided for each status when you search by product issue.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Status</th>
<th>Color</th>
<th>Description of results</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Resolved</td>
<td>Green</td>
<td>The KB number, title, version, description of the problem and change, and hotfix are provided. A list of objects that are affected by the hotfix is also provided whenever possible.
<ul>
<li>To download the hotfix, click <strong>Download hotfix</strong>.</li>
<li>To determine what code was changed in a hotfix, click <strong>View changes</strong>. Added code is indicated by a green highlight, and deleted code is indicated by a red highlight. <strong>Important:</strong> The list of code changes is provided for reference only. Code changes should not be manually inserted into a higher development layer. Otherwise, they become unsupported customized objects that the partner or customer assumes full responsibility for.</li>
</ul></td>
</tr>
<tr class="even">
<td>Open</td>
<td>Red</td>
<td>A bug number, title, version, and description of the problem are provided.</td>
</tr>
<tr class="odd">
<td>Workarounds</td>
<td>Brown</td>
<td>The issue number, title, version, problem description, and mitigation are provided.</td>
</tr>
<tr class="even">
<td>Postponed</td>
<td>Gray</td>
<td>A bug number, title, version, and description of the problem are provided. If a workaround is available, it&#39;s described. A bug that has this status has been evaluated and won&#39;t be fixed at this time.</td>
</tr>
<tr class="odd">
<td>By design</td>
<td>Gray</td>
<td>A bug number, title, version, and description of the problem are provided. An explanation of the design is provided whenever possible. A bug that has this status has been evaluated, and it has been determined that this functionality is working as designed.</td>
</tr>
<tr class="even">
<td>Not reproducible</td>
<td>Gray</td>
<td>A bug number, title, version, and description of the problem are provided. An explanation of the problem is provided whenever possible. A bug that has this status has been evaluated, and a fix won&#39;t be issued at this time.</td>
</tr>
<tr class="odd">
<td>Will not be fixed</td>
<td>Gray</td>
<td>A bug number, title, version, and description of the problem are provided. If a workaround is available, it&#39;s described. A bug that has this status has been evaluated and won&#39;t be fixed.</td>
</tr>
</tbody>
</table>

The following table describes the information that is provided for each status when you search by regulatory feature.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Status</th>
<th>Color</th>
<th>Description of results</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Resolved</td>
<td>Green</td>
<td>For feature updates: The KB number, title, version, description of the problem, and hotfix are provided. A list of objects that are affected by the hotfix is also provided whenever possible.
<ul>
<li>To download the hotfix, click <strong>Download hotfix</strong>.</li>
<li>To read the KB article for the hotfix, click <strong>Read KB article</strong>.</li>
</ul>
For white papers, certifications, registrations, and reports: The title, product version, and description of the white paper, certification, registration, or report are provided.
<ul>
<li>To read the documentation, click <strong>Read documentation</strong>.</li>
</ul></td>
</tr>
<tr class="even">
<td>Open</td>
<td>Red</td>
<td>A bug number, title, version, planned release date, and description of the problem are provided.</td>
</tr>
</tbody>
</table>

## Issue details
The code changes are provided for reference only and should not be manually inserted into a higher development layer. Otherwise, they become unsupported customized objects that the partner or customer assumes full responsibility for.





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
