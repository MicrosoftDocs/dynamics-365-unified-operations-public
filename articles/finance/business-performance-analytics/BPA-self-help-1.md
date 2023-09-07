---

title: Business performance analytics self help - Missing fiscal calendar for general ledger 
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

# Business performance analytics error - Missing fiscal calendar for general ledger 

> [!NOTE]
> The functionality that's described in this article is available as part of a preview release. The functionality and the content of this article are subject to change. For more information about how to participate in the public preview for business performance analytics, contact <bpaquestions@service.microsoft.com>.

## Missing fiscal calendar for GL: Error Code: ERR00001 [Type:Error] 

Error Code ERR00001 occurs when the BPA_SelfHelp_Log table registers an issue. When the accounting dates in the General journal entries table in Dynamics 365 Finance don't align with corresponding fiscal
calendar in the ledger. This mismatch causes transactions in the generalledgerfact to be linked to an accounting date key of -1, which affects the accuracy of your reports. 

### Resolution  
To address this error, include calendar years/periods from the minAccountingDate to the maxAccountingDate for the relevant Fiscal calendars. Fiscal calendar, minAccountingDate, and maxAccountingDate are located in the BPA_SelfHelp_Log table, specifically under the LogDetails column. 

See the sample record below to understand how to extract these details: 
1 records in GeneralJournalEntry have AccountingDate outside of the Fiscal Calendar - [Row(a67d3eda-1b93-48dd-b561-a87120983889_mserp_calendarid='Fiscal', fiscalCalendarStartDate='2014-01-01 00:00:00', fiscal
CalendarEndDate='2025-12-31 00:00:00', 76f242a5-15cf-416c-89ef-3c1590107d7d_mserp_name='USMF', minAccountingDate='2026-01-15 00:00:00', maxAccountingDate='2026-02-15 00:00:00')]” 

Follow the steps below in Dynamics 365 Finance to add a new fiscal year: 
1. Go to **General ledger > Calendars > Fiscal calendar**.
2. Select the relevant calendar from the dropdown list.
3. Click **+ New Year** to create a new fiscal year. 

>[!IMPORTANT]
> Adding a new year in the past isn’t possible, this can only be done for future years. If there are transactions posted in a year before the calendar's starting year, a new year can't be created within the existing fiscal calendar.  

After the fix is complete, these transactions will map to appropriate accounting date key. 
 
