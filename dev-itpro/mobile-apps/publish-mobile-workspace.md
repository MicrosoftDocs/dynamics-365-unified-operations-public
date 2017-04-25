---
# required metadata

title: Publish a mobile workspace
description: This topic describes the steps that system administrators can follow to publish a mobile workspace. You must publish a mobile workspace before users can access it in the Dynamics 365 for Operations mobile app. 
author: sericks007
manager: AnnBe
ms.date: 04/21/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: Operations, Platform
# ms.tgt_pltfrm: 
ms.custom: 272873
ms.assetid: e9a3028b-3559-4314-afcc-ea0319cdd154
ms.search.region: Global
# ms.search.industry: 
ms.author: sericks
ms.dyn365.ops.intro: Platform update 4
ms.search.validFrom: 2017-02-28

---

# Publish a mobile workspace

[!include[banner](../includes/banner.md)]

"[!include[banner](../includes/banner.md)]"


This topic describes the steps that system administrators can follow to publish a mobile workspace. You must publish a mobile workspace before users can access it in the Dynamics 365 for Operations mobile app. 

Prerequisites
-------------

Before you publish a mobile workspace, make sure that the following prerequisites are in place.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Prerequisite</th>
<th>Role</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Microsoft Dynamics 365 for Operations version 1611 with platform update 3 or later must be implemented.</td>
<td>System administrator</td>
<td>If you don't already have Dynamics 365 for Operations deployed in your organization, your system administrator should see <a href="https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/deployment/deploy-demo-environment">Deploy a Microsoft Dynamics 365 for Operations demo environment</a>.</td>
</tr>
<tr class="even">
<td>KBs that contain the mobile workspaces that are provided by Microsoft must be implemented.</td>
<td>System administrator</td>
<td>You must implement the KBs (hotfixes) that contain the mobile workspaces that are provided by Microsoft. To implement the KBs, see the "Prerequisites" section of the topic about the mobile workspace that your organization wants to use:
<ul>
<li><a href="https://docs.microsoft.com/en-us/dynamics365/operations/financials/cost-accounting/cost-controlling-mobile-workspace">Cost controlling mobile workspaces</a></li>
<li><a href="https://docs.microsoft.com/en-us/dynamics365/operations/scm/production-control/inventory-on-hand-mobile-workspace">Inventory on-hand mobile workspace</a></li>
<li><a href="https://docs.microsoft.com/en-us/dynamics365/operations/scm/production-control/sales-orders-mobile-workspace">Sales orders mobile workspaces</a></li>
<li><a href="https://docs.microsoft.com/en-us/dynamics365/operations/scm/procurement/vendor-collaboration-mobile-workspace">Vendor collaboration mobile workspace</a></li>
<li><a href="https://docs.microsoft.com/en-us/dynamics365/operations/project-management/project-time-entry-mobile-workspace">Project time entry mobile workspace</a></li>
<li><a href="https://docs.microsoft.com/en-us/dynamics365/operations/financials/expense-management/expense-management-mobile-workspace">Expense management mobile workspace</a></li>
</ul></td>
</tr>
<tr class="odd">
<td>Deployable packages that contain custom mobile workspaces must be applied to the Dynamics 365 for Operations system.</td>
<td>System administrator</td>
<td>If you want to use custom mobile workspaces that an independent software vendor (ISV) created, you must apply the deployable package to your Dynamics 365 for Operations system. For instructions, see <a href="https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/deployment/apply-deployable-package-system">Apply a deployable package on a Microsoft Dynamics 365 for Operations system</a>.</td>
</tr>
</tbody>
</table>

## Publish a mobile workspace to the Dynamics 365 for Operations mobile app
1.  Start Dynamics 365 for Operations in your browser.
2.  On the **System parameters** page, on the **Manage mobile workspaces** tab, select the workspace to publish.
3.  Click **Publish mobile workspace**.

After a new workspace is published, users will have to pull to refresh the list of mobile workspaces. 

[![Pull to refresh](./media/pull-to-refresh-list-of-workspaces-183x300.png)](./media/pull-to-refresh-list-of-workspaces.png)



