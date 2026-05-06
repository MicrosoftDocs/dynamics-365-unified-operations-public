---
title: ER Use horizontally expandable ranges to dynamically add columns in Excel reports (Part 2 - Run format)
description: This article describes how to configure an Electronic reporting (ER) format to generate reports as OPENXML worksheets (Excel) files. (Part 2)
author: kfend
ms.date: 04/10/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: ERSolutionTable, SysQueryForm
---

# ER Use horizontally expandable ranges to dynamically add columns in Excel reports (Part 2 - Run format)

[!include [banner](../../includes/banner.md)]

The following steps explain how a user assigned to the system administrator or electronic reporting developer role can configure an Electronic reporting (ER) format to generate reports as OPENXML worksheets (Excel) files in which the required columns can be created dynamically as horizontally expandable ranges. You can perform these steps in the DEMF company.

To complete these steps, you must first complete the steps in the "ER Use horizontally expandable ranges to dynamically add columns in Excel reports (Part 1: Design format)" procedure.

This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.

## Find created format

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. In the tree, expand **Financial dimensions sample model**.
1. In the tree, select **Financial dimensions sample model\Sample report with horizontally expandable ranges**.

## Execute format to create Excel output

1. Select **Run**.
1. In the **Dimension name** field, type `BusinessUnit;CostCenter;Department`.
    * In the **Dimension name** field, enter or select a value. To select all dimensions for the current company, enter the following value: `BusinessUnit;CostCenter;Department;ItemGroup;MainAccount;Project`  
1. Expand the **Records to include** section.
1. Select **Filter**.
1. Select the row for the **Ledger journal** table and the **Journal batch number** field.
1. In the **Criteria** field, type `00057..00058`.
    * 00057..00058  
1. Select **OK**.
1. Select **OK**.
    * Review the generated output. The newly created Excel file contains the same number of columns that you selected for financial dimensions. The report header in those columns represents financial dimensions' names. The transactions' lines in those columns represent financial dimensions. Run this report and select different dimensions to see that the report isn't dependent on the number of selected dimensions or the number of dimensions configured for this instance.    

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
