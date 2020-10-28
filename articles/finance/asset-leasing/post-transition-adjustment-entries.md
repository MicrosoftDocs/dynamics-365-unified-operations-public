---
# required metadata

title: Post transition adjustment journal entries
description: This topic explains how to post transition adjustments to a lease portfolio so that they comply with the new lease accounting standards, Accounting Standards Codification Topic 842 (ASC 842) and International Financial Reporting Standard 16 (IFRS 16).
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

# Post transition adjustment journal entries

[!include [banner](../includes/banner.md)]

This topic explains how to transition adjustments to a lease portfolio so that they adhere to the new lease accounting standards: Accounting Standards Codification Topic 842 (ASC 842), which is the standard in Generally Accepted Accounting Principles in the US (US GAAP), and International Financial Reporting Standard 16 (IFRS 16).

For a full review of the transition methods, see [Transition methods](transition-methods.md). For information about how to set up a book for the transition to the new standards, see [Set up lease books](set-up-lease-books.md).

When you create a transition adjustment journal entry, it's reflected on your balance sheet. The balance sheet is updated to reflect the changes that are made to the lease, based on the new standards. The appropriate asset account is debited for the carrying amount on that date, and the liability account is credited. The difference is either debited or credited to retained earnings.

To post a transition adjustment in a manner that complies with the new accounting standards, follow these steps.

1. On the **Lease summary** page, select the lease, and then select **Books**.
2. In the book, select **Payment schedule**.
3. Select **Confirm**, and then close the payment schedule.
4. Select **Transition adjustment**.

    > [!NOTE]
    > A transition adjustment entry can be created only for lease books that are assigned to a book where the **Transition book** field is turned on. Additionally, if the value of the **Lease commencement** field is later than the transition date, the **Transition adjustment** field will be blank.

5. To view the journal entry, select **General journals**.
6. Select the new journal, and then select **Post**.
