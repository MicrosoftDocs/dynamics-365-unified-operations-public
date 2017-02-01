---
# required metadata

title: Table of Contents form pattern | Microsoft Docs
description: This article provides information about the Table of Contents form pattern. This pattern should be used when two or more logically related forms are required for setup configuration. 
author: jasongre
manager: AnnBe
ms.date: 2015-12-02 23:36:47
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
ms.custom: 14621
ms.assetid: e36f9ab7-f97d-474b-94c6-81e7cc0151c0
ms.region: Global
# ms.industry: 
ms.author: jasongre

---

# Table of Contents form pattern

This article provides information about the Table of Contents form pattern. This pattern should be used when two or more logically related forms are required for setup configuration. 

Usage
-----

The Table of Contents pattern should be used when two or more logically related forms are required for setup configuration. The vertical arrangement of tabs implies the order of completion. This form pattern is also used for collections of unrelated items, such as tab pages that have a different root entity per tab. This form pattern contains a collection of smaller content regions, each of which follows a container subpattern such as Toolbar and List, Nested Simple List and Details, or Fields and Field Groups.

## Wireframe
[![TOC(1)](./media/toc1.png)](./media/toc1.png)

## Pattern changes
Here are the main changes to this pattern since Microsoft Dynamics AX 2012:

-   The Content Body child container uses dynamic columns for a responsive layout.
-   An optional secondary instruction has been added under the Title Group.

## Model
### High-level structure

Design

Tab (Style=VerticalTabs)

TabPage *\[repeats 1..N times\]*

Title (Group)

MainInstruction (StaticText)

*SecondaryInstruction (StaticText) \[Optional\]*

Body (Group) | FastTabContent (Tab)

### Core components

-   Apply the TableOfContents pattern on **Form.Design**.
-   Address BP Warnings:
    -   **Design.Caption** isn't empty.
    -   The form must be referenced by at least one menu item.
    -   **TabPage.Caption** isn't empty.
    -   **TabPage.DataSource** isn't empty.
    -   **StaticText.Text** isn't empty.

### Commonly used subpatterns

Each BodyGroup will use one of the following container patterns for the content in the Table of Contents section:

-   [Fields and Field Groups](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/fields-and-field-groups-subpattern)
-   [Toolbar and List](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/toolbar-and-list-subpattern)
-   [Toolbar and Fields](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/toolbar-and-fields-subpattern)
-   [Nested Simple List and Details](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/nested-simple-list-and-details-subpattern)
-   [Tabular Fields](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/tabular-fields-subpattern)
-   [List Panel](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/list-panel-subpattern)

## UX guidelines
The verification checklist shows the steps for manually verifying that the form complies with UX guidelines. This checklist doesn't include any guidelines that will be enforced automatically through the development environment. Open the form in the browser, and walk through these steps. **Standard form guidelines:**

-   Standard form guidelines have been consolidated into the Microsoft Dynamics AX [General Form Guidelines](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/general-form-guidelines)document.

**Table of contents guidelines:**

-   The supplemental instruction, if it's shown, is composed of a complete, concise sentence in sentence case and has end punctuation.
-   TOC tabs should appear in the same sequence that is typically used to enter information.
-   The first tab in the list should be highlighted when the form is opened, unless the form is opened in the context of a specific task from another form.
-   The **content area** for the TOC content should primarily be one of three patterns: Simple List, Simple List and Details, or Simple Details.
    -   Simple List content should follow the subpattern guidelines.
    -   Simple List and Details content should follow the [Nested Simple List and Details](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/nested-simple-list-and-details-subpattern) subpattern guidelines.
    -   Simple Details content should follow the [Toolbar and Fields](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/toolbar-and-fields-subpattern) subpattern guidelines.
    -   FastTabs should follow the FastTab guidelines in the Dynamics AX [General Form Guidelines ](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/general-form-guidelines)document.
    -   Actions appearing on a Toolbar on a tab page.
-   A TOC form should **not** have the following:
    -   Application actions on a standard ActionPane. (It should have only framework actions.)
    -   FactBoxes.
    -   Standard tabs on a TOC tab page.

## Examples
Form: **CustParameters** [![TOC(2)](./media/toc2.png)](./media/toc2.png)

## Appendix
### Frequently asked questions

This section will have answers to frequently asked questions that are related to this guideline/pattern.

-   **What do I do with ‘Global’ buttons?**
    -   There have been several cases where a button is required in order to initialize data or sync information between services. Because we allow only system buttons on the standard Action Pane in this pattern, we recommend that these buttons go in one of two places:
        -   On the tab page that the action is most closely related to.
        -   If a place doesn’t exist, on a toolbar on the first tab page of the pattern.

### Open issues

-   None

### AX 2012 content

[![TOC(3)](./media/toc3.png)](./media/toc3.png)[![TOC(4)](./media/toc4.png)](./media/toc4.png)

