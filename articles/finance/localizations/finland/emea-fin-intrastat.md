---
title: Finnish Intrastat
description: Learn about the Finnish Intrastat report, including an outline on setting up VAT IDs table that defines various fields.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/11/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2018-02-03
---

# Finnish Intrastat

[!include [banner](../../includes/banner.md)]

Use the **Intrastat** page to generate and report information about trade among European Union (EU) countries and regions. The Finnish Intrastat declaration contains information about the trade of goods for reporting.

The Finnish Intrastat declaration includes the following fields. All of the fields are included on arrivals and dispatches except for **VAT number of trading partner**, which isn't included on arrivals.

| Field | Description |
|-------------------------|-------------------------|
| Data provider | The value-added tax (VAT) ID of the data provider. This ID is set on the **Registration IDs** tab of the **Legal entity** page. |
| Statistical period | The reporting period of the Intrastat report. |
| Declaration number | The direction of the Intrastat report.</br><ul><li>For an Intrastat report on arrivals, "1" is printed.</li><li>For an Intrastat report on dispatches, "2" is printed.</li> |
| Agent | The VAT number of the agent. This number is set in the **Tax exempt number** field on the **Agent** tab of the **Foreign trade parameters** page. |
| VAT number of trading partner | The tax-exempt number of the counterparty. |
| Commodity code | The commodity code according to the Combined Nomenclature (CN) classification. This code is set on the product page. |
| Country of consignment (arrivals) / Country of destination (dispatches) | The International Organization for Standardization (ISO) code of the country/region of the counterparty. |
| Country of origin | The ISO code of the country/region where the goods were produced. This code is set in the **Country of origin** field on the product page. |
| Nature of transaction | The transaction code. Companies in Finland use two-digit codes. |
| Mode of transport | The code of the mode of transport. Companies in Finland use one-digit transport codes. |
| Net mass | The net mass of the goods item in kilograms. The unit itself ("kg") isn't printed. |
| Supplementary unit | For some commodities, you must report the supplementary unit. The unit itself (for example, "pairs" or "dozens") isn't reported. |
| Invoice value | The invoice value. You can view the invoice value in the **Invoice amount** field in the Intrastat journal. |
| Statistical value | The statistical value. You can view the statistical value in the **Statistical value** field in the Intrastat journal. |

## Set up Intrastat

From the Global repository, import the latest version of the following electronic reporting (ER) configurations:

- Intrastat model
- Intrastat report
- Intrastat (FI)

For more information, see [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

### Set up VAT IDs

#### Create a registration type for the company code

1. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration types**.
1. On the Action Pane, select **New** to create a registration type for the VAT ID.
1. In the **Enter registration type details** dialog box, in the **Name** field, enter a name for the new registration type. For example, enter **VAT ID**.
1. In the **Country/region** field, select **FIN**.
1. Select **Create**.

   You must also create VAT ID registration types for all the countries or regions that your company does business with.

#### Match the registration type with a registration category

1. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration categories**.
1. On the Action Pane, select **New** to create a link between a registration type and a registration category.
1. For the registration type for the VAT ID, select the **VAT ID** registration category.
1. Repeat steps 2 through 3 for the other registration types that you created for the countries/regions that your company does business with.

#### Set up the VAT ID of the data provider for your company

1. Go to **Organization administration** > **Organizations** > **Legal entities**.
1. In the grid, select your company.
1. On the Action Pane, select **Registration IDs**.
1. On the **Registration ID** FastTab, select **Add**.
1. In the **Registration type** field, select the registration type that you created for the company code earlier in this article.
1. Enter the VAT ID of your company's data provider.

#### Set up the VAT number of a trading partner

##### Create a customer's VAT registration number

1. Go to **Accounts receivable** > **Customers** > **All customers**.
1. In the grid, select a customer.
1. On the Action Pane, on the **Customer** tab, in the **Registration** group, select **Registration IDs**.
1. On the **Registration ID** FastTab, select **Add** to create a registration ID.
1. In the **Registration type** field, select the registration type that you created for the company code earlier in this article.
1. In the **Registration number** field, enter the company's VAT number.
1. On the Action Pane, select **Save**. Then close the page.

For more information, see [Registration IDs](../europe/emea-registration-ids.md).

Alternatively, you can create a customer's VAT registration numbers by using the **Tax exempt number** page.

1. Go to **Tax** > **Setup** > **Sales tax** > **Tax exempt numbers**.
1. For each tax-exempt number, create a record that includes the following information:

    - **Country/region** – Select the tax registration of the counterparty.
    - **Tax exempt number** – Enter the tax-exempt number of the counterparty.
    - **Company name** – Enter the name of the counterparty.

1. Go to **Accounts receivable** > **Customers** > **All customers**.
1. In the grid, select a customer.
1. On the **Invoice and delivery** FastTab, in the **Sales tax** section, in the **Tax exempt number** field, select the registration number that you just created.

### Set up foreign trade parameters

1. Go to **Tax** > **Setup** > **Foreign trade parameters**.
1. On the **Intrastat** tab, on the **Electronic reporting** FastTab, in the **File format mapping** field, select **Intrastat (FI)**.
1. In the **Report format mapping** field, select **Intrastat report**.
1. On the **Commodity code hierarchy** FastTab, in the **Category hierarchy** field, select **Intrastat**.
1. In the **Transaction code** field, select the transaction code for property transfers. Use this code for transactions that produce actual or planned transfers of property against compensation (financial or otherwise). Also use it for corrections. Companies in Finland use two-digit transaction codes.
1. In the **Credit note** field, select the transaction code for the return of goods. Use this code for returns of goods.
1. On the **Country/region properties** tab, in the **Country/region** field, list all the countries or regions that your company does business with. For each country that is part of the EU, in the **Country/region type** field, select **EU**, so that the country appears on your Intrastat report.
1. On the **Agent** tab, add information about the company that provides the statistical declaration. In the **Sales tax** section, in the **Tax exempt number** field, enter the VAT number of the agent.

### Set up the product parameters for the Intrastat declaration

1. Go to **Product information management** > **Products** > **Released products**.
1. In the grid, select a product.
1. On the **Foreign trade** FastTab, in the **Intrastat** section, in the **Commodity** field, select the commodity code.
1. In the **Origin** section, in the **Country/region** field, select the product's country/region of origin.
1. On the **Manage inventory** FastTab, in the **Net weight** field, enter the product's weight in kilograms.
1. Go to **Tax** > **Setup** > **Foreign trade** > **Compression of Intrastat**, and select the fields that should be compared when Intrastat information is summarized. For Finnish Intrastat, select the following fields:

    - Commodity
    - Transaction code
    - Country/region of origin
    - Transport
    - Country/region of sender
    - Country/region
    - Tax exempt number
    - Direction
    - Invoice

#### Set up the transport method

1. Go to **Tax** > **Setup** > **Foreign trade** > **Transport method**.
1. On the action pane, select **New**.
1. In the **Transport** field, enter a unique code. Companies in Finland use one-digit transport codes.

### Intrastat transfer

On the **Intrastat** page, on the Action Pane, select **Transfer** to automatically transfer the information about intracommunity trade from your sales orders, free text invoices, purchase orders, vendor invoices, vendor product receipts, project invoices, and transfer orders. Only documents that have an EU country as the country/region of destination (for dispatches) or consignment (for arrivals) are transferred.

Alternatively, you can manually enter transactions by selecting **New** on the Action Pane.

#### Generate an Intrastat report

1. Go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
1. On the Action Pane, select **Output** > **Report**.
1. In the **Intrastat Report** dialog box, enter the start and end dates for the report.
1. Set the **Generate file** option to **Yes** to generate a .txt file, and then enter the name of the .txt file for the Intrastat report.
1. Set the **Generate report** option to **Yes** to generate an .xlsx file, and then enter a name for the file.
1. In the **Direction** field, select **Arrivals** if the report is about intracommunity arrivals or **Dispatches** if the report is about intracommunity dispatches.
1. Select **OK**, and review the generated reports.

## Example

This example shows how to post arrivals and dispatches for Intrastat. It uses the **DEMF** legal entity.

### Preliminary setup

1. Go to **Organization administration** > **Organization** > **Legal entities**, and select the **DEMF** legal entity.
1. On the **Addresses** FastTab, select **Edit**.
1. In the **Country/region** field, select **FIN (Finland)**.
1. Import the latest version of the following ER configurations:

    - Intrastat model
    - Intrastat report
    - Intrastat (FI)

### Set up VAT IDs

#### Create registration types for company codes

1. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration types**.
1. Verify that the **VATID** registration type exists for German VAT IDs.
1. On the Action Pane, select **New** to create a registration type for the VAT ID.
1. In the **Enter registration type details** dialog box, enter **VAT ID** in the **Name** field.
1. In the **Country/region** field, select **FIN**.
1. Select **Create**.

#### Match the registration type with a registration category

1. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration categories**.
1. Verify that the **VATID** registration type for Germany matches with the **VAT ID** registration category.
1. On the Action Pane, select **New** to create a link between the registration type and the registration category.
1. For the **VAT ID** registration type, select the **VAT ID** registration category.

#### Set up the VAT ID of the data provider for your company

1. Go to **Organization administration** > **Organizations** > **Legal entities**.
1. In the grid, select **DEMF**.
1. On the Action Pane, select **Registration IDs**.
1. On the **Registration ID** FastTab, select **Add**.
1. In the **Registration type** field, select **VAT ID**.
1. In the **Registration number** field, enter **FI02345678**.

#### Set up the customer's VAT registration number

1. Go to **Accounts receivable** > **Customers** > **All customers**.
1. In the grid, select **DE-016**.
1. On the Action Pane, on the **Customer** tab, in the **Registration** group, select **Registration IDs**.
1. On the **Registration ID** FastTab, select **Add** to create a registration ID.
1. In the **Registration type** field, select **VATID**.
1. In the **Registration number** field, enter **DE9012**.
1. On the Action Pane, select **Save**. Then close the page.

### Set up foreign trade parameters

1. Go to **Tax** > **Setup** > **Foreign trade** > **Foreign trade parameters**.
1. On the **Intrastat** tab, on the **General** FastTab, in the **Transaction** **code** field, select **11**.
1. On the **Electronic reporting** FastTab, in the **File format mapping** field, select **Intrastat (FI)**.
1. In the **Report format mapping** field, select **Intrastat Report**.
1. On the **Commodity code hierarchy** FastTab, verify that the **Category hierarchy** field is set to **Intrastat**.
1. On the **Country/region properties** tab, select **New**.
1. In the **Party country/region** field, select **FIN**.
1. In the **Country/region type** field, select **Domestic**.
1. In the **Party country/region** field, select **DEU**. Then, in the **Country/region type** field, select **EU**.
1. On the **Agent** tab, on the **Agent** FastTab, in the **Sales tax** section, in the **Tax exempt number** field, enter **FI87654320**.

### Set up product information

1. Go to **Product information management** > **Products** > **Released** **products**.
1. In the grid, select **D0001**.
1. On the **Foreign trade** FastTab, in the **Intrastat** section, in the **Commodity** field, select **100 200 30**.
1. In the **Origin** section, in the **Country/region** field, select **FIN**.
1. On the **Manage inventory** FastTab, in the **Weight measurements** section, in the **Net weight** field, enter **2**.
1. On the action pane, select **Save**.
1. In the grid, select **D0003**.
1. On the **Foreign trade** FastTab, in the **Intrastat** section, in the **Commodity** field, select **100 200 30**.
1. In the **Origin** section, in the **Country/region** field, select **DEU**.
1. On the **Manage inventory** FastTab, in the **Weight measurements** section, in the **Net weight** field, enter **5**.
1. On the action pane, select **Save**.

### Change the site address

1. Go to **Warehouse management** > **Setup** > **Warehouse** > **Sites**.
1. In the grid, select **1**.
1. On the **Addresses** FastTab, select **Edit**.
1. In the **Edit address** dialog box, select **FIN** in the **Country/region** field.
1. Select **OK**.

### Set up a transport method

1. Create a new transport method.

    1. Go to **Tax** > **Setup** > **Foreign trade** > **Transport method**.
    1. On the action pane, select **New**.
    1. In the **Transport** field, enter **3**.
    1. In the **Description** field, enter **Road transport**.

2. Assign the transport method to the mode of delivery. By using this step, you set up the default values for the transport method when you select the corresponding mode of delivery.

    1. Go to **Procurement and sourcing** > **Setup** > **Distribution** > **Modes of delivery**.
    1. In the grid, select **10**.
    1. On the **Foreign trade** FastTab, in the **Transport** field, select **3**.

3. Select the default mode of delivery for a customer.

    1. Go to **Accounts receivable** > **Customers** > **All customers**.
    1. In the grid, select **DE-016**.
    1. On the **Invoice and delivery** FastTab, in the **Mode of delivery** field, select **10**.

4. Select the default mode of delivery for a vendor.

    1. Go to **Accounts payable** > **Vendors** > **All vendors**.
    1. In the grid, select **DE-001**.
    1. On the **Invoice and delivery** FastTab, in the **Mode of delivery** field, select **10**.

### Create a sales order with an EU customer

1. Go to **Accounts receivable** > **Orders** > **All sales orders**.
1. On the action pane, select **New**.
1. In the **Create sales order** dialog box, on the **Customer** FastTab, in the **Customer** section, in the **Customer account** field, select **DE-016**.
1. On the **General** FastTab, in the **Storage dimensions** section, in the **Site** field, select **1**.
1. In the **Warehouse** field, select **11**.
1. Select **OK**.
1. On the **Lines** tab, on the **Sales order lines** FastTab, in the **Item number** field, select **D0001**. Then, in the **Quantity** field, enter **10**.
1. On the **Line details** FastTab, on the **Foreign trade** tab, verify that the **Transaction code**, **Transport**, **Commodity**, and **Country/region of origin** fields are automatically set.
1. On the action pane, select **Save**.
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

    :::image type="content" source="../media/intrastat_fi_1.png" alt-text="Screenshot of the line that represents the sales order on the Intrastat page.":::

9. Select the transaction line, and then select the **General** tab to view more details.

    :::image type="content" source="../media/intrastat_fi_2.png" alt-text="Screenshot of the sales order details on the General tab of the Intrastat page.":::

10. On the action pane, select **Output** &gt; **Report**.
11. In the **Intrastat Report** dialog box, on the **Parameters** FastTab, in the **Date** section, select the month of the sales order that you created.
12. In the **Export** **options** section, set the **Generate file** option to **Yes**. Then, in the **File name** field, enter the required name.
13. Set the **Generate report** option to **Yes**. Then, in the **Report file name** field, enter the required name.
14. In the **Direction** field, select **Dispatches**.
15. Select **OK**, and review the report in text format that is generated. The following table shows the values in the example report.

    | Field                               | Value      |
    |-------------------------------------|------------|
    | Data provider                       | FI02345678 |
    | Statistical period                  | 202110     |
    | Declaration number                  | 2          |
    | Agent                               | FI87654320 |
    | VAT number of trading partner       | DE9012     |
    | Commodity code                      | 10020030   |
    | Nature of transaction               | 11         |
    | Country of destination (dispatches) | DE         |
    | Country of origin                   | FI         |
    | Mode of transport                   | 3          |
    | Net mass                            | 20         |
    | Invoice value                       | 3290       |
    | Statistical value                   | 3290       |

1. Review the report in Excel format that is generated.

    :::image type="content" source="../media/intrastat_fi_3.png" alt-text="Screenshot of the Intrastat report on dispatches.":::

### Create a purchase order

1. Go to **Accounts payable** > **Purchase orders** > **All purchase orders**.
1. On the action pane, select **New**.
1. In the **Create purchase order** dialog box, in the **Vendor account** field, select **DE-001**.
1. Select **OK**.
1. On the **Header** tab, on the **Foreign** **trade** FastTab, verify that the **Transaction code** field is set to **11**.
1. On the **Lines** tab, on the **Purchase order lines** FastTab, in the **Item number** field, select **D0003**. Then, in the **Quantity** field, enter **6**.
1. On the **Line details** FastTab, on the **Foreign trade** tab, in the **Foreign trade** section, verify that the **Transaction code**, **Transport**, **Commodity**, and **Country/region of origin** fields are automatically set.
1. On the Action Pane, on the **Purchase** tab, in the **Actions** group, select **Confirm**.
1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
1. On the Action Pane, select **Default from**. In the **Default quantity for lines** field, select **Ordered quantity**. Then select **OK**.
1. On the **Vendor invoice header** FastTab, in the **Invoice identification** section, in the **Number** field, enter **0010**.
1. In the **Invoice dates** section, in the **Invoice date** field, select **10/5/2021** (October 5, 2021).
1. On the Action Pane, select **Post** to post the invoice.

### Create an Intrastat declaration for arrivals

1. Go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
1. On the action pane, select **Transfer**.
1. In the **Intrastat (Transfer)** dialog box, set the **Vendor invoice** option to **Yes**.
1. Select **OK** to transfer the transactions, and review the Intrastat journal.

    :::image type="content" source="../media/intrastat_fi_4.png" alt-text="Screenshot of the line that represents the purchase order on the Intrastat page.":::

1. Review the **General** tab for the purchase order.

    :::image type="content" source="../media/intrastat_fi_5.png" alt-text="Screenshot of the purchase order details on the General tab of the Intrastat page.":::

1. On the Action Pane, select **Output** > **Report**.
1. In the **Intrastat Report** dialog box, on the **Parameters** FastTab, in the **Date** section, select the month of the purchase order that you created.
1. In the **Export options** section, set the **Generate file** option to **Yes**. Then, in the **File name** field, enter the required name.
1. Set the **Generate report** option to **Yes**. Then, in the **Report file name** field, enter the required name.
1. In the **Direction** field, select **Arrivals**.
1. Select **OK**, and review the report in text format that is generated. The following table shows the values in the example report.

    | Field                             | Value      |
    |-----------------------------------|------------|
    | Data provider                     | FI02345678 |
    | Statistical period                | 202110     |
    | Declaration number                | 1          |
    | Agent                             | FI87654320 |
    | Commodity code                    | 10020030   |
    | Nature of transaction             | 11         |
    | Country of consignment (arrivals) | DE         |
    | Country of origin                 | DE         |
    | Mode of transport                 | 3          |
    | Net mass                          | 30         |
    | Invoice value                     | 965        |
    | Statistical value                 | 965        |

1. Review the report in Excel format that is generated.

    :::image type="content" source="../media/intrastat_fi_6.png" alt-text="Screenshot of the Intrastat report on arrivals.":::

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
