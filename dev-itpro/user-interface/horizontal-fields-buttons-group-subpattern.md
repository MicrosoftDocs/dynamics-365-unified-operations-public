---
# required metadata

title: Horizontal Fields and Buttons Group subpattern | Microsoft Docs
description: This article provides information about the Horizontal Fields and Buttons Group form subpattern. This subpattern is used when actions must be defined for an individual field on a form.
author: jasongre
manager: AnnBe
ms.date: 2015-11-04 20:50:52
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: 61
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 12464
ms.assetid: fa86c96a-fbf4-4d96-8eaf-e83027bfe377
ms.region: Global
# ms.industry: 
ms.author: jasongre

---

# Horizontal Fields and Buttons Group subpattern

This article provides information about the Horizontal Fields and Buttons Group form subpattern. This subpattern is used when actions must be defined for an individual field on a form.

Usage
-----

This subpattern is used when actions must be defined for an individual field on a form. The buttons are laid out just to the right of the field to visually associate the actions with the field. The buttons should display only an icon (no text). Actions that are associated with a section or an entire form should be placed in a Toolbar or ActionPane above that section or form.

### Typical contents

-   1–2 fields
-   1–3 buttons

## Wireframe
[![HorizontalFieldsButtons(1)](./media/horizontalfieldsbuttons1.png)](./media/horizontalfieldsbuttons1.png)

## Pattern changes
Here are the main changes to this pattern since Microsoft Dynamics AX 2012:

-   The layout of fields and buttons will use a single column, where **ArrangeMethod**=**HorizontalLeft**.

## Model
### High-level structure

Group (ArrangeMethod=HorizontalLeft)

Field

*Field (optional)*

Buttons (1–3 buttons)

### Core components

-   Apply the HorizontalFieldsButtonsGroup subpattern to the container control.
-   Address BP Warnings:
    -   There should be no more than three buttons.
    -   No additional BP checks are required beyond the AX6.3 BP checks that were carried forward.

### Related patterns

-   [Toolbar and Fields](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/toolbar-and-fields-subpattern)
-   Horizontal Fields

## UX guidelines
The verification checklist shows the steps for manually verifying that the form complies with UX guidelines. This checklist doesn't include any guidelines that will be enforced automatically through the development environment. Open the form in a browser, and walk through these steps.

-   **Standard form guidelines:**
    -   Standard form guidelines have been consolidated into the [General Form Guidelines](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/general-form-guidelines)document.
-   **Horizontal Fields and Buttons Group guidelines:**
    -   The width of the fields + buttons should not exceed the standard size of a column.
    -   Buttons should have a symbol image assigned.
    -   Buttons should have tooltips.
    -   There should be a maximum of three buttons. The last button can be a menu button.

## Examples
Form: **SalesTable (GroupHeaderAddressHeaderOverview)** [![HorizontalFieldsButtons(2)](./media/horizontalfieldsbuttons2.png)](./media/horizontalfieldsbuttons2.png)

## Resources
### Typically used by patterns

-   [Simple List and Details](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/simple-list-and-details-form-pattern)
-   [Table of Contents](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/table-of-contents-form-pattern)
-   [Details Master](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/details-master-form-pattern)
-   [Details Transaction](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/details-transaction-form-pattern)

## Appendix
### Frequently asked questions

This section will have answers to frequently asked questions that are related to this guideline/pattern.

### Open issues

-   None

### Dynamics AX 2012 content

**SalesTable** [![HorizontalFieldsButtons(3)](./media/horizontalfieldsbuttons3.png)](./media/horizontalfieldsbuttons3.png)

