---
title: EU Sales list for Sweden
description: Learn about the European Union (EU) sales list report for Sweden, including outlines and step-by-step processes for various setups.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/27/2024
ms.reviewer: johnmichalak
 
---

# EU Sales list for Sweden

[!include [banner](../../includes/banner.md)]

This article provides information about the European Union (EU) sales list report. The Swedish EU sales list report contains information about the sale of goods and services for reporting in text format.

The following fields are included on the Swedish EU sales list report:

- **EU sales list header**

    - Company VAT ID
    - Person responsible for the report
    - Primary email and telephone number of the person
    - Reporting period

- **EU sales list lines**

    - Customer VAT ID
    - Total amount of items
    - The total amount of services
    - Total amount of the triangular trade

## Setup

For general setup information, see [EU Sales list reporting](../europe/emea-eu-sales-list.md#prerequisites).

> [!NOTE]
> The company's tax registration number will be used in the .xlsx file for the EU sales list report.

### Set up company information

Create a registration type, and assign it to the **VAT ID** registration category for Sweden and all the countries or regions that your company does business with. For more information, see [Registration IDs](../europe/emea-registration-ids.md).

1. Go to **Organization administration** > **Organizations** > **Legal entities**.
2. In the grid, select your company.
3. On the Action Pane, select **Registration IDs**.
4. On the **Registration ID** FastTab, select **Add**.
5. On the **Overview** tab, in the **Registration type** field, select the registration type that is assigned to the **VAT ID** registration category.
6. Enter your company's value-added tax (VAT) ID.
7. Optional: On the **General** tab, in the **General** section, change the period when the registration ID is used.
8. Close the page.

>[!NOTE]
> If the **VAT exempt number export** field in the **Intrastat** section on the **Foreign trade and logistics** FastTab is set (that is, it isn't blank), that value will be used, instead of the VAT ID that you created, in the .txt file of the EU sales list report.

### Import Electronic reporting configurations

In [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/Logon/Index), import the latest version of the following Electronic reporting (ER) configurations for the EU sales list:

- EU Sales list model
- EU Sales list by columns report
- EU Sales list by rows report
- EU Sales list (SE)

For more information, see [Download Electronic reporting configurations from Lifecycle Services](../../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

### Set up foreign trade parameters

1. In Dynamics 365 Finance, go to **Tax** > **Setup** > **Foreign trade** > **Foreign trade parameters**.
2. On the **EU sales list** tab, set the **Report cash discount** option to **Yes** if a cash discount should be included in the value when a transaction is included in the EU sales list.
3. On the **Electronic reporting** FastTab, in the **File format mapping** field, select **EU Sales list (SE)**.
4. In the **Report format mapping** field, select **EU Sales list by rows report** or **EU Sales list by columns report**.
5. On the **Country/region properties** tab, select **New**, and set the following fields:

    - In the **Country/region** field, select **SWE**.
    - In the **Country/region type** field, select **Domestic**.

6. List all the countries or regions that your company does business with. For each country that is part of the EU, in the **Country/region type** field, select **EU** to show trade with those countries on the **EU sales list** page.

## Work with the EU sales list

For general information about which types of transactions are included in the EU sales list, how to generate the EU sales list report, and how to close the EU sales list reporting period, see [EU Sales list reporting](../europe/emea-eu-sales-list.md#working-with-the-esl).

### Generate the EU sales list report

1. Go to **Tax** > **Declarations** > **Foreign trade** > **EU sales list**.
2. Transfer transactions in the usual way.
3. On the Action Pane, select **Reporting**.
4. In the **EU sales list reporting** dialog box, on the **Parameters** FastTab, set the following fields.

    | Field            | Description                                                                         |
    |------------------|-------------------------------------------------------------------------------------|
    | Reporting period | Select **Monthly** or **Quarterly**.                                                |
    | From date        | Select the start date for the report.                                               |
    | Generate file    | Set this option to **Yes** to generate a .txt file for your EU sales list report.   |
    | File name        | Enter the name of the .txt file.                                                    |
    | Generate report  | Set this option to **Yes** to generate an .xlsx file for your EU sales list report. |
    | Report file name | Enter the name of the .xlsx file.                                                   |
    | Contact ID       | Select the contact for the person who is responsible for the report.                |

5.  Select **OK**, and review the generated reports.

## Example

For information about how to create a general setup, create postings, and transfer transactions by using the **DEMF** legal entity for Sweden, see [Example for generic EU Sales list](../europe/emea-eu-sales-list-example.md). However, for the example in this article, create **SE100200300400** as the company's VAT ID. Additionally, set the **DE-011** customer location to Germany, and create **DE100200300** as the VAT ID.

### Create a contact for the person who is responsible for the report

1. Go to **Sales and marketing** > **Relationships** > **Contacts**.
2. On the Action Pane, select **New**.
3. In the **Create contact** dialog box, in the **Contact for** field, select **Contoso Entertainment System Sweden**. Then select **Select**.
4. In the **First name** field, select **Aaren Ekelund**. Then select **Select**.
5. Select **Save**.

### Create an EU sales list report

1. Go to **Tax** > **Declarations** > **Foreign trade** > **EU sales list**.
2. On the Action Pane, select **Reporting**.
3. In the **EU sales list reporting** dialog box, on the **Parameters** FastTab, set the following fields:

    - In the **Reporting period** field, select **Monthly**.
    - In the **From date** field, select **8/1/2021** (August 1, 2021).
    - Set the **Generate file** option to **Yes**.
    - In the **File name** field, enter **SE-001F**.
    - Set the **Generate report** option to **Yes**.
    - In the **Report file name** field, enter **SE-001R**.
    - In the **Contact ID** field, select the contact that you created.

4. Select **OK**, and review the report in text format that is generated. The following tables show the values on the example report.

    **EU sales list header**

    | Field                 | Value              | Comment                                                            |
    |-----------------------|--------------------|--------------------------------------------------------------------|
    | File indicator        | SKV574008          |                                                                    |
    | Company VAT ID        | 100200300400       | The value is the company's VAT ID without the country/region code. |
    | Reporting period      | 2108               | The value is the reporting year and the quarter or month number.   |
    | Contact name          | Ekelund Aaren      |                                                                    |
    | Contact phone         | 415 555-5153       |                                                                    |
    | Contact email address | AarenE@contoso.com |                                                                    |

    **EU sales list lines**

    | Field                                   | Line 1 value | Line 2 value |
    |-----------------------------------------|--------------|--------------|
    | Customer VAT ID                         | ES1234567    | DE100200300  |
    | Sum of all item invoices by customer    | 120.00       | 0            |
    | Sum of triangular trade by customer     | 0            | 0            |
    | Sum of all service invoices by customer | 0            | 240.00       |

5. Review the report in Excel format that is generated.

    ![Table Description automatically generated with medium confidence](../media/EUSL-swe.png)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
