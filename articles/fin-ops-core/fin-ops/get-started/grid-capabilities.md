---
# required metadata

title: Grid capabilities
description: This topic describes several powerful features of the grid control. You must enable the new grid feature to have access to these capabilities. 
author: jasongre
ms.date: 04/25/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  DefaultDashboard
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
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

The new grid control provides several useful and powerful capabilities that you can use to enhance user productivity, construct more interesting views of your data, and get meaningful insights into your data. This article will cover the following capabilities: 

- Calculating totals
- Typing ahead of the system
- Evaluating math expressions 
- Grouping tabular data (enabled separately by using the **Grouping in grids** feature)
- Freezing columns (enabled separately by using the **Freezing columns in grids** feature)
- Autofit column width
- Stretchable columns

## Calculating totals
In Finance and Operations apps, users have the ability to see totals at the bottom of numeric columns in grids. A footer section at the bottom of the grid shows these totals. 

### Showing the grid footer
There is a footer area at the bottom of every tabular grid in Finance and Operations apps. The footer can show valuable information that is related to the data that appears in the grid. Here are some examples of this information:

- The number of selected rows in the table (when you select more than one record)
- Grand totals at the bottom of configured, numeric columns
- The number of rows in the dataset 

This footer is hidden by default, but you can turn it on. To show the footer for a grid, select the **Grid options** button in the grid header, and then select the **Show footer** option. After you turn on the footer for a particular grid, that setting will be remembered until the user chooses to hide the footer. To hide the footer, select **Hide footer** on the **Grid options** menu.

### Specifying columns with totals
Currently, no columns show totals by default. Instead, this is considered a one-time setup activity, similar to adjusting the widths of columns in grids. Once you specify that you want to see totals for a column, that setting will be remembered the next time you visit the page.

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

If the calculation takes a long time to complete, you can cancel the operation by selecting the **Cancel** button. Sometimes, the dataset will be too large to calculate totals (a limit imposed by your organization), and you will instead be notified to filter your data more. 

> [!NOTE]
> System administrations can modify the limit for the number of records available for calculating totals by adjusting the **Maximum number of local records for each grid** parameter on the **Client performance options** page. The default value is 25,000 records. Administrators should be careful when adjusting this value because a value that is too large can exhaust the available memory on the user's machine. The recommendation is to not exceed 50,000 records.   

Totals will update automatically as you update, delete, or create rows in the dataset.

## Typing ahead of the system
In many business scenarios, the ability to quickly enter data into the system is very important. Before the new grid control was introduced, users could change data only in the current row. Before they could create a new row or switch to a different row, they were forced to wait for the system to successfully validate any changes. In an attempt to reduce the amount of time that users wait for these validations to be completed, and to improve user productivity, the new grid adjusts these validations so that they are asynchronous. Therefore, the user can move to other rows to make changes while previous row validations are pending. 

To support this new behavior, a new column for the row status has been added to the right of the row selection column when the grid is in edit mode. This column indicates one of the following statuses:

- **Blank** – No status image indicates that the row has been successfully saved by the system.
- **Processing pending** – This status indicates that the changes in the row haven't yet been saved by the server but are in a queue of changes that must be processed. Before you take action outside the grid, you must wait for all the pending changes to be processed. Additionally, the text in these rows is italicized to indicate the unsaved status of the rows. 
- **Invalid state** – This status indicates that some warning or message was triggered during the processing of the row, and it might have prevented the system from saving the changes in that row. In the old grid, if the save operation was unsuccessful, you were forced back into the row to fix the issue immediately. However, in the new grid, you're notified that a validation issue was encountered, but you can decide when you want to fix any issues in the row. When you're ready to fix an issue, you can manually move focus back to the row. Alternatively, you can select the **Fix this issue** action. This action immediately moves focus back to the row that has the issue, and lets you make edits inside or outside the grid. Note that the processing of subsequent pending rows is stopped until this validation warning is resolved. 
- **Paused** – This status indicates that processing by the server is paused because validation of the row triggered a pop-up dialog box that requires user input. Because the user might be entering data in some other row, the pop-up dialog box isn't immediately presented to that user. Instead, it will be presented when the user chooses to resume processing. This status is accompanied by a notification that informs the user about the situation. The notification includes a **Resume processing** action that will trigger the pop-up dialog box.

When users are entering data ahead of the place where the server is processing, they can expect a few degradations in the data entry experience, such as a lack of lookups, control-level validation, and entry of default values. Users who need a drop-down list to find a value are encouraged to wait for the server to catch up to the current row. Control-level validation and entry of default values will also occur when the server processes that row.

### Pasting from Excel
Users have always been able to export data from grids in Finance and Operations apps to Microsoft Excel by using the **Export to Excel** mechanism. However, the ability to enter data ahead of the system enables the new grid to support copying tables from Excel and pasting them directly into grids in Finance and Operations apps. The grid cell that the paste operation is initiated from determines where the copied table begins to be pasted in. The contents of the grid are overwritten by the contents of the copied table, except in two cases:

- If the number of columns in the copied table exceeds the number of columns that remain in the grid, starting from the paste location, the user is notified that the extra columns have been ignored. 
- If the number of rows in the copied table exceeds the number of rows in the grid, starting from the paste location, the existing cells are overwritten by the pasted content, and any extra rows from the copied table are inserted as new rows at the bottom of the grid. 

## Evaluating math expressions
As a productivity booster, users can enter mathematical formulas in numeric cells in a grid. They don't have to do the calculation in an app outside the system. For example, if you enter **=15\*4** and then press the **Tab** key to move out of the field, the system will evaluate the expression and save a value of **60** for the field.

To make the system recognize a value as an expression, start the value with an equal sign (**=**). For more information about the supported operators and syntax, see [Supported math symbols](http://bugwheels94.github.io/math-expression-evaluator/#supported-maths-symbols).

## Grouping tabular data
Business users often need to perform ad-hoc analysis of data. While this can be done by exporting data to Microsoft Excel and using pivot tables, the **Grouping in grids** feature, which is dependent on the new grid control feature, allows users to organize their tabular data in interesting ways within Finance and Operations apps. Because this feature extends the **Totals** feature, **Grouping** allows you to get meaningful insights into the data by providing subtotals at the group level.

To use this feature, right-click the column that you want to group by, and select **Group by this column**. This action will sort the data by the selected column, add a new **Group by** column to the beginning of the grid, and insert "header rows" at the beginning of each group. These header rows provide the following information about each group:

- Data value for the group 
- Column name (this information is especially useful when you have multiple levels of grouping)
- Number of data rows in this group
- Subtotals for any column configured to show totals

With [Saved views](saved-views.md) enabled, you can save grouping as part of a view on pages that allow queries to be saved to views. For example, those with large view selectors. See the [Switching between views](saved-views.md#switching-between-views) section for more details. 

### Multiple levels of grouping
After you've grouped data by a single column, you can group the data by a different column by selecting **Group by this column** on the desired column. This process can be repeated until you have 5 nested levels of grouping, which is the maximum supported depth. At this point, you will no longer be able to group by additional columns.

At any point, you can remove the grouping on any column by right-clicking that column and selecting **Ungroup**. You can also remove the grouping from all columns by selecting **Grid options** and then **Ungroup all**.

### Sorting grouped data
After you group data by one or more columns, you can change the sort direction for any grouping column through the corresponding column header. 

The behavior when you sort on non-grouped columns depends on your product version:

- In version 10.0.24 and earlier, if you sort on a non-grouped column, the grouping is removed from all columns, and the data is sorted on the selected column. 
- In version 10.0.25 and later, if you sort on a non-grouped column, the grouping remains intact, and the data is sorted inside each group, based on the selected column.

### Expanding and collapsing groups
The initial grouping of data will have all groups expanded. You can create summarized views of the data by collapsing individual groups, or you can use group expanding and collapsing to assist in navigating through the data. To expand or collapse a group, select the chevron (>) button in the corresponding group header row. Note that the expand/collapse state of individual groups is **not** saved in personalization.

### Selecting and unselecting rows at the group level
In the same way that you can select (or unselect) all rows in the grid by selecting the check box at the top of the first column in the grid, you can also quickly select (or unselect) all the rows in a group by selecting the check box in the corresponding group header row. The check box in the group header row will always reflect the current selection state of rows in that group, regardless of whether all rows are selected, no rows are selected, or only some rows are selected.

### Hiding column names
When grouping data, the default behavior is to show the column name in the group header row. You can choose to suppress the column name in group header rows by selecting **Grid options** > **Hide group column name**.

### Grouping on date and time columns
As of version 10.0.24, for Date or DateTime fields, the option has been added to group by year, month, or day. The group "value" in the corresponding header row will match the format from that field. Additionally, for DateTime and Time fields, you can group by hour, minute, or second. 

## Freezing columns
Some columns in a grid might be important enough for context that you don't want them to scroll out of view. Instead, you might want the values in those columns to always be visible. The **Freezing columns in grid** feature provides this flexibility to users. 

To freeze a column, right-click in the column's header, and then select **Freeze column**. The first time that you complete this step, the selected column becomes the first column and will no longer scroll out of view. Any subsequent column that you freeze will be added to the right of the last frozen column. You can use the standard Move functionality to reorder frozen columns as you require. However, frozen columns can't be moved so that they appear among the set of unfrozen columns. Likewise, unfrozen columns can't be moved so that they appear among the set of frozen columns.

To unfreeze a column, right-click in the frozen column's header, and then select **Unfreeze column**. 

Note that the row selection and row status columns in the new grid are always frozen as the first two columns. Therefore, when these columns are included in a grid, they will always be visible to users, regardless of the horizontal scroll position in the grid. These two columns can't be reordered.

## Autofit column width
Similar to Excel, users can automatically force a column to resize based on the content currently shown in that column. To do this, double click on the sizing handles in the column, or by putting focus into the column header and pressing **A** (for autofit). This capability is available starting in version 10.0.23.

## Frequently asked questions
### How do I enable the new grid control in my environment? 

The **New grid control** feature is available directly in Feature management in any environment. After enabling the feature in Feature management, all subsequent user sessions will utilize the new grid control. 

This feature is enabled by default starting in version 10.0.21 and is targeted to become mandatory in October 2022.  

## [Developer] Opting out individual pages from using the new grid 
If your organization discovers a page that has some issues utilizing the new grid, an API is available to allow an individual form to use the legacy grid control while still permitting the rest of the system to utilize the new grid control. To opt out an individual page from the new grid, add the following call post `super()` in the `run()` method for the form.

```this.forceLegacyGrid();```

This API will be honored until the new grid control becomes mandatory. That change is currently targeted for October 2022. If any issues require that this API be used, report them to Microsoft.

### Forcing a page to use the new grid after previously opting out the grid
If you have opted out an individual page from using the new grid, you might want to later re-enable the new grid after the underlying issues were solved. To do this, you simply need to remove the call to `forceLegacyGrid()`. The change will not take effect until one of the following occurs:

- **Environment redeployment**: When an environment is updated and redeployed, the table that stores the pages that have opted out of the new grid (FormControlReactGridState) is automatically cleared.
- **Manual clearing of the table**: For development scenarios, you will need to use SQL to clear the FormControlReactGridState table and then restart the AOS. This combination of actions will reset the caching of pages that have opted out of the new grid.

## [Developer] Opting individual grids out of the Typing ahead of the system capability
Some scenarios have arisen that don't lend themselves to working well with the *Typing ahead of the system* capability of the grid. (For example, some code that is triggered when a row is validated causes a datasource research to be triggered, and the research can then corrupt uncommitted edits on existing rows.) If your organization discovers such a scenario, an API is available that lets a developer opt an individual grid out of asynchronous row validation and revert to the legacy behavior.

When asynchronous row validation is disabled in a grid, users can't create a new row or move to a different existing row in the grid while there are validation issues on the current row. As a side effect of this action, tables can't be pasted from Excel into Finance and Operations grids.

To opt an individual grid out of asynchronous row validation, add the following call after `super()` in the `run()` method of the form.

```<gridControl>.allowPreemptiveClient(false);```

> [!NOTE]
> - This call should be invoked only in exceptional cases and should not be the norm for all grids.
> - We don't recommend that you toggle this API at runtime after the form loads.

## [Developer] Size-to-available-width columns
If a developer sets the **WidthMode** property to **SizeToAvailable** for columns inside the new grid, those columns initially have the same width that they would have if the property were set to **SizeToContent**. However, they stretch to use any extra available width inside the grid. If the property is set to **SizeToAvailable** for multiple columns, all those columns share any extra available width inside the grid. However, if a user manually resizes one of those columns, the column becomes static. It will remain at that width and will no longer stretch to take up extra available grid width.

## Known issues
This section maintains a list of known issues for the new grid control.

### Open issues
- After enabling the **New grid control** feature, some pages will continue to utilize the existing grid control. This will happen in the following situations:
 
    - A card list exists on the page that is rendered in multiple columns.
    - A grouped card list exists on the page.
    - A grid column with a non-react extensible control.

    When a user first encounters one of these situations, a message will display about refreshing the page. After this message appears, the page will continue to utilize the existing grid for all users until the next product version update. Better handling of these scenarios, so that the new grid can be utilized, will be considered for a future update.

- [KB 4582758] Records are blurry when you change zoom from 100 to any other percentage
- [KB 4592012] Unexpected client error in IE11 when pasting multiple lines from Excel

    Microsoft is not pursuing a fix for this issue


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
