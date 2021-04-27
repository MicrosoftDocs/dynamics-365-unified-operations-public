---
# required metadata

title: Confirm Asset leasing payment schedules in a batch
description: This topic explains how to confirm multiple payment schedules in a batch. 
author: moaamer
ms.date: 04/12/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: AssetLeasePaymConfirmationDetails
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2020-10-28
ms.dyn365.ops.version: 10.0.14
---

# Confirm Asset leasing payment schedules in a batch

[!include [banner](../includes/banner.md)]

This topic explains how to confirm multiple payment schedules in a batch. Payment schedules are confirmed either on a lease-to-lease basis or through the confirmation batch process. A journal entry can be posted only against a lease that has a confirmed payment schedule. Confirmation of the payment schedule serves as a final approval of the financial information for the lease. All future changes to the financial information for the lease, such as payments and the lease term, constitute a lease adjustment and should be processed in that way.

To confirm multiple payment schedules, follow these steps.

1. Go to **Asset leasing \> Periodic \> Confirmation batch**.
2. On the **Confirmation batch** page, select **Confirmation batch**.
3. In the dialog box that appears, filter for the books that you want to confirm.

    - To confirm all the books in a specific lease group, select the group in the **Lease group** field.
    - To confirm specific books, select the books in the **Book ID** field.
    - To confirm all books, turn on the **For all books** parameter.

Information for the newly confirmed books is shown on the **Confirmed books** page. After the payment schedules are confirmed, the initial recognition journal entries can be posted against the leases.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
