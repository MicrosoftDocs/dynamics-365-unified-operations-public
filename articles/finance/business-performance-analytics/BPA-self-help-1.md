---

title: Business performance analytics self-help error - Missing fiscal calendar for general ledger
description: This article provides information about the Missing fiscal calendar for general ledger error (error code ERR00001) in business performance analytics.
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

# Business performance analytics self-help error - Missing fiscal calendar for general ledger

> [!NOTE]
> The functionality that's described in this article is available as part of a preview release. The functionality and the content of this article are subject to change. For more information about how to participate in the public preview for business performance analytics, contact <bpaquestions@service.microsoft.com>.

## Missing fiscal calendar for GL: Error code: ERR00001 [Type: Error]

Error code *ERR00001* is logged in the `Transform Log` table in Microsoft Dataverse when the accounting dates in the General journal entries table in Dynamics 365 Finance aren't aligned with the corresponding fiscal calendar in the ledger. This misalignment causes transactions in `generalledgerfact` to be linked to an accounting date key of *-1*. Therefore, it affects the accuracy of your reports.

### Resolution

To address this error, include calendar years/periods from the `minAccountingDate` value through the `maxAccountingDate` value for the relevant fiscal calendars. You can find the fiscal calendar, the `minAccountingDate` value, and the `maxAccountingDate` value in the `LogDetails` column of the `Transform Log` table.

Here's an example of a record:

> 1 records in GeneralJournalEntry have AccountingDate outside of the Fiscal Calendar - \[Row(a67d3eda-1b93-48dd-b561-a87120983889_mserp_calendarid='Fiscal', fiscalCalendarStartDate='2014-01-01 00:00:00', fiscalCalendarEndDate='2025-12-31 00:00:00', 76f242a5-15cf-416c-89ef-3c1590107d7d_mserp_name='USMF', minAccountingDate='2026-01-15 00:00:00', maxAccountingDate='2026-02-15 00:00:00')\]

Follow these steps in Dynamics 365 Finance to add a new fiscal year.

1. Go to **General ledger** \> **Calendars** \> **Fiscal calendar**.
2. In the dropdown list, select the relevant calendar.
3. Select **New year** to create a new fiscal year.

> [!IMPORTANT]
> You can't add a new year in the past. You can add only future years. If transactions were posted in a year before the calendar's start year, you can't create a new year in the existing fiscal calendar.

After the fix is completed, the transactions will be mapped to the appropriate accounting date key.
