---
title: List Panel subpattern
description: Learn about the List Panel form subpattern, which manages two lists that move data between each other, including overviews on usage, wireframes, and pattern changes.
author: jasongre
ms.author: jasongre
ms.topic: article
ms.date: 06/20/2017
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# List Panel subpattern

[!include [banner](../includes/banner.md)]

This article provides information about the List Panel form subpattern. Application teams use this subpattern to manage two lists that move data between each other.

## Usage

List Panel is the subpattern that application teams use to manage two lists that move data between each other. This pattern is meant to represent a modeled version of the **SysListPanel** class (programmatic) approach of managing two lists that move data between each other. The List Panel subpattern can be applied on the following controls:

-   TabPage control
-   Group control

## Wireframe
[![List Panel wireframe.](./media/listpanel1-1024x339.png)](./media/listpanel1.png)

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

- \[Container\]

    - *CustomFilterGroup (Group) \[Optional\]*
    - ListPanelGroup (Group)

        - AvailablePanel (Group)

            - Grid | Tree | ListView | ListBox

        - ActionPanel (Group)

            - AddButton (Button)
            - RemoveButton (Button)
            - *AllAllButton (Button) \[Optional\]*
            - *RemoveAllButton (Button) \[Optional\]*

        - SelectedPanel (Group)

            - Grid | Tree | ListView | ListBox\*

        - *MoveUpDownPanel \[Optional\]*

            - MoveUpButton (Button)
            - MoveDownButton (Button)

### Core components

-   Apply the ListPanel subpattern to the container (TabPage or Group) control.
-   Address BP Warnings:
    -   No additional BP checks are required beyond the AX6.3 BP checks that were carried forward.

## UX guidelines
The verification checklist shows the steps for manually verifying that the form complies with UX guidelines. This checklist doesn't include any guidelines that will be enforced automatically through the development environment. Open the form in a browser, and walk through these steps.

-   **Standard form guidelines:**
    -   Standard form guidelines have been consolidated into the [General Form Guidelines](general-form-guidelines.md) document.

## Examples
Form: **SalesSummaryParameters (GroupQuotation)** 

[![List Panel example for SalesSummaryParameters.](./media/listpanel3.png)](./media/listpanel3.png)

## Resources
### Typically used by patterns

-   [Simple List and Details](simple-list-details-form-pattern.md)
-   [Table of Contents](table-of-contents-form-pattern.md)
-   [Details Master](details-master-form-pattern.md)
-   [Dialog](dialog-form-pattern.md)
-   [Wizard](wizard-form-pattern.md)

## Appendix
### Frequently asked questions

This section will have answers to frequently asked questions that are related to this guideline/pattern.

### Open issues

-   None

### AX 2012 content

[![List Panel example.](./media/listpanel4.png)](./media/listpanel4.png)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
