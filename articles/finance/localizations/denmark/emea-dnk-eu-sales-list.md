---
title: EU Sales list for Denmark
description: Learn about the European Union (EU) sales list report for Denmark, including outlines on setup and how to work with the EU sales list.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/05/2026
ms.reviewer: johnmichalak
---

# EU sales list for Denmark

[!include [banner](../../includes/banner.md)]

This article provides information about the European Union (EU) sales list report for Denmark. The Danish EU sales list report contains information about the sale of goods and services for reporting in text format. The following fields are included on the Danish EU sales list report:

- **EU sales list header:**
  - Company's VAT ID without country/region code
- **EU sales list lines:**
  - Dispatch ID
  - The last day of the selected period
  - Company's VAT ID without country/region code
  - Customer VAT ID
  - The total amount of items
  - The total amount of services
  - Total amount of the triangular trade
- **EU sales list footer:**
  - Total amount
  - Number of EU sales list lines

## Setup

For general setup information, see [EU Sales list reporting](../europe/emea-eu-sales-list.md#prerequisites).

### Set up information about the company

Create a registration type, and assign it to the **VAT ID** registration category for Denmark and all the countries or regions that your company does business with, as described in Registration IDs.

1. In Microsoft Dynamics 365 Finance, go to **Organization administration** > **Organizations** > **Legal entities**.
1. In the grid, select your company.
1. On the Action Pane, select **Registration IDs**.
1. On the **Registration ID** FastTab, select **Add**.
1. On the **Overview** tab, in the **Registration type** field, select the registration type that you created.
1. Enter your company's value-added tax (VAT) ID.
1. (Optional) On the **General** tab, in the **General** section, change the period that the VAT ID is used for.
1. Close the page.

   > [!NOTE]
   > If you set the **VAT exempt number export** field in the **Intrastat** section of the **Foreign trade and logistics** FastTab (that is, it isn't blank), the value is used instead of the VAT ID that you created in step 6 in the .txt and .xlsx files for the EU sales list report.

### Import Electronic reporting configurations

- In [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/Logon/Index), import the latest versions of the following Electronic reporting (ER) configurations for the EU sales list:
  - EU Sales list model
  - EU Sales list by columns report
  - EU Sales list by rows report
  - EU Sales list (DK)

For more information, see [Download Electronic reporting configurations from Lifecycle Services](../../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

### Set up foreign trade parameters

1. In Finance, go to **Tax** > **Setup** > **Foreign trade** > **Foreign trade parameters**.
1. On the **EU sales list** tab, set the **Report cash discount** option to **Yes** if a cash discount should be included in the value when a transaction is included in the EU sales list.
1. On the **Electronic reporting** FastTab, in the **File format mapping** field, select **EU Sales list (DK)**.
1. In the **Report format mapping** field, select **EU Sales list by rows report** or **EU Sales list by columns report**.
1. On the **Country/region properties** tab, select **New**, and specify the following information:
    - In the **Country/region** column, select **DNK**.
    - In the **Country/region type** column, select **Domestic**.
1. List all the countries or regions that your company does business with. For each country/region that is part of the EU, in the **Country/region type** field, select **EU**.

## Work with the EU sales list

For general information about the types of transactions that are included in the EU sales list, and how to generate the EU sales list report and close the EU sales list reporting period, see [EU Sales list reporting](../europe/emea-eu-sales-list.md#working-with-the-esl).

### Generate the EU sales list report

1. Go to **Tax** > **Declarations** > **Foreign trade** > **EU sales list**.
1. Transfer transactions.
1. On the action pane, select **Reporting**.
1. In the **EU sales list reporting** dialog box, on the **Parameters** FastTab, set the following fields.

    | Field            | Description                                                                         |
    |------------------|-------------------------------------------------------------------------------------|
    | Reporting period | Select **Monthly** or **Quarterly**.                                                |
    | From date        | Select the start date for the report.                                               |
    | Generate file    | Set this option to **Yes** to generate a .txt file for your EU sales list report.   |
    | File name        | Enter the name of .txt file.                                                        |
    | Generate report  | Set this option to **Yes** to generate an .xlsx file for your EU sales list report. |
    | Report file name | Enter the name of the .xlsx file.                                                   |

1. Select **OK**, and review the generated reports.

## Example

For information about how to create a general setup, create postings, and transfer transactions by using the **DEMF** legal entity for Denmark, see Example for generic EU Sales list. However, for this example, use **DK00088000** as the company's VAT ID.

**Create an EU sales list report**

1. Go to **Tax** > **Declarations** > **Foreign trade** > **EU sales list**.
1. On the action pane, select **Reporting**.
1. In the **EU sales list reporting** dialog box, on the **Parameters** FastTab, set the following fields:
    - In the **Reporting period** field, select **Monthly**.
    - In the **From date** field, select **8/1/2021** (August 1, 2021).
1. Select **OK**, and review the report in text format that is generated. The following tables show the values on the example report.

    **EU sales list header**

    | Field                                        | Value            |
    |----------------------------------------------|------------------|
    | Record type                                  | 0                |
    | Company's VAT ID without country/region code | 00088000         |
    | Technical fields                             | LISTE; ; ; ; ; ; |

    **EU sales list lines**

    | Field                                        | Line1 value | Line 2 value |
    |----------------------------------------------|-------------|--------------|
    | Record type                                  | 2           | 2            |
    | Dispatch ID                                  | 000002      | 000002       |
    | The last day of the selected period          | 2021-08-31  | 2021-08-31   |
    | Company's VAT ID without country/region code | 00088000    | 00088000     |
    | Customer country/region code                 | ES          | SE           |
    | Customer VAT ID without country/region code  | 12345678    | 100200300400 |
    | Sum of all item invoices by customer         | 120         | 0            |
    | Sum of triangular trade by customer          | 0           | 0            |
    | Sum of all service invoices by customer      | 0           | 240          |

    **EU sales list footer**

    | Field                         | Value |
    |-------------------------------|-------|
    | Record type                   | 10    |
    | Number of EU sales list lines | 2     |
    | Total amount                  | 360   |

1. Review the report in Excel format that is generated.

    :::image type="content" source="../media/EUSL-dnk.png" alt-text="Screenshot of the EU sales list report in Excel for Denmark.":::

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
