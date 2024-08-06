---
title: Budget control account detail history report
TOCTitle: Budget control account detail history report
author: mibeinar
ms.date: 02/08/2024
---

# Budget control account detail history report 

[!include [banner](../includes/banner.md)]

This article provides information about the **Budget control account detail history** report which allows users to view budget account entries for the financial dimension and legal entity that has been select.

To generate this report, users should select a financial dimension, budget model, and budget cycle time span that are used by the organization. Selected dates should  either match the selected budget cycle or users can define a range of dates in the fiscal calendar that is associated with the budget cycle.
Users can also select a range of specific accounts or all accounts.



## Filter the data on this report

When this report is generated, the following default parameters are available:
| Field| Description |
| ------------------------- | -------------------------------- |
| **Dimension criteria** | Select a financial dimension set for the report which is defined in the *Financial dimension sets* form. A financial dimension set is a named group of accounts or dimensions that contains either account values for the account or dimension values for a single dimension. Examples include main accounts, departments, and cost centers, or combinations such as a cost center and main account, or a department and cost center. |
| **Budget model** | Select a budget model which is used by your organization. |
| **Budget cycle time span** | Select a budget cycle time span which is used by your organization. |
| **Include carry-forward amounts** | Select this check box to include budget amounts carried forward from a previous fiscal year.|
| **Dates to include**| Select either **Budget cycle** or **Date range**.|
|**Budget cycle**|If you selected **Budget cycle**, select the name of a budget cycle. This will use the dates that were set up for the selected budget cycle in the **Budget cycle time spans** form. |
|**From date**|	If you selected **Date range**, select the starting date for budget account entries to include in the report. This date must be in one or more of the fiscal years that are included in the fiscal calendar that was selected when the budget cycle time span was set up. For example, a fiscal calendar for a budget cycle includes fiscal years with dates from January 1, 2020 to December 31, 2024. The **From date** cannot be before January 1, 2020.|
|**To date**|If you selected **Date range**, select the ending date for budget account entries to include in the report. This date must be in one or more of the fiscal years that are included in the fiscal calendar that was selected when the budget cycle time span was set up. For example, a fiscal calendar for a budget cycle includes fiscal years with dates from January 1, 2020 to December 31, 2024. The **To date** cannot be after December 31, 2024.|
|**From account**|Select the first account in the range of accounts to include in the report.|
|**To account**|Select the last account in the range of accounts to include in the report.|

![image](https://github.com/user-attachments/assets/99a7f195-d139-4a03-b282-308b7b6a5649)

> [!NOTE]
> You can specify additional report filters in the **Records to include** tab.
> Please note, if you select field **Company ID related to the budget model** in the filter option, you will be able to select the legal entity in which you are running this report. 
If other legal entity or multiple legal entities are selected in this field, the report will be empty or will show details only for the current legal entity in which you are running the report.
> If you would like to see the data for other organization, you should run the report in the respective legal entity.

## Report structure

The data on this report is taken from the following sources:
- BudgetAccountDetailHistoryDP.processReport class instance metho
- BudgetAccountDetailTmpHistory table
- BudgetSourceTracking table
- BudgetSourceTrackingDetail table
