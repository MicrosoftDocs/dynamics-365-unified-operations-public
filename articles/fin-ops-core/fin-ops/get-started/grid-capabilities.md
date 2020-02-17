---
# required metadata

title: Grid capabilities
description: This topic describes several powerful features of the grid control. The new grid feature must be enabled to have access to these capabilities. 
author: jasongre
manager: AnnBe
ms.date: 02/10/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form:  DefaultDashboard
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations, Core 
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: jasongre
ms.search.validFrom: 2020-02-29
ms.dyn365.ops.version: Platform update 33
---

# Grid capabilities

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

The new grid control provides a number of useful and powerful capabilities that can be used to enhance user productivity, construct more interesting views of your data, and get meaningful insights into your data. This article will cover the following capabilities: 

-  Calculating totals
-  Grouping data
-  Typing ahead of the system
-  Evaluating math expressions 

## Calculating totals
In Finance and Operations apps, users have the ability to see totals at the bottom of numeric columns in grids. These totals are shown in a footer section at the bottom of the grid. 

### Showing the grid footer
There is a footer area at the bottom of every tabular grid in Finance and Operations apps. The footer can show valuable information that is related to the data that appears in the grid. Here are some examples of this information:

- The number of selected rows in the table (when more than one record is selected)
- Grand totals at the bottom of configured, numeric columns
- The number of rows in the dataset 

This footer is hidden by default, but can be easily turned on. To show the footer for a grid, right-click on a column header in the grid and select the **Show footer** option. Once the footer has been turned on for a particular grid, that setting will be remembered until the user opts to hide the footer, which can be done by right-clicking on a column header and selecting **Hide footer**.  Note the placement of the **Show footer/Hide footer** action is expected to be re-located in a future update. 

### Specifying columns with totals
Currently, no columns will be configured to show totals by default. Instead, this is considered a one-time setup activity, similar to adjusting the widths of columns in grids. Once you specify that you want to see totals for a column, that setting will be remembered the next time you visit the page.  

There are two ways to configure a column to show a total: 

- Right-click in the column that you want to see a total for, and then select **Total this column**. This action causes three events to occur:

    1. The footer becomes visible. 
    2. Your preference for seeing a total for this column is saved. 
    3. A calculation of totals is initiated for this column and any other columns that you previously configured to see totals for. The time that is required to show a total depends on the size of the dataset that you're totaling.

- After the footer is visible, select **Show total** in the footer area at the bottom of the column that you want to see a total for. If there are no configured columns, the **Show total** button will be available for all numeric columns. 

    After at least one column is configured for totals, the **Show total** buttons will be available only on hover or focus. The action of selecting **Show total** just saves your preference for seeing a total in this column, so that the preference is applied during future visits to the page. In the footer, this state is indicated by a dash that appears in the column. (Alternatively, if the dataset is small enough, a total is immediately shown.)

If you make a mistake and no longer want to see a total in a particular column, right-click on the column and select **Hide total** or select the **Hide total** button in the footer in that column. This preference will also be saved for future visits to the page. 

### Calculating totals
When you come to a page with the footer visible and columns already configured for totals, totals may or may not be shown in the footer. The behavior is dependent on the size of the dataset on the page. If the dataset is sufficiently small, totals will be shown automatically, along with the number of rows in the dataset. If there are dashes in the footer under the columns you configured for totals, then the dataset is too large for the system to show totals immediately, and an explicit action is needed to calculate the totals. To do this, click the **Calculate** button in the footer, or right-click on a column you want a total for and select **Total this column**.  

If the calculation is taking too long, you can cancel the operation by selecting the **Cancel** button. Sometimes, however, the dataset will be too large to calculate totals (a limit imposed by your organization), and you will instead be notified to filter your data more.

Totals will update automatically as you update, delete, or create rows in the dataset.  

## Grouping data
Business users often need to perform ad-hoc analysis of data. While this can be done by exporting data to Microsoft Excel and using pivot tables, the **Grouping** capability in tabular grids allows users to organize their data in interesting ways within Finance and Operations apps. As this feature extends the **Totals** feature, **Grouping** also allows you to get meaningful insights into the data by providing subtotals at the group level.

To use this feature, right-click on the column you wish to group by, and select **Group by this column**. This action will sort the data by the selected column, add a new Group by column to the beginning to the grid, and insert "header rows" at the beginning of each group. These header rows provide the following information about each group: 
-  Data value for the group 
-  Column label (This information will be especially useful after multiple levels of grouping are supported.)
-  Number of data rows in this group
-  Subtotals for any column configured to show totals

With [Saved views](saved-views.md) enabled, this grouping can be saved by personalization as part of a view for quick access the next time you visit the page.  

If you select **Group by this column** for a different column, the original grouping is replaced, because only one level of grouping is supported in version 10.0.9 with Platform update 33.

To undo grouping in a grid, right-click on the grouping column and select **Ungroup**.  


## Evaluating math expressions
As a productivity booster, users can enter mathematical formulas in numeric cells in a grid. They don't have to do the calculation in an app outside the system. For example, if you enter **=15\*4** and then press the **Tab** key to move out of the field, the system will evaluate the expression and save a value of **60** for the field.

To make the system recognize a value as an expression, start the value with an equal sign (**=**). For more details on the supported operators and syntax, see [Supported math symbols](http://bugwheels94.github.io/math-expression-evaluator/#supported-maths-symbols).  
