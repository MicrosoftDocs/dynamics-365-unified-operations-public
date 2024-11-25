---
title: Online financial consolidations
description: Learn about online financial consolidations that use templates in General ledger, including an outline and process for performing consolidation.
author: jchrist
ms.author: jchrist
ms.topic: article
ms.date: 04/22/2024
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2018-5-31
ms.search.form: 
ms.dyn365.ops.version: 8.0.1
---

# Online financial consolidations

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article describes online financial consolidations in General ledger. Before you read this article, be sure to read the [Financial consolidations and currency translation overview](financial-consolidations-currency-translation.md) article.

## Perform consolidation

After the consolidation templates are set up, use the **Consolidate online** page to consolidate legal entities.

1. On the **Consolidate online** page, on the Action Pane, select **Perform consolidation**.
1. Use the **From** and **To** fields to specify the date range that you want to use for the consolidation.
1. In the **Template** field, select the consolidation template.

    > [!NOTE]
    > We don't recommend that you set the **Rebuild balances during consolidation** option to **Yes**. Instead, rebuild balances as a separate batch job.

1. By default, the **Description** field is set to the template name, but you can edit the value.
1. To run the consolidation as a batch job, set the **Batch process** option to **Yes**, and update the fields as required.
1. Select **OK** to start the consolidation process.

After the consolidation process is completed, the **Consolidation history** tab shows a record of the process. Each legal entity that was processed during the consolidation appears in the grid.

- The **Process date/time** column shows when the process was started.
- The **Company accounts** column shows the legal entity.
- The **Description** column shows the text from the **Consolidations** page.
- The **From date** and **To date** columns show the date range that's included in the consolidation.
- The **Ledger consolidation template** column shows the template name.
- Use the **Notes** column to enter any notes about the consolidation or your review process. Notes can be entered only until the record is marked **Reviewed**.

To access the consolidation templates, select **Consolidation online template setup** on the Action Pane.

### Other consolidation options

- To view the transactions, select a consolidation line, and then, under **Consolidations history**, on the **Transactions** menu, select one of the following options:

    - Select **Actuals** to view the transactions for this legal entity.
    - Select **Budget** if you included budget transactions on the template.

- After you finish reviewing the transactions, select **Reviewed** on the Action Pane to mark the record as **Reviewed**. The checkbox in the **Reviewed** column is selected, and **Notes** can no longer be entered for the record.
- Select **Rerun consolidation** to rerun the same consolidation process. The same template, the same dates, and the same legal entity are processed again. Any consolidation transactions are removed from the existing record and processed again on the new record.
- Select **Reverse transaction** to remove the transactions from the consolidated accounts. After a record is reversed, select the **Show reversed** checkbox to view the records that were reversed. The **Reversed** checkbox is selected, and a value is entered in the **Reversed date/time** column. Any record can be reversed, including records that were marked **Reviewed**.
- Use **View consolidation timeline** to view the background progress of the consolidations batch job. The name of the batch job is used as the title of the page that appears. After the consolidation batch job is completed, the batch job name, the status, and the start and end times are shown.

### Display options

All consolidation records are kept in history and can be viewed in the grid for audit purposes.

- Use the **Show** option to change the lines that are shown. Select **All** to show both reviewed and unreviewed consolidation records.
- Select **Not reviewed** to show only consolidation records that aren't marked **Reviewed**.
- Select **Reviewed** to show only consolidation records that are marked **Reviewed**.
- Select the **Show reversed** checkbox to include reversed records in the grid.

For more information about consolidation templates and how to set them up, see [Consolidation templates](Consolidation-templates.md).
