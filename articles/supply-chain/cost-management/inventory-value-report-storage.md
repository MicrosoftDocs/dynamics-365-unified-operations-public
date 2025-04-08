---
title: Inventory value reports
description: Learn how to set up, generate, and use inventory value reports. These reports provide details about your inventory physical and financial quantities.
author: prasungoel
ms.author: prasungoel
ms.topic: how-to
ms.date: 09/03/2024
ms.custom:
  - bap-template
ms.reviewer: kamaybac
ms.search.form: InventValueProcess, InventValueReportSetup, InventValueExecutionHistory, DataManagementWorkspace
---

# Inventory value reports

[!include [banner](../includes/banner.md)]

Inventory value reports provide details about your inventory physical and financial quantities and amounts. You can view the reports in many different ways. For example, you can show totals or transactions, or filter by items or a time range. You can view cost of goods sold (COGS) values or work in process (WIP) values, and set other options.

Inventory value reports let you perform the following tasks:

- Do reconciliation between the general ledger and inventory.
- Consult on-hand inventory and values for a specific period.
- Create report configurations that are tailored to a specific purpose.
- Save report configurations so that they can be used multiple times.
- Add ranges to filter data when you run a report.

## Types of inventory value report

There are two types of inventory value report: **Inventory value** (the standard report) and **Inventory value report storage**.

### Standard Inventory value report

The standard **Inventory value** report is a simple report that lets you select the information that is included and then shows that information on the screen. It doesn't save the results. It also doesn't provide interactive features for filtering, drilling down, browsing, or exporting. For these reasons, we recommend that you use the **Inventory value report storage** report instead in most cases.

### Inventory value report storage report

The **Inventory value report storage** report provides output either as an interactive page in Microsoft Dynamics 365 Supply Chain Management or as an exported document in one of several formats.

When you view the report in your browser, columns and aggregate balances are dynamically adjusted, depending on the layout that you've configured. You can sort the results, filter them, drill down into the data, and more.

Report results are stored in the **Inventory value** data entity. Therefore, you can filter and export the results to a format such as comma-separated values (CSV) or Microsoft Excel format.

The **Inventory value report storage** report is helpful when the output contains many lines. For example, you have 50,000 items, and 300 stores have been created as warehouses. In this case, if you request inventory ending balances by item, site, and warehouse, the output will contain many lines.

> [!NOTE]
> The **Inventory value report storage** report doesn't include subtotals that are defined in the report layout. It also doesn't include general ledger balances, even if those balances are defined in the report layout. Reconciliation to the general ledger must be done by using trial balances. However, the standard **Inventory value** report does include these subtotals and balances.

## Turn the Inventory value report storage feature on or off

To use this feature, it must be turned on for your system. As of Supply Chain Management version 10.0.25, the feature is turned on by default. As of Supply Chain Management version 10.0.29, the feature is mandatory and can't be turned off. If you're running a version older than 10.0.29, then admins can turn this functionality on or off by searching for the *Inventory value report storage* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

## <a name="report-configuration"></a>Define inventory value report configurations

Use the **Inventory value reports** page to set up the content that is included in the different types of inventory value report. You can define any number of report types. Each time that you generate either type of inventory value report, you'll select a report type.

1. Go to **Cost management \> Inventory accounting policies setup \> Inventory value reports**.
1. Follow one of these steps:

    - To edit an existing report, select it in the list pane, and then select **Edit** on the Action Pane.
    - To create a new report, select **New** on the Action Pane.

1. In the header of the new or selected report, set the following fields:

    - **ID** – Enter a short identifier for the report. This value must be unique among all inventory value report configurations. It can't be edited after you save a new configuration.
    - **Name** – Enter a descriptive name for the report.

1. If you're creating a new report configuration, select **Save** on the Action Pane to make the remaining fields available.
1. On the **General** FastTab, set the following fields:

    - **Date interval** – Select a predefined date interval. You can override this date interval when you run the report.
    - **Range** – Select either *Posting date* or *Transaction Time*, depending on the date and time that should be used when records are retrieved for the report.
    - **Dimension set** – Select the set of dimensions to run the data for. (The dimensions are defined in the general ledger.) For example, you might run the data for *Main account* or for *Main account + Business unit*. The dimension set that you select must have no more than two dimensions. Learn more in [Financial dimension sets](../../finance/general-ledger/financial-dimension-sets.md).

1. On the **Columns** FastTab, set the following fields. These fields control the columns that your report includes and the types of data that those columns contain.

    - **Inventory** – Set this option to *Yes* to show the inventory values. You can then reconcile those values with the general ledger account balances.
    - **WIP** – Set this option to *Yes* to show the WIP values. You can then reconcile those values with WIP account balances in the general ledger. When you set this option to *Yes*, the report will show only the physical quantities and amounts of inventory that have WIP status. Production orders that have WIP status have been picked or reported as finished, but they haven't been ended.
    - **Deferred COGS** – Set this option to *Yes* to display a column that shows the physical quantities and amounts of inventory for deferred COGS. Deferred COGS is shown by using physical quantities and amounts, because it offsets packing slip quantities and amounts.
    - **COGS** – Set this option to *Yes* to display a column that shows the financial quantities and amounts for COGS. COGS is shown by using financial quantities and amounts, because it offsets the invoice quantities and amounts.
    - **Profit and loss** – Set this option to *Yes* to display a column that shows the financial amount that was posted to the profit and loss accounts for inventory.
    - **Print cumulative account values for comparison** – Set this option to *Yes* to display a column that shows the general ledger account balance. In this way, you won't have to check the trail balance. This option works only with the standard **Inventory value** report, not with the **Inventory value report storage** report. After you set this option to *Yes*, you must use the following fields to specify each general ledger account that you want to list, depending on the **Financial position** options that you've enabled.

        > [!NOTE]
        > If you select a *total* account for any of these fields, both the amount of each inventory account that is included in the total account and the amount of the total account will be shown.

        - **Inventory account** – Specify the general ledger account to show inventory information for. (Both the **Inventory** option and the **Print cumulative account values for comparison** option must be set to *Yes*.)
        - **WIP account** – Specify the general ledger account to show WIP information for. (Both the **WIP** option and the **Print cumulative account values for comparison** option must be set to *Yes*.)
        - **Deferred COGS account** – Specify the general ledger account to show deferred COGS information for. (Both the **Deferred COGS** option and the **Print cumulative account values for comparison** option must be set to *Yes*.)
        - **COGS account** – Specify the general ledger account to show COGS information for. (Both the **COGS** option and the **Print cumulative account values for comparison** option must be set to *Yes*.)

    - **Summarize physical and financial values** – Set this option to *Yes* to display a column that shows the total inventory quantity and inventory amount (a summary of both physical and financial inventory values). If this option is set to *No*, the report will show both physical and financial inventory values.
    - **Include not posted to ledger** Set this option to *Yes* to display a column that shows the transactions that were never posted to the general ledger. Transactions for the following types of items might not be posted to the general ledger:

        - Received and not yet invoiced items when the **Post physical inventory** option is cleared for the relevant item model group.
        - Received and not yet invoiced items when the **Post product receipt in ledger** option is cleared on the **Product receipt** FastTab on the **General** tab of the **Accounts payable parameters** page (**Accounts payable \> Setup \> Accounts payable parameters**).

    - **Calculate average unit cost** – Set this option to *Yes* to display a column that shows the average unit cost. The average unit cost is the total amount divided by the total quantity.
    - **Total quantity and value** – Set this option to *Yes* to display columns that show the total quantity of physical inventory (and financial quantities) and the total amount of physical inventory (and financial amounts). You can set this option to *Yes* only if the **Summarize physical and financial values** option is set to *No*.
    - **Inventory dimensions** – In this grid, select the **View** checkbox for each dimension that you want to show on the report. Only dimensions where the **Financial inventory** option is enabled will show values on the report. Other dimensions will show only blank columns. For those dimensions that you select to show, you can select the **Total** checkbox to include totals too.
    - **Resource ID** – Set the **View** option to *Yes* to display a column that identifies the item for each row. Set the **Total** option to *Yes* to include totals too. Depending on the type of item that is listed in each row, the column shows one of the following types of information:

        - **Material** – The column shows the `ItemID` field value for the relevant material record.
        - **Labor** – The column shows the `WorkCenterID` field value for the relevant labor record.
        - **Indirect cost** – The column shows the `CodeID` field value for the relevant cost record.

        If the **View** option is set to *No* for both the **Resource ID** field and the **Resource Group** field, you'll see only a total inventory value that is based on the inventory dimensions that you selected.

    - **Resource Group** – Set the **View** option to *Yes* to display a column that identifies the resource group for each row. Set the **Total** option to *Yes* to include totals too. Depending on the type of item that is listed in each row, the column shows one of the following types of information:

        - **Material** – The column shows the `ItemGroup` field value for the relevant material record.
        - **Labor** – The column shows the `WorkcenterGroup` field value for the relevant labor record.
        - **Indirect cost** – The column shows the `CostGroup` field value for the relevant cost record. (The `CostGroupType` value must be *Indirect*.)

        If the **View** option is set to *No* for both the **Resource ID** field and the **Resource Group** field, you'll see only a total inventory value that is based on the inventory dimensions that you selected.

1. On the **Rows** FastTab, set the following fields. These fields let you add corresponding WIP-related subsections to the report or remove them.

    - **Material** – Set this option to *Yes* to show information about materials. *Material* is a default resource type because materials must be included in all report configurations to create reliable output.
    - **Labor** – Set this option to *Yes* to show labor costs of WIP.
    - **Indirect cost** – Set this option to *Yes* to show indirect costs of WIP.
    - **Direct outsourcing** – Set this option to *Yes* to show direct outsourcing costs of WIP. This information is useful for subcontracting.
    - **Detail Level** – Select a view option for the report:

        - *Transactions* – View all relevant transactions on the report. You might experience performance issues when you view reports that include a large volume of transactions. Therefore, if you want to use this view option, we recommend that you use the **Inventory value report storage** report.
        - *Totals* – View the total result.

    - **Include beginning balance** – Set this option to *Yes* to show the beginning balance. This option is available only when the **Detail level** field is set to *Transactions*.

## Generate an Inventory value report storage report

Follow these steps to generate and store an **Inventory value report storage** report.

1. Go to **Cost management \> Inquiries and reports \> Inventory value report storage**.
1. On the Action Pane, select **New**.
1. In the **Inventory value** dialog box, on the **Parameters** FastTab, set the following fields:

    - **Name** – Enter a unique name for the report.
    - **ID** – Select the [inventory value report configuration](#report-configuration) to use for the report. The configuration establishes options for the columns and rows that will be included on your report.
    - **Date interval** – Use the fields in this section to define which records are included on the report. To define the date interval, you can either select a preset range (relative to the report generation date) in the **Date interval code** field, or select specific dates in the **From date** and **To date** fields.

1. On the **Records to include** FastTab, set up filters and constraints to define which data is included on the report. Select **Filter** to open a standard query editor dialog, where you can define selection criteria, sorting criteria, and joins. The fields work just as they do for other types of queries in Supply Chain Management. All these filters will be applied to the inventory transactions but not to the general ledger balance. Keep this behavior in mind when you set up your filters. Otherwise, you might see a discrepancy between inventory and the general ledger.
1. On the **Run in the background** FastTab, specify how, when, and how often the report is generated. The fields work just as they do for other types of [background jobs](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management.

    > [!NOTE]
    > This report is always run as part of a batch job.

1. Select **OK** to apply your settings and close the dialog box.

After the batch job is completed, the report will be listed on the **Inventory value report storage** page. You might have to refresh the page to see the report.

> [!IMPORTANT]
> In the selected inventory value report configuration, you might get an incorrect beginning balance if you select the same date in both the **From date** field and the **To date** field, and if you also set the **Include beginning balance** option to *Yes*.

## Explore an Inventory value report storage report

After you've generated a report, you can view and explore it at any time by following these steps.

1. Go to **Cost management \> Inquiries and reports \> Inventory value report storage**.
1. Select a report in the list. The page shows the details of the [inventory value report configuration](#report-configuration) that was used to generate the selected report.
1. On the Action Pane, select **View details** to show the report content.
1. Explore the report by following any of these steps:

    - As for most standard pages in Supply Chain Management, you can select almost any column heading to sort or filter the grid by the values in that column.
    - Use the **Filter** field to filter the report by any value in any of several available columns.
    - Use the view menu (above the **Filter** field) to save and load your favorite combinations of sort and filter options.

## <a name="export-stored-report"></a>Export an Inventory value report storage report

Every report that you generate is stored in the **Inventory value** data entity. You can use the standard data management features of Supply Chain Management to export data from this entity to any supported data format, such as CSV or Excel format.

The following example shows how to export an **Inventory value report storage** report.

1. Go to **System administration \> Workspaces \> Data management**.
1. In the **Import / Export** section, select the **Export** tile.
1. On the **Export** page, enter a **Group name** for the job.
1. On the **Selected entities** FastTab, select **Add entity**.
1. In the **Add entity** drop-down dialog, set the following fields:

    - **Entity name** – Select *Inventory value report storage*.
    - **Target data format** – Select the format to export data to.

1. Select **Add** to add the new row, and then select **Close** to close the dialog box.
1. Usually, you'll export one report at a time. To export a single report, select the button in the **Filter** column for the row that you just added to **Selected entities** FastTab. Then use the query designer to set up the following filter:
    - **Table** – Select *Inventory value report storage*.
    - **Field** – Select *Execution name*.
    - **Criteria** – Enter the name of the report that you want to export.

1. On the Action Pane, select **Save**.
1. On the Action Pane, open the **Export options** tab and select **Export now**.
1. The **Execution summary** page opens. Here you can view the status of your export job and a list of the entities that were exported. In the **Entity processing status** section, select the **Inventory value** entity in the list, and then select **Download file** to download the data that was exported from that entity.

For more information about how to use data management to export data, see [Data import and export jobs overview](../../fin-ops-core/fin-ops/data-entities/data-import-export-job.md)

## Delete stored inventory value reports

As the number of stored inventory value reports increases, they might eventually begin to take up too much space in your database. This situation can affect system performance and cause higher data-storage costs. Therefore, you'll probably have to clean up the reports from time to time by deleting older reports.

> [!IMPORTANT]
> Before you delete any of your previously generated inventory value reports, we strongly recommend that you first [export the reports](#export-stored-report) and store them externally, because you might not be able to regenerate them again later. This limitation exists because when you generate an inventory value report, the system works backwards from today and processes each inventory transaction record in reverse order as it goes. If you try to look too far back when you generate a report, the volume of transactions to process might eventually become so large that the system will time out before it can finish generating the report. The distance into the past that you can generate new reports for depends on the number of inventory transactions that you have in your system for the relevant time span.

### Delete one report at a time

Follow these steps to delete one stored report at a time.

1. [Export the report](#export-stored-report) that you're planning to delete, and store it in an external location for future reference.
1. Go to **Cost management \> Inquiries and reports \> Inventory value report storage**.
1. In the list pane, select the report to delete.
1. On the Action Pane, select **Delete**.
1. A warning message reminds you to back up generated reports. Select **Yes** if you're ready to proceed with the deletion.

### Delete several reports at the same time

Follow these steps to delete several stored reports at the same time.

1. [Export all the reports](#export-stored-report) that you're planning to delete, and store them in an external location for future reference.
1. Go to **Cost management \> Inventory accounting \> Clean up \> Inventory value report data clean up**.
1. In the **Inventory value report data clean up** dialog box, in the **Delete inventory value report executed before** field, select the date before which all inventory value reports should be deleted.
1. On the **Records to include** FastTab, you can set additional filter conditions to limit the set of reports that will be deleted. Select **Filter** to open a standard query editor where you can define the properties of the reports to delete.
1. On the **Run in the background** FastTab, you can specify how, when, and how often the reports should be deleted. The fields work just as they do for other types of [background jobs](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management. However, you'll typically run this job manually each time that it's required.
1. Select **OK** to delete the specified reports.

## Generate a standard Inventory value report

Use the following procedure generate a standard **Inventory value** report.

1. Go to **Cost management \> Inquiries and reports \> Inventory accounting - status reports \> Inventory value**.
1. In the **Inventory value report** dialog box, on the **Parameters** FastTab, set the following fields:

    - **Name** – Enter a unique name for the report.
    - **ID** – Select the [inventory value report configuration](#report-configuration) to use for the report. The configuration establishes options for the columns and rows that will be included in your report.
    - **Date interval** – Use the fields in this section to define which records are included on the report. To define the date interval, you can either select a preset range (relative to the report generation date) in the **Date interval code** field, or select specific dates in the **From date** and **To date** fields.

1. On the **Records to include** FastTab, set up filters and constraints to define which data is included on the report. Select **Filter** to open a standard query editor dialog, where you can define selection criteria, sorting criteria, and joins. The fields work just as they do for other types of queries in Supply Chain Management.
1. On the **Run in the background** FastTab, specify how, when, and how often the report is generated. The fields work just as they do for other types of [background jobs](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management.
1. Select **OK** to apply your settings and close the dialog box. The report appears.

## Reading inventory value reports

This section provides some guidance about how to read and understand an inventory value report.

Supply Chain Management supports the following two important concepts that are related to inventory status:

- **Financial updated** – This concept indicates that the inventory transactions are already invoiced. For production orders, it indicates the end of a production order.
- **Physical updated** – This concept indicates that the inventory transactions haven't yet been invoiced, but they have been received or shipped. For production orders, it indicates that material has been picked or the production order has been reported as finished.

When you understand these two concepts, it should be easy to understand the following columns in the report output:

- **Inventory: Financial Quantity** – The quantity that has been financially updated.
- **Inventory: Financial Amount** – The amount value of inventory that has been financially updated.
- **Inventory: Physical Quantity Posted** – The quantity that has been physical updated.
- **Inventory: Physical Amount Posted** – The amount value of inventory that has been physical updated.
- **Inventory: Physical Quantity Not Posted** – The quantity that has inventory transactions but hasn't been posted to the general ledger. For example, you have an item model group where the **Post physical inventory** and **Post financial inventory** options are cleared, and you have an item that is linked to that group. You then create a purchase order, receive it, and invoice it. At this point, if you review the inventory value report for the item, you'll see that the quantity and the value on the purchase order are shown in the **Inventory: Physical Quantity Not Posted** and **Inventory: Physical Amount Not Posted** columns.
- **Inventory: Physical Amount Not Posted** – You can set up your reports so that they show unposted amounts. However, if you're using the report for inventory reconciliation, don't use this value. Otherwise, the amount isn't posted to the general ledger.
- **Inventory: Quantity** – The total quantity of all the quantity columns on the report.
- **Inventory: Amount** – The total quantity of all the amount columns on the report. When you do inventory reconciliation, don't use this column if your report includes the **Inventory: Physical Amount Not Posted** column. In this case, you must exclude the **Inventory: Physical Amount Not Posted** amount from the total amount.
- **Average unit cost** – The total amount divided by the total quantity.

Typically, you'll use an inventory value report to view the inventory value and quantity. However, sometimes the report won't show all the relevant inventory dimensions. If you don't see the dimensions that you expect, validate the following settings:

- Review the item storage and tracking dimension groups. Only dimensions where the **Financial inventory** option is enabled can be shown on the report.
- Go to **Cost management \> Inventory accounting policies setup \> Inventory value reports**, select the report configuration that you used to generate the report, and make sure that the required inventory dimensions are selected in the **View** column.

For example, you have an item that has the item number *A0001*. In the storage dimensions group, only the site is enabled for financial inventory. The site and warehouse are both enabled for physical inventory. In the tracking dimension group, the batch number is enabled for physical inventory but not for financial inventory. You then use a report configuration where site, warehouse, and batch number are all selected. When you view the report, you see a value only for the site. The columns for the warehouse and batch number are blank. As this example shows, inventory value reports can show only inventory dimensions that are enabled for financial inventory.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
