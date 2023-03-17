---
# required metadata

title: Three-way matching policies
description: This article provides examples of three-way matching.
author: abruer
ms.date: 02/11/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: VendInvoicePostingHistory
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 2761
ms.assetid: 70f3cb1a-18b7-4474-95ec-28b2410dd8f8
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Three-way matching policies

[!include [banner](../includes/banner.md)]

This article provides examples of three-way matching.

## Example: Three-way matching for items

**Summary:** Ken is the controller at the corporate headquarters of a legal entity named Fabrikam. Ken decides that all vendor invoices that are based on purchase orders should be matched with purchase order lines (two-way matching). For purchases of items that will be used as fixed assets, invoices should be matched with both the purchase order lines and the product receipt lines (three-way matching).

Fabrikam operates with multiple legal entities and employees in all parts of the world. As the volume of transactions increases, discrepancies between receipts and invoices are also increasing. This results in assets being written off. Invoices from vendors are being paid, but the process does not include identifying discrepancies when fewer items are received than were ordered, or when items are not received at all. Spending also increases because employees still need tools and other materials to do their jobs. Ken wants to make sure that vendors are shipping the products that are ordered and the items are being received by Fabrikam employees. Therefore, Ken requires two-way and three-way matching for all legal entities in the organization. Invoice matching helps make sure that problems with items that have disappeared or not been received can be tracked and resolved. 

The invoice matching policies in this example help people in the following roles meet these goals:

-   Ken is the controller for the Fabrikam enterprise. Ken can help the people in the organization to identify and correct problems with ordering, receiving, and paying for items (goods and services) from vendors.
-   Phyllis and April are accounting managers in the accounts payable department for the United States division of Fabrikam. They can enforce corporate policy and make sure that invoices are paid only after the invoices are matched with the purchase order and receipts of goods and services, where applicable.
-   Tony is the production manager for the United States division of Fabrikam. Tony and other production personnel can make sure that items are received as they were ordered from vendors, and are accounted for so that the personnel have what they must have in order to perform their jobs.

### Prerequisites

-   Ken sets the **Matching policy** at the legal entity level to **Three-way matching**.
-   Ken sets the **Automatically update header matching status** toggle at the legal entity to **Yes**.
-   Ken sets the **Match price totals** field for the legal entity to **Percentage**, and enters 15% as the **Tolerance percentage**.
-   Ken sets the matching policy at the item level for item 1500 – CNC Milicron Machine to **Three-way matching**. This item is an asset item that is used for production at Fabrikam. Invoices for this item are matched with purchase order lines for prices and with product receipts for quantities.
-   Tony enters a requisition for five CNC Milicron Machines. Alicia, a purchase order clerk at Fabrikam, issues a purchase order to a legal entity named Contoso to supply the items.

    | Item number                 | Quantity | Unit price | Net amount | Charges code        | Charges value |
    |-----------------------------|----------|------------|------------|---------------------|---------------|
    | 1500 – CNC Milicron Machine | 5        | 8,000.00   | 40,000.00  | Shipping & handling | 3,000.00      |

-   Arnie, an accounts receivable clerk at Contoso, reviews shipments for the week. Arnie selects shipment transactions to invoice Fabrikam for the delivery of the CNC Milicron Machines. Arnie includes a charge for shipping and handling. Fabrikam will consider the charge to be part of the cost of the asset.

### Scenario

1.  Sammy, a worker in the receiving department at Fabrikam, receives the total quantity of machines that are shipped from Contoso. Sammy enters a quantity of 5 on a product receipt. Because the purchase order has been fully received, the status of the purchase order changes to Received.
2.  April, the accounts payable coordinator at Fabrikam, enters and verifies the invoice that is submitted by Contoso, and verifies the following information:
    -   For items that require three-way matching, the quantity on the invoice line matches the quantity that was received. The received quantity is indicated on the product receipt that is matched to the invoice.
    -   For items that require two-way or three-way matching, the prices on the invoice line are within the tolerances that are defined in Microsoft Dynamics 365 Finance. This includes the following types of price matching:
        -   Net unit price matching – The net unit price on the invoice line matches the net unit price on the purchase order line, within the tolerance percentage. In this example, the net unit price tolerance is +8%.
        -   Price totals matching – The net amount on the invoice line matches the net amount on the purchase order line, within the tolerance percentage, amount, or percentage and amount. In this example, the price totals matching tolerance is +15%.

The paper invoice from Contoso contains the following information.

| Item                        | Quantity | Unit price | Net amount |
|-----------------------------|----------|------------|------------|
| 1500 – CNC Milicron Machine | 5        | 8,100.00   | 40,500.00  |
| Shipping and handling       |          |            | 4,000.00   |
| Tax                         |          |            | 0.00       |
| Total                       |          |            | 44,500.00  |

The invoice line includes the following information.

| Item number                 | Quantity | Unit price | Line net amount | Matching policy    | Product receipt quantity match | Price match | Price total match |
|-----------------------------|----------|------------|-----------------|--------------------|--------------------------------|-------------|-------------------|
| 1500 – CNC Milicron Machine | 5        | 8,100.00   | 40,500.00       | Three-way matching | Passed                         | Passed      | Passed            |

Because this line passes the invoice matching process, the invoice can be posted.

## Example: Three-way matching for item and vendor combinations
Summary: Ken is the controller at the corporate headquarters of a legal entity named Fabrikam. Ken decides that all invoices that are based on purchase orders should be matched with purchase order lines (two-way matching). Cassie is the bookkeeper at the Malaysia division of Fabrikam. Cassie specifies that selected items that are ordered from certain vendors in Malaysia should be matched with both the purchase order lines and product receipt lines (three-way matching). Cassie can also override the matching policy to a higher level of matching for specific purchase orders. 

The volume and amounts are small, and there have been problems with delivery from some vendors in Malaysia. For these reasons, Cassie sets the level of control for certain item and vendor combinations that are procured in Malaysia to three-way matching. 

The invoice matching policies in this example help people in the following roles meet these goals:
-   Ken is the controller for the Fabrikam enterprise. Ken can help the people in the organization to identify and correct problems with ordering, receiving, and paying for items (goods and services) from vendors.
-   Cassie is the bookkeeper for the Malaysia division of Fabrikam. Cassie can enforce corporate policy and make sure that invoices are paid only after they are matched with purchase order lines and product receipts that represent the receipt of goods and services. Cassie can also increase the level of control to three-way matching for specific items to control operational costs.

### Prerequisites

-   Ken sets the **Matching policy** at the legal entity level to **Two-way matching**.
-   Ken sets the **Match price totals** field for the legal entity to **Percentage**, and enters **10%** as the **Tolerance percentage**.
-   Ken sets the unit price tolerance for all items to 2%.
-   Cassie sets the **Matching policy** at the item and vendor combination level for item PH2500 – Computer and vendor Contoso to **Three-way matching**.
-   Alicia, a purchase order clerk at the Malaysia division of Fabrikam, issues purchase orders to Contoso to supply three items, as shown in the following table. When Alicia creates the purchase order, the **Matching policy** is overridden for the wireless mouse to be three-way matching instead of two-way matching.

    | Item number           | Quantity | Unit price | Net amount | Matching policy (default entry) | Matching policy (on the purchase order line) |
    |-----------------------|----------|------------|------------|---------------------------------|----------------------------------------------|
    | PH2500 – Computer     | 2        | 2,500.00   | 5,000.00   | Three-way matching              | Three-way matching                           |
    | MM01 – Wireless Mouse | 2        | 40.00      | 80.00      | Two-way matching                | Three-way matching                           |
    | USB Drive             | 200      | 10.00      | 2,000.00   | Two-way matching                | Two-way matching                             |

### Scenario

1.  The items arrive. Sammy, a worker in the receiving department of the Malaysia division of Fabrikam, is interrupted and does not post the product receipt immediately.
2.  April, the accounts payable coordinator at Fabrikam, enters and verifies the invoice that is submitted by Contoso, and verifies the following information:
    -   For items that require three-way matching, the quantity on the invoice line matches the quantity that was received. The received quantity is indicated on the product receipt that is matched to the invoice.
    -   For items that require two-way or three-way matching, the prices on the invoice line are within the tolerances that are defined in the application. This includes the following types of price matching:
        -   Net unit price matching – The net unit price on the invoice line matches the net unit price on the purchase order line, within the tolerance percentage. In this example, the net unit price tolerance is +2%.
        -   Price totals matching – The net amount on the invoice line matches the net amount on the purchase order line, within the tolerance percentage, amount, or percentage and amount. In this example, the price totals matching tolerance is +10%.

The paper invoice from Contoso contains the following information.

| Item                  | Quantity | Unit price | Net amount |
|-----------------------|----------|------------|------------|
| PH2500 – Computer     | 2        | 2,500.00   | 5,000.00   |
| MM01 – Wireless Mouse | 2        | 41.00      | 82.00      |
| USB Drive             | 200      | 10.05      | 2,010.00   |
| Total invoice         |          |            | 7,092.00   |

The invoice line includes the following information.

| Item number           | Quantity | Unit price | Line net amount | Matching policy    | Product receipt quantity match | Price match | Price total match |
|-----------------------|----------|------------|-----------------|--------------------|--------------------------------|-------------|-------------------|
| PH2500 – Computer     | 2        | 2,500.00   | 5,000.00        | Three-way matching | Failed                         | Passed      | Passed            |
| MM01 – Wireless Mouse | 2        | 41.00      | 82.00           | Three-way matching | Failed                         | Failed      | Passed            |
| USB Drive             | 200      | 10.05      | 2010.00         | Two-way matching   |                                | Passed      | Passed            |

Note the following items:
-   For the PH2500 – Computer line, the Product receipt quantity match column has a warning icon because the invoice line is not matched to a product receipt.
-   For the MM01 – Wireless Mouse line, the Product receipt quantity match column has a warning icon because the invoice line is not matched to a product receipt. The Unit price match column has a warning icon because the 2% net unit price tolerance is exceeded.
-   For the USB Drive line, the Product receipt quantity match column is blank because two-way matching does not match invoice line and product receipt line quantities.

If approval is required for invoices to be posted with invoice matching discrepancies, the **Approve posting with matching discrepancies** toggle on the **Invoice matching details** page must be selected before the invoice can be posted with price matching errors and quantity matching errors. If approval is not required, invoice processing can continue if there are no other posting errors.


For more information, see [Accounts payable invoice matching overview](accounts-payable-invoice-matching.md).





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
