---
# required metadata

title: Workspace form pattern
description: This topic discusses workspace form patterns. Workspaces are the primary way that users navigate to tasks and specific pages.
author: jasongre
ms.date: 05/23/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: tfehr
# ms.tgt_pltfrm: 
ms.custom: 29151
ms.assetid: 4ca77c08-1c8f-4b0c-af55-ca89a7e8982b
ms.search.region: Global
# ms.search.industry: 
ms.author: jasongre
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Workspace form pattern

[!include [banner](../includes/banner.md)]

This topic discusses workspace form patterns. Workspaces are the primary way that users navigate to tasks and specific pages. A workspace should be created for every significant business activity that is supported.  

## Usage

Workspaces are meant to be the primary way that users navigate to tasks and specific pages. A workspace should be created for every significant business “activity” that you want to support. An “activity” is less granular than a task and more granular than a legacy “area page.” A workspace is intended to provide a one-page overview of the activity and to help users understand the current status, upcoming workload, and performance of the process or user. Users should be able to start the most typical tasks for the activity directly from the workspace. If possible, users should also be able to complete tasks directly in the workspace based on the overview surfaced on the page. Currently, there are three workspace patterns:

-   **Operational workspace**: This is the standard pattern currently used for workspace development. Because of the set of components permitted by it, this pattern has superior performance over the deprecated "workspace" pattern. For this reason and to ensure visual and behavioral consistency with the other workspaces in the system, we recommend that you use this pattern. Starting in 10.0.25, this pattern has been updated to no longer utilize panorama controls and be horizontally scrolling; forms using this pattern now scroll vertically and utilize restyled fast tabs for the content sections.  
    -   **Operational workspace w/Tabs**: This variant of the Operational workspace pattern is available starting with version 10.0.25 and uses standard tabs at the highest level for organizing the workspace into different sections. Within each standard tab can be a standard Operational workspace layout, a links section, or more custom content like embedded Power BI reports.  
-   (Deprecated) **Tabbed workspace**: This pattern was initially created as an early to facilitate embedded Power BI reports and a more vertical orientation of workspaces. This pattern is now deprecated and should be replaced by the Operational workspace w/Tabs pattern where possible.
-   (Obsolete) **Workspace**: This pattern is only mentioned for the sake of completeness and cannot be used after version 10.0.25. It is recommended that any remaining usages of this pattern be migrated to one of the other patterns.

The rest of this topic will focus on the Operational workspace patterns.

## Wireframe

### Operational workspace

[![Wireframe for operational workspace.](./media/workspace1.png)](./media/workspace1.png)

### Tabbed workspace

[![Wireframe for tabbed workspace.](./media/tabbedWorkspaceWireframe.png)](./media/tabbedWorkspaceWireframe.png)

## Pattern changes for Finance and Operations
The Microsoft Dynamics AX 2012 Role Center has been replaced by multiple activity-focused workspaces.

## Model

### Operational workspace – High-level structure

- Design

    - *Action pane (ActionPane) \[Optional\]*
    - *Workspace page filter group (Group) \[Optional\]* – This must use the [Workspace Page Filter Group](workspace-filter-group-subpattern.md) subpattern.
    - FastTabs (Tab)

        - Section summary tiles (TabPage) – This must use the [Section Tiles](section-tiles-subpattern.md) subpattern.
        - Section tabbed list (TabPage) – This must use the [Section Tabbed List](section-tabbed-list-subpattern.md) subpattern.
        - *Section charts (TabPage) \[Optional\]* – This must use the [Section Stacked Chart](section-stacked-chart-subpattern.md) subpattern.
        - *Section PowerBI (TabPage) \[Optional\]* – This must use the [Section PowerBI](section-powerbi-subpattern.md) subpattern.
        - Section related links (TabPage) – This must use the [Section Related Links](section-related-links-subpattern.md) subpattern.

### Operational workspace w/Tabs – High-level structure

- Design

    - *Action pane (ActionPane) \[Optional\]*
    - *Workspace page filter group (Group) \[Optional\]* – This must use the [Workspace Page Filter Group](workspace-filter-group-subpattern.md) subpattern.
    - StandardTab (Tab)
        
        - Operatonal workspace content
        - Other content (0..N) 

## Core components

-   Apply the appropriate Workspace pattern on **Form.Design**.
-   Address BP Warnings:
    -   **Form** must be referenced by at least one menu item.
    -   **TabPage.Caption** isn't empty (for all content sections).

## Commonly used subpatterns

- [Workspace Page Filter Group ](workspace-filter-group-subpattern.md)
- [Section Tiles](section-tiles-subpattern.md)
- [Section Tabbed List ](section-tabbed-list-subpattern.md)
- [Section Stacked Chart](section-stacked-chart-subpattern.md)
- [Section PowerBI](section-powerbi-subpattern.md)
- [Section Related Links](section-related-links-subpattern.md)

## Related patterns

- [Form Part Section List](section-list-form-pattern.md)
- [Section Chart](section-chart-form-pattern.md)

## UX guidelines
The verification checklist shows the steps for manually verifying that the form complies with UX guidelines. This checklist doesn't include any guidelines that will be enforced automatically through the development environment. Open the form in the browser, and walk through these steps.

-   Standard form guidelines
    -   Standard form guidelines have been consolidated into the [General Form Guidelines](general-form-guidelines.md) document.
-   Workspace form guidelines
    -   Use a noun phase for the page title, and avoid general words. The page title should not duplicate the title of an area page.
    -   The page title should begin with the noun that users would have in mind.
    -   All sections must have a title.
    -   A section typically spans the width of two to four standard tiles.
    -   Any section that uses a FormPartControl to display content should have **HeightMode** set to **SizeToAvailable** on the FormPartControl.
-   Actions
    -   Include only frequently used commands.
    -   Actions on the Action Pane should be related to the whole workspace (not a specific section of it).
        -   **Exception:** A single "New" action can be put as a tile in the **Summary** section if it's very frequently used.
    -   Group variations of the same command on drop-down menus.
        -   **Examples:** New sales quote, New sales order, New return order
-   Filters
    -   Zero to five filter fields are allowed on a workspace.
        -   Only a single field can be put under the page title
        -   The remaining filters must be in a workspace configuration dialog.

## Example

### Operational workspace

Form: **FMClerkWorkspace** 

[![Operational workspace example.](./media/workspace3.png)](./media/workspace3.png)

## Migration of workspaces to be vertical 
Starting with version 10.0.25, the workspace form patterns and related subpatterns have been adjusted so that content sections stack vertically and are collapsible. The out-of-the-box workspaces were migrated to the latest visuals; however, any other workspaces will need to follow these steps to switch to be vertical in orientation and maintain visual consistency with the rest of the application.  

### Mass updating forms to follow the latest pattern

- BP fixer script
- PowerShell script to iterate over models if you have multiple
- Still need to set some properties manually for now (on workspace - FrameOptionBUtton=None on link groups, FormPart=STA width)

### Manually updating a form 
- If you have a small number of workspaces that follow the pattern or you have a workspace that doesn't utilize the operational workspace pattern
- Remove/reapply form pattern and all subpatterns to get the latest version
- Make same manual metadata tweaks
- If not following the pattern, need to simulate the important parts of what the pattern is doing (panorama -> fast tab, extended style -> simple fast tab, fast tab expanded=yes, 

### Updating form extensions
- Any form extension that adds content into a workspace may also need to be minorly tweaked. The metadata properties set by the new version of the pattern will not take effect (and could cause compile errors) until you open and save the extension. Also, if your form extension is adding new lists via form parts to the workspace or groups of links in teh links section you will need to manually adjust the metadata properties there (frameoptionbutton, widthmode)

## Fit and finish reviews
- Tiles
- Simple lists 
- Card lists

## Frequently asked questions

This section will have answers to frequently asked questions that are related to this guideline/pattern.

## Open issues

-   None

## AX 2012 content

### AX 2012 links

-   [MSDN Role Center Page Reference \[AX 2012\]](/dynamicsax-2012/developer/role-center-page-reference)
-   [MSDN Role Center User Experience Guidelines \[AX 2012\]](/dynamicsax-2012/developer/role-center-user-experience-guidelines)

### AX 2012 example

[![Previous version workspace example.](./media/workspace5.png)](./media/workspace5.png)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
