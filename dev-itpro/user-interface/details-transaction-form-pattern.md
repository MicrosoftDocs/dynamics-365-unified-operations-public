---
# required metadata

title: Details Transaction form pattern | Microsoft Docs
description: This article provides information about the Details Transaction form pattern. Forms that use this pattern can have two details views that the user can switch between: a Header view and a Line view.
author: jasongre
manager: AnnBe
ms.date: 2015-12-04 00:18:36
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
ms.custom: 16281
ms.assetid: 430ec516-af39-4504-afd8-802f9a7c36bc
ms.region: Global
# ms.industry: 
ms.author: jasongre

---

# Details Transaction form pattern

This article provides information about the Details Transaction form pattern. Forms that use this pattern can have two details views that the user can switch between: a Header view and a Line view.

Usage
-----

A details form with lines (Details Transaction form) consists of one form that can have two details views that the user can switch between. The Header view contains all fields that are related to or part of the header. The Line view contains the lines grid, line details, and a section that contains a collection of the most important header fields.

## Wireframe
### Line view

[![Wireframe: Line view](./media/detailstransaction1-1024x575.png)](./media/detailstransaction1.png)

### Header view

[![Wireframe: Header view](./media/detailstransaction2-1024x576.png)](./media/detailstransaction2.png)

### Grid view

[![Wireframe: Grid view](./media/detailstransaction3-1024x575.png)](./media/detailstransaction3.png)

## Pattern changes
Here are the main changes to this pattern since Microsoft Dynamics AX 2012:

-   A List style grid was been added to the left of the Details view content, which is shown in either Header view or Line view.
-   List Page and Details Master have been merged into a single form. This change has the following benefits:
    -   It improves performance when users move between the list and details.
    -   It enables bulk editing in the initial list.
    -   It allows for elimination of the list page preview pane.
-   View/Edit, New, Delete, Save, Refresh, Attachments, and Export to Excel actions are all provided by the foundation and should not have explicit app buttons unless the foundation-provided button is removed.

## Model
### High-level structure

Design

ActionPane (ActionPane)

SidePanel (Group)

QuickFilter

*CustomFilters (Group\] \[Optional\]*

NavigationList (Grid, Style=List)

PanelTab (Tab ShowTabs=No)

DetailsPanel (TabPage)

TitleGroup (Group)

HeaderTitle (String)

*EntityStatus (Group) \[Optional\]*

StatusFields (1..N)

HeaderLinePanels (Tab ShowTabs=No)

LinePanel (TabPage PanelStyle=Line)

LineViewTab (Tab Style=FastTabs)

LineViewHeader (TabPage)

LineViewLines (TabPage)

LineViewLineDetails (TabPage)

LineDetailsTab (Tab Style=Standard)

LineDetailsTabPages (TabPages 1..N)

HeaderPanel (TabPage PanelStyle=Header)

HeaderViewTab (Tab Style=FastTabs)

HeaderViewTabPages (TabPages 1..N)

GridPanel (TabPage PanelStyle=Grid)

CustomFilterGroup (Group)

QuickFilter

*OtherFilters ($Field) \[0..N\]*

MainGrid (Grid)

MainGridDefaultAction (CommandButton)

### Core components

1.  Apply the DetailsTransaction pattern on **Form.Design**.
2.  Address BP Warnings:
    1.  **Design.Caption** isn't empty.
    2.  The form must be referenced by at least one menu item.
    3.  **TabPage.Caption** isn't empty.
    4.  **TabPage.DataSource** isn't empty.

### Related patterns

-   [Details Master](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/details-master-form-pattern)
-   [Simple List and Details](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/simple-list-and-details-form-pattern)

### Commonly used subpatterns

-   [Fields and Field Groups](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/fields-and-field-groups-subpattern)
-   [Toolbar and List](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/toolbar-and-list-subpattern)
-   [Toolbar and Fields](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/toolbar-and-fields-subpattern)
-   [Nested Simple List and Details](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/nested-simple-list-and-details-subpattern)
-   [Custom Filter Group](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/custom-filter-group-subpattern)

## UX guidelines
The verification checklist shows the steps for manually verifying that the form complies with UX guidelines. This checklist doesn't include any guidelines that will be enforced automatically through the development environment. Open the form in the browser, and walk through these steps. **Standard form guidelines:**

-   Standard form guidelines have been consolidated into the Microsoft Dynamics AX [General Form Guidelines](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/general-form-guidelines) document.

**Detail Transaction guidelines:**

-   There should not be any duplicate **New** and **Delete** buttons.
-   **ActionPane** guidelines have been consolidated into the Dynamics AX [General Form Guidelines](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/general-form-guidelines) document, in the ActionPane guidelines section.
-   In its **default** state, the content of the first FastTab should be fully visible without scrolling.
-   **FastTabs** guidelines have been consolidated into the Dynamics AX [General Form Guidelines](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/general-form-guidelines) document.
-   **Page title area**:
    -   The following format should be used: **&lt;ID&gt; : &lt;Description&gt;**
    -   A link to the Details page should be provided on the Main Menu after the List page has been merged into the Details page.
    -   The page title should be in a plural form.
-   **Navigation list grid**:
    -   The list style grid should not have fields within a grid row that spans more than three lines.
        -   Typically, just the ID and Description are sufficient.
        -   There should be at least two fields.
    -   The last field should be the total of the transaction.
-   **Grid view**:
    -   The grid has 2 to 15 fields. Typically, all mandatory fields are included, so that records can be created in the grid.
    -   A linked field lets the user open the details for the selected record.
    -   By default, the Quick Filter should use the most likely field for a filter scenario.
    -   Focus should be in the Quick Filter when the list page is opened.
    -   **Grid**:
        -   The **ID** field should be the first column, followed by the master entity **ID** and **Name** fields.
        -   Additional grid guidelines have been consolidated into the Dynamics AX [General Form Guidelines](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/general-form-guidelines) document, in the Grid guidelines section.
    -   **FactBox** guidelines have been consolidated into the [FactBox Form Patterns](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/factbox-form-patterns) document.

## Example
Form: **SalesTable**

#### Line view

[![Details Transaction example: Line view](./media/detailstransaction4-1024x508.png)](./media/detailstransaction4.png)

#### Header view

[![Details Transaction example: Header view](./media/detailstransaction5-1024x509.png)](./media/detailstransaction5.png)

#### Grid view

[![Details Transaction example: Grid view](./media/detailstransaction6-1024x509.png)](./media/detailstransaction6.png)

## Appendix
### Frequently asked questions

This section will have answers to frequently asked questions that are related to this guideline/pattern.

-   **Why is the Header view compulsory?**
    -   The Header view is compulsory for the Details Transaction pattern. Initially, the Header view might not have more than the Line view header summary information. However, over time, it will be extended by application teams, internationalization teams, partners, and customers. It's important that the Header view be available for future modifications. In addition, a consistent and dependable form structure has benefits for usability and upgrade reasons.

### Open issues

None currently.

### AX 2012 content

#### AX 2012 links

-   [MSDN Details Form with Lines User Experience Guidelines \[AX 2012\]](http://msdn.microsoft.com/EN-US/library/gg886601.aspx)
-   [MSDN Details Form \[AX 2012\]](http://msdn.microsoft.com/EN-US/library/hh397318.aspx)

#### AX 2012 example

##### Line view

[![AX 2012 example: Line view](./media/detailstransaction7-1024x727.png)](./media/detailstransaction7.png)

##### Header view

[![AX 2012 example: Header view](./media/detailstransaction8-1024x727.png)](./media/detailstransaction8.png)

##### Grid view

[![AX 2012 example: Grid view](./media/detailstransaction9-1024x727.png)](./media/detailstransaction9.png)

