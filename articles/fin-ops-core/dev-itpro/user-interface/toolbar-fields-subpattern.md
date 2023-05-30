---
title: Toolbar and Fields subpattern
description: This article provides information about the Toolbar and Fields subpattern. This container pattern is used to show actions above a subpattern of data fields.
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
ms.assetid: c5d6aa38-1f5f-41e5-9d90-11766d34a947
---

# Toolbar and Fields subpattern

[!include [banner](../includes/banner.md)]

This article provides information about the Toolbar and Fields subpattern. This container pattern is used to show actions above a subpattern of data fields. The toolbar should contain fewer than 10 actions.

## Usage

This container pattern is used to show actions above a subpattern of data fields. The toolbar should contain fewer than 10 actions.

## Wireframe

[![Wireframe for Toolbar and Fields subpattern.](./media/toolbarfields1.png)](./media/toolbarfields1.png)

## Model
### High-level structure

- \[Container\]

    - Toolbar (ActionPane, Style=Strip)
    - ContentGroup (Group) – **Note:** A fields subpattern is used.

### Core components

-   Apply the ToolbarFields subpattern to the container control.
-   Address BP Warnings:
    -   No additional BP checks are required beyond the AX6.3 BP checks that were carried forward.

### Related patterns

-   [Toolbar and List](toolbar-list-subpattern.md)

### Commonly used subpatterns

-   [Fields and Field Groups](fields-field-groups-subpattern.md)
-   [Tabular Fields](tabular-fields-subpattern.md)
-   [Dimension Expression Builder](../financial/dimension-expression-builder-subpattern.md)

## UX guidelines
The verification checklist shows the steps for manually verifying that the form complies with UX guidelines. This checklist doesn't include any guidelines that will be enforced automatically through the development environment. Open the form in the browser, and walk through these steps. 

**Standard form guidelines:**

-   Standard form guidelines have been consolidated into the [General Form Guidelines](general-form-guidelines.md) document.

**Toolbar** **guidelines:**

-   Toolbar guidelines have been consolidated into the Dynamics AX [General Form Guidelines](general-form-guidelines.md) document.

## Examples
### Toolbar and Fields

Form: **HcmPosition** **(WorkerAssignmentTabPage)** 

[![Example of Toolbar and Fields subpattern.](./media/toolbarfields2-1024x131.png)](./media/toolbarfields2.png)

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

-   **Should the ShowMoreLess group be part of the pattern, or should it be its own subpattern?**
    -   We will treat the **ShowMoreLess** group as a custom container pattern until there is enough demand to justify the addition of a new pattern.

### Microsoft Dynamics AX 2012 content

**HcmPosition** 

![Toolbar and Fields in previous version.](./media/toolbarfields3.png)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
