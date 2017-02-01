---
# required metadata

title: List Panel subpattern | Microsoft Docs
description: This article provides information about the List Panel form subpattern. Application teams use this subpattern to manage two lists that move data between each other.
author: jasongre
manager: AnnBe
ms.date: 2015-11-04 20:47:36
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
ms.custom: 12433
ms.assetid: e311e10e-2393-4692-bf85-ecb86cbd38d5
ms.region: Global
# ms.industry: 
ms.author: jasongre

---

# List Panel subpattern

This article provides information about the List Panel form subpattern. Application teams use this subpattern to manage two lists that move data between each other.

Usage
-----

List Panel is the subpattern that application teams use to manage two lists that move data between each other. This pattern is meant to represent a modeled version of the **SysListPanel** class (programmatic) approach of managing two lists that move data between each other. The List Panel subpattern can be applied on the following controls:

-   TabPage control
-   Group control

## Wireframe
[![ListPanel(1)](./media/listpanel1-1024x339.png)](./media/listpanel1.png)

## Pattern changes
Here are the main changes to this pattern since Microsoft Dynamics AX 2012:

-   List (Grid/ListView) and Tree controls are supported.
-   The right panel is the selected section.
-   The left panel is the available section.
-   Six buttons are available as actions:
    -   Add
    -   Remove
    -   Add All (Optional)
    -   Remove All (Optional)
    -   Move Up (Optional)
    -   Move Down (Optional)

## Model
### High-level structure

\[Container\]

*CustomFilterGroup (Group) \[Optional\]*

ListPanelGroup (Group)

AvailablePanel (Group)

Grid | Tree | ListView | ListBox

ActionPanel (Group)

AddButton (Button)

RemoveButton (Button)

*AllAllButton (Button) \[Optional\]*

*RemoveAllButton (Button) \[Optional\]*

SelectedPanel (Group)

Grid | Tree | ListView | ListBox\*

*MoveUpDownPanel \[Optional\]*

MoveUpButton (Button)

MoveDownButton (Button)

### Core components

-   Apply the ListPanel subpattern to the container (TabPage or Group) control.
-   Address BP Warnings:
    -   No additional BP checks are required beyond the AX6.3 BP checks that were carried forward.

## UX guidelines
The verification checklist shows the steps for manually verifying that the form complies with UX guidelines. This checklist doesn't include any guidelines that will be enforced automatically through the development environment. Open the form in a browser, and walk through these steps.

-   **Standard form guidelines:**
    -   Standard form guidelines have been consolidated into the Microsoft Dynamics AX [General Form Guidelines](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/general-form-guidelines)document.

## Examples
Form: **CLIPatterns\_ListPanel** **(FormTabPageControl1)** [![ListPanel(2)](./media/listpanel2-1024x283.png)](./media/listpanel2.png) Form: **SalesSummaryParameters (GroupQuotation)** [![ListPanel(3)](./media/listpanel3.png)](./media/listpanel3.png)

## Resources
### Typically used by patterns

-   [Simple List and Details](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/simple-list-and-details-form-pattern)
-   [Table of Contents](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/table-of-contents-form-pattern)
-   [Details Master](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/details-master-form-pattern)
-   [Dialog](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/dialog-form-pattern)
-   [Wizard](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/wizard-form-pattern)

## Appendix
### Frequently asked questions

This section will have answers to frequently asked questions that are related to this guideline/pattern.

### Open issues

-   None

### AX 2012 content

[![ListPanel(4)](./media/listpanel4.png)](./media/listpanel4.png)

