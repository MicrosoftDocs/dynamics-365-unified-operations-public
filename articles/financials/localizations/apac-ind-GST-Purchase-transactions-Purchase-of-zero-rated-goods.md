---
# required metadata

title: Purchase of zero-rated goods
description:  This topic includes information about Indis GST Whitepaper in Microsoft Dynamics 365 for Finance and Operations.
author: EricWang
manager: RichardLuan
ms.date: 06/04/2019
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

# Purchase of zero-rated goods

1. Click **Accounts payable > Purchase orders > All purchase orders**
2. Create a purchase order for a zero-rated item.
3. Save the record.
4. Click **Tax information**.
5. Click the **GST** tab.
6. Click **OK**

### Validate the tax details

7. On the **Action** Pane, on the **Purchase** tab, in the **Tax** group, click **Tax document**.
8. Verify that the **Tax computed** field is set to 0.00.
9. Click **Close**.
10. Click **Confirm**.

### Post the purchase invoice

11. On the **Action** Pane, on the **Invoice** tab, in the **Generate** group, click **Invoice**.
12. In the **Default quantity for lines** field, select **Ordered quantity**.
13. Enter the invoice number.
14. On the **Action** Pane, on the **Vendor invoice** tab, in the **Actions** group, click **Post > Post**.
15. On the **Action** Pane, on the **Invoice** tab, in the **Journals** group, click **Invoice**. Then, on the **Overview** tab, click **Voucher**.

![](media/Annotation-2019-05-16-095042.png)



