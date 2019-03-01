---
# required metadata

title: Pro-rate Header Charges to matching sales lines
description: This topic describes additional capabilities for calculating and applying auto-charges to Retail channel orders using the advanced auto charges features.
author: hhaines
manager: annbe
ms.date: 02/28/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: hhaines
ms.search.validFrom: 
ms.dyn365.ops.version: 10.0


---

# Pro-ration and grouping of Header Auto Charges to Retail sales lines

This feature will be available for Point of Sale created transactions in version 10.0.1 and available for Call Center created sales in version 10.0.2.

This feature is only available if the Advanced Auto Charges feature is enabled in Retail parameters.  This calculation currently will only be applied to Retail sales orders created through Retail channels (POS, Call Center and Ecommerce).

This feature will allow an organization to have more flexibility in how Header level Auto Charges are calculated and applied to Retail sales transactions.

Prior to version 10.0.1, the Auto Charges defined at the Header level with a specific Mode of Delivery relation would only be calculated when there was a match with the Mode of Delivery data applied at the sales order header.  For example, if Header level Auto Charges were defined for both Mode of Delivery "99" and Mode of Delivery "11" in the application, and a Sales Order was created with Mode of Delivery "99" on the order header; but had some sale lines that were configured to ship by Mode of Delivery "11"; with the existing functionality in this scenario, only the Header level charges linked to Mode of Delivery "99" would be considered and applied to this sales order. 

In all in-market versions of our product, the Header level charges have an added feature that allows you to define a tiered charge configuration based on the order value.  For example, if the order value is between $50.00-$200.00, the organization may want to charge a freight charge of $5.00, but if the order is between 200.01-500.00, the freight charge may be $4.00.  

In Retail scenarios, organizations want the benefits of the tiered charges calculation that is provided with the Header level charges, but they also want to ensure that in a mixed delivery mode scenario that the charges calculated are based on a match with the Mode of Delivery as defined on each sales line.

This new feature allows for configuring your Header level Auto Charges so that all modes of delivery on the order will be considered.  This feature adds a more complex calculation logic when calculating the Header charges that will group together the items shipping the same mode of delivery and treat those as their own order for the purpose of calculating the Header Auto Charges based on their combined sales value and delivery mode designation.   

With this new feature, once the appropriate Header charges are obtained for the sales lines that are shipping the same mode of delivery, this calculated charge will be pro-rated down to the sales line level.  By placing these charges at the line level vs. keeping them at the header level, it allows for a more specific link between the item and the charges value calculated for it.  This can be useful in partial return scenarios when an organization may wish to only refund a portion of the charge instead of the entire charge when only some items are returned.

Below is an example of a scenario and how these charges would be calculated with and without this new feature enabled

Scenario when xxxx is disabled (note this is the equivalent to how the Header charges behaved prior to version 10.0.1).

In this scenario, Header level charges are defined for Mode of Delivery "99" and Mode of Delivery "11".

A sales order is created in Call Center where the Header Mode of Delivery is "99".  This order contains 5 items, but two of the line item have been configured to use Mode of Delivery "11".

In this scenario, the entire order is evaluated against the Auto Charges table for Mode of Delivery "99".  The full total of all sales lines is used to determine a matching Tier in the Auto Charges configuration and this charge is applied at the order header level.

Even though charges should be higher for items shipping by Mode of Delivery "11" (based on the Auto Charges setup for Mode of Delivery "11"), the sales lines shipping mode of delivery "11" are not referincing the matching auto charges table and only the Auto Charges for Mode of Delivery "99" are applied to the entire order.

In a returns situation using this scenario, if the charge code has been configured to be refunded, the total Header charge will be systematically applied to the refund, even if only some of the items are being returned.

In a scenario where XXXX is enabled (available in 10.0.1 for POS and 10.0.2 for Call Center)

In this scenario, Header level charges are also defined for Mode of Delivery "99" and Mode of Delivery "11", but the xxxxxxx flag has also been enabled for these Auto Charge tables.

In this scenario, a sales order is created where the Header Mode of Delivery is "99" and 3 out of 5 items on the order are designated to ship this mode of delivery, but 2 line items on the order have been manually changed to Mode of Delivery "11".

Due to the configuration of the Auto Charges to use xxxxxx, the system will perform the following calculation:

xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx



Because the charges are pro-rated to each salesline, in a partial return scenario, if the charge code is refundable, only the portion of the charge allocated to that line will be refunded when the item is returned. Unlike the previous scenario where the full total charge is refunded, this gives the organization the ability to only give a portion of the full charge back based on specifically which lines were returned.

