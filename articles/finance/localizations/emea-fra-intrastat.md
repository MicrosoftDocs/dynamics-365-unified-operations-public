---
# required metadata

title: French Intrastat
description: This topic contains information about Intrastat declaration in France.
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

The following table shows the fields that are included in the French Intrastat declaration in SAISUNIC 330 format. The table also indicates the report level of the field. The field can be **4** (simplified), **1** (full), or both.

| **Field**                   | **Report level** |
|-----------------------------|------------------|
| Period Of Reference         | 4, 1              | 
| Number Of Declaration       | 4, 1              |
| Line Number                 | 4, 1              |
| Country ISO Code (FR)       | 4, 1              | 
| Complementary Code          | 4, 1              | 
| Siren Number                | 4, 1              | 
| VAT Code Of Customer        | 4, 1              | 
| Direction Code              | 4, 1              |
| Transaction Type            | 4, 1              | 
| Obligation Level            | 4, 1              |
| Commodity Code              | 1                | 
| National NGP                | 1                | 
| County (Department)         | 1                |
| Nature Of Transaction       | 1                | 
| Country Of Origination      | 1                | 
| Country Of Origin - Imports | 1                | 
| Final Destination - Exports | 1                | 
| Invoice Value               | 4, 1              | 
| Statistical Value           | 1                |
| Net Weight                  | 1                | 
| Additional Units            | 1                |
| Transport Code              | 1                | 

The following table shows the fields that are included in the French Intrastat declaration in INTRACOM format.
The table also indicates the report level of the field. The field can be **4** (simplified), **1** (full), or both.

| **Field**                   | **Report level**   | 
|-----------------------------|--------------------|
| Code                        | 4, 1               | 
| Number Of Declaration       | 4, 1               |
| Number Of Line              | 4, 1               | 
| Siren                       | 4, 1               |
| County (Department)         | 1                  |          
| Transport Code              | 1                  |          
| Country Of Origin           | 1                  |            
| Nature Of Transaction       | 1                  |             
| Invoice Value               | 4, 1               |             
| Modes Of Delivery           | 1                  |           
| Transaction Type            | 4, 1               |            
| Obligation Level            | 4, 1               |           
| Commodity Code              | 1                  |            
| National NGP                | 1                  |            
| Net Weight                  | 1                  |            
| Statistical Value           | 1                  |            
| Additional Units            | 1                  |            
| Country Of Origin - Imports | 1                  |            
| Final Destination - Exports | 1                  |            
| VAT Code Of Customer        | 4, 1               |            
| Complementary Code          | 4, 1               |           
| Period Of Reference         | 4, 1               |         

### Set up Intrastat

1.  In [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/Logon/Index), in the Shared asset library, download the latest versions of the following Electronic reporting (ER) configurations for the Intrastat declaration:

    - Intrastat model
    - Intrastat report
    - Intrastat INTRACOM (FR)
    - Intrastat SAISUNIC (FR)

    For more information, see [Download Electronic reporting configurations from Lifecycle Services](../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

2.  In Dynamics 365 Finance, go to **Tax** > **Setup** >  **Foreign trade** > **Foreign trade parameters**, and follow these steps:

    1. On the **Intrastat** tab, on the **Electronic reporting** FastTab, in the **File format mapping** field, select **Intrastat INTRACOM (FR)** or **Intrastat SAISUNIC (FR)**.
    2. In the **Report format mapping** field, select **Intrastat report**.
    3. On the **Commodity code hierarchy** FastTab, in the **Category hierarchy** field, select **Intrastat**.
    4. On the **General** FastTab, in the **Transaction code** field, select the code that is used for transfers of goods.
    5. In the **Credit note** field, select the code that is used for returns of goods.
    6. In the **Obligation level for export** field, enter the level of detail for the export report. The level that you select affects the lines that are shown on the report. For more information, see the tables at the beginning of this topic.

3. Go to **Organization administration** > **Organizations** > **Legal entities**, select your company, and then follow these steps:

    1. On the **Registration numbers** FastTab, in the **NAF code** field, enter your NAF code. For more information, see [FR-00003 NAF codes and Siret numbers](tasks/fr-00003-naf-codes-siret-numbers.md).
    2. On the **Foreign trade and logistics** FastTab, in the **Intrastat** section, set the **VAT exempt number export** and **VAT exempt number import** fields.
    3. On the **Tax registration** FastTab, in the **Tax registration number** field, enter your company's tax registration number.

4. To specify NAF codes and tax-exempt numbers for customers, go to **Accounts receivable** > **Customers** > **All customers**, and follow these steps:

    1. Select a customer.
    2. On the **Invoice and delivery** FastTab, in the **Sales tax** section, in the **Tax exempt number** field, enter the customer's tax-exempt number.
    3. On the **Sales demographics** FastTab, in the **French Siret** field, enter the company's Siret number.
    4. In the **NAF code** field, enter the company's NAF code.
    5. Repeat these steps for other customers.

5. To specify NAF codes and tax-exempt numbers for vendors, go to **Accounts payable** > **Vendors** > **All vendors**, and follow these steps:

    1. Select a vendor.
    2. On the **Invoice and delivery** FastTab, in the **Sales tax** section, in the **Tax exempt number** field, enter the vendor's tax-exempt number.
    3. On the **Purchasing demographics** FastTab, in the **French Siret** field, enter the company's Siret number.
    4. In the **NAF code** field, enter the company's NAF code.
    5. Repeat these steps for other vendors.

6. Go to **Tax** > **Setup** > **Foreign trade** > **Compression of Intrastat**, and select the fields that should be compared when Intrastat information is summarized. For French Intrastat, select **Statistics procedure**, **State of origin**, **Country/region of origin**, **Delivery terms**, **Transport**, **Correction**, **Country/region**, **County of origin/destination**, **Direction**, **Country/region of sender**, **State of sender**, **State**, **Transaction code**, and **Commodity**.

7. Go to **Warehouse management** > **Setup** > **Warehouse** > **Warehouses**, select a warehouse, and then follow these steps:

    1. On the **Addresses** FastTab, select **Add** or **Edit**.
    2. In the dialog box, in the **City** field, select the warehouse's city. The city's state will be used as a county for your DEB report.

### NGP codes

On the DEB report, the codification of products consists of the following elements:

  - The eight-digit CN8 code that represents the tariff and statistical nomenclature of the EU.
  - If applicable, the one-digit Nomenclature Générale des Produits (NGP) national item code.

In 2021, the NGP applies to only three types of products:

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

## Intrastat journal

Go to **Tax** > **Declarations** > **Foreign** **trade** > **Intrastat** to manage your transactions that are applicable to foreign trade with EU countries. For more information, see [Intrastat overview](emea-intrastat.md).

The **NGP** column is specific to France. It shows the NGP code for the product. If the NGP isn't applicable to a product, **0** (zero) is shown. You can adjust the NGP code. Select the transaction, and then, on the **General** tab, in the **Codes** section, in the **NGP** field, select the required NGP code.

### Intrastat transfer

On the **Intrastat** page, on the Action Pane, you can select **Transfer** to automatically transfer the information about intracommunity trade from your sales orders, free text invoices, purchase orders, vendor invoices, vendor product receipts, project invoices, and transfer orders. Only documents that have an EU country as the country or region of destination (for dispatches) or consignment (for arrivals) will be transferred.

Because the DEB report is a combination of the EU Sales List and the Intrastat report, it also includes *triangular* transactions, where a direct delivery is made from one EU country (party A) to another EU country (party C), and a French legal entity (party B) is in the middle of the triangular deal.

### Generate a DEB (Intrastat) report

1. Go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
2. On the Action Pane, select **Output** > **Report**.
3. In the **Intrastat Report** dialog box, set the following fields.

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

## Example

The following example shows how to set up French Intrastat and create the DEB report. It uses the **DEMF** legal entity.

1. In [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/Logon/Index), in the Shared asset library, download the latest versions of the following ER configurations for the Intrastat declaration format:

    - Intrastat model
    - Intrastat report
    - Intrastat INTRACOM (FR)

2. In Finance, set up a transaction code:

    1. Go to **Tax** > **Setup** > **Foreign trade** > **Transaction codes**.
    2. On the Action Pane, select **New**.
    3. In the **Transaction code** field, enter **11**.
    4. In the **Name** field, enter **Purchase or Sales**.
    5. On the Action Pane, select **Save**.

3.  Set up a product hierarchy:

    1. Go to **Product information management** > **Setup** > **Categories and attributes** > **Category hierarchies**.
    2. In the grid, select **Intrastat**. Then, on the Action Pane, on the **Category hierarchy** tab, in the **Maintain** group, select **Edit**.
    3. On the Action Pane, select **New category node**.
    4. In the **Name** field, enter **Autres Libournais**.
    5. In the **Code** field, enter **2204 21 42**
    6. On the Action Pane, select **Save**.

4. Go to **Tax** > **Setup** > **Foreign trade** > **Foreign trade parameters**, and follow these steps:

    1. On the **Intrastat** tab, on the **General** FastTab, in the **Transaction code** field, select **11**.
    2. On the **Electronic reporting** FastTab, in the **File format mapping** field, select **Intrastat INTRACOM (FR)**.
    3. In the **Report format mapping** field, select **Intrastat report**.
    4. On the **Commodity code hierarchy** FastTab, in the **Category hierarchy** field, select **Intrastat**.

5. Set up an NGP code:

    1. Go to **Tax** > **Setup** > **Foreign trade** > **NGP codes**.
    2. On the Action Pane, select **New**.
    3. In the **NGP** field, enter **8**.
    4. In the **Description name** field enter **NGP 8**.
    5. On the Action Pane, select **Save**.

6. Assign the NGP code to a product:

    1. Go to **Product information management** > **Products** > **Released products**.
    2. In the grid, select **0001**.
    3. On the **Foreign trade** FastTab, in the **NGP** field, select **8**.
    4. In the **Commodity** field, select **2204 21 42**.
    5. On the Action Pane, select **Save**.

7. Create a sales order that includes the new product:

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

8.  Create the DEB report:

    1. Go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**:
    2. On the Action Pane. select **Transfer**.
    3. In the **Intrastat (Transfer)** dialog box, in the **Parameters** section, set the **Customer invoice** option to **Yes**. Then select **OK**.
    4. Sort transactions by the **Date** field. The top transaction is the result transaction. The **NGP** field is automatically set.
    5. On the Action Pane, select **Output** &gt; **Report**.
    6. In the **Intrastat Report** dialog box, on the **Parameters** FastTab, in the **Date** section, select the month of the sales order that you created.
    7. In the **Export options** section, set the **Generate file** option to **Yes**.
    8. In the **File name** field, enter the required name.
    9. Select **OK**, and review the report.

