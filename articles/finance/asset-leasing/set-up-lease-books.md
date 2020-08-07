---
# required metadata

title: Set up lease books
description: This topic describes the information that's maintained in lease books, which contain the accounting policies that determine how the lease is accounted for in the system.
author: moaamer
manager: Ann Beebe
ms.date: 07/20/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: TaxTable
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
ms.search.validFrom: 2020-07-20
ms.dyn365.ops.version: 10.0.13


---

# Set up lease books (Preview)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Lease books contain the accounting policies that determine how the lease is accounted for in the system. Asset leasing supports both US GAAP, ASC 842, and ASC 840, international standards IFRS 16 and IAS 17, in addition to cash basis accounting.

1. To create a lease book, go to **Asset leasing > Setup > Lease books**.
2. Select **New** to add a new book.
3. Enter information in the following fields as indicated in the following table.

|     Name                                        |     Description                                                                                                                                                                                                                                                                                                                                                                                       |
|-------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     Posting layer                               |     Select the desired posting layer to be used. Each book   that is attached to a lease is set up for a particular posting layer   that has different posting purposes.                                                                                                                                                                                                                 |
|     Lease type                                  |     Select whether the lease type will be classified automatically, or predefined as a Finance or Operating lease.                                                                                                                                                                                                                                                                   |
|     Accounting framework                        |     Select the framework that's associated with the book you're working with.                                                                                                                                                                                                                                                                                                                                  |
|     Lease term / Useful life Set Up             |     Enter the percentage of the useful life. The application will classify the lease as finance lease if it is set to automatic and if the if the lease term over the asset's useful life is greater than or equal to the percentage entered in this field.                                                    |
|     Present value / Asset fair value set up     |     Enter the value as a whole number to be used as the   threshold to determine the lease type. When the book’s lease classification   is set to automatic, if the present value of future minimum lease payments is   greater than the user defined value from the book setup form, the application   will classify the lease as finance.                                                           |
|     Short term threshold                        |     Enter the number of months to be used as a short term   lease threshold. If the lease term is less than or equal to the number of   months entered in this field, the lease will be classified as a short term   lease and the deferred rent treatment will be applied.                                                                                                                           |
|     Low value threshold                         |     Enter an amount to use as a low-value lease threshold. If the fair value of the asset equal or less than the value entered, the system will classify the lease as low-value, and the deferred rent treatment will be applied.                                                                                                                                   |
|     Pay to vendor                               |     Select Yes to allow payments to be posted directly to the   vendor account specified on each lease. When a payment invoice is posted, the   vendor account will be credited. If set to No, the account specified on the   Lease Posting Parameters page for Lease Payments will be credited instead.                                                                                              |
|     Transition book                             |     Select Yes if this book will be used to transition leases   from the old standard to the new standard. If you select No, all leases will   be accounted for using the full retrospective transition method.                                                                                                                                                                                       |
|     Transition type                             |     If the selected book is a transition book, select   transition method to use when posting the transition adjustment for the   lease. If the selected book is not a transition book, the transition type   will be Full retrospective by default.                                                                                                                                                  |
|     Transition date                             |     Enter the date of transition onto the new standard. This   will be the transition date used to post the transition adjustment. Depending   on the accounting framework and transition method, your company may need to   comparatively state the balance sheet prior to the transition date. Enter the   earliest comparative period as the transition date to accommodate this   requirement.    |
|     Incremental borrowing rate at transition    |     Enter the incremental borrowing rate present at the date   of transition. Based on the transition type, this rate will be used to   calculate the present value of future minimum lease payments. This field will   be inactive if the Incremental Borrowing Rate on Books is not checked.                                                                                                        |
