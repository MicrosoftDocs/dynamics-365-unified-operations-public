---
title: Budget control account detail history report
description: This article provides information about the Budget control account detail history report. 
author: music727
ms.author: mibeinar
ms.topic: article
ms.date: 07/24/2024
ms.reviewer: twheeloc
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2021-11-28
ms.search.form: BudgetControlConfiguration
---

# Budget control account detail history report 

[!include [banner](../includes/banner.md)]

This article provides information about the **Budget control account detail history** report. This report lets users view budget account entries for the selected financial dimension and legal entity.

To generate the report, users select a financial dimension, a budget model, and a budget cycle time span that the organization uses. Selected dates should match the selected budget cycle. Alternatively, users can define a range of dates in the fiscal calendar that is associated with the budget cycle. Users can also select a range of specific accounts or all accounts.

## Filter the report 

When users generate the report, the following parameters are available.

| Field | Description |
| ----- | ----------- |
| **Dimension criteria** | Select a financial dimension set for the report. A financial dimension set is a named group of accounts or dimensions. It contains either account values for the account or dimension values for a single dimension. Examples include main accounts, departments, and cost centers, or combinations such as a cost center and main account, or a department and cost center. Financial dimension sets are defined on the **Financial dimension sets** page. |
| **Budget model** | Select a budget model. |
| **Budget cycle time span** | Select a budget cycle time span. |
| **Include carry-forward amounts** | Set this option to *Yes* to include budget amounts that were carried forward from a previous fiscal year.|
| **Dates to include** | Select either the **Budget cycle** option or the **Date range** option. |
| **Budget cycle** | If you selected the **Budget cycle** option, select the name of a budget cycle. In this case, the report includes the dates that are set up for the selected budget cycle on the **Budget cycle time spans** page. |
| **From date** | If you selected the **Date range** option, select the start date for the budget account entries to include on the report. The date must be in one of the fiscal years that are included in the fiscal calendar that was selected when the budget cycle time span was set up. For example, a fiscal calendar for a budget cycle includes fiscal years that have dates from January 1, 2020, through December 31, 2024. In this case, the **From date** value can't be before January 1, 2020.|
| **To date** | If you selected the **Date range** option, select the end date for the budget account entries to include on the report. The date must be in one of the fiscal years that are included in the fiscal calendar that was selected when the budget cycle time span was set up. For example, a fiscal calendar for a budget cycle includes fiscal years that have dates from January 1, 2020, through December 31, 2024. In this case, the **To date** value can't be after December 31, 2024.|
| **From account** | Select the first account in the range of accounts to include. |
| **To account** | Select the last account in the range of accounts to include. |

![Screenshot that shows the configuration parameters for generation of the Budget control account detail history report.](https://github.com/user-attachments/assets/99a7f195-d139-4a03-b282-308b7b6a5649)

> [!NOTE]
> You can specify additional report filters on the **Records to include** tab.
>
> If you select the **Company ID related to the budget model** field in the filter options, you can select the legal entity that you're running the report in. If you select another legal entity or multiple legal entities in the field, the report is empty, or it shows details only for the current legal entity that you're running the report in.
>
> To view the data for other organizations, run the report in the appropriate legal entity.

## Report structure

The data on the report is taken from the following sources:

- `BudgetAccountDetailHistoryDP.processReport` class instance method
- `BudgetAccountDetailTmpHistory` table
- `BudgetSourceTracking` table
- `BudgetSourceTrackingDetail` table
