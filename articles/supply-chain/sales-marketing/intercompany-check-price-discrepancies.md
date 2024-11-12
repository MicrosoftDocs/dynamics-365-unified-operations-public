---
title: Check intercompany order price discrepancies
description: Learn how to check intercompany order price discrepancies, including a step-by-step process for price discrepancies on intercompany orders.
author: kamaybac
ms.author: adpattanaik
ms.topic: article
ms.date: 09/01/2021
ms.reviewer: kamaybac
ms.search.form: PurchTable, PurchTablePart, PurchLineOpenOrder
---

# Check intercompany order price discrepancies

[!include [banner](../../includes/banner.md)]

You can use this procedure to check for price discrepancies on intercompany orders.

1. Go to **Procurement and sourcing \> Purchase orders \> Intercompany \> Check intercompany order price discrepancies**.
1. Set up a batch job, if you need to, and then select **OK** to check the prices and discounts for intercompany sales orders and purchase orders. Otherwise, select **Cancel** to close the page without performing the check.

    > [!TIP]
    > If there are any synchronization issues or issues with the prices, these will be listed in an informational message that will be displayed. You can print the informational message for reference.

1. On the informational message, select the relevant line to open the order in the current legal entity. Open the order in the related legal entity by selecting **Intercompany**, and then **Intercompany purchase order** or **Intercompany sales order**.

    > [!NOTE]
    > To allow an update of the intercompany order:
    >
    > 1. Go to **Accounts receivable \> Customers \> All customers**.
    > 1. On the Action Pane, select the **General** tab, and then select **Intercompany**.
    > 1. On the **Intercompany** page, select **Purchase order policies** or **Sales order policies**.
    > 1. Select **Allow price edit** and **Allow discount edit** in both areas.

1. Open the relevant intercompany order where you want to keep the price.
1. For each order line, change the **Unit price** field for the line, and then change it back to the original value. Change the **Discount** field for the line back and forth, and change the relevant **Charges on purchases** or **Sales charges** fields back and forth. Changing the values back and forth will trigger a synchronization of the prices, discounts, and charges from this intercompany order line to the referenced intercompany order line, so they will be automatically aligned.

    > [!NOTE]
    > This synchronization is valid only if the intercompany sales order has not been invoiced. If the intercompany sales order has been invoice-posted and a customer invoice journal has been created, changes must be performed directly on the intercompany purchase order lines by setting the prices, discounts, and charges equal to those on the intercompany customer invoice journal. If this is not done, the intercompany purchase order cannot be invoice-posted, because there will be a mismatch in the order totals.

1. Repeat the procedure until all intercompany purchase and sales orders are synchronized.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
