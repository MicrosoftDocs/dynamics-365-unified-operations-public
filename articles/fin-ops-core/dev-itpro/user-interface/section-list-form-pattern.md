---
title: Form Part Section List form patterns
description: Learn about the Form Part Section List form patterns, which were developed to show filtered lists inside workspaces.
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.date: 01/03/2025
ms.update-cycle: 1095-days
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.assetid: 05e02e22-6b71-45f2-bacd-5e3f8ea898fb
ms.custom: 
  - bap-template
  - evergreen
---

# Form Part Section List form patterns

[!include [banner](../includes/banner.md)]

This article provides information about the Form Part Section List form patterns. These workspace-specific patterns have been developed to show filtered lists inside workspaces.

## Usage

The Form Part Section List form patterns are workspace-specific patterns that are used to show filtered lists. The tabbed section of the workspace contains a set of vertical tabs. Each tab contains a Form Part Control that points to a form that contains one of the Form Part Section List patterns. Two patterns are described in this article:

-   **Form Part Section List** – This is the default Section pattern. It allows for a single list of data, together with an optional header group that contains filters and/or actions.  Most content areas in the tabbed section of a workspace will use this pattern.
-   **Form Part Section List - Double** – This variant enables a second list of data to appear to the right of the primary list. By default, the secondary list is hidden. To show it, the user clicks a button on the Toolbar above the primary list.

## Pattern changes for finance and operations apps
These patterns did not exist for Microsoft Dynamics AX 2012.

## Model
### Form Part Section List: High-level structure

- Design | Container

    - *Header (Group) \[Optional\]* – This must use one of the [Filters and Toolbar](filters-toolbar-subpattern.md) subpatterns.
    - Grid
    - *GridDefaultAction (Button) \[Optional\]*
    - *SeeMoreButton (Button) \[Optional\]*

### Form Part Section List - Double: High-level structure

- Design | Container

    - PrimaryGroup (Group)

        - *Header (Group) \[Optional\]* – This must use one of the [Filters and Toolbar](filters-toolbar-subpattern.md) subpatterns.
        - Grid
        - *GridDefaultAction (Button) \[Optional\]*
        - *SeeMoreButton (Button) \[Optional\]*

    - SecondaryGroup (Group)

        - *Header (Group) \[Optional\]* – This must use one of the [Filters and Toolbar](filters-toolbar-subpattern.md) subpatterns.
        - Grid
        - *GridDefaultAction (Button) \[Optional\]*
        - *SeeMoreButton (Button) \[Optional\]*

### Core components

1.  Apply the appropriate Form Part Section List pattern on **Form.Design**.
2.  In the backing Operational workspace form, set the Form Part control on the corresponding vertical tab to point to a menu item that points to this form.

### Related container patterns

-   [Section Tabbed List](section-tabbed-list-subpattern.md)
-   [Filters and Toolbar](filters-toolbar-subpattern.md)

## UX guidelines
The verification checklist shows the steps for manually verifying that the form complies with UX guidelines. This checklist doesn't include any guidelines that will be enforced automatically through the development environment. Open the form in the browser, and walk through these steps.

-   **General form guidelines**
    -   Standard form guidelines have been consolidated into the [General Form Guidelines](general-form-guidelines.md) document.
-   **Pattern-specific guidelines**
    -   If a backing form exists, and especially if not all the records are shown in the list, a **See more** button should appear at the bottom of the list, so that the user can see the full list.
    -   Up to two important filters exist above the list.
    -   Up to three frequently used actions exist above the list.
-   **Grid**
    -   Lists are filtered down to an interesting, relatively small set of data.
    -   List grids have no more than three lines of data per row.
    -   Card grids show no more than four fields (not including an image).
    -   Tabular grids show no more than eight fields.
-   **Form Part Section List - Double guidelines**
    -   If both lists have actions and/or filters, both list must use the same [Filters and Toolbar](filters-toolbar-subpattern.md) subpattern (either the Stacked variant or the Inline variant).
 


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
