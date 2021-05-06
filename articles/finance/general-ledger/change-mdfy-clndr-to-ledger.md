---
# required metadata

title: Change or reassign a ledger calendar 
description: This topic walks through the process of changing the calendar assigned to a ledger, or assinging an new calendar to the ledger.  
author: kweekley
ms.date: 05/07/2021
ms.topic: index-page
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
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

This topic walks through the process of changing the calendar assigned to a ledger, or assinging an new calendar to the ledger. 

## Issue

At some point in a company’s development, there could arise a situation where they will need to change or modify the calendar assigned to their ledger. How do I change/modify a calendar assigned to my Ledger?

During a company’s development, it’s likely that a situation will arise where they’ll need to change the calendar assigned to their ledger, or assign a different calendar. How is this done? 

## Resolution

There are two scenarios for changing or reassigning a calendar. The first scenario involves making changes to an existing calendar assigned to the Ledger. The second scenario involves creating a new calendar and assigning it to the ledger.  Note that either change be done at any time, even after transactions are posted to the ledger. 

### Modify an existing fiscal calendar

To modify a calendar already assigned to your ledger, navigate to **General ledger > Ledger setup > Ledger** and click on the hyperlink for the fiscal calendar. This take you to the **Ledger calendars** page. 

There are limits to the changes that can be made to a calendar.  For example, you can change the start and end dates of the *periods* within a year, but the start and end date of a *year* within the calendar cannot be changed.  To change the periods, first select the appropriate calendar and year, then use the **Delete period** and **Divide period** buttons.  First delete some or all the existing operating periods.  All the Operating periods can be deleted, except for the first period. Then divide the one remaining period into the new periods by entering the appropriate start date for the next period. 

If any changes are made to the fiscal periods with the calendar, you must run the “Recalculate ledger periods” process in every legal entity that is assigned that calendar. At this time, we don’t even present a warning message to run the Recalculation, but it is required.

To do this, click on the ** Recalculate ledger periods** menu button on the **Ledger setup** page in each company.  This is required in order to update the period assigned to each posted transaction within General ledger.  If the Recalculate process isn’t run, you could see transaction balances included in periods incorrectly on the trial balance or financial statements. If this has happened, you can correct the balances any time by running the Recalculate process. 

### Assign new fiscal calendar

Assigning a new fiscal calendar is a relatively simple process. First, open the **Ledger** page (**General ledger > Ledger setup > Ledger**).  Click the **Edit** button to enable edit-mode for this page. Next click the **Fiscal calendar** drop-down list to select a new fiscal calendar.

After changing the Fiscal calendar is changed for a ledger, the “Recalculate ledger periods” process must be run.  A message will remind you to complete this task.  Even though the message appears to be an optional step, it is not.  To do this, click the **Recalculate ledger periods** menu button on the **Ledger setup** page.  Recalculating the ledger periods will update the period assigned to each posted transaction within General ledger.  If the recalculate process isn’t run, transaction balances might appear in periods incorrectly on the trial balance or financial statements. If this has happened, you can correct the balances by running the Recalculate ledger period process at any time.

