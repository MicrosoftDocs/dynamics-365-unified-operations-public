---
title: ER Configure format to do counting and summing (Part 4 - Run format)
description: This article describes how to configure an Electronic reporting format to do counting and summing based on data of the already generated text output. (Part 4)
author: kfend
ms.date: 04/10/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: ERWorkspace, ERSolutionTable, IntrastatParameters, Intrastat, InventItemIdLookupSimple, IntrastatCommodityLookup, ERFormatMappingRunLogTable, DocuView
---

# ER Configure format to do counting and summing (Part 4 - Run format)

[!include [banner](../../includes/banner.md)]

The following steps explain how a user assigned to the system administrator or electronic reporting developer role can configure an Electronic reporting (ER) format to do counting and summing based on data from the already generated text output. You can perform these steps in the DEMF company.

To complete these steps, you must first complete the steps in the "ER Configure format to do counting and summing (Part 3: Use computations to make the output)" procedure.

This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.

## Test this configuration for generation of the Intrastat reports

1. Go to Organization administration > Workspaces > Electronic reporting.
1. Click Reporting configurations.
1. In the tree, expand **Intrastat model**.
1. In the tree, expand **Intrastat model\Intrastat (DE)**.
1. In the tree, select **Intrastat model\Intrastat (DE)\Intrastat (DE) with counting & summing**.
1. On the Action Pane, select **Configurations**.
1. Select **User parameters**.
1. Select Yes in the Run settings field.
1. Select **OK**.
1. Click Edit.
1. Select Yes in the Run Draft field.
1. Click Save.
1. Go to Tax > Setup > Foreign trade > Foreign trade parameters.
1. Expand the Electronic reporting section.
1. Select the "Intrastat (DE) with counting & summing" configuration.
1. Select the "Intrastat (DE) with counting & summing" configuration.
1. Click Save.
1. Close the page.
1. Go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
1. Select **Output**.
1. Select **Report**.
    * Run the Intrastat report generation process.  
1. In the From date field, set the date to '2000-01-01'.
    * Define start and end dates for the reporting period that include the existing on the form transactions.  
1. In the To date field, set the date to '2022-12-31'.
    * Define start and end dates for the reporting period that include the existing on the form transactions.  
1. In the Direction field, select 'Arrivals'.
1. Select Yes in the Generate file field.
1. Select **OK**.
    * Review the created output with the summary lines in the end.  
1. Click New.
1. In the list, mark the selected row.
1. In the Direction field, select 'Dispatches'.
1. In the Item number field, enter or select a value.
1. In the Commodity field, enter or select a value.
1. Set Weight to '10'.
1. Set Invoice amount to '10000'.
1. Set Statistical amount to '10000'.
1. Select **Output**.
1. Select **Report**.
1. In the Direction field, select 'Dispatches'.
1. Select **OK**.
    * Review the created output with the summary lines in the end. Note that it has been changed in comparison to the first run.    

## Run this configuration in debug mode to review the collected counting and summing data

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. In the tree, expand **Intrastat model**.
1. In the tree, expand **Intrastat model\Intrastat (DE)**.
1. In the tree, select **Intrastat model\Intrastat (DE)\Intrastat (DE) with counting & summing**.
1. On the Action Pane, select **Configurations**.
1. Select **User parameters**.
1. Select **Yes** in the **Run in debug mode** field.
1. Select **OK**.
1. Close the page.
1. Go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
1. Select **Output**.
1. Select **Report**.
1. Select **OK**.
1. Close the page.
1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. In the tree, expand **Intrastat model**.
1. In the tree, expand **Intrastat model\Intrastat (DE)**.
1. In the tree, select **Intrastat model\Intrastat (DE)\Intrastat (DE) with counting & summing**.
1. Select **Debug logs**.
    * A debug log record is created for the execution process of the selected configuration.  
1. Select **Attach**.
1. Select **Open**.
    * Review the created XML file that contains counting and summing details that the system collects during the execution of the selected configuration.    

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
