---
# required metadata

title: Perform invoice updates for returns  
description: This functionality supports the business processes of organizations that choose to have return orders and sales orders invoiced at the same time and by the same person.
author: Henrikan
ms.author: henrikan
ms.date: 05/01/2018
ms.topic: article

# optional metadata

ms.search.form: SMAServiceOrderTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---


# Perform invoice updates for returns

[!include [banner](../includes/banner.md)]

A return order is a type of sales order that is marked as a returned order. Therefore, the **All sales orders** list page is used to generate invoices for return orders instead of the **Return orders** form. This functionality supports the business processes of organizations that choose to have return orders and sales orders invoiced at the same time and by the same person.

Because the invoice for a returned item is for a negative amount, it is called a credit note.

When you set up the invoice update for batch processing, the sales order of type **Returned order** must have a return line status of **Received**, which indicates that the order's packing slip has been updated.

## Post an invoice for a return order

1. Go to **Accounts receivable** \>  **Orders** \> **All sales orders**.

1. Select a sales order for which **Returned order** is displayed in the **Order type** field.

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.

1. On the **Parameters** tab, select the **Posting** check box.

1. Review information in the form and make any changes that are needed.

1. Select **OK**. The credit note is posted.

## See also

- [Packing slip updates for returns](packing-slip-updates-returns.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]