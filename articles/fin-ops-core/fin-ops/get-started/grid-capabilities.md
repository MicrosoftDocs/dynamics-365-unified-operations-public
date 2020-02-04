---
# required metadata

title: Grid capabilities
description: This topic describes several powerful features of the grid control. The new grid feature must be enabled to have access to these capabilities. 
author: jasongre
manager: AnnBe
ms.date: 01/20/2020
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
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Platform update 33
---

# Grid capabilites

[!include [banner](../includes/banner.md)]

The new grid control provides a number of useful and powerful capabilities that can be used to enhance user productivity, construct more interesting views of your data, and get meaningful insights into your data. This article will cover the following capabilities: 

-  Calculating totals
-  Grouping data
-  Typing ahead of the system
-  Evaluating math expressions 

## Calculating totals
In Finance and Operations apps, users have the ability to see totals at the bottom of numeric columns in grids. These totals are shown in a footer section at the bottom of the grid. 

### Showing the grid footer
Every tabular grid in the Finance and Operations apps has a footer area at the bottom of the grid that can show valuable information related to the data being displayed. This information includes: 
-  The number of selected rows in the table (when more than one record is selected)
-  Grand totals at the bottom of configured numeric columns
-  The number of rows in the dataset 

This footer is hidden by default, but can be easily turned on. To show the footer for a grid, right-click on a column header in the grid and select the **Show footer** option. Once the footer has been turned on for a particular grid, that setting will be remembered until the user opts to hide the footer, which can be done by right-clicking on a column header and selecting **Hide footer**.  Note the placement of the **Show footer/Hide footer** action is expected to be re-located in a future update. 

### Specifying columns with totals
Currently, no columns will be configured to show totals by default. Instead, this is considered a one-time setup activity, similar to adjusting the widths of columns in grids. Once you specify that you want to see totals for a column, that setting will be remembered the next time you visit the page.  

There are two ways to configure a column to show a total: 
1.	Right-click on the column you are interested in seeing a total for and select **Total this column**. This action will do three things. First, it will make the footer visible. Second, it will save your preference for seeing a total on this column. Third, this action will initiate a totals calculation for this column and any others you’ve previously configured to see totals. The time it takes for a total to be shown is directly related to the size of the dataset you are totalling.  

2.	Once the footer has been shown, you can alternatively click on the **Show total** button in the footer region at the bottom of the column you are interested in seeing a total for. If there are no configured columns, then the **Show total** button will be visible for all numeric columns. Once there is at least one column configured for totals, the **Show total** buttons will only be available on hover or focus. This action simply saves your preference for seeing a total in this column for future visits to this page, and this state is indicated by the dash that appears in this column in the footer (or a total will show immediately if the dataset is sufficiently small).

If you make a mistake and no longer want to see a total in a particular column, right-click on the column and select **Hide total** or select the **Hide total** button in the footer in that column. This preference will also be saved for future visits to the page. 

### Calculating totals
When you come to a page with the footer visible and columns already configured for totals, totals may or may not be shown in the footer. The behavior is dependent on the size of the dataset on the page. If the dataset is sufficiently small, totals will be shown automatically, along with the number of rows in the dataset. If there are dashes in the footer under the columns you configured for totals, then the dataset is too large for the system to show totals immediately, and an explicit action is needed to calculate the totals. To do this, click the **Calculate** button in the footer, or right-click on a column you want a total for and select **Total this column**.  

If the calculation is taking too long, you can cancel the operation by selecting the **Cancel** button. Sometimes, however, the dataset will be too large to calculate totals (a limit imposed by your organization), and you will instead be notified to filter your data more.

Totals will update automatically as you update, delete, or create rows in the dataset.  

## Grouping data
Business users often need to perform ad-hoc analysis of data. While this can be done by exporting data to Microsoft Excel and using pivot tables, the **Grouping** capability in tabular grids allows users to organize their data in interesting ways within Finance and Operations apps. As this feature extends the **Totals** feature, **Grouping** also allows you to get meaningful insights into the data by providing subtotals at the group level.

To use this feature, right-click on the column you wish to group by, and select **Group by this column**. This action will sort the data by the selected column, add a new Group by column to the beginning to the grid, and insert “header rows” at the beginning of each group. These header rows provide the following information about each group: 
-  Data value for the group 
-  Column label. This will be particularly useful once multiple levels of grouping is supported.  
-  Number of data rows in this group
-  Subtotals for any column configured to show totals

With [Saved views](saved-views.md) enabled, this grouping can be saved by personalization as part of a view for quick access the next time you visit the page.  

If you select **Group by this column** on a different column, the original grouping will be replaced, as only level of grouping is supported in 10.0.9 / Platform update 33.

To undo grouping in a grid, right-click on the grouping column and select **Ungroup**.  


## Evaluating math expressions
As a productivity booster, user can enter mathematical formulae into numeric cells in a grid, instead of having to do the calculation in an app outside the system. For example, you can enter **=15\*4** and tab out of the field. The system will evaluate the expression and save a value of “60” for the field.

To make the system recognize a value as an expression, start the value with an equal sign (**=**). For more details on the supported operators and syntax, see [Supported math symbols](http://redhivesoftware.github.io/math-expression-evaluator/#supported-maths-symbols).  
