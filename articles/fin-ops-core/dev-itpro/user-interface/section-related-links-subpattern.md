---
title: Section Related Links subpattern
description: This article provides information about the Section Related Links subpattern.
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
ms.assetid: 984d7c6b-cf0a-4056-88f3-c32c92ca3401
---

# Section Related Links subpattern

[!include [banner](../includes/banner.md)]

This article provides information about the Section Related Links subpattern. This subpattern is used as part of the Operational Workspace pattern, specifically for the last panorama section that contains a set of links to other forms.

## Usage

The Section Related Links subpattern is used as part of the Operational Workspace pattern, specifically for the last panorama section that contains a set of links to other forms.

## Wireframe
[![Section Related Links wireframe.](./media/sectionrelatedlinkswireframe.png)](./media/sectionrelatedlinkswireframe.png)

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

## Examples
Form: **PurchOrderProcessReceiptsWorkspace** (**All workspaces** &gt; **Purchase order receipt and follow-up** (see the **Links** section) 

[![Section Related Links example.](./media/sectionrelatedlinksexample.png)](./media/sectionrelatedlinksexample.png)

## Appendix
### Frequently asked questions

This section will have answers to frequently asked questions that are related to this guideline/pattern.

### Open issues

None


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
