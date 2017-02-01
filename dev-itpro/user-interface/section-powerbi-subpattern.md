---
# required metadata

title: Section Power BI subpattern | Microsoft Docs
description: This article provides information about the Section PowerBI subpattern. This subpattern is used as part of the Operational Workspace pattern, specifically for the panorama section that contains a PowerBI control.
author: jasongre
manager: AnnBe
ms.date: 2016-01-12 22:30:41
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: annbe
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 29431
ms.assetid: 81dbe415-5f87-43be-b760-32c9745b8512
ms.region: Global
# ms.industry: 
ms.author: jasongre

---

# Section Power BI subpattern

This article provides information about the Section PowerBI subpattern. This subpattern is used as part of the Operational Workspace pattern, specifically for the panorama section that contains a PowerBI control.

Usage
-----

The Section PowerBI subpattern is used as part of the Operational Workspace pattern, specifically for the panorama section that contains the PowerBI control.

## Wireframe
[![sectionPowerBIWireframe](./media/sectionpowerbiwireframe.png)](./media/sectionpowerbiwireframe.png)

## Pattern changes for Microsoft Dynamics AX
This pattern didn't exist for Microsoft Dynamics AX 2012.

## Model
### High-level structure

TabPage PowerBI (PowerBI)

### Core components

Apply Section PowerBI to the appropriate tab page in the workspace.

### Related container patterns

-   [Operational workspace](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/workspace-form-pattern)

## UX guidelines
None

## Examples
Form: **FmClerkWorkspace** (**All workspaces** &gt; **Reservation Management**) PowerBI must be configured before the form can appear. (For information about how to configure PowerBI, see the Appendix.)

## Appendix
### Related articles

-   [Configuring PowerBI integration for workspaces](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/analytics-bi-reporting/configuring-powerbi-integration)
-   [Power BI Integration in Dynamics AX](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/analytics-bi-reporting/powerbi-integration-in-ax7)

### Frequently asked questions

This section will have answers to frequently asked questions that are related to this guideline/pattern.

-   **How do I configure PowerBI for integration with my workspace?**
    -   See the [Configuring PowerBI integration for workspaces](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/analytics-bi-reporting/configuring-powerbi-integration) article.

### Open issues

None

