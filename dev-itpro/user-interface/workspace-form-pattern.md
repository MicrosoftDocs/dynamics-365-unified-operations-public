---
# required metadata

title: Workspace form pattern | Microsoft Docs
description: This article discusses the Operational workspace form pattern. Workspaces are a new concept in Microsoft Dynamics AX, and are intended to be the primary way that users navigate to tasks and specific pages. A workspace should be created for every significant business activity that is supported.  
author: jasongre
manager: AnnBe
ms.date: 2016-01-11 18:33:33
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
ms.custom: 29151
ms.assetid: 47c0c87f-62bc-48cf-97dc-af12fe66f690
ms.region: Global
# ms.industry: 
ms.author: jasongre

---

# Workspace form pattern

This article discusses the Operational workspace form pattern. Workspaces are a new concept in Microsoft Dynamics AX, and are intended to be the primary way that users navigate to tasks and specific pages. A workspace should be created for every significant business activity that is supported.  

Usage
-----

Workspaces are a new concept, and are meant to be the primary way that users navigate to tasks and specific pages. A workspace should be created for every significant business “activity” that is supported in Microsoft Dynamics AX. An “activity” is less granular than a task and more granular than a legacy “area page.” A workspace is intended to provide a one-page overview of the activity, and to help users understand the current status, the upcoming workload, and the performance of the process or user. Users should be able to start the most typical tasks for the activity directly from the workspace. If possible, users should also be able to complete tasks directly in the workspace, based on the overview that they just received. Currently, there are two workspace patterns:

-   **Operational workspace** – This is the pattern that should be used for workspace development. Because of the set of components that are permitted in it, this pattern has superior performance. Therefore, we strongly recommend that you use it.
-   (Deprecated) **Workspace** – This pattern is only mentioned for the sake of completeness. Do **not** use this pattern. It will soon be removed from the product.

The rest of this article will describe only details of the Operational workspace pattern, because the original Workspace pattern is deprecated and should not be used.

## Wireframe
[![Workspace(1)](./media/workspace1.png)](./media/workspace1.png)

## Pattern changes for Dynamics AX
The Microsoft Dynamics AX 2012 Role Center has been replaced by multiple activity-focused workspaces in the current version of Dynamics AX.

## Model
### High-level structure

Design

*Action pane (ActionPane) \[Optional\]*

*Workspace page filter group (Group) \[Optional\]* – This must use the [Workspace Page Filter Group](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/workspace-filter-group-subpattern)subpattern.

Panorama (Tab)

Section summary tiles (TabPage) – This must use the [Section Tiles](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/section-tiles-subpattern) subpattern.

Section tabbed list (TabPage) – This must use the [Section Tabbed List](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/section-tabbed-list-subpattern)subpattern.

*Section charts (TabPage) \[Optional\]* – This must use the [Section Stacked Chart](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/section-stacked-chart-subpattern) subpattern.

*Section PowerBI (TabPage) \[Optional\]* – This must use the [Section PowerBI](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/section-powerbi-subpattern) subpattern.

Section related links (TabPage) – This must use the [Section Related Links](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/section-related-links-subpattern) subpattern.

### Core components

-   Apply the Workspace Operational pattern on **Form.Design**.
-   Address BP Warnings:
    -   **Form** must be referenced by at least one menu item.
    -   **TabPage.Caption** isn't empty (for all panorama sections).

### Commonly used subpatterns

-   [Workspace Page Filter Group ](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/workspace-filter-group-subpattern)
-   [Section Tiles](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/section-tiles-subpattern)
-   [Section Tabbed List ](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/section-tabbed-list-subpattern)
-   [Section Stacked Chart](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/section-stacked-chart-subpattern)
-   [Section PowerBI](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/section-powerbi-subpattern)
-   [Section Related Links](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/section-related-links-subpattern)

### Related patterns

-   [Form Part Section List](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/section-list-form-pattern)
-   [Section Chart](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/section-chart-form-pattern)

## UX guidelines
The verification checklist shows the steps for manually verifying that the form complies with UX guidelines. This checklist doesn't include any guidelines that will be enforced automatically through the development environment. Open the form in the browser, and walk through these steps.

-   **Standard form guidelines**
    -   Standard form guidelines have been consolidated into the Dynamics AX [General Form Guidelines](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/general-form-guidelines) document.
-   **Workspace form guidelines**
    -   Use a noun phase for the page title, and avoid general words. The page title should not duplicate the title of an area page.
    -   The page title should begin with the noun that users would have in mind.
    -   All sections must have a title.
    -   A section typically spans the width of two to four standard tiles.
    -   Any section that uses a FormPartControl to display content should have **HeightMode** set to **SizeToAvailable** on the FormPartControl.
-   **Actions**
    -   Include only frequently used commands.
    -   Actions on the Action Pane should be related to the whole workspace (not a specific section of it).
        -   **Exception:** A single "New" action can be put as a tile in the **Summary** section if it's very frequently used.
    -   Group variations of the same command on drop-down menus.
        -   **Examples:** New sales quote, New sales order, New return order
-   **Filters**
    -   Filter fields that are zero to five workspaces wide are allowed.
        -   Only a single field can be put under the page title
        -   The remaining filters must be in a workspace configuration dialog.

## Example
Form: **FMClerkWorkspace** [![Workspace(3)](./media/workspace3.png)](./media/workspace3.png)

## Appendix
### Frequently asked questions

This section will have answers to frequently asked questions that are related to this guideline/pattern.

### Open issues

-   None

### AX 2012 content

#### AX 2012 links

-   [MSDN Role Center Page Reference \[AX2012\]](http://msdn.microsoft.com/en-us/library/cc558235.aspx)
-   [MSDN Role Center User Experience Guidelines \[AX2012\]](http://msdn.microsoft.com/en-us/library/gg886608.aspx)

#### AX 2012 example

[![Workspace(5)](./media/workspace5.png)](./media/workspace5.png)

