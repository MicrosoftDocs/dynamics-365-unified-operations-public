---
# required metadata

title: Fill Text subpattern | Microsoft Docs
description: This article provides information about the Fill Text subpattern. This subpattern is used when a single String or StaticText control must stretch to the full width of the container, so that users have more space to enter information.
author: jasongre
manager: AnnBe
ms.date: 2015-11-04 20:46:48
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
ms.custom: 12414
ms.assetid: b7572e9e-052a-4094-83e6-80388a24d815
ms.region: Global
# ms.industry: 
ms.author: jasongre

---

# Fill Text subpattern

This article provides information about the Fill Text subpattern. This subpattern is used when a single String or StaticText control must stretch to the full width of the container, so that users have more space to enter information.

Usage
-----

Fill Text is used when you need a single String or StaticText control to stretch to the full width of the container. This subpattern is typically used for multi-line string controls that require more space for users to enter information.

## Wireframe
[![Fill Text sub-pattern wireframe](./media/filltext1.png)](./media/filltext1.png)

## Model
### High-level structure

\[Container\]

String | StaticText

### Core components

-   Apply the Fill Text subpattern to the container control.

### Related container patterns

-   [Fields and Field Groups](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/fields-and-field-groups-subpattern)

## UX guidelines
None

## Examples
Form: **FmRental (Notes)** [![Fill Text sub-pattern example](./media/filltext2.png)](./media/filltext2.png)

## Resources
### Typically used by patterns

-   [Details Master](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/details-master-form-pattern)
-   [Details Transaction](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/details-transaction-form-pattern)
-   [Simple Details](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/simple-details-form-pattern)
-   [Simple List and Details](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/simple-list-and-details-form-pattern)
-   [Table Of Contents](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/table-of-contents-form-pattern)
-   [Wizard](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/wizard-form-pattern)

## Appendix
### Frequently asked questions

This section will have answers to frequently asked questions that are related to this guideline/pattern.

### Open issues

-   The pattern currently sets the **HeightMode** property of the control to **SizeToAvailable**. This can produce very tall string controls if the pattern is used in a **SizeToAvailable** container. We’re investigating whether this control should use **SizeToContent** height, or whether it should not set the property at all and should instead let the developer decide the appropriate control height.


