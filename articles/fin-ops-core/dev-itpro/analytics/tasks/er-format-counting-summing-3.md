---
title: ER Configure format to do counting and summing (Part 3 - Use computations to make the output)
description: This article describes how to configure an Electronic reporting format to do counting and summing based on data of the already generated text output. (Part 3)
author: kfend
ms.date: 04/10/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: ERWorkspace, ERSolutionTable, EROperationDesigner, ERDataSourceAddDropDialog, ERExpressionDesignerFormula, ERComponentTypeDropDialog
---

# ER Configure format to do counting and summing (Part 3 - Use computations to make the output)

[!include [banner](../../includes/banner.md)]

The following steps explain how a user assigned to the system administrator or electronic reporting developer role can configure an Electronic reporting (ER) format to do counting and summing based on data of the already generated text output. You can perform these steps in any company.

To complete these steps, you must first complete the steps in the "ER Configure format to do counting and summing (Part 2: Configure computations)" procedure.

This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.

## Configure this report to use counting and summing info

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
1. Select **Reporting configurations**.
1. In the tree, expand **Intrastat model**.
1. In the tree, expand **Intrastat model\Intrastat (DE)**.
1. In the tree, select **Intrastat model\Intrastat (DE)\Intrastat (DE) with counting & summing**.
1. Select **Designer**.
1. Select the **Mapping** tab.
1. Select **Add root** to open the drop dialog.
    * Add a new data source to get the list of memorized blocks.  
1. In the tree, select **Functions\Calculated field**.
1. In the **Name** field, type `$BlocksList`.
    * `$BlocksList`  
1. Select **Edit formula**.
1. In the tree, select **Data collection functions\COLLECTEDLIST**.
1. Select **Add function**.
1. Select **Add data source**.
1. In the **Formula** field, enter `COLLECTEDLIST('$BlockName', '`.
    * `COLLECTEDLIST('$BlockName', `  
1. In the **Formula** field, enter `COLLECTEDLIST('$BlockName', "*")`.
    * `COLLECTEDLIST('$BlockName', "*")`  
1. Select **Save**.
    * The pattern `*` means that all blocks are included in the list for this record.  
1. Close the page.
1. Click OK.
1. Select the **Format** tab.
1. In the tree, select 'Intrastat\Data'.
1. Click Add to open the drop dialog.
1. In the tree, select 'Text\Sequence'.
1. In the Name field, type 'Totals by blocks'.
    * Totals by blocks  
1. In the Special characters field, select 'New line - Windows (CR LF)'.
1. Click OK.
1. In the tree, select 'Intrastat\Data\Totals by blocks'.
1. Click Add to open the drop dialog.
1. In the tree, select 'Text\String'.
1. In the Name field, type 'Block code'.
    * Block code  
1. Click OK.
1. Click Add String.
1. In the Name field, type 'Lines counting'.
    * Lines counting  
1. Click OK.
1. Click Add String.
1. In the Name field, type 'Total amount'.
    * Total amount  
1. Click OK.
1. Select the **Mapping** tab.
1. In the tree, select '$BlocksList'.
1. Click Bind.
    * Create a summary line for each memorized block.  
1. Select the **Format** tab.
1. In the tree, select 'Intrastat\Data\Totals by blocks\Block code'.
1. Select the **Mapping** tab.
1. Select **Edit formula**.
1. In the Formula field, enter '"Block id: " & '.
    * "Block id: " &  
1. In the tree, expand `$BlocksList`.
1. In the tree, select `$BlocksList\Value`.
1. Select **Add data source**.
1. Select **Save**.
1. Close the page.
1. Select the **Format** tab.
1. In the tree, select `Intrastat\Data\Totals by blocks\Lines counting`.
1. Select the **Mapping** tab.
1. Select **Edit formula**.
    * Create output for the number of lines for each block presented in this report.  
1. In the **Formula** field, enter `"Number of lines in this block: " & `.
    * `"Number of lines in this block: " & `  
1. In the **Formula** field, enter `"Number of lines in this block: " & TEXT(`.
    * `"Number of lines in this block: " & TEXT(`  
1. In the tree, select `Data collection functions\COUNTIFS`.
1. Select **Add function**.
1. Select **Add data source**.
1. In the **Formula** field, enter `"Number of lines in this block: " & TEXT(COUNTIFS('$BlockName', `.
    * `"Number of lines in this block: " & TEXT(COUNTIFS('$BlockName', `  
1. In the tree, expand `$BlocksList`.
1. In the tree, select `$BlocksList\Value`.
1. Select **Add data source**.
1. In the **Formula** field, enter `"Number of lines in this block: " & TEXT(COUNTIFS('$BlockName', '$BlocksList'.Value, `.
    * `"Number of lines in this block: " & TEXT(COUNTIFS('$BlockName', '$BlocksList'.Value, `  
1. In the tree, select `$RecName`.
1. Select **Add data source**.
1. In the **Formula** field, enter `"Number of lines in this block: " & TEXT(COUNTIFS('$BlockName', '$BlocksList'.Value, '$RecName', "*"))`.
    * `"Number of lines in this block: " & TEXT(COUNTIFS('$BlockName', '$BlocksList'.Value, '$RecName', "*"))`  
1. Select **Save**.
1. Close the page.
1. Select the **Format** tab.
1. In the tree, select `Intrastat\Data\Totals by blocks\Total amount`.
1. Select the **Mapping** tab.
1. Select **Edit formula**.
    * Create output that is the total of the invoiced amount for each block presented in this report.  
1. In the **Formula** field, enter `"Sum of invoiced amount: " & TEXT(SUMIFS('$InvName', '$BlockName', '$BlocksList'.Value, '$RecName', "*"))`.
    * `"Sum of invoiced amount: " & TEXT(SUMIFS('$InvName', '$BlockName', '$BlocksList'.Value, '$RecName', "*"))`  
1. Select **Save**.
1. Close the page.
1. Select **Save**.
1. Close the page.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
