---
title: EU Sales list for Germany
description: Learn about the European Union (EU) sales list report for Germany, including a list of various fields that are included on the German EU sales list report.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/11/2024
ms.reviewer: johnmichalak
 
---

# EU Sales list for Germany

[!include [banner](../../includes/banner.md)]

This article provides information about the European Union (EU) sales list report. The German EU sales list report contains information about the sale of goods and services for reporting in CSV format.

> [!NOTE]
> The **EU Sales list (DE)** ER format (TXT) has been deprecated and replaced by **EU Sales list CSV (DE)** ER format. For additional details, refer to [Features removed or deprecated in the Finance](../../get-started/removed-deprecated-features-finance.md#features-removed-or-deprecated-in-the-finance-10046-release).

## Setup

For general setup information, see [EU Sales list reporting](../europe/emea-eu-sales-list.md#prerequisites).

### Import Electronic reporting configurations

Import the latest version of the following Electronic reporting (ER) configurations for the EU sales list:

- EU Sales list model
- EU Sales list by columns report
- EU Sales list by rows report
- EU Sales list CSV (DE)

Learn more about how to import ER configurations in [Import Electronic reporting (ER) configurations from Dataverse](../../localizations/global/workspace/gsw-import-er-config-dataverse.md).

### Set up foreign trade parameters

1. In Dynamics 365 Finance, go to **Tax** > **Setup** > **Foreign trade** > **Foreign trade parameters**.
2. On the **EU sales list** tab, set the **Report cash discount** option to **Yes** if a cash discount should be included in the value when a transaction is included in the EU sales list.
3. On the **Electronic reporting** FastTab, in the **File format mapping** field, select **EU Sales list CSV (DE)**.
4. In the **Report format mapping** field, select **EU Sales list by rows report** or **EU Sales list by columns report**.
5. On the **Country/region properties** tab, select **New**, and set the following fields:

    - In the **Country/region** field, select **DEU**.
    - In the **Country/region type** field, select **Domestic**.

6. List all the countries or regions that your company does business with. For each country that is part of the EU, in the **Country/region type** field, select **EU**.

## Work with the EU sales list

For general information about which types of transactions are included in the EU sales list, how to generate the EU sales list report, and how to close the EU sales list reporting period, see [EU Sales list reporting](../europe/emea-eu-sales-list.md#working-with-the-esl).

### Generate the EU sales list report

1. Go to **Tax** > **Declarations** > **Foreign trade** > **EU sales list**.
2. Transfer transactions in the usual way.
3. Optional: To create correction files, follow these steps.

    1. For corrective lines, select the checkbox in the **Corrected** column.
    2. In the **EU sales list reporting** dialog box, on the **Parameters** FastTab, set the **Correction** option to **Yes**.
    3. On the **Records to include** FastTab, apply a filter to show only corrective lines.

4. On the Action Pane, select **Reporting**.
5. In the **EU sales list reporting** dialog box, on the **Parameters** FastTab, set the following fields.

    | Field                         | Description                                                                                                               |
    |-------------------------------|---------------------------------------------------------------------------------------------------------------------------|
    | Reporting period              | Select **Monthly** or **Quarterly**.                                                                                      |
    | From date                     | Select the start date for the report.                                                                                     |
    | Generate file                 | Set this option to **Yes** to generate a .txt file for your EU sales list report.                                         |
    | File name                     | Enter the name of the .csv file.                                                                                          |
    | Generate report               | Set this option to **Yes** to generate an .xlsx file for your EU sales list report.                                       |
    | Report file name              | Enter the name of the .xlsx file.                                                                                         |
    | Correction                    | Set this option to **Yes** to create correction files.                                                                    |

6. Select **OK**, and review the generated reports.


   ![Table Description automatically generated](../media/EUSL-deu.png)
    
    
[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
