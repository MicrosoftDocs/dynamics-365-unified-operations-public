---
# required metadata

title: Add a lease
description: This topic describes the steps required to create a new lease by entering information for it in Asset leasing, or by copying information from an existing lease.
author: moaamer
manager: Ann Beebe
ms.date: 07/28/2020
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
ms.author: vstehman
ms.search.validFrom: 2020-07-28
ms.dyn365.ops.version: 10.0.14

---

# Add or copy a lease (Preview)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic walks through the steps for creating a new lease in Asset leasing, as well as copying a lease. Creating a new lease involves entering information for the new lease and then creating a lease schedule. When you have at least one lease set up, you might find it easier to copy the information from an existing lease, and modify as needed to create a new lease. 

## Create a new lease

Complete the following steps to create a new lease in Asset leasing.

1.	Open the **Lease summary** page.
2.	Click **New** in the toolbar.
3.	Enter the lease information.

Fields that are required are set off with red borders in the product. 

## Create a lease schedule

After you've entered information for the lease, complete the following steps to create a lease schedule. 

> [!Note]
> The financial dimensions may change based upon any custom financial dimensions.

1. Once the lease information is entered, click **Create schedules**. This will generate the lease book(s), which will include the payment, amortization, depreciation, and expense schedules.
2. To access the lease books and view the newly created schedules, click the **Books** tab.
3. The **Book Details** page shows how the lease is being accounted for by the book(s) that has been allocated to it. From here, you can view the lease schedules.

   The payment schedule contains the inputs from the **Payment schedule lines** tab on the **Add Lease** page. You can still change each payment amount and variable payment. The measurement of the lease liability is calculated based on the modified payment schedule.

   After reviewing the payment schedule, click **Confirm schedule**. The lease won't be available for editing after the schedule is confirmed. 

> [!Note]
> The application automatically calculates the lease term from the payment schedule lines on the create lease form.

In order to calculate the lease term in months, the system will find the difference between the start date and the end date for a particular payment schedule line and will then move to the next payment schedule line, and find the difference again. Then the system sums all these amounts to determine the lease term in months.


In order to view the calculated period interest expenses go to **Liability amortization schedule**, to view calculated stright line depreciation go to **Asset depreciation schedule**, 

After revewing calculated amount you can go to **Initial recognition** to create the initial recognition journal entry. A prompt that shows that the journal has been created will displayed.

> [!Note]
> The journal entry is not posted to General ledger until the user manually "posts" the entry.

4.	Click **Asset leasing journal** to view and post the proposed initial recognition entry.

> [!Note]
> Asset leasing journal is only created automatically from lease schedules.

Now you can view the initial recognition journal entry before posting.	Click **Post** to recognize the right-of-use asset and lease liability in General ledger.

## Copy a Lease

Asset leasing lets you copy the details of a lease to create a new lease with the same information. You can change the lease fields before creating the schedules of the copied lease.

1. To copy a lease, select the lease to be copied from the **Lease summary** and select **Copy lease** in the top ribbon.

 > [!Note]
 > If the **Manual** parameter on the lease ID Number sequence is disabled, the copied lease will automatically generate the next number in the sequence to use for its lease ID. If this parameter is enabled, a message will be displayed that prompts you to enter the Lease ID before proceeding with copying the lease.
 
2. When you click **Copy**, the lease details from the selected lease will be copied over into a new lease where the user can edit the details before saving and creating the lease schedules.

## Asset leasing journal

All journal entries created in the Asset leasing module are contained in the Asset leasing journal (**Asset leasing > Journal entries> Asset leasing journal**). Use this page to filter by posting status, view specific journal entries and the vouchers, and post unposted journal entries.

To view all journal entries created through Asset leasing, go to (**Asset leasing > Journal entries> Asset leasing journal**).

> [!Note] 
> The asset leasing journal can't be created manually. Asset leasing journals are created automatically when lease schedules are created.
