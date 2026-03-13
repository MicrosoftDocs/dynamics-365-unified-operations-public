---
title: German Intrastat
description: Learn about Intrastat declaration in Germany, including a table that shows the fields that are included in the German Intrastat declaration.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/13/2026
ms.reviewer: johnmichalak
ms.search.region: Global
---

# German Intrastat

[!include [banner](../../includes/banner.md)]

The **Intrastat** page is used to generate and report information about trade among European Union (EU) countries/regions. The German Intrastat declaration contains information about the trade of goods for reporting. The report is formatted according to the guidelines of the German authorities.

The following table shows the fields that are included in the German Intrastat declaration.

| Fields | Dispatches | Arrivals |
|-------------------------|-------------------------|-------------------------|
| Reference period | X | X |
| Direction code | X | X |
| Currency of the Intrastat declaration</br>**Note:** This currency is the <em>accounting currency</em>. | X | X |
| Commodity code | X | X |
| Commodity name | X | X |
| Supplementary unit code | X | X |
| Member State of consignment/destination | X | X |
| Net mass | X | X |
| Quantity in supplementary units | X | X |
| Country of origin |  | X |
| Invoice amount | X |  |
| Statistical value | X | X |
| Nature of transactions | X | X |
| Mode of transport | X | X |
| Region code</br>**Note:**</br><ul></br><li>If the country or region of origin is Germany, and the invoice is for dispatches, an Intrastat code for the state of origin is shown.</li></br><li>If the country or region of origin isn't Germany, and the invoice is for dispatches, the code **99** is shown.</li></br><li>If the invoice is for arrivals, an Intrastat code for the state is shown.</li></br></ul> | X | X |
| Port/Airport/Inland port code | X | X |
| Delivery terms | X | X |

## Set up Intrastat

1. Set up the company's codes.

    1. Go to **Organization administration** > **Organizations** > **Legal entities**.
    1. On the **Foreign trade and Logistics** FastTab, in the **Identification** section, in the **DVR** field, enter the Interchange agreement ID. This ID appears on the report.
    1. In the **VAT exempt number export** field, enter your company's value-added tax (VAT) number for export.
    1. In the **VAT exempt number import** field, enter your company's VAT number for import.
    1. In the **Intrastat code** field, enter the Intrastat code that is assigned to the legal entity.
    1. On the **Tax registration** FastTab, in the **Tax registration number** field, enter your company's tax registration number.

    > [!NOTE]
    > If you generate an Intrastat report for affiliates, in the **Tax registration number** field, enter the tax registration number of your parent company.

1. In [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/Logon/Index), in the Shared asset library, download the latest versions of the following Electronic reporting (ER) configurations for the Intrastat declaration.

    - Intrastat model
    - Intrastat report
    - INSTAT XML
    - INSTAT XML (DE)

1. Set up foreign trade parameters:

    1. In Dynamics 365 Finance, go to **Tax** > **Setup** > **Foreign trade parameters**.
    1. On the **Intrastat** tab, on the **Electronic reporting** FastTab, in the **File format mapping** field, select **Intrastat XML (DE)**.
    1. In the **Report format mapping** field, select **Intrastat report**.
    1. On the **Commodity code hierarchy** FastTab, in the **Category hierarchy** field, select **Intrastat**.
    1. In the **Transaction code** field, select the transaction code for property transfers. Use this code for transactions that produce actual or planned transfers of property against compensation (financial or other). Also use it for corrections.
    1. In the **Credit note** field, select the transaction code for the return of goods.
    1. In the **Worker** field, select the contact person for Intrastat report. Alternatively, on the **Contact** tab enter or select values in the **Name**, **Telephone**, **Fax**, **Email**, and **Internet address** fields. These fields are included in the report.
    1. In the **Authority** field, select the Intrastat authority.
    1. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax authorities**, and enter the following information for the Intrastat authority that you selected in the previous step:

       - Authority identification
       - Address
       - Contact information

    1. On the **Country/region properties** tab, in the **Country/region** field, list all the countries or regions that your company does business with. For each country or region, in the **Country/region type** field, select **EU**, so that the country or region appears on your Intrastat report.

1. Set up region codes.

    1. Go to **Organization administration** > **Global address book** > **Addresses** > **Address setup**.
    1. On the **State/province** tab, in the **Country/region** field, select **DEU**, and then select **Apply filter**.
    1. In the grid, select the state. Then, in the **Intrastat code** field, enter the unique Intrastat code.

1. Set up the address of origin for a product.

    1. Go to **Product information management** > **Products** > **Released products**.
    1. In the grid, select the product.
    1. On the **Foreign trade** FastTab, in the **Intrastat** section, in the **Country/region of origin** field, select **DEU**.

1. Go to **Tax** > **Setup** > **Foreign trade** > **Compression of Intrastat**, and select the fields that should be compared when Intrastat information is summarized. For German Intrastat, select the following fields:

    - Commodity
    - Country/region
    - Correction
    - Direction
    - Delivery terms
    - Invoice
    - Country/region of origin
    - Port
    - Country/region of sender
    - State of sender
    - Statistical procedure
    - Transaction code
    - Transport
    - Tax exempt number

### Intrastat transfer

On the **Intrastat** page, on the action pane, select **Transfer** to automatically transfer the information about intracommunity trade from your sales orders, free text invoices, purchase orders, vendor invoices, vendor product receipts, project invoices, and transfer orders. Only documents that have an EU country/region as the country/region of destination (for dispatches) or consignment (for arrivals) are transferred.

Alternatively, you can manually enter transactions by selecting **New** on the action pane.

### Generate an Intrastat report

1. Go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
1. On the action pane, select **Output** > **Report**.
1. In the **Intrastat Report** dialog box, set the following fields.

    | Field | Description |
    |-------------------------|-------------------------|
    | From date | Select the start date for the report. |
    | To date | Select the end date for the report. |
    | Generate file | Set this option to **Yes** to generate an .xml file. |
    | File name | Leave this field blank. The file name is automatically generated and consists of the value of the **&lt;envelopeId&gt;** XML tag plus the file name extension **.xml**.</br>The **&lt;envelopeId&gt;** value is a concatenation of the following elements, in this order:</br><ol type="1"></br><li>The value of the **&lt;interchangeAgreementId&gt;** tag</li></br><li>A hyphen (-)</li></br><li>The value of the **&lt;referencePeriod in YYYYMM&gt;** tag</li></br><li>A hyphen (-)</li></br><li>The value of the **&lt;Envelope/DateTime/date in YYYYMMDD&gt;** tag</li></br><li>A hyphen (-)</li></br><li>The value of the **&lt;Envelope/DateTime/time in hhmm&gt;** tag</li></br></ol> |
    | Direction | <ul></br><li>Select **Arrivals** to report on intracommunity arrivals.</li></br><li>Select **Dispatches** to report on intracommunity dispatches.</li></br><li>Select **Both** to report on both arrivals and dispatches.</li></br></ul> |
    | Tax registration number | Enter the registration number to use to generate the identification code of the sender, if the number differs from the tax registration number of the legal entity. |


## Example

This example shows how to post arrivals and dispatches for Intrastat. It uses the **DEMF** legal entity.

1. In [LCS](https://lcs.dynamics.com/Logon/Index), in the Shared asset library, download the latest versions of the following ER configurations for the Intrastat declaration format:

    - Intrastat model
    - Intrastat report
    - Intrastat XML
    - Intrastat XML (DE)

1. Create transaction codes.

    1. Go to **Tax** > **Setup** > **Foreign trade** > **Transaction codes**.
    1. On the Action Pane, select **New**.
        1. In the **Transaction code** field, enter "21."
        1. In the **Name** field, enter "Return of goods."
    1. On the Action Pane, select **Save**.

1. Set up the authority identification number.

    1. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax authorities**.
    1. In the list, select **TA**.
        1. In the **Authority identification** field, enter "123."

1. Set up region codes.

    1. Go to **Organization administration** > **Global address book** > **Addresses** > **Address setup**.
    1. On the **State/province** tab, in the **Country/region** field, select **DEU**, and then select **Apply filter**.
        1. In the grid, select **BE**, and then, in the **Intrastat code** field, enter "11."
    1. On the Action Pane, select **Save**.

1. Set up foreign trade parameters.

    1. Go to **Tax** > **Setup** > **Foreign trade** > **Foreign trade parameters**.
            1. On the **Intrastat** tab, on the **General** FastTab, in the **Transaction code** field, select **11**.
            1. In the **Credit note** field, select **21**.
    1. In the **Authority** field, select **TA**.
    1. On the **Electronic reporting** FastTab, in the **File format mapping** field, select **INSTAT XML (DE)**.
    1. In the **Report format mapping** field, select **Intrastat Report**.
    1. On the **Commodity code hierarchy** FastTab, in the **Category hierarchy** field, make sure that **Intrastat** is selected.
    1. On the **Country/region properties** tab, select **New**.
    1. In the **Party country/region** field, select **FRA**.
    1. In the **Country/region type** field, select **EU**.

1. Assign a commodity code to a product, and set the product's origin. The **Commodity code**, **Country/region of origin**, and **State of origin** fields automatically set on sales orders and purchase orders when you select the product.

    1. Go to **Product information management** > **Products** > **Released products**.
    1. In the grid, select **D0001**.
        1. On the **Foreign trade** FastTab, in the **Intrastat** section, in the **Commodity** field, select **920 20 34**.
    1. In the **Origin** section, in the **Country/region** field, select **DEU**.
        1. On the **Manage inventory** FastTab, in the **Weight measurements** section, in the **Net weight** field, enter "12."
    1. On the Action Pane, select **Save**.

1. Assign transport to a mode of delivery. The transport code automatically sets on orders when you select the mode of delivery.

    1. Go to **Procurement and sourcing** > **Setup** > **Distribution** > **Modes of delivery**.
            1. In the list, select **10**.
        1. On the **Foreign trade** FastTab, in the **Transport** field, select **01**.

1. Create a sales order with an EU customer.

    1. Go to **Accounts receivable** > **Orders** > **All sales orders**.
    1. On the Action Pane, select **New**.
    1. In the **Create sales order** dialog box, on the **Customer** FastTab, in the **Customer** section, in the **Customer account** field, select **DE-012**.
    1. On the **General** FastTab, in the **Storage dimensions** section, in the **Site** field, select **1**.
    1. In the **Warehouse** field, select **11**.
    1. Select **OK**.
    1. On the **Header** tab, on the **Foreign trade** FastTab, in the **Port** field, select **53**.
    1. In the **Statistical procedure** field, select **31710**.
    1. On the **Lines** tab, on the **Sales order** **lines** FastTab, in the **Item number** field, select **D0001**. Then, in the **Quantity** field, enter **10**.
    1. On the **Line details** FastTab, on the **Foreign trade** tab, make sure that the **Transaction code**, **Transport**, **Commodity**, and **Country/region of origin** fields are automatically set.
    1. On the Action Pane, select **Save**.
    1. On the Action Pane, on the **Invoice** tab, in the **Generate** section, select **Invoice**.
    1. In the **Posting invoice** dialog box, on the **Parameters** FastTab, in the **Parameter** section, in the **Quantity** field, select **All**.
    1. Select **OK** to post the invoice.

1. Transfer the transaction to the Intrastat journal, and review the result.

    1. Go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
    1. On the Action Pane, select **Transfer**.
    1. In the **Intrastat (Transfer)** dialog box, in the **Parameters** section, set the **Customer invoice** option to **Yes**.
    1. Select **Filter**.
    1. In the **Intrastat Filter** dialog box, on the **Range** tab, select the first line, and make sure that the **Field** field is set to **Date**.
    1. In the **Criteria** field, select the current date.
    1. Select **OK** to close the **Intrastat Filter** dialog box.
    1. Select **OK** to close the **Intrastat (Transfer)** dialog box, and review the result. The line represents the sales order that you created earlier.

        :::image type="content" source="../media/intrastat_deu_1.png" alt-text="Screenshot of line that represents the sales order on the Intrastat page.":::

1. Select the transaction line, and then select the **General** tab to view more details.

    :::image type="content" source="../media/intrastat_deu_2.png" alt-text="Screenshot of sales order details on the General tab of the Intrastat page.":::

1. Create a credit note by using a sales order.

    1. Go to **Accounts receivable** > **Orders** > **All sales orders**.
    1. On the Action Pane, select **New**.
    1. In the **Create sales order** dialog box, on the **Customer** FastTab, in the **Customer** section, in the **Customer account** field, select **DE-012**.
    1. On the **General** FastTab, in the **Storage dimensions** section, in the **Site** field, select **1**.
    1. In the **Warehouse** field, select **11**.
    1. On the **Header** tab, on the **Foreign trade** FastTab, in the **Port** field, select **53**.
    1. In the **Statistical procedure** field, select **31710**.
    1. On the **Lines** tab, on the **Sales order** **lines** FastTab, in the **Item number** field, select **D0001**. Then, in the **Quantity** field, enter **-2**.
    1. On the **Line details** FastTab, on the **Foreign trade** tab, in the **Transaction code** field, select **21**.
    1. Make sure that the **Transport**, **Commodity**, and **Country/region of origin** fields are automatically set.
    1. On the Action Pane, select **Save**.
    1. On the Action Pane, on the **Invoice** tab, in the **Generate** section, select **Invoice**.
    1. In the **Posting invoice** dialog box, on the **Parameters** FastTab, in the **Parameter** section, in the **Quantity** field, select **All**.
    1. Select **OK** to post the invoice.

1. Transfer the transaction to the Intrastat journal, and review the result.

    1. Go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
    1. On the Action Pane, select **Transfer**.
    1. In the **Intrastat (Transfer)** dialog box, in the **Parameters** section, set the **Customer invoice** option to **Yes**.
    1. Select **OK** to close the **Intrastat (Transfer)** dialog box, and review the result. A new line where the **Direction** field is set to **Arrivals** has been added.            
        This line represents the physical return of goods.

        :::image type="content" source="../media/intrastat_deu_3.png" alt-text="Screenshot of line for the physical return on goods on the Intrastat page.":::

1. Select the transaction line, and then select the **General** tab to view more details.

    :::image type="content" source="../media/intrastat_deu_4.png" alt-text="Screenshot of details of the physical return of goods on the General tab of the Intrastat page.":::

1. Create a correction by using a sales order:

    1. Go to **Accounts receivable** > **Orders** > **All sales orders**.
    1. On the Action Pane, select **New**.
    1. In the **Create sales order** dialog box, on the **Customer** FastTab, in the **Customer** section, in the **Customer account** field, select **DE-012**.
    1. On the **General** FastTab, in the **Storage dimensions** section, in the **Site** field, select **1**.
    1. In the **Warehouse** field, select **11**.
    1. On the **Header** tab, on the **Foreign trade** FastTab, in the **Port** field, select **53**.
    1. In the **Statistical procedure** field, select **31710**.
    1. On the **Lines** tab, on the **Sales order** **lines** FastTab, in the **Item number** field, select **D0001**. Then, in the **Quantity** field, enter **-3**.
    1. On the **Line details** FastTab, on the **Foreign trade** tab, in the **Transaction code** field, select **11**.
    1. Make sure that the **Transport**, **Commodity**, and **Country/region of origin** fields are automatically set.
    1. On the Action Pane, select **Save**.
    1. Make sure that the **Transaction code** field is set to 11.
    1. On the Action Pane, on the **Invoice** tab, in the **Generate** section, select **Invoice**.
    1. In the **Posting invoice** dialog box, on the **Parameters** FastTab, in the **Parameter** section, in the **Quantity** field, select **All**.
    1. Select **OK** to post the invoice.

1. Transfer the transaction to the Intrastat journal, and review the result:

    1. Go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
    1. On the Action Pane, select **Transfer**.
    1. In the **Intrastat (Transfer)** dialog box, in the **Parameters** section, set the **Customer invoice** option to **Yes**.
    1. Select **OK** to close the **Intrastat (Transfer)** dialog box, and review the result. A new line where a check mark appears in the **Correction** column has been added.

        :::image type="content" source="../media/intrastat_deu_5.png" alt-text="Screenshot of line for the correction on the Intrastat page.":::

1. Select the transaction line, and then select the **General** tab to view more details.

    :::image type="content" source="../media/intrastat_deu_6.png" alt-text="Screenshot of details of the correction on the General tab of the Intrastat page.":::

1. On the action pane, select **Output** > **Report**.
1. In the **Intrastat Report** dialog box, on the **Parameters** FastTab, in the **Date** section, select the month of the sales order that you created.
1. In the **Export** **options** section, set the **Generate file** option to **Yes**.
1. In the **File name** field, enter the required name.
1. Select **OK**, and review the report that is generated. The following table shows the values in the example report.

    | **Name**                  | **Sales invoice**  |   **Correction**   | **Credit note** |
    |---------------------------|--------------------|--------------------|-----------------|
    | declarationId             | 2021-07-D          | 2021-07-A          |                 |
    | referencePeriod           | 2021-07            | 2021-07            |                 |
    | PSIId                     | 11203/118/12345000 | 11203/118/12345000 |                 |
    | functionCode              | O                  | O                  |                 |
    | flowCode                  | D                  | A                  |                 |
    | CurrencyCode              | EUR                | EUR                |                 |
    | itemNumber                | 0000362            | 0000362            | 0000361         |
    | CN8Code                   | 9202034            | 9202034            | 9202034         |
    | goodsDescription          | Speaker            | Speaker            | Speaker         |
    | MSConsDestCode            | FR                 | FR                 | FR              |
    | countryOfOriginCode       | \-                 | \-                 | DE              |
    | netMass                   | 120                | -36                | 24              |
    | invoicedAmount            | 3290               | -987               | \-              |
    | StatisticalValue          | 3290               | -987               | 658             |
    | natureOfTransactionACode  | 1                  | 1                  | 2               |
    | natureOfTransactionBCode  | 1                  | 1                  | 1               |
    | modeOfTransportCode       | 01                 | 01                 | 01              |
    | regionCode                | 11                 | 11                 | 11              |
    | portAirportInlandportCode | 53                 | 53                 | 53              |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
