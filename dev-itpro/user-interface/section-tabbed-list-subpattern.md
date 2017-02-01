---
# required metadata

title: Section Tabbed List subpattern | Microsoft Docs
description: This article provides information about the Section Tabbed List subpattern. This subpattern is used as part of the Operational Workspace pattern, specifically for a panorama section that contains a set of vertical tabs, each of which contains a filtered list of data.
author: jasongre
manager: AnnBe
ms.date: 2016-01-11 22:21:22
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
ms.custom: 29291
ms.assetid: 61d22a2d-a0cc-4fc6-b2dd-5b36ebcc9e33
ms.region: Global
# ms.industry: 
ms.author: jasongre

---

# Section Tabbed List subpattern

This article provides information about the Section Tabbed List subpattern. This subpattern is used as part of the Operational Workspace pattern, specifically for a panorama section that contains a set of vertical tabs, each of which contains a filtered list of data.

Usage
-----

The Section Tabbed List subpattern is used as part of the Operational Workspace pattern, specifically for a panorama section that contains a set of vertical tabs, each of which contains a filtered list of data.

## Wireframe
[![sectionTabbedListWireframe](./media/sectiontabbedlistwireframe.png)](./media/sectiontabbedlistwireframe.png)

## Pattern changes for Microsoft Dynamics AX
This pattern didn't exist for Microsoft Dynamics AX 2012.

## Model
### High-level structure

TabPage TabbedList (Tab) (Style=VerticalTabs)

*TabbedListPage (TabPage) \[0..N\]*

TargetForm (FormPart)

Each Form Part points to a form that contains the content for the section. Each of these forms should use one of the Form Part Section List form patterns.

### Core components

Apply Section Tabbed List to the appropriate tab page in the workspace.

### Related container patterns

-   [Operational Workspace](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/workspace-form-pattern)
-   [Form Part Section List](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/section-list-form-pattern)

## UX guidelines
The verification checklist shows the steps for manually verifying that the form complies with UX guidelines. This checklist doesn't include any guidelines that will be enforced automatically through the development environment. Open the form in the browser, and walk through these steps.

-   At least one list should be present in the tabbed list section.
-   Each Form Part Control should point to a form that uses one of the [Form Part Section List](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/section-list-form-pattern) patterns.

## Examples
Form: **PurchOrderMaintainWorkspace** (**All workspaces** &gt; **Purchase order preparation**) [![tabbedListSectionExample](./media/tabbedlistsectionexample.png)](./media/tabbedlistsectionexample.png)

## Appendix
### Frequently asked questions

This section will have answers to frequently asked questions that are related to this guideline/pattern.

### Open issues

None

