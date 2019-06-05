---
# required metadata

title: Tax journal
description:  This topic includes information about Indis GST Whitepaper in Microsoft Dynamics 365 for Finance and Operations.
author: EricWang
manager: RichardLuan
ms.date: 06/05/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: 
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: EricWang
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.4

---

# Tax journal

The tax journal lets you post a tax adjustment journal.
In the case of reverse charge transactions, where the tax credit should be claimed after the authority settlement, the tax journal lets you claim the tax credit.

1. Click **Tax > Journals entries > Tax journals**.
2. Create a record.
3. In the **Date** field, enter a value.
4. On the **Tax journal lines** FastTab, click **Add**.
5. On the **Tax account** FastTab, in the **Account type** field, select **Tax**.
6. In the **Tax type** field, select **GST**.
7. In the **Tax component** field, select a value.
8. In the **Tax posting type** field, select **Interim recoverable**.
9. In the **Account** field, select a value.
10. In the **Offset account type** field, select **Tax**.
11. In the **Tax type** field, select **GST**.
12. In the **Tax component** field, select a value.
13. In the **Tax posting type** field, select **Tax recoverable**.
14. In the **Account** field, select a value.
15. On the journal line, in the **Credit** field, enter a value
16. Click **Tax information**.
17. Click the **GST** tab
18. Click OK.
19. Click **Tax document**
20. Click Close.
21. Click Post.
22. Close the message
23. Click Voucher
