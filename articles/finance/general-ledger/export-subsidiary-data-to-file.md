---
title: Export subsidiary data to files
description: Learn how to prepare to export data from Microsoft Dynamics 365 Finance and then import it into a consolidated legal entity.
author: jinniew
ms.author: jiwo
ms.topic: article
ms.date: 11/09/2022
ms.custom: 
ms.search.form:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2018-5-31
ms.dyn365.ops.version: 8.0.1
---

# Export subsidiary data to files

[!include [banner](../includes/banner.md)]

You use the **Export** page (**System administration \> Workspaces \> Import/Export**) to prepare to export subsidiary data to files that can then be imported into a consolidated legal entity. For more information about the import and export processes, see [Data import and export jobs overview](../../fin-ops-core/dev-itpro/data-entities/data-import-export-job.md).

1. Create a legal entity for the consolidation process. For information about how to create legal entities, see [Create a legal entity](../../fin-ops-core/fin-ops/organization-administration/tasks/create-legal-entity.md). For more information, see [Prepare a legal entity for use in the consolidation process](prepare-company-for-consolidation.md) and [Set up a subsidiary legal entity for consolidation](set-up-subsidiary-company-for-consolidation.md). 

2. Go to **Consolidations \> Export company balances**. On the **Export company balances** page, on the **Criteria** tab, specify the details of the consolidation by setting the following fields.

    | Field                             | Description |
    |-----------------------------------|-------|
    | **Main account**                      | Specify the accounts to consolidate. To include all accounts, leave this field blank. |
    | **Use consolidation account**         | If you've specified consolidation accounts, set this option to **Yes**. |
    | **Select consolidation account from** | Select either **Main account** or **Consolidation account group**. |
    | **Consolidation account group**       | Select a consolidation account group for the consolidation account that you selected. |
    | **Consolidation period**              | Specify "from" and "to" dates for the consolidation. |
    | **Include actual amounts**            | Set this option to **Yes** to include actual amounts. |
    | **Include budget amounts**            | Set this option to **Yes** to include budget amounts in consolidations. |
    | **Budget models**                     | Specify the budget model to include. |

3. On the **Financial dimensions** tab, specify the details of the consolidation:

    - Specify the financial dimension information that should be transferred from the transactions in the subsidiary accounts to the transactions in the consolidated legal entity.
    - Select financial dimensions in the list.
    - Identify the correct specification for each financial dimension that is consolidated. The available options include **Dimension**, **Group dimension**, **Company accounts**, and **Account**.

        > [!NOTE]
        > The **Group dimension** option lets you define the dimension value that is used by the group of companies that is being consolidated.

    - Specify the segment order to consolidate in.

4. On the **Legal entities** tab, follow these steps to specify the legal entity that you're exporting:

    1. Select **New**.
    2. In the **Source legal entity** field, enter the legal entity.

        If the same criteria apply to several subsidiaries that are in the same database, you can transfer data from those subsidiaries to separate export files in a single operation:

        1. Create a line for each subsidiary legal entity for which accounts should be exported to files. These files will be imported into the consolidated legal entity later.
        2. For each subsidiary, enter the subsidiary name and the name of the export file that will be created during the export job.

    3. In **Account type of conversion differences** field, Select **Profit and loss** or **Balance sheet**.
    4. Enter a file name for the export file that will be created.

5. Select **OK** to run the export.

When the export is completed, you receive a message that shows the number of records that were saved in each file. You can then import the files into the consolidated legal entity.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
