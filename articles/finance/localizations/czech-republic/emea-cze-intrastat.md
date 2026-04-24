---
title: Czech Intrastat
description: Learn about the Czech Intrastat report, including a table the defines various field names and on outline on setting up Intrastat.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/05/2026
ms.reviewer: johnmichalak
ms.search.region: Global
---

# Czech Intrastat

[!include [banner](../../includes/banner.md)]

The **Intrastat** page is used to generate and report information about trade among European Union (EU) countries/regions. The Czech Intrastat declaration contains information about the trade of goods for reporting.

The Czech Intrastat declaration includes the following fields. All the fields except **VAT number of trading partner** appear on both arrivals and dispatches. The **VAT number of trading partner** field appears only on dispatches.

| Field name | Description |
|-------------------------|-------------------------|
| Declaration month | The reference month of the declaration. |
| Declaration year | The reference year of the declaration. |
| VAT registration number | Value-added tax (VAT) ID of the company that provides the statistical declaration. |
| The report direction | For arrivals, the value is "1".</br>For dispatches, the value is "2". |
| VAT number of trading partner | The customer's foreign VAT number in an EU member state. |
| Country of consignment (arrivals) / Country of destination (dispatches) | The International Organization for Standardization (ISO) code of the country or region of the counterparty. |
| Country of origin | The ISO code of the country or region where the goods were produced. |
| Nature of transaction | The transaction code. |
| Mode of transport | The code for the mode of transport. Companies in Czech Republic use one-digit transport codes. |
| Delivery terms | The Intrastat code for the delivery terms. Companies in Czech Republic use one-digit codes. |
| Code of movement | The two-digit code for the movement of special goods. The default value is specified in the **Special movement code** field on the **General** tab of the **Foreign trade parameters** page. You can overwrite the default value when you create an order. |
| Commodity code | The commodity code according to the Combined Nomenclature (CN) classification. Set this code on the product page. |
| Statistical sign | For some commodities, you must report the supplementary statistical sign. Set this code on the product page. |
| Description of goods | The trade name of the commodity. |
| Net mass | The net mass of the goods item in kilograms. The unit itself ("kg") isn't printed. |
| Quantity of supplementary goods | For some commodities, you must report the supplementary unit. The unit itself (for example, "pairs" or "dozens") isn't reported. |
| Invoice amount | The invoice value. |

## Set up Intrastat

From the Global repository, import the latest version of the following Electronic reporting (ER) configurations:

- Intrastat model
- Intrastat report
- Intrastat (CZ)

For more information, see [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

### Set up VAT IDs

#### Set up the VAT ID of your company

1. In Microsoft Dynamics 365 Finance, go to **Organization administration** > **Organizations** > **Legal entities**.
1. In the grid, select your company.
1. On the **Tax registration** FastTab, in the **Tax registration number** field, enter the VAT ID for your company.

#### Set up the VAT number of a trading partner

##### Create a registration type for the company code

You must create VAT ID registration types for all the countries or regions that your company does business with.

1. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration types**.
1. On the Action Pane, select **New** to create a registration type for the VAT ID.
1. In the **Enter registration type details** dialog box, in the **Name** field, enter a name for the new registration type. For example, enter **VAT ID**.
1. In the **Country/region** field, select the country or region that your company does business with.
1. Select **Create**.

##### Match the registration type with a registration category

1. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration categories**.
1. On the Action Pane, select **New** to create a link between a registration type and a registration category.
1. For the registration type for the VAT ID, select the **VAT ID** registration category.
1. Repeat steps 2 through 3 for the other registration types that you created for the countries or regions that your company does business with.

##### Create a customer's VAT registration number

1. Go to **Accounts receivable** > **Customers** > **All customers**.
1. In the grid, select a customer.
1. On the Action Pane, on the **Customer** tab, in the **Registration** group, select **Registration IDs**.
1. On the **Registration ID** FastTab, select **Add** to create a registration ID.
1. In the **Registration type** field, select the registration type that you previously created for the company code.
1. In the **Registration number** field, enter the company's VAT number.
1. On the Action Pane, select **Save**. Then close the page.

For more information, see [Registration IDs](../europe/emea-registration-ids.md).

Alternatively, you can create a customer's VAT registration number by using the **Tax exempt number** page.

1. Go to **Tax** > **Setup** > **Sales tax** > **Tax exempt numbers**.
1. For each tax-exempt number, create a record that includes the following information:

    - In the **Country/region** field, select the tax registration of the counterparty.
    - In the **Tax exempt number** field, enter the tax-exempt number of the counterparty.
    - In the **Company name** field, enter the name of the counterparty.

1. Go to **Accounts receivable** > **Customers** > **All customers**.
1. In the grid, select a customer.
1. On the **Invoice and delivery** FastTab, in the **Sales tax** section, in the **Tax exempt number** field, select the registration number that you just created.

## Set up the statistical signs for commodities

1. Go to **Tax** > **Setup** > **Foreign trade** > **Statistics procedure**.
1. On the Action Pane, select **New**.
1. In the **Commodity** field, select the commodity code that requires a statistical sign.
1. In the **Statistics procedure** field, enter the required statistical sign.
1. Repeat steps 2 through 4 for other commodity codes.

## Set up product parameters for the Intrastat declaration

1. Go to **Product information management** > **Products** > **Released products**.
1. In the grid, select a product.
1. On the **Foreign trade** FastTab, in the **Intrastat** section, in the **Commodity** field, select the commodity code. The name of the commodity prints in the **Description of commodities** field in the Intrastat declaration.
1. In the **Statistics procedure** field, select the statistical sign if it's required. The available values depend on the commodity code that you selected.
1. In the **Origin** section, in the **Country/region** field, select the product's country or region of origin.
1. On the **Manage inventory** FastTab, in the **Net weight** field, enter the product's weight in kilograms.

## Set up the transport method and delivery terms

1. Set up transport codes.

    1. Go to **Tax** > **Setup** > **Foreign trade** > **Transport method**.
    1. On the Action Pane, select **New**.
    1. In the **Transport** field, enter a unique code. Czech companies use one-digit transport codes.

1. Set up mode of delivery Intrastat codes.

    1. Go to **Procurement and sourcing** > **Setup** > **Distribution** > **Terms of delivery**.
    1. In the grid, select a set of delivery terms.
    1. On the **General** FastTab, in the **Intrastat code** field, enter the unique code.

## Set up the special movements codes

1. Go to **Tax** > **Setup** > **Foreign trade** > **Special movements**.
1. On the Action Pane, select **New** to create the special movement code.
1. In the **Special movements** field, enter the unique code.
1. In the **Description** field, enter a description of the code.

## Set up foreign trade parameters

1. Go to **Tax** > **Setup** > **Foreign trade parameters**.
1. On the **Intrastat** tab, on the **Electronic reporting** FastTab, in the **File format mapping** field, select **Intrastat (CZ)**.
1. In the **Report format mapping** field, select **Intrastat report**.
1. On the **Commodity code hierarchy** FastTab, in the **Category hierarchy** field, select **Intrastat**.
1. In the **Transaction code** field, select the transaction code for property transfers.
1. In the **Credit note** field, select the transaction code for the return of goods.
1. In the **Special movement code** field, set the default value for purchase orders and sales orders. You can overwrite the default value when you create an order.
1. On the **Country/region properties** tab, in the **Country/region** field, list all the countries or regions that your company does business with. For each country or region that is part of the EU, select **EU** in the **Country/region type** field, so that the country or region appears on your Intrastat report. For Czech Republic, select **Domestic** in the **Country/region type** field.

## Set up compression of Intrastat

Go to **Tax** > **Setup** > **Foreign trade** > **Compression of Intrastat**, and select the fields that should be compared when Intrastat information is summarized. For Czech Intrastat, select the following fields:

- Commodity
- Transaction code
- Country/region of origin
- Statistics procedure
- Country/region of sender
- Special movement
- Correction
- Country/region
- Tax exempt number
- Invoice
- Direction
- Delivery terms
- Transport

## Intrastat transfer

On the **Intrastat** page, on the Action Pane, select **Transfer** to automatically transfer the information about intracommunity trade from your sales orders, free text invoices, purchase orders, vendor invoices, vendor product receipts, project invoices, and transfer orders. Only documents that have an EU country/region as the country or region of destination or consignment are transferred.

You can also manually enter transactions by selecting **New** on the Action Pane.

### Generate an Intrastat report

1. Go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
1. On the Action Pane, select **Output** &gt; **Report**.
1. In the **Intrastat Report** dialog box, enter the start date for the report.
1. Set the **Generate file** option to **Yes** to generate a .txt file, and then enter the name of the .txt file for the Intrastat report.
1. Set the **Generate report** option to **Yes** to generate an .xlsx file, and then enter a name for the file.
1. In the **Direction** field, select **Arrivals** if the report is about intracommunity arrivals, **Dispatches** if the report is about intracommunity dispatches, or **Both** if the report combines information about intracommunity arrivals and dispatches.
1. Select **OK**, and review the generated reports.

## Example

This example shows how to post arrivals and dispatches for Intrastat by using the **DEMF** legal entity.

### Preliminary setup

1. Go to **Organization administration** > **Organization** > **Legal entities**, and select the **DEMF** legal entity.
1. On the **Addresses** FastTab, select **Edit**, and then, in the **Country/region** field, select **CZE (Czech Republic)**.
1. Import the latest version of the following ER configurations:

    - Intrastat model
    - Intrastat report
    - Intrastat (CZ)

### Set up VAT IDs

#### Set up the VAT ID of your company

1. Go to **Organization administration** > **Organizations** > **Legal entities**.
1. In the grid, select **DEMF**.
1. On the **Tax registration** FastTab, in the **Tax registration number** field, enter **1234567890**.

#### Create registration types for company codes

1. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration types**.
1. On the Action Pane, select **New** to create a registration type for the VAT ID.
1. In the **Enter registration type details** dialog box, in the **Name** field, enter **VAT ID**.
1. In the **Country/region** field, select **DEU**.
1. In the **Restricted to** field, select **Organization**.
1. Select **Create**.

#### Match the registration type with a registration category

1. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration categories**.
1. On the Action Pane, select **New** to create a link between the registration type and the registration category.
1. For the **VAT ID** registration type, select the **VAT ID** registration category.

#### Set up the customer's VAT registration number

1. Go to **Accounts receivable** > **Customers** > **All customers**.
1. In the grid, select **DE-016**.
1. On the Action Pane, on the **Customer** tab, in the **Registration** group, select **Registration IDs**.
1. On the **Registration ID** FastTab, select **Add** to create a registration ID.
1. In the **Registration type** field, select **VATID**.
1. In the **Registration number** field, enter **DE0234**.
1. On the Action Pane, select **Save**. Then close the page.

### Set up the statistical signs for commodities

1. Go to **Tax** > **Setup** > **Foreign trade** > **Statistics procedure**.
1. On the Action Pane, select **New**.
1. In the **Commodity** field, select **100 200 30**.
1. In the **Statistics procedure** field, enter **50**.

### Set up product information

1. Go to **Product information management** > **Products** > **Released products**.
1. In the grid, select **D0001**.
1. On the **Foreign trade** FastTab, in the **Intrastat** section, in the **Commodity** field, select **100 200 30**.
1. In the **Statistics procedure** field, select **50**.
1. In the **Origin** section, in the **Country/region** field, select **CZE**.
1. On the **Manage inventory** FastTab, in the **Weight measurements** section, in the **Net weight** field, enter **2**.
1. On the Action Pane, select **Save**.
1. In the grid, select **D0003**.
1. On the **Foreign trade** FastTab, in the **Intrastat** section, in the **Commodity** field, select **100 200 30**.
1. In the **Statistics procedure** field, select **50**.
1. In the **Origin** section, in the **Country/region** field, select **DEU**.
1. On the **Manage inventory** FastTab, in the **Weight measurements** section, in the **Net weight** field, enter **5**.
1. On the Action Pane, select **Save**.

### Set up the special movements codes

1. Go to **Tax** > **Setup** > **Foreign trade** > **Special movements**.
1. On the Action Pane, select **New** to create the special movement code.
1. In the **Special movements** field, enter **ZR**.
1. In the **Description** field, enter **Staggered Consignments**.

### Set up foreign trade parameters

1. Go to **Tax** > **Setup** > **Foreign trade** > **Foreign trade parameters**.
1. On the **Intrastat** tab, on the **General** section, in the **Transaction code** field, select **11**.
1. In the **Special movement code** field, select **ZR**.
1. On the **Electronic reporting** section, in the **File format mapping** field, select **Intrastat (CZ)**.
1. In the **Report format mapping** field, select **Intrastat Report**.
1. On the **Commodity code hierarchy** section, verify that the **Category hierarchy** field is set to **Intrastat**.
1. On the **Country/region properties** tab, select **New**.
1. In the **Party country/region** field, select **CZE**. Then, in the **Country/region type** field, select **Domestic**.
1. In the **Party country/region** field, select **DEU**. Then, in the **Country/region type** field, select **EU**.

### Change the site address

1. Go to **Warehouse management** > **Setup** > **Warehouse** > **Sites**.
1. In the grid, select **1**.
1. On the **Addresses** section, select **Edit**.
1. In the **Edit address** dialog box, in the **Country/region** field, select **CZE**.
1. Select **OK**.

### Set up a transport method

1. Create a transport method.

    1. Go to **Tax** > **Setup** > **Foreign trade** > **Transport method**.
    1. On the Action Pane, select **New**.
    1. In the **Transport** field, enter **3**.
    1. In the **Description** field, enter **Road transport**.

1. Assign the new transport method to a mode of delivery. By doing this step, you set up the default values for the transport method when you select the corresponding mode of delivery.

    1. Go to **Procurement and sourcing** > **Setup** > **Distribution** > **Modes of delivery**.
    1. In the grid, select **10**.
    1. On the **Foreign trade** FastTab, in the **Transport** field, select **3**.

1. Select the default mode of delivery for a customer.

    1. Go to **Accounts receivable** > **Customers** > **All customers**.
    1. In the grid, select **DE-016**.
    1. On the **Invoice and delivery** FastTab, in the **Mode of delivery** field, select **10**.

1. Select the default mode of delivery for a vendor.

    1. Go to **Accounts payable** > **Vendors** > **All vendors**.
    1. In the grid, select **DE-001**.
    1. On the **Invoice and delivery** FastTab, in the **Mode of delivery** field, select **10**.

### Set up codes for terms of delivery

1. Set up an Intrastat code for the terms of delivery.

    1. Go to **Procurement and sourcing** > **Setup** > **Distribution** > **Terms of delivery**.
    1. In the grid, select **CIF**.
    1. On the **General** tab, in the **Intrastat code** field, enter **L**.

1. Select the default delivery terms for a customer.

    1. Go to **Accounts receivable** > **Customers** > **All customers**.
    1. In the grid, select **DE-016**.
    1. On the **Invoice and delivery** tab, in the **Delivery terms** field, select **CIF**.

1. Select the default delivery terms for a vendor.

    1. Go to **Accounts payable** > **Vendors** > **All vendors**.
    1. In the grid, select **DE-001**.
    1. On the **Invoice and delivery** tab, in the **Delivery terms** field, select **CIF**.

### Create a sales order with an EU customer

1. Go to **Accounts receivable** > **Orders** > **All sales orders**.
1. On the Action Pane, select **New**.
1. In the **Create sales order** dialog box, on the **Customer** FastTab, in the **Customer** section, in the **Customer account** field, select **DE-016**.
1. On the **General** FastTab, in the **Storage dimensions** section, in the **Site** field, select **1**.
1. In the **Warehouse** field, select **11**.
1. On the **Address** tab, verify that the **Address** field is set to **Teichgasse 12, Kiel, 24103, DEU**, because the customer is from Germany.
1. Select **OK**.
1. On the **Header** tab, on the **Delivery** FastTab, verify that the **Delivery terms** field is set to **CIF**, and the **Mode of delivery** field is set to **10**.
1. On the **Lines** tab, on the **Sales order lines** FastTab, in the **Item number** field, select **D0001**. Then, in the **Quantity** field, enter **8**.
1. On the **Line details** FastTab, on the **Foreign trade** tab, verify that the fields are set to the following values:

    - **Transaction code:** 11
    - **Transport:** 3
    - **Commodity:** 100 200 30
    - **Country/region of origin:** CZE
    - **Special movement:** ZR

1. On the Action Pane, select **Save**.
1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
1. In the **Posting invoice** dialog box, on the **Parameters** FastTab, in the **Parameter** section, in the **Quantity** field, select **All**.
1. Select **OK** to post the invoice.

### Transfer the transaction to the Intrastat journal and review the result

1. Go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
1. On the action pane, select **Transfer**.
1. In the **Intrastat (Transfer)** dialog box, in the **Parameters** section, set the **Customer invoice** option to **Yes**.
1. Select **Filter**.
1. In the **Intrastat Filter** dialog box, on the **Range** tab, select the first line, and verify that the **Field** field is set to **Date**.
1. In the **Criteria** field, select the current date.
1. Select **OK** to close the **Intrastat Filter** dialog box.
1. Select **OK** to close the **Intrastat (Transfer)** dialog box, and review the result. The line represents the sales order that you created earlier.

    :::image type="content" source="../media/intrastat_cz_1.png" alt-text="Screenshot of the line that represents the sales order on the Intrastat page.":::

1. Select the transaction line, and then select the **General** tab to view more details.

    :::image type="content" source="../media/intrastat_cz_2.png" alt-text="Screenshot of sales order details on the General tab of the Intrastat page.":::

1. On the action pane, select **Output** > **Report**.
1. In the **Intrastat Report** dialog box, on the **Parameters** FastTab, in the **Date** section, in the **From date** field, select the first day of the current month.
1. In the **Export options** section, set the **Generate file** option to **Yes**. Then, in the **File name** field, enter the required name.
1. Set the **Generate report** option to **Yes**. Then, in the **Report file name** field, enter the required name.
1. In the **Direction** field, select **Dispatches**.
1. Select **OK**, and review the report in text format that is generated. The following table shows the values in the example report.

    | Field name                                                              | Value      |
    |-------------------------------------------------------------------------|------------|
    | Declaration month                                                       | 11         |
    | Declaration year                                                        | 2021       |
    | VAT registration number                                                 | 1234567890 |
    | The report direction                                                    | 2          |
    | VAT number of trading partner                                           | DE0234     |
    | Country of consignment (arrivals) / Country of destination (dispatches) | DE         |
    | Country of origin                                                       | CZ         |
    | Nature of transaction                                                   | 11         |
    | Mode of transport                                                       | 3          |
    | Delivery terms                                                          | L          |
    | Code of movement                                                        | ZR         |
    | Commodity code                                                          | 10020030   |
    | Statistical sign                                                        | 50         |
    | Description of goods                                                    | Hardware   |
    | Net mass                                                                | 16         |
    | Quantity of supplementary goods                                         | 0.000      |
    | Invoice amount                                                          | 2632       |

1. Review the report in Excel format that is generated.

    :::image type="content" source="../media/intrastat_cz_3.png" alt-text="Screenshot of the Intrastat report on dispatches.":::

### Create a purchase order

1. Go to **Accounts payable** > **Purchase orders** > **All purchase orders**.
1. On the Action Pane, select **New**.
1. In the **Create purchase order** dialog box, in the **Vendor account** field, select **DE-001**.
1. In the **Site** field, select **1**.
1. In the **Warehouse** field, select **11**.
1. Select **OK**.
1. On the **Header** tab, on the **Delivery** FastTab, verify that the **Mode of delivery** field is set to **10**, and the **Delivery terms** field is set to **CIF**.
1. On the **Lines** tab, on the **Purchase order lines** FastTab, in the **Item number** field, select **D0003**. Then, in the **Quantity** field, enter **6**.
1. On the **Line details** FastTab, on the **Foreign trade** tab, verify that the fields are set to the following values:

    - **Transaction code**: 11
    - **Transport**: 3
    - **Commodity**: 100 200 30
    - **Country/region of origin**: DEU
    - **Special movement**: ZR

1. On the Action Pane, on the **Purchase** tab, in the **Actions** group, select **Confirm**.
1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
1. On the Action Pane, select **Default from**, and then, in the **Default quantity for lines** field, select **Ordered quantity**. Then select **OK**.
1. On the **Vendor Invoice header** FastTab, in the **Invoice identification** section, in the **Number** field, enter **0010**.
1. In the **Invoice dates** section, in the **Invoice date** field, select the current date. This date is used for Intrastat transfer.
1. On the Action Pane, select **Post** to post the invoice.

### Create an Intrastat declaration for arrivals

1. Go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
1. On the action pane, select **Transfer**.
1. In the **Intrastat (Transfer)** dialog box, set the **Vendor invoice** option to **Yes**.
1. Select **Filter**.
1. In the **Intrastat Filter** dialog box, on the **Range** tab, select the **Vendor invoice journal** line, and verify that the **Field** field is set to **Date**.
1. In the **Criteria** field, select the current date.
1. Select **OK** to close the **Intrastat Filter** dialog box.
1. Select **OK** to transfer the transactions, and review the Intrastat journal.

    :::image type="content" source="../media/intrastat_cz_4.png" alt-text="Screenshot of the line that represents the purchase order on the Intrastat page.":::

1. Review the information on the **General** tab for the purchase order.

    :::image type="content" source="../media/intrastat_cz_5.png" alt-text="Screenshot of purchase order details on the General tab of the Intrastat page.":::

1. On the action pane, select **Output** > **Report**.
1. In the **Intrastat Report** dialog box, on the **Parameters** FastTab, in the **Date** section, in the **From date** field, select the first day of the current month.
1. In the **Export options** section, set the **Generate file** option to **Yes**. Then, in the **File name** field, enter the required name.
1. Set the **Generate report** option to **Yes**. Then, in the **Report file name** field, enter the required name.
1. In the **Direction** field, select **Arrivals**.
1. Select **OK**, and review the report in XML format that is generated. The following table shows the values in the example report.

    | Field name                                                              | Value      |
    |-------------------------------------------------------------------------|------------|
    | Declaration month                                                       | 11         |
    | Declaration year                                                        | 2021       |
    | VAT registration number                                                 | 1234567890 |
    | The report direction                                                    | 1          |
    | Country of consignment (arrivals) / Country of destination (dispatches) | DE         |
    | Country of origin                                                       | DE         |
    | Nature of transaction                                                   | 11         |
    | Mode of transport                                                       | 3          |
    | Delivery terms                                                          | L          |
    | Code of movement                                                        | ZR         |
    | Commodity code                                                          | 10020030   |
    | Statistical sign                                                        | 50         |
    | Description of goods                                                    | Hardware   |
    | Net mass                                                                | 30         |
    | Quantity of supplementary goods                                         | 0.000      |
    | Invoice amount                                                          | 965        |

1. Review the report in Excel format that is generated.

    :::image type="content" source="../media/intrastat_cz_6.png" alt-text="Screenshot of the Intrastat report on arrivals.":::

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
