---
title: Section Stacked Chart subpattern
description: Learn about the Section Stacked Chart subpattern, including overviews on usage, wireframes, pattern changes, models, and UX guidelines.
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.date: 01/03/2025
ms.update-cycle: 1095-days
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.assetid: 58fea559-4d50-46f3-9a88-4cca1d882d04
ms.custom: 
  - bap-template
  - evergreen
---

# Section Stacked Chart subpattern

[!include [banner](../includes/banner.md)]

This article provides information about the Section Stacked Chart subpattern. This subpattern is used as part of the Operational Workspace pattern when a panorama section contains one or two charts.  

## Usage

The Section Stacked Chart subpattern is used as part of the Operational Workspace pattern, specifically for a panorama section that contains one or two charts.

## Pattern changes for Microsoft Dynamics AX
This pattern didn't exist for Microsoft Dynamics AX 2012.

## Model
### High-level structure

- TabPage

    - *ChartPart (FormPart) \[0..N\]*

Each Form Part points to a form that contains a single chart. Each of these forms should use the [Section Chart](section-chart-form-pattern.md) form pattern.

### Core components

Apply Section Stacked Chart to the appropriate tab page in the workspace.

### Related container patterns

-   [Operational workspace](workspace-form-pattern.md)
-   [Section Chart](section-chart-form-pattern.md)

## UX guidelines
The verification checklist shows the steps for manually verifying that the form complies with UX guidelines. This checklist doesn't include any guidelines that will be enforced automatically through the development environment. Open the form in the browser, and walk through these steps.

-   There should be no more than two charts in this section.
-   Each Form Part Control should point to a form that uses the [Section Chart](section-chart-form-pattern.md) pattern.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
