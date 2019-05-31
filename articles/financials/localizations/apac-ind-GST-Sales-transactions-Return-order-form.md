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

## Return order form

1. Click **Sales and marketing > Return orders > All return orders**.
2. Create a return order for a taxable item.
3. On the **Line details** FastTab, in the **Disposition code** field, select **Credit only**.
4. On the Action Pane, on the **Return order** tab, in the **Send** group, click **Return order**.
5. Click **OK**.
6. Close the form.

### Sales order form

7. Click **Accounts receivable > Sales orders > All sales orders**.
8. Select the record where the **Order type** field is set to **Returned order**.
9. On the Action Pane, on the **Sales order** tab, in the **Maintain** group, click **Edit**.
10. Click **Tax information**
11. Click the **GST** tab.
12. Click the **Customer tax information** tab

Note: The Tax information value is automatically set, based on the original sales order that the return order is created against.

13. Click OK.
14. On the Action Pane, on the **Sell** tab, in the **Tax** group, click **Tax document**.

Example:

- Taxable amount: 10,000
- CGST: 10 percent
- SGST: 10 percent
- CESS: 1 percent

15 Click Close.

### Post the invoice

16. On the Action Pane, on the **Invoice** tab, in the **Generate** group, click **Invoice**.
17. In the **Quantity** field, select **All**.
18. Click OK.
19. Click Yes to acknowledge the warning message.

### Validate the voucher

20. On the Action Pane, on the **Invoice** tab, in the **Journals** group, click **Invoice**.
21. Click **Voucher**.

Financial entry for the Credit only/Replace and scrap/Scrap disposition code

![](media/GST-Whitepaper/Annotation-2019-05-20-163321.png)

Financial entry for the Credit/Replace and credit disposition code

![](media/GST-Whitepaper/Annotation-2019-05-20-163405.png)