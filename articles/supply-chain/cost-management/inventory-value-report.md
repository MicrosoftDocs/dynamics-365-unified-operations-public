---
title: Inventory value reports
description: The inventory value report shows inventory physical/financial quantities and amounts. It can show totals or transactions using COGS values or WIP values.
author: banluo-ms
ms.date: 10/19/2021
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: banluo
ms.search.validFrom: 2021-10-10
ms.dyn365.ops.version: 10.0.22
---

# Inventory value reports

[!include [banner](../includes/banner.md)]

## Purpose of the inventory value report

Inventory value report is a very powerful report that shows the inventory physical/financial quantities and amounts where it can be presented in different ways such as in totals or in transactions, filtered on a specific period, specific items or with no filter at all, can be used to see the COGS values, to see the WIP values, and other more options.

With the Inventory value report framework, you can:

- Most of the users uses this report to do reconciliation between general ledger and inventory.
- Consult the on-hand and values for a specific period.
- Create a report configuration that is tailored for a specific purpose.
- Save a report configuration with a unique ID so that it can be used multiple times.
- Add ranges to filter data when you run a report.

## Turn on the inventory value report feature

Before you can use this feature, it must be turned on in your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module** – Cost management
- **Feature name** – Inventory value report storage

## Contains/setup (Inventory Value Report ID)

1. Navigate To: **Cost management \> Inventory accounting policies setup \> Inventory value reports**.
1. Click **New** and type in a unique **ID** and descriptive **Name**.
1. Expand the FastTabs to choose where the data for the report is coming from:  

    - For the **Date interval** field you can choose a pre-defined date interval and this date interval can be overridden before executing the report.
    - For the **Range** field you can choose between "Posting date" or "Transaction Time" and upon which value the report data will be retrieved.
    - For the **Dimension Set** field you can choose what is the dimension set to run the data for, For example, by Main Account, or by Main Account + Business Unit. Please note that the dimension set can have a maximum of 2 dimensions.
    - For the columns of **Financial position**, you can only mark **Inventory** if you want to reconcile the inventory value with inventory G/L accounts balance. Or you can only mark **WIP**, if you want to reconcile the WIP value with WIP G/L accounts balance.
    - If you mark the **WIP** option, only the physical quantities and amounts of inventory in WIP status will show in the report. In WIP status means production orders that have been picked or reported finished but not ended.
    - If you mark the **Deferred COGS** and **COGS** options, the report will display the physical quantities and amounts of inventory for the mark of Deferred COGS and will display the financial quantities and amounts for the mark of COGS. The Deferred COGS are the physical quantities and amounts because they offset packing slip quantities and amounts, however, the COGS are the financial quantities and amounts because they offset the invoice quantities and amounts.
    - If you mark the **Profit and loss** option, the report display the financial amount posted to the Profit and loss accounts for inventory.
    - Please enable the option **Print cumulative account values for comparison**, if you want the G/L accounts balance showing in the report. By doing this, you don't need to check the trail balance. This works only with the Inventory value report not the inventory value report storage. Please note that choosing a Total account will show the amounts of each of the inventory accounts included in the total account and the amount of the total account as well.
    - After you enable this option, you need to fill in the G/L account you want to reconcile.
    - For the **Inventory dimensions** area, you can select the dimensions that you want to show in the report. Please be noted that only the dimensions that have **Financial inventory** option enabled can be showed in the report, otherwise you will only see blank columns.
    - The **Summarize physical and financial values** option If it's marked the report will show the total inventory quantity and inventory amount (summarizing both physical and financial inventory values). If it's not marked the report will show both physical and financial inventory values.
    - The **Include not posted to ledger** option shows those transactions that never posted to G/L. This can be caused by:
        - The Item is received and not yet invoiced, where the item model group with the field Post physical inventory not marked.
        - The Item is received and not yet invoiced, where in Accounts payable parameters &gt; General tab &gt; Product receipt &gt; with the field Post product receipt in ledger not marked.

    - The **Average Unit Cost** option is suggested to be marked if you want to check the average unit cost. The Average Unit Cost is just a simple calculation: total quantity divided by the total amount.
    - The **Total quantity and value** option can only be marked when the **Summarize physical and financial values** option is not marked. The report will show additional two columns for the total quantity of inventory physical and financial quantities and the total amount of inventory physical and financial amounts.
    - The **Resource ID** mostly means the item number. The information in the Resource column of the inventory value report is based on a combination of ItemID, WorkcenterID, and CodeID.
        - Material: Resource = ItemID
        - Labor: Resource = WorkCenterID
        - Indirect cost: Resource = CodeID

    - The **Resource Group** mostly mean item group.The information in the Resource column of the inventory value report is based on a combination of ItemGroup, WorkcenterGroup, and CostGroup (CostGroupType = Indirect).
        - Material: Resource = ItemGroup
        - Labor: Resource = WorkcenterGroup
        - Indirect cost: Resource = CostGroup

    - If either **Resource ID** or **Resource Group** are not marked, you will only see a total inventory value based on the inventory dimensions you selected.
    - The option **Detail Level** enable the user to select different view of the report. If you want to view the report per transactions, you can select transactions. Otherwise, please select "Total". Please be noticed that there might be slow performance issue if you are trying to view a large volume of data on "Transactions" level and for that it is recommended to use inventory value report storage.
    - The option **Include beginning balance** is only available when you select "Transactions" in detail level option.
    - In the system there are two important concepts, financial updated and physical updated. Financial updated means the inventory transactions are already invoiced (For production orders, it's production order end.). Physical updated means the inventory transactions are not invoice but received or shipped. (For production order, it means material picked or production order report as finished). After understanding the two concepts, it will be easy to understand the below columns.
        - **Inventory: Financial Quantity** – the quantity that are financially updated.
        - **Inventory: Financial Amount** –the amount value of inventory that are financially updated.
        - **Inventory: Physical Quantity Posted** – the quantity that are physical updated.
        - **Inventory: Physical Amount Posted** – the amount value of inventory that are physical updated.
        - **Inventory: Physical Quantity Not Posted** –the quantity that has inventory transactions but not posted to the GL. For example, you have item model group which has the options "post physical inventory" and "post financial inventory" disabled. Then you have an item which linked to this item group. Then you have a purchase order, you receive it and invoice it. Then if you check the inventory value report for this item, you will see the quantity and the value in this purchase order are actually under the column "Inventory: Physical Quantity Not Posted" and "Inventory: Physical Amount Not Posted"
        - **Inventory: Physical Amount Not Posted** – please do not include this amount when you do the inventory reconciliation because this amount is not post into G/L.
        - **Inventory: Quantity** –the total quantity of all the qty columns in the report.
        - **Inventory: Amount** – the total quantity of all the amount columns in the report. Like the note above, please do not use this column to do the inventory reconciliation if you have the "Inventory: Physical Amount Not Posted" showed in the report. You need to exclude "Inventory: Physical Amount Not Posted" from the total amount.
        - **Average unit cost** – total amount divided by total quantity.

    - Normally, we use inventory value report to view the inventory value and quantity. Sometimes, we cannot see some inventory dimensions in the report. To make the inventory dimensions showing in the report, you need to make sure:
        - Check the item storage and tracking dimension groups. Only the dimensions that have the option "financial inventory" enabled can be shown in the report.
        - Go to Cost management &gt; Inventory accounting policies setup &gt; Inventory value reports, select the inventory value report ID which you use to view the report and make sure the inventory dimensions are selected.

    - For example, there is an item "test". In the storage dimensions group, only site is financial inventory enabled. Site and warehouse are both physical inventory enabled. In the tracking dimension group, batch number is physical inventory enabled while financial inventory is disabled.
    - Now in the inventory value report ID settings, site, warehouse and batch number are all selected. If we view the report, we can only see site is shown in the report while warehouse and batch number columns are blank.
    - In conclusion, inventory value report can only show the inventory dimensions which are financial inventory enabled.

## Generate inventory value reports

The inventory value has two options: **Inventory value report** and **Inventory value report storage**.

### Generate an inventory value report

1. Go to **Cost management &gt; Inquiries and reports &gt; Inventory accounting - status reports &gt; Inventory value.**
1. In the dialog box that appears, set the following values to define which records are included in your report:
    - On the **Parameters** FastTab, the **Date interval code** is used when you want to view the predefined period instead of giving the **From date** and **To date**. For example, if you select **current period** in this parameter, the report will calculate the **From date** and **To date** based on the current session date. If you don't use date interval code, you can manually fill the **From date** and **To date** based on your need.
    - On the **Records to include** FastTab, set up filters and constraints to define which data is included in the report.
    - On the **Run in the background** FastTab, specify how, when, and how often the report is generated.

1. Select **OK** to apply your settings and close the dialog box, then the report will appear on screen.

### Generate an inventory value report storage

1. go to **Cost management &gt; Inquiries and reports &gt; Inventory value report storage**.
1. Click **New**.
1. In the dialog box that appears, set the following values to define which records are included in your report:

    - On the **Parameters** FastTab, for **Inventory value report storage** enter a unique name for the report. The **Date interval code** is used when you want to view the predefined period instead of giving the **From date** and **To date**. For example, if you select **current period** in this parameter, the report will calculate the **From date** and **To date** based on the current session date. If you don't use date interval code, you can manually fill the **From date** and **To date** based on your need.
    - On the **Records to include** FastTab, set up filters and constraints to define which data is included in the report.
    - On the **Run in the background** FastTab, specify how, when, and how often the report is generated.

    The **Inventory value report storage** report is always run as part of a batch job. After the batch job is completed, the report will be listed on the **Inventory value report storage** page. You might have to refresh the page to see the report.

1. Select a report in the list.
1. Select **View details** to show the report content.

There is one known issue. When you select the same date for both **From date** and **To date** and also enable **include beginning balance** option in inventory value report ID, you may get incorrect beginning balance. This is a by-design scenario.

All the filters in the **Records to include** section will be applied to the inventory transactions but not the G/L balance. So, when you try to use these filters, please keep this in mind. Otherwise, you may see the discrepancy between inventory and G/L account which is caused improper usage of the filters.

## Inventory value report examples and logic

The examples in this topic show results that are presented on a standard **Inventory value** report. Also, we will show **Inventory value report storage**, as we recommend that you use the **Inventory value report storage** version of this report, especially when you have many items and warehouses that must be processed. Inventory value report storage saves each report that you generate, shows the results as an interactive page, and lets you export any saved report.

### Sample data that is used in these examples

The examples in this topic are based on the sample inventory transaction data that is described in this section.

#### Storage dimension setup

The example system contains the following setup of storage dimensions.

| **Name** | **Active** | **Physical inventory** | **Financial inventory** |
|---|---|---|---|
| Site | Yes | Yes | Yes |
| Warehouse | Yes | Yes | No |

#### Inventory model

For the example system, the inventory model for the released products is *FIFO*, and the **Cost price** setting for the inventory model is *Include physical value*.

#### Inventory transactions

The example system contains the following inventory transactions for a released product that has the item number *B0001*.

| Reference | Site | Warehouse | Receipt | Issue | Physical date | Financial date | Quantity | Cost amount | Physical cost amount |
|---|---|---|---|---|---|---|---|---|---|
| Purchase order | 1 | 11 | Purchased | | March 15 | March 15 | 10 | 1,000 | 1,000 |
| Purchase order | 2 | 21 | Purchased | | March 15 | March 15 | 10 | 2,000 | 2,000 |
| Purchase order | 1 | 11 | Received | | April 15 | | 5 | | 375 |
| Transfer order | 1 | 11 | | Sold | May 2 | May 2 | -5 | -458.33 | -458.33 |
| Transfer order | 1 | 12 | Purchased | | May 2 | May 2 | 5 | 458.33 | 458.33 |
| Sales order | 1 | 12 | | Sold | May 3 | May 3 | -1 | -91.67 | -91.67 |

### Inventory value report example 1

By using the sample data that is described in the previous sections, you can run an **Inventory value** report that has the following **ID** settings:

- **Range:**  *Posting date*
- **Inventory:** *Yes*
- **Calculate average unit cost:** *Yes*
- **Total quantity and value:** *Yes*
- **Site View:** *Marked*
- **RESOURCE ID View:** *Yes*
- **Level:** *Totals*

| Resource type | Resource | Site | Reference | Inventory: Financial quantity | Inventory: Financial amount | Inventory: Physical quantity posted | Inventory: Physical amount posted | Inventory: Quantity | Inventory: Amount | Average unit cost |
|---|---|---|---|---|---|---|---|---|---|---|
| Material | B0001 | 1 | Ending balance | 9.00 | 908.33 | 5.00 | 375.00 | 14.00 | 1,283.33 | 91.67 |
| Material | B0001 | 2 | Ending balance | 10.00 | 2,000.00 | 0.00 | 0.00 | 10.00 | 2,000.00 | 200.00 |

#### Inventory value report for example 1

The following screenshot shows the inventory value report for example 1 (select to enlarge).

[![Inventory value report for example 1](media/inventory-value-report-ex1-small.png "Inventory value report for example 1")](media/inventory-value-report-ex1.png)

#### Inventory value report storage for example 1

The following screenshot shows the inventory value report storage for example 1 (select to enlarge).

[![Inventory value report storage for example 1](media/inventory-value-report-storage-ex1-small.png "Inventory value report storage for example 1")](media/inventory-value-report-storage-ex1.png)

### Inventory value report example 2

By using the same data that is described in the previous sections, but on **Level**: *Transactions* and **From date:** *March 15.*

| Resource type | Resource | Site | Date | Number | Reference | Inventory: Financial quantity | Inventory: Financial amount | Inventory: Physical quantity posted | Inventory: Physical amount posted | Inventory: Quantity | Inventory: Amount |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Material | B0001 | 1 | 3/15/2021 | 00000126 | Purchase order | 0.00 | 0.00 | 10.00 | 1,000.00 | **10.00** | **1,000.00** |
| Material | B0001 | 1 | 3/15/2021 | 00000126 | Purchase order | 10.00 | 1,000.00 | -10.00 | -1,000.00 | **0.00** | **0.00** |
| Material | B0001 | 1 | 4/15/2021 | 00000128 | Purchase order | 0.00 | 0.00 | 5.00 | 375.00 | **5.00** | **375.00** |
| Material | B0001 | 1 | 5/2/2021 | 000003 | Transfer order shipment | -5.00 | -458.33 | 0.00 | 0.00 | **-5.00** | **-458.33** |
| Material | B0001 | 1 | 5/2/2021 | 000003 | Transfer order receive | 5.00 | 458.33 | 0.00 | 0.00 | **5.00** | **458.33** |
| Material | B0001 | 1 | 5/3/2021 | 000835 | Sales order | 0.00 | 0.00 | -1.00 | -91.67 | **-1.00** | **-91.67** |
| Material | B0001 | 1 | 5/3/2021 | 000835 | Sales order | -1.00 | -91.67 | 1.00 | 91.67 | **0.00** | **0.00** |
| Material | B0001 | 2 | 3/15/2021 | 00000127 | Purchase order | 0.00 | 0.00 | 10.00 | 2,000.00 | **10.00** | **2,000.00** |
| Material | B0001 | 2 | 3/15/2021 | 00000127 | Purchase order | 10.00 | 2,000.00 | -10.00 | -2,000.00 | **0.00** | **0.00** |
| Material | B0001 | 2 | 5/2/2021 | 000003 | Transfer order shipment | 5.00 | 458.33 | 0.00 | 0.00 | **5.00** | **458.33** |
| Material | B0001 | 2 | 5/2/2021 | 000003 | Transfer order receive | -5.00 | -458.33 | 0.00 | 0.00 | **-5.00** | **-458.33** |

#### Inventory value report for example 2

The following screenshot shows the inventory value report for example 2 (select to enlarge).

[![Inventory value report for example 2](media/inventory-value-report-ex2-small.png "Inventory value report for example 2")](media/inventory-value-report-ex2.png)

#### Inventory value report storage for example 2

The following screenshot shows the inventory value report storage for example 2 (select to enlarge).

[![Inventory value report storage for example 2](media/inventory-value-report-storage-ex2-small.png "Inventory value report storage for example 2")](media/inventory-value-report-storage-ex2.png)

### Inventory value report example 3

Note that it is recommended to execute the inventory value report after the recalculation/inventory closing to have the transactions and amounts affected by the recalculation/inventory closing.

Below are the inventory value report values after inventory closing till May 30.

#### Example 3 using the totals level

**Level:** *Totals*

| Resource type | Resource | Site | Reference | Inventory: Financial quantity | Inventory: Financial amount | Inventory: Physical quantity posted | Inventory: Physical amount posted | Inventory: Quantity | Inventory: Amount | Average unit cost |
|---|---|---|---|---|---|---|---|---|---|---|
| Material | B0001 | 1 | Ending balance | 9.00 | 900.00 | 5.00 | 375.00 | 14.00 | 1,275.00 | 91.07 |
| Material | B0001 | 2 | Ending balance | 10.00 | 2,000.00 | 0.00 | 0.00 | 10.00 | 2,000.00 | 200.00 |

#### Example 3 using the transactions level

**Level**: *Transactions*

| Resource type | Resource | Site | Date | Number | Reference | Inventory: Financial quantity | Inventory: Financial amount | Inventory: Physical quantity posted | Inventory: Physical amount posted | Inventory: Quantity | Inventory: Amount |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Material | B0001 | 1 | 3/15/2021 | 00000126 | Purchase order | 0.00 | 0.00 | 10.00 | 1,000.00 | 10.00 | 1,000.00 |
| Material | B0001 | 1 | 3/15/2021 | 00000126 | Purchase order | 10.00 | 1,000.00 | -10.00 | -1,000.00 | 0.00 | 0.00 |
| Material | B0001 | 1 | 4/15/2021 | 00000128 | Purchase order | 0.00 | 0.00 | 5.00 | 375.00 | 5.00 | 375.00 |
| Material | B0001 | 1 | 5/2/2021 | 000003 | Transfer order shipment | -5.00 | -458.33 | 0.00 | 0.00 | -5.00 | -458.33 |
| Material | B0001 | 1 | 5/2/2021 | 000003 | Transfer order receive | 5.00 | 458.33 | 0.00 | 0.00 | 5.00 | 458.33 |
| Material | B0001 | 1 | 5/3/2021 | 000835 | Sales order | 0.00 | 0.00 | -1.00 | -91.67 | -1.00 | -91.67 |
| Material | B0001 | 1 | 5/3/2021 | 000835 | Sales order | -1.00 | -91.67 | 1.00 | 91.67 | 0.00 | 0.00 |
| Material | B0001 | 1 | 5/31/2021 | 000835 | Sales order | 0.00 | -8.33 | 0.00 | 0.00 | 0.00 | -8.33 |
| Material | B0001 | 1 | 5/31/2021 | 000003 | Transfer order shipment | 0.00 | -41.67 | 0.00 | 0.00 | 0.00 | -41.67 |
| Material | B0001 | 1 | 5/31/2021 | 000003 | Transfer order receive | 0.00 | 41.67 | 0.00 | 0.00 | 0.00 | 41.67 |
| Material | B0001 | 2 | 3/15/2021 | 00000127 | Purchase order | 0.00 | 0.00 | 10.00 | 2,000.00 | 10.00 | 2,000.00 |
| Material | B0001 | 2 | 3/15/2021 | 00000127 | Purchase order | 10.00 | 2,000.00 | -10.00 | -2,000.00 | 0.00 | 0.00 |
| Material | B0001 | 2 | 5/2/2021 | 000003 | Transfer order shipment | 5.00 | 458.33 | 0.00 | 0.00 | 5.00 | 458.33 |
| Material | B0001 | 2 | 5/2/2021 | 000003 | Transfer order receive | -5.00 | -458.33 | 0.00 | 0.00 | -5.00 | -458.33 |
| Material | B0001 | 2 | 5/31/2021 | 000003 | Transfer order shipment | 0.00 | 41.67 | 0.00 | 0.00 | 0.00 | 41.67 |
| Material | B0001 | 2 | 5/31/2021 | 000003 | Transfer order receive | 0.00 | -41.67 | 0.00 | 0.00 | 0.00 | -41.67 |
