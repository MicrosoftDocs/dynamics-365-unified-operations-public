---
# required metadata

title: Create a tax journal
description:  This topic provides information about creating a tax journal.
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
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: EricWang
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.4

---

# Create a tax journal

You can use a tax journal to post a tax adjustment journal. In the case of reverse charge transactions where the tax credit should be claimed after the authority settlement, you can use a tax journal to claim the tax credit.

1. Click **Tax** \> **Journals entries** \> **Tax journals** and create a new record.
2. In the **Date** field, enter a value.
3. On the **Tax journal lines** FastTab, click **Add**, and on the **Tax account** FastTab, in the **Account type** field, select **Tax**.
4. In the **Tax type** field, select **GST**.
5. In the **Tax component** field, select a value, and in the **Tax posting type** field, select **Interim recoverable**.
6. In the **Account** field, select a value, and in the **Offset account type** field, select **Tax**.
7. In the **Tax type** field, select **GST**, and in the **Tax component** field, select a value.
8. In the **Tax posting type** field, select **Tax recoverable**.
9. In the **Account** field, select a value.
10. On the journal line, in the **Credit** field, enter a value, and then click **Tax information**.
11. On the **GST** tab, click **OK** and then click **Tax document**
12. Click **Close**, and then click **Post**.
13. Close the message and then click **Voucher**.
