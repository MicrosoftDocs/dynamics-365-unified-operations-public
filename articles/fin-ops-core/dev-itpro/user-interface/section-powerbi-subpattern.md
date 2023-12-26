---
title: Section Power BI subpattern
description: This article provides information about the Section PowerBI subpattern.
author: jasongre
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: jasongre
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 3e760372-e5ee-49d6-b715-c638294345de
---

# Section Power BI subpattern

[!include [banner](../includes/banner.md)]

This article provides information about the Section PowerBI subpattern. This subpattern is used as part of the Operational Workspace pattern, specifically for the panorama section that contains a PowerBI control.

## Usage

The Section PowerBI subpattern is used as part of the Operational Workspace pattern, specifically for the panorama section that contains the PowerBI control.

## Wireframe
[![Section PowerBI wireframe.](./media/sectionpowerbiwireframe.png)](./media/sectionpowerbiwireframe.png)

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

-   [Configure Power BI integration for workspaces](../analytics/configure-power-bi-integration.md)
-   [Features and services available through Power BI integration](../analytics/power-bi-integration.md)

### Frequently asked questions

This section will have answers to frequently asked questions that are related to this guideline/pattern.

-   **How do I configure PowerBI for integration with my workspace?**
    -   See the [Configure Power BI integration for workspaces](../analytics/configure-power-bi-integration.md) article.

### Open issues

None





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
