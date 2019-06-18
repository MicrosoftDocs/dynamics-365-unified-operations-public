---
# required metadata

title: Select Analytical Workspace from PowerBI.com 
description: This topic explains how to select a report hosted on PowerBI.com for an application workspace.
author: tjvass
manager: AnnBe
ms.date: 07/18/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:
# ROBOTS:
audience: IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: Global
# ms.search.industry:
ms.author: tjvass
ms.search.validFrom: 2019-07-18 
ms.dyn365.ops.version: Platform update 27
---

# Select Analytical Workspace from PowerBI.com

[!include[banner](../includes/banner.md)]

## Analytical Workspaces
Analytical Workspaces are bundled with the Application Suite and offer user insights into their data based on standard business operations.  However, there will be cases where it makes sense to replace the standard reports with custom solutions available for users within your organization.  

With the latest Platform update, power users are able to replace the standard embedded solutions with reports hosted on PowerBI.com.  PowerBI.com provides world-class tooling for producing analytical solutions containing mash-up views with data from external sources.  

**Important** - this is not an exercise of personalization.  Changes made here are scoped to the active Legal Entity and apply to all users of the system.


### Motivations for embedding PowerBI.com report
Although, the standard solutions deliver insights tailored for a given business persona, there will be cases where an organization prefers a custom solution.  Dynamics 365 for Finance & Operations allows a Power User to promote custom solutions hosted on PowerBI.com which are shared with members of the organization.  

Here are a few of the top motivations for selecting reports hosted on PowerBI.com
- PowerBI.com reports support data-mashups with external data sources and are accessible outside of Dynamics 365 Finances & Operations
- Appropriate for demonstrating custom solutions hosted on PowerBI.com embedded in the application on 1Box deployment 
- Organizations with Power BI Premium services that wish to augment the standard solutions

### Embedding a PowerBI.com report into an Analytical Workspace
To replace the standard application solutions you must be a member of the System Report Editors security group.  Members of this security group have access to Options in the Application Workspaces that allow them to customize the standard solution.  In this example, we will replace the standard Analytical Workspace with a customer report hosted on PowerBI.com

**Step #1 -** Log into Dynamics 365 for Finance and Operations, and then access the Application Workspace you'll be customizing.  Here, we'll replace the standard analytical report embedded in the **Compensation management** Workspace.

