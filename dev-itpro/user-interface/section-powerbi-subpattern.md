---
# required metadata

title: Section Power BI subpattern
description: This article provides information about the Section PowerBI subpattern. This subpattern is used as part of the Operational Workspace pattern, specifically for the panorama section that contains a PowerBI control.
author: jasongre
manager: AnnBe
ms date: 2017-04-04
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
ms.custom: 29431
ms.assetid: 3e760372-e5ee-49d6-b715-c638294345de
ms.search.region: Global
# ms.search.industry: 
ms.author: jasongre
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Section Power BI subpattern

This article provides information about the Section PowerBI subpattern. This subpattern is used as part of the Operational Workspace pattern, specifically for the panorama section that contains a PowerBI control.

Usage
-----

The Section PowerBI subpattern is used as part of the Operational Workspace pattern, specifically for the panorama section that contains the PowerBI control.

## Wireframe
[![sectionPowerBIWireframe](./media/sectionpowerbiwireframe.png)](./media/sectionpowerbiwireframe.png)

## Pattern changes for Microsoft Dynamics AX
This pattern didn't exist for Microsoft Dynamics AX 2012.

## Model
### High-level structure

TabPage PowerBI (PowerBI)

### Core components

Apply Section PowerBI to the appropriate tab page in the workspace.

### Related container patterns

-   [Operational workspace](workspace-form-pattern.md)

## UX guidelines
None

## Examples
Form: **FmClerkWorkspace** (**All workspaces** &gt; **Reservation Management**) PowerBI must be configured before the form can appear. (For information about how to configure PowerBI, see the Appendix.)

## Appendix
### Related articles

-   [Configuring PowerBI integration for workspaces](..\analytics\configure-power-bi-integration.md)
-   [Power BI Integration in Dynamics AX](..\analytics\power-bi-integration.md)

### Frequently asked questions

This section will have answers to frequently asked questions that are related to this guideline/pattern.

-   **How do I configure PowerBI for integration with my workspace?**
    -   See the [Configuring PowerBI integration for workspaces](..\analytics\configure-power-bi-integration.md) article.

### Open issues

None

