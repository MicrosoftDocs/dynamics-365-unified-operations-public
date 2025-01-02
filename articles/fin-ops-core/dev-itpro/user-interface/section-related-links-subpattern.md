---
title: Section Related Links subpattern
description: Learn about the Section Related Links subpattern, including overviews on usage, wireframes, pattern changes, models, UX guidelines, and examples.
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.date: 01/03/2025
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.assetid: 984d7c6b-cf0a-4056-88f3-c32c92ca3401
ms.custom: 
  - bap-template
  - evergreen
---

# Section Related Links subpattern

[!include [banner](../includes/banner.md)]

This article provides information about the Section Related Links subpattern. This subpattern is used as part of the Operational Workspace pattern, specifically for the last panorama section that contains a set of links to other forms.

## Usage

The Section Related Links subpattern is used as part of the Operational Workspace pattern, specifically for the last panorama section that contains a set of links to other forms.

## Pattern changes for Microsoft Dynamics AX
This pattern didn't exist for Microsoft Dynamics AX 2012.

## Model
### High-level structure

- TabPage

    - *LinkButton ($Button) \[0..N\]*
    - *ButtonGroup (Group) \[0..N\]*

- LinkButton ($Button) \[1..N\]

### Core components

Apply Section Related Links to the appropriate tab page in the Operational Workspace.

### Related container patterns

-   [Operational Workspace](workspace-form-pattern.md)

## UX guidelines
The verification checklist shows the steps for manually verifying that the form complies with UX guidelines. This checklist doesn't include any guidelines that will be enforced automatically through the development environment. Open the form in the browser, and walk through these steps. None



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
