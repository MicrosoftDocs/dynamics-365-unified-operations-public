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

## Types of inventory value reports

There are two types of inventory value reports: *inventory value report* and *inventory value report storage*.

### The standard inventory value report

The standard *inventory value report* is a simple report that lets you choose what to include and then displays information on your screen. It doesn't save the results, nor does it provide interactive features for filtering, drilling down, browsing, or exporting. For these reasons, we recommend using *inventory value report storage* instead in most cases.

### The inventory value report storage report

The *inventory value report storage* report provides output either as an interactive page in Supply Chain Management or as an exported document in any of several formats.

When you view the report in your browser, columns and aggregate balances are dynamically adjusted, depending on the layout that you've configured. You can sort the results, filter them, drill down into the data, and more.

Report results are stored in the **Inventory value** data entity. Therefore, you can filter and export the results to a format such as comma-separated values (CSV) or Microsoft Excel format.

The *inventory value report storage* report is helpful when the output contains many lines. For example, you have 50,000 items, and 300 stores have been created as warehouses. In this case, if you request inventory ending balances by item, site, and warehouse, the output will contain many lines.

> [!NOTE]
> The inventory value report storage won't include subtotals that are defined in the report layout. It also won't include general ledger balances, even when they are defined in the report layout. Reconciliation to the general ledger must be done by using trial balances. However, the standard inventory value report does include these subtotals and balances.

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
    - **ID** – Enter a short identifier for the report. This value must be unique among all inventory value report configurations, and can't be edited after you save a new configuration.
    - **Name** – Enter a descriptive name for the report.

1. If you are creating a new report configuration, then select **Save** on the Action Pane to enable the remaining settings.
1. Expand the **General** FastTab and make the following settings:  
    - **Date interval** – Choose a pre-defined date interval. This date interval can be overridden when you run the report.
    - **Range** – Choose either *Posting date* or *Transaction Time*, depending on which date and time the report should use when retrieving records for use in the report.
    - **Dimension set** – Choose which set of dimensions (as defined in the general ledger) to run the data for. For example, you might run the data by *Main account*, or by *Main account + Business unit*. You must choose a dimension set that has two or fewer dimensions. See also [Financial dimension sets](../../finance/general-ledger/financial-dimension-sets.md).

1. Expand the **Columns** FastTab and make the following settings. These settings control which columns your report will include and the types of data they will contain.
    - **Inventory** – Set to *Yes* to show the inventory values, which you can then reconcile with the general ledger accounts balances.
    - **WIP** – Set to *Yes* to show the work in process (WIP) values, which you can then reconcile with with WIP accounts balances in the general ledger. When you use this option, only the physical quantities and amounts of inventory in WIP status will show in the report. Production orders that are in WIP status have been picked or reported as finished but not ended.
    - **Deferred COGS** – Set to *Yes* to display a column showing the physical quantities and amounts of inventory for the deferred cost of good sold (deferred COGS). Deferred COGS are shown using physical quantities and amounts because they offset packing slip quantities and amounts.
    - **COGS** – Set to *Yes* to display a column showing the financial quantities and amounts for the cost of goods sold (COGS). COGS are shown using financial quantities and amounts because they offset the invoice quantities and amounts.
    - **Profit and loss** – Set to *Yes* to display a column for the financial amount posted to the profit and loss accounts for inventory.
    - **Print cumulative account values for comparison** – Set to *Yes* to display a column showing the general ledger accounts balance in the report. By doing this, you won't need to check the trail balance. This works only with the *inventory value report*, not *inventory value report storage*. After you enable this option, you must use the following fields to specify each of the general ledger accounts you want to list, depending on which of the **Financial position** options you have enabled (note that choosing a *total* account for any of these settings will show both the amounts of each of the inventory accounts included in the total account and the amount of the total account).
        - **Inventory account** – Specify the general ledger account for which to show inventory information (both **Inventory** and **Print cumulative account values for comparison** must be set to *Yes*).
        - **WIP account** – Specify the general ledger account for which to show WIP information (both **WIP** and **Print cumulative account values for comparison** must be set to *Yes*).
        - **Deferred COGS account** – Specify the general ledger account for which to show deferred COGS information (both **Deferred COGS** and **Print cumulative account values for comparison** must be set to *Yes*).
        - **COGS account** – Specify the general ledger account for which to show COGS information (both **COGS** and **Print cumulative account values for comparison** must be set to *Yes*).

    - **Summarize physical and financial values** – Set to *Yes* to display a column showing the total inventory quantity and inventory amount (summarizing both physical and financial inventory values). When set to *No*, the report report will show both physical and financial inventory values.
    - **Include not posted to ledger** Set to *Yes* to display a column showing the transactions that never posted to the general ledger. This can occur for the following types of items:
        - Received and not yet invoiced items where the **Post physical inventory** option unselected for the relevant item model group.
        - Received and not yet invoiced items when the **Post product receipt in ledger** option isn't selected in **Accounts payable parameters** (**Accounts payable \> Setup \> Accounts payable parameters**, **General** tab, **Product receipt** FastTab).

    - **Calculate average unit cost** – Set to *Yes* to display a column showing the average unit cost. The average unit cost is the total quantity divided by the total amount.
    - **Total quantity and value** – Set to *Yes* to display columns showing the total quantity of physical inventory (and financial quantities) and the total amount of physical inventory (and financial amounts). You can only enable this option when the **Summarize physical and financial values** option is not enabled.
    - **Inventory dimensions** – In this grid, select the **View** check box for each dimension that you want to show in the report. Only dimensions that have the **Financial inventory** option enabled will show values in the report; other dimensions will show only blank columns. For those dimensions you choose to show, you can also mark the **Total** check box to also include totals.
    - **Resource ID** – Set **View** to *Yes* to display a column that identifies the item for each listed row. Set **Total** to *Yes* to also include totals. Depending on the type of item being listed in each row, the information in this column will be one of the following:
        - **Material**: Shows the `ItemID` field value for the relevant material record.
        - **Labor**: Shows the `WorkCenterID` field value for the relevant labor record.
        - **Indirect cost**: Shows the `CodeID` field value for the relevant cost record.

        If neither **Resource ID** nor **Resource Group** has **View** enabled, you will only see a total inventory value based on the inventory dimensions you selected.

    - **Resource Group** – Set **View** to *Yes* to display a column that identifies the resource group for each row. Set **Total** to *Yes* to also include totals. Depending on the type of item being listed in each row, the information in this column will be one of the following:
        - **Material**: Shows the `ItemGroup` field value for the relevant material record.
        - **Labor**: Shows the `WorkcenterGroup` field value for the relevant labor record.
        - **Indirect cost**: Shows the `CostGroup` field value for the relevant cost record (`CostGroupType` must be *Indirect*).

        If neither **Resource ID** nor **Resource Group** has **View** enabled, you will only see a total inventory value based on the inventory dimensions you selected.

1. Expand the **Rows** FastTab and make the following settings. These settings let you add or remove the following WIP-related subsections to the report.
    - **Material** – Set this to *Yes* to show information about materials. Material is a default resource type because materials must be included in all report configurations to create a reliable output.
    - **Labor** – Set this to *Yes* to show labor costs of work in progress.
    - **Indirect cost** – Set this to *Yes* to show indirect costs of work in progress.
    - **Direct outsourcing** – Set this to *Yes* to show direct outsourcing costs of work in progress. This is useful for subcontracting.
    - **Detail Level** – Choose a view option for the report. Select one of the following options:
        - *Transactions* – View all relevant transactions in the report. Note that you may experience performance issues when viewing reports that include a large volume of transactions, so we recommend using inventory value report storage when using this option.
        - *Totals* – View the total result.
    - **Include beginning balance** – Set this to *Yes* to show the beginning balance. This option is only available when **Detail level** is set to *Transactions*.

## Generate an Inventory value report storage report

Follow these steps to generate and store an **Inventory value storage** report.

1. Go to **Cost management \> Inquiries and reports \> Inventory value report storage**.
1. On the Action Pane, select **New**.
1. The **Inventory value** dialog opens. Make the following settings on the **Parameters** FastTab:
    - **Name** – Enter a unique name for the report
    - **ID** – Select the [inventory value report configuration](#report-configuration) that you want to use for this report. The configuration establishes options for the columns and rows that will be included in your report.
    - **Date interval** – Use the fields in this section to define which records are included in the report. To define the date interval, you can either select a preset range (relative to the report generation date) in the **Date interval code** field, or select specific dates in the **From date** and **To date** fields.
1. On the **Records to include** FastTab, set up filters and constraints to define which data is included in the report. Select **Filter** to open a standard query editor dialog, where you can define selection criteria, sorting criteria, and joins. The fields work just as they do for other types of queries in Supply Chain Management. All of these filters will be applied to the inventory transactions but not the general ledger balance. Keep this in mind when setting up your filters. Otherwise, you may see a discrepancy between inventory and the general ledger.
1. On the **Run in the background** FastTab, specify how, when, and how often the report is generated. The fields work just as they do for other types of [background jobs](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management.

    > [!NOTE]
    > This report is always run as part of a batch job.

1. Select **OK** to apply your settings and close the dialog box.

After the batch job is completed, the report will be listed on the **Inventory value report storage** page. You might have to refresh the page to see the report.

> [!IMPORTANT]
> If you select the same date for both **From date** and **To date** and also enable the **Include beginning balance** option in the selected inventory value report configuration, you may get incorrect beginning balance.

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
1. On the **Records to include** FastTab, set up filters and constraints to define which data is included in the report. Select **Filter** to open a standard query editor dialog, where you can define selection criteria, sorting criteria, and joins. The fields work just as they do for other types of queries in Supply Chain Management.
1. On the **Run in the background** FastTab, specify how, when, and how often the report is generated. The fields work just as they do for other types of [background jobs](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management.
1. Select **OK** to apply your settings and close the dialog box, then the report will appear on screen.

## How to read inventory value reports

This section provides some guidance about how to read and understand an inventory value report.

Supply Chain Management supports the following two important concepts regarding inventory status:

- *Financial updated* – Indicates that the inventory transactions are already invoiced. For production orders, it indicates the end of a production order.
- *Physical updated* – Indicates that the inventory transactions aren't yet invoiced, but have been received or shipped. For production orders, it indicates that material has been picked or the production order has been reported as finished.

Understanding these two concepts should make it easy to understand the following columns in the report output:

- **Inventory: Financial Quantity** – The quantity that has been financially updated.
- **Inventory: Financial Amount** – The amount value of inventory that has been financially updated.
- **Inventory: Physical Quantity Posted** – The quantity that has been physical updated.
- **Inventory: Physical Amount Posted** – The amount value of inventory that has been physical updated.
- **Inventory: Physical Quantity Not Posted** – The quantity that has inventory transactions but hasn't been posted to the general ledger. For example, suppose you have an item model group where the **Post physical inventory** and **Post financial inventory** options aren't selected, and you have an item that is linked to this group. Then you create a purchase order, receive it, and invoice it. If you then check the inventory value report for this item, you will see that the quantity and the value in this purchase order are shown under the columns **Inventory: Physical Quantity Not Posted** and **Inventory: Physical Amount Not Posted**.
- **Inventory: Physical Amount Not Posted** – You can set your reports to show un-posted amounts, but if you are using the report for inventory reconciliation, then don't use this value because this amount is not posted to the general ledger.
- **Inventory: Quantity** – The total quantity of all the quantity columns in the report.
- **Inventory: Amount** – The total quantity of all the amount columns in the report. Don't use this column when doing inventory reconciliation if your report includes the **Inventory: Physical Amount Not Posted** column, in which case you must exclude **Inventory: Physical Amount Not Posted** from the total amount.
- **Average unit cost** – The total amount divided by the total quantity.

Normally, you will use the inventory value report to view the inventory value and quantity, but sometimes you won't see all of the relevant inventory dimensions in the report. If you aren't seeing the dimensions you expect, check the following settings:

- Check the item storage and tracking dimension groups. Only dimensions that have the **Financial inventory** option enabled can be shown in the report.
- Go to **Cost management \> Inventory accounting policies setup \> Inventory value reports**, select the report configuration that you used to generate the report and make sure the required inventory dimensions are selected in the **View** column.

For example, suppose you have an item *A0001*. In the storage dimensions group, only the site is enabled for financial inventory. The site and warehouse are both enabled for physical inventory. In the tracking dimension group, the batch number is enabled for physical inventory but not enabled for financial inventory. Now you use a report configuration where site, warehouse, and batch number are all selected. Then, when you view the report, you will only see a value for the site, and the warehouse and batch number columns are blank. This shows that inventory value reports can only show inventory dimension that are enabled for financial inventory.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]