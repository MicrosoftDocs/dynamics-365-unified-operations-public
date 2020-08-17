---
# required metadata

title: Confirm payment schedules in batch
description: This topic walks through the process of confirmaing multiple payment schedules in a batch. 
author: moaamer
manager: Ann Beebe
ms.date: 08/07/2020
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
ms.search.validFrom: 2020-08-07
ms.dyn365.ops.version: 10.0.14
---

# Confirm payment schedules in batch

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic walks through the process of confirmaing multiple payment schedules in a batch. Payment schedules are confirmed on a lease-to-lease basis or through the confirmation batch process. A journal entry can only be posted against a lease with a confirmed payment schedule. Confirming the payment schedule acts as a final approval of the financial information for the lease. All future changes of the financial information of the lease, such as payments and lease term, constitute a lease adjustment and should be processed as such.

1. To confirm multiple payment schedules, open the Confirmation batch** page (**Asset leasing > Periodic > Confirmation batch**).
2. Click **Confirmation batch**.
3. A parameter dialog will open. To filter which books to confirm, the user can select the specific lease group to confirm all the books of by selecting the group from the **Lease group** menu. In addition, the user can select specific books from the **Book ID** menu. To confirm all books, enable the **For all books** parameter. 
4. The newly confirmed books will populate the **Confirmed books** page. Once the payment schedules are confirmed, the initial recognition journal entries can be posted against the leases.
