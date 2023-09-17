---
title: Czech Intrastat
description: This article contains information about the Czech Intrastat report.
author: AdamTrukawka
ms.date: 01/18/2022
ms.topic: article
audience: 
ms.reviewer: kfend
ms.search.region: Global
ms.author: atrukawk
ms.search.validFrom: 
---

# Czech Intrastat

[!include [banner](../includes/banner.md)]

The **Intrastat** page is used to generate and report information about trade among European Union (EU) countries/regions. The Czech Intrastat declaration contains information about the trade of goods for reporting.

The following fields are included in the Czech Intrastat declaration. All the fields except **VAT number of trading partner** are included on both arrivals and dispatches. The **VAT number of trading partner** field is included only on dispatches.

| Field name | Description |
|-------------------------|-------------------------|
| Declaration month | The reference month of the declaration. |
| Declaration year | The reference year of the declaration. |
| VAT registration number | Value-added tax (VAT) ID of the company that is providing the statistical declaration. |
| The report direction | For arrivals, "1" is printed.</br>For dispatches, "2" is printed. |
| VAT number of trading partner | The customer's foreign VAT number in an EU member state. |
| Country of consignment (arrivals) / Country of destination (dispatches) | The International Organization for Standardization (ISO) code of the country or region of the counterparty. |
| Country of origin | The ISO code of the country or region where the goods were produced. |
| Nature of transaction | The transaction code. |
| Mode of transport | The code for the mode of transport. Companies in Czech Republic use one-digit transport codes. |
| Delivery terms | The Intrastat code for the delivery terms. Companies in Czech Republic use one-digit codes. |
| Code of movement | The two-digit code for the movement of special goods. The default value is specified in the **Special movement code** field on the **General** tab of the **Foreign trade parameters** page. You can overwrite the default value when you create an order. |
| Commodity code | The commodity code according to the Combined Nomenclature (CN) classification. This code is set on the product page. |
| Statistical sign | For some commodities, you must report the supplementary statistical sign. This code is set on the product page. |
| Description of goods | The trade name of the commodity. |
| Net mass | The net mass of the goods item in kilograms. The unit itself ("kg") isn't printed. |
| Quantity of supplementary goods | For some commodities, you must report the supplementary unit. The unit itself (for example, "pairs" or "dozens") isn't reported. |
| Invoice amount | The invoice value. |


## Set up Intrastat

From the Global repository, import the latest version of the following Electronic reporting (ER) configurations:

- Intrastat model
- Intrastat report
- Intrastat (CZ)

For more information, see [Download ER configurations from the Global repository of Configuration service](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

### Set up VAT IDs

#### Set up the VAT ID of your company

1. In Microsoft Dynamics 365 Finance, go to **Organization administration** > **Organizations** > **Legal entities**.
2. In the grid, select your company.
3. On the **Tax registration** FastTab, in the **Tax registration number** field, enter the VAT ID of your company.

#### Set up the VAT number of a trading partner

##### Create a registration type for the company code

You must create VAT ID registration types for all the countries or regions that your company does business with.

1.  Go to **Organization administration** > **Global address book** > **Registration types** > **Registration types**.
2.  On the Action Pane, select **New** to create a registration type for the VAT ID.
3.  In the **Enter registration type details** dialog box, in the **Name** field, enter a name for the new registration type. For example, enter **VAT ID**.
4.  In the **Country/region** field, select the country or region that your company does business with.
5.  Select **Create**.

##### Match the registration type with a registration category

1. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration categories**.
2. On the Action Pane, select **New** to create a link between a registration type and a registration category.
3. For the registration type for the VAT ID, select the **VAT ID** registration category.
4. Repeat steps 2 through 3 for the other registration types that you created for the countries or regions that your company does business with.

##### Create a customer's VAT registration number

1. Go to **Accounts receivable** > **Customers** > **All customers**.
2. In the grid, select a customer.
3. On the Action Pane, on the **Customer** tab, in the **Registration** group, select **Registration IDs**.
4. On the **Registration ID** FastTab, select **Add** to create a registration ID.
5. In the **Registration type** field, select the registration type that you previously created for the company code.
6. In the **Registration number** field, enter the company's VAT number.
7. On the Action Pane, select **Save**. Then close the page.

For more information, see [Registration IDs](emea-registration-ids.md).

Alternatively, you can create a customer's VAT registration number by using the **Tax exempt number** page.

1. Go to **Tax** > **Setup** > **Sales tax** > **Tax exempt numbers**.
2. For each tax-exempt number, create a record that includes the following information:

    - In the **Country/region** field, select the tax registration of the counterparty.
    - In the **Tax exempt number** field, enter the tax-exempt number of the counterparty.
    - In the **Company name** field, enter the name of the counterparty.

3. Go to **Accounts receivable** > **Customers** > **All customers**.
4. In the grid, select a customer.
5. On the **Invoice and delivery** FastTab, in the **Sales tax** section, in the **Tax exempt number** field, select the registration number that you just created.

## Set up the statistical signs for commodities

1. Go to **Tax** > **Setup** > **Foreign trade** > **Statistics procedure**.
2. On the Action Pane, select **New**.
3. In the **Commodity** field, select the commodity code that requires a statistical sign.
4. In the **Statistics procedure** field, enter the required statistical sign.
5. Repeat steps 2 through 4 for other commodity codes.

## Set up product parameters for the Intrastat declaration

1. Go to **Product information management** > **Products** > **Released products**.
2. In the grid, select a product.
3. On the **Foreign trade** FastTab, in the **Intrastat** section, in the **Commodity** field, select the commodity code. The name of the commodity will be printed in the **Description of commodities** field in the Intrastat declaration.
4.  In the **Statistics procedure** field, select the statistical sign if it's required. The values that are available for selection depend on the commodity code that you selected.
5. In the **Origin** section, in the **Country/region** field, select the product's country or region of origin.
6. On the **Manage inventory** FastTab, in the **Net weight** field, enter the product's weight in kilograms.

## Set up the transport method and delivery terms

1. Set up transport codes.

    1. Go to **Tax** > **Setup** > **Foreign trade** > **Transport method**.
    2. On the Action Pane, select **New**.
    3. In the **Transport** field, enter a unique code. Czech companies use one-digit transport codes.

2. Set up mode of delivery Intrastat codes.

    1. Go to **Procurement and sourcing** > **Setup** > **Distribution** > **Terms of delivery**.
    2. In the grid, select a set of delivery terms.
    3. On the **General** FastTab, in the **Intrastat code** field, enter the unique code.

## Set up the special movements codes

1. Go to **Tax** > **Setup** > **Foreign trade** > **Special movements**.
2. On the Action Pane, select **New** to create the special movements code.
3. In the **Special movements** field, enter the unique code.
4. In the **Description** field, enter a description of the code.

## Set up foreign trade parameters

1. Go to **Tax** > **Setup** > **Foreign trade parameters**.
2. On the **Intrastat** tab, on the **Electronic reporting** FastTab, in the **File format mapping** field, select **Intrastat (CZ)**.
3. In the **Report format mapping** field, select **Intrastat report**.
4. On the **Commodity code hierarchy** FastTab, in the **Category hierarchy** field, select **Intrastat**.
5. In the **Transaction code** field, select the transaction code for property transfers.
6. In the **Credit note** field, select the transaction code for the return of goods.
7. In the **Special movement code** field, set the default value for purchase orders and sales orders. You can overwrite the default value when you create an order.
8. On the **Country/region properties** tab, in the **Country/region** field, list all the countries or regions that your company does business with. For each country that is part of the EU, select **EU** in the **Country/region type** field, so that the country appears on your Intrastat report. For Czech Republic, select **Domestic** in the **Country/region type** field.

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

On the **Intrastat** page, on the Action Pane, you can select **Transfer** to automatically transfer the information about intracommunity trade from your sales orders, free text invoices, purchase orders, vendor invoices, vendor product receipts, project invoices, and transfer orders. Only documents that have an EU country as the country or region of destination or consignment will be transferred.

You can also manually enter transactions by selecting **New** on the Action Pane.

### Generate an Intrastat report

1. Go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
2. On the Action Pane, select **Output** &gt; **Report**.
3. In the **Intrastat Report** dialog box, enter the start date for the report.
4. Set the **Generate file** option to **Yes** to generate a .txt file, and then enter the name of the .txt file for the Intrastat report.
5. Set the **Generate report** option to **Yes** to generate an .xlsx file, and then enter a name for the file.
6. In the **Direction** field, select **Arrivals** if the report is about intracommunity arrivals, **Dispatches** if the report is about intracommunity dispatches, or **Both** if the report combines information about intracommunity arrivals and dispatches.
7. Select **OK**, and review the generated reports.

## Example

This example shows how to post arrivals and dispatches for Intrastat by using the **DEMF** legal entity.

### Preliminary setup

1. Go to **Organization administration** > **Organization** > **Legal entities**, and select the **DEMF** legal entity.
2. On the **Addresses** FastTab, select **Edit**, and then, in the **Country/region** field, select **CZE (Czech Republic)**.
3. Import the latest version of the following ER configurations:

    - Intrastat model
    - Intrastat report
    - Intrastat (CZ)

### Set up VAT IDs

#### Set up the VAT ID of your company

1. Go to **Organization administration** > **Organizations** > **Legal entities**.
2. In the grid, select **DEMF**.
3. On the **Tax registration** FastTab, in the **Tax registration number** field, enter **1234567890**.

#### Create registration types for company codes

1. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration types**.
2. On the Action Pane, select **New** to create a registration type for the VAT ID.
3. In the **Enter registration type details** dialog box, in the **Name** field, enter **VAT ID**.
4. In the **Country/region** field, select **DEU**.
5. In the **Restricted to** field, select **Organization**.
6. Select **Create**.

#### Match the registration type with a registration category

1. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration categories**.
2. On the Action Pane, select **New** to create a link between the registration type and the registration category.
3. For the **VAT ID** registration type, select the **VAT ID** registration category.

#### Set up the customer's VAT registration number

1. Go to **Accounts receivable** > **Customers** > **All customers**.
2. In the grid, select **DE-016**.
3. On the Action Pane, on the **Customer** tab, in the **Registration** group, select **Registration IDs**.
4. On the **Registration ID** FastTab, select **Add** to create a registration ID.
5. In the **Registration type** field, select **VATID**.
6. In the **Registration number** field, enter **DE0234**.
7. On the Action Pane, select **Save**. Then close the page.

### Set up the statistical signs for commodities

1. Go to **Tax** > **Setup** > **Foreign trade** > **Statistics procedure**.
2. On the Action Pane, select **New**.
3. In the **Commodity** field, select **100 200 30**.
4. In the **Statistics procedure** field, enter **50**.

### Set up product information

1. Go to **Product information management** > **Products** > **Released products**.
2. In the grid, select **D0001**.
3. On the **Foreign trade** FastTab, in the **Intrastat** section, in the **Commodity** field, select **100 200 30**.
4. In the **Statistics procedure** field, select **50**.
5. In the **Origin** section, in the **Country/region** field, select **CZE**.
6. On the **Manage inventory** FastTab, in the **Weight measurements** section, in the **Net weight** field, enter **2**.
7. On the Action Pane, select **Save**.
8. In the grid, select **D0003**.
9. On the **Foreign trade** FastTab, in the **Intrastat** section, in the **Commodity** field, select **100 200 30**.
10. In the **Statistics procedure** field, select **50**.
11. In the **Origin** section, in the **Country/region** field, select **DEU**.
12. On the **Manage inventory** FastTab, in the **Weight measurements** section, in the **Net weight** field, enter **5**.
13. On the Action Pane, select **Save**.

### Set up the special movements codes

1. Go to **Tax** > **Setup** > **Foreign trade** > **Special movements**.
2. On the Action Pane, select **New** to create the special movements code.
3. In the **Special movements** field, enter **ZR**.
4. In the **Description** field, enter **Staggered Consignments**.

### Set up foreign trade parameters

1. Go to **Tax** > **Setup** > **Foreign trade** > **Foreign trade parameters**.
2. On the **Intrastat** tab, on the **General** FastTab, in the **Transaction code** field, select **11**.
3. In the **Special movement code** field, select **ZR**.
4. On the **Electronic reporting** FastTab, in the **File format mapping** field, select **Intrastat (CZ)**.
5. In the **Report format mapping** field, select **Intrastat Report**.
6. On the **Commodity code hierarchy** FastTab, verify that the **Category hierarchy** field is set to **Intrastat**.
7. On the **Country/region properties** tab, select **New**.
8. In the **Party country/region** field, select **CZE**. Then, in the **Country/region type** field, select **Domestic**.
9. In the **Party country/region** field, select **DEU**. Then, in the **Country/region type** field, select **EU**.

### Change the site address

1. Go to **Warehouse management** > **Setup** > **Warehouse** > **Sites**.
2. In the grid, select **1**.
3. On the **Addresses** FastTab, select **Edit**.
4. In the **Edit address** dialog box, in the **Country/region** field, select **CZE**.
5. Select **OK**.

### Set up a transport method

1. Create a transport method.

    1. Go to **Tax** > **Setup** > **Foreign trade** > **Transport method**.
    2. On the Action Pane, select **New**.
    3. In the **Transport** field, enter **3**.
    4. In the **Description** field, enter **Road transport**.

2. Assign the new transport method to a mode of delivery. In this way, you set up the default values that are used for the transport method when the corresponding mode of delivery is selected.

    1. Go to **Procurement and sourcing** > **Setup** > **Distribution** > **Modes of delivery**.
    2. In the grid, select **10**.
    3. On the **Foreign trade** FastTab, in the **Transport** field, select **3**.

3.  Select the default mode of delivery for a customer.

    1. Go to **Accounts receivable** > **Customers** > **All customers**.
    2. In the grid, select **DE-016**.
    3. On the **Invoice and delivery** FastTab, in the **Mode of delivery** field, select **10**.

4.  Select the default mode of delivery for a vendor.

    1. Go to **Accounts payable** > **Vendors** > **All vendors**.
    2. In the grid, select **DE-001**.
    3. On the **Invoice and delivery** FastTab, in the **Mode of delivery** field, select **10**.

### Set up codes for terms of delivery

1.  Set up an Intrastat code for the terms of delivery.

    1. Go to **Procurement and sourcing** > **Setup** > **Distribution** > **Terms of delivery**.
    2. In the grid, select **CIF**.
    3. On the **General** FastTab, in the **Intrastat code** field, enter **L**.

2.  Select the default delivery terms for a customer.

    1. Go to **Accounts receivable** > **Customers** > **All customers**.
    2. In the grid, select **DE-016**.
    3. On the **Invoice and delivery** FastTab, in the **Delivery terms** field, select **CIF**.

3.  Select the default delivery terms for a vendor.

    1. Go to **Accounts payable** > **Vendors** > **All vendors**.
    2. In the grid, select **DE-001**.
    3. On the **Invoice and delivery** FastTab, in the **Delivery terms** field, select **CIF**.

### Create a sales order with an EU customer

1. Go to **Accounts receivable** > **Orders** > **All sales orders**.
2. On the Action Pane, select **New**.
3. In the **Create sales order** dialog box, on the **Customer** FastTab, in the **Customer** section, in the **Customer account** field, select **DE-016**.
4. On the **General** FastTab, in the **Storage dimensions** section, in the **Site** field, select **1**.
5. In the **Warehouse** field, select **11**.
6. On the **Address** tab, verify that the **Address** field is set to **Teichgasse 12, Kiel, 24103, DEU**, because the customer is from Germany.
7. Select **OK**.
8. On the **Header** tab, on the **Delivery** FastTab, verify that the **Delivery terms** field is set to **CIF**, and the **Mode of delivery** field is set to **10**.
9. On the **Lines** tab, on the **Sales order lines** FastTab, in the **Item number** field, select **D0001**. Then, in the **Quantity** field, enter **8**.
10. On the **Line details** FastTab, on the **Foreign trade** tab, verify that the fields are set to the following values:

    - **Transaction code:** 11
    - **Transport:** 3
    - **Commodity:** 100 200 30
    - **Country/region of origin:** CZE
    - **Special movement:** ZR

11. On the Action Pane, select **Save**.
12. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
13. In the **Posting invoice** dialog box, on the **Parameters** FastTab, in the **Parameter** section, in the **Quantity** field, select **All**.
14. Select **OK** to post the invoice.

### Transfer the transaction to the Intrastat journal and review the result

1. Go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
2. On the Action Pane, select **Transfer**.
3. In the **Intrastat (Transfer)** dialog box, in the **Parameters** section, set the **Customer invoice** option to **Yes**.
4. Select **Filter**.
5. In the **Intrastat Filter** dialog box, on the **Range** tab, select the first line, and verify that the **Field** field is set to **Date**.
6. In the **Criteria** field, select the current date.
7. Select **OK** to close the **Intrastat Filter** dialog box.
8. Select **OK** to close the **Intrastat (Transfer)** dialog box, and review the result. The line represents the sales order that you created earlier.

    ![Line that represents the sales order on the Intrastat page](media/intrastat_cz_1.png)

9. Select the transaction line, and then select the **General** tab to view more details.

    ![Sales order details on the General tab of the Intrastat page](media/intrastat_cz_2.png)

10. On the Action Pane, select **Output** > **Report**.
11. In the **Intrastat Report** dialog box, on the **Parameters** FastTab, in the **Date** section, in the **From date** field, select the first day of the current month.
12. In the **Export** **options** section, set the **Generate file** option to **Yes**. Then, in the **File name** field, enter the required name.
13. Set the **Generate report** option to **Yes**. Then, in the **Report file name** field, enter the required name.
14. In the **Direction** field, select **Dispatches**.
15. Select **OK**, and review the report in text format that is generated. The following table shows the values in the example report.

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

16. Review the report in Excel format that is generated.

    ![Intrastat report on dispatches](media/intrastat_cz_3.png)

### Create a purchase order

1. Go to **Accounts payable** > **Purchase orders** > **All purchase orders**.
2. On the Action Pane, select **New**.
3. In the **Create purchase order** dialog box, in the **Vendor account** field, select **DE-001**.
4. In the **Site** field, select **1**.
5. In the **Warehouse** field, select **11**.
6. Select **OK**.
7. On the **Header** tab, on the **Delivery** FastTab, verify that the **Mode of delivery** field is set to **10**, and the **Delivery terms** field is set to **CIF**.
8. On the **Lines** tab, on the **Purchase order lines** FastTab, in the **Item number** field, select **D0003**. Then, in the **Quantity** field, enter **6**.
9. On the **Line details** FastTab, on the **Foreign trade** tab, verify that the fields are set to the following values:

    - **Transaction code**: 11
    - **Transport**: 3
    - **Commodity**: 100 200 30
    - **Country/region of origin**: DEU
    - **Special movement**: ZR

10. On the Action Pane, on the **Purchase** tab, in the **Actions** group, select **Confirm**.
11. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
12. On the Action Pane, select **Default from**, and then, in the **Default quantity for lines** field, select **Ordered quantity**. Then select **OK**.
13. On the **Vendor Invoice header** FastTab, in the **Invoice identification** section, in the **Number** field, enter **0010**.
14. In the **Invoice dates** section, in the **Invoice date** field, select the current date. This date will be used for Intrastat transfer.
15. On the Action Pane, select **Post** to post the invoice.

### Create an Intrastat declaration for arrivals

1. Go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
2. On the Action Pane, select **Transfer**.
3. In the **Intrastat (Transfer)** dialog box, set the **Vendor invoice** option to **Yes**.
4. Select **Filter**.
5. In the **Intrastat Filter** dialog box, on the **Range** tab, select the **Vendor invoice journal** line, and verify that the **Field** field is set to **Date**.
6. In the **Criteria** field, select the current date.
7. Select **OK** to close the **Intrastat Filter** dialog box.
8. Select **OK** to transfer the transactions, and review the Intrastat journal.

    ![Line that represents the purchase order on the Intrastat page](media/intrastat_cz_4.png)

9. Review the information on the **General** tab for the purchase order.

    ![Purchase order details on the General tab of the Intrastat page](media/intrastat_cz_5.png)

10. On the Action Pane, select **Output** > **Report**.
11. In the **Intrastat Report** dialog box, on the **Parameters** FastTab, in the **Date** section, in the **From date** field, select the first day of the current month.
12. In the **Export** **options** section, set the **Generate file** option to **Yes**. Then, in the **File name** field, enter the required name.
13. Set the **Generate report** option to **Yes**. Then, in the **Report file name** field, enter the required name.
14. In the **Direction** field, select **Arrivals**.
15. Select **OK**, and review the report in XML format that is generated. The following table shows the values in the example report.

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

16. Review the report in Excel format that is generated.

    ![Intrastat report on arrivals](media/intrastat_cz_6.png)
    
[!INCLUDE[footer-include](../../includes/footer-banner.md)]
