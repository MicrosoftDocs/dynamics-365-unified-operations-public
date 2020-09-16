---
# required metadata

title: Troubleshoot prices, discounts, agreements, and rebates
description: This topic describes how to fix issues that you might encounter while working with prices, discounts, agreements and rebates.
author: SmithaNataraj
manager: tfehr
ms.date: 09/16/2020
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
ms.search.validFrom: 2020-9-16
ms.dyn365.ops.version: Release 10.0.14

---
# Troubleshoot prices, discounts, agreements, and rebates

This topic describes how to fix common issues that you might encounter while working with prices, discounts, agreements and rebates.

## Unable to link a purchase agreement to a purchase order line after creation

A purchase agreement must be associated to the purchase order at the time of creation. Purchase order lines can't be associated to purchase agreement lines if the purchase order was not initially associated at the time of purchase order creation.

## What check triggers the prompt 'Update prices and discounts entered manually or external document' message?

This message is shown when you change the shipping date because this means that a different trade or sales agreement may get triggered, resulting in a price change. It can also affect warehouse schedules and other related information. It gets triggered whenever any of the dates or some other parameters have been changed. The purpose of this message is to make sure that you are aware of price changes that can occur due to this change. This is the trade agreement evaluation (TAE) prompt; for a full description, see [Trade agreement evaluation policies](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/trade-agreement-evaluation-policies-white-paper).

## Purchase order receipt does not include all charges

### Reproduce the issue

One way to reproduce this issue is do the following:

1. On the **Procurement and sourcing parameters** page, open the **Delivery** tab and make sure **Generate charges on product receipt** is set to *Yes*.
1. Create a purchase order that includes charges.
1. Confirm the purchase order.
1. Receive the purchase order.
1. Look at the receipt total and compare it to the expected total.
1. Note that the charges on the purchase order receipt don't include all the charges.

### Issue resolution

This depends on how the miscellaneous charges have been setup. For details about how to set this according your requirements, see this blog post: [Post misc. charges at time of product receipt](https://cloudblogs.microsoft.com/dynamics365/no-audience/2014/11/11/post-misc-charges-at-time-of-product-receipt/).

## Trade agreement prices and discounts are not applied on sales or purchase order lines imported through data management

### Issue description

Trade agreements that are applicable for sales or purchase order lines don't get applied to lines imported through data management, though the same trade agreements are applied on regular sales or purchase order lines created manually.

### Reproduce the issue

One way to reproduce this issue is do the following:

1. Create a purchase order for a vendor that has a trade agreement set up for line discount percentage.
2. Import purchase order lines with price set, for example through the entity "Purchase Order Lines V2".
3. Enable **Line discount percentage**.
4. Note that the line discount percentage is not updated after import of these lines.

### Reason for the issue

When purchase order lines that are imported via data management already include price information, the trade agreement will not be re-evaluated for these lines.

### Issue workaround

Import the purchase order lines without setting any price information. Then the trade agreements will kick in and the purchase order lines will get updated based on the defined trade agreements.

This is the expected behavior and works similarly for both sales orders and purchase orders.

## Vendor rebate isn't cumulated based on invoices

### Issue description

Invoices posted with different due dates aren't reflected in vendor rebates that are generated from the invoices.

### Issue resolution

By design, the due date isn't considered when calculating the vendor rebate. You could consider customizing the system so that the due date and the relation to the invoice is more apparent in relation to the actual vendor rebate.

## Unit prices in purchase orders aren't calculated based on unit conversion

### Issue description

Trade agreement prices aren't recalculated according to unit conversion definitions when a unit is changed on a purchase order.

### Issue resolution

Price is always obtained from trade agreements (or other price settings in the system, such as sales agreements or item price) and the price is set for a unit.

If the unit is changed on an order line, then the system will look for a price for that particular unit and apply that price. If no price is found for the unit, the system won't apply the price. The unit conversion can't be used to recalculate the price into an other unit. Theoretically, it could be that price for a box with 10 isn't equal to ten times the price of one box.

### Issue workaround

One way to overcome this issue is to make sure that there are trade agreements for the particular units that are expected to be used on order lines for the item.

## Currency conversion issues with trade agreements

Trade agreement prices aren't recalculated according to currency when the currency is different on a purchase order.

The *Generic currency* feature lets you define prices and discounts in only one currency and then convert to other currencies on the fly. Furthermore, after conversion, the feature can automatically apply smart rounding.  

## When opening the "Purchase agreement page" in a line view mode, it isn't possible to personalize the screen to add the "Price unit" field in the overview of the line

Certain shared fields in the agreement framework can't be included in personalization. This is due to the implemented data model. As a result, you can't personalize the **Price unit** field.

## Purchase agreement max limit on a purchase requisition isn't effective

### Issue description

When a purchase requisition is linked to a purchase agreement, the max limit from the purchase agreement isn't effective on the purchase requisition. The price is defaulted correctly, but it is possible to order more than the maximum purchase agreement limit in the purchase requisition.

### Issue resolution

This is working as expected. Because requisitions aren't always approved, we don't want to "reserve" quantity or amount on the purchase agreement, which means you won't meet the max limit on the purchase agreement.

## Trade agreements can be created from rejected RFQs, so the system doesn't prevent trade agreement journals from being created if the RFQ line hasn't been accepted

It is possible to create trade agreements for any replies for an RFQ, regardless of whether they were accepted or rejected. For more information, see [Requests for quotation (RFQs) overview](request-quotations.md).

## Additional resources

[Purchase agreements](purchase-agreements.md)  
[Vendor Rebates](vendor-rebates.md)
