---
title: Invoice matching and intercompany purchase orders
description: Learn about how the purchasing legal entity that is involved in an intercompany trade transaction might be set up to use accounts payable invoice matching.
author: twheeloc
ms.author: shpandey
ms.topic: how-to
ms.date: 07/28/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: PurchLineMatchingPolicy
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 9c7c2e44-45f8-4325-b6de-a09fe790f9cf
---

# Invoice matching and intercompany purchase orders

[!include [banner](../includes/banner.md)]

Set up the purchasing legal entity that participates in an intercompany trade transaction to use accounts payable invoice matching. When you set the **Post invoice with discrepancies** field in the **Accounts payable parameters** page to **Require approval**, the system performs invoice matching validation. In this case, the posting requirements for both intercompany trade and accounts payable invoice matching must be met before you can post intercompany vendor invoices.

The examples in this article use the following setup for intercompany trade:

- Fabrikam Purchase is the purchasing legal entity.
- Fabrikam Sales is the selling legal entity.
- Customer 4020 exists in Fabrikam Sales.
- Vendor 3024 exists in Fabrikam Purchase.
- In Fabrikam Purchase, you specify intercompany information for vendor 3024. You specify Fabrikam Sales as the customer company, and customer 4020 as the customer account that corresponds to the Fabrikam Purchase legal entity.
- In Fabrikam Sales, you specify intercompany information for customer 4020. You specify Fabrikam Purchase as the vendor company, and vendor 3024 as the vendor account that corresponds to the Fabrikam Sales legal entity.

The examples use the following setup for accounts payable invoice matching for Fabrikam Purchase:

- On the **Accounts payable parameters** page, select the **Enable invoice matching validation** option.
- On the **Accounts payable parameters** page, set the **Post invoice with discrepancies** field to **Require approval**.
- Set the price tolerance percentage for the legal entity to 2 percent.

## Example: Price matching and intercompany trade

The net amounts for the intercompany vendor invoice and the intercompany customer invoice must be equal. This requirement overrides any invoice matching approvals or price tolerance percentages that apply. For example, follow these steps:

1. In Fabrikam Purchase, create sales order SO888 for customer 4020. The system automatically creates intercompany purchase order ICPO222 for vendor 3024 in Fabrikam Purchase, and sales order ICSO888 is automatically created in Fabrikam Sales.
1. In Fabrikam Sales, register that the items are received, and post a packing slip. The status of ICSO888 changes to **Delivered**. The status of ICPO222 changes to **Received**.
1. In Fabrikam Sales, update an invoice for ICSO888. The unit price is 0.45, and 100 items are updated.
1. In Fabrikam Purchase, create an invoice for ICPO222. You accidentally change the net price from 45.00 to 54.00. An icon is displayed to indicate that the price exceeds the allowable price tolerance of 2 percent.
1. On the **Invoice matching details** page, select the option to approve posting with matching discrepancies. On the **Vendor invoice** page, click **OK**. If the vendor invoice wasn't an intercompany vendor invoice, posting would be successful. However, because you're working with an intercompany vendor invoice, posting is unsuccessful. For intercompany trade, the invoice totals on the intercompany sales order must equal the invoice totals on the corresponding intercompany purchase order. To resolve this issue, you must correct the net price on the invoice by changing the net price back to the default amount, 45.00.

## Example: Quantity matching with intercompany trade

The quantities on the intercompany purchase order and the intercompany sales order must be equal. This requirement overrides any invoice matching approvals that apply. This example uses the following additional setup for intercompany trade:

- In Fabrikam Purchase, set the purchase order action policy for vendor 3024 to automatically post both the original customer invoice and the intercompany vendor invoice.

This example uses the following additional setup for accounts payable invoice matching for Fabrikam Purchase:

- On the **Item model groups** page for the model group that item B-R14 uses, select the **Receiving requirements** option.
- The on-hand quantity for item B-R14 is 0.

For example, follow these steps:

1. In Fabrikam Purchase, create sales order SO999 for customer 4020. The order contains one line item: 100 batteries (item B-R14) at a unit price of 1.00 each. The system automatically creates intercompany purchase order ICPO333 for vendor 3024 in Fabrikam Purchase, and sales order ICSO999 in Fabrikam Sales.
1. In Fabrikam Sales, perform an invoice update for ICSO999. Posting is unsuccessful, because the item is out of stock and isn't yet received. Therefore, the financial information can't be updated.
1. In Fabrikam Sales, register that the items are received, and post a packing slip for ICSO999. The system automatically posts a product receipt for ICPO333 in Fabrikam Purchase. In Fabrikam Purchase, the received quantity for item B-R14 changes to 100.
1. In Fabrikam Sales, perform an invoice update for ICSO999. Posting is successful in both legal entities. In Fabrikam Purchase, the quantity that is purchased for item B-R14 changes to 100.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
