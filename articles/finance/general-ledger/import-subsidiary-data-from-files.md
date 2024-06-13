---
title: Import subsidiary data from files
description: Learn how to prepare data from external systems so that it can be imported into Microsoft Dynamics 365 Finance, including a step-by-step process.
author: jinniew
ms.author: jiwo
ms.topic: article
ms.date: 10/09/2022
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-12-01
ms.search.form: 
ms.dyn365.ops.version: 8.0.1
---

# Import subsidiary data from files

[!include [banner](../includes/banner.md)]

This article explains how to prepare data from external systems so that it can be imported into Microsoft Dynamics 365 Finance. You use the **Consolidate with import** page (**Consolidations \> Consolidate with import**) to prepare the transfer of subsidiary data from external systems.

1. Create a subsidiary legal entity for the consolidation. For information about how to create legal entities, see [Create a legal entity](../../fin-ops-core/fin-ops/organization-administration/tasks/create-legal-entity.md). For more information, see [Prepare a legal entity for use in the consolidation process](prepare-company-for-consolidation.md) and [Set up a subsidiary legal entity for consolidation](set-up-subsidiary-company-for-consolidation.md).

2. Prepare a file that will contain the data that is imported. For more information about the import process, see [Data import and export jobs overview](../../fin-ops-core/dev-itpro/data-entities/data-import-export-job.md).
3. Export the data to a file by following the steps in the "Data import/export process" procedure in [Data import and export jobs overview](../../fin-ops-core/dev-itpro/data-entities/data-import-export-job.md). You can use that procedure to consolidate data either from another instance of Dynamics 365 Finance or from Dynamics 365 Business Central. If you're importing data from external systems, data must be in the format that's described in [Export subsidiary data to files](export-subsidiary-data-to-file.md).
4. Go to **Consolidations \> Consolidate with import**. On the **Consolidate with import** page, on the **Criteria** tab, specify the details of the report and/or the import by setting the following fields.

| Field                                 | Value for the report | Value for the import |
|---------------------------------------|----------------------|----------------------|
| **Description**                      | Not applicable | Enter a description to identify the import. |
| **Main account**    | Define the range of accounts that the report should include. If you don't define a range, all accounts will be included. | Define the range of accounts that the import should include. If you don't define a range, all accounts will be included. |
    | **Consolidation period**                  | Define the range of dates to consolidate. | Define the range of dates to consolidate. |
    | **Include actual amounts**                | Set this option to **Yes** to include actuals. | Set this option to **Yes** to include actuals. |
| **Include budget amounts** | Set this option to **Yes** to include budget amounts in consolidations. | Set this option to **Yes** to include budget amounts in consolidations. |
| **Rebuild balances during consolidation** | Set this option to **Yes** if the rebuild process should completely clear the balance and new records, and re-create the balance from the beginning of time. | Set this option to **Yes** if the rebuild process should completely clear the balance and new records, and re-create the balance from the beginning of time. |
| **Budget models**                         | Not applicable | If you selected to import budget amounts, enter the budget models to consolidate. |
    | **Budget rate type**                      | Not applicable | Enter the type of budget exchange rate. |

6. If you have different accounting currencies, use the fields on the **Currency translation** tab to configure the translation that is done during consolidation.

    | Field                      | Description |
    |----------------------------|-------------|
 | **Source legal entity**        | Select the legal entity that you're importing from. |
 | **Source accounting currency** | This default currency is the currency that is associated with the source legal entity that you selected in the **Source legal entity** field. |
 | **From** and **To accounts**       | Define the range of accounts to import from the source legal entity. |
    | **Exchange rate type**         | Select the type of exchange rate. Exchange rate types are assigned when you create a main account. For more information, see [Create a main account](tasks/create-main-account.md). |
| **Apply exchange rate from**   | Enter a date to apply the exchange rate that was effective on that date. Alternatively, enter the value that should be used as the exchange rate. |
| **Exchange rate**  | The default value depends on the type of exchange rate that you selected in the **Exchange rate type** field. If you entered a user-defined exchange rate, you can define a rate. |

7. Set the **Run in background** option to **Yes** to enable the import process to run in the background.
8. Set the **Batch Processing** option to **Yes** to run the consolidation as a batch job at a specific time. To run the consolidation immediately, select **OK**. 

The transactions and balances that were specified for consolidation in the subsidiaries are added to the appropriate accounts in the consolidated legal entity.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
