---
# required metadata

title: Section Related Links subpattern | Microsoft Docs
description: This article provides information about the Section Related Links subpattern. This subpattern is used as part of the Operational Workspace pattern, specifically for the last panorama section that contains a set of links to other forms.
author: jasongre
manager: AnnBe
ms.date: 2016-01-11 22:34:29
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
ms.custom: 29331
ms.assetid: 1623aa20-1c3a-4b8c-ab4c-4b3f65172b24
ms.region: Global
# ms.industry: 
ms.author: jasongre

---

# Section Related Links subpattern

This article provides information about the Section Related Links subpattern. This subpattern is used as part of the Operational Workspace pattern, specifically for the last panorama section that contains a set of links to other forms.

Usage
-----

The Section Related Links subpattern is used as part of the Operational Workspace pattern, specifically for the last panorama section that contains a set of links to other forms.

## Wireframe
[![sectionRelatedLinksWireframe](./media/sectionrelatedlinkswireframe.png)](./media/sectionrelatedlinkswireframe.png)

## Pattern changes for Microsoft Dynamics AX
This pattern didn't exist for Microsoft Dynamics AX 2012.

## Model
### High-level structure

TabPage

*LinkButton ($Button) \[0..N\]*

*ButtonGroup (Group) \[0..N\]*

LinkButton ($Button) \[1..N\]

### Core components

Apply Section Related Links to the appropriate tab page in the Operational Workspace.

### Related container patterns

-   [Operational Workspace](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/workspace-form-pattern)

## UX guidelines
The verification checklist shows the steps for manually verifying that the form complies with UX guidelines. This checklist doesn't include any guidelines that will be enforced automatically through the development environment. Open the form in the browser, and walk through these steps. None

## Examples
Form: **PurchOrderProcessReceiptsWorkspace** (**All workspaces** &gt; **Purchase order receipt and follow-up** \[see the **Links** section\]) [![sectionRelatedLinksExample](./media/sectionrelatedlinksexample.png)](./media/sectionrelatedlinksexample.png)

## Appendix
### Frequently asked questions

This section will have answers to frequently asked questions that are related to this guideline/pattern.

### Open issues

None

