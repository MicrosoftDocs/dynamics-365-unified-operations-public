---
title: Order entry deadlines
description: Learn about order entry deadlines, which is a cut-off time that determines whether a customer order is treated as if it was received on the current or next day.
author: AditiPattanaik
ms.author: adpattanaik
ms.topic: article
ms.date: 06/20/2017
ms.reviewer: kamaybac
ms.search.form: InventOrderEntryDeadlineGroup, InventOrderEntryDeadlineParameters, InventOrderEntryDeadlineTable, MCRAutoTaxRules
ms.assetid: bbc4f9a2-df4b-4d92-9f18-25282a85541f
---

# Order entry deadlines

[!include [banner](../includes/banner.md)]

This article provides information about order entry deadlines. An order entry deadline is a cut-off time that determines whether a customer order is treated (and fulfilled) as if it was received on the current day or the next day.

In many companies, only sales orders that are received before a certain time of day are treated as if they were received on that day. Any orders that are received after that time are treated as if they are received on the next business day. This cut-off time for orders is known as the order entry deadline.  

Order entry deadlines are used as input for order promising. Therefore, they help you manage customer expectations about order deliveries. For example, customers can see that, if they place an order with you before a specific time, you will commit to shipping the goods on the same day. However, if they miss that deadline, they can expect the shipment only on the next business day. You set order entry deadlines based on your warehouse capabilities and shipping carrier schedules.  

On the **Order entry deadlines** page, you set up order entry deadline times for all the days of the week. If orders are received after the specified times, they are treated as if they are received on the next day. By default, these times are set to 23:59 (that is, one minute before midnight at the end of the relevant day). You can change the default times so that they coincide with actual ship or receipt deadline times.  

You can define order entry deadlines for a specific group of customers. For example, you might want a specific group of customers to have order entry deadlines that are later than those of other customers. In this case, you first define groups for order entry deadlines on the **Order entry deadline groups** page. You then assign the groups to customers on the **Customers** page.  

If your company consists of several sites, you can set up order entry deadlines for each site. If the sites are located in different time zones, the order entry deadlines are set up in each site's time zone. However, when you work with sales orders and sales quotations, the order entry deadline is converted to your time zone on the **Available ship and receipt dates** page.  

On the **Activate order entry deadline combinations** page, you define the combinations of sites and order entry deadline groups that are allowed.

## Example: Order entry deadline
The order entry deadline on Tuesdays has been set to 16:00. On a particular Tuesday, at 17:00, you try to set the current date as the ship date. (Note that there is no lead time for this example.) If the **Delivery date control** check box is selected, you receive a warning that states that the date isn't valid. This warning appears on the **Available ship and receipt dates** page, where you can then select alternative dates.

## Example: Different order entry deadlines per site
Your company consists of two sites. The sites are located in different time zones, as shown in the following table.

| Site A                      | Site B                      |
|-----------------------------|-----------------------------|
| California                  | Florida                     |
| PST (Pacific Standard Time) | EST (Eastern Standard Time) |

Sites A and B have defined the following order entry deadlines.

| Day of the week             | A: Order entry deadlines (PST) | B: Order entry deadlines (EST) |
|-----------------------------|--------------------------------|--------------------------------|
| Monday                      | 13:00                          | 14:00                          |
| Tuesday                     | 13:00                          | 14:00                          |
| Wednesday                   | 13:00                          | 14:00                          |
| Thursday                    | 13:00                          | 14:00                          |
| Friday                      | 13:00                          | 14:00                          |

You're an order processor in Utah, where the time zone is MST (Mountain Standard Time). Therefore, provided that you place orders with site A before 14:00 MST and place orders with site B before 12:00 MST, you meet the order entry deadlines for both sites.  

The following table shows how the order entry deadlines for sites A and B are converted to MST time.

| Site A: PST         | Site A: MST        | Site B: EST           | Site B: MST        |
|---------------------|--------------------|-----------------------|--------------------|
| 13:00               | 14:00              | 14:00                 | 12:00              |

**Note:** If adjustment for daylight saving time is in effect, the order entry deadlines are adjusted accordingly.

## Example: Same order entry deadline per site
Your company consists of two sites. The sites are located in different time zones, as shown in the following table.

| Site A                      | Site B                      |
|-----------------------------|-----------------------------|
| California                  | Florida                     |
| PST (Pacific Standard Time) | EST (Eastern Standard Time) |

Sites A and B have defined the following order entry deadlines.

| Day of the week | PST and EST |
|-----------------|-------------|
| Monday          | 13:00       |
| Tuesday         | 13:00       |
| Wednesday       | 13:00       |
| Thursday        | 13:00       |
| Friday          | 13:00       |

You're an order processor in Utah, where the time zone is MST. Therefore, provided that you place orders with site A before 14:00 MST and place orders with site B before 11:00 MST, you meet the order entry deadlines for both sites. 

The following table shows how the order entry deadlines for sites A and B are converted to MST time.

| Site A: PST         | Site A: MST        | Site B: EST           | Site B: MST        |
|---------------------|--------------------|-----------------------|--------------------|
| 13:00               | 14:00              | 13:00                 | 11:00              |

**Note:** If adjustment for daylight saving time is in effect, the order entry deadlines are adjusted accordingly.

## Related information

[Delivery schedules](delivery-schedules.md)





[!INCLUDE[footer-include](../../includes/footer-banner.md)]