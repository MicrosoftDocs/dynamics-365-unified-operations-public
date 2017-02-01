---
# required metadata

title: Invoice matching and intercompany purchase orders | Microsoft Docs
description: The purchasing legal entity that is involved in an intercompany trade transaction might be set up to use accounts payable invoice matching. In this case, the posting requirements for both intercompany trade and accounts payable invoice matching must be met before intercompany vendor invoices can be posted.
author: twheeloc
manager: AnnBe
ms.date: 2015-09-10 20:21:21
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

keywords: PurchLineMatchingPolicy
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: annbe
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 3101
ms.assetid: 93e3d814-cbe4-4a39-ab87-40ba2aa1682a
ms.region: Global
# ms.industry: 
ms.author: abruer

---

# Invoice matching and intercompany purchase orders

The purchasing legal entity that is involved in an intercompany trade transaction might be set up to use accounts payable invoice matching. In this case, the posting requirements for both intercompany trade and accounts payable invoice matching must be met before intercompany vendor invoices can be posted.

The examples in this topic use the following setup for intercompany trade:
-   Fabrikam Purchase is the purchasing legal entity.
-   Fabrikam Sales is the selling legal entity.
-   Customer 4020 exists in Fabrikam Sales.
-   Vendor 3024 exists in Fabrikam Purchase.
-   In Fabrikam Purchase, intercompany information is specified for vendor 3024. Fabrikam Sales is specified as the customer company, and customer 4020 is specified as the customer account that corresponds to the Fabrikam Purchase legal entity.
-   In Fabrikam Sales, intercompany information is specified for customer 4020. Fabrikam Purchase is specified as the vendor company, and vendor 3024 is specified as the vendor account that corresponds to the Fabrikam Sales legal entity.

The examples use the following setup for accounts payable invoice matching for Fabrikam Purchase:
-   On the Accounts payable parameters page, the Enable invoice matching validation option is selected.
-   On the Accounts payable parameters page, the Post invoice with discrepancies field is set to Require approval.
-   The price tolerance percentage for the legal entity is 2 percent.

## Example: Price matching and intercompany trade
The net amounts for the intercompany vendor invoice and the intercompany customer invoice must be equal. This requirement overrides any invoice matching approvals or price tolerance percentages that apply. For example, you follow these steps.
1.  In Fabrikam Purchase, create sales order SO888 for customer 4020. Intercompany purchase order ICPO222 is automatically created for vendor 3024 in Fabrikam Purchase, and sales order ICSO888 is automatically created in Fabrikam Sales.
2.  In Fabrikam Sales, register that the items have been received, and post a packing slip. The status of ICSO888 changes to Delivered. The status of ICPO222 changes to Received.
3.  In Fabrikam Sales, perform an invoice update for ICSO888. The unit price is 0.45, and 100 items are updated.
4.  In Fabrikam Purchase, create an invoice for ICPO222. You accidentally change the net price from 45.00 to 54.00. An icon is displayed to indicate that the price exceeds the allowable price tolerance of 2 percent.
5.  On the Invoice matching details page, select the option to approve posting with matching discrepancies. On the Vendor invoice page, click OK.If the vendor invoice was not an intercompany vendor invoice, posting would be successful. However, because you are working with an intercompany vendor invoice, posting is unsuccessful. For intercompany trade, the invoice totals on the intercompany sales order must equal the invoice totals on the corresponding intercompany purchase order. To resolve this issue, you must correct the net price on the invoice by changing the net price back to the default amount, 45.00.

## Example: Quantity matching with intercompany trade
The quantities on the intercompany purchase order and the intercompany sales order must be equal. This requirement overrides any invoice matching approvals that apply. This example uses the following additional setup for intercompany trade:
-   In Fabrikam Purchase, the purchase order action policy for vendor 3024 is set up to automatically post both the original customer invoice and the intercompany vendor invoice.

This example uses the following additional setup for accounts payable invoice matching for Fabrikam Purchase:
-   On the Item model groups page for the model group that is used by item B-R14, the Receiving requirements option is selected.
-   The on-hand quantity for item B-R14 is 0 (zero).

For example, you follow these steps.
1.  In Fabrikam Purchase, create sales order SO999 for customer 4020. The order contains one line item: 100 batteries (item B-R14) at a unit price of 1.00 each. Intercompany purchase order ICPO333 is automatically created for vendor 3024 in Fabrikam Purchase, and sales order ICSO999 is automatically created in Fabrikam Sales.
2.  In Fabrikam Sales, perform an invoice update for ICSO999. Posting is unsuccessful, because the item is out of stock and has not yet been received. Therefore, the financial information cannot be updated.
3.  In Fabrikam Sales, register that the items have been received, and post a packing slip for ICSO999. A product receipt for ICPO333 is automatically posted in Fabrikam Purchase. In Fabrikam Purchase, the received quantity for item B-R14 changes to 100.
4.  In Fabrikam Sales, perform an invoice update for ICSO999. Posting is successful in both legal entities. In Fabrikam Purchase, the quantity that is purchased for item B-R14 changes to 100.



