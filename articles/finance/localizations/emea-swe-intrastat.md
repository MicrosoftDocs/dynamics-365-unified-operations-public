---
title: Swedish Intrastat
description: This article contains information about Intrastat reporting in Sweden.
author: AdamTrukawka
ms.date: 08/24/2021
ms.topic: article
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: atrukawk
ms.search.validFrom: 
---

# Swedish Intrastat

[!include[banner](../includes/banner.md)]

The **Intrastat** page is used to generate and report information about trade among European Union (EU) countries/regions. The Swedish Intrastat declaration contains information about the trade of goods for reporting.

The following fields are included in the Swedish Intrastat declaration:

   - Partner country ISO code
   - Transaction code
   - Commodity Code
   - Additional unit
   - Weight
   - Invoice amount

## Set up Intrastat

Import the latest version of the following Electronic reporting (ER) configurations:

   - Intrastat model
   - Intrastat report
   - Intrastat (SE)

For more information, see [Download ER configurations from the Global repository of Configuration service](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

## Set up foreign trade parameters

1. In Microsoft Dynamics 365 Finance, go to **Tax** > **Setup** > **Foreign trade parameters**.
2. On the **Intrastat** tab, on the **Electronic reporting** FastTab, in the **File format mapping** field, select **Intrastat (SE)**.
3. In the **Report format mapping** field, select **Intrastat report**.
4. On the **Commodity code hierarchy** FastTab, in the **Category hierarchy** field, select **Intrastat**.
5. In the **Transaction code** field, select the transaction code for property transfers. You use this code for transactions that produce actual or planned transfers of property against compensation (financial or otherwise). You also use it for corrections. Companies in Sweden use one-digit transaction codes.
6. In the **Credit note** field, select the transaction code for the return of goods.
7. On the **Country/region properties** tab, in the **Country/region** field, list all the countries or regions that your company does business with. For each country that is part of the EU, in the **Country/region type** field, select **EU**, so that the country appears on your Intrastat report.

## Set up the product parameters for the Intrastat declaration

1. Go to **Product information management** > **Products** > **Released products**.
2. In the grid, select a product.
3. On the **Foreign trade** FastTab, in the **Intrastat** section, in the **Commodity** field, select the commodity code.
4. On the **Manage inventory** FastTab, in the **Net weight** field, enter the product's weight in kilograms.
5. Go to **Tax** > **Setup** > **Foreign trade** > **Compression of Intrastat**, and select the fields that should be compared when Intrastat information is summarized. For Swedish Intrastat, select the following fields:

    - Commodity
    - Transaction code
    - Direction
    - Country/region
    - Correction
    - Invoice

## Intrastat transfer

On the **Intrastat** page, on the Action Pane, you can select **Transfer** to automatically transfer the information about intracommunity trade from your sales orders, free text invoices, purchase orders, vendor invoices, vendor product receipts, project invoices, and transfer orders. Only documents that have an EU country as the country or region of destination (for dispatches) or consignment (for arrivals) will be transferred.

Alternatively, you can manually enter transactions by selecting **New** on the Action Pane.

### Generate an Intrastat report

1. Go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
2. On the Action Pane, select **Output** > **Report**.
3. In the **Intrastat Report** dialog box, set the following fields.

    | Field            | Description                                                                                                                         |
    |------------------|-------------------------------------------------------------------------------------------------------------------------------------|
    | From date        | Select the start date for the report.                                                                                               |
    | To date          | Select the end date for the report.                                                                                                 |
    | Generate file    | Set this option to **Yes** to generate a .txt file for your Intrastat report.                                                       |
    | File name        | Enter the name of the .txt file.                                                                                                    |
    | Generate report  | Set this option to **Yes** to generate an .xlsx file for your Intrastat report.                                                     |
    | Report file name | Enter the name of the .xlsx file.                                                                                                   |
    | Direction        | Select **Arrivals** for a report about intracommunity arrivals. Select **Dispatches** for a report about intracommunity dispatches. |

4. Select **OK**, and review the generated reports.

## Example

This example shows how to post arrivals and dispatches for Intrastat. It uses the **DEMF** legal entity.

### Preliminary setup

1. Go to **Organization administration** > **Organization** > **Legal entities**, and select the **DEMF** legal entity.
2. On the **Addresses** FastTab, select **Edit**, and then, in the **Country/region** field, select **SWE (Sweden)**.
3. Import the latest version of the following ER configurations:

    - Intrastat model
    - Intrastat report
    - Intrastat (SE)

### Create transaction codes

1. Go to **Tax** > **Setup** > **Foreign trade** > **Transaction codes**.
2. On the Action Pane, select **New**.
3. In the **Transaction** **code** field, enter **1**.
4. In the **Name** field, enter **Normal transactions**
5. On the Action Pane, select **Save**.

### Set up foreign trade parameters

1. Go to **Tax** > **Setup** > **Foreign trade** > **Foreign trade parameters**.
2. On the **Intrastat** tab, on the **General** FastTab, in the **Transaction** **code** field, select **1**.
3. On the **Electronic reporting** FastTab, in the **File format mapping** field, select **Intrastat (SE)**.
4. In the **Report format mapping** field, select **Intrastat Report**.
5. On the **Commodity code hierarchy** FastTab, in the **Category hierarchy** field, make sure that **Intrastat** is selected.
6. On the **Country/region properties** tab, select **New**.
7. In the **Party country/region** field, select **SWE**.
8. In the **Country/region type** field, select **Domestic**.
9. In the **Party country/region** field, select **DEU**, and then, in the **Country/region type** field, select **EU**.

### Set up product information

1. Go to **Product information management** > **Products** > **Released  products**.
2. In the grid, select **D0001**.
3. On the **Foreign trade** FastTab, in the **Intrastat** section, in the **Commodity** field, select **100 200 30**.
4. On the **Manage inventory** FastTab, in the **Weight measurements** section, in the **Net weight** field, enter **5**.
5. On the Action Pane, select **Save**.

### Change the site address

1. Go to **Warehouse management** > **Setup** > **Warehouse** > **Sites**.
2. In the grid, select **1**.
3. On the **Addresses** FastTab, select **Edit**.
4. In the **Edit address** dialog box, in the **Country/region** field, select **SWE**.
5. Select **OK**.

### Create a sales order with an EU customer

1. Go to **Accounts receivable** > **Orders** > **All sales orders**.
2. On the Action Pane, select **New**.
3. In the **Create sales order** dialog box, on the **Customer** FastTab, in the **Customer** section, in the **Customer account** field, select **DE-015**.
4. On the **General** FastTab, in the **Storage dimensions** section, in the **Site** field, select **1**.
5. In the **Warehouse** field, select **11**.
6. Select **OK**.
7. On the **Lines** tab, on the **Sales order lines** FastTab, in the **Item number** field, select **D0001**. Then, in the **Quantity** field, enter **10**.
8. On the **Line details** FastTab, on the **Foreign trade** tab, make sure that the **Transaction code** and **Commodity** fields are automatically set.
9. On the Action Pane, select **Save**.
10. On the Action Pane, on the **Invoice** tab, in the **Generate** section, select **Invoice**.
11. In the **Posting invoice** dialog box, on the **Parameters** FastTab, in the **Parameter** section, in the **Quantity** field, select **All**.
12. Select **OK** to post the invoice.

### Transfer the transaction to the Intrastat journal and review the result

1. Go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
2. On the Action Pane, select **Transfer**.
3. In the **Intrastat (Transfer)** dialog box, in the **Parameters** section, set the **Customer invoice** option to **Yes**.
4. Select **Filter**.
5. In the **Intrastat Filter** dialog box, on the **Range** tab, select the first line, and make sure that the **Field** field is set to **Date**.
6. In the **Criteria** field, select the current date.
7. Select **OK** to close the **Intrastat Filter** dialog box.
8. Select **OK** to close the **Intrastat (Transfer)** dialog box, and review the result. The line represents the sales order that you created earlier.

    ![Intrastat journal lines for sales order](media/swe_intrastat_journal_sales_order.png)

9. Select the transaction line, and then select the **General** tab to view more details.

    ![Intrastat journal line details for sales order](media/swe_intrastat_journal_sales_order_line_details.png)

10. On the Action Pane, select **Output** > **Report**.
11. In the **Intrastat Report** dialog box, on the **Parameters** FastTab, in the **Date** section, select the month of the sales order that you created.
12. In the **Export** **options** section, set the **Generate file** option to **Yes**. Then, in the **File name** field, enter the required name.
13. Set the **Generate report** option to **Yes**. Then, in the **Report file name** field, enter the required name.
14. In the **Direction** field, select **Dispatches**.
15. Select **OK** and review the report in .txt format that is generated. The following table shows the values in the example report.

    | Partner country ISO code | Transaction code | Commodity Code | Additional unit | Weight | Invoice amount |
    |--------------------------|------------------|----------------|-----------------|--------|----------------|
    | IT                       | 1                | 10020030       | 0               | 50     | 3290           |

16. Review the report in Excel format that is generated.

    ![Intrastat report](media/swe_intrastat_report_for_dispatches.png)

### Create a purchase order

1. Go to **Accounts payable** > **Purchase orders** > **All purchase orders**.
2. On the Action Pane, select **New**.
3. In the **Create purchase order** dialog box, in the **Vendor account** field, select **DE-001**.
4. Select **OK**.
5. On the **Header** tab, on the **Foreign** **trade** FastTab, verify that the **Transaction code** field is set to **1**.
6. On the **Lines** tab, on the **Purchase order lines** FastTab, in the **Item number** field, select **D0001**. Then, in the **Quantity** field, enter **6**.
7. On the Action Pane, on the **Purchase** tab, in the **Actions** group, select **Confirm**.
8. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
9. On the Action Pane, select **Default from**. In the **Default quantity for lines** field, select **Ordered quantity**. Then select **OK**.
10. On the **Vendor invoice header** FastTab, in the **Invoice identification** section, in the **Number** field, enter **0001**.
11. On the Action Pane, select **Post** to post the invoice.

### Create an Intrastat declaration for arrivals

1. Go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
2. On the Action Pane, select **Transfer**.
3. In the **Intrastat (Transfer)** dialog box, set the **Vendor invoice** option to **Yes**.
4. Select **OK** to transfer the transactions, and review the Intrastat journal.

    ![Intrastat journal for purchase order](media/swe_intrastat_journal_purchase_order.png)

5. Review the **General** tab for the purchase order.

    ![Intrastat journal line details for purchase order](media/swe_intrastat_journal_purchase_order_line_details.png)

6. On the Action Pane, select **Output** > **Report**.
7. In the **Intrastat Report** dialog box, on the **Parameters** FastTab, in the **Date** section, select the month of the sales order that you created.
8. In the **Export** **options** section, set the **Generate file** option to **Yes**. Then, in the **File name** field, enter the required name.
9. Set the **Generate report** option to **Yes**. Then, in the **Report file name** field, enter the required name.
10. In the **Direction** field, select **Arrivals**.
11. Select **OK**, and review the report in .txt format that is generated. The following table shows the values in the example report.

    | Partner country ISO code | Transaction code | Commodity Code | Additional unit | Weight | Invoice amount |
    |--------------------------|------------------|----------------|-----------------|--------|----------------|
    | IT                       | 1                | 10020030       | 0               | 30     | 1714           |

12. Review the report in Excel format that is generated.

    ![Intrastat arrivals report](media/swe_intrastat_arrivals_report.png)
