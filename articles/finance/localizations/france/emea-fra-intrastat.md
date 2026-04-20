---
title: French Intrastat
description: Learn about Intrastat declaration in France, including an outline on setting up Intrastat and a table that outlines report levels for various fields.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/11/2026
ms.reviewer: johnmichalak
ms.search.region: Global
---

# French Intrastat

[!include[banner](../../includes/banner.md)]

Companies in France that register for value-added tax (VAT) and trade with other European Union (EU) countries or regions must declare the exchange of goods and services to and from France. The **Declaration d'exchanges de biens** (Declaration of Trade in Goods, or DEB) combines the EU Sales List and the Intrastat report. You must submit this report monthly for all intracommunity sales of goods.

You can generate the DEB report in either of two electronic text file formats: SAISUNIC 330 or INTRACOM format.

The following table shows the fields that the French Intrastat declaration includes in SAISUNIC 330 format. The table also indicates the report levels of each field. A field can have the following report levels:

- **4** – Tax declaration.
- **1** – Statistical response.
- **5** – Statistical response to shipment and tax declaration, and joint filling.

| Field                       | Report levels |
|-----------------------------|---------------|
| Period of Reference         | 4, 1, 5       |
| Number Of Declaration       | 4, 1, 5       |
| Line Number                 | 4, 1, 5       |
| Country/region ISO Code (FR)       | 4, 1, 5       |
| Complementary Code          | 4, 1, 5       |
| Siren Number                | 4, 1, 5       |
| VAT Code of Customer        | 4, 1, 5       |
| Direction Code              | 4, 1, 5       |
| Transaction Type            | 4, 1, 5       |
| Obligation Level            | 4, 1, 5       |
| Commodity Code              | 1, 5          |
| National NGP                | 1, 5          |
| County (Department)         | 1, 5          |
| Nature Of Transaction       | 1, 5          |
| Country/regionOf Origination      | 1, 5          |
| Country/region of Origin - Imports | 1, 5          |
| Final Destination - Exports | 1, 5          |
| Invoice Value               | 4, 1, 5       |
| Statistical Value           | 1, 5          |
| Net Weight                  | 1, 5          |
| Additional Units            | 1, 5          |
| Transport Code              | 1, 5          |

The following table shows the fields that the French Intrastat declaration includes in INTRACOM format. The table also indicates the report levels of each field. A field can have the following report levels:

- **4** – Tax declaration.
- **1** – Statistical response.
- **5** – Statistical response to shipment and tax declaration, and joint filling.

| Field                       | Report levels |
|-----------------------------|---------------|
| Direction code              | 4, 1, 5       |
| Number Of Declaration       | 4, 1, 5       |
| Number Of Line              | 4, 1, 5       |
| Siren                       | 4, 1, 5       |
| County (Department)         | 1, 5          |
| Transport Code              | 1, 5          |
| Country/region Of Origin           | 1, 5          |
| Nature Of Transaction       | 1, 5          |
| Invoice Value               | 4, 1, 5       |
| Modes Of Delivery           | 1, 5          |
| Transaction Type            | 4, 1, 5       |
| Obligation Level            | 4, 1, 5       |
| Commodity Code              | 1, 5          |
| National NGP                | 1, 5          |
| Net Weight                  | 1, 5          |
| Statistical Value           | 1, 5          |
| Additional Units            | 1, 5          |
| Country/region of Origin - Imports | 1, 5          |
| Final Destination - Exports | 1, 5          |
| VAT Code of Customer        | 4, 1, 5       |
| Complementary Code          | 4, 1, 5       |
| Period of Reference         | 4, 1, 5       |

## Set up Intrastat

- In [Microsoft Dynamics Lifecycle Services](https://lcs.dynamics.com/Logon/Index), in the Shared asset library, download the latest versions of the following Electronic reporting (ER) configurations for the Intrastat declaration:

  - Intrastat model
  - Intrastat report
  - Intrastat INTRACOM (FR)
  - Intrastat SAISUNIC (FR)

    For more information, see [Download Electronic reporting configurations from Lifecycle Services](../../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

### Set up VAT IDs

#### Set up VAT codes for your company

1. Go to **Tax** > **Setup** > **Sales tax** > **Tax exempt numbers**.
1. On the action pane, select **New**.
1. In the **Country/region** field, select **FRA**.
1. In the **Tax exempt number** field, enter your company's VAT number key.
1. Go to **Organization administration** > **Organizations** > **Legal entities**, and select your company.
1. On the **Foreign trade and logistics** FastTab, in the **Intrastat** section, set the **VAT exempt number export** and **VAT exempt number import** fields to the code that you created in step 4.
1. On the **Tax registration** FastTab, in the **Tax registration number** field, enter your company's tax registration number.

#### Set up the VAT IDs for trading partners

##### Create a registration type for the company code

You must create VAT ID registration types for all the countries or regions that your company does business with.

1. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration types**.
2. On the action pane, select **New** to create a registration type for the VAT ID.
3. In the **Enter registration type details** dialog box, in the **Name** field, enter a name for the new registration type. For example, enter **VAT ID**.
4. In the **Country/region** field, select the country or region of the trading partner.
5. Select **Create**.

##### Match the registration type with a registration category

1. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration categories**.
2. On the action pane, select **New** to create a link between a registration type and a registration category.
3. For the registration type for the VAT ID, select the **VAT ID** registration category.
4. Repeat steps 2 and 3 for the other registration types that you created for the countries or regions that your company does business with.

##### Set up the VAT number of a trading partner

1. Go to **Accounts receivable** > **Customers** > **All customers**.
2. In the grid, select a customer.
3. On the action pane, on the **Customer** tab, in the **Registration** group, select **Registration IDs**.
4. On the **Registration ID** FastTab, select **Add** to create a registration ID.
5. In the **Registration type** field, select the registration type that you created for the company code.
6. In the **Registration number** field, enter the company's VAT number.
7. On the action pane, select **Save**, and then close the page.

For more information, see [Registration IDs](../europe/emea-registration-ids.md).

### Set up foreign trade parameters

1. Go to **Tax** > **Setup** > **Foreign trade** > **Foreign trade parameters**.
1. On the **Intrastat** tab, on the **Electronic reporting** FastTab, in the **File format mapping** field, select **Intrastat INTRACOM (FR)** or **Intrastat SAISUNIC (FR)**.
1. In the **Report format mapping** field, select **Intrastat report**.
1. On the **Commodity code hierarchy** FastTab, in the **Category hierarchy** field, select **Intrastat**.
1. On the **General** FastTab, in the **Transaction code** field, select the code that is used for transfers of goods.
1. In the **Credit note** field, select the code that is used for returns of goods.
1. In the **Worker** field, select the name of the contact person.
1. On the **Contact** tab, add information about the contact person:

    - In the **Telephone** field, enter the telephone number of the contact person.
    - In the **Fax** field, enter the fax number of the contact person.

1. On the **Country/region properties** tab, in the **Country/region** field, list all the countries or regions that your company does business with. For each country/region that is part of the EU, select **EU** in the **Country/region type** field, so that the country/region appears on your Intrastat report. For France, select **Domestic** in the **Country/region type** field.

### Set up compression of Intrastat

- Go to **Tax** > **Setup** > **Foreign trade** > **Compression of Intrastat**, and select the fields that should be compared when you summarize Intrastat information. For French Intrastat, select the following fields:

  - Statistics procedure
  - Country/region of origin
  - Transport
  - Correction
  - Country/region
  - County of origin/destination
  - Direction
  - Country/region of sender
  - Transaction code
  - Commodity

### Set up product parameters for the Intrastat declaration

1. Go to **Product information management** > **Products** > **Released products**.
1. In the grid, select a product.
1. On the **Foreign trade** FastTab, in the **Intrastat** section, in the **Commodity** field, select the commodity code. The name of the commodity is printed in the **Description of commodities** field on the Intrastat report.
1. In the **Origin** section, in the **Country/region** field, select the product's country or region of origin.
1. On the **Manage inventory** FastTab, in the **Net weight** field, enter the product's weight in kilograms.

### NGP codes

On the DEB report, the codification of products consists of the following elements:

- The eight-digit CN8 code that represents the tariff and statistical nomenclature of the EU.
- If applicable, the one-digit Nomenclature Générale des Produits (NGP) national item code.

In 2022, the NGP applies to only three types of products:

- Some products from cows, sheep, and goats
- Military equipment
- French wines

Set up the NGP codes and assign them to related products. The **NGP** field is then automatically set on the **Intrastat journal** page.

#### Set up an NGP code

1. Go to **Tax** > **Setup** > **Foreign trade** > **NGP codes**.
1. On the action pane, select **New**.
1. In the **NGP** field, enter a single-digit code.
1. In the **Description** field, enter a description for the code.

#### Assign an NGP code to a product

1. Go to **Product information management** > **Products** > **Released products**.
1. In the grid, select a product.
1. On the **Foreign trade** FastTab, in the **Intrastat** section, in the **NGP** field, select the appropriate NGP code.

### Set up warehouse parameters for the Intrastat declaration

1. Go to **Warehouse management** > **Setup** > **Warehouse** > **Warehouses**.
1. Select a warehouse, and then, on the **Addresses** FastTab, select **Add** or **Edit**.
1. In the dialog box, in the **City** field, select the warehouse's city. The city's state or province is used as a county for your DEB report.

### Set up the transport method

1. Go to **Tax** > **Setup** > **Foreign trade** > **Transport method**.
1. On the action pane, select **New**.
1. In the **Transport** field, enter a unique code. Companies in France use one-digit transport codes.

### Intrastat journal

Go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat** to manage your transactions that apply to foreign trade with EU countries or regions. For more information, see [Intrastat overview](../europe/emea-intrastat.md).

The **NGP** column is specific to France and shows the NGP code for the product. If the NGP code doesn't apply to a product, the column shows **0** (zero). To adjust the NGP code, select the transaction, and then, on the **General** tab, in the **Codes** section, enter the required NGP code in the **NGP** field.

#### Intrastat transfer

On the **Intrastat** page, on the action pane, you can select **Transfer** to automatically transfer the information about intracommunity trade from your sales orders, free text invoices, purchase orders, vendor invoices, vendor product receipts, project invoices, and transfer orders. Only documents that have an EU country/region as the country or region of destination (for dispatches) or consignment (for arrivals) will be transferred.

Because the DEB report is a combination of the EU Sales List and the Intrastat report, it also includes *triangular* transactions, where a direct delivery is made from one EU country/region (party A) to another EU country/region (party C), and a French legal entity (party B) is in the middle of the triangular deal.

#### Generate a DEB (Intrastat) report

1. Go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
1. On the action pane, select **Output** > **Report**.
1. In the **Intrastat Report** dialog box, set the following fields.

    | Field            | Description                                                                                                                         |
    |------------------|-------------------------------------------------------------------------------------------------------------------------------------|
    | From date        | Select the start date for the report.                                                                                               |
    | To date          | Select the end date for the report.                                                                                                 |
    | Generate file    | Set this option to **Yes** to generate a .txt file.                                                                                 |
    | File name        | Enter the name of the .txt file for your Intrastat report.                                                                          |
    | Generate report  | Set this option to **Yes** to generate an .xml file.                                                                                |
    | Report file name | Enter the required name.                                                                                                            |
    | Only corrections | Set this option to **Yes** to report only corrections. Set it to **No** to report both normal transactions and corrections.         |
    | Direction        | Select **Arrivals** for a report about intracommunity arrivals. Select **Dispatches** for a report about intracommunity dispatches. |

1. Select **OK** to close the **Intrastat Report** dialog box.
1. In the **Electronic report parameters** dialog box, on the **Parameters** tab, in the **Report level** field, select the report level. The report level can be **1 - statistical response**, **4 - tax declaration**, or **5 - statistical response to shipment and tax declaration**.

## Example

The following example shows how to set up French Intrastat and create the DEB report. It uses the **DEMF** legal entity.

### Preliminary setup

1. In [Microsoft Dynamics Lifecycle Services](https://lcs.dynamics.com/Logon/Index), in the Shared asset library, download the latest versions of the following ER configurations for the Intrastat declaration format:

    - Intrastat model
    - Intrastat report
    - Intrastat INTRACOM (FR)

2. Set up a product hierarchy:

    1. Go to **Product information management** > **Setup** > **Categories and attributes** > **Category hierarchies**.
    2. In the grid, select **Intrastat**.
    3. On the action pane, on the **Category hierarchy** tab, in the **Maintain** group, select **Edit**.
    4. On the action pane, select **New category node**.
    5. In the **Name** field, enter **Autres Libournais**.
    6. In the **Code** field, enter **2204 21 42**.
    7. On the action pane, select **Save**.

### Set up VAT IDs

#### Set up VAT codes for your company

1. Go to **Tax** > **Setup** > **Sales tax** > **Tax exempt numbers**.
1. On the action pane, select **New**.
1. In the **Country/region** field, select **FRA**.
1. In the **Tax exempt number** field, enter **MS123456**.
1. Go to **Organization administration** > **Organizations** > **Legal entities**, and select **DEMF**.
1. On the **Foreign trade and logistics** FastTab, in the **Intrastat** section, set the **VAT exempt number export** and **VAT exempt number import** fields to the code that you created in step 4.
1. On the **Tax registration** FastTab, in the **Tax registration number** field, enter **123456789**.

#### Set up the VAT IDs for trading partners

##### Create a registration type for the company code

1. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration types**.
2. On the action pane, select **New** to create a registration type for the VAT ID.
3. In the **Enter registration type details** dialog box, in the **Name** field, enter **VAT ID**.
4. In the **Country/region** field, select **DEU**.
5. Select **Create**.

##### Match the registration type with a registration category

1. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration categories**.
2. On the action pane, select **New** to create a link between the registration type and the registration category.
3. For the **VAT ID** registration type of the **DEU** country/region, select the **VAT ID** registration category.

##### Set up the customer's VAT registration number

1. Go to **Accounts receivable** > **Customers** > **All customers**.
2. In the grid, select **DE-016**.
3. On the action pane, on the **Customer** tab, in the **Registration** group, select **Registration IDs**.
4. On the **Registration ID** FastTab, select **Add** to create a registration ID.
5. In the **Registration type** field, select **VAT ID**.
6. In the **Registration number** field, enter **DE9012**.
7. On the action pane, select **Save**, and then close the page.
8. On the **Invoice and delivery** FastTab, in the **Sales tax** section, in the **Tax exempt number** field, select **DE9012**.

### Set up foreign trade parameters

1. Go to **Tax** > **Setup** > **Foreign trade** > **Foreign trade parameters**.
1. On the **Intrastat** tab, on the **General** section, select **11** in the **Transaction code** field.
1. On the **Electronic reporting** section, select **Intrastat INTRACOM (FR)** in the **File format mapping** field.
1. Select **Intrastat report** in the **Report format mapping** field.
1. On the **Commodity code hierarchy** section, select **Intrastat** in the **Category hierarchy** field.
1. Select a record in the **Worker** field.
1. On the **Contact** tab, enter the contact's telephone number in the **Telephone** field.
1. In the **Fax** field, enter the contact's fax number.

### Create NGP code

1. Go to **Tax** > **Setup** > **Foreign trade** > **NGP codes**.
2. On the action pane, select **New**.
3. Enter **8** in the **NGP** field.
4. Enter **NGP 8** in the **Description name** field.
5. On the action pane, select **Save**.

### Set up product information

1. Go to **Product information management** > **Products** > **Released products**.
1. In the grid, select **D0001**.
1. On the **Foreign trade** FastTab, in the **Intrastat** section, in the **NGP** field, select **8**.
1. In the **Commodity** field, select **2204 21 42**.
1. In the **Origin** section, in the **Country/region** field, select **FRA**.
1. On the **Manage inventory** FastTab, in the **Weight measurements** section, in the **Net weight** field, enter **2**.
1. On the action pane, select **Save**, and then close the page.
1. In the grid, select **D0003**.
1. On the **Foreign trade** FastTab, in the **Intrastat** section, in the **Commodity** field, select **100 200 30**.
1. In the **Origin** section, in the **Country/region** field, select **DEU**.
1. On the **Manage inventory** FastTab, in the **Weight measurements** section, in the **Net weight** field, enter **5**.
1. On the action pane, select **Save**.

### Set up Regime codes

1. Go to **Tax** > **Setup** > **Foreign trade** > **Statistics procedure**.
1. On the action pane, select **New**.
1. In the **Statistics procedure** field, enter **21**.
1. In the **Text 1** field, enter **Regime code 21**.

### Change the site address

1. Go to **Warehouse management** > **Setup** > **Warehouse** > **Sites**.
1. In the grid, select **1**.
1. On the **Addresses** FastTab, select **Edit**.
1. In the **Edit address** dialog box, in the **Country/region** field, select **FRA**.
1. Select **OK**.
1. Go to **Warehouse management** > **Setup** > **Warehouse** > **Warehouses**, and select a warehouse.
1. On the **Addresses** FastTab, select **Add**.
1. In the **New address** dialog box, in the **Country/region** field, select **FRA**.
1. In the **City** field, select **Bordeaux**.
1. Select **OK** to close the dialog box.

### Set up a transport method

1. Go to **Tax** > **Setup** > **Foreign trade** > **Transport method**.
1. On the action pane, select **New**.
1. In the **Transport** field, enter **3**.
1. In the **Description** field, enter **Road transport**.

### Assign a transport mode to a mode of delivery

1. Go to **Procurement and sourcing** > **Setup** > **Distribution** > **Modes of delivery**.
1. In the grid, select **50**.
1. On the **Foreign trade** FastTab, in the **Transport** field, select **3**.

### Create a sales order with an EU customer that includes the new product

1. Go to **Accounts receivable** > **Orders** > **All sales orders**.
2. On the action pane, select **New**.
3. In the **Create sales order** dialog box, in the **Customer** section, enter **DE-016** in the **Customer account** field.
4. In the **Address** section, select the plus sign (**+**) next to **Delivery address** to create an address.
5. In the **New address** dialog box, enter **Germany** in the **Name of description** field.
6. Select **DEU** in the **Country/region** field.
7. Select **OK**.
8. In the **Create sales order** dialog box, select **OK**.
9. On the **Sales order lines** FastTab, select **0001** in the **Item number** field.
10. On the **Lines details** FastTab, **Foreign trade** tab, select **21** in the **Statistics procedure** field.
11. Select **AL** in the **State of origin** field.
12. On the action pane, select **Save**.
13. On the **Header** tab, on the **Delivery** FastTab, make sure that **50** is selected in the **Mode of delivery** field.
14. On the action pane, on the **Invoice** tab, select **Invoice** in the **Generate** group.
15. In the **Posting invoice** dialog box, on the **Parameters** FastTab, select **All** in the **Quantity** field. Then select **OK** to post the invoice.

### Transfer the transaction to the Intrastat journal and review the result

1. Go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
1. On the action pane, select **Transfer**.
1. In the **Intrastat (Transfer)** dialog box, in the **Parameters** section, set the **Customer invoice** option to **Yes**. Then select **OK**.
1. Sort transactions by the **Date** field. The top transaction is the result transaction.

    :::image type="content" source="../media/intrastat_fr_1.png" alt-text="Screenshot of the line that represents the sales order on the Intrastat page.":::

1. Select the transaction line, and then select the **General** tab to view more details.

    :::image type="content" source="../media/intrastat_fr_2.png" alt-text="Screenshot of the sales order details on the General tab of the Intrastat page.":::

1. On the action pane, select **Output** > **Report**.
1. In the **Intrastat Report** dialog box, on the **Parameters** FastTab, in the **Date** section, select the month of the sales order that you created.
1. In the **Export options** section, set the **Generate file** option to **Yes**.
1. In the **File name** field, enter the required name.
1. Select **OK** to close the **Intrastat Report** dialog box.
1. In the **Electronic report parameters** dialog box, on the **Parameters** FastTab, in the **Report level** field, select **5 - statistical response to shipment and tax declaration**, and review the report.

    :::image type="content" source="../media/intrastat_fr_3.png" alt-text="Screenshot of the Intrastat Intracom report on dispatches.":::

1. Review the generated Excel report.

    :::image type="content" source="../media/intrastat_fr_4.png" alt-text="Screenshot of the Intrastat report on dispatches.":::

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
