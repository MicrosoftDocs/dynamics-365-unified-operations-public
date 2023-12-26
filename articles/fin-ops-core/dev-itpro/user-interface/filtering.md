---
title: Filtering options
description: This article explains the filtering options that are available.
author: jasongre
ms.date: 03/07/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: jasongre
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: f5501319-dcaa-4912-9456-97a0ef2c2452
---

# Filtering options

[!include [banner](../includes/banner.md)]

This article explains the filtering options that are available.

## Introduction

Microsoft Dynamics AX 2012 offers the following filtering options.

| Filter option                         | Description                                                                                                                                                                   |
|---------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Filter by grid                        | The user defines filter conditions in input fields below the grid column headers.                                                                                             |
| Filter by selection (filter by field) | The user selects a field value and uses that value as a filter condition.                                                                                                     |
| Advanced filter                       | The user opens a dialog box that contains advanced filtering options (filter on columns, not on the form; join additional data sources; sort by multiple columns; and so on). |

Finance and operations offers the following filtering options.

| Filter option         | Description                                                                                                                                |
|-----------------------|--------------------------------------------------------------------------------------------------------------------------------------------|
| Filter Pane           | An inline pane that slides in from the left, and that contains multiple filter criteria that can be applied to the targeted content.       |
| QuickFilter           | A framework-provided filtering mechanism that can appear above any list or grid, and that provides fast single-column filtering.           |
| Grid column filtering | The user can define filter conditions and perform single-column sorting by using a drop dialog that is opened from the grid column header. |
| Advanced filter or sort  | For most advanced filtering scenarios, the migrated **Advanced filter** form from Dynamics AX 2012 is still available.                     |

## Filter expressions
One important difference between filtering in finance and operations apps and filtering in Dynamics AX 2012 is related to the way that query symbols are used when filter values are defined (for example, "\*" to match 0 or more characters, or ".." to specify a range of values to match). In Dynamics AX 2012, these symbols are highly visible during the filtering experience. For example, for the filter by grid option, if a user selects the **contains** operator on a field, the system translates that operator by adding wildcard characters (\*) to each end of the current expression. In the current version, the query symbols are implied by the selected operator and aren't injected into the user interface. This makes filtering more intuitive and simpler for users. For users who want to specify additional filter conditions by using specific query symbols, or users who must enter more complex conditions, the **matches** operator is provided for each data type. For all other operators, the query symbols are interpreted as literals. For example, the filter condition "First name MATCHES A" finds all records where the first name starts with the letter A. However, the filter condition "First Name IS A\*" finds records where the first name is literally equal to "A\*." The following table shows how the client translates between finance and operations apps filter operators and Dynamics AX 2012 query syntax.

| Filter operator                      | Finance and operations apps query syntax |
|--------------------------------------|------------------------------------------|
| Is exactly “circle” /  Is equal to “circle”        | “circle”                                    |
| Is not “circle” / Is not equal to “circle” | “!circle”                                   |
| Is one of “circle”, “square”, “circlesquare”     | “circle,square,circlesquare”                         |
| Contains “circle”                       | “\*circle\*”                                |
| Does not contain “circle”               | “!\*circle\*”                               |
| Begins with “circle”                    | “circle\*”                                  |
| After “circle” / Greater than “circle”     | “&gt;circle”                                |
| Greater than or equal “circle”          | “circle..”                                  |
| Before “circle” / Less than “circle”       | “&lt;circle”                                |
| Less than or equal “circle”             | “..circle”                                  |
| Between “square” and “circle”              | “square..circle”                               |

Any query syntax that doesn't match the preceding templates is interpreted as the **matches** operator.

### Other frequent filter expressions
Users may want to filter for blank values in column. While there is no filter operator for this specifically, the syntax for performing this filtering remains the same as Dynamics AX 2012. With either the **matches** operator or the **is equal to** operator, users can type **""** to retrieve rows with blank values for the current column. For example, **First Name IS ""** will find all records where the first name is blank. Note that "" only matches rows where the column value is the empty string and does not match rows where the column value is NULL or 0.

Users may also want to filter for records that do not belong to a specific list of values. While "is not one of" is not a filter operator, this filter expression can be achieved using the **matches** operator by negating each list item in the list. For example,  **!circle, !square** will find all records that are neither "circle" nor "square." 
    
## Filter Pane
The Filter Pane provides an easy-to-use interface for filtering full page lists. The Filter Pane is an inline pane that slides in from the left side of the screen and pushes the page content to the right, so that users can see the data that they want to filter. Users open this filter mechanism by clicking the system-defined **Show filters** button on the left side of the page. After it has been opened, the Filter Pane remains visible until the user goes to a new page, or until the user closes the Filter Pane by using the **Hide filters** button.

### When is the Filter Pane available?

Currently, the Filter Pane is available for all forms except the following forms:

-   Drop dialogs
-   Dialogs
-   Enhanced previews
-   Lookups
-   Form parts
-   Parts
-   Table of contents form type
-   Forms that have no data sources

**Note:** The availability of the Filter Pane on particular forms and form types is evolving, so this list might change.

### What data does the Filter Pane work on?

Because the Filter Pane is targeted at full page lists, it works only on the tables and fields that are directly joined (by inner/outer joins) to the first master data source on the form. This filtering mechanism isn't intended for filtering on secondary collections, or for filtering on other root data sources and their directly joined data sources. Other filtering mechanisms (QuickFilter, grid column filtering, and so on) are available to meet these other requirements.

### What fields are initially shown in the Filter Pane?

Here is how the fields that are initially shown in the Filter Pane are selected:

1.  All ranges/filters that currently exist on the query (only non-hidden filters/ranges are shown) are used.
2.  If no ranges filters currently exist on the query, the fields from the primary index from the first master data source are used.
3.  If there are no fields from the primary index from the first master data source, the TitleFields that are defined directly on the first master data source are used.  If no TitleFields are defined, no default fields are shown. (Currently, if the first master data source extends another table (for example, table B), we don't show the TitleFields from table B. However, we plan to add that check in the future.)

### Can I control the default fields that appear in the Filter Pane?

Developers can make sure that a particular field appears in the Filter Pane by adding an empty filter for that field to the query. For an example, see the **FmCustomer** form, which adds the filters post super() in form init(). Note that after an empty field has been added to guarantee that it appears in the Filter Pane, the fields in the Filter Pane will always be those that are explicitly on the query, and will never be the TitleFields or fields from the primary index on the first master data source.

### I don’t want users to be able to filter on a specific field or modify an existing filter. How do I accomplish this?

Developers can affect whether users can modify/add filters on certain fields by changing the status of the filters. The allowed values are in the **RangeStatus** enum:

1.  **Open (default)** – The user can see and modify this filter.
2.  **Locked** – The user can see the filter value but can't modify it. The user also can't add another filter on this column.
3.  **Hidden** – The user can't see that there is a filter on this column. The user also can't add another filter on this column.

### Can I control the fields that appear in the Add a filter field list in the Filter Pane?

The fields that appear in the **Add a filter field** list are all the filterable fields from the query that involves the first master data source on the form. Therefore, developers can't control the fields that appear in this list. Usually, if you see unexpected fields or can't find the fields that you want to filter on, the fields that you're expecting are either on a different master data source (not the first) or on a child collection.

### How is the Filter Pane used?

The Filter Pane is simple and straightforward to use. First, select a filtering operator in the list that is associated with each filter field. Note that the set of operators that appears depends on the data type of the field. Then enter an appropriate value for the filter condition, and click **Apply**. The form is updated based on the filter criteria that you specified.

## QuickFilter
In Dynamics AX 2012, the QuickFilter was a framework control that was automatically added only to list pages. In finance and operations apps, the QuickFilter is now a modeled control that can be associated with any grid in the system. As the user starts to type, a column selector drop-down appears to guide the user toward the column that the filter will be applied to. The developer can also specify the default column for the QuickFilter. If no column is specified by the developer, the default column is the first field that can be filtered in the grid. [![QuickFilter control.](./media/3_filter.png)](./media/3_filter.png)

### Why don't I have a column selector in my QuickFilter?

Column selectors are shown only for QuickFilters that are attached to grids. If you don't see a column selector, the most likely reason is that the **TargetControl** property on the QuickFilter is blank. This property must point to the grid that it should operate on. If the **TargetControl** property is set correctly, but you don't see a column selector, you might not have any filterable columns in your grid. In addition to non-text controls (such as images), controls that are bound to data methods aren't filterable.

### Can I use the QuickFilter to filter other collection controls (such as trees)?

Yes, you can use the QuickFilter to filter other collection controls, but you must manually wire up the filtering. Here are the general steps:

-   Leave the **TargetControl** property blank.
-   Override the **applyFilter()** method on the QuickFilter.
-   Write code in that method to perform the desired filtering.

## Grid column header filtering/sorting
In finance and operations apps, the grid filtering experience is more closely aligned with the experience in Microsoft Excel. When the user clicks a column header, a drop-down dialog appears, and the user can use it to filter the column. The filtering experience here mimics the filtering experience in the Filter pane. Additionally, there are options to sort the grid based on the column that is currently selected.

> [!NOTE]
> Some columns in a grid may not be filterable. In these cases, the column header will not be clickable. From a technical perspective, only columns corresponding to fields in a SQL table can be filtered on or sorted. Columns whose values are computed via code are not filterable or sortable using grid column headers, the Filter pane, QuickFilter, or Advanced filter or sort. 

[![Example of grid filtering.](./media/4_filter.png)](./media/4_filter.png)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

