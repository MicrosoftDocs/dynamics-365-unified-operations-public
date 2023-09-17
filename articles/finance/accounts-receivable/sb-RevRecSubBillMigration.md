---
# required metadata

title: Migrate Revenue recognition to Subscription billing
description: This article explains how to move in-progress revenue schedules in Revenue recognition to deferral schedules in Revenue and expense deferrals.
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

This article describes how to move in-progress *revenue schedules* in Revenue recognition to *deferral schedules* in Revenue and expense deferrals.

## Migrate in-progress revenue schedules to deferral schedules in Revenue and expense deferrals

For this example, a revenue schedule is configured by fiscal period. It has even amounts from January 1 and has been recognized through June 30.

1. Export the **Deferred line (RevRecDeferredLineEntity)** Revenue recognition entity.
2. Import the data into the **Subscription billing deferral table (SubBillDeferralScheduleTableEntity)** Revenue and expense deferrals entity. The following table shows how the fields can be mapped to each other.

    | Subscription billing deferral table | Deferred line                | Notes |
    |-------------------------------------|------------------------------|-------|
    | Deferral schedule number            |                              | Specify the number, or copy the sales order number, which was the revenue schedule number in Revenue recognition. |
    | Schedule type                       |                              | Straight line or event-based. |
    | Description                         | Revenue schedule description | |
    | Deferral account                    | Deferred revenue account     | The value must match the dimension structure for integrating applications. Empty dimensions must be shown with a delimiter. |
    | Recognition Account                 | REVACCOUNT                   | The value must match the dimension structure for integrating applications. Empty dimensions must be shown with a delimiter. |
    | Recognition type                    |                              | Credit for revenue schedules and debit for consumption. |
    | Date                                | Date of invoice              | |
    | Start date                          |                              | The deferral start date. |
    | End date                            |                              | The deferral end date. |

    The newly imported deferral schedules must be stubbed to the date when they were previously recognized in Revenue recognition. In this example, that date is June 30. The stubbing option is used to set the periods for January through June as stubbed, to help prevent recognition for periods that were already recognized through the revenue schedule.

3. On the **Revenue and expense deferrals** page, select **Periodic tasks** and then **Recognition processing**.
4. In the **Recognition** field, select **Stub**. 
5. In the **Cutoff date** field, specify June 30, 2023. You can use filters to find deferral schedules to stub.
6. Select **Process**. You receive the following notification: "Schedule lines processed: 6."
7. Review the deferral schedule, and notice that the first six periods are marked as stubbed.
