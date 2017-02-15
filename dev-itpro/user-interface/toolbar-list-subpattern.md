---
# required metadata

title: Toolbar and List subpattern
description: This article provides information about the Toolbar and List form subpattern. This subpattern is used to show child collections for the parent entity as either a tabular grid or a tree. 
author: jasongre
manager: AnnBe
ms.date: 2015-12-03 21 - 34 - 06
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 15931
ms.assetid: f1eb2629-1043-4514-bb66-95638f427277
ms.search.region: Global
# ms.search.industry: 
ms.author: jasongre
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# Toolbar and List subpattern

This article provides information about the Toolbar and List form subpattern. This subpattern is used to show child collections for the parent entity as either a tabular grid or a tree. 

Usage
-----

This subpattern is used to show child collections for the parent entity as either a tabular grid or a tree. The toolbar contains fewer than 10 actions. If a grid is used, it contains fewer than 10 fields. This article describes two patterns:

-   **Toolbar and list** – This is the basic version of the pattern and should be used by default.
-   **Toolbar and list (double)** – This variant includes two lists and an optional toolbar above each list.

## Wireframes
### Toolbar and list

[![ToolbarList(1)](./media/toolbarlist1.png)](./media/toolbarlist1.png)

### Toolbar and list (double)

[![ToolbarList(2)](./media/toolbarlist2.png)](./media/toolbarlist2.png)

## Model
### Toolbar and list – High-level structure

\[Container\]

*Toolbar (ActionPane, Style=Strip) \[Optional\]*

*CustomFilterGroup (Group) \[Optional\]*

Grid | Tree | ListView | Table

*Footer (Group) \[Optional\]*

### Toolbar and list (double) – High-level structure

\[Container\]

*Toolbar1 (ActionPane, Style=Strip) \[Optional\]*

*CustomFilterGroup1 (Group) \[Optional\]*

Grid | Tree | ListView | Table

*Toolbar2 (ActionPane, Style=Strip) \[Optional\]*

*CustomFilterGroup2 (Group) \[Optional\]*

Grid | Tree | ListView | Table

*Footer (Group) \[Optional\]*

### Core components

-   Apply the ToolbarList subpattern to a container control.
-   Address BP Warnings:
    -   **Grid.DataSource** must not be empty.
    -   No additional BP checks are required beyond the AX6.3 BP checks that were carried forward.

### Related patterns

-   [Toolbar and Fields](toolbar-fields-subpattern.md)

## UX guidelines
The verification checklist shows the steps for manually verifying that the form complies with UX guidelines. This checklist doesn't include any guidelines that will be enforced automatically through the development environment. Open the form in the browser, and walk through these steps. **Standard form guidelines:**

-   Standard form guidelines have been consolidated into the Microsoft Dynamics AX [General Form Guidelines](general-form-guidelines.md)document.

**Toolbar** **guidelines:**

-   Toolbar guidelines have been consolidated into the Dynamics AX [General Form Guidelines ](general-form-guidelines.md)document.

## Examples
### Toolbar and list

Form: **VendTable (TabCommunication)** [![ToolbarList(3)](./media/toolbarlist3.png)](./media/toolbarlist3.png)

### Toolbar and list (double)

Form: **SalesQuickQuote (TabPageExistingItems)** [![ToolbarList(4)](./media/toolbarlist4.png)](./media/toolbarlist4.png)

## Resources
### Typically used by patterns

-   [Simple List and Details](simple-list-details-form-pattern.md)
-   [Table of Contents](table-of-contents-form-pattern.md)
-   [Details Master](details-master-form-pattern.md)
-   [Details Transaction](details-transaction-form-pattern.md)

## Appendix
### Frequently asked questions

This section will have answers to frequently asked questions that are related to this guideline/pattern.

### Open issues

-   **Does CommandButton.Command contain Add and Remove actions that provide the default icon, label, and tooltip?**
    -   Not yet. Deliverable 1052359 will look at setting these defaults for Add and Remove commands.
-   **Do we care about separators between groups of icons in a migration context?**
    -   Currently, we don't show separators between button groups on toolbars.

### Microsoft Dynamics AX 2012 content

**VendTable** [![ToolbarList(5)](./media/toolbarlist5.png)](./media/toolbarlist5.png)

