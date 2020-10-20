---
# required metadata

title: Create and update timeslots for customer pickup
description: This topic describes how to create, configure, and update customer pickup timeslots in Commerce headquarters.
author: anupamar-ms
manager: AnnBe
ms.date: 10/20/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: rapraj
ms.search.validFrom: 2020-09-20
ms.dyn365.ops.version: Retail 10.0.15 update

---

# Create and update timeslots for customer pickup

[!include [banner](../../includes/banner.md)]

This topic describes how to create, configure, and update customer pickup timeslots in Commerce headquarters.

## Overview

The timeslot feature provides a way for retailers to define a timeslot for items that have customer pickup delivery mode enabled. Timeslots allow retailers to define what days and times that orders can be picked up from a store. In addition, they can also define the number of orders that can be picked up in a given time window. Retailers can then limit the number of orders that can be picked up at a given day and time, resulting in a better quality experience for their customers. 

> [!NOTE] 
> The timeslot feature is available in Microsoft Dynamics 365 Commerce versions 10.0.15 and later.

The following image shows an example of timeslot selection during e-commerce checkout.

![Example of timeslot selection during e-commerce checkout](../dev-itpro/media/Curbside_timeslot_eCommerce.PNG)

## Timeslot properties 

A timeslot is a specific interval of time when a customer can choose to pick up their order from a specific store or location. The timeslot management feature is only available when the customer pickup delivery mode is configured in Dynamics 365 Commerce.

A timeslot is defined using the following properties.

- **Mode of delivery**: Specifies the pickup mode of delivery that the timeslot applies to.

- **Minimum Days** and **Maximum Days**: Specifies the earliest and latest days that can be selected for pickup relative to the day that the order is placed. "Minimum" ensures there is enough time for the retailer to process the order before it's ready for pickup. "Maximum" ensures that the user cannot pick a date that is too far into the future. For example, with a minimum of "1", if an order is placed on September 20th, the earliest day available for pickup will be the next eligible day (September 21st). Similarly, you can also define a maximum number of days within which to pick up an order. With minimum and maximum values defined, a site user can only see and pick a certain set of days during their checkout experience. The minimum value can be expressed in decimals if it is less than 1, for example 4 hours would be represented as a minimum value of 0.17 (4 divided by 24, and rounded up). If the minimum value is higher than 1, it will be always rounded even if its a decimal. The maximum value will always be rounded up, for example 1.2 will be rounded up to 2.

- **Start Date** and **End Date**: Specifies the timeslot start and end dates. Each timeslot entry has a start and end date, which provides the flexibility to add different timeslots throughout the year (for example, pickups during holiday hours). Once an order is placed, changing the start and end date on the timeslots will not apply to the existing order. When defining start and end dates, you must take into account store closure dates (for example, Christmas day), and ensure that a timeslot is not defined for these days.

- **Active Hours of Delivery**: Specifies the time period within which pickup is allowed (for example, you can define the pickup times to be between 2PM and 5PM every day). This allows the pickup times to be independent of store hours and allows a retailer to configure them for their specific business needs. When defining the active hours of pickup, you must ensure that store hours are taken into account and that a pickup time is not defined for when the store is closed.

    >[!NOTE]
    > The hours for store pickup have to be defined in the time zone of the respective store.

- **Time Slot Interval** - Specifies the time duration that can be allotted for each timeslot (for example, the time duration of each timeslot could be in increments of 15 minutes, 30 minutes, 1 hour, or some other duration).

- **Slots Per Interval** - Specifies the number of orders that can be served in each time interval (for example, 1, 2, 3, or any whole number). This allows the retailer to define how many customers or orders they want to serve for pickup within a given time interval.

- **Active Days** - Specifies the days during which the pick up timeslots are active (for example, Monday, Tuesday, Wednesday, Sunday, etc.). This allows retailers to define the days they want to support pickup orders.

- **Retail Channels**: Specifies the retail channel(s). Each timeslot can be associated with one or more retail stores. Depending on each store's hours of operation, one or more timeslot entries can be created and associated with a channel. 

<!-- ![HQ Timeslot overview](../dev-itpro/media/Curbside_timeslot_Settings_overview.PNG) -->

Only a single timeslot template can be configured per channel. These channels include brick-and-mortar stores, call centers, mobile devices, and e-Commerce sites.

## Configure the timeslot feature in Commerce headquarters

Timeslots must be defined in Commerce headquarters for each pickup mode of delivery so that point of sale (POS) and e-commerce channels can reference them.

 - Only one timeslot template can be associated with each store or channel.
 - Each timeslot created should be unique per delivery mode within each template.
 - Once the timeslot feature is configured, the timeslot calendar will be available to the selected stores or store groups, and will also be visible at the POS for reference.

To configure the timeslot feature in Commerce headquarters, follow these steps.

1. Go to **Commerce** \> **Channel setup** \> **Store pickup time slot**.
1. Select **New** to create a new timeslot template. To use an existing template, select the template in the left navigation pane.
1. Enter values for **Time Slot ID** and **Description**.
1. Under **Order Pickup - Time settings**, select **Add** to open a dialog box where you can define the date range, mode of delivery, active hours of delivery, active days, time slot interval, slots per interval, and other settings. 

    - If timeslots are going to be static for the foreseeable future, leave **End date** blank.
    - If the timeslots in a day are going to vary, create additional entries under **Order Pickup - Time settings** to ensure that the dates and times do not overlap. 

    > [!NOTE]
    > You can create multiple templates, but only one template can be associated with a single channel or store. 

    ![Order Pickup - Time settings dialog box](../dev-itpro/media/Curbside_timeslot_Settings_Page.PNG)

1. After configuring the **Order Pickup - Time settings** settings, select **OK**.
1. Next you will associate the timeslot template with the stores or channels where it will be used. Under **Retail Channels**, select **Add**. In the **Choose organization nodes** dialog box, Use the arrow buttons to select (or deselect) the stores, regions, and organizations that the template should be associated with, and then select **OK**.
    <!-- ![HQ Timeslot overview](../dev-itpro/media/Curbside_timeslot_Settings_overview.PNG) -->

1. On the **Distribution schedule** page, run the **1070** and **1135** jobs to sync the data to the channels.

## Timeslot selection for POS orders 

In POS, when an order or order line is identified for pickup, the cashier can select the pickup store or location and choose a date and timeslot. If a customer has a pickup order for a different store, the cashier can select dates when the pickup will be available in that store. The store lookup will provide a reference to the dates and store times. 

The following image shows an example of timeslot selection in a POS order.

![An example of timeslot selection in a POS order](../dev-itpro/media/Curbside_timeslot_POS.png)

## Timeslot selection for e-commerce orders 

For details on enabling timeslot selection for e-commerce orders, see [Pickup information module](./pickup-info-module.md). 

> [!NOTE]
> A Commerce site's checkout page must be authored with the pickup information module for users to view or edit pickup timeslots. In the absence of the pickup information module, orders will be placed without specifying or viewing timeslot information. 

The following image shows an example of an e-commerce order with timeslot information selected for pickup.

![Example of an e-Commerce order with timeslot information selected for pickup](../dev-itpro/media/Curbside_timeslot_eCommerce_checkoutsummary.PNG)

## Additional resources

[Pickup information module](./pickup-info-module.md)


