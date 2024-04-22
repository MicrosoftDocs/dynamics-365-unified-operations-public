---
# required metadata

title: Online financial consolidations
description: This article describes online financial consolidations using templates in General ledger.
author: aprilolson
ms.date: 12/07/2022
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
ms.author: aolson
ms.search.validFrom: 2018-5-31
ms.dyn365.ops.version: 8.0.1

---
The Consolidate online page was changed in version 10.0.40 to use Consolidation Templates. See more information on how to enable and use the Consolidation templates. 

## Perform consolidation

After you have setup Consolidation templates use the Consolidate online page to perform the consolidation of your legal entities. Select **Perform consolidation** from the action pane. Enter the **From** and **To** date that you want to use for the consolidation. Select the consolidation **Template** using the drop down. We don't recommend that you set the **Rebuild balances during consolidation** to **Yes**. Instead, rebuild balances as a separate batch job. The **Description** field will default with the template name but this can be edited as needed. To run the consolidation as a batch job set the Batch process to **Yes** and update the fields as needed. Select **OK** to start the consolidation process. 

Once the Consolidation process has finished a record of the process will show in the Consolidation history tab. Each legal entity that was processed in the consolidation will display in the grid. 
- The **Process date/time** shows when the process started. The legal entity displays in Company accounts.
- The **Description** is the text from the Consolidations page.
- The **From date** and **To date** show the dates included in the consolidation.
- The template name shows in the **Ledger consolidation template** field.
- Use the **Notes** column to enter any notes about the consolidation or your review process. Notes can only be entered before the record is marked as Reviewed. 

To access the consolidation templates select the **Consolidation online template setup** in the action pane. 

### Other consolidation options
- To view the transactions select a consolidation line, then select the Transactions menu under **Consolidations history**.
  - Select **Actuals** to take you to the Ledger transactions page to view the transactions for this legal entity.
  - Select **Budget** if you included budget transactions on the template.
- After reviewing transactions select **Reviewed** from the action pane to mark this record as Reviewed. The checkbox in the Reviewed column will be marked and Notes can no longer be entered for the record. 

- Select **Rerun consolidation** to run the exact same consolidation process again. The same template, same dates and same legal entity will be processed again. Any consolidation transactions are removed from the existing record and processed again on the new record.
- Select **Reverse transaction** to remove the transactions from the consolidated accounts. Once a record has been reversed select the **Show reversed** checkbox to view any records that have been reversed. The **Reversed** checkbox is marked along with the **Reversed date/time** column. Any record can be reversed, including records that have been marked Reviewed.
- Use the **View consolidation timeline** to see the background progress of the consolidations batch job. The name of the batch job is the title of the page that opens. Once the consolidation batch job is finished you will only see the name of the batch job, the status and the start and end times. 

### Display options 
All consolidation records are kept in history and can be seen in the grid for audit purposes. 
- Use the **Show** option to change what lines are displaying. Select **All** to view all (reviewed and not reviewed) consolidation records. 
- Select **Not reviewed** to show only those consolidation records that have not been marked Reviewed. This is the default display.
- Select **Reviewed** to show only those consolidation records that have marked Reviewed.
- Mark the **Show reversed** checkbox to include reversed records in the grid. 

To learn more about Consolidation templates and how to set them up see [Consolidation templates](Consolidation-templates.md)

