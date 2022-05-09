---
# required metadata

title: Calendars and master planning
description: This topic provides an overview of supply chain calendars and how they affect master planning.
author: t-benebo
ms.date: 08/19/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: global
ms.search.industry: Manufacturing
ms.author: benebotg
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Calendars and master planning

[!include [banner](../includes/banner.md)]

This topic provides an overview of supply chain calendars and how they affect master planning.  The different calendars used in master planning engine are explained, including how they affect the shipping and receiving dates in the planned orders. Finally, recommendations regarding the assignment, use and update of the calendars are given.

## Definition of a calendar

You can define a calendar to use in your organization in the page in **Organization administration > Setup > Calendars > Calendars**. 

Each date entry in a calendar can be **open** or **closed** or **base calendar**. This is specified in the **Control** column in the **Working times** page. For each date: 
- **Open** - Indicates that work is performed on the selected day. The calendar will be updated according to the working time template.
- **Closed** - Indicates work that is not performed during the day. 
- **Base calendar** - Indicates that the specific date will inherit the working times and open/closed from the base calendar. Therefore, when the base calendar is updated, the selected calendar will inherit operation times from it. 

For any closed dates, the **Closed for pickup** check box will automatically be assigned. For open dates, you can manually select the **Closed for pickup** option. This indicates that work is performed on the date, but shipping is not performed. 

## Calendars that affect master planning

### Calendar for a coverage group
A coverage group indicates a common set of parameters used for replenishment of the items that belong to the given coverage group. 

To add a calendar for a coverage group, go to **Master Planning > Setup > Coverage > Coverage groups**. Find the coverage group to which you want to assign the calendar to and then select it on the **Calendar** field.

The coverage group can be assigned in different pages: 
	- On the **Released product details** page of an item. To see the coverage group for an item, go to **Product information management > Products > Released products** and select the item to go to the **Released Products Details** page. You can see the item coverage group under the **Plan** FastTab.
	- On the **Item coverage** page. In the released products details page, click **Item coverage** to go to the item coverage page. In the overview tab you can see different parameters for replenishment depending on the site, warehouse, and product dimensions. The coverage group for each item will be inherited from the coverage group on the **Released product details** page. This can be overridden by using **Use specific settings** or **Override group setting** on the **General** tab.
	- On the **Master planning parameters** page. If am item does not have a coverage group set in the previous pages, master planning will take the general coverage group set on master planning parameters. This is set up in **Master planning > Setup > Master planning parameters** in the **General coverage group** field . 

### Calendar for a vendor
To indicate the working days of a vendor, you can assign a purchase calendar to the vendor on the **Purchase order defaults** page for a vendor. 

To set a calendar for a vendor, you need to create the calendar in **Organization Administration > Calendars > Calendars**. When the calendar is created, you have to assign it to the vendor. Go to **Accounts Payable > Vendors > All vendors** and select the vendor that you want to assign the calendar to. Then, on the vendor's page on the **Purchase order defaults** FastTab assign the new purchase calendar using the drop-down menu. 

The calendar for a vendor indicates the days on which they accept the placement of the purchase order and the dates when they can deliver the orders to your company. Consequently, the order dates for purchase orders for the vendor with a purchase calendar will be dates defined as open in the calendar. The delivery dates for those orders will also be in open days, and thus, will impact the lead time of the purchased item. 

#### Define the lead time for a purchased item

To specify the purchase lead time (and if only working days should be considered) for an item, you need to go to the default order settings page for the product, found under **Product information management > Products > Released products** and select **Default order settings**. 

> [!Note]
> The **Working days** under purchase lead time indicates the working days of the vendor. For example, a calendar for delivery only on Tuesdays with a lead time of 10 days and working days check box selected indicates that it would take 10 weeks (10 Tuesdays) for the item to be delivered.
Thus, in most cases it is not recommended to select working days for purchase order lead times.

#### Define lead times from the trade agreements page

Master planning can be set up to include all trade agreements for vendors. Trade agreements are fixed prices or discount agreements that are set up for one or more customers or vendors for the sale or purchase of individual or multiple products. Go to **Master planning > Setup > Master planning parameters** and on the **Planned orders** tab and select **Find trade agreements** to include the trade agreements when planning. Master planning can select the vendor with the **Minimum lead time** or with the **Lowest unit price**.

### Calendar for a warehouse
You can assign a calendar to a warehouse to indicate the open dates for receiving and shipping. If no calendar has been assigned to a warehouse, it is assumed that it is open all days. 

> [!Note]
> Assigning a calendar to a transit warehouse does not have any impact. Transit warehouses are used for supporting transfer orders. The applicable shipping or receipt dates for the orders are defined by the open days within the "From" warehouse and the "To" warehouse, and the mode of delivery calendar.

#### Closed for pickup policy
To indicate that a warehouse is open for receiving but pickup is not possible, you can use the **Closed for pickup policy** within the warehouse calendar. This also applies to customer pickups. 

### Transport calendar 
To indicate the dates that are available for shipping transfer orders from a **From warehouse**, you can assign a **Transport calendar**. 
You can set up a transport calendar per mode of delivery, or per mode of delivery and from warehouse. 
The transport calendar is set up in **Sales and marketing > Setup > Distribution > Modes of delivery**. Select a mode of delivery and click the **Transport calendar** button.

A line can be created for each warehouse and mode of delivery, where the calendar is added in the **Transport calendar** column. It will specify the transport calendar that will be applied when goods are shipped from the warehouse using the given mode of delivery. 
To apply a transport calendar to all shipments using a given mode of delivery, a line can be created without specifying the warehouse.  It will affect all shipments using the given mode of delivery, regardless of the warehouse. 

If no transport calendar is assigned, it is assumed that all days are open for transport.

### Calendar for a customer
To indicate the dates when a customer can accept deliveries, you can assign a receipt calendar to the customer. If no calendar is assigned to a customer, it is assumed that the customer can receive orders on all days. This will affect the receipt date on the sales order lines. If you select a date in the sales order lines that is not "open" in the customer calendar, the system will indicate that the receipt date is not valid. 

Note that it is only possible to include one calendar per customer. If you need to include a calendar for each different address for a customer, you can create one customer per address and then assign its respective calendar. 

The requested receipt date on the sales order lines is affected by the customer calendar and by the delivery date control method. You can read more about how the earliest delivery date is calculated in [Order Promising.](/dynamics365/unified-operations/supply-chain/sales-marketing/delivery-dates-available-promise-calculations).

### Shipping calendar for a legal entity
To indicate the dates in which a legal entity can ship goods, you can set up a shipping calendar under **Organization administration > Organizations > Legal entities**. Select the legal entity and add the calendar in the **Foreign trade and logistics** tab in the  **Shipping calendar** field. The shipping calendar will act as a source of defaults for all warehouse calendars in the legal entity. 

## How calendars affect dates in planning

### Order date of a planned purchase order 
The order date in a planned purchase order indicates the date when the order is placed. It will be an open date both in the vendor calendar and in the coverage group calendar. 
Sometimes, vendors need a few days of margin between when they receive the purchase order and when they are able to ship the goods. These dates are indicated in the vendor's margin days. However, if the item purchased is assigned to a coverage group with margin days, these margin days will override the vendor's margin days.

### Delivery date of a planned purchase order
The receipt date of a purchase indicates the date when you will receive the goods. It will be an open date in the calendar. The calendar that will be taken into account to indicate which days the purchase orders can be received are the following, in order from highest to lowest priority: 
1. Vendor's calendar
1. Coverage group calendar
1. Warehouse calendar for the receiving warehouse

Note that the coverage group calendar can be set in different pages and will take priority in the following order:
1. Item coverage group on the **Item coverage** page
1. Item coverage group on the **Released products details** page
1. Default item coverage group in **Master planning parameters**

### Shipping date of a planned transfer order
When creating a transfer order between two warehouses, the shipping date and the receipt date are included in the transfer order header, along with the "From" warehouse and "To" warehouse. The difference between these two dates is the expected transportation time (in days) between the warehouses.

The shipping date of a planned transfer order indicates the date that the goods are shipped from the "From" warehouse. The calendars used for specifying the available shipping date are listed by priority: 
1. Warehouse calendar of the "From" warehouse
1. Coverage group calendar (see fallback order for this calendar above)
If there is a warehouse calendar set, the shipping date will be an open date in the calendar. If there is not a warehouse calendar set, it will take the coverage group calendar. 

### Receipt date of a planned transfer order
The receipt date for a transfer order indicates the date that the goods are received in the "To" warehouse.

The calendars used for specifying the receipt date are the ones listed by priority: 
1. Coverage group calendar 
1. Warehouse calendar of the "To" warehouse
If there is a coverage calendar set, the receipt date will be an open date in the calendar. If there is not a coverage group calendar set, it will take the warehouse calendar. 

When finding the shipment and receiving dates for the planned transfer, the margins established by the user for shipping and receiving will also be considered. 

## Using calendars in master planning

### Assignment of SCM calendars
It is important to set the calendars to identify the working days of the company. The best implementation is to set a calendar for each element with different working days. In other words, all external calendars (customer, vendor) and all internal (warehouse, coverage group, and mode of delivery) related to the company.

### Recommendation on warehouse calendars
It is recommended to use one calendar per warehouse to include the specific changes only affecting the warehouse. For example, two or more warehouses could have the same working days but a different pickup policy. In that case, a calendar for each of the warehouses with its respective pickup policy is the best implementation for the system to include the best dates for planned purchase, transfer, and  production orders. 
If no warehouse calendars are set, the legal entity calendar can be used as a source of defaults for the warehouse calendar. 

### Recommendation of coverage group calendars
Regarding the coverage group calendar, it is important to consider that that has an overriding behavior regarding receiving dates in master planning. Thus, it is recommended to use it with caution. Particularly, it is useful in the case when replenishment needs to be done specific days in the week. 

### Updating SCM related calendars
While it is important that all relevant calendars are assigned in their respective place (vendor, customer, warehouse, mode of delivery, or coverage group), updating them is as important so they reflect the changes. The system will define the production, transfer, purchase, and sales order dates depending on the combination of the assigned calendars. 
It is a best practice to clarify who holds the responsibility for assigning and updating the calendars in its corresponding areas. In case of a breakdown or any other unusual change in the working days, it is essential to update the calendars according to it. All tasks which depend on calendars, such as master planning and production scheduling, must be rerun when calendars are updated. 


[!INCLUDE[footer-include](../../includes/footer-banner.md)]