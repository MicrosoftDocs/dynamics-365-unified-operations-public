---
title: Issue search in Lifecycle Services
description: Learn about the Issue search tool on Microsoft Dynamics Lifecycle Services, including a table that outlines the description results and colors for various statuses.
author: johnmichalak
ms.author: johnmichalak
ms.topic: how-to
ms.date: 11/11/2025
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 160b2882-c70c-44b1-9780-68dc47afb2e8
---

# Issue search in Lifecycle Services

[!include [banner](../includes/banner.md)]

This article provides information about the Issue search tool on Microsoft Dynamics Lifecycle Services. It explains how to search for product issues and regulatory features, and describes the information that is provided for each status.

## Prerequisites

None

## Search for product issues and regulatory features
You can use Issue search to search for product issues, and determine whether an issue has been resolved, is open, or has a workaround. You can also search for regulatory features, and determine whether a feature is available or is planned in a future release. Finally, you can find regulatory white papers, certifications, and registrations.

1.  [Go to Microsoft Dynamics Lifecycle Services](https://lcs.dynamics.com).
2.  Select a project to work in.
3.  Select the **Issue search** tile.
4.  Enter search terms. You can enter a keyword or group of keywords, or a Microsoft Knowledge Base (KB) number. You can also use a dollar sign ($) to indicate an Application Object Tree (AOT) object path in the format $\\*ObjectType\\Object* or $\\*ObjectType\\Object*\#*Method* (for example, **$\\Classes\\Tax\#Save**). Standard search operators such as **AND** and **OR** are supported.

You can filter the results list for resolved or open issues, workarounds, and issues that won't be fixed or are postponed. You can also filter by the application version. By default, the results are sorted by relevance. However, you can sort by date ascending, date descending, version ascending, or version descending instead. By default, all status and product version filters are selected. **Note:** Results for Microsoft Dynamics AX 2009 are included in Microsoft Dynamics AX 2012 projects only when you search for regulatory features. The following table describes the information that is provided for each status when you search by product issue.

| Status | Color | Description of results |
|--------|-------|------------------------|
| Resolved | Green | The KB number, title, version, description of the problem and change, and hotfix are provided. A list of objects that are affected by the hotfix is also provided whenever possible.<ul><li>To download the hotfix, select **Download hotfix**.</li><li>To determine what code was changed in a hotfix, select **View changes**. Added code is indicated by a green highlight, and deleted code is indicated by a red highlight. **Important:** The list of code changes is provided for reference only. Code changes shouldn't be manually inserted into a higher development layer. Otherwise, they become unsupported customized objects that the partner or customer assumes full responsibility for.</li></ul> |
| Open | Red | A bug number, title, version, and description of the problem are provided. |
| Workarounds | Brown | The issue number, title, version, problem description, and mitigation are provided. |
| Postponed | Gray | A bug number, title, version, and description of the problem are provided. If a workaround is available, it's described. A bug that has this status has been evaluated and won't be fixed at this time. |
| By design | Gray | A bug number, title, version, and description of the problem are provided. An explanation of the design is provided whenever possible. A bug that has this status has been evaluated, and it has been determined that this functionality is working as designed. |
| Not reproducible | Gray | A bug number, title, version, and description of the problem are provided. An explanation of the problem is provided whenever possible. A bug that has this status has been evaluated, and a fix won't be issued at this time. |
| Won't be fixed | Gray | A bug number, title, version, and description of the problem are provided. If a workaround is available, it's described. A bug that has this status has been evaluated and won't be fixed. |

The following table describes the information that is provided for each status when you search by regulatory feature.

| Status | Color | Description of results |
|--------|-------|------------------------|
| Resolved | Green | For feature updates: The KB number, title, version, description of the problem, and hotfix are provided. A list of objects that are affected by the hotfix is also provided whenever possible.<ul><li>To download the hotfix, select **Download hotfix**.</li><li>To read the KB article for the hotfix, select **Read KB article**.</li></ul>For white papers, certifications, registrations, and reports: The title, product version, and description of the white paper, certification, registration, or report are provided.<ul><li>To read the documentation, select **Read documentation**.</li></ul> |
| Open | Red | A bug number, title, version, planned release date, and description of the problem are provided. |

## Issue details
The code changes are provided for reference only and shouldn't be manually inserted into a higher development layer. Otherwise, they become unsupported customized objects that the partner or customer assumes full responsibility for.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
