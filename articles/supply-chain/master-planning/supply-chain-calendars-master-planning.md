---
title: Calendars and master planning
description: Learn about supply chain calendars and how they affect master planning, including an definition of a calendar and outlines of various values.
author: t-benebo
ms.author: benebotg
ms.topic: how-to
ms.date: 11/24/2023
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form: WorkCalendarTable, VendTable
---

# Calendars and master planning

[!include [banner](../includes/banner.md)]

This article provides an overview of supply chain calendars and how they affect master planning. The different calendars used in master planning engine are explained, including how they affect the shipping and receiving dates in the planned orders. Finally, recommendations regarding the assignment, use and update of the calendars are given.

## Definition of a calendar

To define a calendar to use in your organization, go to **Organization administration** \> **Setup** \> **Calendars** \> **Calendars**.

Each date entry in a calendar can be open or closed, or it can inherit its open/closed status and working times from the base calendar. The value is specified in the **Control** column on the **Working times** page. For each date, the **Column** field is set to one of the following values:

- **Open** – Work is performed on the selected day. The calendar is updated according to the working time template.
- **Closed** – Work isn't performed on the selected day.
- **Base calendar** – The specific date inherits its working times and open/closed status from the base calendar. Therefore, when the base calendar is updated, the selected calendar is updated accordingly.

For any closed dates, the **Closed for pickup** checkbox is automatically selected. For open dates, you can manually select the **Closed for pickup** checkbox. In this way, you indicate that work is performed on the date, but shipping isn't performed.

## Calendars that affect master planning

### Calendar for a coverage group

A coverage group defines a common set of parameters that are used for replenishment of all items that belong to the group.

To add a calendar for a coverage group, go to **Master planning** \> **Setup** \> **Coverage** \> **Coverage groups**. Find the coverage group that you want to assign the calendar to, and then select it in the **Calendar** field.

The coverage group can be assigned on different pages:

- On the **Released product details** page of an item. To view the coverage group for an item, go to **Product information management** \> **Products** \> **Released products**, and select the item to open the **Released product details** page. The **Plan** FastTab shows the item coverage group.
- On the **Item coverage** page. On the **Released product details** page, select **Item coverage** to open the **Item coverage** page. The **Overview** tab shows different parameters for replenishment, depending on the site, warehouse, and product dimensions. The coverage group for each item is inherited from the coverage group on the **Released product details** page. However, you can override it by selecting **Use specific settings** or **Override group setting** on the **General** tab.
- On the **Master planning parameters** page. If no coverage group is assigned to an item on the previously mentioned pages, master planning uses the general coverage group that's set in the **General coverage group** field on the **Master planning parameters** page (**Master planning** \> **Setup** \> **Master planning parameters**).

> [!NOTE]
> If no calendar is defined on the Coverage group of the item, Planning Optimization will consider the calendar of the default coverage group defined on the **Master Planning Parameters**.

#### Define the lead time for a purchased item

You specify the purchase lead time for an item (and whether only working days should be considered) on the **Default order settings** page for the product. To open this page, go to **Product information management** \> **Products** \> **Released products**, and select **Default order settings**.

> [!NOTE]
> The **Working days** checkbox for purchase lead time indicates working days as counted on the coverage group calendar. For example, a coverage group calendar set to allow delivery only on Tuesdays, with a lead time of 10 days and the **Working days** checkbox selected, indicates that it would take 10 weeks (10 Tuesdays) for the item to be delivered. Therefore, in most cases, you shouldn't select **Working days** for purchase order lead times.

### Calendars for a vendor

#### Vendor working days and shipping days

You can set up calendars that define each vendor's standard operating hours (that is, the days when the vendor can, for example, receive purchase orders) and the days when the vendor can ship goods. The system uses these calendars when it calculates lead times, delivery times, and other dates. Follow these steps to set up vendor calendars.

1. Go to **Organization administration** \> **Calendars** \> **Calendars**, and either set up or identify the calendars that you want to use for each purpose.
1. Go to **Accounts payable** \> **Vendors** \> **All vendors**, and select the vendor that you want to assign the calendars to.
1. To set the standard operating hours for the vendor, on the **Purchase order defaults** FastTab, in the **Purchase calendar** field, select a calendar.
1. The days when the vendor can ship orders might differ from the standard operating hours. To set the shipping days, on the **Invoice and delivery** FastTab, in the **Ship calendar** field, select a calendar. For more information about this field and how it's used, see [Calculate requested ship dates for purchase orders](supplier-requested-confirmed-dates.md).

#### Define lead times from the trade agreements page

Master planning can be set up to include all trade agreements for vendors. Trade agreements are fixed prices or discount agreements that are set up for one or more customers or vendors for the sale or purchase of individual or multiple products. To include the trade agreements during planning, go to **Master planning** \> **Setup** \> **Master planning parameters**, and then, on the **Planned orders** tab, select **Find trade agreements**. Master planning can select the vendor that has either the minimum lead time or the lowest unit price.

### Calendar for a warehouse

You can assign a calendar to a warehouse to indicate the open dates for receiving and shipping. If no calendar is assigned to a warehouse, the system assumes that the warehouse is open every day.

> [!NOTE]
> Assigning a calendar to a transit warehouse doesn't have any impact. Transit warehouses are used for supporting transfer orders. The applicable shipping or receipt dates for the orders are defined by the open days within the "from" warehouse and the "to" warehouse, and the mode of delivery calendar.

#### Closed for pickup policy

To indicate that a warehouse is open for receiving, but pickup isn't possible, you can set the **Closed for pickup policy** field in the warehouse calendar. This setting also applies to customer pickups.

### Transport calendar

To indicate the dates when shipping transfer orders can be shipped from a "from" warehouse, you can assign a transport calendar. You can set up a transport calendar for each mode of delivery, or for each mode of delivery and "from" warehouse.

To set up a transport calendar, go to **Sales and marketing** \> **Setup** \> **Distribution** \> **Modes of delivery**, select a mode of delivery, and then select **Transport calendar**.

You can create a line for each warehouse and mode of delivery. The **Transport calendar** column specifies the transport calendar that's applied when goods are shipped from the warehouse that uses the mode of delivery.

To apply a transport calendar to all shipments that use a specific mode of delivery, regardless of the warehouse, create a line where no warehouse is specified.

If no transport calendar is assigned, the system assumes that all days are open for transport.

### Calendar for a customer

To indicate the dates when a customer can accept deliveries, you can assign a receipt calendar to the customer. If no calendar is assigned to a customer, the system assumes that the customer can receive orders every day.

This setup affects the receipt date on sales order lines. If the date that you select on the sales order lines isn't open in the customer calendar, the system indicates that the receipt date isn't valid.

Only one calendar can be assigned to each customer. If a customer has multiple addresses, and you must include a calendar for each address, you can create one customer per address and then assign the appropriate calendar to each customer.

The requested receipt date on the sales order lines is affected by the customer calendar and by the delivery date control method. You can read more about how the earliest delivery date is calculated in [Order Promising.](/dynamics365/unified-operations/supply-chain/sales-marketing/delivery-dates-available-promise-calculations).

### Shipping calendar for a legal entity

To indicate the dates when a legal entity can ship goods, you can set up a shipping calendar for it. Go to **Organization administration** \> **Organizations** \> **Legal entities**, select the legal entity, and then, on the **Foreign trade and logistics** tab, in the **Shipping calendar** field, add the calendar. The shipping calendar acts as a source of default values for all warehouse calendars in the legal entity.

## How calendars affect dates in planning

### Order date of a planned purchase order

The order date of a planned purchase order indicates the date when the order is placed. It will be an open date in both the vendor calendar and the coverage group calendar. Sometimes, vendors need a margin of a few days between the date when they receive the purchase order and the date when they can ship the goods. These dates are indicated in the vendor's margin days. However, if the item that's purchased is assigned to a coverage group that has margin days, those margin days override the vendor's margin days.

### Delivery date of a planned purchase order

The receipt date of a purchase indicates the date when you'll receive the goods. It will be an open date in the calendar. To determine which days the purchase orders can be received on, the system considers the following calendars, in order from highest to lowest priority:

1. Vendor's calendar
1. Coverage group calendar
1. Warehouse calendar for the receiving warehouse

The coverage group calendar can be set on different pages and takes priority in the following order:

1. Item coverage group on the **Item coverage** page
1. Item coverage group on the **Released products details** page
1. Default item coverage group on the **Master planning parameters** page

### Shipping date of a planned transfer order

When creating a transfer order between two warehouses, the shipping date and the receipt date are included in the transfer order header, along with the "from" warehouse and "to" warehouse. The difference between these two dates is the expected transportation time (in days) between the warehouses.

The shipping date of a planned transfer order indicates the date when the goods are shipped from the "from" warehouse. The calendars that are used to specify the available shipping date are listed here in order of priority:

1. Warehouse calendar of the "from" warehouse
1. Coverage group calendar (See the fallback order for this calendar earlier in this article.)

If a warehouse calendar is set, the shipping date will be an open date in that calendar. If no warehouse calendar is set, the coverage group calendar is used.

### Receipt date of a planned transfer order

The receipt date for a transfer order indicates the date that the goods are received in the "to" warehouse.

The calendars that are used to specify the receipt date are listed here in order of priority:

1. Coverage group calendar
1. Warehouse calendar of the "to" warehouse

If a coverage calendar is set, the receipt date will be an open date in that calendar. If no coverage group calendar is set, the warehouse calendar is used.

To determine the shipping and receipt dates for the planned transfer, the system also considers the margins that the user defined for shipping and receiving.

## Using calendars in master planning

### Assignment of SCM calendars

It's important to set the calendars to identify the working days of the company. The best practice is to set a calendar for each element that has different working days. In other words, set all external calendars (customer and vendor) and all internal calendars (warehouse, coverage group, and mode of delivery) that are related to the company.

### Recommendation for warehouse calendars

We recommend that you use one calendar for each warehouse, to include the specific changes that affect only that warehouse. For example, two or more warehouses have the same working days but a different pickup policy. In this case, the best practice is to use a separate calendar for each warehouse and its pickup policy. In this way, the system can include the best dates for planned purchase, transfer, and production orders.

If no warehouse calendars are set, the legal entity calendar can be used as a source of default values for the warehouse calendar.

### Recommendation for coverage group calendars

It's important to consider that a coverage group calendar overrides receipt dates in master planning. Therefore, we recommend that you use coverage group calendars cautiously. They're especially useful in cases where replenishment must be done on specific days of the week.

### Updating SCM-related calendars

Although it's important that all relevant calendars are assigned in their appropriate place (vendor, customer, warehouse, mode of delivery, or coverage group), it's equally important to update them so that they reflect changes. The system defines the production, transfer, purchase, and sales order dates based on the combination of assigned calendars.

The best practice is to clarify who is responsible for assigning and updating calendars in their appropriate place. In the event of a breakdown or any other unusual change in the working days, it's essential to update the calendars according to that change. All tasks that depend on calendars, such as master planning and production scheduling, must be rerun when calendars are updated.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
