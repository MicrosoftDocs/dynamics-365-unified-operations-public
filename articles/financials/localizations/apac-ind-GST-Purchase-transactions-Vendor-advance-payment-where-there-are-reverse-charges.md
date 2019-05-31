---
# required metadata

title: Indis GST Whitepaper
description:  This topic includes information about Indis GST Whitepaper in Microsoft Dynamics 365 for Finance and Operations.
author: EricWang
manager: RichardLuan
ms.date: 05/31/2019
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

## Vendor advance payment where there are reverse charges

1. Click **Accounts payable > Payments > Vendor Payment journal**.
2. Create a record.
3. In the **Name** field, select a value.
4. Click **Lines**.
5. Create a vendor advance payment journal.
6. Save the record.
7. Click **Tax information**.
8. On the **GST** tab, in the **HSN code** field, select a value.
9. Click the **Vendor tax information** tab.
10. Click OK.

### Validate the tax details

11. On the Action Pane, on the **Purchase** tab, in the **Tax** group, click **Tax document**.

Example:

- CGST: 10 percent
- SGST: 10 percent
- CESS: 1 percent
- Reverse charge percentage: 70 percent for all the three components

12. Click **Close**.
13. Click **Post > Post**.
14. Close the message.

### Update the transaction ID

15. Click **Functions > GST transaction Id**.
16. In the **Date** field, enter a value.
17. In the **Text** field, enter a value.
18. Click **Close**.

### Validate the financial entries
19. Click **Inquiries > Voucher**.

![](media/GST-Whitepaper/Annotation-2019-05-16-113421.png)