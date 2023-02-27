---
# required metadata

title: Change or reassign a ledger calendar
description: This article explains how to change the calendar that is currently assigned to a ledger, and how to assign a new calendar to the ledger.
author: kweekley
ms.date: 02/07/2023
ms.topic: index-page
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2021-5-07
ms.dyn365.ops.version: 10.0.14

---

# Change or reassign a ledger calendar

[!include [banner](../includes/banner.md)]

This article explains how to change the calendar that is currently assigned to a ledger, and how to assign a new calendar to the ledger.

## Issue

Sometime, companies must either change the existing calendar that is assigned to a ledger or assign a new calendar.

## Resolution

There are two scenarios for changing or reassigning a ledger calendar. The first scenario involves changing an existing calendar that is already assigned to the ledger. The second scenario involves creating a new calendar and assigning it to the ledger. Both changes can be done at any time, even after transactions have been posted to the ledger.

### Change an existing fiscal calendar

To change an existing calendar that is assigned to your ledger, go to **General ledger \> Ledger setup \> Ledger**, and select the link for the fiscal calendar to open the **Ledger calendars** page.

There are limits to the changes that can be made to a calendar. For example, you can change the start and end dates of the *periods* in a year if no transactions have been posted into the period. You also can't change the start and end dates of a *year* in the calendar.

To change the periods in a year, select the appropriate calendar and year. First, use the use the **Delete period** button to delete some or all of the existing operating periods. All operating periods except the first can be deleted. Then use the **Divide period** button to divide the remaining period or periods into new periods by entering an appropriate start date for the next period.

After you change the periods in a calendar, you must run the **Recalculate ledger periods** process in every legal entity (company) that the calendar is assigned to. Although no warning message reminds you to complete this step, the recalculation process is required to update the period that is assigned to each posted transaction in General ledger. To run the recalculation process, select **Recalculate ledger periods** on the **Ledger setup** page in each company.

If the recalculation process isn't run, transaction balances on a trial balance or on financial statements might be incorrectly included in periods. In this case, you can correct the balances at any time by running the recalculation process.

### Assign a new fiscal calendar

To assign a new fiscal calendar, go to **General ledger \> Ledger setup \> Ledger**, and select **Edit** to put the **Ledger** page into edit mode. Then, in the **Fiscal calendar** field, select a new fiscal calendar.

After you change the fiscal calendar for a ledger, you must run the **Recalculate ledger periods**. When you assign a new fiscal calendar to a ledger, a message reminds you to complete this step. Although the message might seem to indicate that the recalculation process is optional, it isn't. It's required to update the period that is assigned to each posted transaction in General ledger. To run the recalculation process, select **Recalculate ledger periods** on the **Ledger setup** page.

If the recalculation process isn't run, transaction balances on a trial balance or on financial statements might be incorrectly included in periods. In this case, you can correct the balances at any time by running the recalculation process.
