---
# required metadata

title: Removed or deprecated features in Lifecycle Services (LCS)
description: This topic describes features that have been removed, or that are planned for removal from Microsoft Dynamics Lifecycle Services (LCS).
author: AngelMarshall
manager: AnnBe
ms.date: 02/05/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: tsmarsha
ms.search.validFrom: 2019-08-31
ms.dyn365.ops.version: 10.0.5
---

# Removed or deprecated features in Lifecycle Services (LCS)

[!include[banner](../includes/banner.md)]

This topic describes features that have been removed or deprecated for Microsoft Dynamics Lifecycle Services (LCS).

- A *removed* feature is no longer available in the service.
- A *deprecated* feature isn't in active development and might be removed in a future update.

This list is provided so that you can consider these removals and deprecations as you do your own planning.

## October 2019 announcements

### Flowchart diagrams in Business process modeler

<table>
<tbody>
<tr>
<td><strong>Reason for deprecation/removal</strong></td>
<td>We are deprecating the flowchart diagrams component in Business process modeler (BPM), because the legacy design caused low usage.</td>
</tr>
<tr>
<td><strong>Replaced by another feature?</strong></td>
<td>No</td>
</tr>
<tr>
<td><strong>Areas affected</strong></td>
<td>Business process modeler</td>
</tr>
<tr>
<td><strong>Status</strong></td>
<td>Deprecated: The flowchart diagrams component in BPM is expected to be removed in 2020. The following functionality will be removed:
<ul>
<li>Existing flowcharts will be unavailable for viewing or editing. The shape properties that are associated with flowchart activities will also be unavailable, because the whole <strong>Flowchart</strong> tab will be removed. These flowcharts include both the default flowcharts that are automatically generated and customized flowcharts that are modified based on those default flowcharts.</li>
<li>The legacy fit/gap analysis feature will be unavailable. Therefore, no gap list will be automatically created or available for export.
<p><strong>Note:</strong> This feature had previously been deprecated and replaced by Microsoft Azure DevOps integrations.</p>
</li>
<li>The version history of the flowchart will be unavailable.</li>
</ul>
</td>
</tr>
</tbody>
</table>
