---
# required metadata

title: Add or copy leases (Preview)
description: This topic describes how to create a new lease by entering information for it in Asset leasing or copying information from an existing lease.
author: moaamer
manager: Ann Beebe
ms.date: 10/28/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations, Retail

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2020-10-28
ms.dyn365.ops.version: 10.0.14

---

# Add or copy leases (Preview)

[!include [banner](../includes/banner.md)]

This topic explains how to create a lease from scratch in Asset leasing, and also how to create a lease by copying an existing lease. The process for creating a lease from scratch involves entering information for the new lease and then creating a lease schedule. After at least one lease has been set up, you might find it easier to copy the information from an existing lease and then edit that information as you require to create a new lease.

## Create a lease

Follow these steps to create a lease in Asset leasing.

1. On the **Lease summary** page, on the Action Pane, select **New**.
2. Enter the lease information. Fields that are required have red borders.

## Create a lease schedule

After you've finished entering information for the lease, follow these steps to create a lease schedule.

> [!NOTE]
> The financial dimensions might change based on any custom financial dimensions.

1. Select **Create schedules** to generate the lease books. The lease books include the payment, amortization, depreciation, and expense schedules.
2. To access the lease books and view the newly created schedules, select the **Books** tab.

    The **Book details** page shows how the lease is accounted for by the books that have been allocated to it. From here, you can view the lease schedules.

    The payment schedule contains the inputs from the **Payment schedule lines** tab on the **Add lease** page. You can still change each payment amount and variable payment. The lease liability is calculated based on the modified payment schedule.

4. After you've finished reviewing the payment schedule, select **Confirm schedule**. After the schedule is confirmed, the lease is no longer available for editing.

    > [!NOTE]
    > The system automatically calculates the lease term from the payment schedule lines on the **Add lease** page.
    >
    > To calculate the lease term in months, the system finds the difference between the start date and the end date for a specific payment schedule line. It then moves to the next payment schedule line and finds the difference again. Finally, the system sums all the amounts to determine the lease term in months.

5. To view the calculated period interest expenses, open the **Liability amortization schedule** page. To view calculated straight-line depreciation, open the **Asset depreciation schedule** page.
6. After you've finished reviewing the calculated amount, you can create the initial recognition journal entry on the **Initial recognition** page. You receive a message that states that the journal has been created.

    > [!NOTE]
    > The journal entry isn't posted to General ledger until you manually post the entry.

7. To review the proposed initial recognition entry before you post it, select **Asset leasing journal**.

    > [!NOTE]
    > The Asset leasing journal can't be created manually. It's automatically created when lease schedules are created.

8. When you've finished reviewing the initial recognition journal entry and are ready to post it, select **Post** to recognize the right-of-use (ROU) asset and lease liability in General ledger.

## Copy a lease

Asset leasing lets you copy the details of a lease to create a new lease that has the same information. You can then change the lease fields before you create the schedules for the copied lease.

1. On the **Lease summary** page, select the lease to copy, and then, on the Action Pane, select **Copy lease**.

    > [!NOTE]
    > If the **Manual** parameter is turned off for the number sequence for lease IDs, the next number in the sequence is automatically generated as the lease ID of the copied lease. If the **Manual** parameter is turned on, you receive a message that prompts you to enter the lease ID before you proceed to copy the lease.

2. Select **Copy**. The lease details from the selected lease are copied to a new lease. You can then edit the details of the new lease before you save it and create the lease schedules.

## Asset leasing journal

All journal entries that are created in Asset leasing are contained in the Asset leasing journal. On the **Asset leasing journal** page (**Asset leasing \> Journal entries \> Asset leasing journal**), you can filter by posting status, view specific journal entries and the vouchers, and post unposted journal entries.

> [!NOTE]
> The Asset leasing journal can't be created manually. It's automatically created when lease schedules are created.
