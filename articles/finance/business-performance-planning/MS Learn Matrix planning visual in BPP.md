---
title: Matrix planning visual in Business Performance Planning
description: Learn the recommended practices to improve performance and responsiveness when using the Matrix planning visual.
author: romainpham

---

# Matrix planning visual in Business Performance Planning

The **Matrix planning visual** is the default planning visual available in Business Performance Planning (BPP).  
It enables users to enter, adjust, and allocate data directly in Power BI reports, with automatic write-back to Dataverse tables.  
This visual supports both **top-down** and **bottom-up** planning at any level of detail, making it ideal for financial, operational, and workforce planning scenarios.

---

## Overview

Use the Matrix planning visual to create and manage comprehensive planning and forecasting scenarios in an intuitive, spreadsheet-like interface.  
Changes made in the visual are instantly validated and written back to Dataverse, keeping your planning data synchronized across the organization.

### Key capabilities

- **Direct data entry:** Enter or edit values directly in the Power BI report.  
- **Allocation logic:** Perform top-down or bottom-up allocations (“Allocation Like”).  
- **Drilldown flexibility:** Navigate from summary to detail level while maintaining context.  
- **Conditional formatting:** Highlight trends, exceptions, and KPI thresholds visually.  
- **Advanced calculations:** Use custom aggregations, relative changes, and validations.  
- **Collaboration support:** Add comments or lock cells for control and governance.  
- **Persistent state:** Maintain your drill position and view state when refreshing the report.  
- **Excel interoperability:** Copy and paste data seamlessly between Power BI and Excel.

---

## Building a Matrix planning visual

### 1. Add the visual to your report

1. In Power BI Desktop, select the **Matrix planning** visual from the **BPP visuals** pane.  
2. Drag and drop your data fields into the following areas:
   - **Rows:** The hierarchy or dimension you want to display as row headers (for example, Account, Cost Center).  
   - **Columns:** The hierarchy or dimension you want to show across columns (for example, Period, Scenario).  
   - **Values:** The measure or amount to plan (for example, Budget Amount).  
   - **Filter Measure (recommended):** Add a measure that limits the dataset retrieved for better performance.

> [!NOTE]
> Always define a **Filter Measure**. Without it, Power BI retrieves unfiltered data, which can cause long rendering times.

---

## 2. Granularity and dimensional selection

When performing **data entry or write-back** in the Matrix visual, you must include **at least one field from each dimension** defined in your cube.  
This ensures that the update happens at the correct level of granularity in Dataverse.

### Example cube structure

Let’s consider a cube built with the following dimensions:

- **Account**
- **Cost Center**
- **Period**
- **Scenario**

Each dimension contains several fields:

| Dimension | Example fields |
|------------|----------------|
| **Account** | `msdyn_name` (Account Code), `Account Type`, `Account Category`, `PnL Category` |
| **Cost Center** | `msdyn_name` (Cost Center Code), `Cost Center Group` |
| **Period** | `msdyn_name` (Month_Year), `Month`, `Quarter`, `Year` |
| **Scenario** | `Version`, `Scenario Type` |

To enable write-back, you must select **at least one field from each dimension** — but it doesn’t have to be the key field (`msdyn_name`).  
You can use any descriptive or grouped field in the Matrix visual, such as `Account Category` or `PnL Category`.

---

### How write-back granularity works

When you edit data, BPP determines the update granularity based on the fields you’ve selected in the Matrix visual:

- If you use **Account Code (`msdyn_name`)**, updates are written at the most detailed level — one record per account code.  
- If you use a **grouping field** (like `Account Category`), the update is **allocated to all account codes** that belong to that group:
  - If there’s only one account code in that category, the entire amount is applied to that account.  
  - If multiple account codes already have values, the update is distributed **proportionally** to their existing values.  
  - If no existing values are found, the update is **allocated equally** across all account codes in the category.  

This behavior ensures planning remains consistent and correctly aggregated across different levels of detail.

---

### Example

Suppose your visual includes the following fields:
- Rows: `Account Category`  
- Columns: `Month`  
- Drivers: `Amount`  

You enter a new value of **60,000** under **Account Category = OTHEREMPEXP** for **January**.  

| Account Category | Jan | Feb | Mar |
|-------------------|-----|-----|-----|
| OTHEREMPEXP | 60,000 |     |     |

BPP will process this as follows:
- The system identifies all account codes under the **OTHEREMPEXP** category.  
- The 60,000 is distributed across those accounts:
  - If there’s **1 account**, all 60,000 is assigned to it.  
  - If there are **multiple accounts with existing values**, distribution is **proportional** to their prior amounts.  
  - If there are **multiple accounts without values**, 60,000 is divided **equally** across them.  

After saving, you can drill down to the account code level to see the distributed results.

---

> [!IMPORTANT]
> Write-back updates always occur at the **granularity represented in the visual**.  
> For example, if your visual shows only `Account Category` and `Month`, BPP allocates updates across all Cost Centers and Scenarios for those intersections.

---

 
## 3. Configuring Drivers (Values)

In the Matrix planning visual, **Drivers** represent the measurable values available for planning.  
Each driver corresponds to a measure in your data model, and can be customized to control display and aggregation.

### Driver configuration options

| Option | Description |
|--------|--------------|
| **Aggregation method** | Defines how the driver aggregates at parent levels. For example, `SUM`, `AVG`, `MIN`, or `MAX`. |
| **Editable toggle** | Determines whether a driver can be edited directly in the Matrix. |
| **Hide driver** | Hides a driver from display but keeps it in the model for reference or validation. Useful to simplify layout or when a driver is only used in validation logic. |
| **Rename driver** | Allows renaming the column header to better describe the driver (for example, rename “Amount” to “Planned Spend”). |

> [!TIP]
> Use hidden drivers to store validation or approval status measures that shouldn’t clutter the end-user layout but are required for rule logic or write-back control.

---

### 4. Entering and editing data

Once the visual is configured, you can enter or modify data directly in the grid.

- **Single entry:** Click a cell and enter a value.  
- **Multi-select entry:** Select multiple cells and enter a value to distribute evenly.  
- **Additive entry:** Prefix values with `a` to add to the existing amount.  
- **Relative increase/decrease:** Use `i#%` or `d#%` to adjust values by percentage.  
- **Fill right:** Use `r` to repeat a value across periods.  
- **Repeat to children:** Use `c` to apply a parent value to all children.  

After editing, select **Save** to write changes back to Dataverse.

---

### 5. Using allocation capabilities

#### Allocation Like
The **Allocation Like** feature lets you distribute a new value based on the relative ratios of another scenario or dimension.  
For example, you can allocate a “Forecast” total proportionally to mirror the ratios of a “Budget” scenario.

**To use Allocation Like:**
1. Right-click the target cell.
2. Select **Allocation Like** from the context menu.
3. In the dialog, specify the reference (for example, Version = Budget).
4. Enter the new value and confirm.

The new value is then distributed across the children according to the reference pattern.

---

### 6. Validation and editing lock

To maintain governance and data integrity, the Matrix planning visual allows defining **validation rules** and **editing locks**.  
These rules are evaluated dynamically based on driver values present in the Matrix.

### Terminology

Each driver is referenced internally by its position in the **Drivers** list:

| Driver position | Example measure | Reference name |
|-----------------|-----------------|----------------|
| 1st | `Amount` | `val1` |
| 2nd | `Approval Status` | `val2` |
| 3rd | `Variance %` | `val3` |

This notation allows creating flexible rules that depend on relationships between drivers.

---

### Example: Edit validation

**Scenario:**  
You want to prevent users from entering a new planned amount (`val1`) that is lower than the approved baseline amount and on a scenario that is locked.

**Setup:**
- Driver 1 (`val1`): `Amount`  
- Driver 2 (`val2`): `Approval Status` (numeric value, e.g. 0 = Draft, 1 = Unlock, 2 = Locked)

**Validation formula:**
val1 >= 0 && val2 <> 2

**Meaning:**
- The entered Amount must be non-negative.  
- Editing is blocked if the scenario’s Approval Status (`val2`) equals 2 (Locked).

If the validation fails, the user will see an on-screen message, and the edit won’t be saved.

---

### Example: Edit lock

**Scenario:**  
You want to lock all values when a scenario has been approved (Approval Status = 1).

**Setup:**
- Driver 1 (`val1`): `Amount`  
- Driver 2 (`val2`): `Approval Status`

**Editing lock formula:**
*val2 = 1*


When this condition is met, all cells for the affected dimension row become **read-only**, preventing accidental edits after approval.

> [!NOTE]
> Locking operates at the cell level. You can’t lock an entire row or column directly, but conditional logic can achieve the same effect.

---

### Example: Multi-driver dependency

**Scenario:**  
Lock a cell only when the amount exceeds 10,000 *and* approval status is approved.

**Editing lock formula:** *val1 > 10000 && val2 = 1*


When this condition is met, all cells for the affected dimension row become **read-only**, preventing accidental edits after approval.

> [!NOTE]
> Locking operates at the cell level. You can’t lock an entire row or column directly, but conditional logic can achieve the same effect.

---

### Example: Multi-driver dependency

**Scenario:**  
Lock a cell only when the amount exceeds 10,000 *and* approval status is approved.

**Editing lock formula:** *val1 > 10000 && val2 = 1*

---

### 7. Formatting and customization options

You can customize the appearance of the matrix through the **Format** pane.

| Option | Description |
|--------|--------------|
| **Grid colors** | Customize header, row, and alternate row colors. |
| **Totals** | Choose to display or hide row/column grand totals, and position totals to the left or right. |
| **Row total label / suffix** | Rename or format total labels. |
| **Text settings** | Adjust text size, font, and wrapping. |
| **Conditional formatting** | Apply colors or icons based on rules (for example, highlight negative variances). |
| **Subtotal formatting** | Set distinct styles for subtotal levels. |
| **Show dimension prefix** | Toggle between showing or hiding dimension names in headers. |

> [!TIP]
> You can also freeze panes, undo unsaved edits, or enable automatic refresh from the toolbar.

---

### Editing behavior settings

Several configuration options in the **Format** pane control how data entry behaves in the Matrix planning visual.

#### Allocating at the parent level

When this feature is **On**, you can enter a value directly at a **parent level** (for example, a total account or cost center group).  
After you save and refresh, the system automatically distributes the entered value across all child elements below that parent.

- To perform this action, the parent must be **collapsed** before selecting the cell for editing.  
- When this feature is **Off**, you can only enter values at the lowest level of detail.

#### Allow entry on empty parent

When **Splashing at the parent level** is **On**, enabling **Allow entry on empty parent** lets you enter data in a parent even if no existing child records have values.  
If both options are off, you won’t be able to enter data for parent elements with no initialized child data.

#### All Measure Kind Editable

This option allows all drivers (measures) in the Matrix to be editable simultaneously, regardless of their position.  
When turned off, editability is controlled individually using the **Measure Un-editable** setting.

#### Measure Un-editable (index-based)

Use this option to make specific drivers read-only based on their index position in the visual.  
The first driver starts at index `0`, the second at `1`, and so on.

For example:
- Enter `0` to make the **first driver** (for example, *Amount*) uneditable.  
- Enter `1` to make the **second driver** (for example, *Discount*) uneditable.  

This setting follows the same positional logic used in validation formulas (`val1`, `val2`, etc.), but is managed through the Format pane instead of scripting rules.

> [!NOTE]
> These settings affect editability behavior only. They don’t change write-back logic or locking formulas defined in the validation and lock configuration.
---

### 8. Context menu actions

Right-click a cell to open the context menu and access advanced options:

| Option | Description |
|---------|-------------|
| **Add** | Add a value to the existing cell total. |
| **Paste** | Paste data copied from Excel. |
| **Relative Increase / Decrease** | Adjust values by a specified percentage. |
| **Fill Right** | Repeat value to adjacent columns. |
| **Allocation Like** | Distribute a value using the ratios of another dimension or scenario. |
| **Comment** | Add or view comments tied to a data point. |

---

### 9. Comments and collaboration

The Matrix planning visual integrates with the **Comments** visual to capture user feedback or contextual notes.

- Add comments directly from the matrix via the context menu.  
- View all comments in the **Comments visual** alongside related data.  
- Comments are written back to Dataverse, ensuring traceability and collaboration.

> [!IMPORTANT] 
> - The **`msdyn_name`** field (the linking key between the Fact and Dimension tables in Dataverse) must be included in the Matrix visual for **all cube dimensions**.  
  >This allows BPP to correctly map each comment to its corresponding Dataverse record.  
>- **Comments** can only be added at the **lowest level of granularity** in the cube (where all dimensions are fully specified).  
>  Attempting to add a comment at an aggregated level will result in an error. 
---

## Performance considerations

- Always use a **Filter Measure** to limit the dataset loaded into the visual.  
- Minimize **subtotals** and nested hierarchies.  
- Limit **conditional formatting** and **cell locks** to key metrics only.  
- Use **Active Directory (Entra ID)** authentication for improved performance and SSO.  
- Test on **production-sized datasets** to validate real-world responsiveness.

### Record count warning and partial write-backs

If the Matrix visual loads more than **30,000 records**, an **information (“i”) warning icon** appears in the top-right corner of the visual.  
This indicates that the dataset exceeds the optimal interactive threshold for write-back operations.

**What to do:**
- Hover over the **“i”** icon to view the warning details.  
- Apply additional **filters** (for example, on Account, Cost Center, or Period) to reduce the visible record count below the threshold.  
- If you proceed without filtering, any edit or write-back operation may only partially commit data, as the visual can process only the first 30,000 rows per transaction.

> [!TIP]
> Always confirm that the filters applied match the intended planning scope before editing. Partial write-backs can lead to inconsistent totals between Power BI and Dataverse.

> [!NOTE]
> Edit validations and comments have minimal impact on rendering performance, as they’re triggered only upon user interaction.

---
## Troubleshooting and common issues

If the **Edit** button is unavailable or the visual doesn’t allow write-back, check the following common causes.

### 1. Missing fields from one or more cube dimensions
To enable editing, the Matrix visual must include **at least one field from every cube dimension**.  
If even one dimension is missing, the **Edit** button will remain disabled.

**Example:**  
If your cube includes the dimensions `Account`, `Cost Center`, `Period`, and `Scenario`, but your visual only includes `Account` and `Period`, the Matrix will render data but the **Edit** button won’t appear.

**Resolution:**
Add at least one field (any field) from each dimension to the visual and refresh.  
Once all dimensions are represented, editing and write-back will be enabled.

---

### 2. Expired Power BI authentication token
If the Power BI authentication token has expired, the Matrix planning visual cannot authenticate to the BPP service.  
When this occurs:
- The visual may become **greyed out**.  
- The **Edit** button disappears.  
- An error message may appear such as **“User does not have permission to edit data.”**

**Resolution:**
1. Refresh the browser or Power BI session.  
2. Sign out and sign back in to Power BI to renew your authentication token.  
3. If using Power BI Desktop, close and reopen the file to reauthenticate your session.

If the issue persists:
- **Create a new Matrix planning visual** from scratch and rebuild the configuration.  
- Or, to preserve your layout and fields:  
  1. Switch the existing visual temporarily to a **native Power BI Matrix**.  
  2. Copy and paste the visual.  
  3. Switch the copied visual back to a **Matrix planning visual**.  
  This process forces a full metadata refresh and clears any persistent cached references in the visual.



> [!NOTE]
> This issue is often mistaken for missing permissions, but it’s usually caused by an expired token rather than security configuration.

---

### 3. Format pane options missing

In some cases, when configuring the Matrix planning visual in Power BI, formatting option in the **Format visual your visual**  may disappear or fail to display correctly.  
This can happen if the visual’s local configuration cache becomes outdated after a schema or driver change.

**Resolution:**
- Remove one of the drivers (values) from the visual, then immediately add it back.  
  This forces the visual to refresh its internal cache and repopulate the missing format options.  
- Once the cache refreshes, the full **Tab Layout** configuration options should reappear.

> [!TIP]
> If the issue persists after re-adding a driver, save and reopen your report. The visual will rebuild its cached schema during initialization.

---

### 4. Incorrect API URL or cube name
Even if the visual displays data, a typo or misconfiguration in the **API URL** or **cube name** can block write-back operations.

**Symptoms:**
- The Matrix loads data but can’t enter edit mode.  
- Write-back actions return an error or silently fail.  
- Logs or pop-up messages may include **“An error occurred while executing the operation”**,  **“Cube not found”** or **“Invalid API endpoint.”**

**Resolution:**
1. Open the visual’s **Advanced settings** in Power BI.  
2. Verify that:
   - The **API URL** matches your environment’s BPP instance.  
   - The **Cube name** matches exactly the Dataverse cube name (case-sensitive).  
3. Correct any typos and refresh the report.

If the issue continues:
- Recreate the visual or follow the same **switch–copy–restore** method described above to reset the metadata binding.


---

### 4. Role or permission mismatch
The user must have appropriate Dataverse and BPP security roles to perform write-back.  
If the user can view but not edit data:

**Resolution:**
- Ensure the user has the **BPP Contributor** or **BPP Admin** role.  
- Verify the Dataverse table permissions allow `Create`, `Read`, `Write`, and `Append` for planning tables.  
- If using row-level security (RLS), confirm the user’s data slice matches the visual’s filters.

---

### 5. Comments not available
If the **Comment** option doesn’t appear in the context menu:
- The visual might not include the `msdyn_name` field for all cube dimensions.  
- Comments can only be added at the **lowest level of granularity**.

**Resolution:**
Ensure the Matrix includes the `msdyn_name` field from each dimension, even if hidden in the visual.

---

### 6. Performance degradation after large edits
If the Matrix visual becomes slow after bulk changes or multi-cell updates:

**Resolution:**
- Use **smaller edit batches** (for example, update 50–100 cells at a time).  
- Reduce the number of subtotals in the visual.  
- Refresh the visual after saving to release cached state.

---

> [!TIP]
> For more in-depth guidance on optimizing performance, see [Matrix planning visual performance considerations](matrix-planning-performance.md).

---

## Best practices

- Use **simple hierarchies** with 3–5 levels to maintain performance.  
- Apply **versioning** logic to distinguish between Actual, Budget, and Forecast scenarios.  
- Use **auto-refresh** carefully when reports contain multiple visuals with write-back enabled.  
- Regularly **test on production-sized datasets** to ensure scaling behavior aligns with expectations.  
- Where possible, offload complex calculations to Dataverse tables or stored procedures.

---

## See also

- [Graphical planning visual](graphical-planning.md)  
- [Reporting visual](reporting-visual.md)  
- [Comments visual](comments-visual.md)  
- [Write-back and allocation in BPP](write-back.md)
