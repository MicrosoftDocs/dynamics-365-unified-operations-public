---
# required metadata

title: Add a lease
description: The describes the steps required to create a new lease and record information for it in Asset leasing.
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

# Add a lease (Preview)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

The describes the steps required to create a new lease and record information for it in Asset leasing.

1.	Open the Lease summary
2.	Click on New in the toolbar.
3.	Input the lease information in each field.

Fields that are required are set off with red borders. The following table describes each field. 

*Insert table here*

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

1.	Click **Liability amortization schedule**.
2.	Exit the amortization schedule and **Asset depreciation schedule**.
be 3.	Exit the depreciation schedule and click **Initial recognition** to create the initial recognition journal entry. A prompt that shows that the journal has been created will displayed.

> [!Note]
> The journal entry is not posted to General ledger until the user manually "posts" the entry.

4.	Click **Asset leasing journal** to view and post the proposed initial recognition entry.

> [!Note]
> Asset leasing journal is only created automatically from lease schedules.

Now you can view the initial recognition journal entry before posting.	Click **Post** to recognize the right-of-use asset and lease liability in General ledger.



