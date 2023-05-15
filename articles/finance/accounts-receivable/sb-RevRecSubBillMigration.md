---
# required metadata

title: Migrate Revenue recognition to Subscription billing
description: This article provides information about migrating in progress Revenue recognition schedules to Revenue and expense deferral Deferral schedules.
author: msftbrking
ms.date: 05/15/2023
ms.topic: how-to
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
# Migrate Revenue recognition to Subscription billing

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)] 
 
 ## Migrate in-process revenue schedules to a deferral schedule in Revenue and expense deferrals

This article describes how to move in-process Revenue recognition **Revenue schedules** to Revenue and expense deferrals **Deferral schedules.**

For example, a revenue schedule configured by fiscal period with even amounts starting on January 1 and has been recognized through June 30.

1.  Export Revenue recognition entity **Deferred line (RevRecDeferredLineEntity)**.
2.  Import the data into the Revenue and expense deferrals entity **Subscription billing deferral table (SubBillDeferralScheduleTableEntity)**. The below table illustrates how the fields can be mapped to each other.

| Subscription billing deferral table | Deferred line                | Notes                                                                                                                      |
|-------------------------------------|------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| Deferral schedule number            |                              | Specify number, or copy Sales order number, which was the revenue schedule number in Revenue recognition.               |
| Schedule type                       |                              | Straight line or event-based                                                                                               |
| Description                         | Revenue schedule description |                                                                                                                            |
| Deferral account                    | Deferred revenue account     | This needs to match the dimension structure for integrating applications. Empty dimensions need to show with a delimeter. |
| Recognition Account                 | REVACCOUNT                   | This needs to match the dimension structure for integrating applications. Empty dimensions need to show with a delimiter. |
| Recognition type                    |                              | Credit for revenue schedules and debit for consumption.                                                                        |
| Date                                | Date of invoice              |                                                                                                                            |
| Start date                          |                              | Deferral start date                                                                                                        |
| End date                            |                              | Deferral end date                                                                                                          |

The newly imported deferral schedules need to be Stubbed to the date which they were previously recognized in revenue recognition. In this example, this date is June 30. The stubbing option is used to set the January – June periods as stubbed to prevent recognition for periods already recognized through the **Revenue schedule**.

3. On the **Revenue and expense deferrals** page, click **Periodic tasks** and **Recognition processing**.
4. In the **Recognition** field, select **Stub**. 
5. In the **Cutoff date** field, enter 6/30/2023. Filters can be used to filter deferral schedules to stub.
6. Click **Process**. A notification will display **Schedule lines processed: 6**.
7. Review the deferral schedule and observe the first six periods are marked as stubbed.
