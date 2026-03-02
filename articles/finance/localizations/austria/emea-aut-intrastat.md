---
title: Austrian Intrastat
description: Learn about the Austrian Intrastat report, including an outline on setting up Intrastat, intrastat transfer, and provides examples.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/02/2026
ms.reviewer: johnmichalak
ms.search.region: Global

---

# Austrian Intrastat

[!include[banner](../../includes/banner.md)]

Use the **Intrastat** page to generate and report information about trade among European Union (EU) countries and regions. The Austrian Intrastat declaration contains information about the trade of goods for reporting.

The Austrian Intrastat declaration includes the following fields:

- Commodity Code
- Transaction code
- Statistical procedure
- Product name
- Partner country/region ISO code
- Country/region of origin
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

For more information, see [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

### Set up foreign trade parameters

1. In Microsoft Dynamics 365 Finance, go to **Tax** > **Setup** > **Foreign trade** > **Foreign trade parameters**.
1. On the **Intrastat** tab, on the **Electronic reporting** FastTab, in the **File format mapping** field, select **Intrastat (AT)**.
1. In the **Report format mapping** field, select **Intrastat report**.
1. On the **Commodity code hierarchy** FastTab, in the **Category hierarchy** field, select **Intrastat**.
1. In the **Transaction code** field, select the transaction code for property transfers. Use this code for transactions that produce actual or planned transfers of property against compensation (financial or otherwise). Use it also for corrections. Austrian companies use one-digit transaction codes.
1. In the **Credit note** field, select the transaction code for the return of goods.
1. On the **Country/region properties** tab, in the **Country/region** field, list all the countries or regions that your company does business with. For each country/region that is part of the EU, select **EU** in the **Country/region type** field, so that the country/region appears on your Intrastat report.

### Set up the product parameters for the Intrastat declaration

1. Go to **Product information management** > **Products** > **Released products**.
1. Select the product in the grid.
1. On the **Foreign trade** FastTab, in the **Intrastat** section, select a commodity code in the **Commodity** field.
1. In the **Origin** section, select the product's country/region of origin in the **Country/region** field.
1. On the **Manage inventory** FastTab, enter the product's weight in kilograms in the **Net weight** field.
1. Set up the transport method.
    1. Go to **Tax** > **Setup** > **Foreign trade** > **Transport method**.
    1. Select **New** on the Action Pane.
    1. Enter a unique code in the **Transport** field. Austrian companies use one-digit transport codes.
1. Assign a transport mode to a mode of delivery.
    1. Go to **Procurement and sourcing** > **Setup** > **Distribution** > **Modes of delivery**.
    1. Select a mode in the grid.
    1. Select the corresponding transport in the **Transport** field on the **Foreign trade** FastTab.
1. Go to **Tax** > **Setup** > **Foreign trade** > **Compression of Intrastat**, and select the fields that should be compared when Intrastat information is summarized. For Austrian Intrastat, select the following fields:

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

On the **Intrastat** page, on the Action Pane, select **Transfer** to automatically transfer the information about intracommunity trade from your sales orders, free text invoices, purchase orders, vendor invoices, vendor product receipts, project invoices, and transfer orders. Only documents that have an EU country/region as the country/region of destination (for dispatches) or consignment (for arrivals) are transferred.

Alternatively, you can manually enter transactions by selecting **New** on the Action Pane.

### Generate an Intrastat report

1. Go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
1. On the action pane, select **Output** > **Report**.
1. In the **Intrastat Report** dialog box, enter the start and end dates for the report.
1. Set the **Generate file** option to **Yes** to generate a .txt file, and then enter the name of the .txt file for the Intrastat report.
1. Set the **Generate report** option to **Yes** to generate an .xlsx file, and then enter a name for the file.
1. Select **Arrivals** if the report is about intracommunity arrivals or **Dispatches** if the report is about intracommunity dispatches.
1. Select **OK**, and review the generated reports.

## Example

The following example shows how to set up Austrian Intrastat and create the Intrastat report. It uses the **DEMF** legal entity.

1. Go to **Organization administration** > **Organization** > **Legal entities**, and select the **DEMF** legal entity.
1. On the **Addresses** FastTab, select **Edit**. Then, in the **Country/region** field, select **AUT** (Austria).
1. Import the latest version of the following ER configurations:

    - Intrastat model
    - Intrastat report
    - Intrastat (AT)

### Create transaction codes

1. Go to **Tax** > **Setup** > **Foreign trade** > **Transaction codes**.
1. Select **New** on the Action Pane.
1. In the **Transaction** **code** field, enter **1**.
1. In the **Name** field, enter **Actual/intended transfer of ownership against compensation**.
1. On the Action Pane, select **Save**.

### Set up foreign trade parameters

1. Go to **Tax** > **Setup** > **Foreign trade** > **Foreign trade parameters**.
1. On the **Intrastat** tab, on the **General** FastTab, in the **Transaction** **code** field, select **1**.
1. On the **Electronic reporting** FastTab, in the **File format mapping** field, select **Intrastat (AT)**.
1. In the **Report format mapping** field, select **Intrastat Report**.
1. On the **Commodity code hierarchy** FastTab, in the **Category hierarchy** field, make sure that **Intrastat** is selected.
1. On the **Country/region properties** tab, in the **Party country/region** field, select **AUT**.
1. In the **Country/region type** field, select **Domestic**.
1. Select **DEU** (Germany), and then, in the **Country/region type** field, select **EU**.
1. Make sure that the **Country/region type** field for **ITA** (Italy) is set to **EU**.

### Set up product information

1. Go to **Product information management** > **Products** > **Released** **products**.
1. In the list, select **D0001**.
1. On the **Foreign trade** FastTab, in the **Intrastat** section, in the **Commodity** field, select **100 200 30**.
1. In the **Origin** section, in the **Country/region** field, select **AUT**.
1. On the **Manage inventory** FastTab, in the **Weight measurements** section, in the **Net weight** field, enter **5**.
1. On the Action Pane, select **Save**.
1. In the list, select **D0003**.
1. On the **Foreign trade** FastTab, in the **Intrastat** section, in the **Commodity** field, select **100 200 30**.
1. In the **Origin** section, in the **Country/region** field, select **DEU**.
1. On the **Manage inventory** FastTab, in the **Weight measurements** section, in the **Net weight** field, enter **8**.
1. On the Action Pane, select **Save**.

### Change the site address

1. Go to **Warehouse management** > **Setup** > **Warehouse** > **Sites**.
1. In the list, select **1**.
1. On the **Addresses** FastTab, select **Edit**.
1. In the **Edit address** dialog box, in the **Country/region** field, select **AUT**.
1. Select **OK** to close the **Edit address** dialog box.

### Set up a transport method

1. Go to **Tax** > **Setup** > **Foreign trade** > **Transport method**.
1. Select **New** on the Action Pane.
1. In the **Transport** field, enter **3**.
1. In the **Description** field, enter **Road transport**.

### Assign a transport mode to a mode of delivery

1. Go to **Procurement and sourcing** > **Setup** > **Distribution** > **Modes of delivery**.
1. In the grid, select **50**.
1. On the **Foreign trade** FastTab, in the **Transport** field, select **3**.

### Create a sales order with an EU customer

1. Go to **Accounts receivable** > **Orders** > **All sales orders**.
1. Select **New** on the Action Pane.
1. In the **Create sales order** dialog box, on the **Customer** FastTab, in the **Customer** section, in the **Customer account** field, select **DE-015**.
1. On the **General** FastTab, in the **Storage dimensions** section, in the **Site** field, select **1**.
1. In the **Warehouse** field, select **11**.
1. On the **Address** tab, make sure that the **Address** field is set to **Via Aurelia 1, Rome, 11111, ITA**, because the vendor is from Italy.
1. Select **OK**.
1. On the **Header** tab, on the **Delivery** FastTab, in the **Mode of delivery** field, make sure that **50** is selected.
1. On the **Lines** tab, on the **Sales order lines** FastTab, in the **Item number** field, select **D0001**. Then, in the **Quantity** field, enter **8**.
1. On the **Line details** FastTab, on the **Foreign trade** tab, make sure that the **Transaction code**, **Transport**, **Commodity**, and **Country/region of origin** fields are automatically set.
1. On the **Foreign trade** tab, in the **Statistics procedure** field, select **31710**.
1. On the Action Pane, select **Save**.
1. On the action pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
1. In the **Posting invoice** dialog box, on the **Parameters** FastTab, in the **Parameter** section, in the **Quantity** field, select **All**.
1. Select **OK** to post the invoice.

### Transfer the transaction to the Intrastat journal and review the result

1. Go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
1. On the action pane, select **Transfer**.
1. In the **Intrastat (Transfer)** dialog box, in the **Parameters** section, set the **Customer invoice** option to **Yes**.
1. Select **Filter**.
1. In the **Intrastat Filter** dialog box, on the **Range** tab, select the first line, and make sure that the **Field** field is set to **Date**.
1. In the **Criteria** field, select the current date.
1. Select **OK** to close the **Intrastat Filter** dialog box.
1. Select **OK** to close the **Intrastat (Transfer)** dialog box, and review the result. The line represents the sales order that you created earlier.

    :::image type="content" source="../media/intrastat_at_1.png" alt-text="Screenshot of the line that represents the sales order on the Intrastat page.":::

1. Select the transaction line, and then select the **General** tab to view more details.

    :::image type="content" source="../media/intrastat_at_2.png" alt-text="Screenshot of sales order details on the General tab of the Intrastat page.":::

1. On the action pane, select **Output** > **Report**.
1. In the **Intrastat Report** dialog box, on the **Parameters** FastTab, in the **Date** section, select the month of the sales order that you created.
1. In the **Export** **options** section, set the **Generate file** option to **Yes**. Then, in the **File name** field, enter the required name.
1. Set the **Generate report** option to **Yes**. Then, in the **Report file name** field, enter the required name.
1. In the **Direction** field select **Dispatches**.
1. Select **OK**, and review the report in text format that is generated. The following table shows the values in the example report.

    | Commodity code | Transaction code | Statistical procedure | Product name    | Partner country/region ISO code | Country/Region of origin | Net mass | Additional unit | Mode of transport | Invoice amount | Statistical value |
    |----------------|------------------|-----------------------|-----------------|--------------------------|-------------------|----------|-----------------|-------------------|----------------|-------------------|
    | 10020030       | 1                | 31710                 | MidRangeSpeaker | IT                       | AT                | 50       |                 | 3                 | 2632           | 2632              |

1. Review the generated report file.

    :::image type="content" source="../media/intrastat_at_3.png" alt-text="Screenshot of the Intrastat report on dispatches.":::

### Create a purchase order

1. Go to **Accounts payable** > **Purchase orders** > **All purchase orders**.
1. Select **New** on the Action Pane.
1. In the **Create purchase order** dialog box, in the **Vendor account** field, select **DE-001**. Then select **OK**.
1. On the **Header** tab, on the **Foreign** **trade** FastTab, make sure that the **Transaction code** field is set to **1**.
1. In the **Transport** field, select **3**.
1. On the **Lines** tab, on the **Purchase order lines** FastTab, in the **Item number** field, select **D0003**.
1. In the **Quantity** field, enter **6**.
1. On the **Line details** FastTab, on the **Foreign trade** tab, make sure that the **Transaction code**, **Transport**, **Commodity**, and **Country/region of origin** fields are automatically set.
1. On the **Foreign trade** tab, in the **Statistics procedure** field, select **10000**.
1. On the action pane, on the **Purchase** tab, in the **Actions** group, select **Confirm**.
1. On the action pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
1. On the action pane, select **Default from**, and then, in the **Default quantity for lines** field, select **Ordered quantity**. Then select **OK**.
1. On the **Vendor Invoice header** FastTab, in the **Invoice identification** section, in the **Number** field, enter **0001**.
1. On the action pane, select **Post** to post the invoice.

### Create an Intrastat declaration for arrivals

1. Go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
1. On the action pane, select **Transfer**.
1. In the **Intrastat (Transfer)** dialog box ,set the **Vendor invoice** option to **Yes**.
1. Select **OK** to transfer the transactions, and review the Intrastat journal.

    :::image type="content" source="../media/intrastat_at_4.png" alt-text="Screenshot of the line that represents the purchase order on the Intrastat page.":::

1. Review the **General** tab for the purchase order.

    :::image type="content" source="../media/intrastat_at_5.png" alt-text="Screenshot of purchase order details on the General tab of the Intrastat page.":::

1. On the Action Pane, select **Output** &gt; **Report**.
1. In the **Intrastat Report** dialog box, on the **Parameters** FastTab, in the **Date** section, select the month of the purchase order that you created.
1. In the **Export** **options** section, set the **Generate file** option to **Yes**. Then, in the **File name** field, enter the required name.
1. Set the **Generate report** option to **Yes**. Then, in the **Report file name** field, enter the required name.
1. In the **Direction** field, select **Arrivals**.
1. Select **OK**, and review the report in text format that is generated. The following table shows the values in the example report.

    | Commodity code | Transaction code | Statistical procedure | Product name    | Partner countryregion ISO code | Country/Region of origin | Net mass | Additional unit | Mode of transport | Invoice amount | Statistical value |
    |----------------|------------------|-----------------------|-----------------|--------------------------|-------------------|----------|-----------------|-------------------|----------------|-------------------|
    | 10020030       | 1                | 10000                 | StandardSpeaker | DE                       | DE                | 48       |                 | 3                 | 965            | 965               |

1. Review the generated Excel report.

    :::image type="content" source="../media/intrastat_at_6.png" alt-text="Screenshot of the Intrastat report on arrivals.":::

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
