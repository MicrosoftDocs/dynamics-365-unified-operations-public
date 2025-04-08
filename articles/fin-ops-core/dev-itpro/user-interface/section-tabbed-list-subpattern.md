---
title: Section Tabbed List subpattern
description: Learn about the Section Tabbed List subpattern, including overviews on usage, wireframes, pattern changes, models, and UX guidelines.
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.date: 01/03/2025
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.assetid: 3f8b00ff-54f0-4e32-bd7f-b94a74785537
ms.custom: 
  - bap-template
  - evergreen
---

# Section Tabbed List subpattern

[!include [banner](../includes/banner.md)]

This article provides information about the Section Tabbed List subpattern. This subpattern is used as part of the Operational Workspace pattern, specifically for a panorama section that contains a set of vertical tabs, each of which contains a filtered list of data.

## Usage

The Section Tabbed List subpattern is used as part of the Operational Workspace pattern, specifically for a panorama section that contains a set of vertical tabs, each of which contains a filtered list of data.

## Pattern changes for Microsoft Dynamics AX
This pattern didn't exist for Microsoft Dynamics AX 2012.

## Model
### High-level structure

- TabPage
- TabbedList (Tab) (Style=VerticalTabs)

    - *TabbedListPage (TabPage) \[0..N\]*

        - TargetForm (FormPart)

Each Form Part points to a form that contains the content for the section. Each of these forms should use one of the Form Part Section List form patterns.

### Core components

Apply Section Tabbed List to the appropriate tab page in the workspace.

### Related container patterns

-   [Operational Workspace](workspace-form-pattern.md)
-   [Form Part Section List](section-list-form-pattern.md)

## UX guidelines
The verification checklist shows the steps for manually verifying that the form complies with UX guidelines. This checklist doesn't include any guidelines that will be enforced automatically through the development environment. Open the form in the browser, and walk through these steps.

-   At least one list should be present in the tabbed list section.
-   Each Form Part Control should point to a form that uses one of the [Form Part Section List](section-list-form-pattern.md) patterns.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
