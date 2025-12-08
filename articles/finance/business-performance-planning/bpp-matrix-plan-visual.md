---
title: Matrix planning visual in Business performance planning
description: Learn the recommended practices to improve performance and responsiveness when using the Matrix planning visual.
author: twheeloc
ms.author: romainpham
ms.topic: overview
ms.date: 12/08/2025
ms.reviewer: twheeloc
ms.collection: get-started

---

# Matrix planning visual in Business performance planning

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

The Matrix planning visual is the default planning visual available in Business performance planning. It enables users to enter, adjust, and allocate data directly in Power BI reports, with automatic write-back to Dataverse tables. This visual supports both top-down and bottom-up planning at any level of detail, making it ideal for financial, operational, and workforce planning scenarios.

## Overview

Use the Matrix planning visual to create and manage comprehensive planning and forecasting scenarios in an intuitive, spreadsheet-like interface. Changes made in the visual are instantly validated and written back to Dataverse, keeping your planning data synchronized across the organization.

### Key capabilities

- Direct data entry - Enter or edit values directly in the Power BI report.  
- Allocation logic - Perform top-down or bottom-up allocations.  
- Drilldown flexibility - Navigate from summary to detail level while maintaining context.  
- Conditional formatting - Highlight trends, exceptions, and KPI thresholds visually.  
- Advanced calculations - Use custom aggregations, relative changes, and validations.  
- Collaboration support - Add comments or lock cells for control and governance.  
- Persistent state - Maintain your drill position and view state when refreshing the report.  
- Excel interoperability - Copy and paste data seamlessly between Power BI and Excel.

### Build a Matrix planning visual

To build a Matrix planning visual, follow these steps:

1. In Power BI Desktop, select the **Matrix planning** visual from the **Business performance planning visuals** pane.  
1. Drag and drop your data fields into the following areas:
   - **Rows** - The hierarchy or dimension you want to display as row headers. For example, Account or Cost center.  
   - **Columns** - The hierarchy or dimension you want to show across columns. For example, Period or Scenario.  
   - **Values** - The measure or amount to plan. For example, Budget amount.  
   - **Filter measure** recommended - Add a measure that limits the dataset retrieved for better performance.

> [!NOTE]
> Always define a **Filter measure**. Without it, Power BI retrieves unfiltered data, which causes long rendering times.

### Granularity and dimensional selection

When performing data entry or write-back in the Matrix visual, include at least one field from each dimension defined in your cube. This approach ensures that the update happens at the correct level of granularity in Dataverse.

### Example cube structure

Consider a cube built with the following dimensions:

- **Account**
- **Cost center**
- **Period**
- **Scenario**

Each dimension contains several fields:

| Dimension     | Example fields                                                                 |
|---------------|--------------------------------------------------------------------------------|
| **Account**   | `msdyn_name` (Account code), `Account Type`, `Account Category`, `PnL Category` |
| **Cost center** | `msdyn_name` (Cost center code), `Cost Center Group`                          |
| **Period**    | `msdyn_name` (Month_Year), `Month`, `Quarter`, `Year`                          |
| **Scenario**  | `Version`, `Scenario Type`                                                    |

To enable write-back, select at least one field from each dimension. The field doesn't need to be the key field (`msdyn_name`). You can use any descriptive or grouped field in the Matrix visual, such as Account category or PnL category.

---

### Write-back granularity

When you edit data, Business performance planning determines the update granularity based on the fields you select in the Matrix visual:

- If you use **Account Code (`msdyn_name`)**, the system writes updates at the most detailed level - one record per account code.  
- If you use a grouping field, like Account category, the system allocates the update to all account codes that belong to that group:
  - If there's only one account code in that category, the system applies the entire amount to that account.  
  - If multiple account codes already have values, the system distributes the update proportionally to their existing values.  
  - If no existing values are found, the system allocates the update equally across all account codes in the category.  

This behavior ensures planning remains consistent and correctly aggregated across different levels of detail.

### Example

Suppose your visual includes the following fields:
- Rows: Account category  
- Columns: Month  
- Drivers: Amount  

You enter a new value of 60,000 under Account category = OTHEREMPEXP for **January**.  

| Account category | Jan    | Feb | Mar |
|-------------------|--------|-----|-----|
| OTHEREMPEXP       | 60,000 |     |     |

Business performance planning processes this update as follows:

- It identifies all account codes under the **OTHEREMPEXP** category.  
- It distributes the 60,000 across those accounts:
  - If there's one account, it assigns all 60,000 to that account.  
  - If there are multiple accounts with existing values, it distributes the amount proportionally based on their prior amounts.  
  - If there are multiple accounts without values, it divides the 60,000 equally across those accounts.  

After saving, you can drill down to the account code level to see the distributed results.

> [!IMPORTANT]
> Write-back updates always occur at the granularity represented in the visual. For example, if your visual shows only Account category and Month, Business performance planning allocates updates across all Cost centers and Scenarios for those intersections.

### Configuring drivers

In the Matrix planning visual, Drivers represent the measurable values available for planning. Each driver corresponds to a measure in your data model, and you can customize it to control display and aggregation.

### Driver configuration options

| Option              | Description                                                                 |
|---------------------|-----------------------------------------------------------------------------|
| Aggregation method  | Defines how the driver aggregates at parent levels. For example, SUM, AVG, MIN, or MAX. |
| Editable toggle     | Determines if a driver can be edited directly in the Matrix.               |
| Hide driver         | Hides a driver from display but keeps it in the model for reference or validation. Useful to simplify layout or when a driver is only used in the validation logic. |
| Rename driver       | Allows renaming the column header to better describe the driver. For example, rename Amount to Planned spend. |

> [!TIP]
> Use hidden drivers to store validation or approval status measures that shouldn't clutter the end-user layout but are required for rule logic or write-back control.

### Entering and editing data

After you configure the visual, enter or modify data directly in the grid.
- Single entry - Select a cell and enter a value.  
- Multi-select entry - Select multiple cells and enter a value to distribute evenly.  
- Additive entry - Prefix values with `a` to add to the existing amount.  
- Relative increase or decrease - Use `i#%` or `d#%` to adjust values by percentage.  
- Fill right - Use `r` to repeat a value across periods.  
- Repeat to children - Use `c` to apply a parent value to all children.  

When you finish editing, select **Save** to write changes back to Dataverse.

### Allocation capabilities

The **Allocation like** feature distributes a new value based on the relative ratios of another scenario or dimension. For example, you can allocate a forecast total proportionally to mirror the ratios of a Budget scenario.

To use **Allocation like**, follow these steps:

1. Right-click the target cell.
1. Select **Allocation like** from the context menu.
1. In the dialog, specify the reference. For example, Version = Budget.
1. Enter the new value and confirm.

The new value is then distributed across the children according to the reference pattern.

>[Note!]
> Allocation operations in Business performance planning are limited to 50,000 rows per operation. Above this threshold, the allocation fails with a maximum row limit error. Use slicers and filters to narrow the allocation scope before retrying.

### Validation and editing lock

To maintain governance and data integrity, the Matrix planning visual allows defining validation rules and editing locks. These rules are evaluated dynamically based on driver values present in the Matrix.

### Terminology

Each driver is referenced internally by its position in the **Drivers** list:

| Driver position | Example measure | Reference name |
|-----------------|-----------------|----------------|
| 1st | Amount | val1 |
| 2nd | Approval status | val2 |
| 3rd | Variance % | val3 |

This notation allows creating flexible rules that depend on relationships between drivers.

#### Edit validation

You want to prevent users from entering a new planned amount (val1) that is lower than the approved baseline amount and on a scenario that is locked.

Setup:

- Driver 1 (val1): Amount  
- Driver 2 (val2): Approval status (numeric value, such as 0 = Draft, 1 = Unlock, 2 = Locked)

Validation formula:
val1 >= 0 && val2 <> 2

- The entered amount must be non-negative.  
- Editing is blocked if the scenario’s approval status (val2) equals 2 (Locked).

If the validation fails, the user sees an on-screen message, and the edit isn't saved.

#### Edit lock

You want to lock all values when a scenario is approved (Approval status = 1).
Setup:

- Driver 1 (val1): Amount  
- Driver 2 (val2): Approval status
- Driver 2 (val2): Approval status

Editing lock formula:
*val2 = 1*

When this condition is met, all cells for the affected dimension row become read-only, preventing accidental edits after approval.

> [!NOTE]
> Locking operates at the cell level. You can't lock an entire row or column directly, but conditional logic can achieve the same effect.


### Multi-driver dependency

Lock a cell only when the amount exceeds 10,000 and approval status is approved.

Editing lock formula: *val1 > 10000 && val2 = 1*

When this condition is met, all cells for the affected dimension row become read-only, preventing accidental edits after approval.

> [!NOTE]
> Locking operates at the cell level. You can't lock an entire row or column directly, but conditional logic can achieve the same effect.

### Formatting and customization options

You can customize the appearance of the matrix through the **Format** pane.

| Option | Description |
|--------|--------------|
| Grid colors | Customize header, row, and alternate row colors. |
| Totals | Choose to display or hide row and column grand totals, and position totals to the left or right. |
| Row total label / suffix | Rename or format total labels. |
| Text settings | Adjust text size, font, and wrapping. |
| Conditional formatting | Apply colors or icons based on rules. For example, highlight negative variances. |
| Subtotal formatting | Set distinct styles for subtotal levels. |
| Show dimension prefix | Toggle between showing or hiding dimension names in headers. |

> [!TIP]
> You can also freeze panes, undo unsaved edits, or enable automatic refresh from the toolbar.

#### Editing behavior 

Several configuration options in the **Format** pane control how data entry behaves in the Matrix planning visual.

- Allocating at the parent level - Select this feature to enter a value directly at a parent level. For example, a total account or cost center group. After you save and refresh, the entered value is automatically distributed across all child elements below that parent. To allocate at the parent level, the parent must be collapsed before selecting the cell for editing. When this feature is off, you can only enter values at the lowest level of detail.
- Allow entry on empty parent - When **Splashing at the parent level** is on, enabling **Allow entry on empty parent** lets you enter data in a parent even if no existing child records have values. If both options are off, you can't enter data for parent elements with no initialized child data.
- All measure kind editable - This option allows all drivers (measures) in the Matrix to be editable simultaneously, regardless of their position. When turned off, editability is controlled individually using the **Measure uneditable** setting.
- Measure uneditable - Use this option to make specific drivers read-only based on their index position in the visual. The first driver starts at index 0, the second at 1, and so on.

For example:

- Enter 0 to make the first driver, such as Amount, uneditable.  
- Enter 1 to make the second driver, such as Discount, uneditable.  

This setting follows the same positional logic used in validation formulas (val1, val2), but is managed through the **Format** pane instead of scripting rules.

> [!NOTE]
> These settings affect editability behavior only. They don't change write-back logic or locking formulas defined in the validation and lock configuration.

### Comments and collaboration

The Matrix planning visual integrates with the **Comments** visual to capture user feedback or contextual notes.

- Add comments directly from the matrix via the context menu.  
- View all comments in the **Comments visual** alongside related data.  
- Comments are written back to Dataverse, ensuring traceability and collaboration.

> [!IMPORTANT] 
>
> - Include the msdyn_name field, the linking key between the fact and dimension tables in Dataverse, in the Matrix visual for all cube dimensions.
> - This field allows Business performance planning to correctly map each comment to its corresponding Dataverse record.  
> - You can only add **Comments** at the lowest level of granularity in the cube where all dimensions are fully specified.  
>  Attempting to add a comment at an aggregated level results in an error. 

#### Performance considerations

- Always use a **Filter measure** to limit the dataset loaded into the visual.  
- Minimize subtotals and nested hierarchies.  
- Limit conditional formatting and cell locks to key metrics only.  
- Use **Active Directory (Entra ID)** authentication for improved performance and SSO.  
- Test on production-sized datasets to validate real-world responsiveness.

#### Record count warning and partial write-backs

If the Matrix visual loads more than 30,000 records, an information (i) warning icon appears in the top-right corner of the visual. This warning indicates that the dataset exceeds the optimal interactive threshold for write-back operations.

If you receive an information warning, follow these steps: 
- Hover over the “i” icon to view the warning details.  
- Apply additional filters, such as on Account, Cost center, or Period, to reduce the visible record count below the threshold.  
- If you proceed without filtering, any edit or write-back operation might only partially commit data, as the visual can process only the first 30,000 rows per transaction.

Always confirm that the filters you apply match the intended planning scope before editing. Partial write-backs can lead to inconsistent totals between Power BI and Dataverse.

> [!NOTE]
> Edit validations and comments have minimal impact on rendering performance, as they’re triggered only upon user interaction.

### Best practices

- Use simple hierarchies with three to five levels to maintain performance.  
- Apply versioning logic to distinguish between Actual, Budget, and Forecast scenarios.  
- Use auto-refresh carefully when reports contain multiple visuals with write-back enabled.  
- Regularly test on production-sized datasets to ensure scaling behavior aligns with expectations.  
- Where possible, offload complex calculations to Dataverse tables or stored procedures.


## See also

- [Graphical planning visual](graphical-planning.md)  
- [Reporting visual](reporting.md)  
- [Comments visual](comments.md)  







