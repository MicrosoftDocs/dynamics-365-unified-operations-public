---

title: Business performance analytics self help - Missing Fiscal Calendar for Budget
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

# Business performance analytics self help error

> [!NOTE]
> The functionality that's described in this article is available as part of a preview release. The functionality and the content of this article are subject to change. For more information about how to participate
> in the public preview for business performance analytics, contact <bpaquestions@service.microsoft.com>.

## Missing Fiscal Calendar for Budget: Error Code: ERR00002 [Type: Error] 
Missing Fiscal Calendar for Budget: Error Code: ERR00002 [Type: Error] 

Description: Error Code ERR00002 occurs when there is an issue, which is documented in the BPA_SelfHelp_Log table. This issue arises when transaction dates in Budget transaction lines within D365 Finance do not align with the respective fiscal calendar in the ledger. This misalignment results in the transaction within the Budget fact being linked to an accounting date key of -1. 

Resolution Steps: 

To address this error, follow these steps: 

Include calendar years/periods from the minBudgetTransactionDate to the maxBudgetTransactionDate for the relevant Fiscal calendars. 

Retrieve the details for the Fiscal calendar, minBudgetTransactionDate, and maxBudgetTransactionDate from the BPA_SelfHelp_Log table. You can locate these details in the LogDetails column.  

Refer to the sample record below to understand how to extract these details  

 

Sample record 

1 records in BudgetTransactionLine have TransactionDate outside of the Fiscal Calendar - [Row(b9d140ec-7227-4942-b20f-b0e0a3012d41_mserp_calendarid='Fiscal', fiscalCalendarStartDate='2014-01-01 00:00:00', fiscalCalendarEndDate='2025-12-31 00:00:00', cae61f4c-c088-4bc4-b600-c5bd07f1af3d_mserp_name='USMF', minBudgetTransactionDate='2026-01-01 00:00:00', maxBudgetTransactionDate='2026-02-01 00:00:00')] 

 

Steps to Rectify: 

Note: Before proceeding, ensure you have the necessary permissions to make changes to the fiscal calendar. 

In D365 Finance, navigate to F&O Modules > General ledger > Calendars > Fiscal Calendar. 

From the dropdown menu, choose the fiscal calendar that requires the addition of a new year. This should be the same calendar that corresponds to the reported issue. 

Within the chosen fiscal calendar, locate the option to '+ New Year' and click on it. 

A dialogue box or form will appear, prompting you to input details for the new fiscal year.Specify the relevant information, such as the fiscal year's starting and ending dates. In this case, make sure the new fiscal year includes the months of January and February (as mentioned in the minBudgetTransactionDate and maxBudgetTransactionDate). 

Ensure that the date range for the new fiscal year accurately covers the required periods. 

Once you've provided the necessary details, save the new fiscal year entry. 

Important Notes: 

Adding a new year in the past is not feasible within the system; only future years can be created. This means that if you have transactions posted in a year before the calendar's starting year, you cannot insert a new year within the existing fiscal calendar. 

When dealing with fiscal calendar issues, you have two options: create a new calendar or stick with the current one. Keeping the current calendar might lead to transactions not matching your reporting periods, causing reporting problems and making historical comparisons difficult. You might need to make adjustments, which can complicate audits. To decide, consider how much the misaligned data will affect your reporting and costs. Work with experts and teams to make the best choice for your organization's needs.When the fix is successfully implemented, the transactions that were previously misaligned will now map to the appropriate accounting date key, ensuring accurate financial processing and reporting. 

By following these steps, you'll be able to add a new fiscal year to the relevant calendar and resolve the issue related to misaligned transaction dates. 
