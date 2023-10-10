---

title: Business performance analytics self-help error - Missing fiscal calendar for budget
description: This article provides information about the Missing fiscal calendar for budget error (error code ERR00002) in business performance analytics.
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

# Business performance analytics self-help error - Missing fiscal calendar for budget

> [!NOTE]
> The functionality that's described in this article is available as part of a preview release. The functionality and the content of this article are subject to change. For more information about how to participate in the public preview for business performance analytics, contact <bpaquestions@service.microsoft.com>.

## Missing fiscal calendar for budget: Error code: ERR00002 [Type: Error]

Error code *ERR00002* is logged in the `Transform Log` table in Microsoft Dataverse when the transaction dates on budget transaction lines in Dynamics 365 Finance aren't aligned with the corresponding fiscal calendar in the ledger. This misalignment causes the transaction in the Budget fact to be linked to an accounting date key of *-1*.

### Resolution

To address this error, include calendar years/periods from the `minBudgetTransactionDate` value through the `maxBudgetTransactionDate` value for the relevant Fiscal calendars. You can find the fiscal calendar, the `minBudgetTransactionDate` value, and the `maxBudgetTransactionDate` value in the `LogDetails` column of the `Transform Log` table.

Here's an example of a record:

> 1 records in BudgetTransactionLine have TransactionDate outside of the Fiscal Calendar - \[Row(b9d140ec-7227-4942-b20f-b0e0a3012d41_mserp_calendarid='Fiscal', fiscalCalendarStartDate='2014-01-01 00:00:00', fiscalCalendarEndDate='2025-12-31 00:00:00', cae61f4c-c088-4bc4-b600-c5bd07f1af3d_mserp_name='USMF', minBudgetTransactionDate='2026-01-01 00:00:00', maxBudgetTransactionDate='2026-02-01 00:00:00')\]

> [!IMPORTANT]
> Before you begin, confirm that you have the permissions that are required to make changes to the fiscal calendar.

1. In Dynamics 365 Finance, go to **General ledger** \> **Calendars** \> **Fiscal calendar**.
2. In the dropdown list, select the fiscal calendar that requires the addition of a new year. This calendar should be the calendar that corresponds to the reported issue.
3. In the selected fiscal calendar, select **New year**.
4. Enter the relevant information for the new fiscal year, such as the start and end dates. For this example, confirm that the new fiscal year includes the months of January and February (as specified in `minBudgetTransactionDate` and `maxBudgetTransactionDate`).
5. Confirm that the date range for the new fiscal year accurately covers the required periods.
6. Save the new fiscal year entry.

> [!IMPORTANT]
> You can't add a new year in the past. You can add only future years. If transactions were posted in a year before the calendar's start year, you can't create a new year in the existing fiscal calendar.

There are two options for fixing fiscal calendar issues:

- Create a new calendar.
- Keep the current calendar.

Keeping the current calendar might lead to a situation where transactions don't match your reporting periods. Therefore, it might cause reporting issues and make historical comparisons difficult. You might have to make adjustments that can complicate audits. When the fix is successfully implemented, transactions that were previously misaligned will be mapped to the appropriate accounting date key, and will therefore ensure accurate financial processing and reporting.

After you complete these steps, a new fiscal year is added to the relevant calendar and fixes issues that are related to misaligned transaction dates.
