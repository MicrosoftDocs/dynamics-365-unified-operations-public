---
title: Create a cube from Excel (preview)
description: Learn how to create planning cubes in Business performance planning by importing Excel files using the Data model builder (preview) experience.
author: twheeloc
ms.author: romainpham
ms.topic: how-to
ms.date: 08/25/2026
ms.reviewer: twheeloc
ms.collection: get-started
---

# Create a cube from Excel (preview)

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

> [!IMPORTANT]
> This article describes one of the new workflows available under **Cubes (preview)** in the Navigation pane, since version v1.17 of Business performance planning application.
>
> Unlike the classic flow, where dimensions must already exist before you can build a cube on top of them, this workflow lets you create dimensions and a cube **at the same time**, directly from an Excel file.
> The existing **Cubes** page remains available for backward compatibility until migration to the new experience is complete.
> To use the classic cube creation flow, see [Creating cubes](create-cubes.md).

Uploading data from Excel uses an Excel extract, from an existing spreadsheet-based process, a legacy planning tool, or your organization's information system, to quickly stand up dimensions and granularity without prebuilding them in Dataverse. This approach lets you assess whether a proposed data model and level of granularity actually fit the planning process, using real data rather than a blank canvas.

## Create a cube from Excel

Create a new cube by importing one or several Excel files that contain fact and dimension data. Business performance planning automatically detects all worksheets in your uploaded files and guides you to tag, validate, and preview the resulting planning model.

- The **Create cube from Excel** workflow currently supports creating one cube per iteration.
- You can upload multiple Excel files at once. For example, one file containing the fact data and others containing related dimensions.
- Across all uploaded files, tag only one table as the Fact.
- Treat all remaining tagged tables as Dimensions.
- Attempting to tag more than one fact table, from the same or different files, results in errors. Multiple fact tables introduce ambiguity in relationships within a single cube model.

### Choose data source

To select a data source, follow these steps:

1. Go to **Model** > **Cubes (preview)**, select **+ New cube**.
1. In the **Data source** step, choose **Excel workbook (.xlsx)** as the source.  
   Other options include **Business performance planning dimensions** and **Import cube (JSON)**.

### Upload Excel files

Add one or more Excel workbooks (.xlsx or .xls). Sheets from each file are grouped together in the next step.

- Upload a workbook—for example, `PBI SOURCES DEMO RETAIL.xlsx`. After you upload the file, it shows its status and the number of sheets it contains (for example, `Uploaded · 10 sheets`).
- Select **+ Add new files** to upload more workbooks. You can combine sheets from multiple files into the same planning model.

Guidance for file count and size:

- Upload up to five files. Adding more files shows a performance warning but doesn't block you.
- Upload files smaller than 2 MB. Files larger than 2 MB show a performance warning. Files larger than 2 MB might affect performance. For the best experience, upload smaller files.
- Files larger than 10 MB can't use automatic data loading after publish. This option is turned off and locked later during the review step. The cube is still created and you import the data yourself afterward.
- Shorten sheet and column names that are too long. The system flags them as errors.

### Select sheets

Business performance planning automatically lists all the worksheets or named tables it detects in your uploaded Excel files.  
Select the sheets you want to include in your planning model.

- You don't need to import every sheet. For example, you can leave unchecked and exclude from the model a setup or reference tab, such as `Information setup` or `Product mix`.
- Each selected sheet appears as a table in the next step.

### Set table types

In this step, assign one selected table as a **Fact** table.
For each **Dimension**, select the column that uniquely identifies a row.
For each table, the Table types and relationships grid shows:

- **Type**: set to Dimension or Fact. Exactly one table must be set to Fact; all others are Dimensions.
- **Primary name**: For each Dimension, choose the column that serves as its primary key from the columns detected in that sheet. For example, Store, ProductKey, or YearMonth. This value isn't applicable for the Fact table.
- **\# Columns**: the number of columns imported from that sheet.
This information replaces the earlier behavior where a system-generated **Name** column was always used as the primary key. You now choose which existing column acts as the primary key for each dimension.

### Set relationships

Connect fact table columns to dimensions, or mark them as drivers. The cube renames mapped columns to match the selected dimension name.

- For each column in the **Fact** table, use **Map to** to either select one of the chosen dimensions or choose **Mark as driver** for numeric columns that represent planning inputs. For example, Amount, Units, or Sales per unit.
- You must map all fact columns before you can proceed. An unmapped column, shown as Choose mapping…, blocks you from continuing.
- Columns that look numeric but represent a dimension key, such as ProductKey, might default to **Mark as driver**. If a column is meant to link to a dimension rather than serve as a planning input, change its mapping to the correct dimension before moving on.

#### Review

The **Review** page summarizes the configuration: cube name, dimensions, and drivers.

- You can rename the cube at this stage.
- The system imports any dimension that isn't mapped to a column of the fact table as disconnected. From the **Review** page, you can either use it to power a linked column from an existing dimension or remove it from the model.
- The same handling applies to drivers - you can link or remove any driver that isn't connected to the fact table.
- If one or more of the dimensions in your model already exist elsewhere in your environment, Business performance planning reuses them instead of creating duplicates. Because other cubes might already use these dimensions, the system keeps their existing data unchanged and doesn't load data from your uploaded sheet into them.
On the **Review** page, you see a warning listing which dimensions will be reused: "These dimensions already exist and will be reused:\<list>\. Their existing data is preserved, so the data in your uploaded sheet won't be loaded for them."
This behavior is intentional. It prevents your upload from overwriting dimension data that other cubes depend on. If you need to add or update members in a shared dimension, do so directly in that dimension or by using a dataflow, rather than through this cube's Excel upload.
In the data load status report after publishing, these dimensions appear with a status of **Skipped**, not **Failed**, since no error occurred.
- **Auto data load after publish (preview)**: this toggle is on by default and loads your Excel data into the cube automatically as soon as you publish. It automatically turns off and locks if:
  - any uploaded file is larger than 10 MB
  - a dimension sheet has more than 3,000 rows
  - the fact sheet has more than 200,000 rows
  In those cases, the system still creates the cube; you load the data yourself afterward by using [Dataflows](load-data-dataflows.md).

Select **Create** to generate a **Draft** cube.
The cube now appears under **Draft** in the left-hand panel. In the background, your workbook is staged for loading. This process can't block cube creation. If staging fails, the system still creates the cube and doesn't automatically load data.

### Refine the draft cube

In **Draft** mode, your cube opens in the **Data Model view**, displaying the relationships between your fact and dimension tables.  

You can:

- Add or delete drivers.  
- Add or delete dimensions from existing Business performance planning dimensions, additional Excel files, or manually configured ones.

> [!NOTE]
> If you add a new dimension here after your Excel workbook is already uploaded and staged, that dimension has no source sheet - no data is ever uploaded for it. When you publish, this dimension is reported as skipped in the data load status, and because a missing dimension could corrupt the numbers, it also blocks the fact table from loading. To load data for a dimension added this way, either populate it separately, for example, by using dataflow, or recreate the cube from a workbook that includes that dimension's sheet.

- Enable or disable optional features under **Properties > Advanced**:
  - **Audit** - Records write-back and user changes.  
  - **Enable fast analytics index** (Non-Clustered Column Index aka NCCI), which improves performance for large datasets. Starting in version 1.17, NCCI is enabled by default for new cubes. You can disable it if it isn't needed for your model.

The Excel upload creates the schema of the cube. No data is imported at this stage. To load actual data into the cube, use [Dataflows](load-data-dataflows.md) after publishing or rely on **Auto data load after publish** if it's enabled for your cube.  
When you finalize your model structure, select **Publish**.

### Publish and add data

Publishing converts the cube schema into physical Dataverse tables and relationships to use in planning and analytics.
If you enable **Auto data load after publish**, publishing also queues a background load of your staged Excel data. You don't need to do anything else. The system waits for the newly created tables to be ready before loading, to absorb normal post-publish provisioning delay. To track progress and understand the results, see **Monitor the automatic data load**, later in this article.

The cube status updates to **Published** and you can:

- Load fact data by using **Dataflows**.  
- Add drivers to the published cube - Starting in version 1.16, you can add new drivers directly to a cube after it's published. You're no longer limited to defining drivers only while the cube is in **Draft** mode.
- Create calculated columns by using the Dataverse formula column engine.
- For example:
- Revenue = Units Sold × Unit Price
- Gross Margin = Revenue − COGS
- Connect your cube to Power BI or Excel for real-time write-back planning.
Calculated columns become available only after the cube is published.

### Monitor the automatic data load (preview)

When you enable automatic data loading, publishing your cube also starts loading your workbook's data into it in the background. You no longer need to run a separate import step afterward. A progress card tracks the load. When it finishes, open the **Data load status** dialog to see exactly what loaded, what didn't, and why. The dialog includes:

- KPI cards showing counts for: **Tables processed**, **Loaded**, **Partially loaded**, **Failed**, and **Skipped**.
- Filter pivots to view **All tables**, or just **Loaded**, **Partially loaded**, **Failed**, or **Skipped**.
- A per-table results table that lists each table's name, status, and a plain language explanation of what happened.

Every table lands in one of these outcomes:

| Status | What it means | Blocks the fact table load? |
| --- | --- | --- |
| **Loaded** | Everything in that sheet loaded successfully. | No |
| **Partially loaded** | Some rows loaded, some didn't. Most commonly because of duplicate primary keys. Distinct rows load; duplicates are rejected individually. | Yes |
| **Skipped** | Nothing to do, this isn't an error. Covers empty sheets, reused or existing dimensions, tables removed from the schema after staging, and dimensions added to the draft after staging. | Usually no, except when a dimension is added to the draft after staging |
| **Failed** | Nothing loaded, due to a hard error. For example, every row was a duplicate, or the cube wasn't ready yet. | Yes |

Why does a partial or failed dimension block the fact load? The fact table's numbers reference dimension members (the labels). If a required dimension didn't fully load, some numbers would point at missing labels and corrupt the cube. The system deliberately holds the fact load back rather than load incomplete data. If the fact load is blocked, its status shows as **Skipped**, with an explanation that one or more dimensions failed to load or were added after staging.

Linked or relationship columns in a sheet never load from Excel, even when the rest of that sheet loads successfully. The status message calls out which linked columns were skipped.
The fact table only loads after all dimensions finish, and only if none of them blocked it.
Fact data loads by overwrite-by-key, so if the background load is retried, it doesn't create duplicate rows.

#### File and row limits for automatic data load

| Limit | Threshold | What happens above it |
| --- | --- | --- |
| Recommended file count | 5 files | Performance warning only—not blocked |
| Per-file performance warning | 2 MB | Performance warning only—still allowed |
| Per-file automatic-load ceiling | 10 MB | Automatic data loading is turned off and locked; the cube is still created |
| Dimension sheet rows for automatic load | 3,000 rows | Automatic data loading is disabled; load that data using a dataflow instead |
| Fact sheet rows for automatic load | 200,000 rows | Automatic data loading is disabled; load that data using a dataflow instead |
| Post-publish table-ready wait | ~2 minutes + 1 retry | Absorbs normal provisioning lag after publish |

#### Why didn't my data load?

- My reused or existing dimension is empty, or didn't take my sheet's data - This condition is by design. Reused dimensions keep their existing data, and the uploaded sheet is skipped to avoid overwriting records shared with other cubes.
- My dimension shows Partially loaded - You likely have duplicate primary-key rows. The distinct ones loaded, and duplicates were rejected. This condition also blocks the fact table load.
- The fact table didn't load at all - A dimension was **Failed**, **Partially loaded**, or added to the draft after staging, which blocked it. Fix the dimension data (or reload it via a dataflow) and try again.
- Auto data load was greyed out during the review step - A file was over 10 MB, a dimension sheet exceeded 3,000 rows, or the fact sheet exceeded 200,000 rows. The cube was still created. Import the data by using a dataflow.
- I added a dimension after uploading, and nothing loaded, including the rest of the cube's data - This condition is expected. A dimension added after staging has no source sheet, so it's **Skipped**, and it blocks the fact table. Load that dimension by using a dataflow, or recreate the cube from a workbook that includes it.
- Everything was small, but I still didn't get automatic loading - Staging happens right after you select **Create**, and can occasionally fail without blocking cube creation. If this condition happens, load your data manually by using a dataflow.

### Known limitations (preview)

The following limitations currently apply to the Cube (preview) Create a cube from Excel:

- You can’t modify published dimensions directly in the Cube (preview) interface. After you publish a cube, you can’t add or remove columns within a dimension from the Cube (preview) workspace. To make these changes, go to the dimension directly in the **Dimensions** area of the Business performance planning app or in the **Power Apps maker portal**, and update it there.
- Changes made to dimensions outside the Cube (preview) experience aren’t automatically reflected in the model view. If you update a dimension, for example, by adding or deleting columns in the **Dimensions** area of the app, select **Sync cube** in the Cube (preview) workspace to refresh the model view with the latest structure. These changes still apply at the Dataverse level, so the updated structure and data remain available in Power BI and Excel reports connected to the same environment, even before you sync. This limitation will be removed in an upcoming release. Future versions of the Data Model Builder will reflect dimension updates automatically in the Cube (preview) interface.
- Bad-cell (data type) errors during automatic data load aren't reported row by row. For example, a text value in a column expected to be numeric can cause that batch to fail during preparation, rather than being counted individually the way duplicate-key failures.
- The data load status shows only the first error per table, not a full list of every failing row.
- You need to recreate dimensions that you created before a display-name fix for the "Name" column to benefit from current primary-key behavior.
- Very large dimensions report a member count capped at 5,000 in some diagnostic views, even if the dimension contains more members.

### Next steps

- [Create a cube from existing dimensions](BPP-cub-dim.md)  
- [Create a cube from JSON](bpp-json.md)  
- [Load data using dataflows](load-data-dataflows.md)  
- [Create calculated columns](calculated-columns.md)
