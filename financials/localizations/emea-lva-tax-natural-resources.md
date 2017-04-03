---
# required metadata

title: Tax on natural resources report
description: This topic explains how to set up and generate the Tax on natural resources (NR Tax) report.
author: ShylaThompson
manager: AnnBe
ms.date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: LvNRTaxItemGroupLookup
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 81
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 270454
ms.assetid: ca5fb637-e01b-4499-9bc4-51da02b8c61a
ms.search.region: Latvia
# ms.search.industry: 
ms.author: v-lenest
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Tax on natural resources report

This topic explains how to set up and generate the Tax on natural resources (NR Tax) report.

Latvian companies must periodically submit a **Tax on natural resources** (**NR tax**) report. This functionality applies only to legal entities in Latvia. Tax must also be calculated on imported or self-produced goods that are used internally. Finally, tax on natural resources must be calculated for packaging materials that are used to package goods that are sold within the reporting period.

## Prerequisites
| Prerequisite                                                   | More information                                                                                                                                                                                                                                                                                                                                                                                            |
|----------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Set up a tax authority.                                        |    |
| Set up the ledger posting group for the Natural resources tax. |  |
| Set up a settlement period for the Natural resources tax.      |  |
| Set up sales tax codes for the Natural resources tax.          | |
| Set up sales tax groups for the Natural resources tax.         |  |
| Set up tax groups for the Natural resources tax.               | Use the **Natural resources tax group** page to set up tax groups that define the correct sales tax codes, based on the intersection of the tax group and sales tax group for the Natural resources tax.                                                                                                                                                                                                    |
| Set up inventory parameters.                                   | On the **Inventory and warehouse management parameters** page, set the **Calculate packing material fees** option to **Yes**. In the **Sales tax group** field, select a sales tax group for the Natural resources tax. By default, this sales tax group is used to find the sales tax code that is used for report calculations if a transaction that is transferred to the report has no sales tax group. |
| Specify natural resources tax information for an item.         | In Product information management, on the **Released products** page, on the **Manage inventory** tab, in the **Natural resource tax group** field, specify a value to calculate the Natural resources tax for an item in a sale or in inventory transactions.                                                                                                                                              |

## Report setup
Before you can generate the **Natural resources tax** report, you must set up the lines for each report layout. Repeat the following steps for every line in each report layout.

1.  Click **Tax** &gt; **Setup** &gt; **Sales tax** &gt; **Natural resources tax report setup**.
2.  Click **New**.
3.  In the **Form number** field, select the form to set up:
    -   **Form 2** – This form shows information about the use of natural resources and any environmental pollution that is generated within the reporting period.
    -   **Form 3** – This form shows information about the tax on natural resources that is calculated for goods that were imported or produced by the company and sold in Latvia for the first time.

4.  Select a sequence number. This number specifies the position of the line in the sequence of lines on the report.
5.  In the **Line type** field, select the type of report line:
    -   **Header** – The line is printed as header lines on report pages.
    -   **Line**
    -   **Total** – The line shows the summarized line values.

6.  If you selected **Line** in step 5, enter the line code for the **Natural resources tax** report line.
7.  In the **Description** field, enter a brief description of the transaction.
8.  In the **Total line code** field, enter the total line code. If you selected **Line** in step 5, the **Warehouse** field shows the warehouse code.
9.  In the **Sales tax code** field, select the sales tax code that was created for the calculation of the Natural resources tax.
10. In the **Packing material code** field, select the packing material code that was created for the Natural resources tax. This field isn't available if you select a sales tax code in the **Sales tax code** field. Only one of these two fields is available at a time.

### Example: Form 2 layout

This example layout has the following information elements:

-   A header that introduces the content of the report
-   Lines that show the descriptions and individual values to report
-   The total amounts for the line values

| Form number | Line type | Sequence number | Line code | Description                                | Total line code | Location Id | Natural resources Tax code | Packing material code |
|-------------|-----------|-----------------|-----------|--------------------------------------------|-----------------|-------------|----------------------------|-----------------------|
| Form 2      | Header    | 1               |           | I. Tax on utilization of natural resources |                 |             |                            |                       |
| Form 2      | Total     | 2               | 1         | Utilization of natural resources (Total)   | 3               |             |                            |                       |
| Form 2      | Line      | 3               | 1.1       | Contoso Manufacturing Co                   | 1               | 785200      | NR-water                   |                       |
| Form 2      | Line      | 4               | 1.2       | Sandpit Nr1                                | 1               | 600900      | NR-sand                    |                       |
| Form 2      | Total     | 5               | 2         | Environment pollution (Total)              | 3               |             |                            |                       |
| Form 2      | Line      | 6               | 2.1       | Contoso Manufacturing Co                   | 2               | 785200      | NR-CO2                     |                       |
| Form 2      | Line      | 7               | 2.1       | Reporting Line                             | 2               |             |                            |                       |
| Form 2      | Total     | 8               | 3         | Total line (line1+ line2)                  |                 |             |                            |                       |
| Form 2      | Line      | 9               | 4         | Reporting Line                             |                 |             |                            |                       |

### Example: Form 3 layout

This example layout has the following elements:

-   A header that introduces the content of the report
-   Lines that show the descriptions and individual values to report
-   The total amounts for the line values

| Form number | Line type | Sequence number | Line code | Description                                                       | Total line code | Location Id | Natural resources Tax code | Packing material code |
|-------------|-----------|-----------------|-----------|-------------------------------------------------------------------|-----------------|-------------|----------------------------|-----------------------|
| Form 3      | Header    | 1               |           | I. Tax on hazardous goods, packing materials and throwaway dishes |                 |             |                            |                       |
| Form 3      | Total     | 2               | 1         | Hazardous goods - Total:                                          | 4               |             |                            |                       |
| Form 3      | Line      | 3               | 1.1       | Aluminum foil                                                     | 1               |             | NR-GAlum                   |                       |
| Form 3      | Line      | 4               | 1.2       |                                                                   | 1               |             |                            |                       |
| Form 3      | Total     | 5               | 2         | Packing materials - Total:                                        | 4               |             |                            |                       |
| Form 3      | Line      | 6               | 2.1       | Packing: glass                                                    | 2               |             |                            | PM-Glass              |
| Form 3      | Line      | 7               | 2.2       | Packing: plastics                                                 | 2               |             |                            | PM-Plastic            |
| Form 3      | Line      | 8               | 2.3       | Packing: metal foil                                               | 2               |             |                            | PM-MetalF             |
| Form 3      | Line      | 9               | 2.4       | Packing: wood, paper, cartons                                     | 2               |             |                            | PM-WPC                |
| Form 3      | Total     | 10              | 3         | Throwaway dishes - Total:                                         | 4               |             |                            |                       |
| Form 3      | Line      | 11              | 3.1       | plastics                                                          | 3               |             |                            | T-Plast               |
| Form 3      | Line      | 12              | 3.2       | Metal foil                                                        | 3               |             |                            | T-MetalF              |
| Form 3      | Line      | 13              | 3.3       | Wood, paper, cartons                                              | 3               |             |                            | T-WPC                 |
| Form 3      | Total     | 14              | 4         | Total line (line1+ line2 + line3)                                 |                 |             |                            |                       |

## Generate the Natural resources tax report
Natural resources taxes are calculated during inventory journal transactions, and when sales or project invoices are created for Latvian customers, if the transactions involve items that are subject to the Natural resources tax. This section describes to get a list of the Natural resources tax transactions that are related to packing materials and print the Natural resources tax statement.

1.  Click **Tax** &gt; **Declarations** &gt; **Sales tax** &gt; **Tax on natural resources**.
2.  Click **Create** &gt; **Create natural resources tax lines on package**.
3.  Enter the quarter and the year for the reporting period.
4.  Click **OK** to transfer the information that will be used to generate the report about the tax on packing materials for the reporting period.
5.  Click **Create** &gt; **Create natural resources tax lines on items**.
6.  Enter the quarter and the year for the reporting period.
7.  Click **OK** to transfer the information that will be used to generate the report about the tax on dangerous materials.
8.  After the Natural resources tax lines are created, you can manually add or modify the information on each line.
    | Field                      | Description                                                                                                                                                                                                                              |
    |----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Voucher                    | The voucher number in the ledger.                                                                                                                                                                                                        |
    | Date                       | The date of the Natural resources tax transaction.                                                                                                                                                                                       |
    | Invoice                    | The identifier of the invoice.                                                                                                                                                                                                           |
    | Transaction type           | The type of the Natural resources tax transaction. The available options are **Tax on dangerous items** and **Tax on packing materials**.                                                                                                |
    | Natural resource tax group | The tax group for natural resources. This field isn't available when **Tax on packing materials** is selected in the **Transaction type** field.                                                                                         |
    | Sales tax group            | The sales tax group that is created for Natural resources taxes that are calculated during a sale or a purchase transaction. This field isn't available when **Tax on packing materials** is selected in the **Transaction type** field. |
    | Sales tax code             | The code that identifies the sales tax.                                                                                                                                                                                                  |
    | Tax Base Amount            | The original amount that the sales tax is calculated from. This field isn't available when **Tax on packing materials** is selected in the **Transaction type** field.                                                                   |
    | Tax amount                 | The calculated sales tax amount.                                                                                                                                                                                                         |
    | BOM line                   | Select this option if the transaction is a BOM (bill of materials) line.                                                                                                                                                                 |
    | Reference                  | The module that generates the transaction.                                                                                                                                                                                               |
    | Number                     | A number such as an order number, project number, or production number.                                                                                                                                                                  |
    | Reference table ID         | The source table for the transaction.                                                                                                                                                                                                    |
    | Reference                  | The source reference field in a different table.                                                                                                                                                                                         |

    **Note:** The fields in the **Packing material** field group are available only when you select **Tax on packing materials** in the **Transaction type** field.
9.  Click **Data validation** to validate the Natural resources tax transaction lines.
10. Correct any errors by manually editing the lines.
11. Click **Print**.
12. Enter the report year.
13. Select a managing director.
14. Select the person who is responsible for the report.
15. Select the tax authority.
16. Click **OK** to print the statement for tax on natural resources.


