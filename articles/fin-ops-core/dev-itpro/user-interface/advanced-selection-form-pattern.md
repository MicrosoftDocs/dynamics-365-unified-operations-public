---
title: Advanced selection form pattern
description: Learn about the Advanced Selection form pattern, which lets users filter and select items from a large, wide list.
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.date: 01/03/2025
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.assetid: c3c5eea7-f771-41ea-9976-8d0e1f3d3f25
ms.custom: 
  - bap-template
  - evergreen
---

# Advanced selection form pattern

[!include [banner](../includes/banner.md)]

This article provides information about the Advanced Selection form pattern. This Dialog form pattern lets users filter and select items from a large, wide list. Like the List Panel pattern, this pattern should be used when the primary user task is to select a set of items.

## Usage

The Advanced Selection form pattern should be used when the primary user task is to select a set of items. This task is usually accomplished through a multiselect list. However, in many scenarios, users must select items that aren't contiguous and, at the same time, must see the set of items that they're selecting. This pattern resembles the List panel pattern, in that the user selects items in one list and adds them to another. However, this pattern allows for custom filters and a “wide” list on top, and uses most of the screen "real estate" of the page (typically, it's a Large dialog). Use this pattern when a user must be able to filter and select in a large, wide list.

### Related patterns

-   [List Panel subpattern](list-panel-subpattern.md)
-   [Dialog form pattern](dialog-form-pattern.md)

## UX guidelines
The verification checklist shows the steps for manually verifying that the form complies with UX guidelines. This checklist doesn’t include any guidelines that are enforced automatically through the development environment. Open the form in the browser, and walk through these steps.

-   **Standard form guidelines:**
    -   Standard form guidelines are consolidated into the [General form guidelines](general-form-guidelines.md) document.
-   **Advanced selection guidelines:**
    -   By default, the Quick filter should use the name or description column.
    -   The list can display up to 15 columns.
    -   The main instruction should instruct users what they need to do.
    -   When there's no data, the grid shouldn't  automatically add a new record.





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
