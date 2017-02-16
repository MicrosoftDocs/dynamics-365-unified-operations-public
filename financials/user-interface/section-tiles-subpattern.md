---
# required metadata

title: Section Tiles subpattern
description: This article provides information about the Section Tiles subpattern. This subpattern is used as part of the Operational Workspace pattern, specifically for the first panorama section (the Summary section) that contains a set of tiles, charts, and singleton cards. 
author: jasongre
manager: AnnBe
ms.date: 2016-01-11 22 - 28 - 19
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
ms.custom: 29311
ms.assetid: b8f4edc2-2720-4722-9c04-66dcba79212d
ms.search.region: Global
# ms.search.industry: 
ms.author: jasongre
ms.dyn365.ops.intro: Feb-16
ms.dyn365.ops.version: AX 7.0.0

---

# Section Tiles subpattern

This article provides information about the Section Tiles subpattern. This subpattern is used as part of the Operational Workspace pattern, specifically for the first panorama section (the Summary section) that contains a set of tiles, charts, and singleton cards. 

Usage
-----

The Section Tiles subpattern is used as part of the Operational Workspace pattern, specifically for the first panorama section (the **Summary** section) that contains a set of tiles, charts, and singleton cards.

## Wireframe
[![sectionTilesWireframe](./media/sectiontileswireframe.png)](./media/sectiontileswireframe.png)

## Pattern changes for Microsoft Dynamics AX
This pattern didn't exist for Microsoft Dynamics AX 2012.

## Model
### High-level structure

TabPage

*TileButton (TileButton) \[0..N\]*

*TargetForm (FormPart) \[0..N\]*

The Form Parts are used to embed Charts or singleton Cards into the **Summary** section of the workspace. Each form that represents a Chart should use the [Section Chart](section-chart-form-pattern.md) form pattern.

### Core components

Apply Section Tiles to the first tab page in the Operational Workspace.

### Related container patterns

-   [Operational Workspace](workspace-form-pattern.md)
-   [Section Chart](section-chart-form-pattern.md)

## UX guidelines
The verification checklist shows the steps for manually verifying that the form complies with UX guidelines. This checklist doesn't include any guidelines that will be enforced automatically through the development environment. Open the form in the browser, and walk through these steps.

-   The **Summary** section should be named "Summary" or a variant that qualifies the word “Summary.”
-   No two tiles in the workspace should have the same symbol.
-   There should be a maximum of one "New" tile.
-   Chart sizes should correspond to multiples of tile sizes.
    -   Available sizes include 1 tile tall × 2 tiles wide, 2 × 2, 2 × 3, 2 × 4, 2 × 6, 4 × 4, 4 × 6, and 4 × 8.

## Examples
Form: **PurchOrderMaintainWorkspace** (**All workspaces** &gt; **Purchase order preparation** \[see the **Summary** section\]) [![sectionTilesExample](./media/sectiontilesexample.png)](./media/sectiontilesexample.png)

## Appendix
### Frequently asked questions

This section will have answers to frequently asked questions that are related to this guideline/pattern.

### Open issues

None

