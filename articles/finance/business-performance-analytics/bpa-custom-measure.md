---
title: Add custom measures to Business performance analytics (preview)
description: This article explains how to add custom Power BI measures to the Business performance analytics semantic model and upload them for use in reports.
author: yvishwa
ms.author: yvishwa
ms.reviewer: twheeloc 
ms.date: 3/13/2026
ms.topic: how-to
ms.custom:
ms.search.form: business-performance-analytics
audience: Application User
ms.application-unique-name: msdyn_BusinessPerformanceAnalytics
---

# Add custom measures to Business performance analytics (preview)

Business performance analytics enables organizations to extend the semantic model with custom Power BI measures. This article explains how to download the semantic model, add custom measures, export the model artifacts, and upload them back to Business performance analytics for use in custom reports.

## Prerequisites

Before you add custom measures to Business performance analytics, the following prerequisites must be completed:

1. Your organization must have Business performance analytics successfully installed.
2. You must have a System Administrator role in Business performance analytics.
3. Business performance analytics version 2.7 or later must be installed.
4. Power BI Desktop must be installed (matching the PBIX compatibility for the downloaded model).

## Before you start

- **Backup**: Export and save the current semantic model (.pbix) and any existing measure artifacts before making changes.
- **Versioning**: Keep a versioned copy of the edited model and the final `.tmdl` files.
- **Test tenant**: Test your measures in a non-production Business performance analytics environment first.

## High-level flow

1. Download the semantic model from Business performance analytics.
2. Open the model in Power BI Desktop (or Tabular Editor via External Tools).
3. Add or modify measures.
4. Validate and test the measures in Power BI.
5. Save project artifacts and export `.tmdl` files.
6. Upload `.tmdl` files to Business performance analytics.
7. Validate in Business performance analytics and refresh reports/dashboards.

## Download the semantic model

To download the semantic model from Business performance analytics, follow these steps:

1. In Business performance analytics, select the **Administration** tab.
2. On the **Download Semantic Model** card, select **Download**.
3. Save the downloaded file (.pbix) and open it in Power BI Desktop.

## Add custom measures

You can add custom measures using either Power BI Desktop or Tabular Editor.

### Method A: Power BI Desktop (for simple/new measures)

1. Open the model in Power BI Desktop.
2. Connect to your Dataverse environment:
   - Go to **Transform Data** > **Edit Parameters**.
   - Update the **CdsOrgUrl** parameter (remove "https://" and trailing forward slash).
   - Select a small window of time (last 6 months recommended based on data size).
3. In the Model or Report view, select the table where the measure should live.
4. Select **New measure** and author the DAX expression.
5. Name the measure clearly (see naming guidelines below).
6. Save frequently.

### Method B: Tabular Editor (recommended for advanced scenarios)

1. From Power BI Desktop, select **External Tools** > **Tabular Editor**.
2. Create measures using Tabular Editor (allows templating, scripts, and bulk edits).
3. Save changes in Tabular Editor, which applies to the open model.

### Sample DAX measure

The following example shows a simple DAX measure:

```dax
Total Active Work Items = 
CALCULATE(
    COUNTROWS('WorkItems'), 
    'WorkItems'[Status] = "Active"
)
```

### Naming guidelines

- Use a clear prefix to indicate source or owner, for example, **[Custom]_[Team]_[MeasureName]**.
- Keep names short but descriptive.
- Avoid special characters that may break upload scripts.

## Validate and test your measures

To validate and test your custom measures, follow these steps:

1. Add visuals in Power BI to confirm measure values are correct against known test cases.
2. Verify filters, relationships, and that the measure respects row-level security if applicable.
3. Check performance—complex DAX may slow reports.

## Save as Power BI project

1. Save the modified .pbix locally and in your version control/project folder.
2. If you use Tabular Editor or other tooling, export/save the model artifacts per your team's standard.

## Export .tmdl files

To export `.tmdl` files for upload to Business performance analytics, follow these steps:

1. Use Tabular Editor (or your model-authoring tool) to export the measure(s) or model objects to `.tmdl` files that Business performance analytics expects.
2. Typical export steps in Tabular Editor:
   - Right-click the measure or selected objects.
   - Select **Save/Export** > choose **`.tmdl`** (or your team's export option).

> [!NOTE]
> If you don't have Tabular Editor or an export option, consult your tooling documentation for `.tmdl` export instructions.

## Upload `.tmdl` files to Business performance analytics

To upload your custom measures to Business performance analytics, follow these steps:

1. In Business performance analytics, select **Administration** > **Report measures**.
2. Locate the **Upload/Import measures** functionality (**Upload `.tmdl` files**).
3. Upload each `.tmdl` file per the UI instructions.
4. Confirm the upload succeeded and note any errors or warnings.

## Post-upload validation

After uploading your custom measures, follow these steps to validate:

1. Refresh datasets/reports that use the updated semantic model.
2. Verify the new measures show in Business performance analytics reports/dashboards and return expected values.
3. Communicate changes to consumers and add notes to change logs.

## Limitations and considerations

Consider the following limitations when adding custom measures:

- **Business performance analytics version**: Extensibility workflows depend on Business performance analytics version 2.3 or later. Some upload features may differ across minor versions.
- **Model schema changes**: Structural changes to tables/columns (not just measures) can break reports—avoid schema changes unless coordinated.
- **Name collisions**: Uploading measures with existing names may overwrite or conflict. Use prefixes and versioning.
- **Unsupported features**: Some complex model features or external dependencies may not be supported in the Business performance analytics import path—test thoroughly.
- **Security and RLS**: Adding measures doesn't automatically change or bypass row-level security—validate security after upload.

## Troubleshooting

Use the following guidance to troubleshoot common issues:

- **Upload errors**: Check the Business performance analytics admin upload logs for the exact error. Common causes include mismatched model schema, duplicate measure names, and unsupported DAX.
- **Wrong values**: Re-check relationships, filters, and measure DAX logic. Use simple test visuals with filters to isolate issues.
- **Performance regressions**: Identify expensive DAX (iterations, large table scans). Consider optimizing with variables, reduced row contexts, or pre-aggregations.

## Checklist before upload

Before uploading your custom measures, verify the following:

- Model .pbix saved and backed up
- Measures named and documented
- Upload tested in non-production environment (if available)

## See also

[Tabular Model Definition Language (TMDL) overview](/analysis-services/tmdl/tmdl-overview?view=sql-analysis-services-2025)
