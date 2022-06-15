---
# required metadata

title: French Intrastat
description: This article contains information about Intrastat declaration in France.
author: anasyash
ms.date: 07/9/2021
ms.topic: article
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: anasyash
ms.search.validFrom: 
---


# French Intrastat

[!include[banner](../includes/banner.md)]

Companies in France that are registered for value-added tax (VAT), and that trade with other European Union (EU) countries, must declare the exchange of goods and services to and from France. The Declaration d'exchanges de biens (Declaration of Trade in Goods, or DEB) is a combination of the EU Sales List and the Intrastat report. You must submit this report monthly for all intracommunity sales of goods.

You can generate the DEB report in either of two electronic text file formats: SAISUNIC 330 or INTRACOM format.

The following table shows the fields that are included in the French Intrastat declaration in SAISUNIC 330 format. The table also indicates the report level of the field. The field can be **4** (tax declaration), **1** (statistical response), or **5** (statistical response to shipment and tax declaration, joint filling).

| **Field**                   | **Report level** |
|-----------------------------|------------------|
| Period Of Reference         | 4, 1, 5              | 
| Number Of Declaration       | 4, 1, 5              |
| Line Number                 | 4, 1, 5              |
| Country ISO Code (FR)       | 4, 1, 5              | 
| Complementary Code          | 4, 1, 5              | 
| Siren Number                | 4, 1, 5              | 
| VAT Code Of Customer        | 4, 1, 5              | 
| Direction Code              | 4, 1, 5              |
| Transaction Type            | 4, 1, 5              | 
| Obligation Level            | 4, 1, 5              |
| Commodity Code              | 1, 5                | 
| National NGP                | 1, 5                | 
| County (Department)         | 1, 5                |
| Nature Of Transaction       | 1, 5                | 
| Country Of Origination      | 1, 5                | 
| Country Of Origin - Imports | 1, 5                | 
| Final Destination - Exports | 1, 5                | 
| Invoice Value               | 4, 1, 5              | 
| Statistical Value           | 1, 5                |
| Net Weight                  | 1, 5                | 
| Additional Units            | 1, 5                |
| Transport Code              | 1, 5                | 

The following table shows the fields that are included in the French Intrastat declaration in INTRACOM format.
The table also indicates the report level of the field. The field can be **4** (tax declaration), **1** (statistical response), or **5** (statistical response to shipment and tax declaration, joint filling).

| **Field**                   | **Report level**   | 
|-----------------------------|--------------------|
| Direction code                        | 4, 1, 5               | 
| Number Of Declaration       | 4, 1, 5               |
| Number Of Line              | 4, 1, 5               | 
| Siren                       | 4, 1, 5               |
| County (Department)         | 1, 5                  |          
| Transport Code              | 1, 5                  |          
| Country Of Origin           | 1, 5                  |            
| Nature Of Transaction       | 1, 5                  |             
| Invoice Value               | 4, 1, 5               |             
| Modes Of Delivery           | 1, 5                  |           
| Transaction Type            | 4, 1, 5               |            
| Obligation Level            | 4, 1, 5               |           
| Commodity Code              | 1, 5                  |            
| National NGP                | 1, 5                  |            
| Net Weight                  | 1, 5                  |            
| Statistical Value           | 1, 5                  |            
| Additional Units            | 1, 5                  |            
| Country Of Origin - Imports | 1, 5                  |            
| Final Destination - Exports | 1, 5                  |            
| VAT Code Of Customer        | 4, 1, 5               |            
| Complementary Code          | 4, 1, 5               |           
| Period Of Reference         | 4, 1, 5               |         


## Set up Intrastat

1.  In [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/Logon/Index), in the Shared asset library, download the latest versions of the following Electronic reporting (ER) configurations for the Intrastat declaration:

    - Intrastat model
    - Intrastat report
    - Intrastat INTRACOM (FR)
    - Intrastat SAISUNIC (FR)

    For more information, see [Download Electronic reporting configurations from Lifecycle Services](../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

### Set up VAT IDs

#### Set up VAT codes for your company

1. Go to **Tax** > **Setup** > **Sales tax** > **Tax exempt numbers**.
2. On the Action Pane, select **New**.
3. In the **Country/region** field, select **FRA**.
4. In the **Tax exempt number** field, enter your company's VAT number key.
5. Go to **Organization administration** > **Organizations** > **Legal entities** and select your company.
6. On the **Foreign trade and logistics** FastTab, in the **Intrastat** section, set the **VAT exempt number export** and **VAT exempt number import** fields with the code created on step 4.
7. On the **Tax registration** FastTab, in the **Tax registration number** field, enter your company's tax registration number.

#### Set up the VAT IDs for trading partners

##### Create a registration type for the company code

You must create VAT ID registration types for all the countries or regions that your company does business with.

1. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration types**.
2. On the Action Pane, select **New** to create a registration type for the VAT ID.
3. In the **Enter registration type details** dialog box, in the **Name** field, enter a name for the new registration type. For example, enter **VAT ID**.
4. In the **Country/region** field, select the country or region of the trading partner.
5. Select **Create**.

##### Match the registration type with a registration category

1. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration categories**.
2. On the Action Pane, select **New** to create a link between a registration type and a registration category.
3. For the registration type for the VAT ID, select the **VAT ID** registration category.
4. Repeat steps 2 and 3 for the other registration types that you created for the countries or regions that your company does business with.

##### Set up the VAT number of a trading partner

1. Go to **Accounts receivable** > **Customers** > **All customers.**
2. In the grid, select a customer.
3. On the Action Pane, on the **Customer** tab, in the **Registration** group, select **Registration IDs**.
4. On the **Registration ID** FastTab, select **Add** to create a registration ID.
5. In the **Registration type** field, select the registration type that you created for the company code earlier in this article.
6. In the **Registration number** field, enter the company's VAT number.
7. On the Action Pane, select **Save**. Then close the page.

For more information, see [Registration IDs](emea-registration-ids.md).

### Set up foreign trade parameters

In Dynamics 365 Finance, go to **Tax** > **Setup** >  **Foreign trade** > **Foreign trade parameters**, and follow these steps:

1. On the **Intrastat** tab, on the **Electronic reporting** FastTab, in the **File format mapping** field, select **Intrastat INTRACOM (FR)** or **Intrastat SAISUNIC (FR)**.
2. In the **Report format mapping** field, select **Intrastat report**.
3. On the **Commodity code hierarchy** FastTab, in the **Category hierarchy** field, select **Intrastat**.
4. On the **General** FastTab, in the **Transaction code** field, select the code that is used for transfers of goods.
5. In the **Credit note** field, select the code that is used for returns of goods.
6. In the **Worker** field, select the name of the contact person.
7. On the **Contact** tab, add information about contact person.

    1. In the **Telephone** field, enter the telephone number of the contact person.
    2. In the **Fax** field, enter the fax number of the contact person.

8. On the **Country/region properties** tab, in the **Country/region** field, list all the countries or regions that your company does business with. For each country that is part of the EU, select **EU** in the **Country/region type** field, so that the country appears on your Intrastat report. For France, select **Domestic** in the **Country/region type** field.


### Set up compression of Intrastat

Go to **Tax** > **Setup** > **Foreign trade** > **Compression of Intrastat**, and select the fields that should be compared when Intrastat information is summarized. For French Intrastat, select the following fields:
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
2. In the grid, select a product.
3. On the **Foreign trade** FastTab, in the **Intrastat** section, in the **Commodity** field, select the commodity code. The name of the commodity will be printed in the **Description of commodities** field on the Intrastat report.
3. In the **Origin** section, in the **Country/region** field, select the product's country or region of origin.
4. On the **Manage inventory** FastTab, in the **Net weight** field, enter the product's weight in kilograms.    

### NGP codes

On the DEB report, the codification of products consists of the following elements:

  - The eight-digit CN8 code that represents the tariff and statistical nomenclature of the EU.
  - If applicable, the one-digit Nomenclature Générale des Produits (NGP) national item code.

In 2022, the NGP applies to only three types of products:

  - Some products from cows, sheep, and goats
  - Military equipment
  - French wines

 You must set up the NGP codes and assign them to related products. The **NGP** field is then automatically set on the **Intrastat journal** page.

#### Set up an NGP code

1. Go to **Tax** > **Setup** > **Foreign trade** > **NGP codes**.
2. On the Action Pane, select **New** to create an NGP code.
3. In the **NGP** field, enter a single-digit code.
4. In the **Description** field, enter a description for the code.

#### Assign an NGP code to a product

1. Go to **Product information management** > **Products** > **Released products**.
2. In the grid, select a product.
3. On the **Foreign trade** FastTab, in the **Intrastat** section, in the **NGP** field, select the appropriate NGP code.

### Set up warehouse parameters for the Intrastat declaration

Go to **Warehouse management** > **Setup** > **Warehouse** > **Warehouses**, select a warehouse, and then follow these steps:
1. On the **Addresses** FastTab, select **Add** or **Edit**.
2. In the dialog box, in the **City** field, select the warehouse's city. The city's state will be used as a county for your DEB report.

### Set up the transport method
Go to **Tax** > **Setup** > **Foreign trade** > **Transport method**.
On the Action Pane, select New.
In the **Transport** field, enter a unique code. Companies in France use one-digit transport codes.

### Intrastat journal

Go to **Tax** > **Declarations** > **Foreign** **trade** > **Intrastat** to manage your transactions that are applicable to foreign trade with EU countries. For more information, see [Intrastat overview](emea-intrastat.md).

The **NGP** column is specific to France. It shows the NGP code for the product. If the NGP isn't applicable to a product, **0** (zero) is shown. You can adjust the NGP code. Select the transaction, and then, on the **General** tab, in the **Codes** section, in the **NGP** field, select the required NGP code.

#### Intrastat transfer

On the **Intrastat** page, on the Action Pane, you can select **Transfer** to automatically transfer the information about intracommunity trade from your sales orders, free text invoices, purchase orders, vendor invoices, vendor product receipts, project invoices, and transfer orders. Only documents that have an EU country as the country or region of destination (for dispatches) or consignment (for arrivals) will be transferred.

Because the DEB report is a combination of the EU Sales List and the Intrastat report, it also includes *triangular* transactions, where a direct delivery is made from one EU country (party A) to another EU country (party C), and a French legal entity (party B) is in the middle of the triangular deal.

#### Generate a DEB (Intrastat) report

1. Go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
2. On the Action Pane, select **Output** > **Report**.
3. In the **Intrastat Report** dialog box, set the following fields:

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

4. Select OK to close the **Intrastat Report** dialog box.
5. In the **Electronic report parameters** dialog box, on the **Parameters** FastTab, in the **Report level** field, select the report level. The report level can be **1 - statistical response**, **4 - tax declaration**, or **5 - statistical response to shipment and tax declaration**.

## Example

The following example shows how to set up French Intrastat and create the DEB report. It uses the **DEMF** legal entity.

### Preliminary setup

1. In [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/Logon/Index), in the Shared asset library, download the latest versions of the following ER configurations for the Intrastat declaration format:

    - Intrastat model
    - Intrastat report
    - Intrastat INTRACOM (FR)

2.  Set up a product hierarchy:

    1. Go to **Product information management** > **Setup** > **Categories and attributes** > **Category hierarchies**.
    2. In the grid, select **Intrastat**. Then, on the Action Pane, on the **Category hierarchy** tab, in the **Maintain** group, select **Edit**.
    3. On the Action Pane, select **New category node**.
    4. In the **Name** field, enter **Autres Libournais**.
    5. In the **Code** field, enter **2204 21 42**
    6. On the Action Pane, select **Save**.

### Set up VAT IDs

#### Set up VAT codes for your company
1. Go to **Tax** > **Setup** > **Sales tax** > **Tax exempt numbers**.
2. On the Action Pane, select **New**.
3. In the **Country/region** field, select **FRA**.
4. In the **Tax exempt number** field, enter **MS123456**.
5. Go to **Organization administration** > **Organizations** > **Legal entities** and select **DEMF**.
6. On the **Foreign trade and logistics** FastTab, in the **Intrastat** section, set the **VAT exempt number export** and **VAT exempt number import** fields with the code created on step 4.
7. On the **Tax registration** FastTab, in the **Tax registration number** field, enter **123456789**.

#### Set up the VAT IDs for trading partners

##### Create a registration type for the company code

1. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration types**.
2. On the Action Pane, select **New** to create a registration type for the VAT ID.
3. In the **Enter registration type details** dialog box, in the **Name** field, enter **VAT ID**.
4. In the **Country/region** field, select **DEU**.
5. Select **Create**.

#### Match the registration type with a registration category

1. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration categories**.
2. On the Action Pane, select **New** to create a link between the registration type and the registration category.
3. For the **VAT ID** registration type of the **DEU** country, select the **VAT ID** registration category.

#### Set up the customer's VAT registration number

1. Go to **Accounts receivable** > **Customers** > **All customers**.
2. In the grid, select **DE-016**.
3. On the Action Pane, on the **Customer** tab, in the **Registration** group, select **Registration IDs**.
4. On the **Registration ID** FastTab, select **Add** to create a registration ID.
5. In the **Registration type** field, select **VAT ID**.
6. In the **Registration number** field, enter **DE9012**.
7. On the Action Pane, select **Save**. Then close the page.
8. On the **Invoice and delivery** FastTab, in the **Sales tax** section, in the **Tax exempt number** field, select **DE9012123456789**.

### Set up foreign trade parameters

1. Go to **Tax** > **Setup** > **Foreign trade** > **Foreign trade parameters**.
2. On the **Intrastat** tab, on the **General** FastTab, in the **Transaction code** field, select **11**.
3. On the **Electronic reporting** FastTab, in the **File format mapping** field, select **Intrastat INTRACOM (FR)**.
4. In the **Report format mapping** field, select **Intrastat report**.
5. On the **Commodity code hierarchy** FastTab, in the **Category hierarchy** field, select **Intrastat**.
6. In the **Worker** field, select **Jodi Christiansen**.
7. On the **Contact** tab, in the **Telephone** field, enter **425-555-5068**.
8. In the **Fax** field, enter **425-555-5106**.

### Create NGP code

1. Go to **Tax** > **Setup** > **Foreign trade** > **NGP codes**.
2. On the Action Pane, select **New**.
3. In the **NGP** field, enter **8**.
4. In the **Description name** field enter **NGP 8**.
5. On the Action Pane, select **Save**.

### Set up product information

1. Go to **Product information management** > **Products** > **Released products**.
2. In the grid, select **D0001**.
3. On the **Foreign trade** FastTab, in the **Intrastat** section, in the **NGP** field, select **8**.
4. In the **Commodity** field, select **2204 21 42**.
5. In the **Origin** section, in the **Country/region** field, select **FRA**.
6. On the **Manage inventory** FastTab, in the **Weight measurements** section, in the **Net weight** field, enter **2**.
7. On the Action Pane, select **Save** and close the form.
8. In the grid, select **D0003**.
9. On the **Foreign trade** FastTab, in the **Intrastat** section, in the **Commodity** field, select **100 200 30**.
10. In the **Origin** section, in the **Country/region** field, select **DEU**.
11.On the **Manage inventory** FastTab, in the **Weight measurements** section, in the **Net weight** field, enter **5**.
12.On the Action Pane, select **Save**.

### Set up Regime codes

1. Go to **Tax** > **Setup** > **Foreign trade** > **Statistics procedure**
2. On the Action Pane, select **New**.
3. In the **Statistics procedure** field, enter the regime code.
4. In the **Text 1** field, enter the regime code description.

### Change the site address

1. Go to **Warehouse management** > **Setup** > **Warehouse** > **Sites**.
2. In the grid, select **1**.
3. On the **Addresses** FastTab, select **Edit**.
4. In the **Edit address** dialog box, in the **Country/region** field, select **FRA**.
5. Select **OK**.
6. Go to **Warehouse management** > **Setup** > **Warehouse** > **Warehouses**, select a warehouse.
7. On the **Addresses** FastTab, select **Add**.
8. In the **New address** dialog box, in the **City** field, select **Bordeaux**.

### Create a sales order with an EU customer that includes the new product

1. Go to **Accounts receivable** > **Orders** > **All sales orders**.
2. On the Action Pane, select **New**.
3. In the **Create** **sales** **order** dialog box, in the **Customer** section, in the **Customer** **account** field, select **100001**.
4. In the **Address** section, in the **Delivery address** field, select the plus sign (**+**) to create an address.
5. In the **New address** dialog box, in the **Name of description** field, enter **Germany**.
6. In the **Country/region** field, select **DEU**.
7. Select **OK**.
8. In the **Create sales order** dialog box, select **OK**.
9. On the **Sales** **order lines** FastTab, in the **Item number** field, select **0001**.
10. On the Action Pane, select **Save**.
11. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
12. In the **Posting invoice** dialog box, on the **Parameters** FastTab, in the **Parameter** section, in the **Quantity** field, select **All**. Then select **OK** to post the invoice.

### Transfer the transaction to the Intrastat journal and review the result

1. Go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**:
2. On the Action Pane. select **Transfer**.
3. In the **Intrastat (Transfer)** dialog box, in the **Parameters** section, set the **Customer invoice** option to **Yes**. Then select **OK**.
4. Sort transactions by the **Date** field. The top transaction is the result transaction. The **NGP** field is automatically set.
5. On the Action Pane, select **Output** &gt; **Report**.
6. In the **Intrastat Report** dialog box, on the **Parameters** FastTab, in the **Date** section, select the month of the sales order that you created.
7. In the **Export options** section, set the **Generate file** option to **Yes**.
8. In the **File name** field, enter the required name.
9. Select OK to close the **Intrastat Report** dialog box.
10. In the **Electronic report parameters** dialog box, on the **Parameters** FastTab, in the **Report level** field, select **5 - statistical response to shipment and tax declaration**, and review the report.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
