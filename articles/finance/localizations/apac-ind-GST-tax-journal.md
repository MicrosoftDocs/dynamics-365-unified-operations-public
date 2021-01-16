---
# required metadata

title: Create a tax journal
description: This topic explains how to create a tax journal.
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
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.4

---

# Create a tax journal

[!include [banner](../includes/banner.md)]

You can use a tax journal to post a tax adjustment journal. For reverse charge transactions where the tax credit should be claimed after the authority settlement, you can use a tax journal to claim the tax credit.

1. Go to **Tax** \> **Journals entries** \> **Tax journals**.
2. Create a record.
3. In the **Date** field, enter a value.
4. On the **Tax journal lines** FastTab, select **Add**.
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
15. On the journal line, in the **Credit** field, enter a value, and then select **Tax information**.
16. On the **GST** tab, select **OK**.
17. Select **Tax document**.
18. Select **Close**, and then select **Post**.
19. Close the message that you receive, and then select **Voucher**.
