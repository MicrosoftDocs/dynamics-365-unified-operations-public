---
title: Inventory value reports
description: Inventory value reports provide details about your inventory physical and financial quantities and amounts. This topic explains how to set up, generate, and use them.
author: banluo-ms
ms.date: 10/19/2021
ms.topic: article
ms.search.form: InventValueProcess, InventValueReportSetup
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: banluo
ms.search.validFrom: 2021-10-19
ms.dyn365.ops.version: 10.0.9
---

# Inventory value reports

[!include [banner](../includes/banner.md)]

Inventory value reports provide details about your inventory physical and financial quantities and amounts. You can choose to view the report in many different ways, such as by showing totals or transactions and by applying filters based on items or time range. You can view COGS values or WIP values and set other options.

With the inventory value report, you can:

- Do reconciliation between the general ledger and inventory.
- Consult on-hand inventory and values for a specific period.
- Create report configurations tailored for a specific purposes.
- Save report configurations that can be used multiple times.
- Add ranges to filter data when you run a report.

> [!NOTE]
> The report won't include subtotals that are defined in the report layout. It also won't include general ledger balances, even when they are defined in the report layout. Reconciliation to the general ledger must be done by using trial balances. <!-- KFM: Does this note apply to both types of reports, or just storage? -->

<!-- KFM: I think one reason we are adding this new text is that we wanted to provide more information about "reconciliation". Maybe we should do that here in the intro and/or add a section about it (here or in the other topic). Otherwise, we rarely mention it.  -->

## Types of inventory value reports

There are two types of inventory value reports: *inventory value report* and *inventory value report storage*.

### The standard inventory value report

The standard *inventory value report* is a simple report that lets you choose what to include and then displays information on your screen. It doesn't save the results, nor does it provide interactive features for filtering, drilling down, browsing, or exporting. For these reasons, we recommend using *inventory value report storage* instead in most cases.

### The inventory value report storage report

The *inventory value report storage* report provides output either as an interactive page in Supply Chain Management or as an exported document in any of several formats.

When you view the report in your browser, columns and aggregate balances are dynamically adjusted, depending on the layout that you've configured. You can sort the results, filter them, drill down into the data, and more.

Report results are stored in the **Inventory value** data entity. Therefore, you can filter and export the results to a format such as comma-separated values (CSV) or Microsoft Excel format.

The *inventory value report storage* report is helpful when the output contains many lines. For example, you have 50,000 items, and 300 stores have been created as warehouses. In this case, if you request inventory ending balances by item, site, and warehouse, the output will contain many lines.

## Turn on the Inventory value report storage feature

The standard *inventory value report* feature is enabled by default, but if you want to generate the more advanced *inventory value report storage* reports, you must turn on the feature in your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on if it's required. In the **Feature management** workspace, the feature is listed in the following way:

- **Module** – Cost management
- **Feature name** – Inventory value report storage

## <a name="report-configuration"></a>Define inventory value report configurations

Use the **Inventory value reports** page to set up the content that you want to include in various type of inventory value reports. You can define any number of report types, and you will select a type each time you generate either type of inventory value report.

1. Go to **Cost management \> Inventory accounting policies setup \> Inventory value reports**.
1. Do one of the following steps:
    - To edit an existing report, select it in the list pane and then select **Edit** on the Action Pane.
    - To create a new report, select **New** on the Action Pane.
1. Make the following settings in the header of the new or selected report:
    - **ID** – Enter a short identifier for the report. This value must be unique among all inventory value reports, and can't be edited after you create and save a new report configuration.
    - **Name** – Enter a descriptive name for the report.

1. If you are creating a new report configuration, then select **Save** on the Action Pane to enable the remaining settings.
1. Expand the **General** FastTab and make the following settings:  
    - **Date interval** – Choose a pre-defined date interval. This date interval can be overridden when you run the report.
    - **Range** – Choose either *Posting date* or *Transaction Time*, depending on which value the report should use to retrieve data. <!-- KFM: This isn't clear. Please revise. -->
    - **Dimension set** – Choose which set of dimensions to run the data for. For example, you might run the data by *Main account*, or by *Main account + Business unit*. You must choose a dimension set that has two or fewer dimensions. <!-- KFM: Where are these defined? Can we link to a topic with more info about how to set these up? What do we mean by "run the data"? -->

1. Expand the **Columns** FastTab and make the following settings. <!-- KFM: Can we briefly introduce what these options have in common? (Eg, "Use these setting to control which columns will be included in the report.") -->
    - **Inventory** – Set to *Yes* to reconcile the inventory value with inventory G/L accounts balance <!-- KFM: Spell out "G/L" on first use. Are we actually reconciling anything here, or are we just including information that we can use to reconcile later? -->.
    - **WIP** – Set to *Yes* to reconcile the WIP value with WIP G/L accounts balance <!-- KFM: Spell out WIP. Are we actually reconciling anything here, or are we just including information that we can use to reconcile later? -->. When you use this option, only the physical quantities and amounts of inventory in WIP status will show in the report. Production orders that are in WIP status have been picked or reported as finished but not ended. <!-- KFM: Is it production orders or inventory that can have "WIP status" (or both)? -->
    - **Deferred COGS** – Set to *Yes* to display a column showing the physical quantities and amounts of inventory for the mark of Deferred COGS <!-- KFM: Spell out COGS. What do you mean by "for the mark of Deferred COGS"? -->. The report will display the financial quantities and amounts for the mark of COGS <!-- KFM: "for the mark of Deferred COGS"? -->. Deferred COGS are shown using physical quantities and amounts because they offset packing slip quantities and amounts. However, COGS are shown using financial quantities and amounts because they offset the invoice quantities and amounts.
    - **COGS** – <!-- KFM: Description needed. -->
    - **Profit and loss** – Set to *Yes* to display a column for the financial amount posted to the profit and loss accounts for inventory.
    - **Print cumulative account values for comparison** – Set to *Yes* to display a column showing the G/L accounts balance in the report. By doing this, you won't need to check the trail balance. This works only with the *inventory value report*, not *inventory value report storage*. Please note that choosing a Total account <!-- KFM: How do I "choose a total account"? --> will show both the amounts of each of the inventory accounts included in the total account and the amount of the total account. After you enable this option, you must fill in the G/L account you want to reconcile <!-- KFM: Where/how do I do this? -->.
    - **Inventory account** – <!-- KFM: Description needed. -->
    - **WIP account** – <!-- KFM: Description needed. -->
    - **Deferred COGS account** – <!-- KFM: Description needed. -->
    - **COGS account** – <!-- KFM: Description needed. -->
    - **Summarize physical and financial values** – Set to *Yes* to display a column showing the total inventory quantity and inventory amount (summarizing both physical and financial inventory values). When set to *No*, the report report will show both physical and financial inventory values.
    - **Include not posted to ledger** Set to *Yes* to display a column showing the transactions that never posted to G/L. This can occur for the following types of items:
        - Received and not yet invoiced items where the **Post physical inventory** option unselected for the relevant item model group.
        - Received and not yet invoiced items when the **Post product receipt in ledger** option isn't selected in **Accounts payable parameters** (**Accounts payable \> Setup \> Accounts payable parameters**, **General** tab, **Product receipt** FastTab).

    - **Calculate average unit cost** – Set to *Yes* to display a column showing the average unit cost. The average unit cost is the total quantity divided by the total amount.
    - **Total quantity and value** – Set to *Yes* to display columns showing the total quantity of physical inventory (and financial quantities) and the total amount of physical inventory (and financial amounts). You can only enable this option when the **Summarize physical and financial values** option is not enabled. <!-- KFM: Please confirm my revision. Also, what is the difference between "quantity" and "amount"? -->
    - **Inventory dimensions** – In this grid, select the dimensions to show in the report. Only dimensions that have the **Financial inventory** option enabled will show values in the report; other dimensions will show only blank columns. <!-- KFM: What's the difference between "view" and "total"? -->
    - **Resource ID** – Set options related to displaying item numbers <!-- KFM: More detail needed. How are the "view" and "total" options different? -->. The information in the **Resource** column of the inventory value report is based on a combination of the `ItemID`, `WorkcenterID`, and `CodeID` fields. <!-- KFM: The purpose of this sentence, and the following bullet list, aren't clear. -->
        - Material: Resource = `ItemID`
        - Labor: Resource = `WorkCenterID`
        - Indirect cost: Resource = `CodeID`

        If either **Resource ID** or **Resource Group** are not marked, you will only see a total inventory value based on the inventory dimensions you selected. <!-- KFM: We have four options here. Which combination of options are you referring to? -->

    - **Resource ID** – Set options related to displaying item groups <!-- KFM: More detail needed. How are the "view" and "total" options different? -->. The information in the **Resource** column of the inventory value report is based on a combination of the `ItemGroup`, `WorkcenterGroup`, and `CostGroup` (`CostGroupType` = Indirect) fields. <!-- KFM: The purpose of this sentence (especially the part in parenthesis), and the following bullet list, aren't clear. -->
        - Material: Resource = `ItemGroup`
        - Labor: Resource = `WorkcenterGroup`
        - Indirect cost: Resource = `CostGroup`

        If either **Resource ID** or **Resource Group** are not marked, you will only see a total inventory value based on the inventory dimensions you selected. <!-- KFM: We have four options here. Which combination of options are you referring to? -->

1. Expand the **Rows** FastTab and make the following settings. <!-- KFM: Can we briefly introduce what these options have in common? (Eg, "Use these setting to control which rows will be included in the report.") -->
    - **Material** – <!-- KFM: Description needed. -->
    - **Labor** – <!-- KFM: Description needed. -->
    - **Indirect cost** – <!-- KFM: Description needed. -->
    - **Direct outsourcing** – <!-- KFM: Description needed. -->
    - **Detail Level** – Choose a view option for the report. Select one of the following options:
        - *Transactions* – View all relevant transactions in the report. Note that you may experience performance issues when viewing reports that include a large volume of transactions, so we recommend using inventory value report storage when using this option. <!-- KFM: Confirm my reformulation of this point. -->
        - *Totals* – <!-- KFM: Description needed. -->

    - **Include beginning balance** – <!-- KFM: Description needed. -->. This option is only available when **Detail level** is set to *Transactions*.

## New section <!-- KFM: New title is needed -->

<!-- KFM: The purpose of the following information isn't clear. It seems to require a new section (not related to report configuration). I think we are describing the report output, but that should be made clear in a new introduction added here. Maybe we should move this to the examples topic?  -->

Supply Chain Management supports the following two important concepts regarding inventory status: <!-- KFM: Maybe also describe the difference between "amount" and "quantity". -->

- *Financial updated* – Indicates that the inventory transactions are already invoiced. For production orders, it indicates the end of a production order.
- *Physical updated* – Indicates that the inventory transactions aren't yet invoiced, but have been received or shipped. For production orders, it indicates that material has been picked or the production order has been reported as finished.

Understanding these two concepts should make it easy to understand the following columns: <!-- KFM: Where are these columns? Report output? -->

- **Inventory: Financial Quantity** – The quantity that has been financially updated.
- **Inventory: Financial Amount** – The amount value of inventory that has been financially updated.
- **Inventory: Physical Quantity Posted** – The quantity that has been physical updated.
- **Inventory: Physical Amount Posted** – The amount value of inventory that has been physical updated.
- **Inventory: Physical Quantity Not Posted** – The quantity that has inventory transactions but hasn't been posted to the GL <!-- KFM: Spell out "GL". Same as "G/L"? -->. For example, suppose you have an item model group where the **Post physical inventory** and **Post financial inventory** options aren't selected, and you have an item that is linked to this group. Then you create a purchase order, receive it, and invoice it. If you then check the inventory value report for this item, you will see that the quantity and the value in this purchase order are shown under the columns **Inventory: Physical Quantity Not Posted** and **Inventory: Physical Amount Not Posted**.
- **Inventory: Physical Amount Not Posted** – Don't include this amount when doing inventory reconciliation because this amount is not posted into G/L. <!-- KFM: This isn't clear. Doesn't match the other entries in this list. -->
- **Inventory: Quantity** – The total quantity of all the quantity columns in the report.
- **Inventory: Amount** – The total quantity of all the amount columns in the report. Don't use this column when doing inventory reconciliation if your report includes the **Inventory: Physical Amount Not Posted** column. You must exclude **Inventory: Physical Amount Not Posted** from the total amount. <!-- When and how must I exclude this> -->
- **Average unit cost** – The total amount divided by the total quantity.

Normally, you will use the inventory value report to view the inventory value and quantity, but sometimes you won't see all of the relevant inventory dimensions in the report. To make inventory dimensions show in the report:

1. Check the item storage and tracking dimension groups. Only dimensions that have the **Financial inventory** option enabled can be shown in the report.
2. Go to **Cost management \> Inventory accounting policies setup \> Inventory value reports**, select the report configuration that you used to view <!-- KFM: generate? --> the report and make sure the required inventory dimensions are selected. <!-- KFM: View or Total columns? Both? Either?-->

For example, suppose you have an item *A0001*. In the storage dimensions group, only the site is enabled for financial inventory. The site and warehouse are both enabled for physical inventory. In the tracking dimension group, the batch number is enabled for physical inventory but not enabled for financial inventory. Now you use a report configuration where site, warehouse, and batch number are all selected. Then, when you view the report, you will only see a value for the site, and the warehouse and batch number columns are blank. This shows that inventory value reports can only show inventory dimension that are enabled for financial inventory.

## Generate an Inventory value report storage report

Follow these steps to generate and store an **Inventory value storage** report.

1. Go to **Cost management \> Inquiries and reports \> Inventory value report storage**.
1. On the Action Pane, select **New**.
1. The **Inventory value** dialog opens. Make the following settings on the **Parameters** FastTab:
    - **Name** – Enter a unique name for the report
    - **ID** – Select the [inventory value report configuration](#report-configuration) that you want to use for this report. The configuration establishes options for the columns and rows that will be included in your report.
    - **Date interval** – Use the fields in this section to define which records are included in the report. To define the date interval, you can either select a preset range (relative to the report generation date) in the **Date interval code** field, or select specific dates in the **From date** and **To date** fields.
1. On the **Records to include** FastTab, set up filters and constraints to define which data is included in the report. Select **Filter** to open a standard query editor dialog, where you can define selection criteria, sorting criteria, and joins. The fields work just as they do for other types of queries in Supply Chain Management. All of these filters will be applied to the inventory transactions but not the G/L balance <!-- KFM: Spell out "G/L" -->. Keep this in mind when setting up your filters. Otherwise, you may see a discrepancy between inventory and the G/L.
1. On the **Run in the background** FastTab, specify how, when, and how often the report is generated. The fields work just as they do for other types of [background jobs](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management.

    > [!NOTE]
    > This report is always run as part of a batch job.

1. Select **OK** to apply your settings and close the dialog box.

After the batch job is completed, the report will be listed on the **Inventory value report storage** page. You might have to refresh the page to see the report.

> [!IMPORTANT]
> If you select the same date for both **From date** and **To date** and also enable the **Include beginning balance** option in the selected inventory value report configuration, you may get incorrect beginning balance. This is a by-design scenario. <!-- KFM: How/why is this "by design"? -->

## Explore an Inventory value report storage report

After you've generated a report, you can view and explore it at any time by following these steps.

1. Go to **Cost management \> Inquiries and reports \> Inventory value report storage**.
1. Select a report in the list. The page shows the details of the [inventory value report configuration](#report-configuration) that was used to generate the selected report.
1. On the Action Pane, select **View details** to show the report content.
1. Explore the report by following any of these steps:

    - As for most standard pages in Supply Chain Management, you can select almost any column heading to sort or filter the grid by the values in that column.
    - Use the **Filter** field to filter the report by any value in any of several available columns.
    - Use the view menu (above the **Filter** field) to save and load your favorite combinations of sort and filter options.

## Export an Inventory value report storage report

Every report that you generate is stored in the **Inventory value** data entity. You can use the standard data management features of Supply Chain Management to export data from this entity to any supported data format, such as CSV or Excel format.

The following example shows how to export an **Inventory value report** report.

1. Go to **System administration \> Workspaces \> Data management**.
1. In the **Import / Export** section, select the **Export** tile.
1. On the **Export** page that appears, you will set up the export job. First enter a group name for the job.
1. In the **Selected entities** section, select **Add entity**.
1. In the dialog box that appears, set the following fields:

    - **Entity name** – Select **Inventory value**.
    - **Target data format** – Select the format to export data to.

1. Select **Add** to add the new row, and then select **Close** to close the dialog box.
1. Usually, you will export one report at a time. To export a single report, set up a filter for the row that you just added to the **Inquiry** dialog box. In this way, you can define which report from the **Inventory value** entity is included in your export. Follow these steps to set the following filter options to export a single report:

    1. On the **Range** tab, select **Add** to add a row.
    2. Set the **Table** field to **Inventory value**.
    3. Set the **Derived table** field to **Inventory value**.
    4. Set the **Field** field to the field that you want to filter by. Usually, you will use the **Execution name** field and/or the **Execution time** field.
    5. Set the **Criteria** field to the value that you want to look for in the selected field. (If you selected the **Execution name** field in the previous step, this value will be the name of the report. If you selected the **Execution time** field, it will be the time when the report was generated.)
    6. Add more rows to the **Range** tab as you require, until you've uniquely identified the report that you're looking for.

1. Select **OK** to save your settings and close the dialog box.
1. Select **Save** to save your export setup.
1. On the **Export options** tab, select **Export now** to generate the export file.
1. On the **Execution summary** page that appears, you can view the status of your export job and a list of the entities that were exported. In the **Entity processing status** section, select the **Inventory value** entity in the list, and then select **Download file** to download the data that was exported from that entity.

For more information about how to use data management to export data, see [Data import and export jobs overview](../../fin-ops-core/dev-itpro/data-entities/data-import-export-job.md).

## Generate a standard inventory value report

Use the following procedure generate a standard inventory value report:

1. Go to **Cost management \> Inquiries and reports \> Inventory accounting - status reports \> Inventory value.**
1. The **Inventory value report** dialog opens. Make the following settings on the **Parameters** FastTab:
    - **Name** – Enter a unique name for the report
    - **ID** – Select the [inventory value report configuration](#report-configuration) that you want to use for this report. The configuration establishes options for the columns and rows that will be included in your report.
    - **Date interval** – Use the fields in this section to define which records are included in the report. To define the date interval, you can either select a preset range (relative to the report generation date) in the **Date interval code** field, or select specific dates in the **From date** and **To date** fields.
1. On the **Records to include** FastTab, set up filters and constraints to define which data is included in the report. Select **Filter** to open a standard query editor dialog, where you can define selection criteria, sorting criteria, and joins. The fields work just as they do for other types of queries in Supply Chain Management. <!-- KFM: Does the note for this tab in the "storage" report section also apply here? -->
1. On the **Run in the background** FastTab, specify how, when, and how often the report is generated. The fields work just as they do for other types of [background jobs](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management.  <!-- KFM: Which, if any, of these settings is relevant for the standard IV report? -->
1. Select **OK** to apply your settings and close the dialog box, then the report will appear on screen.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]