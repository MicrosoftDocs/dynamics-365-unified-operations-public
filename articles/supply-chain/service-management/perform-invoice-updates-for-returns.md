---
title: Perform invoice updates for returns
TOCTitle: Perform invoice updates for returns
ms:assetid: 2c24e50d-6446-4dfe-8c12-7f789b8229bc
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg231016(v=AX.60)
ms:contentKeyID: 36056253
ms.date: 04/18/2014
mtps_version: v=AX.60
_tocRel: gg230920(v=ax.60)/toc.json
---

# Perform invoice updates for returns 




A return order is a type of sales order that is marked as a returned order. Therefore, the **All sales orders** list page is used to generate invoices for return orders instead of the **Return orders** form. This Microsoft Dynamics AX functionality supports the business processes of organizations that choose to have return orders and sales orders invoiced at the same time and by the same person.

Because the invoice for a returned item is for a negative amount, it is called a credit note.

When you set up the invoice update for batch processing, the sales order of type **Returned order** must have a return line status of **Received**, which indicates that the order's packing slip has been updated.

## Post an invoice for a return order

1.  Click **Accounts receivable** \> **Common** \> **Sales orders** \> **All sales orders**.

2.  Select a sales order for which **Returned order** is displayed in the **Order type** field.

3.  On the Action Pane, on the **Invoice** tab, in the **Generate** group, click **Invoice**.

4.  On the **Parameters** tab, select the **Posting** check box.

5.  Review information in the form and make any changes that are needed.

6.  Click **OK**. The credit note is posted.

## See also

[About packing slip updates for returns](about-packing-slip-updates-for-returns.md)

  


