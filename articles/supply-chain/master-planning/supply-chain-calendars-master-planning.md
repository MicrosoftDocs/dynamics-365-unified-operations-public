---
title: Calendars and master planning
description: Learn about supply chain calendars and how they affect master planning, including a definition of a calendar and outlines of various values.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: WorkCalendarTable, VendTable
ms.topic: how-to
ms.date: 07/27/2026
ms.custom: 
  - bap-template
---

# Calendars and master planning

[!INCLUDE [banner](../includes/banner.md)]

This article provides an overview of supply chain calendars and how they affect master planning. It explains the different calendars that the master planning engine uses, including how they affect the shipping and receiving dates in the planned orders. It also provides recommendations for assigning, using, and updating calendars.

## Definition of a calendar

To define a calendar for your organization, go to **Organization administration** > **Setup** > **Calendars** > **Calendars**. Use the buttons on the Action Pane to add, remove, or edit calendars as needed.

To manage the details of a selected calendar, select **Working times** on the Action Pane. Each date entry in a calendar can be open or closed, or it can inherit its open or closed status and working times from the base calendar. You specify the value in the **Control** column on the **Working times** page. For each date, set the **Column** field to one of the following values:

- *Open* – Work is performed on the selected day. The calendar is updated according to the working time template.
- *Closed* – Work isn't performed on the selected day.
- *Base calendar* – The specific date inherits its working times and open or closed status from the base calendar. Therefore, when you update the base calendar, you update the selected calendar.

For any closed dates, the **Closed for pickup** checkbox is automatically selected. For open dates, you can manually select the **Closed for pickup** checkbox. By selecting this option, you indicate that work is performed on the date, but shipping isn't performed.

## Calendars that affect master planning

### Calendar for a coverage group

A coverage group defines a common set of parameters that are used for replenishment of all items that belong to the group.

To add a calendar for a coverage group, go to **Master planning** > **Setup** > **Coverage** > **Coverage groups**. Find the coverage group that you want to assign the calendar to, and then select it in the **Calendar** field.

You can assign the coverage group on different pages:

- On the **Released product details** page of an item. To view the coverage group for an item, go to **Product information management** > **Products** > **Released products**, and select the item to open the **Released product details** page. The **Plan** FastTab shows the item coverage group.
- On the **Item coverage** page. On the **Released product details** page, select **Item coverage** to open the **Item coverage** page. The **Overview** tab shows different parameters for replenishment, depending on the site, warehouse, and product dimensions. The coverage group for each item is inherited from the coverage group on the **Released product details** page. However, you can override it by selecting **Use specific settings** or **Override group setting** on the **General** tab.
- On the **Master planning parameters** page. If no coverage group is assigned to an item on the previously mentioned pages, master planning uses the general coverage group that's set in the **General coverage group** field on the **Master planning parameters** page (**Master planning** > **Setup** > **Master planning parameters**).

> [!NOTE]
> If you don't define a calendar for the coverage group of an item, Planning Optimization uses the calendar of the default coverage group defined on the **Master Planning Parameters** page.

#### Define the lead time for a purchased item

Specify the purchase lead time for an item (and whether only working days should be considered) on the **Default order settings** page for the product. To open this page, go to **Product information management** > **Products** > **Released products**, and select **Default order settings**.

> [!NOTE]
> The **Working days** checkbox for purchase lead time indicates working days as counted on the coverage group calendar. For example, a coverage group calendar set to allow delivery only on Tuesdays, with a lead time of 10 days and the **Working days** checkbox selected, indicates that it would take 10 weeks (10 Tuesdays) for the item to be delivered. Therefore, in most cases, don't select **Working days** for purchase order lead times.

### Calendars for a vendor

#### Vendor working days and shipping days

You can set up calendars that define each vendor's standard operating hours, such as the days when the vendor can receive purchase orders, and the days when the vendor can ship goods. The system uses these calendars when it calculates lead times, delivery times, and other dates. Follow these steps to set up vendor calendars.

1. Go to **Organization administration** > **Calendars** > **Calendars**, and either set up or identify the calendars that you want to use for each purpose.
1. Go to **Accounts payable** > **Vendors** > **All vendors**, and select the vendor that you want to assign the calendars to.
1. To set the standard operating hours for the vendor, on the **Purchase order defaults** FastTab, in the **Purchase calendar** field, select a calendar.
1. The days when the vendor can ship orders might differ from the standard operating hours. To set the shipping days, on the **Invoice and delivery** FastTab, in the **Ship calendar** field, select a calendar. For more information about this field and how it's used, see [Calculate requested ship dates for purchase orders](supplier-requested-confirmed-dates.md).

#### Define lead times from the trade agreements page

You can set up master planning to include all trade agreements for vendors. Trade agreements are fixed prices or discount agreements that you set up for one or more customers or vendors for the sale or purchase of individual or multiple products. To include the trade agreements during planning, go to **Master planning** > **Setup** > **Master planning parameters**, and then, on the **Planned orders** tab, select **Find trade agreements**. Master planning can select the vendor that has either the minimum lead time or the lowest unit price.

### Calendar for a warehouse

Assign a calendar to a warehouse to indicate the open dates for receiving and shipping. If you don't assign a calendar to a warehouse, the system assumes that the warehouse is open every day.

> [!NOTE]
> Assigning a calendar to a transit warehouse doesn't have any impact. Transit warehouses support transfer orders. The open days within the "from" warehouse and the "to" warehouse, and the mode of delivery calendar, define the applicable shipping or receipt dates for the orders.

#### Closed for pickup policy

To indicate that a warehouse is open for receiving but pickup isn't possible, set the **Closed for pickup policy** field in the warehouse calendar. This setting also applies to customer pickups.

### Transport calendar

To indicate the dates when transfer orders can be shipped, set up transport calendars for each mode of delivery or for each combination of mode of delivery and "from" warehouse.

To set up a transport calendar, go to **Sales and marketing** > **Setup** > **Distribution** > **Modes of delivery**, select a mode of delivery, and then select **Transport calendar**.

You can create a line for each warehouse and mode of delivery. The **Transport calendar** column specifies the transport calendar that's applied when goods are shipped from the warehouse that uses the mode of delivery.

To apply a transport calendar to all shipments that use a specific mode of delivery, regardless of the warehouse, create a line where you don't specify a warehouse.

If you don't assign a transport calendar, the system assumes that all days are open for transport.

#### Closed for pickup policy on the transport calendar

By default, Planning Optimization considers the **Closed for pickup** setting only on the warehouse calendar of the issuing warehouse when it schedules transfer order shipments. When the *Consider open for pickup on transport calendar for planned transfer orders with Planning Optimization* feature is enabled, Planning Optimization also considers the **Closed for pickup** setting on the transport calendar. The issue calendar becomes the intersection of both calendars. Therefore, the shipping date must be open for pickup on both the warehouse calendar and the transport calendar.

This feature also changes how Planning Optimization selects the receipt calendar for transfer orders. When the feature is enabled, the warehouse calendar of the receiving warehouse takes precedence over the coverage group calendar, if you specify a warehouse calendar. Without the feature, the coverage group calendar takes precedence. For more information, see [Receipt date of a planned transfer order](#receipt-date-of-a-planned-transfer-order) later in this article.

##### Prerequisites

To use this feature, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.49 or later.
- The feature named *Consider open for pickup on transport calendar for planned transfer orders with Planning Optimization* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

##### Example

Consider the following setup:

- Warehouse *WH11* uses a calendar that's open every weekday. Wednesdays are marked as **Closed for pickup**.
- The transport calendar for the *Truck* mode of delivery is open every weekday. Fridays are marked as **Closed for pickup**.
- A planned transfer order ships items from *WH11* by using the *Truck* mode of delivery.

When the feature is disabled, Planning Optimization can schedule the shipment on any weekday except Wednesday, because only the **Closed for pickup** setting on the warehouse calendar is considered.

When the feature is enabled, Planning Optimization can schedule the shipment only on Monday, Tuesday, or Thursday. Both the warehouse calendar (Wednesday is closed for pickup) and the transport calendar (Friday is closed for pickup) must be open for pickup on the shipping date.

### Calendar for a customer

Assign a receipt calendar to the customer to indicate the dates when a customer can accept deliveries. If you don't assign a calendar to a customer, the system assumes that the customer can receive orders every day.

This setup affects the receipt date on sales order lines. If the date that you select on the sales order lines isn't open in the customer calendar, the system indicates that the receipt date isn't valid.

You can assign only one calendar to each customer. If a customer has multiple addresses, and you must include a calendar for each address, create one customer per address and then assign the appropriate calendar to each customer.

The customer calendar and the delivery date control method affect the requested receipt date on the sales order lines. Learn more about how the earliest delivery date is calculated in [Order Promising](/dynamics365/unified-operations/supply-chain/sales-marketing/delivery-dates-available-promise-calculations).

### Shipping calendar for a legal entity

Set up a shipping calendar for a legal entity to indicate the dates when the legal entity can ship goods. Go to **Organization administration** > **Organizations** > **Legal entities**, select the legal entity, and then, on the **Foreign trade and logistics** tab, in the **Shipping calendar** field, add the calendar. The shipping calendar acts as a source of default values for all warehouse calendars in the legal entity.

## How calendars affect dates in planning

### Order date of a planned purchase order

The order date of a planned purchase order indicates the date when you place the order. It must be an open date in both the vendor calendar and the coverage group calendar. Sometimes, vendors need a margin of a few days between the date when they receive the purchase order and the date when they can ship the goods. The vendor's margin days indicate these dates. However, if the item that you purchase is assigned to a coverage group that has margin days, those margin days override the vendor's margin days.

### Delivery date of a planned purchase order

The receipt date of a purchase indicates the date when you expect to receive the goods. It's an open date in the calendar. To determine which days you can receive the purchase orders, the system considers the following calendars, in order from highest to lowest priority:

1. Vendor's calendar
1. Coverage group calendar
1. Warehouse calendar for the receiving warehouse

You can set the coverage group calendar on different pages. The system prioritizes the various page settings in the following order:

1. Item coverage group on the **Item coverage** page
1. Item coverage group on the **Released products details** page
1. Default item coverage group on the **Master planning parameters** page

### Shipping date of a planned transfer order

When you create a transfer order between two warehouses, you specify the shipping date and the receipt date in the transfer order header, along with the "from" warehouse and "to" warehouse. The difference between these two dates is the expected transportation time (in days) between the warehouses.

The shipping date of a planned transfer order indicates the date when the goods are shipped from the "from" warehouse. The calendars that are used to specify the available shipping date are listed here in order of priority:

1. Warehouse calendar of the "from" warehouse
1. Coverage group calendar (See the fallback order for this calendar earlier in this article.)

If you set a warehouse calendar, the system sets a shipping date that's open in that calendar. If you don't set a warehouse calendar, the system uses the coverage group calendar.

### Receipt date of a planned transfer order

The receipt date for a transfer order indicates the date that the goods are received in the "to" warehouse.

The calendars that specify the receipt date are listed here in order of priority:

1. Coverage group calendar
1. Warehouse calendar of the "to" warehouse

If you set a coverage calendar, the system sets a receipt date that's open in that calendar. If you don't set a coverage group calendar, the system uses the warehouse calendar.

When the *Consider open for pickup on transport calendar for planned transfer orders with Planning Optimization* feature is enabled, this priority order is reversed. The warehouse calendar of the "to" warehouse takes precedence over the coverage group calendar, if you specify a warehouse calendar. If you don't set a warehouse calendar, the system uses the coverage group calendar. For more information, see [Closed for pickup policy on the transport calendar](#closed-for-pickup-policy-on-the-transport-calendar) earlier in this article.

To determine the shipping and receipt dates for the planned transfer, the system also considers the margins that you define for shipping and receiving.

## Using calendars in master planning

### Assign calendars

Set the calendars to identify the working days of the company. Best practice is to set a calendar for each element that has different working days. In other words, set all external calendars (customer and vendor) and all internal calendars (warehouse, coverage group, and mode of delivery) that are related to the company.

### Recommendation for warehouse calendars

We recommend that you use one calendar for each warehouse, to include the specific changes that affect only that warehouse. For example, two or more warehouses have the same working days but a different pickup policy. In this case, the best practice is to use a separate calendar for each warehouse and its pickup policy. By using this approach, the system can include the best dates for planned purchase, transfer, and production orders.

If you don't set warehouse calendars, the legal entity calendar provides default values for the warehouse calendar.

### Recommendation for coverage group calendars

A coverage group calendar overrides receipt dates in master planning. Use coverage group calendars cautiously. They're especially useful in cases where replenishment must happen on specific days of the week.

### Update calendars

Although it's important that all relevant calendars are assigned in their appropriate place (vendor, customer, warehouse, mode of delivery, or coverage group), it's equally important to update them to reflect changes. The system defines the production, transfer, purchase, and sales order dates based on the combination of assigned calendars.

Clarify who is responsible for assigning and updating calendars in their appropriate place. In the event of a breakdown or any other unusual change in the working days, update the calendars according to that change. Rerun all tasks that depend on calendars, such as master planning and production scheduling, when you update calendars.

## Related information

- [Calculate requested ship dates for purchase orders](supplier-requested-confirmed-dates.md)
- [Improve scheduling engine performance](scheduling-engine-performance.md)
- [Date and time parameters used by Planning Optimization](planning-optimization/date-time-used.md)
- [Safety margins](planning-optimization/safety-margins.md)
