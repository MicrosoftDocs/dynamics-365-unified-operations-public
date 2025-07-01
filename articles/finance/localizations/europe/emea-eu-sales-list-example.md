---
title: Example for generic European Union (EU) sales list
description: Learn on how to set up and transfer a European Union (EU) sales list, including outlines on setting up country/region parameters and company information.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/11/2024
ms.reviewer: johnmichalak
 
---

# Example for generic EU Sales list 

[!include [banner](../../includes/banner.md)]

This article explains how to set up and transfer a European Union (EU) sales list. The example uses the **DEMF** legal entity. It also uses Germany as a country/region of the **Domestic** country/region type, and Spain and Sweden as countries/regions of the **EU** country/region type.

## Setup

#### Set up country/region parameters

To set up country/region parameters, follow these steps.

1. In Dynamics 365 Finance, go to **Tax \> Setup \> Sales tax \> Country/region parameters**.
1. On the Action Pane, select **New**.
1. In the **Country/region** field, select **SWE**.
1. In the **Sales tax** field, enter "SE".
1. On the Action Pane, select **New**.
1. In the **Country/region** field, select **DEU**.
1. In the **Sales tax** field, enter "DE".
1. On the Action Pane, select **New**.
1. In the **Country/region** field, select **ESP**.
1. In the **Sales tax** field, enter "ES"".
1. On the Action Pane, select **Save**.

#### Set up company information

To set up company information, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration \> Organizations \> Legal entities**.
1. Select the **DEMF** legal entity.
1. In the **Name** field, enter "Contoso Entertainment System Germany".
1. On the **Addresses** FastTab, select **Edit**.
1. In the **Edit address** dialog, set the following fields.

   | **Field**           | **Value**       |
   |---------------------|-----------------|
   | Name or description | Primary address |
   | Purpose             | Business        |
   | Country/region      | DEU             |
   | ZIP/postal code     | 10115           |
   | Street              | Bahnhofstraße 5 |
   | City                | Berlin          |
   | Primary             | Yes             |

1. Select **OK**.
1. On the **Tax registration** FastTab, in the **Tax registration number** field, enter "203/118/12345".

    > [!NOTE]
    > The value of the **Tax registration number** field can be used in EU sales list report files, depending on the specific country or region.

### Set up VAT IDs

#### Create a registration type for a company code

To create a registration type for a company code, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration \> Global address book \> Registration types \> Registration types**.
1. On the Action Pane, select **New**.
1. In the **Enter registration type details** dialog, in the **Name** field, enter "VAT ID".
1. In the **Country/region** field, select **DEU**.
1. Select **Create**.
1. On the **Applicable countries/regions, uses, and validation rules** FastTab, select **Add**.
1. In the **Country/region** field, select **ESP**.
1. Select **Add**.
1. In the **Country/region** field, select **SWE**.

#### Match the registration type with a registration category

To match the registration type with a registration category, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration \> Global address book \> Registration types \> Registration categories**.
1. On the Action Pane, select **New** to create a link between a registration type and a registration category.
1. For the **VAT ID** registration type for Germany, Spain, and Sweden, select the **VAT ID** registration category.

#### Set up the VAT ID of a data provider for your company

To set up the VAT ID of a data provider for your company, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration \> Organizations \> Legal entities**.
1. Select the **DEMF** legal entity.
1. On the Action Pane, select **Registration IDs**.
1. On the **Registration ID** FastTab, select **Add**.
1. In the **Registration type** field, select **VAT ID**.
1. In the **Registration number** field, enter "DE777666555".
1. On the **General** tab, in the **General** section, in the **Effective** field, select **8/1/2021** (August 1, 2021).
1. Close the page.

    > [!NOTE]
    > Depending on the company localization, if the **VAT exempt number export** field in the **Intrastat** section of the **Foreign trade and logistics** FastTab is set (not blank), the value can be used instead of the VAT ID that you created.

#### Create a customer's VAT registration number

To create a customer's VAT registration number, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable \> Customers \> All customers**.
1. In the grid, select **DE-010**.
1. On the Action Pane, on the **Customer** tab, in the **Registration** group, select **Registration Ids**.
1. On the **Registration ID** FastTab, select **Add** to create a registration ID.
1. In the **Registration type** field, select **VAT ID**.
1. In the **Registration number** field, enter "ES1234567".
1. On the **General** tab, in the **General** section, in the **Effective** field, select **8/1/2021** (August 1, 2021).
1. On the Action Pane, select **Save**.
1. Close the page.
1. On the **Invoice and delivery** FastTab, in the **Sales tax** section, in the **Tax exempt number** field, select **ES1234567**.
1. On the **General** tab, in the **General** section, in the **Effective** field, select **8/1/2021**.
1. On the Action Pane, select **Save**.
1. Close the page.
1. In the grid, select **DE-011**.
1. Repeat steps 3 through 5.
1. In the **Registration number** field, enter "SE100200300400".
1. On the Action Pane, select **Save**.
1. Close the page.
1. On the **Invoice and delivery** FastTab, in the **Sales tax** section, in the **Tax exempt number** field, select **SE100200300400**.

### Import electronic reporting configurations

To import electronic reporting configurations, follow these steps.

1. Sign in to [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/Logon/Index).
1. Import the latest versions of the following electronic reporting (ER) configurations for the EU sales list:

    - EU Sales list model
    - EU Sales list by rows report
    - EU Sales list (DE)

### Set up foreign trade parameters

To set up foreign trade parameters, follow these steps.

1. In Dynamics 365 Finance, go to **Tax \> Setup \> Foreign trade \> Foreign trade parameters**.
1. On the **EU sales list** tab, on the **Rounding rules** FastTab, in the **Rounding rule** field, enter "0.01".
1. In the **Number of decimals** field, enter "2".
1. On the **Electronic reporting** FastTab, in the **File format mapping** field, select **EU Sales list (DE)**.
1. In the **Report format mapping** field, select **EU Sales list by rows report**.
1. On the **Country/region properties** tab, select **New**, and set the following fields:

    - In the **Country/region** field, select **DEU**.
    - In the **Country/region type** field, select **Domestic**.

1. Select **New**, and set the following fields:

    - In the **Country/region** field, select **ESP**.
    - In the **Country/region type** field, select **EU**.

1. Select **New**, and set the following fields:

    - In the **Country/region** field, select **SWE**.
    - In the **Country/region type** field, select **EU**.

1. On the **Number sequences** tab, verify that the **Number sequence code** field is set (not blank) for the **EU sales list** reference.

### Set up sales tax codes and sales tax groups

To set up sales tax codes and sales tax groups, follow these steps.

1. In Dynamics 365 Finance, go to **Tax \> Indirect taxes \> Sales tax \> Sales tax codes**.
1. Select the **EUS** sales tax code.
1. Verify that the **Percentage/Amount** field is set to **0.00000**.
1. On the **Report setup** FastTab, in the **Country/region type** section, in the **Country/region type** field, select **EU**.
1. In the **EU sales list** section, verify that the **Excluded** option is set to **No**.
1. Go to **Tax \> Indirect taxes \> Sales tax \> Sales tax groups**.
1. Verify that the **EUS** sales tax code is included in the **AR-EU** sales tax group.
1. On the **Setup** FastTab, verify that the **Exempt** checkbox is selected for the **EUS** sales tax code.
1. Go to **Tax \> Indirect taxes \> Sales tax \> Item sales tax groups**.
1. Verify that the **FULL** item sales tax group includes the **EUS** sales tax code.
1. In the **Reporting type** field, select **Item**.

### Set up customer information

To set up customer information, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable \> Customers \> All customers**.
1. In the grid, select **DE-010**.
1. On the **Addresses** FastTab, select **Edit**.
1. In the **Edit address** dialog, in the **Country/region** field, select **ESP**.
1. In the **Primary** field, select **Yes**.
1. Select **OK**.
1. On the **Invoice and delivery** FastTab, in the **Sales tax** section, in the **Sales tax group** field, select **AR-EU**.
1. Select **Save**.
1. Close the page.
1. In the grid, select **DE-011**.
1. On the **Addresses** FastTab, select **Edit**.
1. In the **Edit address** dialog, in the **Country/region** field, select **SWE**.
1. In the **Primary** field, select **Yes**.
1. Select **OK**.

### Create a free text invoice

To create a free text invoice, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable \> Invoices \> All free text invoices**.
1. On the Action Pane, select **New**.
1. On the **Free text invoice header** FastTab, in the **Customer account** field, select **DE-010**.
1. In the **Invoice** section, in the **Date** field, select **8/6/2021** (August 6, 2021).
1. On the **Invoice lines** FastTab, set the following fields:

    - In the **Main account** field, select **112010**.
    - In the **Sales tax group** field, select **AR-EU**.
    - In the **Item sales tax group** field, select **FULL**.
    - In the **Quantity** field, select **1**.
    - In the **Unit price** field, select **120**.

1. In the **Header** view, on the **Foreign trade** FastTab, verify that the **List code** field is set to **EU trade**.
1. Post the free text invoice.
1. Go to **Tax \> Indirect taxes \> Sales tax \> Item sales tax groups**.
1. For the **FULL** item sales tax group, in the **Reporting type** field, select **Service**.
1. Repeat steps 1 through 7 for customer **DE-011**. However, set the invoice date to **8/2/2021** (August 2, 2021) and the unit price to **240**.

### Set up purchase transfers

Complete the following setup for countries or regions that include purchases in the EU sales list report.

#### Set up vendor information

To set up vendor information, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts payable \> Vendors \> All vendors**.
1. In the grid, select **DE-001**.
1. On the **Addresses** FastTab, select **Edit**.
1. In the **Edit address** dialog, in the **Country/region** field, select **DEU**.
1. In the **Primary** field, select **Yes**.
1. Select **OK**.
1. Close the page.

### Set up VAT IDs

#### Create a registration type for a company code

To create a registration type for a company code, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration \> Global address book \> Registration types \> Registration types**.
1. On the Action Pane, select **New** to create a registration type for the VAT ID.
1. In the **Enter registration type details** dialog, in the **Name** field, enter "VAT ID".
1. In the **Country/region** field, select **DEU**.

#### Match the registration type with a registration category

To match the registration type with a registration category, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration \> Global address book \> Registration types \> Registration categories**.
1. On the Action Pane, select **New** to create a link between a registration type and a registration category.
1. For the **VAT ID** registration type for Germany, select the **VAT ID** registration category.

### Create a vendor's VAT registration number

To create a vendor's VAT registration number, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts payable \> Vendors \> All vendors**.
1. In the grid, select **DE-001**.
1. On the Action Pane, on the **Vendor** tab, in the **Registration** group, select **Registration IDs**.
1. On the **Registration ID** FastTab, select **Add** to create a registration ID.
1. In the **Registration type** field, select **VAT ID**.
1. In the **Registration number** field, enter "DE100200400".
1. On the **General** tab, in the **General** section, in the **Effective** field, select **8/1/2021** (August 1, 2021).
1. On the Action Pane, select **Save**.
1. Close the page.
1. On the **Invoice and delivery** FastTab, in the **Sales tax** section, in the **Tax exempt number** field, select **DE100200400**.
1. On the Action Pane, select **Save**.
1. Close the page.

### Set up foreign trade parameters

To set up foreign trade parameters, follow these steps.

1. In Dynamics 365 Finance, go to **Tax \> Setup \> Foreign trade \> Foreign trade parameters**.
1. On the **EU sales list** tab, set the **Transfer purchases** option to **Yes**.
1. On the **Country/region properties** tab, select **New**.
1. In the **Country/region** field, select **DEU**.
1. In the **Country/region type** field, select **EU**.

### Set up sales tax codes and sales tax groups

To set up sales tax codes and sales tax groups, follow these steps.

1. In Dynamics 365 Finance, go to **Tax \> Indirect taxes \> Sales tax \> Sales tax codes**.
1. Select the **EUS** sales tax code.
1. Verify that the **Percentage/Amount** field is set to **0.00000**.
1. Go to **Tax \> Indirect taxes \> Sales tax \> Sales tax groups**.
1. Verify that the **EUS** sales tax code is included in the **AP-EU** sales tax group.
1. On the **Setup** FastTab, verify that the **Exempt** checkbox is selected for the **EUS** sales tax code.
1. Go to **Tax \> Indirect taxes \> Sales tax \> Item sales tax groups**.
1. Verify that the **FULL** item sales tax group includes the **EUS** sales tax code.
1. In the **Reporting type** field, select **Item**.

### Create a vendor invoice

To create a vendor invoice, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts payable \> Invoices \> Invoice journal**.
1. On the Action Pane, select **New**.
1. In the **Name** field, select **APInvoice**.
1. On the Action Pane, select **Lines**.
1. On the **List** tab, select **New**.
1. In the **Date** field, select **8/6/2021** (August 6, 2021).
1. In the **Account** field, select **DE-001**.
1. In the **Invoice date** field, select **8/6/2021**.
1. In the **Invoice** field, enter "VI-001".
1. In the **Credit** field, enter "120".
1. In the **Offset account** field, enter "110130-001-022".
1. In the **Sales tax group** field, select **AP-EU**.
1. In the **Item sales tax group** field, select **FULL**.
1. On the Action Pane, select **Post**.

## Work with the EU sales list

### Transfer transactions

To transfer transactions, follow these steps.

1. In Dynamics 365 Finance, go to **Tax \> Declarations \> Foreign trade \> EU sales list**.
1. On the Action Pane, select **Transfer**.
1. In the **Transfer transactions for EU sales list** dialog, set the **Item** and **Service** options to **Yes**.
1. Select **Select**.
1. Find the line where the **Table** field is set to **Customer invoice journal** and the **Field** field is set to **Date**. In the **Criteria** field, select **8/1/2021..8/31/2021**.
1. Find the line where the **Table** field is set to **Customer invoice journal** and the **Field** field is set to **List code**. Verify that the **Criteria** field is set to **!Not included**.
1. Select **OK**.
1. Select **OK**, and verify that the free text invoices that you created earlier have been moved to the **EU sales list** page.

   ![EU sales list](../media/EUSL_example.png)

### Generate the EU sales list report

To generate the EU sales list report, follow these steps.

1. On the **EU sales list** page, on the Action Pane, select **Reporting**.
1. In the **EU sales list reporting** dialog, on the **Parameters** FastTab, set the fields to generate a report for a specific country or region.

### Mark EU sales list lines as reported

To mark EU sales list lines as reported, follow these steps.

1. On the **EU sales list** page, on the Action Pane, select **Mark \> Mark as reported**.
1. Find the line where the **Field** field is set to **Reporting status**.
1. In the **Criteria** field, select **Included**.
1. Select **OK**.
1. To view the reported transactions, in the **Selection** field, select **Reported**.

### Mark EU sales list lines as closed

To mark EU sales list lines as closed, follow these steps.

1. On the **EU sales list** page, on the Action Pane, select **Mark \> Mark as closed**.
1. Find the line where the **Field** field is set to **Reporting status**. In the **Criteria** field, select **Reported**.
1. Select **OK**.
1. To view the closed transactions, in the **Selection** field, select **Closed**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
