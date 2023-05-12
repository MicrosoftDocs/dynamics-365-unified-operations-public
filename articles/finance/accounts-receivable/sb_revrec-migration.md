---
# required metadata

title: Migrating revenue recognition schedules to revenue and expense deferrals
description: This article provides information about migrating data from revenue recognition revenue schedules to revenue and expense deferrals deferral schedules
author: msftbrking
ms.date: 05/12/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 539093
ms.search.region: Global
# ms.search.industry: 
ms.author: brking
ms.search.validFrom: 2021-11-05
ms.dyn365.ops.version: 10.0.34

---

# Migrating revenue recognition schedules to revenue and expense deferrals

This topic will detail how to move in-process Revenue recognition **Revenue schedules** to Revenue and expense deferrals **Deferral schedules.** 

For example, a revenue schedule that was configured by fiscal period with even amounts starting on January 1 has been recognized through June 30. 
1. Export Revenue recognition entity **Deferred line (RevRecDeferredLineEntity)**
2. Import the data into Revenue and expense deferrals entity **Subscription billing deferral table (SubBillDeferralScheduleTableEntity).** The below table illustrates how the fields can be mapped to each other.

| Subscription billing deferral table | Deferred line                | Notes                                                                                                                      |
|-------------------------------------|------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| Deferral schedule number            |                              | Can specify own number, or copy Sales order number which was the revenue schedule number in Revenue recognition.           |
| Schedule type                       |                              | Straight line or event-based                                                                                               |
| Description                         | Revenue schedule description |                                                                                                                            |
| Deferral account                    | Deferred revenue account     | Will need to match the dimension structure for integrating applications. Empty dimensions will need to show with delimeter |
| Recognition Account                 | REVACCOUNT                   | Will need to match the dimension structure for integrating applications. Empty dimensions will need to show with delimiter |
| Recognition type                    |                              | Credit for revenue schedules, Debit for consumption                                                                        |
| Date                                | Date of invoice              |                                                                                                                            |
| Start date                          |                              | Deferral start date                                                                                                        |
| End date                            |                              | Deferral end date                                                                                                          |


The newly imported deferral schedules will need to be Stubbed to the date which they were previously recognized in revenue recognition. In the example, this date is June 30. The stubbing option is used to set the January – June periods as stubbed to prevent recognition for periods recognized through the Revenue schedule. 
3. This is done through the **Recognition processing** periodic task (Subscription billing – Revenue and expense deferrals – Periodic tasks – Recognition processing). 
4. Use Recognition action = Stub and set the Cutoff date = 6/30/2023. Fitlers can be used to filter deferral schedules to stub.
5. Click Process. We should see a notification that Schedule lines processed: 6.
6. Review the deferral schedule and observe the first 6 periods are marked as stubbed.






