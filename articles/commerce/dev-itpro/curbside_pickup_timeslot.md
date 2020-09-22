---
# required metadata

title: Create and update timeslots for 'Pickup' delivery mode(s)
description: This topic describes how to create and update 'Timeslots' in Commerce Headquarters and enable them for the 'Pickup' delivery mode(s).
author: josaw1
manager: AnnBe
ms.date: 9/20/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: rapraj
ms.search.validFrom: 2020-09-20
ms.dyn365.ops.version: Retail 10.0.15 update

---

# Create and update timeslots for 'Pickup' delivery mode(s)

[!include [banner](../../includes/banner.md)]

## Overview

The time-slot feature provides a way for retailers to define a time slot for items that have pickup delivery mode(s). A time slot allows the retailer to define what days/times orders can be picked up from a store. In addition, they can also define the number of orders that can be picked up in a given window.  This way a retailer can limit  the number of orders to be picked up at a given time/day which in-turn allows them to  provide a quality experience for their customers. 

This functionality is available in Microsoft Dynamics 365 Commerce versions 10.0.15 and later.

Below is an example of time slot selection during ecommerce checkout
![eCommerce Timeslot Pickup](../dev-itpro/media/Curbside_timeslot_eCommerce.png "eCommerce Timeslot Pickup")

-Time slots for your retail channel
Timeslot is a specific interval of time, where the customer can choose to pickup their order from a specific store/location. This time slot management is only available to only available to the 'Pickup' mode of delivery in Dynamics 365 Commerce.
A timeslot includes the following fields.
•	Mode of delivery: This is the Pickup mode of delivery for which the timeslot applies to. 
•	Minimum and Maximum: This is the earliest and farthest days that can be selected for pickup relative to the day in which the order is placed. The Minimum ensures there is enough time for the retailer to process the order before its ready for pickup. The Maximum ensures the user cannot pick a date that is too far into the future. E.g. With a minimum=1, if the order is being placed on 9/20/2020 it means the earliest day available for pickup will be the next eligible day i.e 9/21/2020. Similarly, you can also define a Maximum. With Minimum and Maximum defined, a user can only see and pick a certain set of days on their checkout experience.  Is there a min/max on this? 

•	Start & End Date: Each time slot entry has a start and end date for which the timeslots are applicable. This provides the flexibility to add different time slots through the year E.g. Fall vs Christmas hours. Once  an order is already placed changing the start and end date on the timeslots will not apply to the existing order. 
•	Active hours of pickup: This defines the time period between which the pickup is allowed. E.g. You can define the pickup times to be 2pm to 5pm everyday. This allows the pickup times to be independent of store hours and allows a retailer to configure it per their business needs.
•	Time Interval: This defines the time duration that can be allotted for each timeslot. E.g. it could be in increments of 15 mins, 30 mins,  1 hour etc.. 
•	Slots per interval: This defines the number of orders that can be served in each time interval. E.g.  1, 2, 3 or any whole number. This allows the retailer to define how many customers/orders they want to serve for pickup within a given time interval.
•	Active Days: This defines the days during which the pick up time slots are active. E.g. Mon, Tue, Wed, Sun etc. This allows the retailer to define days when then want to support pickup orders.
•	Retail channel: Each timeslot can be associated to one or more retail stores. Depending on each stores operational hours, one or more timeslots can be created and associated to a channel. 

![HQ Timeslot overview](../dev-itpro/media/Curbside_timeslot_Settings_overview.png "HQ Timeslot overview")

Only a single Timeslot template can be configured per channel. These channels include brick-and-mortar stores, call centers, mobile devices, and e-Commerce sites.

If a customer has a pickup order for a different store, the cashier can select dates when the pickup will be available in that store. The store lookup will provide a reference to the dates and store times. 

## Enable 'Timeslot' for pickup mode of delivery.

To be able to create and use the 'Timeslot' for the 'Pickup' mode of delivery, the 'Curbside' feature needs to be enabled on the 'Feature Management' workspace. 

<INSERT IMAGE FOR THE FEATURE FLAG & FINAL NAME>

## Configure 'Timeslot' per 'Pickup' mode of delivery.

Follow these steps to configure 'Timeslot' for the 'pickup' mode of delivery.

1. Go to **Commerce** \> **Channel Setup** \> **Timeslot management**.
2. Select **New** to create a new Timeslot template & provide a *ID* and *Description*. To use an existing template, select the template in the left pane.
3. In the **Time settings** TAB, click *Add* to open a slider control and define the date range, Time period, Time slot durartion, active days etc...

    - If Timeslots are going to be as-is for long time, leave the **End date** field 'BLANK'.
    - If the Timeslots in a day are going to vary - create additional entries on the **Time settings** TAB - ensure that the date and times do not overlap. 

    > [!NOTE]
    > You can create multiple templates, but only one template can be associated with a single channel/store. 

    ![Add Time Settings dialog box](../dev-itpro/media/Curbside_timeslot_Settings_Page.png "Add Time Settings dialog box")

4. Associate the 'Timeslot' template with the stores/channels where it will be used. In the **Choose organization nodes** dialog box, select the stores, regions, and organizations that the template should be associated with.

    - Only one 'Timeslot' template can be associated with each store/channel.
    - Use the arrow buttons to select stores, regions, or organizations. The calendar will be available to the stores or store groups, and it will be visible at the POS for reference.

    ![HQ Timeslot overview](../dev-itpro/media/Curbside_timeslot_Settings_overview.png "HQ Timeslot overview")

5. On the **Distribution schedule** page, run the **1070** and **1090** jobs to make the Timeslot details are available to the POS.

## Timeslot selection on POS orders 
1. In POS, once a order / order line is identified for 'Pickup' 
2. Cashier can select the 'Pickup' store/location
3. Once the location is selected - the Pickup Date and Timeslot selection is prompted. 

![POS Timeslot Pickup](../dev-itpro/media/Curbside_timeslot_POS.png "POS Timeslot Pickup")

## Timeslot selection on eCommerce orders 
1. In eCommerce, the timeslot selection is displayed only at the 'Checkout' page.  
2. Based on the 'Pickup mode' the Pickup Date and Timeslot selection is prompted. 

![eCommerce Timeslot Pickup](../dev-itpro/media/Curbside_timeslot_eCommerce.png "eCommerce Timeslot Pickup")

