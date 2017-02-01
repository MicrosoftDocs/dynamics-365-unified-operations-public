---
# required metadata

title: Section Stacked Chart subpattern | Microsoft Docs
description: This article provides information about the Section Stacked Chart subpattern. This subpattern is used as part of the Operational Workspace pattern when a panorama section contains one or two charts.  
author: jasongre
manager: AnnBe
ms.date: 2016-01-11 22:15:55
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
ms.custom: 29251
ms.assetid: b7937069-e4f1-4d98-b373-711889a0a5b9
ms.region: Global
# ms.industry: 
ms.author: jasongre

---

# Section Stacked Chart subpattern

This article provides information about the Section Stacked Chart subpattern. This subpattern is used as part of the Operational Workspace pattern when a panorama section contains one or two charts.  

Usage
-----

The Section Stacked Chart subpattern is used as part of the Operational Workspace pattern, specifically for a panorama section that contains one or two charts.

## Wireframe
[![sectionStackedChartWireframe](./media/sectionstackedchartwireframe.png)](./media/sectionstackedchartwireframe.png)

## Pattern changes for Microsoft Dynamics AX
This pattern didn't exist for Microsoft Dynamics AX 2012.

## Model
### High-level structure

TabPage

*ChartPart (FormPart) \[0..N\]*

Each Form Part points to a form that contains a single chart. Each of these forms should use the [Section Chart](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/section-chart-form-pattern) form pattern.

### Core components

Apply Section Stacked Chart to the appropriate tab page in the workspace.

### Related container patterns

-   [Operational workspace](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/workspace-form-pattern)
-   [Section Chart](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/section-chart-form-pattern)

## UX guidelines
The verification checklist shows the steps for manually verifying that the form complies with UX guidelines. This checklist doesn't include any guidelines that will be enforced automatically through the development environment. Open the form in the browser, and walk through these steps.

-   There should be no more than two charts in this section.
-   Each Form Part Control should point to a form that uses the [Section Chart](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/section-chart-form-pattern) pattern.

## Examples
Form: **FmClerkWorkspace** (**All workspaces** &gt; **Reservation Management**) [![sectionStackedChartExample](./media/sectionstackedchartexample.png)](./media/sectionstackedchartexample.png)

## Appendix
### Frequently asked questions

This section will have answers to frequently asked questions that are related to this guideline/pattern.

### Open issues

None

