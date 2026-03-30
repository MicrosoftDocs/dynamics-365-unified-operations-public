---
title: Test forms that use custom patterns
description: Learn about how to test forms using custom patterns, including overviews on testing configurations and visual issues you may encounter.
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.date: 03/12/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.assetid: 2245dd9f-7ef7-46cc-9e1b-e00fc66526ec
ms.custom: 
  - bap-template
---

# Test forms that use custom patterns

[!include [banner](../includes/banner.md)]

This article shows how to test forms that use custom patterns.

## Introduction

By adhering to form patterns, you gain various benefits. For example, form patterns correctly set layout properties so that forms are laid out responsively. However, when form pattern coverage is lacking (for example, many extensible controls currently aren't supported), or when a form or container has unique requirements or uses that don't fit any pattern, developers can set the pattern to Custom. The developer then becomes responsible for ensuring a correct and responsive form layout.

## Forms that use custom patterns

You can find forms that use custom patterns by using the **Form Patterns** report. For information about running the report, see [Form pattern add-ins](form-pattern-add-ins.md). After running the report, filter the **Percent covered controls** column to show forms that have less than 100-percent coverage. For forms that have a top-level Custom pattern, **Custom** appears in the **Patterns** column.

## Testing configurations

### Key resolution

- 1366 × 768 is a typical resolution on screen sizes that are between 12 and 23 inches. Therefore, this resolution provides a good baseline for testing.
- It's also a good idea to test on a higher resolution, such as 1920 × 1080.

### Parameters

- Browser
  - Internet Explorer 11
  - Google Chrome
  - Microsoft Edge
  - Apple Safari (on iPad) – You need to point Safari to a cloud URL.
    - Landscape and portrait modes
- Density
  - Low density
  - High density
- Viewport size
  - Maximized window
  - Snap view (half the screen) to simulate portrait mode on a tablet
- Zoom
  - 50 to 200 percent

### Steps

Follow these steps: At each step, examine your form for layout problems. As part of your examination, look at all tab pages, and any groups that can expand or collapse content.

1. Open a browser window at full-screen size, and go to your form or control (in low density). Start your testing at a resolution of 1366 × 768.
1. Press the Windows logo key + Left Arrow to switch the browser window to Snap view (half the screen).
1. Slowly resize the browser horizontally back to full width. Stop at intervals, and evaluate the form layout.
1. Slowly resize the browser vertically from full height to half-screen height. Stop at intervals, and evaluate the form layout.
1. Maximize the browser window to full-screen size. Adjust the zoom levels (50 percent, 75 percent, 125 percent, 150 percent, and 200 percent), and evaluate the form layout.
1. Do a sanity check in high density.
1. Do a sanity check in other browsers.

## Visual issues that you might encounter

### Questions to answer while you're testing

- Is the form usable?
- Can I reach everything on the form? (You might have to move multiple scrollbars in smaller viewports.)

### Issues that might suggest problems with the layout metadata

- The form doesn't adjust its content based on the available space.
- Grids and other “fill” controls don't take up the full height or width.
- Containers don't show up at all (there are no scrollbars that you can use to get to parts of the form).
  - This problem can occur with **SizeToAvailable** containers when there's no available height or width.
- There are extra (unnecessary) scrollbars.
  - You should expect more scrollbars in smaller viewports, especially because some containers, such as grids and tab pages, have a minimum height.
  - This problem can occur with **SizeToContent** containers that should be **SizeToAvailable**.

### Other known or expected problems

- Horizontal scrollbars appear on toolbars.
  - When there's not enough width to show all the buttons on a toolbar, a horizontal scrollbar appears. A framework deliverable that implements overflow behavior on toolbars will resolve this problem soon.
- Random input control borders are missing at various zoom levels.
  - This problem is known and is tracked by 1721990.
- Grids receive extra scrollbars, because the space that's available for the grid is less than the grid's minimum height (200 px).
  - The product team plans to investigate reducing or removing this minimum height.
- When StaticText controls that have **SizeToAvailable** width are inside a group that also has **SizeToAvailable** width, horizontal scrollbars appear at some widths (Internet Explorer only).
  - The browser has a calculation error that sometimes causes scrollbars to appear in this scenario.

## Appendix

### Information and guidelines about layout

For information about the layout properties, and for guidelines about scenarios that you should avoid, see [Page layout](page-layout.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
