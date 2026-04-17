---
title: ER Configure format to do counting and summing (Part 2 - Configure computations)
description: This article describes how to configure an Electronic reporting format to do counting and summing based on data of the already generated text output. (Part 2)
author: kfend
ms.date: 04/10/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: ERWorkspace, ERSolutionTable, ERSolutionCreateDropDialog, EROperationDesigner, ERDataSourceAddDropDialog, ERExpressionDesignerFormula
---

# ER Configure format to do counting and summing (Part 2 - Configure computations)

[!include [banner](../../includes/banner.md)]

The following steps explain how a user assigned to the system administrator or electronic reporting developer role can configure an Electronic reporting (ER) format to do counting and summing based on data of the already generated text output. You can perform these steps in any company.

To complete these steps, you must first complete the steps in the "ER Configure format to do counting and summing (Part 1: Create format)" procedure.

This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.

## Create a format configuration to add counting and summing details

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
1. Select **Reporting configurations**.
1. In the tree, expand **Intrastat model**.
1. In the tree, select **Intrastat model\Intrastat (DE)**.
    * To customize the format that Microsoft provides, add lines with summary details at the end of the Intrastat report. Derive your own instance of the Intrastat configuration from the Microsoft instance to make modifications.  
1. Select **Create configuration** to open the dialog.
1. In the **New** field, enter `Intrastat (DE), Microsoft`.
1. In the **Name** field, type `Intrastat (DE) with counting & summing`.
1. Select **Create configuration**.

## Configure this report to count and sum based on output details

1. Select **Designer**.
1. Select **Yes** in the **Collect output details** field.
    * This flag activates at run-time the process of collecting output details for generating the Intrastat file.  
    * You need to count for different Intrastat directions, so add a dedicated model enumeration to the data sources' list of this format configuration.  
1. Select the **Mapping** tab.
1. Select **Add root** to open the drop dialog.
1. In the tree, select `Data model\Enumeration`.
1. In the **Name** field, type `Direction`.
1. In the **Model enumeration** field, enter or select a value.
    * Select the value `Direction`.  
1. Select **OK**.
1. Select **Add root** to open the drop dialog.
1. In the tree, select `Functions\Calculated field`.
1. In the **Name** field, type `$BlockName`.
1. Select **Edit formula**.
1. In the **Formula** field, enter `"block"`.
1. Select **Save**.
1. Close the page.
1. Select **OK**.
1. Select **Add root** to open the drop dialog.
1. In the tree, select `Functions\Calculated field`.
1. In the **Name** field, type `$RecName`.
1. Select **Edit formula**.
1. In the **Formula** field, enter `"record"`.
1. Select **Save**.
1. Close the page.
1. Select **OK**.
1. Select **Add root** to open the drop dialog.
1. In the tree, select `Functions\Calculated field`.
1. In the **Name** field, type `$InvName`.
1. Select **Edit formula**.
1. In the **Formula** field, enter `"InvoicedAmountEUR"`.
1. Select **Save**.
1. Close the page.
1. Select **OK**.
1. In the tree, select `Intrastat\Data`.
1. Select **Edit** for the **Collected data key name** field.
1. Select **Add data source**.
    * Use `$BlockName`.  
1. Select **Save**.
1. Close the page.
1. Select **Edit** for the **Collected data key value** field.
1. In the **Formula** field, enter `IF(Intrastat.CommodityRecord.Direction=Direction.Import, "Import", "Export")`.
    * Use `IF(Intrastat.CommodityRecord.Direction=Direction.Import, "Import", "Export")`.  
1. Select **Save**.
1. Close the page.
    * Count the lines of this sequence. The results are used with the name `block` separately for different directions. Value `Import` is used for any arrivals Intrastat transactions. The value `Export` is used for any Intrastat dispatches transactions. Consider this to be a virtual Excel spreadsheet. For each transaction a row where the first column `block` is filled with the values `Import` and `Export` accordingly.  
1. In the tree, expand `Intrastat\Data: Sequence`.
1. In the tree, select `Intrastat\Data: Sequence\Arrivals?`.
1. Select **Edit** for the **Collected data key name** field.
    * Count the lines of this sequence. The results are stored using the name `record`.  
1. In the tree, select `$RecName`.
1. Select **Add data source**.
1. Select **Save**.
1. Close the page.
1. Select **Edit** for the **Collected data key value** field.
1. In the **Formula** field, enter `Intrastat.CommodityRecord.CommodityCode`.
1. Select **Save**.
1. Close the page.
    * Count the lines in this sequence. Use the results with the name "record" for different commodity codes. Consider this count as a virtual Excel spreadsheet. For each transaction, create a row where the first column "block" contains the values "Import" and "Export" accordingly, and the second column "record" contains the commodity code value.  
1. In the tree, select `Intrastat\Data: Sequence\Dispatches?`.
1. Select **Edit** for the **Collected data key name** field.
1. In the tree, select `$RecName`.
1. Select **Add data source**.
1. Select **Save**.
1. Close the page.
1. Select **Edit** for the **Collected data key value** field.
1. In the **Formula** field, enter `Intrastat.CommodityRecord.CommodityCode`.
1. Select **Save**.
1. Close the page.
1. In the tree, expand `Intrastat\Data: Sequence\Dispatches: Sequence?`.
1. In the tree, expand `Intrastat\Data: Sequence\Dispatches: Sequence?\Record =  Intrastat.CommodityRecord`.
1. Select the **Format** tab.
1. In the tree, select `Intrastat\Data\Dispatches\Record\Invoice amount EUR`.
1. Select the **Mapping** tab.
1. Select **Edit** for the **Collected data key name** field.
1. In the tree, select `$InvName`.
1. Select **Add data source**.
1. Select **Save**.
1. Close the page.
    * Summarize the invoiced amount values for lines in this sequence. Use the results with the name "InvoicedAmountEUR" for different Intrastat directions and commodity codes. Consider this summary as a virtual creation in an Excel spreadsheet. For each transaction, create a row where the first column "block" contains the values "Import" and "Export" accordingly. The second column "record" contains the commodity code value, and the third column "InvoicedAmountEUR" contains the invoice amount value.  
1. In the tree, expand `Intrastat\Data\Arrivals?`.
1. In the tree, expand `Intrastat\Data\Arrivals?\Record =  Intrastat.CommodityRecord`.
1. Select the **Format** tab.
1. In the tree, select `Intrastat\Data\Arrivals\Record\Invoice amount EUR`.
1. Select the **Mapping** tab.
1. Select **Edit** for the **Collected data key name** field.
1. In the tree, select `$InvName`.
1. Select **Add data source**.
1. Select **Save**.
1. Close the page.
1. Select **Save**.
1. Close the page.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
