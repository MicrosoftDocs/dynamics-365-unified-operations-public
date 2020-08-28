---
# required metadata

title: Post transition adjustment journal entries
description:  This topic describes the steps for posting transition adjustments to a lease portfolio that adhere to new accounting standards – US GAAP ASC 842 and IFRS 16.
author: moaamer
manager: Ann Beebe
ms.date: 08/10/2020
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
ms.search.validFrom: 2020-08-10
ms.dyn365.ops.version: 10.0.14
---

# Post transition adjustment journal entries

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic describes the steps for posting transition adjustments to a lease portfolio that adhere to new accounting standards – US GAAP ASC 842 and IFRS 16. For a full review of the transition methods, see [Transition methods](transition-methods.md). For information on how to set up a book to transition to the new standards, see [Setup lease books](https://review.docs.microsoft.com/en-us/dynamics365/finance/asset-leasing/set-up-lease-books?branch=bob-asset-leasing-setup).

When you create a transition adjustment journal entry, that entry will be reflected on your balance sheet. The balance sheet will now reflect the changes to the lease based on the new standards. The appropriate asset account will be debited for the carrying amount at that date and the liability account will be credited. The difference will be either debited or credited to retained earnings. When you create a transition adjustment journal entry, that entry will be reflected on your balance. The balance sheet will now reflect the changes to the lease based on the new standards. 

1.	To post a transition adjustment in compliance with the new accounting standards, select the lease from the **Lease summary** page and click **Books**.
2.	In the book, select **Payment schedule**.
3.	Click **Confirm** and exit the payment schedule.
4.	Click **Transition adjustment**.

> [!Note]
> Only those lease books assigned to a book with the **Transition book** field enabled will allow for a transition adjustment entry to be created. Also, if the **Lease commencement** field is later than the transition date then the **Transition adjustment** field won't be filled in.

5.	To view the journal entry, select **General journals**.
6.	Select the new journal and click **Post**.
