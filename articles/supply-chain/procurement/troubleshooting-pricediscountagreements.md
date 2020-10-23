---
# required metadata

title: Troubleshoot prices, discounts, agreements, and rebates
description: This topic describes how to fix issues that you might encounter while you work with prices, discounts, agreements, and rebates.
author: SmithaNataraj
manager: tfehr
ms.date: 09/16/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: PurchTable, PurchTablePart, PurchRFQTable
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

This topic describes how to fix issues that you might encounter while you work with prices, discounts, agreements, and rebates.

## I can't link a purchase agreement to a purchase order line after the purchase order is created.

A purchase agreement must be associated with a purchase order when the purchase order is created. Otherwise, purchase order lines can't be associated with purchase agreement lines.

## What check triggers the "Update prices and discounts entered manually or external document" message?

When you change the shipping date, you might receive a message that states, "Update prices and discounts entered manually or external document." You receive this message because, if the shipping date is changed, a different trade or sales agreement might be triggered and cause a price change. A change to the shipping date can also affect warehouse schedules and other related information.

The message is triggered whenever any of the dates or some other parameters are changed. The purpose of the message is to make sure that you're aware of price changes that can occur because of those changes.

The message is the trade agreement evaluation (TAE) prompt. For a full description, see [Trade agreement evaluation policies](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/trade-agreement-evaluation-policies-white-paper).

## A purchase order receipt doesn't include all charges.

### Reproduce the issue

The following procedure shows one way to reproduce the issue.

1. On the **Procurement and sourcing parameters** page, on the **Delivery** tab, make sure that the **Generate charges on product receipt** option is set to *Yes*.
1. Create a purchase order that includes charges.
1. Confirm the purchase order.
1. Receive the purchase order.
1. Look at the receipt total, and compare it to the expected total.
1. Notice that not all the charges are included on the purchase order receipt.

### Issue resolution

The resolution depends on the way that the miscellaneous charges have been set up. For information about how to set up miscellaneous charges to meet your requirements, see the following blog post: [Post misc. charges at time of product receipt](https://cloudblogs.microsoft.com/dynamics365/no-audience/2014/11/11/post-misc-charges-at-time-of-product-receipt/).

## Trade agreement prices and discounts aren't applied on sales or purchase order lines that are imported through data management.

### Issue description

Trade agreements that are applicable to sales or purchase order lines aren't applied on lines that are imported through data management. However, the same trade agreements are applied on sales or purchase order lines that are manually created.

### Reason for the issue

If purchase order lines that are imported via data management already include price information, the trade agreement won't be reevaluated for those lines. For example, if **Line discount percentage** or any of the price and discount values is set for a line, then trade agreements will not be looked up for that line.

### Issue workaround

This behavior is expected, and is similar for both sales orders and purchase orders.

As a workaround, import the purchase order lines without setting any price information. The trade agreements will then be applied, and the purchase order lines will be updated based on the defined trade agreements.

## A vendor rebate isn't cumulated based on invoices.

### Issue description

If invoices that are posted have different due dates, those invoices aren't reflected in vendor rebates that are generated from them.

### Issue resolution

By design, the due date isn't considered when the vendor rebate is calculated. Consider customizing the system so that the due date and the relation to the invoice are more apparent with respect to the actual vendor rebate.

## Unit prices on purchase orders aren't calculated based on the unit conversion.

### Issue description

When a unit is changed on a purchase order, trade agreement prices aren't recalculated according to unit conversion definitions.

### Issue resolution

Prices are always obtained from trade agreements (or other price settings in the system, such as sales agreements or item prices), and they are set for a unit.

If the unit is changed on an order line, the system looks for a price for the new unit and applies that price. If no price is found for the unit, the system doesn't apply a price. The unit conversion can't be used to recalculate the price into another unit. Theoretically, the price for one box of ten might not equal ten times the price of one box.

### Issue workaround

One way to work around this issue is to make sure that there are trade agreements for the units that you expect will be used on order lines for the item.

## Currency conversion issues occur with trade agreements.

Trade agreement prices aren't recalculated according to the currency when the currency differs on a purchase order.

The *Generic currency* feature lets you define prices and discounts in only one currency. You can then convert to other currencies as you require. Furthermore, after the conversion is done, the feature can automatically apply smart rounding.

## When I open the Purchase agreement page in a line view mode, I can't personalize the page by adding the Price unit field in the overview of the line.

Some shared fields in the agreement framework can't be included in personalizations. This limitation occurs because of the data model that is implemented. Therefore, you can't personalize the **Price unit** field.

## The maximum limit from a purchase agreement isn't effective on a purchase requisition.

### Issue description

When a purchase requisition is linked to a purchase agreement, the maximum limit from the purchase agreement isn't effective on the purchase requisition. The default price information is correctly entered, but more than the maximum limit from the purchase agreement can be ordered in the purchase requisition.

### Issue resolution

This behavior is expected. Because requisitions aren't always approved, a quantity or amount should not be reserved on the purchase agreement. Therefore, you won't meet the maximum limit from the purchase agreement.

## Trade agreements can be created from rejected RFQs. Therefore, the system doesn't prevent trade agreement journals from being created if the RFQ line hasn't been accepted.

You can create trade agreements for any replies for a request for quotation (RFQ), regardless of whether they were accepted or rejected. For more information, see [Requests for quotation (RFQs) overview](request-quotations.md).

