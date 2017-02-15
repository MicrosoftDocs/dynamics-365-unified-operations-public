---
# required metadata

title: Test forms with custom patterns
description: This wiki how to test forms using custom patterns.
author: jasongre
manager: AnnBe
ms.date: 2015-12-18 23 - 13 - 25
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 28291
ms.assetid: 0eb7d4e4-e166-41b9-b865-c46eed43b838
ms.search.region: Global
# ms.search.industry: 
ms.author: jasongre
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# Test forms with custom patterns

This wiki how to test forms using custom patterns.

Introduction
------------

By adhering to form patterns, you gain various benefits. For example, form patterns correctly set layout properties so that forms are laid out responsively. However, when form pattern coverage is lacking (for example, there currently isn't support for many extensible controls), or when a form or container has unique requirements/uses that don't fit any pattern, developers can set the pattern to Custom. The developer then becomes responsible for ensuring a correct and responsive form layout.

## Forms that use Custom patterns
You can use the **Form Patterns** report to find the set of forms that use Custom patterns (either top-level form patterns or subpatterns). Filter the **Percent covered controls** column to show forms that have less than 100-percent coverage. For forms that have a top-level Custom pattern, **Custom** will appear in the **Patterns** column. To generate the **Form Patterns** report, start Microsoft Visual Studio, click the **DYNAMICS AX** menu, expand **Add-ins**, and then click **Run the form patterns report**. The process will take several seconds. After the report has been generated, a dialog will provide the location of the report. Browse to the specified location, and open the file in Microsoft Excel. You can then filter the report down to the models that interest you.

## Testing configurations
### Key resolution

-   1366 × 768 is a typical resolution on screen sizes that are between 12 and 23 inches. Therefore, this resolution provides a good baseline for testing.
-   It's also a good idea to test on a higher resolution, such as 1920 × 1080.

### Parameters

-   Browser
    -   Internet Explorer 11
    -   Google Chrome
    -   Microsoft Edge
    -   Apple Safari (on iPad) – You'll have to point Safari to a cloud URL.
        -   Landscape and portrait modes
-   Density
    -   Low density
    -   High density
-   Viewport size
    -   Maximized window
    -   Snap view (half the screen) to simulate portrait mode on a tablet
-   Zoom
    -   50 to 200 percent

### Steps

Follow these steps. At each step, examine your form for layout issues. As part of your examination, look at all tab pages, and any groups that can expand/collapse content.

1.  Open a browser window at full-screen size, and navigate to your form/control (in low density). It's a good idea to starting your testing at a resolution of 1366 × 768.
2.  Press the Windows log key+Left Arrow to switch the browser window to Snap view (half the screen).
3.  Slowly resize the browser horizontally back to full width. Stop at intervals, and evaluate the form layout.
4.  Slowly resize the browser vertically from full height to half-screen height. Stop at intervals, and evaluate the form layout.
5.  Maximize the browser window to full-screen size. Adjust the zoom levels (50 percent, 75 percent, 125 percent, 150 percent, and 200 percent), and evaluate the form layout.
6.  Do a sanity check in high density.
7.  Do a sanity check in other browsers.

## Visual issues that you might encounter
### Questions to answer while you're testing

-   Is the form usable?
-   Can I reach everything on the form? (You might have to move multiple scrollbars in smaller viewports.)

### Issues that might suggest problems with the layout metadata

-   Form content isn't being adjusted based on the available space.
-   Grids and other “fill” controls aren't taking up the full height/width.
-   Containers aren't showing up at all (there are no scrollbars that you can use to get to parts of the form).
    -   This issue can occur with **SizeToAvailable** containers when there is no available height/width.
-   There are extra (unnecessary) scrollbars.
    -   You should expect more scrollbars in smaller viewports, especially because some containers (for example, grids and tab pages) have a minimum height.
    -   This issue can occur with **SizeToContent** containers that should be **SizeToAvailable**.

### Other known/expected issues

-   Horizontal scrollbars appear on Toolbars.
    -   Where there isn't enough width to show all the buttons on a Toolbar, a horizontal scrollbar will appear. This issue will be resolved soon by a framework deliverable that will implement overflow behavior on Toolbars.
-   Random input control borders are missing at various zoom levels.
    -   This is a known issue and is tracked by 1721990.
-   Grids receive extra scrollbars, because the space that is available for the grid is less than the grid's minimum height (200 px).
    -   We have a future work item to investigate reducing/removing this minimum height.
-   When StaticText controls that have **SizeToAvailable** width are inside a group that also has **SizeToAvailable** width, horizontal scrollbars appear at some widths (Internet Explorer only).
    -   The browser has a calculation error that sometimes causes scrollbars to appear in this scenario.

## Appendix
### Information/guidelines about layout

For information about the layout properties, and for guidelines about scenarios that you should avoid, see the [Layout in Microsoft Dynamics AX](page-layout.md) page.

