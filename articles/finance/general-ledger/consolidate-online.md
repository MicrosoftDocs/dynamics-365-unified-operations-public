---
# required metadata

title: Online financial consolidations
description: This article describes online financial consolidations using templates in General ledger.
author: jchrist
ms.date: 04/22/2024
ms.topic: article
# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jchrist
ms.search.validFrom: 2018-5-31
ms.dyn365.ops.version: 8.0.1

---

# Online financial consolidations

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article describes online financial consolidations in General ledger. Before you read this article, be sure to read the [Financial consolidations and currency translation overview](financial-consolidations-currency-translation.md) article

## Perform consolidation

After the **Consolidation templates** are set up, use the **Consolidate online** page to consolidate legal entities.
1. Go to **Consolidate online**, select **Perform consolidation** from the action pane.
2. Enter the **From** and **To** date that you want to use for the consolidation.
3. Select the consolidation **Template** using the drop down.
We don't recommend that you set the **Rebuild balances during consolidation** to **Yes**. Instead, rebuild balances as a separate batch job.
4. The **Description** field defaults with the template name but can be edited.
5. To run the consolidation as a batch job, set **Batch process** to **Yes** and update the fields as needed.
6. Select **OK** to start the consolidation process. 

Once the consolidation process has finished, a record of the process shows in the **Consolidation history** tab. Each legal entity that was processed in the consolidation displays in the grid. 
- The **Process date/time** shows when the process started. The legal entity displays in **Company accounts**.
- The **Description** is the text from the **Consolidations** page.
- The **From date** and **To date** show the dates included in the consolidation.
- The template name shows in the **Ledger consolidation template** field.
- Use the **Notes** column to enter any notes about the consolidation or your review process. Notes can only be entered before the record is marked as **Reviewed**. 

To access the consolidation templates, select the **Consolidation online template setup** in the action pane. 

### Other consolidation options
- To view the transactions, select a consolidation line, then select the Transactions menu under **Consolidations history**.
  - Select **Actuals** to view the transactions for this legal entity.
  - Select **Budget** if you included budget transactions on the template.
- After reviewing transactions, select **Reviewed** from the action pane to mark this record as **Reviewed**. The checkbox in the **Reviewed** column will be marked and **Notes** can't be entered for the record. 

- Select **Rerun consolidation** to run the exact same consolidation process again. The same template, same dates, and same legal entity will be processed again. Any consolidation transactions are removed from the existing record and processed again on the new record.
- Select **Reverse transaction** to remove the transactions from the consolidated accounts. Once a record has been reversed, select the **Show reversed** checkbox to view any records that have been reversed. The **Reversed** checkbox is marked along with the **Reversed date/time** column. Any record can be reversed, including records that have been marked **Reviewed**.
- Use the **View consolidation timeline** to see the background progress of the consolidations batch job. The name of the batch job is the title of the page that opens. Once the consolidation batch job is finished, the batch job name, status, and the start and end times are displayed. 

### Display options 
All consolidation records are kept in history and can be seen in the grid for audit purposes. 
- Use the **Show** option to change what lines are displaying. Select **All** to view reviewed and not reviewed consolidation records. 
- Select **Not reviewed** to show only those consolidation records that aren't marked **Reviewed**. 
- Select **Reviewed** to show only those consolidation records that are marked **Reviewed**.
- Select the **Show reversed** checkbox to include reversed records in the grid. 

To learn more about consolidation templates and how to set them up, see [Consolidation templates](Consolidation-templates.md)

