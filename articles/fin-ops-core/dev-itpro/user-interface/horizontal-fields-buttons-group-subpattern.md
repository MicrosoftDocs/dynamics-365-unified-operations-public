---
title: Horizontal Fields and Buttons Group subpattern
description: Learn about the Horizontal Fields and Buttons Group subpattern, which is used when actions must be defined for an individual field.
author: jasongre
ms.author: jasongre
ms.topic: article
ms.date: 06/20/2017
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Horizontal Fields and Buttons Group subpattern

[!include [banner](../includes/banner.md)]

This article provides information about the Horizontal Fields and Buttons Group form subpattern. This subpattern is used when actions must be defined for an individual field on a form.

## Usage

This subpattern is used when actions must be defined for an individual field on a form. The buttons are laid out just to the right of the field to visually associate the actions with the field. The buttons should display only an icon (no text). Actions that are associated with a section or an entire form should be placed in a Toolbar or ActionPane above that section or form.

### Typical contents

-   1–2 fields
-   1–3 buttons

## Wireframe
[![Wireframe for Horizontal Fields and Buttons Group form subpattern.](./media/horizontalfieldsbuttons1.png)](./media/horizontalfieldsbuttons1.png)

## Pattern changes
Here are the main changes to this pattern since Microsoft Dynamics AX 2012:

-   The layout of fields and buttons will use a single column, where **ArrangeMethod**=**HorizontalLeft**.

## Model
### High-level structure

- Group (ArrangeMethod=HorizontalLeft)

    - Field
    - *Field (optional)*
    - Buttons (1–3 buttons)

### Core components

-   Apply the HorizontalFieldsButtonsGroup subpattern to the container control.
-   Address BP Warnings:
    -   There should be no more than three buttons.
    -   No additional BP checks are required beyond the AX6.3 BP checks that were carried forward.

### Related patterns

-   [Toolbar and Fields](toolbar-fields-subpattern.md)
-   Horizontal Fields

## UX guidelines
The verification checklist shows the steps for manually verifying that the form complies with UX guidelines. This checklist doesn't include any guidelines that will be enforced automatically through the development environment. Open the form in a browser, and walk through these steps.

-   **Standard form guidelines:**
    -   Standard form guidelines have been consolidated into the [General Form Guidelines](general-form-guidelines.md) document.
-   **Horizontal Fields and Buttons Group guidelines:**
    -   The width of the fields + buttons should not exceed the standard size of a column.
    -   Buttons should have a symbol image assigned.
    -   Buttons should have tooltips.
    -   There should be a maximum of three buttons. The last button can be a menu button.

## Examples
Form: **SalesTable (GroupHeaderAddressHeaderOverview)** 

[![Example of SalesTable form.](./media/horizontalfieldsbuttons2.png)](./media/horizontalfieldsbuttons2.png)

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

-   None

### Dynamics AX 2012 content
**SalesTable** 

[![Example of form.](./media/horizontalfieldsbuttons3.png)](./media/horizontalfieldsbuttons3.png)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
