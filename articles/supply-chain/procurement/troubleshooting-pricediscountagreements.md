---
# required metadata

title: Troubleshoot prices, discounts, agreements and rebates
description: This topic describes how to fix issues that you might encounter while working with prices, discounts, agreements and rebates.
author: SmithaNataraj
manager: tfehr
ms.date: 05/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: PurchTable, PurchRFQTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: smnatara
ms.search.validFrom: 2020-5-7
ms.dyn365.ops.version: AX 10.0.14

---
# Troubleshoot prices, discounts, agreements and rebates

This topic describes how to fix common issues that you might encounter while working with prices, discounts, agreements and rebates.

## Unable to link a Purchase Agreement to a Purchase Order Line after creation

A purchase agreement has to be associated to the purchase order at the time of creation. Purchase order lines cannot be associated to purchase agreement lines if the purchase order was not initially associated at the time of purchase order creation.

## What check triggers the prompt 'Update prices and discounts entered manually or external document' message?

We prompt this when changing the shipping date because often times this means that a different trade or sales agreement can get triggered, resulting in a price change. It can also effect warehouse schedules and other related information. It gets triggered whenever any of the dates have been changed, to ensure that the user is aware of price changes that can happen due to this change.

## Purchase order receipt does not include all charges

**Scenario**
1. Make sure the procurement and sourcing parameter > Delivery > Generate charges on product receipt option is set to yes.
2. Create purchase order that includes charges.
3. Confirm the PO.
4. Receive the PO.
5. Look at the receipt total and compare it to the expected total. 
6. Result: The charges on the purchase order receipt does not include all the charges.

**Reason**
This is dependent on how the miscellaneous charges have been setup. Please see this blog for how to set this according your requirements. [Post Misc. charges at time of Product receipt](https://cloudblogs.microsoft.com/dynamics365/no-audience/2014/11/11/post-misc-charges-at-time-of-product-receipt/)

## Trade agreement price and discounts are not applied on purchase order lines imported through data management (DMF)
Trade agreements that are applicable for purchase order lines do not get applied to lines imported through data management, though the same trade agreements are applied on regular purchase order lines created manually.

**Scenario**
1. Create a purchase order for a vendor that has a trade agreement set up for line discount percentage.
2 Import purchase order lines with price set for eg., through the entity Purchase Order Lines V2
3. Check field "Line discount percentage".
4. Result: The line discount percentage is not updated after import of these lines.

**Reason**
When purchase order lines that are imported via data management already are decorated with price information, then the trade agreement will not be re-evaluated for these lines. 

**Workaround**
Import the purchase order lines without setting any of the price information, then the trade agreements will get kicked in and the purcase order lines would get updated based on the defined trade agreements.

## Vendor rebate is not cumulated based on invoices.
Posting invoices with different due dates is not reflected to the vendor rebates that is generated from the invoices.

**Resolution**
Due date is not considered when calculating the vendor rebate.
Customization as extension could be considered so that the due date and the relation to the invoice is more apparent in relation to the actual vendor rebate.

## Unit price in purchase order is not calculated based on UOM conversion
Trade agreement Prices are not recalculated according to unit conversion definitions when a unit is changed on a purchase order.

Price is always obtained from trade agreements (or other price settings in the system e.g. sales agreements; item price) and the price is set for a Unit. 

If the unit is changed on an order line then the system will look for a price for that particular unit and apply that price; if no price is found for the unit it will not apply the price. The unit conversion cannot be used to recalculate the price into an other unit. Theoretically, it could be that the price is different for a box with 10 than 10xthe price of 1.

**Workaround**
A way to overcome this is to make sure that there are trade agreements for the particular units that are expected to be used on order lines for the item.

## When opening the Purchase agreement form in a line view mode, it is not possible to personalize the screen to add the Price unit field in the overview of the line.
Certain shared fields in the agreement framework cannot be included in personalization as requested. This is due to the implemented datamodel. Hence, the price unit field cannot be personalized.

**Purchase agreement max limit on a purchase requisition is not effective**
When a purchase requisition is linked to a purchase agreement, the max limit from the purchase agrement is not effective on the purchase requisition. The price is defaulted correctly but it is possible to order more than the maximum purchase agreement limit in the purchase requisition.

**Fix**
This is working as expected. As requisitions are not always being approved, we do not want to "reserve" quantity or amount on the purchase agreement - hence we are not running into meeting the max limit on the purchase agreement. 

## Trade agreements can be created from the rejected RFQs as well. System does not prevent creation of Trade agreement journals if the RFQ line has not be accepted.
It is possible to create trade agreements for any replies for an RFQ, regardless of whether they were accepted or rejected. For more details, see here (Request For Quotations)[https://docs.microsoft.com/en-us/dynamics365/supply-chain/procurement/request-quotations]

## Additional resources

[Purchase agreements](purchase-agreements.md)
[Vendor Rebates](vendor-rebates.md)

