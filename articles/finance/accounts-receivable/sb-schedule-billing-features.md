---
title: Billing schedule features
description: Learn about the features of billing schedules, such as pricing methods, escalations and discounts, alignment dates, proration, reverse billing, and split item groups. 
author: JodiChristiansen
ms.author: jchrist
ms.topic: how-to
ms.date: 07/30/2026
ms.reviewer: twheeloc 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2021-11-05
ms.search.form: 
ms.dyn365.ops.version: 10.0.24
---

# Billing schedule features

[!include [banner](../includes/banner.md)]

This article explains the features of billing schedules and billing schedule lines. It describes the different methods that are used for pricing, how to use escalations and discounts, and how to reverse a billing period. It also includes examples of proration calculations and split item groups.

## Pricing methods

Use one of the following pricing methods to calculate the unit price of an item:

* Flat
* Standard
* Tier
* Flat tier

### Flat pricing

When you use the flat pricing method, you can edit the unit price for a billing schedule line item on the **All billing schedules** page to any value that you want. The **Price unit** value is always **1**. Therefore, the **Unit price** and **Net amount** values for an item are the same.

### Standard pricing (without a trade agreement)

When you use the standard pricing method without a trade agreement, set up the unit price for a billing schedule line item by selecting **Product information management** on the **Release product details** page. The unit price appears in the **Base sales price** section. It's calculated as *Price* &divide; *Price quantity*.

### Standard pricing (with a trade agreement)

The following examples show the standard pricing calculations when a trade agreement exists. You can create trade agreements from the **Release product details** page.

Both examples use an item that has the following price brackets.

| Qty from | Qty to | U of M | Price | Price unit |
|---|---|---|---|---|
| 0 | 100 | Each | 1.50 | 1 |
| 100 | 200 | Each | 1.25 | 1 |
| 200 | 999999 | Each | 1.00 | 1 |

**Example 1**

The invoice quantity is 250, and the standard pricing method is used. Because the quantity is in the 200–999,999 price quantity range, the unit price is 1.00.

Calculate the net amount in the following way:

*Net amount* = (*Quantity* &times; *Price*) &divide; *Price unit* = (250 &times; 1.00) &divide; 1 = 250

**Example 2**

The invoice quantity is 100, and the standard pricing method is used. Because the invoice quantity is in the 100–200 price quantity range, the unit price is 1.25.

> [!NOTE]
> The invoice quantity is in the 100–200 range instead of the 0–100 range because, in the standard quantity matching behavior, a quantity matches if it's *more than or equal to* the "from" quantity and *less than* the "to" quantity.

Calculate the net amount in the following way:

*Net amount* = (100 &times; 1.25) &divide; 1 = 125

### Tier pricing

In the following example, an item has these price brackets.

| Qty from | Qty to | U of M | Price | Price unit |
|---|---|---|---|---|
| 0 | 100 | Each | 1.50 | 10 |
| 100 | 200 | Each | 1.25 | 10 |
| 200 | 999999 | Each | 1.00 | 10 |

If the invoice quantity is 250 and you use the tier pricing method, calculate the prices of the items based on the pricing brackets:

* **First 100 items:** 100 &times; 1.50 = 150.00
* **Second 100 items:** 100 &times; 1.25 = 125.00
* **Remaining items:** 50 &times; 1.00 = 50.00

Calculate the net amount in the following way:

*Net amount* = (150.00 &divide; 10) + (125.00 &divide; 10) + (50.00 &divide; 10) = 15.00 + 12.50 + 5.00 = 32.50

After you calculate the net amount, calculate the unit price by dividing the net amount by the quantity:

*Unit price* = 32.50 &divide; 250 = 0.13

### Flat tier pricing

In the following example, an item has these price brackets.

| Qty from | Qty to | U of M | Flat tier amount | Price unit |
|---|---|---|---|---|
| 0 | 50 | Each | 100.00 | 50 |
| 50 | 200 | Each | 150.00 | 200 |

The following table shows the invoices and the unit prices for the different quantities that are purchased. You calculate the net amount first, and then calculate the unit price.

| Invoice | Quantity purchased | Unit price | Net amount |
|---|---|---|---|
| 1 | 25 | 2.00 &divide; 25 = 0.08 | 100 &divide; 50 = 2.00 |
| 2 | 20 | 2.00 &divide; 20 = 0.10 | 100 &divide; 50 = 2.00 |
| 3 | 50 | 2.00 &divide; 50 = 0.04 | 100 &divide; 50 = 2.00 |
| 4 | 60 | 0.75 &divide; 60 = 0.0125 = 0.01 | 150 &divide; 200 = 0.75 |

## Escalations and discounts

An *escalation* is a price increase for a future billing period that the invoice isn't yet created for. A *discount* is a price reduction for a future billing period that the invoice isn't yet created for.

In Subscription billing, you can't apply escalations and discounts retroactively to a billing schedule. For example, you can't apply an escalation to a billing schedule three months in the past and process it. In other words, you can't apply a price increase that happened three months ago.

You can apply an escalation or discount to a billing schedule or billing schedule line in one of the following places:

* The **All/Active billing schedules** list page
* A specific billing schedule
* A specific billing schedule line

### Apply an escalation or discount

To apply an escalation or discount to a billing schedule, follow these steps:

1. Select a billing schedule or a billing schedule line.
1. Select **Escalation and discount** either on the **Escalation and discount** tab or on the billing schedule line.
1. If a consumer price index is used to calculate the escalation or discount, select a value in the **Consumer price index calculation** field.
1. Select **New** to add an escalation or discount line.
1. For a discount, select the **Discount** checkbox. For an escalation, clear the **Discount** checkbox.
1. Set the **Start date** and **Frequency** fields.
1. For deferral items that use the unbilled revenue feature, set the **End date** field.
1. Set the **Percentage**, **Amount**, or **Consumer price index schedule** field.
1. Set the **End date** field.
1. Select **OK**.
1. Repeat steps 4 through 10 for each additional escalation or discount line that you require.

### Fields on the Billing schedule lines page

The **Billing schedule lines** page contains the following fields.

| Field | Description |
|---|---|
| Item number | The item number for the billing schedule line. This field is available only when you open the page from a billing schedule line item. |
| Consumer price index calculation | <p>Select the method that is used to calculate the consumer price index escalation:</p><ul><li>**Prior consumer price index** – Use the previous consumer price index value for the escalation calculation.</li><li>**Base consumer price index** – Use the base consumer price index value for the escalation calculation.</li></ul> |
| **Line** grid | |
| Discount | <p>Set the checkbox to specify whether the change in the amount is an escalation or discount:</p><ul><li>**Selected** – The change applies a discount to the billing schedule or billing schedule line.</li><li>**Cleared** – The change applies an escalation to a billing schedule or a schedule line.</li></ul><p>You can't change the setting of this checkbox for items that use the unbilled revenue feature. Additionally, you can't apply discounts to items that use revenue splitting.</p> |
| Start date | Select the start date of the escalation or discount. |
| Frequency | Select the frequency of the escalation or discount: **None**, **Monthly**, **Quarterly**, **Semiannually**, or **Annually**. |
| Percentage | Specify the percentage of the escalation or discount. |
| Amount | Specify the amount of the escalation or discount. |
| Consumer price index schedule | Select the consumer price index schedule that is used for the calculations. |
| End date | <p>Select the end date of the escalation or discount.</p><p>**Note:** This field is required for items that use the unbilled revenue feature.</p> |
| Deferral schedule number | <p>The deferral schedule number.</p><p>This field is available only when you open the page from a billing schedule line.</p> |
| Journal batch number | <p>The journal batch number.</p><p>This field is available only when you open the page from a billing schedule line.</p> |
| Total discount amount | <p>The sum of discount amounts for all the lines in the grid.</p><p>This field is available only when you open the page from a billing schedule line.</p> |
| Current short-term unbilled revenue amount | <p>The current short-term unbilled revenue amount.</p><p>This amount appears when you select a short-term deferral method on the **Recurring contract billing parameters** page, and set up the accounts for the line item on the **Unbilled revenue setup** page.</p> |
| Current long-term unbilled revenue amount | <p>The current long-term unbilled revenue amount.</p><p>This amount appears when you select a short-term deferral method on the **Recurring contract billing parameters** page, and set up the accounts for the line item on the **Unbilled revenue setup** page.</p> |

## Proration examples

Calculations for proration can be based on the number of days or the number of months. The method that is used for the proration calculation is set on the **Recurring contract billing parameters** page. The proration method affects how the amounts are calculated for a billing schedule in the following situations:

* Initial creation
* Application of an escalation or discount
* Termination
* Placement or removal a hold
* Addition of support or renewal

The proration method also affects the calculations on the monthly recurring revenue (MRR) report.

### Example 1

The annual amount of a billing schedule is $5,000. The start date is August 12, 2025, and the end date is December 22, 2025. The billing frequency is annual. The prorated amount is calculated in the following ways, depending on whether the daily or monthly calculation method is used:

* **Daily**

  * *Number of days* = *End date* – *Start date* + 1 = 133 days
  * *Number of days in the year* = August 11, 2026 – August 12, 2025 + 1 = 366 days
  * *Prorated amount* = 5,000 &times; (133 &divide; 366) = 1816.94

* **Monthly**

  * *Start month portion* = (31 – 12 + 1) &divide; 31 = 20 &divide; 31
  * *Middle months* = 3
  * *End month portion* = 22 &divide; 31
  * Prorated amount = 5,000 &divide; 12 &times; \[(20 &divide; 31) + 3 + (22 &divide; 31)\] = 1814.52

### Example 2

The annual amount of a billing schedule is $12,000. The start date is August 1, 2025, and the end date is December 31, 2025. The billing frequency is annual. The prorated amount is calculated in the following ways, depending on the calculation method:

* **Daily**

  * *Number of days* = *End date* – *Start date* + 1 = 153 days
  * *Number of days in the year* = July 31, 2026 – August 1, 2025 + 1 = 366 days
  * *Prorated amount* = 12,000 &times; (153 &divide; 366) = 5016.39

* **Monthly (Full month)**

  * *Number of months* = 5
  * *Total months* = 12
  * *Prorated amount* = (12,000 &times; 5) &divide; 12 = 5,000

## Reversing a period billing

For this example, a billing schedule has only one line:

* Billing is done monthly for 12 months from January through December.
* Invoices are created for all periods up through April.

You want to reverse the invoice for the April billing period.

If you didn't create a sales invoice for the April billing period, you could delete the sales order. In this case, the **Billed** status for the detail is removed. However, because you created an invoice for the billing period, you can't clear the **Billed** status for the detail. Therefore, to reverse the April billing, you must create an offsetting credit note for the line.

1. On the **All billing schedules** page, create a schedule line for the same item.
1. Change the **Quantity** value for the item to the negative of the original quantity.
1. Set the **Billing frequency** field to **One-time**.
1. Update the start and end dates so that they match the dates of billing detail line that you want to create a credit note for. For this example, set the start date to April 1, 2025, and the end date to April 30, 2025.
1. Save your changes.
1. Open the **Generate invoice** page, and create the sales order that has the credit note for the specified period.
1. (Optional) Post the invoice.

When you review the lines for the billing schedule, you notice that the new line has a link to the credit note. The original line still has a link to the original April invoice.

## Split item group examples

For this example, use the following setup:

* On **Recurring contract billing parameters**, select **Split by item group**, and set the **Unique schedule type** field to **Customer**.
* Create three item groups: **PREFIX**, **DATAHUB**, and **SPP**.
* Customer US-001 has multiple billing schedules where the item group is PREFIX or DATAHUB.
* Customer US-002 has multiple billing schedules where the item group is PREFIX or SPP.

| Billing schedule number | Customer | Item group |
|---|---|---|
| SCH001 | US-001 | PREFIX |
| SCH002 | US-001 | DATAHUB |
| SCH003 | US-002 | PREFIX |
| SCH004 | US-002 | SPP |

Customer US-001 purchases a renewal item that belongs to the PREFIX item group. This transaction is a new sales order.

| Sales order # | Customer | Main item | Renewal item | Renewal item group | Billing schedule number |
|---|---|---|---|---|---|
| SO0001 | US-001 | D0001 | D0002 | PREFIX | SCH001 |

When you post the invoice for the sales order, the renewal item is added to the existing billing schedule (SCH001) for the customer. This billing schedule uses the PREFIX item group. All renewal items that belong to the same item group go into the same billing schedule.

**Header**

| Billing schedule number | Customer | Item group |
|---|---|---|
| SCH001 | US-001 | PREFIX |

**Line**

| Billing schedule number | Customer | Item group |
|---|---|---|
| SCH001 | US-001 | D0002 |

Customer US-001 now purchases a renewal item that belongs to the SPP item group. This transaction is a new sales order.

| Sales order # | Customer | Main item | Renewal item | Renewal item group | Billing schedule number |
|---|---|---|---|---|---|
| SO0002 | US-001 | D0003 | D0004 | SPP | |

Currently, customer US-001 doesn't have a billing schedule that uses the SPP item group. Therefore, create a new billing schedule.

**Header**

| Billing schedule number| Customer | Item group |
|---|---|---|
| SCH005 | US-001 | SPP |

**Line**

| Billing schedule number | Customer | Item group |
|---|---|---|
| SCH005 | US-001 | D0004 |

### Multiple billing schedules for the same end user and customer

For this example, use the following setup:

* On **Recurring contract billing parameters**, select **Split by item group**, and set the **Unique schedule type** field to **End user**.
* On **End users**, set up the following customer and end user relationship.

    | Customer account | End user account |
    |---|---|
    | US-001 | US-221 |

Create multiple billing schedules for the customer and end user combination. Because you select **Split by item group** on **Recurring contract billing parameters**, you can create multiple billing schedules for the same customer and end user relationship.

| Billing schedule number | Customer | End user account | Header item group |
|---|---|---|---|
| SCH005 | US-001 | US-221 | IG1 |
| SCH006 | US-001 | US-221 | IG2 |
| SCH007 | US-001 | US-221 | IG3 |

On **Item setup**, create support and renewal item relationships.

| Item code | Item relation | Support item | Renewal item | Renewal item group |
|---|---|---|---|---|
| Table | D001 | ITEM27 | D007 | IG1 |
| Table | D002 | ITEM28 | D005 | IG2 |
| Table | D003 | ITEM29 | D006 | IG3 |

Now create a sales order for customer US-001. This sales order has items from **Item setup**. When you create the sales order, open **Support and renewal process**, and set the **End user account** field and any other required information for the renewal item.

When you create and post the invoice for the transaction, the system creates different billing schedules for the customer/end user and item group combination. You can assign more than one line on the same sales order to the same billing schedule.

| Sales order # | Customer | End user account | Main item | Support item | Renewal item | Billing schedule number |
|---|---|---|---|---|---|---|
| SO0001 | US-001 | US-221 | D001 | ITEM27 | D007 | SCH005 |
| SO0001 | US-001 | US-221 | D002 | ITEM28 | D005 | SCH006 |
| SO0001 | US-001 | US-221 | D003 | ITEM29 | D006 | SCH005 |
