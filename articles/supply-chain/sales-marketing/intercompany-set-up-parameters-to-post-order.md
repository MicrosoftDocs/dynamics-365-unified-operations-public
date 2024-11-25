---
title: Set up parameters to post an intercompany order
description: Learn how to set up parameters to post an intercompany order, including a step-by-step process for setting up parameters.
author: AditiPattanaik
ms.author: adpattanaik
ms.topic: article
ms.date: 09/01/2021
ms.reviewer: kamaybac
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable
---

# Set up parameters to post an intercompany order

[!include [banner](../../includes/banner.md)]

When an intercompany customer invoice is posted, you can set it up to post both the intercompany purchase order and the original customer invoice automatically.

> [!NOTE]
> Before you perform this procedure, set up the print management in your organization to point to the correct invoice printer. This will make sure that the invoice for the original sales order is printed on the correct printer.

You must set up the following parameters:

1. Go to **Sales and marketing \> Sales orders \> All sales orders**. Select sales order that you want to work with.
1. On the sales order, on the Action Pane, select **Header view** and then select the **Intercompany settings** FastTab and open it.
1. Go to the Action Pane, on the **Sales order** tab and then select **Edit**.
1. Go back to the **Intercompany settings** FastTab and select **Direct delivery** to enable direct delivery throughout the intercompany chain (all orders).
1. Select **Save** to save the sales order with the new setting. Then select **Close** to close the sales order.
1. Go to **Procurement and sourcing \> Vendors \> All vendors**. On the **General** tab, select **Intercompany**.
1. On the **Intercompany** page, select the **Purchase order policies** link. In the **Intercompany purchase order (direct delivery)** field group, select **Post invoice automatically** and remove the check mark from the **Print invoice automatically** field.
1. In the **Original sales order (direct delivery)** field group, select the **Post invoice automatically** field and the **Print invoice automatically** field.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
