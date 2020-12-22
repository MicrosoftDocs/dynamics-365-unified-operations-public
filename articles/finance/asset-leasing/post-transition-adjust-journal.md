---
# required metadata

title: Post transition adjustment journal entries in Asset leasing
description: This topic describes the functionality that lets you transition a lease portfolio to the new lease accounting standards, Accounting Standards Codification Topic 842 (ASC 842) and International Financial Reporting Standard 16 (IFRS 16).
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
# ms.search.scope: Core, Operations, Retail

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2020-10-28
ms.dyn365.ops.version: 10.0.14
---

# Post transition adjustment journal entries in Asset leasing

[!include [banner](../includes/banner.md)]

This topic describes the functionality that lets you transition a lease portfolio to the new lease accounting standards: Accounting Standards Codification Topic 842 (ASC 842), which is the standard in Generally Accepted Accounting Principles in the US (US GAAP), and International Financial Reporting Standard 16 (IFRS 16).

For information about how to set up a book for the transition to the new standards, see [Set up lease books](set-up-lease-books.md).

When you create a transition adjustment journal entry, a journal entry is generated. This entry reflects the balance sheet impact of recording the lease under the new standards on that date. The appropriate asset account is debited for the carrying amount on that date, and the liability account is credited. The difference is either debited or credited to retained earnings.

To post a transition adjustment in compliance with the new accounting standards, follow these steps.

1. On the **Lease summary** page, select the lease, and then select **Books**.
2. In the book, select **Payment schedule**.
3. In the **Payment schedule** dialog box, select **Confirm**. Then close the dialog box.
4. Select **Transition adjustment**.

    > [!NOTE]
    > A transition adjustment can be created only for lease books that are assigned to a book where the **Transition book** field is available. If the value in the **Lease commencement** field is later than the transition date, the value in the **Transition adjustment** field won't be updated.

5. To view the journal entry, select **Asset leasing journals**.
6. Select the new journal, and then select **Post**.
