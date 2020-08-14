---
# required metadata

title: Post transition adjustment journal entries
description: 
author: moaamer
manager: Ann Beebe
ms.date: 08/14/2020
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
ms.search.validFrom: 2020-08-14
ms.dyn365.ops.version: 10.0.14
---

# Post transition adjustment journal entries

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic describes functionality that lets you transition a lease portfolio to the new accounting standards – US GAAP ASC 842 and IFRS 16.

For a full review of the transition methods, see [Transition methods](transition-methods.md). For information on how to setup a book to transition to the new standards, please review the [Set up lease books](set-up-lease-books.md).

When the user creates the transition adjustment journal entry, a journal entry will be generated to reflect the balance sheet impact of recording that lease under the new standards at that date. The appropriate asset account will be debited for the carrying amount at that date, and the liability account will be credited. The difference will be either debited or credited to retained earnings.

1. To post a transition adjustment in compliance with the new accounting standards, select the lease from the **Lease summary** page and click **Books**.
2. In the book, select **Payment schedule**.
3. Click **Confirm** and exit the **Payment schedule** dialog.
4. Click **Transition adjustment**.

 	> [!Note]
 	> A transition adjustment can be created only for lease books that are assigned to a book that has the **Transition book** field enabled. Also, if the value in the **Lease commencement** field is later than the transition date, then the entry in the **Transition adjustment** field won't be updated.
  
5.	To view the journal entry, select **General journals**.
6.	Select the new journal and click **Post**.
