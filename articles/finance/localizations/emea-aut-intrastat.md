---
title: Austrian Intrastat
description: This article contains information about the Austrian Intrastat report.
author: AdamTrukawka
ms.date: 09/15/2021
ms.topic: article
audience: 
ms.reviewer: kfend
ms.search.region: Global
ms.author: atrukawk
ms.search.validFrom: 
---

# Austrian Intrastat

[!include[banner](../includes/banner.md)]

You can use the **Intrastat** page to generate and report information about trade among European Union (EU) countries/regions. The Austrian Intrastat declaration contains information about the trade of goods for reporting.

The following fields are included in the Austrian Intrastat declaration:

- Commodity Code
- Transaction code
- Statistical procedure
- Product name
- Partner country ISO code
- Country of origin
- Net mass
- Additional unit
- Mode of transport
- Invoice amount
- Statistical value

## Set up Intrastat

### Import Electronic reporting configurations

To set up Intrastat, import the latest version of the following Electronic reporting (ER) configurations:

- Intrastat model
- Intrastat report
- Intrastat (AT)

For more information, see [Download ER configurations from the Global repository of Configuration service](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

### Set up foreign trade parameters

1. In Microsoft Dynamics 365 Finance, go to **Tax** > **Setup** > **Foreign trade** > **Foreign trade parameters**.
2. On the **Intrastat** tab, on the **Electronic reporting** FastTab, in the **File format mapping** field, select **Intrastat (AT)**
3. In the **Report format mapping** field, select **Intrastat report**.
4. On the **Commodity code hierarchy** FastTab, in the **Category hierarchy** field, select **Intrastat**.
5. In the **Transaction code** field, select the transaction code for property transfers. You use this code for transactions that produce actual or planned transfers of property against compensation (financial or otherwise). You also use it for corrections. Austrian companies use one-digit transaction codes.
6. In the **Credit note** field, select the transaction code for the return of goods.
7. On the **Country/region properties** tab, in the **Country/region** field, list all the countries or regions that your company does business with. For each country that is part of the EU, select **EU** in the **Country/region type** field, so that the country appears on your Intrastat report.

### Set up the product parameters for the Intrastat declaration

1. Go to **Product information management** > **Products** > **Released products**.
2. In the grid, select the product.
3. On the **Foreign trade** FastTab, in the **Intrastat** section, in the **Commodity** field, select a commodity code.
4. In the **Origin** section, in the **Country/region** field, select the product's country of origin.
5. On the **Manage inventory** FastTab, in the **Net weight** field, enter the product's weight in kilograms.
6. Set up the transport method.
    1. Go to **Tax** > **Setup** > **Foreign trade** > **Transport method**.
    2. On the Action Pane, select **New**.
    3. In the **Transport** field, enter a unique code. Austrian companies use one-digit transport codes.
7. Assign a transport mode to a mode of delivery.
    1. Go to **Procurement and sourcing** > **Setup** > **Distribution** > **Modes of delivery**.
    2. In the grid, select a mode.
    3. On the **Foreign trade** FastTab, in the **Transport** field, select the corresponding transport.
8. Go to **Tax** > **Setup** > **Foreign trade** > **Compression of Intrastat**, and select the fields that should be compared when Intrastat information is summarized. For Austrian Intrastat, select the following fields:

     - Commodity
     - Transaction code
     - Country/region of origin
     - Statistics procedure
     - Direction
     - Country/region
     - Transport
     - Correction        
     - Invoice

## Intrastat transfer

On the **Intrastat** page, on the Action Pane, you can select **Transfer** to automatically transfer the information about intracommunity trade from your sales orders, free text invoices, purchase orders, vendor invoices, vendor product receipts, project invoices, and transfer orders. Only documents that have an EU country as the country or region of destination (for dispatches) or consignment (for arrivals) will be transferred.

Alternatively, you can manually enter transactions by selecting **New** on the Action Pane.

### Generate an Intrastat report

1. Go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
2. On the Action Pane, select **Output** > **Report**.
3. In the **Intrastat Report** dialog box, enter the start and end dates for the report.
4. Set the **Generate file** option to **Yes** to generate a .txt file, and then enter the name of the .txt file for the Intrastat report.
5. Set the **Generate report** option to **Yes** to generate an .xlsx file, and then enter a name for the file.
6. Select **Arrivals** if the report is about intracommunity arrivals or **Dispatches** if the report is about intracommunity dispatches.
7. Select **OK**, and review the generated reports.

## Example

The following example shows how to set up Austrian Intrastat and create the Intrastat report. It uses the **DEMF** legal entity.

1. Go to **Organization administration** > **Organization** > **Legal entities**, and select the **DEMF** legal entity.
2. On the **Addresses** FastTab, select **Edit**. Then, in the **Country/region** field, select **AUT** (Austria).
3. Import the latest version of the following ER configurations:

    - Intrastat model
    - Intrastat report
    - Intrastat (AT)

### Create transaction codes

1. Go to **Tax** > **Setup** > **Foreign trade** > **Transaction codes**.
2. On the Action Pane, select **New**.
3. In the **Transaction** **code** field, enter **1**.
4. In the **Name** field, enter **Actual/intended transfer of ownership against compensation**.
5. On the Action Pane, select **Save**.

### Set up foreign trade parameters

1. Go to **Tax** > **Setup** > **Foreign trade** > **Foreign trade parameters**.
2. On the **Intrastat** tab, on the **General** FastTab, in the **Transaction** **code** field, select **1**.
3. On the **Electronic reporting** FastTab, in the **File format mapping** field, select **Intrastat (AT)**.
4. In the **Report format mapping** field, select **Intrastat Report**.
5. On the **Commodity code hierarchy** FastTab, in the **Category hierarchy** field, make sure that **Intrastat** is selected.
6. On the **Country/region properties** tab, in the **Party country/region** field, select **AUT**.
7. In the **Country/region type** field, select **Domestic**.
8. Select **DEU** (Germany), and then, in the **Country/region type** field, select **EU**.
9. Make sure that the **Country/region type** field for **ITA** (Italy) is set to **EU**.

### Set up product information

1. Go to **Product information management** > **Products** > **Released** **products**.
2. In the grid, select **D0001**.
3. On the **Foreign trade** FastTab, in the **Intrastat** section, in the **Commodity** field, select **100 200 30**.
4. In the **Origin** section, in the **Country/region** field, select **AUT**.
5. On the **Manage inventory** FastTab, in the **Weight measurements** section, in the **Net weight** field, enter **5**.
6. On the Action Pane, select **Save**.
7. In the grid, select **D0003**.
8. On the **Foreign trade** FastTab, in the **Intrastat** section, in the **Commodity** field, select **100 200 30**.
9. In the **Origin** section, in the **Country/region** field, select **DEU**.
10. On the **Manage inventory** FastTab, in the **Weight measurements** section, in the **Net weight** field, enter **8**.
11. On the Action Pane, select **Save**.

### Change the site address

1. Go to **Warehouse management** > **Setup** > **Warehouse** > **Sites**.
2. In the grid, select **1**.
3. On the **Addresses** FastTab, select **Edit**.
4. In the **Edit address** dialog box, in the **Country/region** field, select **AUT**.
5. Select **OK** to close the **Edit address** dialog box.

### Set up a transport method

1. Go to **Tax** > **Setup** > **Foreign trade** > **Transport method**.
2. On the Action Pane, select **New**.
3. In the **Transport** field, enter **3**.
4. In the **Description** field, enter **Road transport**.

### Assign a transport mode to a mode of delivery

1. Go to **Procurement and sourcing** > **Setup** > **Distribution** > **Modes of delivery**.
2. In the grid, select **50**.
3. On the **Foreign trade** FastTab, in the **Transport** field, select **3**.

### Create a sales order with an EU customer

1. Go to **Accounts receivable** > **Orders** > **All sales orders**.
2. On the Action Pane, select **New**.
3. In the **Create sales order** dialog box, on the **Customer** FastTab, in the **Customer** section, in the **Customer account** field, select **DE-015**.
4. On the **General** FastTab, in the **Storage dimensions** section, in the **Site** field, select **1**.
5. In the **Warehouse** field, select **11**.
6. On the **Address** tab, make sure that the **Address** field is set to **Via Aurelia 1, Rome, 11111, ITA**, because the vendor is from Italy.
7. Select **OK**.
8. On the **Header** tab, on the **Delivery** FastTab, in the **Mode of delivery** field, make sure that **50** is selected.
9. On the **Lines** tab, on the **Sales order lines** FastTab, in the **Item number** field, select **D0001**. Then, in the **Quantity** field, enter **8**.
10. On the **Line details** FastTab, on the **Foreign trade** tab, make sure that the **Transaction code**, **Transport**, **Commodity** and **Country/region of origin** fields are automatically set.
11. On the **Foreign trade** tab, in the **Statistics procedure** field, select **31710**.
12. On the Action Pane, select **Save**.
13. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
14. In the **Posting invoice** dialog box, on the **Parameters** FastTab, in the **Parameter** section, in the **Quantity** field, select **All**.
15. Select **OK** to post the invoice.

### Transfer the transaction to the Intrastat journal and review the result

1. Go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
2. On the Action Pane, select **Transfer**.
3. In the **Intrastat (Transfer)** dialog box, in the **Parameters** section, set the **Customer invoice** option to **Yes**.
4. Select **Filter**.
5. In the **Intrastat Filter** dialog box, on the **Range** tab, select the first line, and make sure that the **Field** field is set to **Date**.
6. In the **Criteria** field, select the current date.
7. Select **OK** to close the **Intrastat Filter** dialog box.
8. Select **OK** to close the **Intrastat (Transfer)** dialog box, and review the result. The line represents the sales order that you created earlier.

    ![Line that represents the sales order on the Intrastat page](media/intrastat_at_1.png)

9.  Select the transaction line, and then select the **General** tab to view more details.

    ![Sales order details on the General tab of the Intrastat page](media/intrastat_at_2.png)

10. On the Action Pane, select **Output** > **Report**.
11. In the **Intrastat Report** dialog box, on the **Parameters** FastTab, in the **Date** section, select the month of the sales order that you created.
12. In the **Export** **options** section, set the **Generate file** option to **Yes**. Then, in the **File name** field, enter the required name.
13. Set the **Generate report** option to **Yes**. Then, in the **Report file name** field, enter the required name.
14. In the **Direction** field select **Dispatches**.
15. Select **OK**, and review the report in text format that is generated. The following table shows the values in the example report.

    | Commodity code | Transaction code | Statistical procedure | Product name    | Partner country ISO code | Country of origin | Net mass | Additional unit | Mode of transport | Invoice amount | Statistical value |
    |----------------|------------------|-----------------------|-----------------|--------------------------|-------------------|----------|-----------------|-------------------|----------------|-------------------|
    | 10020030       | 1                | 31710                 | MidRangeSpeaker | IT                       | AT                | 50       |                 | 3                 | 2632           | 2632              |

16. Review the generated report file.

    ![Intrastat report on dispatches](media/intrastat_at_3.png)

### Create a purchase order

1. Go to **Accounts payable** > **Purchase orders** > **All purchase orders**.
2. On the Action Pane, select **New**.
3. In the **Create purchase order** dialog box, in the **Vendor account** field, select **DE-001**. Then select **OK**.
4. On the **Header** tab, on the **Foreign** **trade** FastTab, make sure that the **Transaction code** field is set to **1**.
5. In the **Transport** field, select **3**.
6. On the **Lines** tab, on the **Purchase order lines** FastTab, in the **Item number** field, select **D0003**.
7. In the **Quantity** field, enter **6**.
8. On the **Line details** FastTab, on the **Foreign trade** tab, make sure that the **Transaction code**, **Transport**, **Commodity**, and **Country/region of origin** fields are automatically set.
9. On the **Foreign trade** tab, in the **Statistics procedure** field, select **10000**.
10. On the Action Pane, on the **Purchase** tab, in the **Actions** group, select **Confirm**.
11. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
12. On the Action Pane, select **Default from**, and then, in the **Default quantity for lines** field, select **Ordered quantity**. Then select **OK**.
13. On the **Vendor Invoice header** FastTab, in the **Invoice identification** section, in the **Number** field, enter **0001**.
14. On the Action Pane, select **Post** to post the invoice.

### Create an Intrastat declaration for arrivals

1. Go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
2. On the Action Pane, select **Transfer**.
3. In the **Intrastat (Transfer)** dialog box ,set the **Vendor invoice** option to **Yes**.
4. Select **OK** to transfer the transactions, and review the Intrastat journal.

    ![Line that represents the purchase order on the Intrastat page](media/intrastat_at_4.png)

5. Review the **General** tab for the purchase order.

    ![Purchase order details on the General tab of the Intrastat page](media/intrastat_at_5.png)

6. On the Action Pane, select **Output** &gt; **Report**.
7. In the **Intrastat Report** dialog box, on the **Parameters** FastTab, in the **Date** section, select the month of the purchase order that you created.
8. In the **Export** **options** section, set the **Generate file** option to **Yes**. Then, in the **File name** field, enter the required name.
9. Set the **Generate report** option to **Yes**. Then, in the **Report file name** field, enter the required name.
10. In the **Direction** field, select **Arrivals**.
11. Select **OK**, and review the report in text format that is generated. The following table shows the values in the example report.

    | Commodity code | Transaction code | Statistical procedure | Product name    | Partner country ISO code | Country of origin | Net mass | Additional unit | Mode of transport | Invoice amount | Statistical value |
    |----------------|------------------|-----------------------|-----------------|--------------------------|-------------------|----------|-----------------|-------------------|----------------|-------------------|
    | 10020030       | 1                | 10000                 | StandardSpeaker | DE                       | DE                | 48       |                 | 3                 | 965            | 965               |

12. Review the generated Excel report.

    ![Intrastat report on arrivals](media/intrastat_at_6.png)
