---

title: Business performance analytics self help - Missing fiscal calendar for budget
description: This article provides information about common errors in business performance analytics.
author: jinniew
ms.author: jiwo
ms.reviewer: twheeloc 
ms.date: 09/09/2023
ms.topic: welcome
ms.prod: 
ms.technology:
ms.custom:
ms.search.form: business-performance-analytics
audience: Application User
---

# Business performance analytics self help error - Missing fiscal calendar for budget

> [!NOTE]
> The functionality that's described in this article is available as part of a preview release. The functionality and the content of this article are subject to change. For more information about how to participate in the public preview for business performance analytics, contact <bpaquestions@service.microsoft.com>.

## Missing fiscal calendar for budget: Error code: ERR00002 [Type: Error] 
Error Code ERR00002 occurs when the BPA_SelfHelp_Log table registers an issue. When the transaction dates in Budget transaction lines within Dynamics 365 Finance don't align with the respective fiscal calendar in the ledger. This misalignment results in the transaction in the Budget fact being linked to -1. 

### Resolution
To address this error, include calendar years/periods from the minBudgetTransactionDate to the maxBudgetTransactionDate for the relevant Fiscal calendars. Fiscal calendar, minBudgetTransactionDate, and maxBudgetTransactionDate are located in the BPA_SelfHelp_Log table. You can locate these details in the LogDetails column.  

See the sample record below to understand how to extract these details:

1 records in BudgetTransactionLine have TransactionDate outside of the Fiscal Calendar - [Row(b9d140ec-7227-4942-b20f-b0e0a3012d41_mserp_calendarid='Fiscal', fiscalCalendarStartDate='2014-01-01 00:00:00', fiscalCalendarEndDate='2025-12-31 00:00:00', cae61f4c-c088-4bc4-b600-c5bd07f1af3d_mserp_name='USMF', minBudgetTransactionDate='2026-01-01 00:00:00', maxBudgetTransactionDate='2026-02-01 00:00:00')] 

>[!NOTE]
>Confirm you have the necessary permissions to make changes to the fiscal calendar. 

1. In Dynamics 365 Finance, go to **General ledger > Calendars > Fiscal calendar**.
2. From the dropdown menu, select the fiscal calendar that requires the addition of a new year. This should be the same calendar that corresponds to the reported issue.
3. Within the chosen fiscal calendar, click **+ New year**.
4. Enter the details for the new fiscal year. Specify the relevant information, such as the fiscal year's starting and ending dates. In this case, make sure the new fiscal year includes the months of January and February (as mentioned in the minBudgetTransactionDate and maxBudgetTransactionDate).
5. Confirm that the date range for the new fiscal year accurately covers the required periods.
6. Save the new fiscal year entry. 

>[!IMPORTANT]
> Adding a new year in the past isn’t possible, this can only be done for future years. If there are transactions posted in a year before the calendar's starting year, a new year can't be created within the existing fiscal calendar. 

There are two options to fix fiscal calendar issues: 
1. Create a new calendar
2. Keep the current calendar

Keeping the current calendar might lead to transactions that don't match your reporting periods, causing reporting problems and making historical comparisons difficult. You might need to make adjustments that can complicate audits. Consider how much the misaligned data will affect reporting and costs. Work with experts and teams to make the best choice for your organization's needs. When the fix is successfully implemented, transactions that were previously misaligned will now map to the appropriate accounting date key, ensuring accurate financial processing and reporting. 

After completing these steps, a new fiscal year will be added to the relevant calendar and resolve issues related to misaligned transaction dates. 
