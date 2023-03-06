---
# required metadata

title: Compare item prices storage report
description: Learn how to generate a Compare item prices storage report and then browse and/or export the result.
author: JennySong-SH
ms.date: 08/05/2022
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

ms.search.form: CostAdminWorkspace, CostAnalysisWorkspace, InventItemPriceCompareStorage, InventItemPriceCompareStorageDetailsChart, InventItemPriceCompareStorageDetails
# ROBOTS:
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm:
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: yanansong
ms.search.validFrom: 2020-03-01
ms.dyn365.ops.version: 10.0.9

---

# Compare item prices storage report

[!include [banner](../includes/banner.md)]

This article explains how to run a **Compare item prices storage** report and make the output available digitally, either as an interactive page in Dynamics 365 Supply Chain Management, or as an exported document in any of several formats.

When you view the report in your browser, columns and aggregate balances are dynamically adjusted, depending on your configured layout. You can sort the results, filter them, drill down into the data, and more.

Report results are stored in the **Compare item prices** data entity, which lets you filter and export the results to a format such as CSV or Microsoft Excel.

The **Compare item prices storage** report is helpful in cases where the output contains many lines. For example, the output will contain many lines if you have more than 40,000 items holding a pending item price in the costing version.

## Turn the Compare item prices storage feature on or off

To use this feature, it must be turned on for your system. As of Supply Chain Management version 10.0.29, the feature is mandatory and can't be turned off. If you're running a version older than 10.0.29, then admins can turn this functionality on or off by searching for the *Compare item price storage* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

## Generate a Compare item prices storage report

Follow these steps to generate and store a **Compare item prices storage** report:

1. Go to **Cost management > Inquiries and reports > Predetermined cost reports > Compare item prices storage**.

1. Select **New** to open the **Compare item prices** pane. Set the following options to define which prices to compare in your report:

    - On the **Parameters** FastTab, give the report a unique **Name** and use the fields in the **Pending prices to compare** and **Prices used for comparison** sections to define which prices and dates to compare.
    - On the **Records to include** FastTab, set up filters and constraints to define which data to include in the report.
    - On the **Run in the background** FastTab, set up how, when, and the frequency at which you want to generate the report.
    > [!NOTE]
    > This report is always executed as part of a batch job.

1. Select **OK** to apply your settings and close the pane.

1. After the batch job is completed, it will be listed on the **Compare item prices storage** page. You may need to refresh the page to see the report.

## Explore the Compare item prices storage report

After you've generated a report, you can view and explore it at any time as follows:

1. Go to **Cost management > Inquiries and reports > Predetermined cost reports > Compare item prices storage**.

1. Select a report from the list.

1. Do one of the following:

    - Select **Overview** to get an overview of your report results.
    - Select **View details** to get a more detailed view of your report

1. After the selected view opens, you can do the following:

    - Select almost any column heading to sort or filter the table by values in that column, just as with most standard forms in Supply Chain Management. Note, you can't sort or filter the **Net change price %** column because it's a calculated field.
    - Select **Dimension display** to open a pane where you can choose which dimension column to include on the form. Set **Save setup** to **Yes** if you'd like to save these settings so they will be preserved the next time you open the report. Select **OK** to apply your settings and close.
    - Select any row in the form and then select **View details** to see more information about the selected item. You'll be able to drill down into the data from here.
    - Select any row in the form and then select **View comparison chart** to see an interactive graphical representation of your results as they relate to your selected item. You can explore these results by selecting various graphical elements in the chart and chart legend.
    - Select any row in the form and then select **View calculation details** to see more information about calculations related to the selected item. You'll be able to drill down into the data from here.

## Export the Compare item prices storage report

Each report that you generate is stored in the **Compare item prices** data entity. You can use the standard data management features of Supply Chain Management to export data from this entity to any supported data format, including CSV or Microsoft Excel.

The following is an example of how to export a **Compare item prices storage** report:

1. Go to **System administration > Workspaces > Data management**.

1. Select the **Export** button in the **Data management** section.

1. The **Export** page opens, which you'll use to set up your export job. Start by giving your job a **Group name**.

1. In the **Selected entities** section, select **Add entity** to open a dialog box where you can set the following options:

    - **Entity name** - Select **Compare item prices**.
    - **Target data format** - Choose the format that you want to export to.

1. Select **Add** to add the new row and then select **Close** to close the dialog box.

1. Usually you'll export one report at a time. To do this, set up a **Filter** for the row you just added to the **Inquiry** pane. This will let you define which reports from the **Compare item prices** entity that you want to include in your export. Set the following filter options to export a single report:

    - On the **Range** tab, select **Add** to add a new row.
    - Set **Table** to **Compare item prices**.
    - Set **Derived table** to **Compare item prices**.
    - Set **Field** to the field that you want to filter by. Usually you'll use **Execution name** or **Execution time**.
    - Set **Criteria** to the value from your selected field that you want to look for (either the name of the report or the time the report was generated).
    - If necessary, add more rows to the **Range** table until you have uniquely identified the report that you're looking for.

1. Select **OK** to save your settings and close.

1. Select **Save** to save your export setup.

1. Open the **Export options** tab and select **Export now** to generate the export file.

1. The **Execution summary** page opens, where you can see the status of your export job and a list of entities that were exported. Select the **Compare item prices** entity listed in the **Entity processing status** area and then select **Download file** to download the data exported from that entity.

For more information about how to use data management to export data, see [Data import and export jobs overview](../../fin-ops-core/dev-itpro/data-entities/data-import-export-job.md).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]