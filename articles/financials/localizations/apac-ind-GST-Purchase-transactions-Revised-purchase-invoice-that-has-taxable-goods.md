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

## Revised purchase invoice that has taxable goods

1. Click **Accounts payable > Purchase orders > All purchase orders**.
2. Create a purchase order for a taxable item

### Validate the tax details

3. On the Action Pane, on the **Purchase** tab, in the **Tax** group, click **Tax document**.
4. On the **Tax details** FastTab, review the tax calculation.

Example:

- Line amount: 10,000.00
- CGST: 10 percent
- SGST: 10 percent
- CESS: 1 percent

5. Click **Close**.
6. Click **Confirm**.

### Post the purchase invoice

7. On the Action Pane, on the **Invoice** tab, in the **Generate** group, click **Invoice**.
8. In the **Default quantity for lines** field, select **Ordered quantity**.
9. On the **Lines** FastTab, enter the invoice number.
10. In the **Invoice type** field, select **Revised**.
11. In the **Original invoice number** field, select a value.
12. Verify that the **Original invoice date field** is automatically set, based on the original invoice number that you selected.
13. On the Action Pane, on the **Vendor invoice** tab, in the **Actions** group, click **Post > Post**.
14. On the Action Pane, on the **Invoice** tab, in the **Journals** group, click **Invoice**. Then, on the Overview tab, click Voucher.

![](media/GST-Whitepaper/Annotation-2019-05-16-103252.png)



