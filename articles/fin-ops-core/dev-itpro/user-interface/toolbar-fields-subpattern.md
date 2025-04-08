---
title: Toolbar and Fields subpattern
description: Learn about the Toolbar and Fields subpattern. This container pattern is used to show actions above a subpattern of data fields.
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.date: 01/03/2025
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.assetid: c5d6aa38-1f5f-41e5-9d90-11766d34a947
ms.custom: 
  - bap-template
  - evergreen
---

# Toolbar and Fields subpattern

[!include [banner](../includes/banner.md)]

This article provides information about the Toolbar and Fields subpattern. This container pattern is used to show actions above a subpattern of data fields. The toolbar should contain fewer than 10 actions.

## Usage

This container pattern is used to show actions above a subpattern of data fields. The toolbar should contain fewer than 10 actions.

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
The verification checklist shows the steps for manually verifying that the form complies with UX guidelines. This checklist doesn't include any guidelines that are enforced automatically through the development environment. Open the form in the browser, and walk through these steps. 

**Standard form guidelines:**

-   Standard form guidelines are consolidated into the [General Form Guidelines](general-form-guidelines.md) document.

**Toolbar** **guidelines:**

-   Toolbar guidelines are consolidated into the Dynamics AX [General Form Guidelines](general-form-guidelines.md) document.

## Resources
### Typically used by patterns

-   [Simple List and Details](simple-list-details-form-pattern.md)
-   [Table of Contents](table-of-contents-form-pattern.md)
-   [Details Master](details-master-form-pattern.md)
-   [Details Transaction](details-transaction-form-pattern.md)

## Appendix

### Open issues

-   **Should the ShowMoreLess group be part of the pattern, or should it be its own subpattern?**
    -   We treat the **ShowMoreLess** group as a custom container pattern until there's enough demand to justify the addition of a new pattern.




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
