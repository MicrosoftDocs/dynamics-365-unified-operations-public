---
# required metadata

title: Grid capabilities
description: This topic describes several powerful features of the grid control. The new grid feature must be enabled to have access to these capabilities. 
author: jasongre
manager: AnnBe
ms.date: 04/23/2020
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

This footer is hidden by default but can be easily turned on. To show the footer for a grid, right-click on a column header in the grid and select the **Show footer** option. Once the footer has been turned on for a particular grid, that setting will be remembered until the user opts to hide the footer, which can be done by right-clicking on a column header and selecting **Hide footer**.  Note the placement of the **Show footer/Hide footer** action is expected to be re-located in a future update. 

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

## Typing ahead of the system
In many business scenarios, the ability to quickly enter data into the system is very important. Before the new grid control was introduced, users could change data only in the current row. Before they could create a new row or switch to a different row, they were forced to wait for the system to successfully validate any changes. In an attempt to reduce the amount of time that users wait for these validations to be completed, and to improve user productivity, the new grid adjusts these validations so that they are asynchronous. Therefore, the user can move to other rows to make changes while previous row validations are pending. 

To support this new behavior, a new column for the row status has been added to the top of the grid when the grid is in edit mode. This column indicates one of the following statuses:

- **Blank** – No status image indicates that the row has been successfully saved by the system.
- **Processing pending** – This status indicates that the changes in the row haven't yet been saved by the server but are in a queue of changes that must be processed. Before you take action outside the grid, you must wait for all the pending changes to be processed. Additionally, the text in these rows is italicized to indicate the unsaved status of the rows. 
- **Validation warning** – This status indicates that the system can't save the changes in the row because of some validation issue. In the old grid, were you forced back into the row to fix the issue immediately. However, in the new grid, you're notified that a validation issue was encountered, but you can decide when you want to fix any issues in the row. When you're ready to fix the issue, you can manually move focus back to the row. Alternatively, you can select the **Fix this issue** action. This action immediately moves focus back to the row that has the issue, and lets you make edits inside or outside the grid. Note that the processing of subsequent pending rows is stopped until this validation warning is resolved. 
- **Paused** – This status indicates that processing by the server is paused because validation of the row triggered a pop-up dialog box that requires user input. Because the user might be entering data in some other row, the pop-up dialog box isn't immediately presented to that user. Instead, it will be presented when the user chooses to resume processing. This status is accompanied by a notification that informs the user about the situation. The notification includes a **Resume processing** action that will trigger the pop-up dialog box.  
    
When users are entering data ahead of the place where the server is processing, they can expect a few degradations in the data entry experience, such as a lack of lookups, control-level validation, and entry of default values. Users who need a drop-down list to find a value are encouraged to wait for the server to catch up to the current row. Control-level validation and entry of default values will also occur when the server processes that row.   

### Pasting from Excel
Users have always been able to export data from grids in Finance and Operations apps to Excel by using the **Export to Excel** mechanism. However, the ability to enter data ahead of the system enables the new grid to support copying tables from Excel and pasting them directly into grids in Finance and Operations apps. The grid cell that the paste operation is initiated from determines where the copied table begins to be pasted in. The contents of the grid are overwritten by the contents of the copied table, except in two cases:

- If the number of columns in the copied table exceeds the number of columns that remain in the grid, starting from the paste location, the user is notified that the extra columns have been ignored. 
- If the number of rows in the copied table exceeds the number of rows in the grid, starting from the paste location, the existing cells are overwritten by the pasted content, and any extra rows from the copied table are inserted as new rows at the bottom of the grid. 

## Evaluating math expressions
As a productivity booster, users can enter mathematical formulas in numeric cells in a grid. They don't have to do the calculation in an app outside the system. For example, if you enter **=15\*4** and then press the **Tab** key to move out of the field, the system will evaluate the expression and save a value of **60** for the field.

To make the system recognize a value as an expression, start the value with an equal sign (**=**). For more information about the supported operators and syntax, see [Supported math symbols](http://bugwheels94.github.io/math-expression-evaluator/#supported-maths-symbols).

## Frequently asked questions
### How do I enable the new grid control in my environment? 

**10.0.9 / Platform update 33 and later**
The **New grid control** feature is available directly in Feature management in any environment. Like other public preview features, enabling this feature in production is subject to the [Supplemental Terms of Use Agreement](https://go.microsoft.com/fwlink/?linkid=2105274).  

**10.0.8 / Platform update 32 and 10.0.7 / Platform update 31**
The **New grid control** feature can be enabled in Tier 1 (Dev/Test) and Tier 2 (Sandbox) environments in order to provide additional testing and design changes by following the steps below.

1.	**Enable the flight**: Execute the following SQL statement: 

    `INSERT INTO SYSFLIGHTING (FLIGHTNAME, enabled, FLIGHTSERVICEID, PARTITION) VALUES('CLIReactGridEnableFeature', 1, 0, 5637144576);`

2. **Reset IIS** to flush the static flighting cache. 

3.	**Find the feature**: Go to the **Feature management** workspace. If **New grid control** does not appear in the list of all features, select **Check for updates**.   

4.	**Enable the feature**: Find the **New grid control** feature in the list of features, and select **Enable now** on the details pane. Note that a browser refresh is required. 

All subsequent user sessions will start with the new grid control enabled.

## Known issues
This section maintains a list of known issues for the new grid control while the feature is in a preview state.  

### Open issues

- Card lists that were rendered as multiple columns are now rendered as a single column.
- Grouped lists aren't rendered as groups or in separate columns.
- Tooltips aren't shown for images.
- The gridlines display doesn't work for all field types.
- Intermittently, you can't click outside the grid after you multi-select some rows.
- The **Validate** and **Copy** Task recorder options aren't available for date/number controls.

### Fixed as part of 10.0.12

> [!Note]
> The following information is being provided so that you can plan accordingly. For more information about the targeted release schedule of version 10.0.12, see [Service update availability](../../fin-ops/get-started/public-preview-releases.md).

- [Issue 429126] Controls outside the grid aren't updated after the last record is deleted.
- [Issue 430575] Table controls don't update the contents of displayed items.
- [KB 4558570] Items are still shown on the page after the record has been deleted.
- [KB 4558584] Negative numbers aren't rendered correctly.
- [KB 4558575] Fields aren't updated after a row change / Grid processing becomes stuck after row deletion.
- [Issue 436980] Styling that is associated with the List Panel **ExtendedStyle** isn't applied.
- [KB 4558573] Validation errors can't be fixed when the required change is outside the grid.
	
### Quality update for 10.0.11

- [KB 4558381] Negative numbers aren't rendered correctly / Users sometimes become stuck after validation issues are encountered.

### Fixed as part of 10.0.11

- [KB 4558374] Records that require a polymorphic selector dialog box can't be created.
- [KB 4558382] Unexpected client errors occur.
- [KB 4558375] Help text isn't shown on columns in the new grid.
- [KB 4558376] List Panel grids aren't rendered at the correct height in Internet Explorer.
- [KB 4558377] Combo box columns that have **SizeToAvailable** width aren't rendered on some pages.
- [KB 4549711] Lines in a payment proposal can't be removed correctly after the new grid control is enabled.
- [KB 4558378] Drill-through sometimes opens the wrong record.
- [KB 4558379] An error occurs when lookups are opened where **ReplaceOnLookup**=**No**.
- [KB 4558380] The available space in the grid isn't filled immediately after part of the page is collapsed.
- [Issue 432458] Empty or duplicated lines are shown at the beginning of some child collections.
- [KB 4558587] Reference groups that have combo boxes for replacement fields don't show values.

### Fixed as part of 10.0.10

- [Issue 414301] Some data from previous lines disappears when new lines are created.
- [KB 4550367] Time values aren't formatted correctly.
- [KB 4549734] Active rows aren't treated as marked if the marking column is hidden.
- [Bug 417044] There is no empty grid message for list-style grids.
- [KB 4558367] Text selection is inconsistent when rows are changed.
- [KB 4558372] The new grid becomes stuck in processing mode if the number of columns in content that is pasted in exceeds the number of remaining columns in the grid.
- [KB 4558368] Multi-select via the keyboard is allowed in single-select scenarios.
- [KB 4539058] Some grids (typically on FastTabs) sometimes aren't rendered (but they will be rendered if you zoom out).
- [KB 4558369] Status images disappear in the hierarchical grid.
- [KB 4558370] A new row isn't scrolled into view.
- [KB 4549796] Values can't be edited in a grid when it's in view mode.

### Quality update for 10.0.9/Platform update 33

- [KB 4550367] Time values aren't formatted correctly.
