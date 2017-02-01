---
# required metadata

title: Advanced selection form pattern | Microsoft Docs
description: This article provides information about the Advanced Selection form pattern. This Dialog form pattern lets users filter and select items from a large, wide list. Like the List Panel pattern, this pattern should be used when the primary user task is to select a set of items.
author: jasongre
manager: AnnBe
ms.date: 2016-01-11 18:36:32
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
ms.custom: 29171
ms.assetid: 9d741388-9431-4d5e-a696-685393903a21
ms.region: Global
# ms.industry: 
ms.author: jasongre

---

# Advanced selection form pattern

This article provides information about the Advanced Selection form pattern. This Dialog form pattern lets users filter and select items from a large, wide list. Like the List Panel pattern, this pattern should be used when the primary user task is to select a set of items.

Usage
-----

The Advanced Selection form pattern should be used when the primary user task is to select a set of items. This task is usually accomplished through a multi-select list. However, in many scenarios, users must select items that aren't contiguous and, at the same time, must see the set of items that they are selecting. This pattern resembles the List panel pattern, in that the user selects items in one list and adds them to another. However, this pattern allows for custom filters and a “wide” list on top, and uses most of the screen "real estate" of the page (typically, it's a Large dialog). Use this pattern when a user must be able to filter and select in a large, wide list.

## Wireframe
[![Advanced Selection pattern wireframe](./media/advancedselection1.png)](./media/advancedselection1.png)

### Related patterns

-   [List Panel](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/list-panel-subpattern)
-   [Dialog](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/dialog-form-pattern)

## Pattern changes for Dynamics AX
This is a new pattern in the current version of Microsoft Dynamics AX.

## UX guidelines
The verification checklist shows the steps for manually verifying that the form complies with UX guidelines. This checklist doesn’t include any guidelines that will be enforced automatically through the development environment. Open the form in the browser, and walk through these steps.

-   **Standard form guidelines:**
    -   Standard form guidelines have been consolidated into the Dynamics AX [General Form Guidelines](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/general-form-guidelines)document.
-   **Advanced selection guidelines:**
    -   By default, the Quick filter should use the name or description column.
    -   The list can display up to 15 columns. **Note:** This guidelines has been relaxed since Microsoft Dynamics AX 2012.
    -   The main instruction should instruct users what they need to do.
    -   When there is no data, the grid should not automatically add a new record.

## Example
Form: **ProcCategoryAddVendor** (Click **Procurement and sourcing** &gt; **Procurement categories**. On the **Vendors** FastTab, click **Add**.) [![advancedSelectionExample](./media/advancedselectionexample.png)](./media/advancedselectionexample.png)

## Appendix
### Frequently asked questions

This section will have answers to frequently asked questions that are related to this guideline/pattern.

### Open issues

None at this time

