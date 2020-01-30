---
# required metadata

title: Run, store, and export compare-item-prices reports
description: Learn how to run a compare-item-prices report and make the output available digitally
author: AndersGirke
manager: AnnBe
ms.date: 03/01/2020
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

ms.search.form: CostAdminWorkspace, CostAnalysisWorkspace  
# ROBOTS:
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm:
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: aevengir
ms.search.validFrom: 2020-03-01
ms.dyn365.ops.version: Release 10.0.9

---

# Run, store, and export compare-item-prices reports

[!include [banner](../includes/banner.md)]

Read this topic to learn how to work with the compare item prices storage feature, which lets you run a compare-item-prices report and make the output available digitally, either as a browsable form in Supply Chain Management, or as an exported document in any of several formats.

When you view the report as a browsable form, columns and aggregate balances are dynamically adjusted, depending on your configured layout. You can sort the form, filter it, drill down into the data, and more.

Report results are stored in the *compare item prices* data entity, which lets you filter and export the results to a format such as CSV or Microsoft Excel.

This method of running the compare-item-prices report is helpful in cases where the output contains many lines. For example, the output will contain many lines if you have more than 40,000 items holding a pending item price in the costing version.

## Enable compare item prices storage

Before you can use this feature, you must make sure it's available on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module**: Cost management
- **Feature name**: Compare item price storage

If you don't see this feature listed under feature management, then we may have made it a standard part of the product since this documentation was written, in which case all of the features described in this topic should already be available to you.

## Generate a compare item prices storage report

To run a compare-item-prices report and then store or export it:

1. Go to **Cost management** > **Inquiries and reports** > **Predetermined cost reports** > **Compare item prices storage**.

1. Select **New** to open the **Compare item prices** flyout. Make the following settings here to define which prices to compare in your report:

    - In the **Parameters** FastTab, give the report a unique **Name** and use the fields in the **Pending prices to compare** and **Prices used for comparison** sections to define which prices and dates to compare.
    - In the **Records to include** FastTab, set up filters and constraints as needed to define which data to include in the report.
    - In the **Run in the background** FastTab, set up how, when, and how often you want to run the report.
    > [!NOTE]
    > This report is always executed as part of a batch job.

1. Select **OK** to apply your settings and close the flyout.

1. After the batch job is completed, it will be listed on the **Compare item prices storage** page. You may need to refresh the page first.

## Explore a compare item prices storage report

After you've run a report, you can view and explore it at any time using the interactive form as follows:

1. Go to **Cost management** > **Inquiries and reports** > **Predetermined cost reports** > **Compare item prices storage**.

1. Select a report from the list.

1. Do one of the following:

    - Select **Overview** on the action pane to get an overview of your report results.
    - Select **View details** on the action pane to get a much more detailed view of your report

1. Your selected view opens. From here, you can do the following:

    - Select nearly any column heading to sort or filter the table by values in that column, just as with most other standard forms in Supply Chain Management. (Note, however, that you can't sort or filter the **Net change price %** column because it's a calculated field.)
    - Select **Dimension display** on the action pane to open a flyout where you can choose which dimension column to include on the form. Set **Save setup** to **Yes** if you'd like to save these settings so they will be preserved the next time you open the report. Select **OK** to apply your settings and close the flyout.
    - Select any row in the form and then select **View details** on the action pane to see more information about the selected item. You'll be able to continue to drill down into the data from here.
    - Select any row in the form and then select **View comparison chart** on the action pane to see an interactive graphical representation of your results as they relate to your selected item. You can explore these results by selecting various graphical elements in the chart and chart legend.
    - Select any row in the form and then select **View calculation details** on the action pane to see more information about calculations related to the selected item.  You'll be able to continue to drill down into the data from here.

## Export a compare item prices storage report

Each report that you generate is stored in the *compare item prices* data entity. You can use the standard data management features of Supply Chain Management to export data from this entity to any supported data format, including CSV or Microsoft Excel.

Here is a typical example for how to export a compare item prices storage report:

1. Go to **System administration** > **Workspaces** > **Data management**.

1. Select the **Export** button in the **Data management** section.

1. The **Export** page opens, which you'll use to set up your export job. Start by giving your job a **Group name**.

1. In the **Selected entities** section, select **Add entity** to open a dialog box and then make the following settings here:

    - **Entity name** &ndash; Select **Compare item prices**.
    - **Target data format** &ndash; Choose the format you want to export to.

1. Select **Add** to add the new row and then select **Close** to close the dialog box.

1. Usually you'll export just one report at a time. To do this, select the funnel icon in the **Filter** column for the row you just added to the **Inquiry** flyout. This will let you define which reports from the *Compare item prices* entity you want to include in your export. Make the following settings to export just one report:

    - On the **Range** tab, select **Add** to add a new row.
    - Set the **Table** to **Compare item prices**.
    - Set the **Derived table** to **Compare item prices**.
    - Set the **Field** to the field you want to filter by. Usually you'll use **Execution name** or **Execution time**.
    - Set the **Criteria** to the value from your selected field that you want to look for (either the name of the report or the time you generated it).
    - If necessary, add more rows to the **Range** table until you have uniquely identified the report you're looking for.

1. Select **OK** to save your settings and close the flyout.

1. Select **Save** on the action pane to save your export setup.

1. Open the **Export options** tab on the action pane and select **Export now** to generate the export file.

1. The **Execution summary** page opens, which provides a list of generated files in the **Entity processing status** area. Select a file listed here and then select **Download file** to download it to your computer.

For more information about how to use data management to export data, see [Data import and export jobs overview](../../fin-ops-core/dev-itpro/data-entities/data-import-export-job.md) and its related topics.